# Matrices for 3D space transformations

## A) Local to World

Given:

* A mesh's position, orientation (pitch/yaw/roll), and scale in world space.
* A local-space vertex $v_0$ from the mesh.

### 1) Build the individual transform matrices

Construct the relevant 4x4 transform matrices:
$$\mathbf{A}_{S}=\left(\begin{array}{cccc}
s_{x} & 0 & 0 & 0\\
0 & s_{y} & 0 & 0\\
0 & 0 & s_{z} & 0\\
0 & 0 & 0 & 1
\end{array}\right)$$
$$\mathbf{A}_{yaw}=\left(\begin{array}{cccc}
\cos\theta & 0 & \sin\theta & 0\\
0 & 1 & 0 & 0\\
-\sin\theta & 0 & \cos\theta & 0\\
0 & 0 & 0 & 1
\end{array}\right)$$
$$\mathbf{A}_{pitch}=\left(\begin{array}{cccc}
1 & 0 & 0 & 0\\
0 & \cos\theta & -\sin\theta & 0\\
0 & \sin\theta & \cos\theta & 0\\
0 & 0 & 0 & 1
\end{array}\right)$$
$$\mathbf{A}_{roll}=\left(\begin{array}{cccc}
\cos\theta & -\sin\theta & 0 & 0\\
\sin\theta & \cos\theta & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{array}\right)$$
$$\mathbf{A}_{T}=\left(\begin{array}{cccc}
1 & 0 & 0 & t_{x}\\
0 & 1 & 0 & t_{y}\\
0 & 0 & 1 & t_{z}\\
0 & 0 & 0 & 1
\end{array}\right)$$
You can skip any matrix that isn't relevant to your problem.

### 2) Construct the model matrix

Arrange the matrices in the correct order, then multiply to form a single 4x4 "model matrix".

$$\mathbf{A}_{model}=\mathbf{A}_{T}\cdot\mathbf{A}_{roll}\cdot\mathbf{A}_{pitch}\cdot\mathbf{A}_{yaw}\cdot\mathbf{A}_{S}$$

You can ignore any matrix that isn't relevant (replace them with $I$, which doesn't affect the product).

Compute:

* $\mathbf{A}_{model}=$<br/><br/><br/><br/><br/><br/>

### 3) Multiply model matrix by local space

$$ v_w = \mathbf{A}_{model} \cdot v_0$$

Compute:

* $v_w=$<br/><br/><br/>

## B) World to View, given R/U/F

Given:

* The camera's position in world space, $C$
* The camera's Right, Up, and Forward vectors
* A world-space vertex $v_w$.

---

### 1) Construct the inverse camera matrix

$$
\mathbf{A}_{camera}^{-1}=\left(\begin{array}{cccc}
R_{x} & R_{y} & R_{z} & -dot\left(C,R\right)\\
U_{x} & U_{y} & U_{z} & -dot\left(C,U\right)\\
F_{x} & F_{y} & F_{z} & -dot\left(C,F\right)\\
0 & 0 & 0 & 1
\end{array}\right)
$$

Compute:

* $-dot\left(C,R\right) = \hspace{4cm}$
* $-dot\left(C,U\right) = \hspace{4cm}$
* $-dot\left(C,F\right) = \hspace{4cm}$
* $\mathbf{A}_{camera}^{-1} =$<br/><br/><br/><br/><br/>

### 2) Multiply inverse camera times world space

$$v_e = \mathbf{A}_{camera}^{-1} \cdot v_w $$

Compute:

* $v_e=$<br/><br/>

---

## C) World to View, with LookAt positioning

Given:

* The camera's position in world space, $C$
* A point in world space that the camera is looking at, $At$.
* A world-space vertex $v_w$.

### 1) Construct the normalized R/U/F vectors

$$
F=normalize\left(C-At\right)
$$
$$
R=cross(F, \left<0,1,0\right>)
$$
$$
U=cross(F, R)
$$
If you are lucky, I will give you numbers such that $C-At$ is already unit length, so you won't have to normalize $F$. Otherwise, you must divide the components of $F$ by the magnitude of $F$ to normalize it.

Compute:

* $F = \hspace{4cm}$
* $R = \hspace{4cm}$
* $U = \hspace{4cm}$

### 2) Pass R/U/F to "World to View, Given R/U/F"

Just take your R/U/F vectors, along with C, and do the same math as in the previous section to find $v_e$.

---

## D) View to Clip

Given:

* Frustum parameters $\mathrm{fov}_y$, (n)ear, (f)ar, and aspect ratio $\frac{width}{height}$.

### 1) Compute frustum top and right

$$t=n\cdot \tan\left(\frac{\mathrm{fov}_y}{2}\right),\qquad
r=t\cdot\frac{width}{height}$$

Compute:

* $t=$
* $r=$

### 2) Build the Perspective Projection matrix

$$\mathbf{A}_{perspective}=\left(\begin{array}{cccc}
\frac{n}{r} & 0 & 0 & 0\\
0 & \frac{n}{t} & 0 & 0\\
0 & 0 & \frac{f+n}{n-f} & \frac{2fn}{n-f}\\
0 & 0 & -1 & 0
\end{array}\right)$$

Compute:
* $\mathbf{A}_{perspective}=$<br/><br/><br/><br/>

### 3) Multiply projection matrix times view space

$$ v_c=\mathbf{A}_{perspective}\cdot v_e$$

Compute:
* $v_c=$<br/><br/>

### 4) Divide through by $w$

You will notice that the fourth component ($w$) of $v_c$ is **not 1**, which is required of all vertices 3D spaces. So $v_c$ from the previous step is **incorrect**; you must divide each component by $w$ to get the actual clip-space coordinates

$$v_c = \frac{v_c}{w}$$

Compute:

* $v_c =$