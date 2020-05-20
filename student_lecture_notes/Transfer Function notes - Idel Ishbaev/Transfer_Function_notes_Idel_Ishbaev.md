# Transfer functions (notes)\
#### by Idel Ishbaev, group 1\
## Introduction:\
Transfer function: Laplace Transform of the impulse response of an LTI system when initial conditions = 0\
\
#### Definition from book:\
*The transfer function of a linear, time-invariant, differential equation system is defined as the ratio of the Laplace transform of the output (response function) to the Laplace transform of the input (driving function) under the assumption that all initial conditions are zero.*\
#### Simple representation:\
![](https://i.imgur.com/UQ7TBQU.png =200x)\
![](https://i.imgur.com/MN24uVw.png =200x)\
\
### Practical usage\
A transfer function is a mathematical model of a system that maps it\'92s input to its output (or response). If the system is a linear time-invariant (LTI) dynamical system, then this function can take a very general form.\
\
**In general**, a transfer function describes the relationship between the input to a system to the output from that system. It gives you a way to mathematically analyze the behavior of a physical system.\
* You can analyze a system mathematically without implementing physical system and measuring it. You can infer the system's behaviour over a wide range of inputs all on paper or in simulation.\
* On the other hand, you can design system mathematically based on its required behaviour by first constructing the desired transfer function, and then working backward to a physical realization of that design\
\
### Methods of Obtaining a Transfer Function\
There are major two ways of obtaining a transfer function for the control system. The ways are:\
\
#### Block Diagram Method: \
It is not convenient to derive a complete transfer function for a complex control system. Therefore the transfer function of each element of a control system is represented by a block diagram. Block diagram reduction techniques are applied to obtain the desired transfer function.\
#### Signal Flow Graphs: \
The modified form of a block diagram is a signal flow graph. Block diagram gives a pictorial representation of a control system. Signal flow graph further shortens the representation of a control system.\
### From ODE to TF\
 \
$$ 3\\ddot\{x\}  + 56 \\dot\{56\} - 7x = u -> 3d^2 /dt^2 + 56dx/dt - 7x = u$$ \
Lets differentiate $$ p = d/dt : 3p^2x+56px -7x = u$$\
$$ (3p^2 + 56p -7)x=u -> x1/(3p^2 + 56p - 7)u $$\
if we denote $$ W(p)= 1/(3p^2+56p-7) $$\
Transfer funstion representation: $$ x = W(p)*u $$ \
\
### From State space to TFs\
![](https://i.imgur.com/FBpoVnW.png =150x) ![](https://i.imgur.com/PC0fWCP.png =150x) ![](https://i.imgur.com/s9pKZZG.png =150x)\
![](https://i.imgur.com/5TtOXP2.png =150x)![](https://i.imgur.com/yxX7lq1.png =150x) ![](https://i.imgur.com/YW5GNka.png =150x)\
\
### Advantages and disadvantages of TF\
+ Popular and used in many cases\
+ A lot of study material\
+ Easy to visual representation\
+ Can access stability of the system knowing its TF\
+ Frequency response of a SISO is easier to study with TF.\
- Does not work for complex systems\
- Replacement with numeric tools can be faster and easier\
- Easy to make mistake without knowing details\
\
#### Video Material for better understanding:\
https://www.youtube.com/watch?v=RJleGwXorUk&list=PLUMWjy5jgHK1NC52DXXrriwihVrYZKqjk&index=6&t=0s\
#### References:\
https://www.quora.com/What-is-the-practical-use-of-a-transfer-function\
https://www.electrical4u.com/transfer-function/\
https://en.wikipedia.org/wiki/Transfer_function\
Book: Modern Control Engineering 5th ed. by Katsuhiko Ogato}
