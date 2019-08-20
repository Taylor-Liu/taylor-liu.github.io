---
layout: post
title: Python vs. C++ 高斯分布例子
tags: [code, c++, python]
---

本文主要比较 Python 和 C++ 在编写类(class)时候的不同。

以高斯分布为例。下面是一个名为 “Gaussian” 的 Python 类代码。该类包含两个类变量：平均值 “mu”，以及方差 “sigma2”。

类包括三个函数：

1. `evaluate`, 它表示概率密度函数$$\frac{1}{\sqrt{2 \pi \sigma^{2}}} e^{-\frac{1}{2} \frac{(x-\mu)^{2}}{\sigma^{2}}}$$。在这个公式中，$$\sigma^{2}$$是方差。
2. `multiply`, 它将两个高斯分布相乘。
3. `add`, 它将两个高斯分布相加。

## Gaussian 类的 Python 代码

```python
class Gaussian():

    def __init__(self, mean, variance):
        self.mu = mean
        self.sigma2= variance

    def evaluate(self, x):
        coefficient = 1.0 / sqrt(2.0 * pi *self.sigma2)
        exponential = exp(-0.5 * (x-self.mu) ** 2 / self.sigma2)
        return coefficient * exponential

    def multiply(self, other):
        # 计算新均值
        denominator =self.sigma2+other.sigma2
        numerator = self.mu * other.sigma2 + other.mu * self.sigma2
        new_mu = numerator / denominator

        # 计算新方差
        new_var =1.0/ ( (1.0/self.sigma2) + (1.0/other.sigma2) )

        # 生成新的高斯分布
        return Gaussian(new_mu, new_var)

    def add(self, other):
        new_mu = self.mu + other.mu
        new_sigma2 =self.sigma2+other.sigma2

        return Gaussian(new_mu, new_sigma2)
```

## Gaussian 类的 C++ 代码

现在，来看看 C++ 中的的一个等价类。和你看到的其他例子一样，C++ 代码更长，并且有 Python 版本没有的方面。

例如，你会注意到，在 C++ 类中，所有的变量及其所有的函数都需要在编写实现之前先声明。类还有一部分标记为`private`，另一部分标记为`public`。此外，C++ 类还包括诸如`setMu`、`setSigma2`、`getMu`和`getSigma2`等额外的函数。


```cpp
# include <math.h>

class Gaussian
{
    private:
        float mu, sigma2;

    public:

        // constructor functions
        Gaussian ();
        Gaussian (float, float);

        // change value of average and standard deviation 
        void setMu(float);
        void setSigma2(float);

        //输出平均值和标准差的值
        float getMu();
        float getSigma2();

        //待评估函数
        float evaluate (float);
        Gaussian multiply (Gaussian);
        Gaussian add (Gaussian);
};

Gaussian::Gaussian() {
    mu = 0;
    sigma2 = 1; 
}

Gaussian::Gaussian (float average, float sigma) {
    mu = average;
    sigma2 = sigma;
}

void Gaussian::setMu (float average) {
    mu = average;
}

void Gaussian::setSigma2 (float sigma) {
    sigma2 = sigma;
}


float Gaussian::getMu () {
    return mu;
}

float Gaussian::getSigma2() {
    return sigma2;
}

float Gaussian::evaluate(float x) {
    float coefficient;
    float exponential;

    coefficient = 1.0 / sqrt (2.0 * M_PI * sigma2);
    exponential = exp ( pow (-0.5 * (x - mu), 2) / sigma2 );
    return coefficient * exponential;
}

Gaussian Gaussian::multiply(Gaussian other) {
    float denominator;
    float numerator;
    float new_mu;
    float new_var;

    denominator = sigma2 + other.getSigma2();
    numerator = mu * other.getSigma2() + other.getMu() * sigma2;
    new_mu = numerator / denominator;

    new_var = 1.0 / ( (1.0 / sigma2) + (1.0 / other.sigma2) );

    return Gaussian(new_mu, new_var);
}

Gaussian Gaussian::add(Gaussian other) {

    float new_mu;
    float new_sigma2;

    new_mu = mu + other.getMu();
    new_sigma2 = sigma2 + other.getSigma2();

    return Gaussian(new_mu, new_sigma2);
}
```




























