---
title: 'A short introduction to optimal control - In preparation !'
date: 2020-05-20
permalink: /posts/2020/05/optimal-control/
tags:
  - optimal
  - control
---
This is a very non-mathematical and straightforward presentation of what is optimal control. The goal is to see :
1. What it is mainly about,
2. Some ideas to solve the problems we are about to see. 

To convey the main ideas, as briefly as possible, I will present the minimum package to understand the main ideas. Have some mercy for my informal tone and my lack of precision, I like it this way because it allows our imagination to fill the gaps and go further ;)

So...what is optimal control ?
======
Okay let's give a short answer : *You have a thing/system which is moving with time and over which you have a control. Your goal is then to choose the best control in order to minimize a cost*. In general you have **3 features** that you monitor : 
- **A state of a system**, denoted $X$,
- **A control** $\alpha$ over $X$,
- **A Loss criterion** $J$ that you want to minimize.

Your goal is simple : you want to find the best control $\alpha$ over $X$ so that you minimize your cost $J$. So classically we first define a model other the system :  
\\[ X_t = x + \int_0^t b(s, X_s, \alpha_s)ds, \qquad t \in [0, T], \label{eq:dynamic} \\]
where $b$ is a given model. And a loss criterion that we want to minimize
\\[J(t,x,\alpha) = \int_t^T f(X_s, \alpha_s)ds + g(X_T).\\]
The number $J(t,x,\alpha)$ is to be interpreted as *the total ammount you will pay if, on $[t,T]$, you implement the strategy $\alpha$ when your state start at $X_t=x$*. To sum up, what you have to do is simple 
1. Define a **model** of your system, ie : $(t, x,\alpha) \mapsto b(t, x,\alpha)$,
2. Define a **loss criterion** $(t,x,\alpha) \mapsto J(t,x,\alpha)$,
3. **Solve the minimization** problem $ V(t,x)= \inf_{\alpha} J(t,x,\alpha)$.

Note here the introduction of a new function : the **value function** $V$. Basically, $V(t,x)$ tells you how much you are going to pay if, starting from $x$ at time $T$, you apply until the end an optimal strategy $\alpha^\star$ (we like to put stars on things that are optimal : $\alpha^\star$ denotes an optimal strategy, so that $V(t,x)=J(t,x,\alpha^\star)$). 

Euh... can you give me some examples ?
======
__First a toy example : An eagle an a bird__ 

Assume you are an eagle. You are hungry. You want to eat. So you are seeking a prey to get close to. Here your **state** is your position in space $X \in \mathbb{R}^3$. Your **control** $\alpha$ is your speed, so **the model of your system** is $\frac{d X_t}{dt} = \alpha_t$ with $x$ being your initial position. Or as we prefer to write 
\\[X_t = x + \int_0^t \alpha_s ds. \\]
Sundenly a moving prey appears, its position is $P_t$. Now here is the thing. You want to get close to this beautiful prey, but it is costly for you to go fast, so you decide that your **loss criterion** to minimize will be something like 
\\[\int_0^T \left(\lambda(X_t - P_t)^2 + N\alpha_t^2 \right) dt + X_T^2,\\] 
where $\lambda$ and $N$ are given constants. As you can see, the bigger $\lambda$ is, the more you want to get close to your prey (you *penalize* the fact of being far from it); the bigger $N$ is, the more it costs you to go fast. That's it ! We have defined a **model**, **loss criterion** and the only things that remains to do is to **solve the minimization** problem ! (See below)

__Another example closer to the real world : Controlling a battery linked to a solar panel and a grid__ 

Assume you have a solar panel above your home. This solar panel is linked to a battery that you can charge or discharge. Everyday you need some electricity that you can either get from your electrical outlet or from your battery (that you hope is charged when you need it). So we have the following situation : 

<img src="https://enzoMiller.github.io/images/control_battery.jpg" width="400">

Of course every month you pay the electricity you get from the electrical outlet. So your goal is to minimize your bill at the end of the month thanks to to your *solar panel & battery*. So Here we have :
- **A system (the battery)** whose state $X$ is the ammount of electricity inside it,
- **A control** $\alpha$ over the quantity of electricity $X$ (you can charge or discharge the battery),
- **A loss criterion** $J$ that we define the bill at the end of the month.
Okay let's be more precise now.  As a simple first appraoch to the problem (for a more sophisticated model you can check this [post](https://enzomiller.github.io/posts/2020/06/stochastic-control-storage-deep-learning/)) we could propose for the **model**:
\\[ dX_t = \alpha_t dt, \qquad X_t \in [0, B_{max}], \alpha_t \in [-1, 1] .\\]
Here $X$ is the ammount of energy inside your battery (unit $J$) and $\alpha$ is the ammount of energy per unit of time you are putting into the battery ($\alpha>0$ : you are charging the battery, $\alpha<0$ you are discharging it).



If you're intersted to see a real implementation of this kind of stuff with neural nets and amore realistic model you can go [there](https://enzomiller.github.io/posts/2020/06/stochastic-control-storage-deep-learning/) ! 

Ok so... What do we want ? 
======
Basically 2 things : you want the optimal control $\alpha^*$ and the price you're going to pay (i.e. the value fonction $(t,x) \mapsto V(t,x)$.)

Nice how do I get it in general ?
======

Can you solve the problem explicitly ?
======
Usually no, in generak we don't have any explicit formulas for the optimal control $\alpha^*$ or the value $(t,x) \mapsto V(t,x)$ of the problem. But in some cases we do have explicit formulas ! The most classical one is the linear quadratic case where the **model** is of the form : 
\\[ d X_t = (A X_t + B X_t) dt. \\]
and the **cost criterion**  : 
\\[J(t,x,\alpha) = \int_t^T Q X_s^2 + N \alpha_s^2 ds + P X_T^2, \\]
were $A,B,Q,N$ could be real numbers, matrices, [linear operator](https://mathworld.wolfram.com/LinearOperator.html), etc.
As you may have noticed the **eagle & bird** problem has this kind of structure, so let's solve it !

<details>
  <summary> <h1> Click to expand! </h1></summary>
  
  ## Heading
  1. A numbered
  2. list
     * With some
     * Sub bullets
</details>
