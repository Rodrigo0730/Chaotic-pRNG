# Chaotic-pRNG
pRNG based on a version of both the Sine map and the Tent map. The equations for the chaotic system are the following:
```math
f(x_{i+1})= \left\{ \begin{array}{cc} \frac{4 - \mu}{4} * sin(\pi*f(x_{i})) + \frac{\mu}{2} * f(x_{i}) & x \leq 0.5 \\ \\ \frac{4 - \mu}{4} * sin(\pi*f(x_{i})) + \frac{\mu}{2} * (1- f(x_{i})) & x \get 0.5 \end{array} \right.
```
![Figure_2](https://github.com/Rodrigo0730/Chaotic-pRNG/assets/98705189/fa6e6d4b-b597-44f6-9537-b72b01adb638)

