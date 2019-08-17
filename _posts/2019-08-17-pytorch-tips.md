---
layout: post
title: 9 Tips For Training Lightning-Fast Neural Networks In Pytorch
tags: [pytorch, deep learning]
---

<!-- <p style="text-align:center">
	<img src="/topics/img/pytorch-tips.jpg"/>
</p> -->

Author: William Falcon  
Date: Jul. 21, 2019  
From: [https://towardsdatascience.com/9-tips-for-training-lightning-fast-neural-networks-in-pytorch-8e63a502f565](https://towardsdatascience.com/9-tips-for-training-lightning-fast-neural-networks-in-pytorch-8e63a502f565)

---

Let’s face it, your model is probably still stuck in the stone age. I bet you’re still using 32bit precision or *\*GASP\** perhaps even training **only** on a single GPU.

😱.

I get it though, there are 99 speed-up guides but a checklist ain’t 1? (yup, that just happened). Well, consider this the **ultimate**, step-by-step guide to making sure you’re squeezing all the (GP-Use) 😂 out of your model.

This guide is structured from simplest to most PITA modifications you can make to get the most out of your network. I’ll show example Pytorch code and the related flags you can use in the [Pytorch-Lightning Trainer](https://williamfalcon.github.io/pytorch-lightning/Trainer/) in case you don’t feel like coding these yourself!

**Who is this guide for?** Anyone working on non-trivial deep learning models in Pytorch such as industrial researchers, Ph.D. students, academics, etc… The models we’re talking about here might be taking you multiple days to train or even weeks or months.

We’ll cover (from simplest to most PITA)

* TOC
{:toc}

## Pytorch-Lightning

<p style="text-align:center">
	<img src="/posts-data/2019-08-17/pytorch-0.gif" />
</p>

You can find every optimization I discuss here in the Pytorch library called [Pytorch-Lightning](https://github.com/williamFalcon/pytorch-lightning). Lightning is a light wrapper on top of Pytorch that automates training for researchers while giving them full control of the critical model parts. Check out [this tutorial for a more robust example](https://github.com/williamFalcon/pytorch-lightning/blob/master/pytorch_lightning/examples/new_project_templates/single_gpu_node_template.py).

Lightning uses the latest best practices and minimizes the places where you can make a mistake.

We’ll define our LightningModel for MNIST [here](https://williamfalcon.github.io/pytorch-lightning/LightningModule/RequiredTrainerInterface/#minimal-example) and fit using the Trainer.

```python
from pytorch_lightning import Trainer
model = LightningModule(…)
trainer = Trainer()
trainer.fit(model)
```

## 1. DataLoaders

<p style="text-align:center">
	<img src="/posts-data/2019-08-17/pytorch-1.gif" />
</p>

This is probably the easiest place to get some speed gains. The days of saving h5py or numpy files to speed up your data loading are gone (wait… you guys weren’t doing that?? ). With [Pytorch dataloader ](https://pytorch.org/tutorials/beginner/data_loading_tutorial.html)loading image data is trivial (for NLP data, check out [TorchText](https://torchtext.readthedocs.io/en/latest/datasets.html))

```python
dataset = MNIST(root=self.hparams.data_root, train=train, download=True)
loader = DataLoader(dataset, batch_size=32, shuffle=True)
for batch in loader:
  x, y = batch
  model.training_step(x, y)
  ...
```

In lightning you don’t need to specify a training loop, just define the dataLoaders and the Trainer will [call them when needed](https://williamfalcon.github.io/pytorch-lightning/LightningModule/RequiredTrainerInterface/#tng_dataloader).

## 2. Number Of Workers in DataLoaders


<p style="text-align:center">
	<img src="/posts-data/2019-08-17/pytorch-2.gif" />
</p>

Another magical place for speed-up comes from allowing batches to be loaded in parallel. So instead of loading one batch at a time, you can load nb_workers batches at a time.

```python
# slow
loader = DataLoader(dataset, batch_size=32, shuffle=True)
# fast (use 10 workers)
loader = DataLoader(dataset, batch_size=32, shuffle=True, num_workers=10)
```

## 3. Batch size


<p style="text-align:center">
	<img src="/posts-data/2019-08-17/pytorch-3.gif" />
</p>

Before starting the next optimization steps, crank up the batch size to as much as your CPU-RAM or GPU-RAM will allow.

The next sections will focus on helping decrease the RAM footprint so you can continue to increase the batch size.

Remember you’ll likely have to update your learning-rate again. A good rule of thumb is to double learning rate if you double batch size.

## 4. Accumulated Gradients


<p style="text-align:center">
	<img src="/posts-data/2019-08-17/pytorch-4.gif" />
</p>

In the case where you have maxed out your compute resources, and your batch size is still too low (say 8), then we need to simulate a larger batch size for gradient descent to provide a good estimate.

Let’s say we want to get to a batch size of 128. Then we’ll do 16 forward and backward passes with a batch-size of 8 before doing a single optimizer step.

```python
# clear last step
optimizer.zero_grad()

# 16 accumulated gradient steps
scaled_loss = 0
for accumulated_step_i in range(16):
     out = model.forward()
     loss = some_loss(out,y)    
     loss.backward()
      scaled_loss += loss.item()
      
# update weights after 8 steps. effective batch = 8*16
optimizer.step()

# loss is now scaled up by the number of accumulated batches
actual_loss = scaled_loss / 16
```

In lightning, this is all done for you though. Just set [this flag](https://williamfalcon.github.io/pytorch-lightning/Trainer/Training%20Loop/#accumulated-gradients).

```python
trainer = Trainer(accumulate_grad_batches=16)
trainer.fit(model)
```

## 5. Retained Graphs


<p style="text-align:center">
	<img src="/posts-data/2019-08-17/pytorch-5.gif" />
</p>

A simple place to blow up your RAM is not releasing the pointer to the computational graph by say… storing your loss for logging purposes

```python
losses = []
...
losses.append(loss)
print(f'current loss: {torch.mean(losses)'})
```

The problem above is that **loss** still has a copy of the graph. In this case, call .item() to release it.

```python
# bad
losses.append(loss)
# good
losses.append(loss.item())
```

Lightning takes special care to make sure it never retains copy of the graph ([here’s an example](https://github.com/williamFalcon/pytorch-lightning/blob/master/pytorch_lightning/models/trainer.py#L812)).

## 6. Single GPU training


<p style="text-align:center">
	<img src="/posts-data/2019-08-17/pytorch-6.gif" />
</p>

Once you’ve maxed out the previous steps, it’s time to move into GPU training. Training on the GPU will parallelize the mathematical computations across the many GPU cores. The speed-up you get depends on the type of GPU you’re using. I recommend the 2080Ti for personal use and the V100 for corporate use.

It may seem overwhelming at first but you really only need to do two things: 1) move your model to the GPU, 2) whenever you run data through it, put the data on the GPU.

```python
# put model on GPU
model.cuda(0)

# put data on gpu (cuda on a variable returns a cuda copy)
x = x.cuda(0)

# runs on GPU now
model(x)
```

If you’re using Lightning, you don’t have to do anything to your code. Just set [this flag:](https://williamfalcon.github.io/pytorch-lightning/Trainer/Distributed%20training/#single-gpu)

```python
# ask lightning to use gpu 0 for training
trainer = Trainer(gpus=[0])
trainer.fit(model)
```

The main thing to take care of when training on GPUs is to limit the number of transfers between CPU and GPU.

```python
# expensive
x = x.cuda(0)

# very expensive
x = x.cpu()
x = x.cuda(0)
```

If you run out of RAM for example, don’t move data back to the CPU to save RAM. Try to optimize your code in other ways or distribute across GPUs before resorting to that.

Another thing to watch out for is calling operations which force the GPUs to synchronize. An example would be clearing the memory cache.

```python
# really bad idea. Stops all the GPUs until they all catch up
torch.cuda.empty_cache()
```

If you use Lightning, however, the only places this could be an issue are when you define your Lightning Module. Lightning takes special care to not make these kinds of mistakes.

## 7. 16-bit precision

Sixteen-bit precision is an amazing hack to cut your memory footprint in half. The majority of models are trained using 32-bit precision numbers. However, recent research has found that models can work just as well with 16-bit. Mixed-precision means you use 16-bit for certain things but keep things like weights at 32-bit.

To use 16-bit precision in Pytorch, install the [apex library](https://github.com/NVIDIA/apex) from NVIDIA and make these changes to your model.

```python
# enable 16-bit on the model and the optimizer
model, optimizers = amp.initialize(model, optimizers, opt_level='O2')

# when doing .backward, let amp do it so it can scale the loss
with amp.scale_loss(loss, optimizer) as scaled_loss:                      
    scaled_loss.backward()
```

The *amp* package will take care of most things for you. It’ll even scale the loss if the gradients explode or go to zero.

In lightning, [it’s trivial to enable 16-bit](https://williamfalcon.github.io/pytorch-lightning/Trainer/Distributed%20training/#16-bit-mixed-precision) without having to modify anything in your model or do what I wrote above.

```python
trainer = Trainer(amp_level='O2', use_amp=False)
trainer.fit(model)
```

## 8. Moving to Multiple GPUs

Now, this is where things get really interesting. There are 3 (maybe more?) ways of doing multi-GPU training.

### Split-batch Training

<p style="text-align:center">
	<img src="/posts-data/2019-08-17/pytorch-8-1.png" />
	<br /> A) Copy model on each GPU. B) Give each GPU a portion of the batch.
</p>

The first way should just be called split-batch training. This strategy copies the model onto each GPU and each GPU gets a portion of the batch.

```python
# copy model on each GPU and give a fourth of the batch to each
model = DataParallel(model, devices=[0, 1, 2 ,3])

# out has 4 outputs (one for each gpu)
out = model(x.cuda(0))
```

In lightning, you can just increase the number of GPUs you tell the trainer about without having to do anything of the above.

```python
# ask lightning to use 4 GPUs for training
trainer = Trainer(gpus=[0, 1, 2, 3])
trainer.fit(model)
```

### Split Model Training

<p style="text-align:center">
	<img src="/posts-data/2019-08-17/pytorch-8-2.png" />
	<br /> Put different parts of the model on different GPUs. Batch moves sequentially
</p>

Sometimes your model can be too big too fit in memory. For example a sequence to sequence model with an encoder and a decoder might take up 20 GB of RAM when generating outputs. In this case, we want to put the encoder and decoder on separate GPUs.

```python
# each model is sooo big we can't fit both in memory
encoder_rnn.cuda(0)
decoder_rnn.cuda(1)

# run input through encoder on GPU 0
encoder_out = encoder_rnn(x.cuda(0))

# run output through decoder on the next GPU
out = decoder_rnn(encoder_out.cuda(1))

# normally we want to bring all outputs back to GPU 0
out = out.cuda(0)
```

For this type of training, don’t give Lightning trainer any GPUs. Instead, put your own modules in the LightningModule on the correct GPU

```python
class MyModule(LightningModule):
    def __init__():
        self.encoder = RNN(...)
        self.decoder = RNN(...)
    def forward(x):
        # models won't be moved after the first forward because 
        # they are already on the correct GPUs
        self.encoder.cuda(0)
        self.decoder.cuda(1)
        out = self.encoder(x)
        out = self.decoder(out.cuda(1))
        
# don't pass GPUs to trainer
model = MyModule()
trainer = Trainer()
trainer.fit(model)
```

### Mixing both

In the case above, both the encoders and decoders can still benefit from parallelizing each operation. We can get more creative now.

```python
# change these lines
self.encoder = RNN(...)
self.decoder = RNN(...)

# to these
# now each RNN is based on a different gpu set
self.encoder = DataParallel(self.encoder, devices=[0, 1, 2, 3])
self.decoder = DataParallel(self.encoder, devices=[4, 5, 6, 7])

# in forward...
out = self.encoder(x.cuda(0))

# notice inputs on first gpu in device
sout = self.decoder(out.cuda(4))  # <--- the 4 here
```

Caveats to think about when using multiple GPUs

- model.cuda() won’t do anything if it’s already on that device.

- Always put the inputs on the first device in the devices list.

- Transferring data across devices is expensive, do it as a last resort.

- The optimizer and gradients will be stored on GPU 0. Thus the memory used on GPU 0 will likely be much greater than the others.

## 9. Multi-Node GPU training


<p style="text-align:center">
	<img src="/posts-data/2019-08-17/pytorch-9.png" />
	<br /> Every GPU on every machine gets a copy of the model. 
	<br /> Each machine gets a portion of the data and trains only on that portion. 
	<br /> Each machine syncs gradients with the other.
</p>

If you’ve made it this far, you’re now in the realm of training Imagenet in minutes! This isn’t as hard as you might think, but it might require a bit more knowledge about your compute cluster. These instructions assume you’re using SLURM on your cluster.

Pytorch allows multi-node training by copying the model on each GPU across every node and syncing the gradients. So, each model is initialized independently on each GPU and in essence trains independently on a partition of the data, except they all receive gradient updates from all models.

At a high-level:

1. Init a copy of a model on each GPU (make sure to set the seed so each model inits to the same weights or it will fail).

2. Cut the dataset into subsets (with DistributedSampler). Each GPU trains only on its own little subset.

3. On .backward() all copies receive a copy of the gradients for all models. This is the only time the models communicate with each other.

Pytorch has a nice abstraction called DistributedDataParallel which can do this for you. To use DDP you need to do 4 things:

```python
def tng_dataloader():
     d = MNIST()
     
     # 4: Add distributed sampler
     # sampler sends a portion of tng data to each machine
     dist_sampler = DistributedSampler(dataset)
     dataloader = DataLoader(d, shuffle=False, sampler=dist_sampler)
     
def main_process_entrypoint(gpu_nb):
     # 2: set up connections  between all gpus across all machines
     # all gpus connect to a single GPU "root"
     # the default uses env://
     world = nb_gpus * nb_nodes
     dist.init_process_group("nccl", rank=gpu_nb, world_size=world)
     
     # 3: wrap model in DPP
     torch.cuda.set_device(gpu_nb)
     model.cuda(gpu_nb)
     model = DistributedDataParallel(model, device_ids=[gpu_nb])
     
     # train your model now...
     
if  __name__ == '__main__':
     # 1: spawn number of processes
     # your cluster will call main for each machine
     mp.spawn(main_process_entrypoint, nprocs=8)
```

Pytorch team has a [nice tutorial](https://github.com/pytorch/examples/blob/master/imagenet/main.py) to see this in full detail.

However, in Lightning, this comes out of the box for you. Just set the number of nodes flag and it takes care of the rest for you.

```python
# train on 1024 gpus across 128 nodes
trainer = Trainer(nb_gpu_nodes=128, gpus=[0, 1, 2, 3, 4, 5, 6, 7])
```

Lightning also comes with a SlurmCluster manager to easily help you submit the correct details for the SLURM job ([example](https://github.com/williamFalcon/pytorch-lightning/blob/master/examples/new_project_templates/multi_node_cluster_template.py#L103-L134)).

## 10. Bonus! Faster multi-GPU training on a single node

Turns out, that the distributedDataParallel is soooo much faster than DataParallel because the only communication it performs is gradient syncing. So, a good hack is to replace DataParallel with this even when training on a single machine

In Lightning, this is easy to achieve by setting the distributed_backend to **ddp** and setting the number of GPUs.

```python
# train on 4 gpus on the same machine MUCH faster than DataParallel
trainer = Trainer(distributed_backend='ddp', gpus=[0, 1, 2, 3])
```

## Thinking Through Model Speed-Ups

Although this guide will give you a list of tricks to speed up your networks, I’ll explain how I think through finding bottlenecks.

I break up the model into a few parts:

First, I make sure I have no bottlenecks in my data loading. For this I use existing data loading solutions I described, but if none fit what you need, think about offline processing and caching into high-performance data-stores such as h5py.

Next look at what you’re doing in the training step. Make sure your forward pass is fast, avoid excessive computations and minimize data transfer between CPU and GPU. Finally, avoid doing things to slow down the GPU (covered in this guide)

Next, I try to maximize my batch size which will usually be bounded by the amount of GPU memory. From there it’s a game about distributing across GPUs while minimizing latency to effectively use a large batch size (for instance on Imagenet I might try to get an effective batch size of 8,000+ across many GPUs.)

However, you need to be careful with large batch sizes. Consult the literature for your specific problem to see what people have gotten away with!

**Acknowledgments**

Thank you to [Jeff Johnson](https://research.fb.com/people/johnson-jeff/) for awesome CUDA insights, and the Pytorch teams for their help with getting DDP to work (not to mention their awesome framework and documentation). Thanks to testing help from my lab members (especially [Cinjon Resnick](https://deepai.org/machine-learning/researcher/cinjon-resnick)).










