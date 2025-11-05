# Phong Lighting Worksheet — Diffuse & Specular (World Space)

Use this worksheet to compute **diffuse** and **specular** lighting for a single **point light** using the Phong reflection model. All inputs are in **world space**.

---

## 0) Given

Fill in all known values.

* Fragment position $P = (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$
* Fragment normal $\vec{N} = (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$
* Camera/eye position $C = (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$
* Light position $L_{pos} = (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$
* Light intensity/color $I_L = (R: \rule{1cm}{0.15mm}, G: \rule{1cm}{0.15mm}, B: \rule{1cm}{0.15mm})$
  (Use linear color space values in [0,∞). If you have sRGB, convert to linear first.)
* Material diffuse reflectance $k_d = (R: \rule{1cm}{0.15mm}, G: \rule{1cm}{0.15mm}, B: \rule{1cm}{0.15mm})$
* Material specular reflectance $k_s = (R: \rule{1cm}{0.15mm}, G: \rule{1cm}{0.15mm}, B: \rule{1cm}{0.15mm})$
* Shininess/exponent $\alpha = \rule{1cm}{0.15mm}$

---

## 1) Build direction vectors (world space)

1. **Light direction** (from fragment to light):
   $\vec{L} = L_{pos} - P = (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$
2. **View direction** (from fragment to camera):
   $\vec{V} = C - P = (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$

> ✅ Check: Are $\vec{L}$ and $\vec{V}$ **non-zero**? If zero, re-check inputs.

---

## 2) Normalize

Compute unit vectors (mark magnitudes too):

* $|\vec{L}| = \rule{1cm}{0.15mm}; ; \hat{L} = \dfrac{\vec{L}}{|\vec{L}|} = (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$
* $|\vec{V}| = \rule{1cm}{0.15mm}; ; \hat{V} = \dfrac{\vec{V}}{|\vec{V}|} = (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$
* $|\vec{N}| = \rule{1cm}{0.15mm}; ; \hat{N} = \dfrac{\vec{N}}{|\vec{N}|} = (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$

> ✅ Check: $|\hat{N}|$ should be ≈1.0. If your normal is already normalized from the mesh/shader, record 1.0 here.

---

## 3) Diffuse component

Compute the cosine factor:

* $cosine = \hat{N} \cdot \hat{L} = \rule{1cm}{0.15mm}$
* $lambert = \max(cosine, 0) = \rule{1cm}{0.15mm}$

Diffuse color (per channel):

* $C_{diff} = k_d \cdot I_L \cdot lambert$
  $= (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$


---

## 4) Specular component

1. Build the **reflection** of $-\hat{L}$ about $\hat{N}$:

   $\hat{R} = \mathrm{reflect}(-\hat{L}, \hat{N})$
   $= 2(\hat{N} \cdot (-\hat{L}))\hat{N} - (-\hat{L})$
   $= (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$

2. Cosine factor (clamped):

   $cosine = \hat{R} \cdot \hat{V} = \rule{1cm}{0.15mm}$
   $spec = \max(cosine, 0) = \rule{1cm}{0.15mm}$

3. Specular color (per channel):

   $C_{spec} = k_s \cdot I_L \cdot (spec)^{\alpha}$
   $= (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$

---

## 5) Combine terms

$C_{total} = C_{diff} + C_{spec}$
$= (\rule{1cm}{0.15mm}, \rule{1cm}{0.15mm}, \rule{1cm}{0.15mm})$

---

## 6) Practice problems 

**Problem A (Phong)**

* $P=(1,2,3)$, $\vec{N}=(0,1,0)$, $C=(1,2,8)$, $L_{pos}=(4,3,6)$
* $k_d=(0.8,0.7,0.6)$, $k_s=(0.2,0.2,0.2)$, $\alpha=32$
* $I_L=(3.0,3.0,3.0)$

Compute: $C_{diff}$, $C_{spec}$, $C_{total}$. 

**Problem B (Phong)**

* $P=(-2,0,1)$, $\vec{N}=(0,0,1)$, $C=(0,0,5)$, $L_{pos}=(3,4,2)$
* $k_d=(0.6,0.6,0.9)$, $k_s=(0.5,0.5,0.5)$, $\alpha=16$
* $I_L=(1.0,0.8,0.6)$

Compute: $C_{diff}$, $C_{spec}$, $C_{total}$.
