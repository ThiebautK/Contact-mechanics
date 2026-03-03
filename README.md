# Contact-mechanics

# Hertzian Cylinder–Plane Contact

## With and Without Friction (McEwen Extension)

This repository provides two Python implementations of the classical Hertzian contact problem for a cylinder in contact with a plane:

1. **Frictionless Hertzian contact**
2. **Hertzian contact with friction**, following McEwen’s analytical formulation

The objective of these notebooks is to provide transparent, reusable, and well-structured tools to compute:

* Contact geometry
* Contact pressure distribution
* Subsurface stress components
* Von Mises equivalent stress field
* Stress maps and visualizations

The codes are intended for educational purposes, preliminary engineering assessment, and validation of numerical models (e.g. FEM).

---

# 1. Problem Description

We consider a 2D plane strain Hertzian contact between:

* A cylinder of radius ( R )
* A semi-infinite elastic half-space
* Normal load per unit length ( F' )

Under classical Hertz assumptions:

* Linear elasticity
* Small deformations
* Smooth surfaces
* Non-conforming contact
* No plasticity

Two cases are implemented:

## Case A — Frictionless Contact

Classical Hertz solution:

* Normal pressure distribution:
  [
  p(x) = p_0 \sqrt{1 - \left(\frac{x}{a}\right)^2}  ]
  
* No tangential traction
* Subsurface stresses derived from analytical elasticity solutions

## Case B — Contact with Friction (McEwen)

* Coulomb friction coefficient ( \mu )
* Tangential traction proportional to local pressure
* Modified subsurface stress field
* Von Mises stress including shear contribution

The frictional formulation follows the classical McEwen analytical approach for cylinder-plane contact under full sliding conditions.

---

# 2. Repository Structure

* `Hertz_Cylinder_Plane_Frictionless.ipynb`
  → Classical Hertz solution (no friction)

* `Hertz_Cylinder_Plane_With_Friction.ipynb`
  → McEwen-based extension including friction

Each notebook is self-contained and includes:

* Parameter definition section
* Analytical functions
* Field computation
* Visualization of stresses

---

# 3. What the Code Computes

For given material and loading parameters:

* Effective elastic modulus ( E' )
* Contact half-width ( a )
* Maximum pressure ( p_0 )

The scripts compute:

* ( \sigma_x(x,z) )
* ( \sigma_z(x,z) )
* ( \tau_{xz}(x,z) )
* Von Mises equivalent stress:
  [
  \sigma_{VM} = \sqrt{\sigma_x^2 + \sigma_z^2 - \sigma_x \sigma_z + 3\tau_{xz}^2}  ]

Stress fields are evaluated on a 2D grid beneath the contact.

---

# 4. Assumptions and Limitations

These models assume:

* Linear elastic materials
* Plane strain conditions
* No plasticity
* No adhesion
* No surface roughness
* Full sliding in frictional case (no partial slip treatment)

The frictional model does **not** implement Mindlin partial slip conditions.
It corresponds to full sliding with Coulomb traction.

For high loads approaching yielding, results should be interpreted cautiously.

---

# 5. Typical Applications

These notebooks may be useful for:

* Tribology studies
* Rolling contact fatigue estimation
* Gear or bearing preliminary design
* Analytical validation of FEM simulations
* Teaching contact mechanics

---

# 6. Dependencies

* Python 3.x
* NumPy
* Matplotlib

Optional:

* SciPy (if extended)
* Jupyter Notebook environment

Install dependencies via:

```bash
pip install numpy matplotlib
```

---

# 7. How to Use

1. Open the notebook in Jupyter.
2. Modify:

   * Radius
   * Load
   * Material properties
   * Friction coefficient (for frictional case)
3. Run all cells.
4. Inspect stress maps and peak stress locations.

You can easily extend the code to:

* Parameter sweeps
* Maximum stress vs friction plots
* Depth of maximum shear analysis
* Fatigue criteria implementation

---

# 8. Engineering Notes

* The maximum shear stress in frictionless Hertz contact typically occurs below the surface (~0.78a depth).
* Friction shifts and amplifies subsurface shear stresses.
* Increasing friction coefficient increases surface shear and von Mises stress.
* Plane strain assumption is appropriate for long cylinders.

Users working in rolling contact fatigue or bearing mechanics may adapt this framework to include:

* Residual stresses
* Plasticity correction
* Multi-axial fatigue criteria

---

# 9. Validation

The frictionless solution matches classical Hertzian analytical results.

The frictional solution follows McEwen’s analytical expressions for 2D sliding contact.

Users are encouraged to:

* Compare against FEM simulations
* Validate peak stress depth
* Check convergence with grid refinement

---

# 10. Contribution

Improvements are welcome, including:

* Code optimization
* Partial slip implementation
* Plasticity extensions
* 3D contact extension
* Benchmark comparisons
