---
title: 'Deep Learning and Stochastic Control - In preparation !'
date: 2020-06-05
permalink: /posts/2020/06/stochastic-control-storage-deep-learning/
tags:
  - optimal
  - stochastic
  - control
  - deep learning
  - battery
  - storage
---

Here I'll explain how to mix deep learning and stochastic control. 
I'll use a work that I did with [EDF](https://en.wikipedia.org/wiki/%C3%89lectricit%C3%A9_de_France) (a French energy company) to illustrate the algorithm on a concrete exemple.


Assume you have a solar panel above your home. This solar panel is linked to a battery that you can charge or discharge. Everyday you need some electricity that you can either get from your electrical outlet or from your battery (that you hope is charged when you need it). So we have the following situation : 

<img src="https://enzoMiller.github.io/images/control_battery.jpg" width="400">

Of course every month you pay the electricity you get from the electrical outlet. So your goal is to minimize your bill at the end of the month thanks to to your *solar panel & battery*. So Here we have :
- **A system (the battery)** whose state $X$ is the ammount of electricity inside it,
- **A control** $\alpha$ over the quantity of electricity $X$ (you can charge or discharge the battery),
- **A loss criterion** $J$ that we define the bill at the end of the month.
Okay let's be more precise now.  As a simple first appraoch to the problem we could propose for the **model**:
\\[ dX_t = \alpha_t dt, \qquad X_t \in [0, B_{max}], \alpha_t \in [-1, 1] .\\]
Here $X$ is the ammount of energy inside your battery (unit $J$) and $\alpha$ is the ammount of energy per unit of time you are putting into the battery ($\alpha>0$ : you are charging the battery, $\alpha<0$ you are discharging it).
