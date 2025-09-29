# View space → Screen space

**Given (fill these in):**

_View space is right-handed; camera looks down −Z._

* Vertical FOV: **$\mathrm{fov}_y$ (deg) = \_\_\_\_**
* Near plane **n = \_\_\_\_**, Far plane **f = \_\_\_\_**
* Screen size **screenwidth = \_\_\_\_**, **screenheight = \_\_\_\_** 
* View-space vertex **$p = (x_v, y_v, z_v)$ = (\_\_\_\_, \_\_\_\_, \_\_\_\_)** 

---

## 1) Project onto the near plane (similar triangles)

$$
x_p = -n \cdot \frac{x_v}{z_v},\qquad
y_p = -n \cdot \frac{y_v}{z_v}
$$

Compute:

* $x_p = \hspace{4cm}$
* $y_p = \hspace{4cm}$

---

## 2) Near-plane half-extents from FOV (_r_ and _t_)

$$
t = n \cdot \tan \left( \frac{\mathrm{fov}_y}{2}\right),\qquad
r = t \cdot \frac{screenwidth}{screenheight}
$$

Compute:

* $t = \hspace{4cm}$
* $r = \hspace{4cm}$

---

## 3) Clip (NDC) coordinates

$$
x_{\text{c}} = \frac{x_p}{r},\qquad
y_{\text{c}} = \frac{y_p}{t}
$$

Compute:

* $x_{\text{c}} = \hspace{4cm}$
* $y_{\text{c}} = \hspace{4cm}$

(If $|x_{\text{c}}|>1$ or $|y_{\text{c}}|>1$, the point lies outside the view frustum horizontally/vertically.)

---

## 4) Screen-space pixels (origin at top-left, +x right, +y down)

$$
x_{\text{s}} = screenwidth \cdot \frac{x_{\text{c}} + 1}{2},\qquad
y_{\text{s}} = screenheight \cdot (1 - \frac{y_{\text{c}} + 1}{2})
$$

Compute:

* $x_{\text{s}} = \hspace{4cm} \text{px}$
* $y_{\text{s}} = \hspace{4cm} \text{px}$
