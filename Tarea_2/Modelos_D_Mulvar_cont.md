# Modelos de distribucion multivariables continuos

1. Sean 𝑋 e 𝑌 variables aleatorias continuas con función de densidad de probabilidad 
conjunta


$$ f_{XY}(x, y) =\begin{cases}
               \frac{1}{2}x + \frac{3}{2}y & 0 \leq x \leq 1, 0\leq y \leq 1\\\\
               0 & otros
            \end{cases}$$

Determine
a) La función de distribución acumulada.

$$F_{XY}(x,y) = \int_{0}^x\int_{0}^{y} \left( \frac{1}{2}u + \frac{3}{2}v \right)dvdu = \int_{0}^x \frac{1}{2}uv +  \frac{3}{4}v^2 \Big|_{0}^{y} du$$


$$= \int_{0}^x \frac{1}{2}uy +  \frac{3}{4}y^2 du$$

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

$f_{XY}(x,y) = \frac{1}{2}x + \frac{3}{2}y$

$f_X(x)f_Y(y) = \left( \frac{1}{2}xy + \frac{3}{4} y^2 \right) \left( \frac{1}{4}x^2 + \frac{3}{2}yx \right)$

$\frac{1}{2}x + \frac{3}{2}y \neq \frac{1}{8}xy\left[ x^2 + \frac{15}{2}xy + 9y^2 \right] \rightarrow \therefore \text{ X y Y No son independientes}$

****

2. Un sistema electrónico tiene uno de cada dos tipos diferentes de componentes de 
operación en operación conjunta. Denote con 𝑋 y 𝑌 las duraciones aleatorias de los 
componentes  del  tipo  I  y  tipo  II  respectivamente.  La  función  de  densidad  de 
probabilidad conjunta está dada por

$$f_{X Y}(x, y) = \begin{cases}
\frac{1}{8} x e^{-(x+y) / 2} & x>0, y>0 \\\\
0 & \text { otros. }
\end{cases}$$

Las mediciones son en cientos de horas.

a) Encuentre $𝑃(𝑋> 1,𝑌> 1)$

$𝑃(𝑋> 1,𝑌> 1) = \int^{\infty}_{1} \int^{\infty}_{1} \frac{1}{8}xe^{-(x + y)/2} dydx$

$= \frac{1}{8} \int^{\infty}_{1} xe^{x/2} \left[ -0 + 2e^{-1/2} \right]dx = -\frac{1}{4} e^{-1/2}  \int^{\infty}_{1} x e^{-x/2} dx$

$= \frac{1}{4} e^{-1/2} e^{-1/2}\left[ -2x -4 \right] \Big|^{\infty}_1 = -\frac{1}{4} e^{-1/2} e^{-1/2}\left[ -2 -4 \right]$

$$\boxed{= \frac{3}{2e} \approxeq .5518}$$

b) Encuentre  la  probabilidad  de  que  el  componente  tipo  II  tenga  una  vida  útil  de 
más de 200 horas.

$P(Y > 2) = \int^{\infty}_2 \int^{\infty}_0 \frac{1}{8} x e^{-(x+y) / 2} dxdy = \frac{1}{8}  \int^{\infty}_2 e^{-y/2} \int^{\infty}_0 xe^{-x/2} dxdy$

$= \frac{1}{8}  \int^{\infty}_2 e^{-y/2} e^{-x/2} [2x - 4] dy \Big|^{\infty}_0$

$= \frac{1}{2} \int^{\infty}_2 e^{-y/2} dy = \frac{1}{2} \left[ -2e^{-y/2} \right] \Big|^{\infty}_2$

$$= \boxed{\frac{1}{e} \approxeq 0.3679}$$

****

3. Sena X e Y variables aleatorias continuas con función de densidad de probabilidad conjunta

$$f_{XY} = \begin{cases}
\frac{1}{4}(1 + xy(x^2 - y^2)), & -1 \leq x \leq 1, \quad -1 \leq y \leq 1 \\\\
0 & otros   
\end{cases}
$$

Determine

a) La función de distribución acumulada.

$$F_{XY}(x, y) = \int^{x}_0 \int^{y}_0 \frac{1}{4}(1 + xy(x^2 - y^2)) dy dx = \frac{1}{4}\int^{x}_0 \int^{y}_0 (1 + x^3y - xy^3) dy dx$$

$$= \frac{1}{4} \int^{x}_0 (y + \frac{1}{2}x^3y^2 - \frac{1}{4}xy^4) dx = \frac{1}{4} (xy + \frac{1}{8}x^4y^2 - \frac{1}{8}x^2y^4) = \boxed{\frac{1}{4} \left(xy + \frac{1}{8}x^2y^2(x^2 - y^2)\right)}$$

b) Las funciones de densidad de probabilidad marginal para 𝑋 e 𝑌.

$$f_X(x) = \int^{y}_0 \frac{1}{4}(1 + xy(x^2 - y^2)) dy = \boxed{\frac{1}{4} \left(y + \frac{1}{2}x^3y^2 - \frac{1}{4}xy^4\right)}$$

$$f_Y(y) = \int^{x}_0 \frac{1}{4}(1 + xy(x^2 - y^2)) dx = \boxed{\frac{1}{4}\left( x + \frac{1}{4}x^4y - \frac{1}{2}x^2y^3 \right)}$$

c) Las funciones de densidad de probabilidad condicional de 𝑋 e 𝑌.

$$f_{X|Y}(X \leq x|Y \leq y) = \boxed{\frac{(1 + xy(x^2 - y^2))}{\left( x + \frac{1}{4}x^4y - \frac{1}{2}x^2y^3 \right)}}$$

$$f_{Y|X}(Y \leq y|X \leq x) = \boxed{\frac{(1 + xy(x^2 - y^2))}{ \left(y + \frac{1}{2}x^3y^2 - \frac{1}{4}xy^4\right)}}$$

d) Si las variables aleatorias son independientes.

Si $f_{XY}(x,y) = f_X(x)f_Y(y)$ para toda x, y; entonces $X$ y $Y$ son independientes

$f_{XY}(x,y) = \frac{1}{4}(1 + xy(x^2 - y^2))$

$f_X(x)f_Y(y) = \frac{1}{4} \left(y + \frac{1}{2}x^3y^2 - \frac{1}{4}xy^4\right) \cdot \frac{1}{4}\left( x + \frac{1}{4}x^4y - \frac{1}{2}x^2y^3 \right)$


<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script type="text/x-mathjax-config">
    MathJax.Hub.Config({ tex2jax: {inlineMath: [['$', '$']]}, messageStyle: "none" });
</script>

