# 3D Computer Graphics

## Math Readiness Worksheet

**Due:** Beginning of next class

**Purpose:** This worksheet reviews the math concepts you will use throughout this course.

It is not a test — it is meant to help you identify what you already know and what you should review.

You are expected to **show your work** where appropriate.

---

## Instructions

* You may use notes, textbooks, or online resources.
* Calculators are allowed.
* If a problem feels unfamiliar, try it anyway — that’s useful information.
* At the end of each section, reflect briefly on your confidence.

---

## 1. Trigonometry

### 1.1 Degrees and Radians

1. Convert the following angles to **radians**:

   * a) $90^\circ$
   * b) $180^\circ$
   * c) $45^\circ$

2. Convert the following angles to **degrees**:

   * a) $\frac{\pi}{2}$
   * b) $\pi$
   * c) $\frac{3\pi}{4}$

---

### 1.2 Right-Triangle Definitions

For a right triangle with angle $\theta$:

$$
\sin(\theta) = \frac{\text{opposite}}{\text{hypotenuse}}
$$

$$
\cos(\theta) = \frac{\text{adjacent}}{\text{hypotenuse}}
$$

$$
\tan(\theta) = \frac{\text{opposite}}{\text{adjacent}}
$$

1. Given a right triangle where the opposite side has length $3$ and the adjacent side has length $4$:

   * a) Compute $\sin(\theta)$
   * b) Compute $\cos(\theta)$
   * c) Compute $\tan(\theta)$

2. If $\sin(\theta) = 0.6$ and the hypotenuse has length $10$, what is the length of the opposite side?

---

### 1.3 Polar Coordinates

In polar coordinates, a **point** is described using a radius $r$ and an angle $\theta$.

1. For each set of polar coordinates below:

   * First **draw the point** described by the polar coordinates.

   * Then convert it to Cartesian **points** $(x, y)$:

   * a) $r = 1$, $\theta = 0$

   * b) $r = 1$, $\theta = \frac{\pi}{2}$

   * c) $r = 2$, $\theta = \pi$

2. A point has polar coordinates $r = 5$, $\theta = \frac{\pi}{4}$.

   * a) Write the Cartesian point $(x, y)$.
   * b) Sketch the point.

---

### Confidence Check

> How confident do you feel using radians, right-triangle trig, and polar coordinates?
> ☐ Very confident ☐ Somewhat confident ☐ Not confident

---

## 2. Vectors

> **Notation:** Vectors are written using arrow notation, for example $\vec{v}$.
> Vector components are written using angle brackets, for example $\langle 1, 2, 3 \rangle$.
> Points are written using parentheses, for example $(x, y)$.

---

### 2.0 What Is a Vector?

A **vector** represents a direction and a magnitude.

In 2D, vectors are often drawn as arrows starting at the origin or at a point in space.

1. On a 2D coordinate plane, **draw and label** the following vectors starting at the origin:

   * $\vec{a} = \langle 3, 1 \rangle$
   * $\vec{b} = \langle -2, 2 \rangle$
   * $\vec{c} = \langle 1, -3 \rangle$

2. For each vector above, describe in words:

   * Its general direction
   * Whether it is longer or shorter than the others

---

### 2.1 Vector Basics

Let

$$
\vec{a} = \langle 2, -1, 3 \rangle, \quad
\vec{b} = \langle -1, 4, 0 \rangle
$$

1. Compute:

   * a) $\vec{a} + \vec{b}$
   * b) $\vec{a} - \vec{b}$
   * c) $2\vec{a}$

---

### 2.2 Magnitude and Normalization

1. Compute the magnitude of the vector

$$
\vec{v} = \langle 3, 4 \rangle
$$

2. Normalize $\vec{v}$.

---

### 2.3 Using a Vector as a Displacement

A vector can be used to **move** (displace) a point.

Let the starting point be

$$
P = (2, 1)
$$

and let the displacement vector be

$$
\vec{d} = \langle 3, -2 \rangle.
$$

1. Compute the new point after applying the displacement:

$$
P' = P + \vec{d}
$$

2. Draw the point $P$, the vector $\vec{d}$, and the resulting point $P'$.

---

### 2.4 Vector from Point A to Point B

Given two points

$$
A = (1, 2), \quad B = (6, 5)
$$

1. Find the vector $\vec{v}$ that moves from point $A$ to point $B$.

2. Verify your answer by checking that:

$$
A + \vec{v} = B
$$

