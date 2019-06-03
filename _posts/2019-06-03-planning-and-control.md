---
layout: post
title: Planning and Control in Self-Driving Cars
---

Illustration of the hierarchy of decision-making processes. A destination is passed to a route planner that generates a route through the road network. A behavioral layer reasons about the environment and generates a motion specification to progress along the selected route. A motion planner then solves for a feasible motion accomplishing the specification. A feedback control adjusts actuation variables to correct errors in executing the reference path.