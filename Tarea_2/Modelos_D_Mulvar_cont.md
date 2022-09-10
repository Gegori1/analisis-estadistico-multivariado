# Modelos de distribucion multivariables continuos

1. Sean 𝑋 e 𝑌 variables aleatorias continuas con función de densidad de probabilidad 
conjunta


$$ f_{XY}(x, y) =\begin{cases}
               \frac{1}{2}x + \frac{3}{2}y, \text{ } 0 \leq x \leq 1, 0\leq y \leq 1\\
               0 \text{ } otros
            \end{cases}$$

Determine
a) La función de distribución acumulada.

$$F_{XY}(x,y) = \int_{0}^x\int_{0}^{y} \left( \frac{1}{2}u + \frac{3}{2}v \right)dvdu = \int_{0}^x \frac{1}{2}uv +  \frac{3}{4}v^2 \Big|_{0}^{y} du = \int_{0}^x \frac{1}{2}uy +  \frac{3}{4}y^2 du$$

$$= \frac{1}{4}u^2y + \frac{3}{4}y^2u \Big|_0^{x} = \frac{1}{4}x^2y + \frac{3}{4}y^2x$$

$$= \boxed{\frac{1}{4}xy\left(x + 3y\right)}$$
b) Las funciones de densidad de probabilidad marginal para 𝑋 e 𝑌.

$f_X(x) = \int_{0}^{y}\left( \frac{1}{2}x + \frac{3}{2} v\right) dv = \frac{1}{2}xv + \frac{3}{4} v^2 \Big|^{y}_0 = \boxed{\frac{1}{2}xy + \frac{3}{4} y^2}$

$f_Y(y) = \int_{0}^{x}\left( \frac{1}{2}u + \frac{3}{2} y\right) du = \frac{1}{4}u^2 + \frac{3}{2}yu \Big|^x_0 = \boxed{\frac{1}{4}x^2 + \frac{3}{2}yx}$

c) Las funciones de densidad de probabilidad condicional de 𝑋 e 𝑌.

$$f_{X|Y}(x|y) = \boxed{\frac{\frac{1}{2}x + \frac{3}{2}y}{\frac{1}{4}x^2 + \frac{3}{2}yx}}$$

$$f_{Y|X}(y|x) = \boxed{\frac{\frac{1}{2}x + \frac{3}{2}y}{\frac{1}{2}xy + \frac{3}{4} y^2}}$$

d) Si las variables aleatorias son independientes.

Si $f_{XY}(x,y) = f_X(x)f_Y(y)$ para toda x, y; entonces $X$ y $Y$ son independientes

$\frac{1}{2}x + \frac{3}{2}y = \left( \frac{1}{2}xy + \frac{3}{4} y^2 \right) \left( \frac{1}{4}x^2 + \frac{3}{2}yx \right)$

$\frac{1}{2}x + \frac{3}{2}y \neq \frac{1}{8}xy\left[ x^2 + \frac{15}{2}xy + 9y^2 \right]$

