# LQR Control Lecture Notes

#### Selina Varouqa | BS18-02 | Control Theory Spring 2020 | Innopolis University



### Overview

------

LQR Control or (**L**inear **Q**uadratic **R**egulator) is a type of **optimal control** (finding a control law for some system such that a certain optimality criterion is achieved) that is based on **state-space representation** (mathematical model as a set of input, output and state variables related by first-order differential equations (*continuous*) or difference equations (*discrete*)). In other words, LQR is a control scheme that gives the best possible performance with respect to a given measure of performance. 

The LQR design problem is to **design a state feedback controller such that the objective function is minimized**. Before getting to the mathematical side, let us answer some questions for better understanding:

- What is an objective function?

  mathematically, it describes how different variables contribute to a certain value that is being sought to be optimized. In LQR, it is referred to as a **cost function**, and the cost function is a type of objective functions.

- Why do we need to optimize the objective function?

  to achieve some compromise between the use of control effort, the magnitude, and the speed of response that will guarantee a **stable system**

- So, again, why **LQR**, it is (**L**inear **Q**uadratic **R**egulator) but what does it mean?

  **L :** the system dynamics are described by a set of **linear** differential equations

  **Q :** the cost function is a **quadratic** function

  **R :** it is a regulator, hence it provides optimally controlled feedback



### LQR Calculations

------

Suppose that a **time-continuous** *linear* system is described by:

$$ \dot{x}(t) = Ax(t)+ Bu(t)$$ 			$$,x(t_{0}) = x_{0}$$

and if a continuous object is to represented by a system of matrix equations:

$$\dot{x}(t) = Ax(t)+ Bu(t)$$

$$y(t) = Cx(t)+ Du(t)$$

where matrix $A$ is the state matrix, $B$ is the input matrix, $C$ is the control matrix, $D$ is the feedforward matrix, $x(t)$ is called the state vector, $u(t)$ is the input vector ,and $y(t)$ is the output vector. 

> *note: if you have any confusion so far, please read more about state-space representation.*


As the cost function is often defined as a sum of the deviations of key measurements, the criterion of optimality of LQR control is to make this cost function as minimized as possible, the cost function of LQR would be the following:

$$ J = \int(x^TQx+ u^TRu)dt$$ 

where $Q$ and $R$ are symmetric positive semi-definite matrices using the state vector $x$ and the input vector $u$. One practical method is for Q and R to be diagonal matrices. In terms of what is happening, matrix $Q$ penalizes bad performance, and matrix $R$ penalizes effort.

The feedback control law that minimizes the cost function $J$  would be: 

$u = -Kx$

where $K = R^{-1}B^TP$ , then the question that comes, where do we get $P$ from? $P$ can be found by solving the **time-continuous** algebraic Ricatti equation:

$A^TP + PA - PBR^{-1}B^TP+Q = 0$

So, our goal is to design state feedback controller $K$ such that the cost function $J$ is minimized.



### LQR using MATLAB

------

Let us assume that our control object has the following transfer function:

$TF = \frac{1}{7s^2 + 2s + 4}$

then our code to calculate K would be as following:

```matlab
nom = 1
den = [7 2 4]
transfer = tf(nom, den)
[A,B,C,D] = tf2ss(nom, den)
Q = diag([1,1])
R = 0.1 * diag([1])
K =lqr(A,B,Q,R)
```



### How to Design with LQR?

------

1- Develop a linear model: $$\dot{x}(t) = Ax(t)+ Bu(t)$$

​												$$y(t) = Cx(t)+ Du(t)$$ 

2- Adjust Q and R 

Note: one practical way is to pick them to be diagonal matrices and then tweak them according to the knowledge of the system.

3- Find the optimal gain set

```matlab
K = lqr(A,B,Q,R)
```

4- Simulate the response and then adjust Q and R again if necessary

------



> ### References:
>
> 1- https://www.mathworks.com/videos/state-space-part-4-what-is-lqr-control-1551955957637.html
>
> 2- https://reader.elsevier.com/reader/sd/pii/S1877050919303503?token=08EBB4D061447B8F6BC27C7A2F894BF659ECFDBF321179D5D3FAC4DAB0E3CB8C425224527722099C2661C013981471BA
>
> 3- http://eprints.uthm.edu.my/id/eprint/4726/1/NOR_AKMAL_BINTI_ALIAS.pdf
>
> 4- https://sites.math.rutgers.edu/~sontag/FTPDIR/sontag_mathematical_control_theory_springer98.pdf
>
> 5- https://homes.esat.kuleuven.be/~maapc/static/files/CACSD/Slides/chapter4.pdf

