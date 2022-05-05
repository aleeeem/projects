# Evaluate all the real zeros of a given polinomial equation with real coefficients
_Alessandro Maggioni, Riccardo Moraschi, Paola Plebani_


**Idea of the solution**: Analyze recursively the derivates of the function till reaching a second degree equation

**Then**: Compare the results given by this implementation with those obtained with STURM sequences.

## Solution with recursive analysis of derivatives

First of all, we extract the coeffiecients of a polynomial in a Numpy array with ```get_list_from_function```. If the polynomial is of a **first** or **second degree**, the common formulas are implemented, with the functions: ```first_deg_eq``` e ```solutions_poly_second_degree```. In the other cases, we use the follow strategy with the extractions of all usefull derivatives. 

For example, if we have the equation ![Figure](https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;x^4-x^3-x^2-x+1=0) the result of the fuction ```all_derivative``` is 

<img src="https://latex.codecogs.com/png.image?\dpi{110}&space;\bg_white&space;\left[\begin{array}{ccccc}1&-1&-1&-1&1\\0&4&-3&-2&-1\\0&0&12&-9&-2\\\color{red}0&\color{red}0&\color{red}0&\color{red}{24}&\color{red}{-9}\\\color{red}0&\color{red}0&\color{red}0&\color{red}0&\color{red}{24}\end{array}\right]">

The red lines are not calculated by the fuction because they are not necessary, due to the definition of ```solutions_poly_second_degree```.
