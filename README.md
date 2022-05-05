# Evaluate all the real zeros of a given polinomial equation with real coefficients
_Alessandro Maggioni, Riccardo Moraschi, Paola Plebani_

**Idea of the solution**: Analyze recursively the derivates of the function till reaching a second degree equation

**Then**: Compare the results given by this implementation with those obtained with STURM sequences.

## Solution with recursive analysis of derivatives
For example, if we have the equation

<img src="https://render.githubusercontent.com/render/math?math= x^4 - x^3 - x^2 - x + 1 = 0">

