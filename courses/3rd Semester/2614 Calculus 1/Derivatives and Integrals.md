- The derivative of a constant is 0 $$\frac{d}{dx}c = 0$$
- The derivative of `c*f(x) = cf'(x)` $$\frac{d}{dx}cf(x) = c\frac{d}{dx}f(x) = c \cdot f'(x) $$
- The derivative of a sum of a number of functions is the sum of the derivative of those functions
	- $$\frac{d}{dx}(f_1(x)+f_2(x)\dots) = f_1'(x) + f_2'(x) + \dots$$
- **Product Rule** - The derivative of `uv` is `uv' + vu'`
	- $$\frac{d}{dx}uv = u \frac{dv}{dx} + v\frac{du}{dx}$$
- **Quotient Rule** - The derivative of `u/v` is `(vu' - uv')/v^2`
	 - $$\frac{d}{dx}\frac{u}{v} = \frac{v\frac{du}{dx} - u\frac{dv}{dx}}{v^2}$$
- **Chain Rule** - The derivative of a function `u^n` is `n*u^(n-1) * u'`
	 - $$\frac{d}{dx}cf(g(x)) = c \cdot f'(g(x)) \cdot g'(x)$$
**Differentials**
 - They are not taken with respect to any variable
 - Every time a variable itself is differentiated, its prefixed with d
**Logarithmic differentiation**
 - Take the natural logarithm of both sides of an equation then differentiate implicitly with respect to x.

# Trigonometry
 - **Theorem on Limits**
 $$
 \begin{align}
 \lim_{x \to 0} {\frac{sin(x)}{x}} = 1 \text{ and } \lim_{x \to 0} {sin(x)} = 0 \\
 \lim_{x \to 0} {\frac{1-cos(x)}{x}} = 0 \text{ and } \lim_{x \to 0} {cos(x)} = 1
 \end{align}
 $$
 - **Derivatives of Trigonometric Functions**
 $$
 \begin{align}
 \frac{d}{dx}sin(u) &= cos(u) * u' \\
 \frac{d}{dx}cos(u) &= -sin(u) * u' \\
 \frac{d}{dx}tan(u) &= sec^2(u) * u' \\
 \frac{d}{dx}csc(u) &= -csc(u)cot(u) * u'\\
 \frac{d}{dx}sec(u) &= sec(u)tan(u) * u' \\
 \frac{d}{dx}cot(u) &= -csc^2(u) * u' \\
 \end{align}
 $$
 - **Derivatives of Inverse trigonometric functions**
