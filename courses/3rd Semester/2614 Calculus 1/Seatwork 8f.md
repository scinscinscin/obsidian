**Find the area bounded as follows**
$$
\begin{align}
& y = 2x - 4 \text{ and } y^2 = 4x \\
& x = \frac{y+4}{2} \text{ and } x = \frac{y^2}{4}\\\\
& \text{get points of intersection}\\
& \frac{y^2}{4} = \frac{y+4}{2}\\ 
& 2y^2 = 4y + 16 \\
& y^2 -2y - 8= 0\\
& \text{the lines intersect at points $y=4, -2$} \\\\

& \int^{y=4}_{y=-2} \left(\frac{y+4}{2} - \frac{y^2}{4}\right)dy = \int^{y=4}_{y=-2} -\frac{y^2-2y-8}{4}dy \\\\
& = \frac{-1}{4}\int^{y=4}_{y=-2} (y^2-2y-8) dy 
	= \frac{-1}{4} \left[\frac{y^3}{3}-y^2-8y\right]^{y=4}_{y=-2} \\\\
& = \frac{-1}{4} \left[\left(\frac{4^3}{3}-4^2-8(4)\right) - \left(\frac{(-2)^3}{3}-(-2)^2-8(-2)\right)\right] \\\\
& = \frac{-1}{4} \left[\left(\frac{64}{3}-16-32\right) - \left(\frac{-8}{3}-4+16\right)\right] \\\\
& = \frac{-1}{4} \left(\frac{64+8}{3}-16-32+4-16\right)\\\\
& = \frac{-1}{4} \left(24-16-32+4-16\right) = \frac{-1}{4} \cdot -36 = 9\\\\
\end{align}
$$

$$
\begin{align}
& x^{2}=8y \text{ and } x-2y+8 = 0 \\
& \frac{x^{2}}{8}=y \text{ and } \frac{x+8}{2} = y \\\\

& \text{get points of intersection} \\
& \frac{x^2}{8} = \frac{x+8}{2} \\
& x^2 = 4x+32 \\
& x^2 -4x - 32 = 0 \\
& x = 8, -4 \\\\

& \int^{8}_{-4} \left[\left(\frac{x+8}{2}\right)-\left(\frac{x^2}{8}\right)\right]dx = \int^{8}_{-4} \left(-\frac{x^2-4x-32}{8}\right)dx \\\\
& = -\frac{1}{8} \int^{8}_{-4} ({x^2-4x-32})dx 
= -\frac{1}{8}\left[\frac{x^3}{3}-2x^2-32x\right]^{8}_{-4} \\\\
& = -\frac{1}{8}\left[\left(\frac{8^3}{3}-2(8^2)-32(8)\right) - \left(\frac{(-4)^3}{3}-2(-4)^2-32(-4)\right)\right] \\\\
& = -\frac{1}{8}\left[\left(\frac{512}{3}-128-256\right) - \left(\frac{-64}{3}-32+128\right)\right] \\\\
& = -\frac{1}{8}\left(\frac{512+64}{3}-128-256+32-128\right) \\\\
& = -\frac{1}{8}\left(192-128-256+32-128\right) = -\frac{1}{8} \cdot -288 = 36\\\\
\end{align}
$$