3. Explain in one sentence why this vector represents the displacement from $A$ to $B$.

---

### 2.5 Dot Product

Let

$$
\vec{u} = \langle 1, 0, 0 \rangle, \quad
\vec{v} = \langle 0, 1, 0 \rangle
$$

1. Compute $\vec{u} \cdot \vec{v}$.
2. What does this result tell you about the angle between the two vectors?

---

### 2.6 Cross Product (3D)

Let

$$
\vec{x} = \langle 1, 0, 0 \rangle, \quad
\vec{y} = \langle 0, 1, 0 \rangle
$$

1. Compute $\vec{x} \times \vec{y}$.
2. Is the resulting vector perpendicular to both input vectors? How can you tell?

---

### Confidence Check

> How confident do you feel working with vectors and vector-based motion?
> ☐ Very confident ☐ Somewhat confident ☐ Not confident

---

## 3. Matrices (3×3 and Conceptual 4×4)

### 3.1 Matrix–Vector Multiplication

Let

$$
M =
\begin{bmatrix}
1 & 0 & 0 \
0 & 2 & 0 \
0 & 0 & 1
\end{bmatrix}
$$

and

$$
\vec{v} = \langle 1, 2, 3 \rangle
$$

1. Compute $M\vec{v}$.
2. Describe in words what this matrix does to the vector.

---

### 3.2 Identity Matrix

1. Write down the $3 \times 3$ identity matrix.
2. What happens when you multiply any vector by the identity matrix?

---

### 3.3 Matrix Composition

Matrix multiplication is **not commutative**.

1. In your own words, explain what it means for matrix order to matter.
2. Why is this important when applying multiple transformations?

---

### 3.4 Inverses (Conceptual)

1. What does it mean for a matrix to have an inverse?
2. In graphics, when might you want to use an inverse transformation?

---

### Confidence Check

> How confident do you feel about matrix–vector multiplication and matrix order?
> ☐ Very confident ☐ Somewhat confident ☐ Not confident

---

## 4. Parametric Representations & Linear Interpolation (LERP)

> **This section is extremely important.**
> Linear interpolation appears everywhere in computer graphics.

---

### 4.1 Parametric Equations

A point on a line between points $A$ and $B$ can be written as:

$$
\vec{p}(t) = (1 - t)A + tB
$$

Let

$$
A = (0, 0), \quad B = (10, 0)
$$

1. Compute $\vec{p}(t)$ for:

   * a) $t = 0$
   * b) $t = 0.5$
   * c) $t = 1$

2. Where is the point when $t = 0.5$?

---

### 4.2 Normalizing an interval

In graphics, we often start with a value $x$ that lies in an interval $[a, b]$, that we want to move to an equivalent value in a different interval $[c, d]$. For example, $x=5$ is halfway in the interval $[0,10]$; the equivalent value in the interval $[6, 10]$ is $x=8$. This is called linear interpolation.

To use linear interpolation, we first convert $x$ into a parameter $t$ in $[0, 1]$. This process is called normalization.

$$ 𝑡 = \frac {𝑥 − a}{b - a} $$​


This value of $t$ represents where $x$ lies between $a$ and $b$. $t = 0$ means that $x$ is exactly at $a$; $t=1$ means that $x$ is at $b$; $t=0.5$ means that $x$ is halfway from $a$ to $b$.

Compute $t$ when:

a) $x = 5$, $a = 0$, $b = 10$

b) $x = 3$, $a = 1$, $b = 5$

---

### 4.3 Scalar lerp

Linear interpolation (lerp) finds a point $x$ that is $t$ distance between values $u$ and $v$, given the definition of $t$ from the previous section.

$$
\text{lerp}(u, v, t) = (1 - t)u + t\cdot v
$$

1. Compute:

   * a) $\text{lerp}(0, 10, 0.25)$
   * b) $\text{lerp}(5, 15, 0.5)$
 

2. Use the lerp function to compute the equivalent value of the given $x$ of the range $[a,b]$, in the range $[u,v]$. Hint: compute $t$ as in section 4.2, then substitute $t$, $u$, and $v$ in the formula above.

   * a) $x = 5, a = 0, b = 10, u = 100, v = 200$
   * b) $x = 0.5, a = -1, b = 1, u = 0, v = 1080$

---

### Confidence Check

> How confident do you feel using lerp for values and vectors?
> ☐ Very confident ☐ Somewhat confident ☐ Not confident
