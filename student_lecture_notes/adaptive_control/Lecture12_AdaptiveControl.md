#  Control Theory 
## Lecture 12
## Adaptive control

#### **What is adaptive control system?**
- It is a system that **adapts itself** in presence of uncertainties, using **prior and online** information

#### **Why to use adaptive control?**
- To **estimate unknown parameters** using measured system signals 
- Automatic adjustment of the controllers in **real time**
- To ensure **stable performance** of a system with unknown parameters that change in time
#### **What is different from robust control?**
-  Adaptive control **does not need a priori information** about the bounds of uncertain parameters
-  More concerned about **changing control law**

![](https://i.imgur.com/3GBJASi.png)
###### *Adaptive control system general scheme*


## Adaptive control techniques classification

- **First way**
    * Direct methods
    * Indirect Methods
    * Hybrid Methods

- **Second way**
    * Feedforward adaptive control
    * Feedback adaptive control

### **First way**
![](https://i.imgur.com/ivBI34G.png)
**Direct Method (Explicit Estimation):** 
>1. Directly estimate $θ_c$ as $\hat{θ}_c$. 
>2. Compute the plant estimate $\hat{θ}_p$ using $\hat{θ}_c$.

**Indirect Method (Implicit Estimation):**
>1. Estimate $θ_p$ as $\hat{θ}_p$. 
>2. Compute controller estimate $\hat{θ}_c$ using $\hat{θ}_p$.
>3. Relies on convergence of the estimated parameters to their true unknown values

### **Second way**

**Feedforward adaptive control:** 
![](https://i.imgur.com/XjoSjv4.png)

Let's consider an example:
>$$ \begin{cases} y = Y(\ddot{q},\dot{q},q)\theta \\ u = y \end{cases} \iff H\ddot{q} + c(\dot{q}, q) = u $$

With desired trajectory 
>$$q^{*} = q^{*}(t)$$

Assume $\hat{\theta}$ are precise enough.

Then we can define control 
>$$ u = K_p(q^{*}-q)+K_d(\dot{q}^{*}-\dot{q})+Y(\ddot{q}^{*},\dot{q},q)\theta \\
Y(\ddot{q}^{*},\dot{q},q)\theta = H\ddot{q}^{*} + c(\dot{q}, q)
$$

Stability proof:
>1. Introduce error $e = q^{*} - q$
>2. Choose $K_p = HD_p$ where $D_p$ is positive definite diagonal matrix
>3. Choose $K_d = HD_d$ where $D_d$ is positive definite diagonal matrix
>4.
>$$H\ddot{q}^{*} + c(\dot{q}, q) - u = 0 \\
H\ddot{q}^{*} + c(\dot{q}, q) - K_p(q^{*}-q)-K_d(\dot{q}^{*}-\dot{q})-H\ddot{q}^{*} - c(\dot{q}, q) = 0 \\
H\ddot{e} + K_d\dot{e} + K_p{e} = 0 \\
\ddot{e} + D_d\dot{e} + D_pe = 0$$ 
>The obtained system of second order linear differential equations is independent  with strictly positive coefficients $D_d$ and $D_p$ (due to assumption above). They are stable.



**Feedback adaptive control:** 
![](https://i.imgur.com/mzLTQ3X.png)
Let's consider an example:
>$$\begin{cases}\dot{x} = Ax+Bu\\
y = Cx+Du
\end{cases}$$

where
>$$A = A(\theta)\\
B = B(\theta)$$

Assume $\hat{\theta}$ are precise enough $\implies$ $A$ and $B$ are precise enough

Solve Riccati's equation using $A$ and $B$

>$$\begin{cases}Q − SB(\hat{\theta})R^{−1}B^{T}(\hat{\theta})S + 2SA(\hat{\theta}) = 0 \\
u = −R^{−1}B^{T}(\hat{\theta})Sx \end{cases}$$

Stability can not be guaranteed.

## In order adaptive control to work we need **real-time estimation** of parameters 

We can estimate parameters in real time using a linear feedback law:
$$\frac{d}{dt}\hat{\theta} = \Gamma M^{T} e_{\theta}$$

>$\hat{\theta}$ is a vector of measured or computed data to be modeled. 
The regressor matrix is $M$.
The vector $\theta$ contains the unknown model parameters.
$e_{theta} = y-M\hat{\theta}$ is a vector of parameter estimation output errors.

By definition of parameter estimation error
>$$\varepsilon_{\theta} = \theta - \hat{\theta} \\
\frac{d}{dt}\varepsilon_{\theta} = \frac{d}{dt}\theta - \frac{d}{dt}\hat{\theta}\\
M\theta = y$$

Assume
>$$\frac{d}{dt}\theta = 0$$

Then we get
>$$\frac{d}{dt}\hat{\theta} = \Gamma M^{T}(M(\theta-\varepsilon_{\theta})-y) = \Gamma M^{T}(M\theta-M\varepsilon_{\theta} - M\theta) = -\Gamma M^{T}M\varepsilon_{\theta}$$

It is essential to make obtained dynamics stable ($|-\Gamma M^{T}M|<0$) to get correct estimates.

To achieve this we can simply choose 
>$$\Gamma = D(M^{T}M)^{-1}$$ 

where 
>$$D>0$$

## Where adaptive control is used?

#### Many of applications show that
- adaptive control can be very useful
- such controllers often have to be "tuned" to the specific application 
- it can be advantageous to use an adaptive controller even if the process is time-invariant, since it will result in better tuned regulators 


#### Some occations where it can be the most advantageous to use adaptation
- Systems with long time delays.
- Systems where feedforward can be used. 
- Systems with time varying character of the disturbances (chemical processes).

There are many practical issues that have to be considered when implementing adaptive control, still experience showed not much efforts are required to make a standard adaptive system to work well. 


##### References:
- https://www.researchgate.net/publication/325963748_Real-Time_Parameter_Estimation_for_Flexible_Aircraft
- http://aaclab.mit.edu/material/lect/2_153_Lecture_01.pdf
- https://en.wikipedia.org/wiki/Adaptive_control
- https://link.springer.com/chapter/10.1007%2F978-0-85729-343-5_1
- https://www.researchgate.net/publication/269401168_Adaptive_Control_But_is_so_Simple_A_Tribute_to_the_Efficiency_Simplicity_and_Beauty_of_Adaptive_Control
- http://acl.mit.edu/papers/GNC97.pdf
