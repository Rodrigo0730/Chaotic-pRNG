# Chaotic-pRNG
This repository proposes a chaos-based pRNG which has passed NIST tests. The pRNG combines two chaotic systems: the Sine map and the Tent map.
Lets take a look at the chaotic properties of this two maps by looking at the Bifurcation diagrams of each. <br>
- Sine map:
```math
g(x_{i+1}) = \frac{4 - \mu}{4} * sin(\pi*g(x_{i}))
```
<p align="center">
<img src="https://github.com/Rodrigo0730/Chaotic-pRNG/assets/98705189/003cefe6-64f3-40e0-88bc-fe7013ba0640" width=500px height=350px >
</p>

- Tent map:
```math
h(x_{i+1}) = \left\{ \begin{array}{lc} \frac{\mu}{2} * f(x_{i}) & x < 0.5 \\ \\ \frac{\mu}{2} * (1- f(x_{i})) & x \ge 0.5 \end{array} \right.
```
<p align="center">
<img src="https://github.com/Rodrigo0730/Chaotic-pRNG/assets/98705189/a173d91e-d588-4822-8ce1-96ab0ade7a21" width=500px height=350px >
</p>
<br>
Putting this together we get splendid results. We define $f(x_{i}) = g(x_{i}) + h(x_{i})$ to define the Sine-Tent map. The equations of this chaotic system are the following:

```math
f(x_{i+1})= \left\{ \begin{array}{lc} \frac{4 - \mu}{4} * sin(\pi*f(x_{i})) + \frac{\mu}{2} * f(x_{i}) & x < 0.5 \\ \\ \frac{4 - \mu}{4} * sin(\pi*f(x_{i})) + \frac{\mu}{2} * (1- f(x_{i})) & x \ge 0.5 \end{array} \right.
```
The following plots show the chaos this system exhibits. The first plot shows the Lyapunov exponent of the system depending on the value of $\mu$. The second plot is the bifurcation diagram for the Sine-Tent map, a good exercise is to compare it with the other bifurcation diagrams from above.

<img src="https://github.com/Rodrigo0730/Chaotic-pRNG/assets/98705189/eb7ea66b-e7f9-4504-9c04-a067d006e82b" width=500px height=350px>
<img src="https://github.com/Rodrigo0730/Chaotic-pRNG/assets/98705189/f8432799-273e-4f04-97ae-4152859c71aa" width=500px height=350px>

<p><strong>Explanation of the code:</strong></p>
<p><strong>pRNG CLASS:</strong></p>
<p>

- <p>__init__(self):</p> 
Initializes the class instance with predefined "safe" parameter values used for generating sequences. 
- <p>sine_tent_map(self, x, mu):</p> 
Computes the next value in the sequence using the sine-tent map formula based on the input value x and parameter mu.
- <p>generate_sequence(self, x_initial, mu, num_iterations): </p>
Generates a sequence of values using the sine-tent map.
Starts from x_initial and iterates num_iterations times to generate the sequence.
- <p>generate_bit_sequence(self, x_initial, mu, num_iterations=8000):</p>
Generates a sequence of binary bits (0s and 1s) using the sine-tent map.
Converts the fractional parts of the generated values into bits.
The number of iterations can be adjusted, and the default is set to 8000.
- <p>bits_to_bytes(self, bit_sequence): </p>
Converts a sequence of binary bits into a bytes object.
Randomly selects a bit from each bit sequence element to form bytes.
- <p>generate_bytes(self, x_initial, mu, num_iterations, num_bytes): </p>
Generates random bytes using the generate_bit_sequence method and converts them to bytes.
The number of iterations and the desired number of bytes can be specified.
- <p>generate_key(self, length): </p>
Generates a random key of the specified length in bytes using the generate_bytes method.
- <p>run_tests(self): </p>
Demonstrates how to run statistical tests on the generated bit sequence.
Generates a bit sequence and checks eligibility for various NIST SP800-22 tests.
Runs eligible tests and prints the results, indicating whether each test passed or failed.
<p><strong>Addition: (Commented-Out) Visualization Methods:</strong></p>
The code also includes commented-out sections that provide code for generating plots to visualize the behavior of the sine-tent map, Lyapunov exponent, and bifurcation diagrams. These where used for the generation of the plots from above.
</p>

NIST tests:
The tests were run using the Nistrng library. https://pypi.org/project/nistrng/ <br>
The code does not fail any of the tests, although it fails the Random excursion test. Notice that this test have a high computational cost to run as they need lots of data (over 1000000 and the test were run with 1000 iterations) to be passed The variant of this test does pass as it can be seen below. <br>
<p align="center">
<img src="https://github.com/Rodrigo0730/Chaotic-pRNG/assets/98705189/edc4956a-0d55-4f84-a582-969e7a0bab67" width=700px height=400px>
</p>