$$
\begin{align}
\frac{d}{dx}sin^{-1}(u) &= \frac{1}{\sqrt{1-u^2}} * u' \\
\frac{d}{dx}cos^{-1}(u) &= -\frac{1}{\sqrt{1-u^2}} * u' \\
\frac{d}{dx}tan^{-1}(u) &= \frac{1}{1+u^2} * u' \\
\frac{d}{dx}csc^{-1}(u) &= -\frac{1}{|u| \sqrt{u^2-1}} * u' \\
\frac{d}{dx}sec^{-1}(u) &= \frac{1}{|u| \sqrt{u^2-1}} * u' \\
\frac{d}{dx}cot^{-1}(u) &= -\frac{1}{1+u^2} * u' \\
\end{align}
$$


 - **Derivatives of Logarithmic and Exponential Functions**
	$$
	\begin{align}
	& \text{the derivative of a exponential function is the ff: where $c$ is a constant and $u$ is a function of $x$} \\
	& \frac{d}{dx}c^u = c^u ln(c)\frac{du}{dx} \\\\
	
	& \text{note that if the constant is $e$ and the exponent is $x$ we get} \\
	& \frac{d}{dx}e^x = e^x \\
	& \text{since $ln(e) = 1$ and $\frac{dx}{dx} = 1$} \\\\
	
	& \text{the derivative of a logarithmic function is the ff:} \\
	& \frac{d}{dx} \log_{c} {u} = \frac{1}{uln(c)} \frac{du}{dx} \\\\
	
	& \text{with this, the derivative of $ln(u)$ is $\frac{u'}{u}$ because $ln(u) = log_e(u)$} \\
	& \frac{d}{dx}ln(u) = \frac{d}{dx}log_e(u) = \frac{1}{uln(e)} \frac{du}{dx} = \frac{u'}{}
	\end{align}
	$$


- **Derivatives of Hyperbolic functions**
$$
\begin {align}
\frac{d}{dx} sinh(u) &= cosh(u) \cdot u' \\
\frac{d}{dx} cosh(u) &= sinh(u) \cdot u' \\
\frac{d}{dx} tanh(u) &= sech^2(u) \cdot u' \\
\frac{d}{dx} csch(u) &= -csch(u)coth(u) \cdot u' \\
\frac{d}{dx} sech(u) &= -sech(u)tanh(u) \cdot u' \\
\frac{d}{dx} coth(u) &= -csch^2(u) \cdot u' \\
\end{align}
$$
- **Derivative of the inverse of hyperbolic functions**
$$
\begin{align}
\frac{d}{dx}sinh^{-1}(u) &= \frac{u'}{\sqrt{1+u^2}} \\
\frac{d}{dx}cosh^{-1}(u) &= \frac{u'}{\sqrt{u^2-1}} \\
\frac{d}{dx}tanh^-1(u) &= \frac{d}{dx}coth^-1(u) = \frac{u'}{1-u^2} \\
\frac{d}{dx}csch^-1(u) &= \frac{-u'}{|u|\sqrt{1+u^2}} \\
\frac{d}{dx}sech^-1(u) &= \frac{-u'}{u\sqrt{1-u^2}} \\
\end{align}
$$
- **Minima and Maxima**
	- A function is increasing on an interval if the value of the function increases as the value of the argument increases over that interval.
		- A function is decreasing on an interval where f'(x) > 0 for any number x in that interval.
	- The graph of a function is concave downward at any point where f''(x) < 0
	- The point of inflection is the point where the reversal of curvature occurs, where the curve changes from concave downward to concave upward. IE: the point where f''(x) = 0
	- Commoner's test
		- At the maximum point, the second derivative is negative
		- At the minimum point, the second derivative is positive

# Integration

 - To indicate the whole of or to give the sum or the total
 - Used in finding the areas bounded by curves / volumes and various solids
 $$
	 \frac{dy}{dx} = f(x) \ or \ dy = f(x)dx 
 $$
 Integrate both sides of the equation where
$$
	\int dy = \int f(x)dx = F(x) + c
$$

Integrating a sum, each term is integrated separately. A constant factor in the integrand can be written before the integral sign.
$$
\begin{align}
	\int (f_1(x) + f_2(x) + \dots + f_n(x)) \ dx &= \int f_1(x)dx + \int f_2(x)dx + \dots + \int f_n(x)dx \\ 
	\int a \ f(x)dx &= a \int f(x)dx 
\end{align}
$$

If a continuous function f(x) is positive over the domain, then the area under its graph is
$$
	\int_{a}^{b} f(x)dx = F(b) - F(a)
$$
 - Integrate the function f(x) to get F(x) and the answer is `F(b) - F(a)`
 - Definite integrals of continuous functions have algebra properties used in computations
	 - Integral of a constant multiple of a function is the same as constant times the integral of the function. **See equation 4 above**
	 - The integral of the sum of two functions is the sum of their integrals. **See equation 3 above**
	 - The sign of an integral chances when its limits of integration are interchanged.
$$	\int_{a}^{b} f(x)dx = -\int_{b}^{a} f(x)dx$$
# Integration Cheat Sheet
$$
\begin{align}
	\int x^ndx &= \frac{x^{n+1}}{n+1} + C \\
	\int \frac{dx}{x} &= lnx + C \\
	\int e^{ax}dx &= \frac{e^{ax}}{a} + C \\
	\int a^{x}dx &= \frac{a^{x}}{lna} + C \\
	\int cos(ax)dx &= \frac{sin(ax)}{a} + C \\
	\int sin(ax)dx &= -\frac{cos(ax)}{a} + C \\
	\int sec^2(ax)dx &= \frac{tan(ax)}{a} + C \\
	\int csc^2(ax)dx &= -\frac{cot(ax)}{a} + C \\
	\int sec(x)tan(x)dx &= sec(x) + C \\
	\int csc(x)cot(x)dx &= -csc(x) + C \\
	\int sec(x)dx &= ln|sec(u)+tan(u)| + C \\
	\int csc(x)dx &= -ln|csc(u)+cot(u)| + C \\
	\int \frac{1}{\sqrt{a^2-x^2}}dx &= sin^{-1}(\frac{x}{a}) + C \\
	\int \frac{1}{a^2+x^2}dx &= \frac{1}{a}tan^{-1}(\frac{x} {a}) + C \\
	\int \frac{1}{x\sqrt{x^2-a^2}}dx &= \frac{1}{a}sec^{-1}(\frac{x}{a}) + C \\
\end{align}
$$

# Integration Techniques
### U-substitution
 - Find something in the equation that you can equate to u
 - Find `du/dx` by getting the derivative of u with respect to x
 - Manipulate the derivative such that something in the original equation can be rewritten in terms of du
 - Now with a (simpler) equation, integrate with respect to u, then replace any u in `F(u)` with the definition in terms of x

**Example of u-substitution**
 - Example 1
	$$
	\begin{align}
	& \int\frac{cos4tdt}{3+sin4t} \\\\
	& \text{perform u-substitution} \\
	&u = sin4t, \text{ and } \frac{du}{4} = cos4tdt \\\\
	
	&\text{replace all variables u to be in terms of t} \\
	&\frac{1}{4}\int \frac{du}{3 + u} = \frac{1}{4}\left(ln|u + 3|\right)
	=\frac{ln|sin4t + 3|}{4} + C
	\end{align}
	$$
 - Example 2
	$$
	\begin{align}
	& \text{integrate}\int \left(3x^2-1\right)x^5dx \\\\
	
	& \text{perform u-substitution} \\
	& u = 3x^2-1, \frac{1}{6}du = xdx, x^4 = \left(\frac{u+1}{3}\right)^{2}\\\\
	
	& \text{replace all variables in terms of u}\\
	& = \int (3x^2 - 1) \cdot x^4 \cdot xdx = \int u \cdot \left(\frac{u+1}{3}\right) ^2 \cdot \frac{1}{6}du \\
	& = \frac{1}{6}\int u \left(\frac{u+1}{3}\right)^2du 
	= \frac{1}{6}\int u \left(\frac{u^2+2u+1}{9}\right)du \\
	
	
	& = \frac{1}{54}\int \left(u^3+2u^2+u\right) du \\
	& = \frac{1}{54} \left(\frac{u^4}{4}+\frac{2u^3}{3}+\frac{u^2}{2}\right)\\\\
	
	& \text{substitute $u = 3x^2-1$} \\
	& = \frac{1}{54}\left( \frac{(3x^2-1)^4}{4} + \frac{2(3x^2-1)^3}{3} + \frac{(3x^2-1)^2}{2}\right) + C
	\end{align}
	$$

**Examples of integration by appropriate substitution**
 - Example 1
	$$
	\begin{align}
	& \text{integrate} \int \frac{xdx}{\sqrt{x+4}} \\\\
	
	& \text{we can then make the following substituitions} \\
	& u=\sqrt{x+4}\\
	& u^2 - 4 = x \\
	& 2udu = dx \\\\
	
	& \text{and rewrite the equation as}\\
	& = \int \frac{(u^2-4) * 2udu}{u}\\
	& = 2\int (u^2-4)du\\
	& = 2\left(\frac{u^3}{3}-4u\right) \\
	& = 2\left(\frac{\sqrt{x+4}^3}{3}-4\sqrt{x+4}\right) + C
	
	\end{align}
	$$
 - Example 2
	$$
	\begin{align}
	& \text{integrate} \int \frac{(x^3+4x)dx}{\sqrt{x^2-6}}\\\\
	
	& \text{ we can make the following substitutions }\\
	& u = \sqrt{x^2-6} \\
	& u^2 = x^2-6 \\
	& u^2 + 10 = x^2 + 4 \\
	& udu = xdx \\\\
	
	& \text { we can then rewrite the integral as } \\
	& \int \frac{(x^2 + 4x)xdx}{\sqrt{x^2 - 6}} \\
	& = \int \frac{(u^2+10)udu}{u} \\
	& = \int (u^2 + 10) du \\
	& = \frac{u^3}{3} + 10u \\
	& = \frac{\sqrt{x^2-6}^3}{3} + 10\sqrt{x^2-6} + C
	\end{align}
	$$
 - Example 3
	$$
	\begin{align}
	& \text{integrate} \int \frac{x+2}{\sqrt[4]{2x-3}^3} dx \\\\
	
	& \text{we can make the following substitutions} \\
	& u = \sqrt[4]{2x-3}, \text{ and } u^2 = \sqrt{2x-3} \\
	& x = \frac{u^4 + 3}{2}, \text{ and } dx = 2u^3du \\\\
	
	& \text{we can then rewrite the integral as } \\
	& \int \frac{\frac{u^4+3}{2} + 2}{u^3}2u^3du \\
	& = 2 \int \left(\frac{u^4+3}{2} + 2\right)du \\
	& = 2 \int \left(\frac{u^4+7}{2}\right)du \\
	& = \int (u^4+7)du \\
	& = \left(\frac{u^5}{5} + 7u\right) = \left(\frac{\sqrt[4]{2x-3}^5}{5} + 7\sqrt[4]{2x-3}\right) + C
	\end{align}
	$$
### Integration by partial fractions
 - an integration technique to integrate functions whose numerator is not a derivative of the denominator
 - Most fractions are integrable by splitting them into sum of fractions with simpler denominators.
 - If the term in the denominator is `(ax+b)^k`, then the term in the decomposition is
 $$
 \frac{A_1}{ax+b} + \frac{A_2}{(ax+b)^2} + \frac{A_3}{(ax+b)^3} + \dots + \frac{A_k}{(ax+b)^k}
 $$
  - If the term in the denominator is `(ax^2 + bx + c)^k`, then the term in the decomposition is
$$
\frac{Ax + B}{(ax^2 + bx + c)} + \frac{Cx + D}{(ax^2 + bx + c)^2} + \frac{Ex + F}{(ax^2 + bx + c)^3} + \dots + \frac{Yx + Z}{(ax^2 + bx + c)^k}
$$

**Examples of partial fractions**
 - Example 1
	$$
	\begin{align}
	& \int \frac{3x+11}{x^2-x-6}dx = \int \left(\frac{A}{x-3} + \frac{B}{x+2}\right) dx\\
	& = \int \left(\frac{A(x+2)+B(x-3)}{(x-3)(x+2)}\right) dx
	= \int \left(\frac{A(x+2)+B(x-3)}{x^2-x-6}\right) dx \\\\
	
	& \text{with the equation above, $A(x+2)+B(x-3) = 3x+11$} \\
	& \text{we can then solve for $A$ and $B$ by substituting zeros of $x$} \\\\
	
	& \text{when $x=-2$, } A(-2+2) + B(-2 - 3) = 3(-2) + 11\\
	& -5B = -6 + 11\\
	& B = -1 \\\\
	
	& \text{when $x=3$, } A(3+2) + B(3-3) = 3(3) + 11\\
	& 5A = 9 + 11 = 20 \\
	& A = 4 \\\\
	
	
	& \text{Now that we have values for $A$ and $B$}\\
	& \int \left(\frac{4}{x-3} - \frac{1}{x+2}\right) dx \\
	& = 4\int \left(\frac{1}{x-3}\right)dx - \int\left(\frac{1}{x+2}\right) dx \\
	& = 4ln|x-3| -ln|x+2| + C
	
	\end{align}
	$$
 - Example 2
	$$
	\begin{align}
	& \text{integrate } \int\frac{3x + 7}{(x-1)(x-2)}dx \\
	& \text{equate $3x+7$ to $A(x-2) + B(x-1)$ and find A, B}\\\\
	
	& \text{When $x=2$ then $A(0) + B(1) = 13$ thus $B=13$}\\
	& \text{When $x=1$ then $A(-1) + B(0) = 10$ thus $A=-10$}\\\\
	
	
	& \text{integrate} \int \left(\frac{-10}{x-1} + \frac{13}{x-2}\right) dx\\
	& = -10\int \frac{1}{x-1}dx + 13\int\frac{1}{x-2}\ dx\\
	& = -10ln|x-1| + 13ln|x-2| + C
	\end{align}
	$$
### Integration by parts
 - Given an integral in the form `u * dv/dx`, it can be integrated below
$$
\begin{align}
\int u\frac{dv}{dx} = uv - \int v\frac{du}{dx}
\end{align}
$$
 - **Steps**
	 - Find a `u` and `dv/dx`
	 - Derive u in terms of x to get `du/dx`
	 - Integrate `dv/dx` to get v
	 - Substitute in the formula above

**Examples of integration by parts**
 - Example 1
	$$
	\begin{align}
	& \text{integrate} \int xe^xdx\\
	& \text{let $u = x$ and $dv = e^xdx$ } \\
	& \text{then $du = dx$ and $v = e^x$} \\\\
	
	& \text{substitute into the formula $\int udv = uv - \int vdu$} \\
	& \int xe^xdx = xe^x-\int e^xdx = xe^x - e^x + C
	\end{align}
	$$
 - Example 2
	$$
	\begin{align}
	& \text{integrate} \int ln(x)dx  \\\\
	& \text{let $u = ln(x)$, and $dv=dx$} \\
	& \text{then $du = \frac{dx}{x}$, and $v=x$} \\\\
	
	& \text{substitute into the formula $\int udv = uv - \int vdu$} \\
	& \int ln(x)dx = x \cdot ln(x) - \int x \cdot \frac{dx}{x}
	= x \cdot ln(x) - \int dx \\
	& = x \cdot ln(x) - x = xln(x) - x + C
	\end{align}
	$$
 - Example 3
	$$
	\begin{align}
	& \text{integrate} \int xcos(x)dx \\\\
	& \text{let $u=x$ and $dv = cos(x)dx $} \\
	& \text{then $du = dx$ and $v = sin(x)$} \\\\
	
	& \text{substitute into the formula $\int udv = uv - \int vdu$} \\
	& \int xcos(x)dx = xsin(x) - \int sin(x)dx = xsin(x) + cos(x) + C
	\end{align}
	$$
- Example 4
	$$
	\begin{align}
	& \text{integrate } \int x^2e^xdx \\\\
	& \text{let $u=x^2$, and $dv = e^xdx$} \\
	& \text{then $du = 2xdx$ and $v = e^x$} \\
	
	& \text{substitute into the formula $\int udv = uv - \int vdu$} \\
	& \int x^2e^xdx = x^2e^x - \int e^x \cdot 2xdx = x^2e^x - 2\int xe^x dx \\
	& = x^2e^x - 2(xe^x - e^x) = x^2e^x - 2xe^x - 2e^x + c
	\end{align}
	$$
### Integration by trig substitution
 - Using the Pythagorean theorem, the following substitutions can be made
	 - `u = asin(theta)` for `sqrt(a^2 - u^2)`
	 - `u = atan(theta)` for `sqrt(a^2 + u^2)`
	 - `u = asec(theta)` for `sqrt(u^2-a^2)`
	 - Other useful trig identities
		 - `sin^2(theta) = 1/2 * (1-cos(2 theta))`
		 - `sin(theta)cos(theta) = 1/2 * (sin(2 theta))`

**Example of Trigonometric Substitution**
 - Example 1
	$$
	\begin{align}
	& \text{integrate} \int \frac{x^2 dx}{\sqrt{25-x^2}} \\\\
	
	& \text{we can make the following substitutions}\\
	& x = 5sin(\theta), \text{ and }dx = 5cos(\theta)d\theta \\\\
	
	& \text{we can then rewrite the integral as}\\
	& \int \frac{25sin^2(\theta) \cdot 5cos(\theta)d\theta}{\sqrt{25-25sin^2(\theta)}}\\
	& = \int \frac{25sin^2(\theta) \cdot 5cos(\theta)d\theta}{\sqrt{25}\sqrt{1-sin^2(\theta)}} = \int \frac{25sin^2(\theta) \cdot 5cos(\theta)d\theta}{5cos(\theta)} \\
	& = \int 25sin^2(\theta) d\theta = 25\int \frac{1}{2} (1-cos(2\theta))d\theta \\
	& = \frac{25}{2}\int (1-cos(2\theta))d\theta = \frac{25}{2} \left(\theta-\frac{sin(2\theta)}{2} \right) \\\\
	
	& \text{in order to get $\theta$, we can use the inverse trig functions } \theta = sin^{-1}(\frac{x}{5}) \\\\
	& \text{we can also use the following identity } \frac{sin(2\theta)}{2} = sin(\theta)cos(\theta) \\\\
	
	& \text{then we have the following eq:} \\
	& = \frac{25}{2}\left(sin^{-1}\left(\frac{x}{5}\right) - sin(\theta)cos(\theta)\right)\\\\
	
	& \text{remember that $sin(\theta) = \frac{x}{5}$, we can use the pythagorean theorem to get} \\
	& \text{that $cos(\theta) = \frac{\sqrt{25-x^2}}{5}$} \\\\
	
	& \text{then we have the following eq:} \\
	& = \frac{25}{2}\left(sin^{-1}\left(\frac{x}{5}\right) - \frac{x\sqrt{25-x^2}}{25}\right) + C\\\\
	
	\end{align}
	$$
 - Example 2
	$$
	\begin{align}
	& \text{integrate} \int \frac{dx}{\sqrt{9+x^2}} \\\\
	& \text{we can make the following substitutions: } \\
	& x = 3tan\theta, \text{ and } dx=3sec^2(\theta)d\theta \\\\
	
	& \text{we can rewrite the integral as} \\
	& \int \frac{3sec^2(\theta)d\theta}{\sqrt{9 + 9tan^2(\theta)}} = \int \frac{3sec^2(\theta)d\theta}{\sqrt{9} \sqrt{1 + tan^2(\theta)}} = \int \frac{3sec^2(\theta)d\theta}{3sec(\theta)} = \int sec(\theta)d\theta \\\\
	& = ln|sec(\theta) + tan(\theta)|\\\\
	
	& \text{we can use the pythagorean theorem to get $sec(\theta)$}\\
	& tan(\theta) = \frac{x}{3}, \text{ $opp = x$, and $adj = 3$ thus} \\
	& sec(\theta) = \frac{hyp}{adj} = \frac{\sqrt{x^2 + 9}}{3} \\\\
	
	& = ln\left|\frac{\sqrt{x^2 + 9}}{3} + \frac{x}{3}\right| = ln\left|\frac{x + \sqrt{x^2 + 9}}{3}\right| + C\\\\
	
	\end{align}
	$$
### Integration of rational functions of sin(x) and cos(x)
$$
\begin{align}
& z = tan\left(\frac{x}{2}\right) \\
& x=2tan^{-1}(z) \text{ and } dx = \frac{2dz}{1+z^2}\\
& cos(x) = \frac{1-z^2}{1+z^2} \text{ and }sin(x) = \frac{2z}{1+z^2} \\
\end{align}
$$
**Example of integration of rational functions**
 - Example 1
$$
\begin{align}
& \text{integrate} \int \frac{dx}{1+cos(x)} \\\\
& \text{substitute the formulas above to rewrite the equation to z} \\
& = \int \frac{1}{1 + \frac{1-z^2}{1+z^2}} \cdot \frac{2dz}{1+z^2}
 = \int \frac{1}{\frac{1+z^2}{1+z^2} + \frac{1-z^2}{1+z^2}} \cdot \frac{2z}{1+z^2} \\
& = \int \frac{1}{\frac{1+z^2 + 1-z^2}{1+z^2} } \cdot \frac{2dz}{1+z^2}
= \int \frac{1}{\frac{2}{1+z^2} } \cdot \frac{2dz}{1+z^2}
= \int \frac{1+z^2}{2} \cdot \frac{2dz}{1+z^2} \\
& = \int dz = z \\
& = tan\left(\frac{x}{2}\right) + C
\end{align}
$$
 - Example 2
	$$
	\begin{align}
	& \text{integrate} \int \frac{dx}{2+sin(x)} \\\\
	& \text{we can substitute the formulas above to get the ff: } \\\
	& \int \frac{2dz}{1+z^2} \cdot \frac{1}{2 + \frac{2z}{1+z^2}}
	 = \int \frac{2dz}{1+z^2} \cdot \frac{1}{\frac{2+2z^2}{1+z^2} + \frac{2z}{1+z^2}}
	 = \int \frac{2dz}{1+z^2} \cdot \frac{1}{\frac{2z^2 + 2z + 2}{1+z^2}}\\\\
	& = \int \frac{2dz}{1+z^2} \cdot \frac{1 + z^2}{2z^2 + 2z + 2}
	= \int \frac{1}{z^2 + z + 1}dz
	= \int \frac{1}{\left(z+\frac{1}{2}\right)^2 + \left(\frac{\sqrt{3}}{2}\right)^2}dz \\\\
	
	& \text{we can then use the following identity to solve the remaining integral: }\\
	& \int \frac{1}{a^2+x^2}dx = \frac{1}{a}tan^{-1}(\frac{x} {a}) + C\\\\
	
	& = \frac{1}{\frac{\sqrt{3}}{2}} tan^{-1}\left( \frac{z+\frac{1}{2}}{\frac{\sqrt{3}}{2}}\right)\
	 = \frac{2\sqrt{3}}{3} tan^{-1}\left( \frac{2z+1}{\sqrt{3}}\right)\\
	& = \frac{2\sqrt{3}}{3} tan^{-1}\left( \frac{2\tan\left(\frac{x}{2}\right) +1}{\sqrt{3}}\right) 
	 = \frac{2\sqrt{3}}{3} tan^{-1}\left( \frac{\sqrt{3}\left(2\tan\left(\frac{x}{2}\right) + 1\right)}{3}\right) + C
	\end{align}
	$$
# Misc Integration Examples
**Integrate the following functions with respect to the var**
$$
\begin{align}
\int \left(6x^{-4} - 10x^4 + 12x \right) \ dx &= 6\frac{x^{-3}}{-3} - 10 \frac{x^5}{5}+12\frac{x^2}{2} \\
&= \frac{-2}{x^3}-2x^5+6x^2 + C
\end{align}
$$

$$
\begin{align}
\int \left(x^{\frac{3}{2}}-4x^{\frac{1}{2}}+\frac{3}{x^{1/2}}\right)dx 
&= \frac{x^{\frac{5}{2}}}{\frac{5}{2}}-4\frac{x^{\frac{3}{2}}}{\frac{3}{2}}+3\frac{x^{\frac{1}{2}}}{\frac{1}{2}} + C\\
&= \frac{2x^{\frac{5}{2}}}{5}-\frac{8x^{\frac{3}{2}}}{3}+\frac{2\sqrt{x}}{3} + C
\end{align}
$$
$$
\begin{align}
\int \left(\frac{4}{x}-12+\frac{6}{x^2} \right) dx &= 4|lnx| - 12x - \frac{6}{x} + C 
\end{align}
$$

$$
\begin{align}
\int \left(e^{2x} + \frac{2}{x} - \frac{4}{e^{2x}} \right)dx &= \frac{e^{2x}}{2} + 2|lnx| - 4 \frac{e^{-2x}}{-2} + C \\
&= \frac{e^{2x}}{2} + 2|lnx| + \frac{8}{e^{2x}} + C
\end{align}
$$
$$
\begin{align}
\int cos(8t) dt = \frac{sin(8t)}{8} + C
\end{align}
$$

$$
\int \left(cos(4\theta) - sin(6\theta)\right)d\theta = \frac{sin(4\theta)}{4} + \frac{cos(6\theta)}{6} + C
$$

$$
\int \left(10sec^2(4\theta)-12csc^2(6\theta)\right) d\theta = \frac{5tan{4\theta}}{2} + 2cot(6\theta) + C
$$

**Evaluate each of the following definite integrals**
$$
\begin{align}
\int^{3}_{2}\left(x^3 - \frac{1}{x}\right)dx = F(3) - F(2)\\
F(x) = \frac{x^4}{4}-ln|x| \\
F(3) - F(2) = 15.845
\end{align}
$$
$$
\begin{align}
\int^{2}_{1} \left(e^{2t} + \frac{1}{2t}\right)dt = F(2) - F(1)\\
F(x) = \frac{e^{2t}}{2} + \frac{ln|x|}{2}
\end{align}
$$

$$
\begin{align}
\int^{\pi}_{0}sinxdx = F(\pi) - F(0) = 2\\
F(x) = -cos(x)
\end{align}
$$
**Solve the following differential equations subject to the prescribed initial conditions**
$$
\begin{align}
\frac{dy}{dx} = 6x^2+6x-3, x=-1, y=0\\
\int dy = \int \left(6x^2+6x-3\right)dx\\
y = \frac{6x^3}{3}+\frac{6x^2}{2}-3x + C\\
y = 2x^3+3x^2-3x + C \\
0 = 2(-1)^3+3(-1)^2-3(-1) + C\\
0 = -2 + 3 + 3 + C \\ 
y = 2x^3+3x^2-3x -4 \\
\end{align}
$$

### Area
 - The area under a curve $y=f(x)$ between a-b is $\int^{b}_{a} ydx$
 - The area bounded by two curves between a-b is $\int^{b}_{a} [f(x) - g(x)]dx$
 - The area bounded by two angles between a-b is $\frac{1}{2}\int^{\beta}_{\alpha} r^2 d\theta$
**Problems**
 - Find the area between the curve `y=x-1` and the x-axis from x=-2 to x=4
	 - `9 square units`
 - Find the area between the curve  `y=x^3-4x^2+3x` and the x-axis from x=0 to x=3
	 - `37/12 sqaure units`
 - Find the area bounded by `y=2x, y=-3x and x=4`
	 - `40 square units`
 - Find the area bounded by `x^2=4y+4 and y=x+2`
	 - `64/3 square units`
 - Find the area bounded by the curves `y^2=2x and y=x-4`
	 - `18 square units`
### Volume of revolution
 - The volume of revolution of a curve between a-b is $\pi \int^{b}_{a} [f(x)]^{2} dx$
 - The volume of revolution of a hollow curve between a-b is $\pi \int^{b}_{a} [f(x)^{2}-g(x)^{2}] dx$
	 - If you are not rotating directly on the axis then `f(x)` should be `m-f(x)` where m is the x value you're rotating from, same with y
 - Using the shell method $2\pi\int^{b}_{a}x[f(x)-g(x)]dx$
	 - Allows you to solve for rotations along y in terms of x
**Problems**
 - Find the volume generated by revolving the given plane area about the line
 - `y=2x^2, y=0, x=0, x=5` about the x-axis
	 - `2500 pi cubic units`
 - `y=2x^2, y=0, x=0, x=5` about the y-axis
	 - `625 pi cubic units`
 - `x=9-y^2, x-y-7=0`, about x=4
	 - `153/5 pi cubic units`
 - `y=x^3, y=0, x=2` about y=8
	 - `320/7 pi cubic units`
### Surface Area
$$
\begin{align}
S&=2\pi\int yds \text{ when rotating about the x-axis}\\
S&=2\pi\int xds \text{ when rotating about the y-axis}\\
ds&= \sqrt{1+\left(\frac{dy}{dx}\right)^2} dx\\
ds&= \sqrt{1+\left(\frac{dx}{dy}\right)^2} dx\\
\end{align}
$$
**Problems**
 - Determine the surface area of the solid obtained by rotating $y=\sqrt{9-x^2}$ about the x-axis between $-2\le x\le2$
	 - `24 pi squared units`
 - Determine the surface area of the solid obtained by rotating $y=\sqrt[3]{x}$ about the y-axis between $1\le y\le 2$
	 - `199.48 pi squared units`
### Arc Length
 - The length of an arc of a f(x) between a to b is
$$
s = \int^{b}_{a} \sqrt{1+f'(x)^2} \text{ } dx
$$
**Problems**
 - Calculate the arc length of `f(x) = 2x^(3/2)` over the interval `[0, 1]`
	 - `2.268 units`
 - Calculate the arc length of `f(x) = (4/3) x^(3/2)` over the interval `[0, 1]`
	 - `1.697 units`
 - Calculate the arc length of `f(x)=x^2` over the interval `[1,3]`
	 - `8.26815 units`