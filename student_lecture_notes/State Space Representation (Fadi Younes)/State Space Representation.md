## State Space Representation

Fadi Younes

a state space representation is a linear representation of a dynamic system either in a continuous or discrete form.

The most general time-continuous linear dynamic system has the
following form:
$$
\dot{x}(t) = A(t)x(t)+ B(t)u(t)\\
y = C(t)x(t)+ D(t)u(t)
$$
where:
$t$ denotes time
the first equation is called the *state equation* and the second is called the *output equation*
$x(t)$ is the state vector, $u(t)$ is the input vector, and $y(t)$ is the output vector

Note: $x(t)$ is called the state vector because:

- Future output depends **only** on current state and future input
- Future output depends on past input **only** **through** current state
- State summarizes effect of past inputs on future output (like the memory of the system)

$A,B,C$ and $D$ are matrices where:
$A(t)$ is the dynamics matrix
$B(t)$ is the input matrix
$C(t)$ is the output matrix
$D(t)$ is the feedthrough matrix

### What are the  state variables?

the minimum set of variables that fully describe (enough information to predict the future behavior) the system.

The first step of representing a system is to select a state vector, which needs to be chosen according to the following:
1- A minimum number of state variables must be selected as components of the state vector.

How do we know what is the **minimum number**?
The minimum number is the order of the differential equation describing the system. 
If we have a TF (transfer function) the the minimum number is the order of the denominator of the transfer function after canceling common factors in the numerator and denominator

2- The minimum number of state variables must be **linearly independent**.

### Converting from state-space to a transfer function

as the above representation of the state space: 
$$
\dot{x}(t) = A(t)x(t)+ B(t)u(t)\\
y = C(t)x(t)+ D(t)u(t)
$$
we take the Laplace transformation (integral transform that converts a function of a real variable (time here) to a function of a complex variable):
$$
sX(s) = AX(s)+ BU(s)\\
Y(s) = CX(s)+ DU(s)
$$
then solving for $X(s)$:
$$
X(s)= (sI-A)^{-1}BU(s)
$$
where $I$ is the identity matrix.

Then, substituting this equation into $Y(s)$ equation above we get:
$$
Y(s) = [C(sI-A)^{-1}B+D]U(s)
$$
and this is the transfer function we have for our state space representation.

### How do we benefit from state-space representation?

**1- Stability**
the state space model is **stable** if all eigenvalues of the matrix $A$ are negative real numbers or the real part of the complex eigenvalues are negative. If at least one **eigenvalue** has a positive real part, then the system is unstable.

**2- Controllability**

A continuous time-invariant linear state-space model is **controllable** if and only if:
$$
{\displaystyle \operatorname {rank} {\begin{bmatrix}\mathbf {B} &\mathbf {A} \mathbf {B} &\mathbf {A} ^{2}\mathbf {B} &\dots &\mathbf {A} ^{n-1}\mathbf {B} \end{bmatrix}}=n}
$$
where rank is the number of linearly independent rows in a matrix, and where $n$ is the number of state variables.

**3- Observability**

A continuous time-invariant linear state-space model is **observable** if and only if:
$$
{\displaystyle \operatorname {rank} {\begin{bmatrix}\mathbf {C} \\\mathbf {C} \mathbf {A} \\\vdots \\\mathbf {C} \mathbf {A} ^{n-1}\end{bmatrix}}=n.}
$$
2- Can be applied to a non-linear system

3- Can be applied to time invariant systems

4- Can be applied to multiple input multiple output systems known as (MIMO) systems.

### References

1-https://www.engbookspdf.com/uploads/pdf-books/ControlSystemsEngineering7thEditionbyNise-1.pdf

2-http://www.circuitstoday.com/state-space-analysis

3-https://ocw.mit.edu/courses/aeronautics-and-astronautics/16-30-feedback-control-systems-fall-2010/lecture-notes/MIT16_30F10_lec05.pdf

4-https://www.youtube.com/watch?v=hpeKrMG-WP0&t=331s





