---
title: 'A short introduction to optimal control - In preparation !'
date: 2020-05-20
permalink: /posts/2020/05/optimal-control/
tags:
  - optimal
  - control
---
What is optimal control ?
======
Okay let's give a short answer : in general you have **3 features** that you monitor: 
- **A state of a system**, denoted $X$,
- **A control** $\alpha$ over $X$,
- **A Loss criterion** $J$, that you want to minimize/maximize, (it could be a maximization criterion) 
And your goal is simple : you want to find the best control $\alpha$ over $X$ so that you minimize your cost $J$. 

Euh... Show some examples !
======
First let's give a toy example : 
Assume you are an eagle. You are hungry. You want to eat. So you are seeking a prey to get close to. Here your **state** is your position in space $X \in \mathbb{R}^3$. Your **control** $\alpha$ is your speed, so $\frac{d X_t}{dt} = \alpha_t$ or as we prefer to write $X_t = X_0 \int_0^t \alpha_s ds$ with $X_0$ being your initial position. Sundenly a moving prey appears, its position is $P_t$. Now since you want to get close to this beautiful prey, you decide that your loss criterion to minimize will be something like \\[ \int_0^T \lambda(X_t - P_t)^2 + N\alpha_t^2 dt + X_T^2  \\]. 

Let's see another example closer to the real world 
Assume you have a solar panel above your home. This solar panel is linked to a battery that you can charge or discharge. Everyday you need some electricity that you can either get from your electrical outlet or from your battery (that you hope is charged when you need it). Of course every month you pay the electricity you get from the electrical outlet. So your goal is to minimize your bill at the end of the month thanks to to your (solar panel, battery). So Here we have :
- **A system (the battery)** whose state $X$ is the ammount of electricity inside it,
- **A control** $\alpha$ over the quantity of electricity $X$ (you can charge or discharge the battery),
- **A loss criterion** $J$ that is the bill at the end of the month.

Ok so... What do we want ? 
======

Nice how do I get it in general?
======

Can you solve the problem explicitely ?
======


This is a sample blog post. Lorem ipsum I can't remember the rest of lorem ipsum and don't have an internet connection right now. Testing testing testing this blog post. Blog posts are cool.




Aren't headings cool?
------
