# Chaotic-pRNG
pRNG based on a version of both the Sine map and the Tent map. The equations for the chaotic system are the following:
```math
f(x_{i+1})= \left\{ \begin{array}{lc} \frac{4 - \mu}{4} * sin(\pi*f(x_{i})) + \frac{\mu}{2} * f(x_{i}) & x < 0.5 \\ \\ \frac{4 - \mu}{4} * sin(\pi*f(x_{i})) + \frac{\mu}{2} * (1- f(x_{i})) & x \ge 0.5 \end{array} \right.
```
The following plots show the chaos this system exhibits. The first plot shows the Lyapunov exponent of the system depending on the value of $\mu$. The second plot is the bifurcation diagram for the Sine Tent map.
![Sine_tent_map_BD](https://github.com/Rodrigo0730/Chaotic-pRNG/assets/98705189/eb7ea66b-e7f9-4504-9c04-a067d006e82b){height="100px" width="100px"}
![Lyapunov_vs_Mu](https://github.com/Rodrigo0730/Chaotic-pRNG/assets/98705189/f8432799-273e-4f04-97ae-4152859c71aa)


