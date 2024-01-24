$$
\begin{align}
&\text{Evaluate the iterated integral} \\
&\int^2_1 \int^{2x}_{0} xy^2 \cdot dydx \\
&= \int^2_1 \frac{xy^3}{3} \Biggm\lvert ^{2x}_{0} dx 
= \frac{8}{3} \int ^{2}_{1} x^4dx \\
&= \frac{8}{3} \left[ \frac{x^5}{5} \right] \Biggm\lvert ^{2}_{1}
= \frac{8}{3} \left[\frac{32}{5}-\frac{1}{5}\right] = \frac{248}{15}
\end{align}
$$

$$
\begin{align}
& \int^{4}_{2} \int^{4x}_{0} (x-2y) dydx
= \int^4_2 (xy-y^2) \bigg\lvert ^{4x}_0 dx \\
&= \int^4_2 (4x^2-16x^2) dx = -12 \int^4_2 x^2 dx \\
&= -12 \left[\frac{x^3}{3}\right] \Bigg\lvert ^4_2
 = -12 \left[\frac{64}{3}-\frac{8}{3}\right] = -224
\end{align}
$$

$$
\begin{align}
& \int^4_1 \int^{4x}_0 (2x-y+2)dydx = \int^{4}_{1} \left[2xy - \frac{y^2}{2} +2y\right] \Biggm\lvert ^{4x}_{0} dx \\
&= \int^{4}_{1} (8x^2-8x^2+8x)dx = \int^{4}_{1} 8xdx = (4x^2) \big\lvert ^4_1\\
&= 64-4 = 60
\end{align}
$$

$$
\begin{align}
& \int^4_2 \int^{x+2}_0 dydx 
= \int^4_2 (y)\Bigm\lvert^{x+2}_0 dx
= \int^4_2 (x+2) dx \\
&=\left[\frac{x^2}{2} + 2x \right] \Bigg\lvert^4_2
 = \left[(8 + 8) - (2+4)\right] = 10
\end{align}
$$

$$
\begin{align}
&\int^4_0 \int^y_0 \sqrt{9+y^2} \text{ }dxdy \\
&=\int^4_0 (x \sqrt{9+y^2}) \Bigg\lvert ^y_0 dy \\
&=\int^4_0 (y \sqrt{9+y^2}) dy \\\\

& \text{use u-substitution where $u=9+y^2$}\\
& \text{then $du/2 = ydy$} \\\\

&= \frac{1}{2} \int^{25}_9 \sqrt{u} du 
= \frac{1}{2} \left[\frac{2u^{\frac{3}{2}}}{3}\right] \Bigg\lvert ^{25}_9
= \frac{1}{3} (125-27) = \frac{98}{3}
\end{align}
$$