# Evaluate all the real zeros of a given polinomial equation with real coefficients
_Alessandro Maggioni, Riccardo Moraschi, Paola Plebani_


**Idea of the solution**: Analyze recursively the derivates of the function till reaching a second degree equation

**Then**: Compare the results given by this implementation with those obtained with STURM sequences.

## Solution with recursive analysis of derivatives

First of all, we extract the coeffiecients of a polynomial in a Numpy array with ```get_list_from_function```. If the polynomial is of a **first** or **second degree**, the common formulas are implemented, with the functions: ```first_deg_eq``` e ```solutions_poly_second_degree```. In the **other cases**, we use the follow strategy with the extractions of all usefull derivatives. 

For example, if we have the equation ![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;x^4-x^3-x^2-x+1=0) the result of the fuction ```all_derivative``` is 

<img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;\left[\begin{array}{ccccc}1&-1&-1&-1&1\\0&4&-3&-2&-1\\0&0&12&-9&-2\\\color{red}0&\color{red}0&\color{red}0&\color{red}{24}&\color{red}{-9}\\\color{red}0&\color{red}0&\color{red}0&\color{red}0&\color{red}{24}\end{array}\right]">

The red lines are not calculated by the fuction because they are not necessary, due to the definition of ```solutions_poly_second_degree```.

In order to determinate the real roots of 

<img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;f\in\mathbb{P}_n\%20\text{s.t.}\%20n>2">

we find its critical points <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;x_1,\dots,x_{m}">. In fact, between two successive critical points <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;x_{i}"> and <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;x_{i+1}"> there is at most one real root, due to the fact that in <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;[x_i,x_{i+1}]"> <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;{f}"> is continuous and monotonic. Hence, we apply bisection method on intervalls defined between two succesive critical points <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;x_{i}">, <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;x_{i+1}"> in which <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;f(x_i)\cdot%20f(x_{i+1})<0">.

To obtain the value of the critical points, we resolve 

<img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;{f'(x)=0}"> 

where <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;f'\in\mathbb{P}_{n-1}">.

We repeate this process until reaching a second degree equation, solved with the formula 

<img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;x_{1,2}=\frac{-b\pm\sqrt{b^2-4ac}}{2a}">

In this way, we defined a recursive algorithm: ```solve_equation```. In this function, in order to avoid unusefull checks, we distinguish between polynomials with even or odd degree. In fact, an even polynomial can have no root, when all critical points <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;x_i"> have got <img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;{\forall%20i:f(x_i)>0}">. 
