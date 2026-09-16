---
layout: page
title: Anisotropic displacement parameters
img: assets/img/projects/aniso.png
importance: 3
category: research
giscus_comments: false
---

This guide explains what anisotropic displacement parameters (ADPs) are, how to read the ellipsoids they describe, what they have revealed in real materials, and how to refine and check them in TOPAS and VESTA. 
It is written for students who are comfortable with a basic Rietveld refinement and want to go beyond a single isotropic *B* value.

# What are atomic displacement parameters?

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso1.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Atoms are never perfectly still. Thermal vibration, and sometimes static disorder, spread each atom over a small volume around its average position. The simplest description is isotropic: a sphere with a single size parameter. In most real structures, however, atoms move more easily in some directions than others, and the motion is better described by an ellipsoid.

The size, shape and orientation of that ellipsoid are not just cosmetic. Directional motion modulates orbital overlap and electron scattering, changes phonon transport, alters polarizability and dielectric response, opens or closes ion-diffusion pathways, and perturbs magnetic exchange.

# The displacement tensor U, and the B and β conventions

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso2.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

The ellipsoid is described by a symmetric 3×3 tensor *U*, in units of Å². The diagonal terms U₁₁, U₂₂ and U₃₃ are mean-square displacements along the three axes. The off-diagonal terms U₁₂, U₁₃ and U₂₃ describe correlated motion along two axes, which tilts the ellipsoid. (Strictly, the Uij are referred to the reciprocal-axis directions; for orthogonal cells these coincide with a, b and c.)

Different programs use different parameters. *U* is used by SHELX, Olex2 and the TOPAS `adps` keyword. *B* = 8π²U is the familiar isotropic value (`beq` in TOPAS). *β*<sub>ij</sub> = 2π² a<sub>i</sub>* a<sub>j</sub>* U<sub>ij</sub> is dimensionless and appears in older literature and software. As a rough guide to sensible Beq values: about 0.5 Å² for tightly bonded metal–oxygen frameworks, 1–2 Å² as a starting value for most inorganic sites, and 3–5 Å² for organic molecules or loosely bound atoms.

# How ADPs show up in diffraction data

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso3.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Displacements are refined through the Debye–Waller factor, which damps the scattered intensity. Smearing an atom out matters little for widely spaced planes (low Q) but washes out closely spaced planes (high Q). In the isotropic case the damping depends only on |Q|; in the anisotropic case it also depends on the direction of the scattering vector, which is what allows the individual Uij to be determined.

This has practical consequences. The X-ray form factor is the Fourier transform of the electron density, so it decays with Q and the high-Q reflections that carry most ADP information are weak, especially for light atoms. Neutrons scatter from point-like nuclei, so scattering lengths do not fall off with Q, making neutron data particularly valuable for reliable ADPs of light elements. Either way, **accurate ADPs need high-resolution, high-Q data.**

# 2. Diagonal terms: spheres, rugby balls and pancakes

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso4.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

If U₁₁ = U₂₂ = U₃₃ and all off-diagonal terms are zero, the displacement is a sphere. If one diagonal term is larger than the other two, the ellipsoid is prolate (a "rugby ball") elongated along that axis. If one term is smaller, it is oblate (a "pancake" or m&m), flattened along that axis. The small unit-cell renderings show the same idea on a lattice: increasing only U₃₃ stretches every atom along c, while decreasing U₃₃ gives pancakes lying in the ab plane.

# Off-diagonal terms: tilt

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso5.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Non-zero off-diagonal terms rotate the ellipsoid so that its long axis points between two crystallographic axes. The sign sets the sense of the tilt: a positive U₁₃ tilts the long axis toward +z when moving along +x, and a negative U₁₃ reverses the tilt. When all terms are unequal and non-zero, as in the compound example, you can read the shape from the diagonal (here a small U₃₃ gives a pancake) and the orientation from the shears (here tilted out of the ab plane).

# Site symmetry decides which Uij are allowed

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso6.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

An ellipsoid must look the same after every symmetry operation of its Wyckoff site, so U = R U Rᵀ for each site operation R. For example, if a twofold or fourfold axis runs along c, one principal axis of the ellipsoid must lie along c, which forces U₁₃ = U₂₃ = 0. Complete tables of these restrictions for every site symmetry were given by Peterse & Palm (1966) and are in International Tables.

In the vacancy-ordered double perovskite K₂SnCl₆ (Fm–3m), Sn (4a, m–3m) and K (8c, –43m) sit on cubic sites, so their ellipsoids must be spheres with no shear terms. Cl at (x, 0, 0) on 24e has 4mm symmetry with the fourfold axis along a: U₁₁ is independent, U₂₂ = U₃₃ (circular in the bc plane), and all off-diagonal terms are zero.

# A word of caution: count your parameters

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso7.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Switching from isotropic to anisotropic displacements can add up to five extra parameters per site. In a high-symmetry structure such as NaCl nothing is added, because both sites are forced to remain spheres. In K₂SnCl₆ only the Cl site gains one parameter. In a low-symmetry structure such as monoclinic VS₄, atoms on general positions have all six Uij free. Before refining ADPs, ask whether your data – resolution, Q-range and counting statistics – can genuinely support the extra parameters.

# ADPs and transport

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso8.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

In YBa₂Cu₃O₇₋ₓ, the superconducting orthorhombic phase has oxygen ordered on (0, ½, 0), forming one-dimensional Cu–O chains along b. As oxygen content drops, anisotropic displacement of the chain oxygen develops into disorder within the plane, the chains are lost, the structure becomes tetragonal and superconductivity is suppressed (Jorgensen et al., 1987).

In the NaSICON family Na₂ScᵧZr₂₋ᵧ(SiO₄)₁₋ᵧ(PO₄)₂₊ᵧ, directional Na displacements map directly onto the diffusion pathways found by maximum-entropy, bond-valence and molecular-dynamics analyses. Increasing Sc³⁺ substitution reduces the Na ADPs, which correlates with lower Na⁺ mobility and conductivity (Deng et al., 2018).

# ADPs and lattice dynamics

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso9.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Unusually large, strongly temperature-dependent Cs ADPs revealed Cs⁺ "rattling" in oversized cages. These localised low-frequency vibrations scatter acoustic phonons and disrupt heat transport along c, giving glass-like thermal conductivity below the theoretical minimum (Newnham et al., 2023).

In the Cs₂(Na/Ag)BiCl₆ double perovskites, the more ionic Na–Cl interaction lets Na⁺ motion couple to specific low-frequency lattice modes, giving strongly anisotropic displacements that weaken on cooling. Heavier, more covalently bonded Ag⁺ (d¹⁰) shows damped, more isotropic motion. The Cl⁻ ellipsoids form pancakes perpendicular to the M–Cl bond, reflecting octahedral tilting and libration (Tian et al., submitted).

# Hidden disorder in (H/D)RhO₂

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso10.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Refinement of neutron data for delafossite (H/D)RhO₂ gave strongly elongated (H/D)⁺ ellipsoids along c. That prompted a closer look: Fourier and maximum-entropy maps showed the nuclear density splitting into two sites. PDF, NMR, vibrational spectroscopy and DFT (a double-well potential) confirmed the splitting, and molecular dynamics showed the disorder is random. The result is strong yet split hydrogen bonding obeying ice rules on a triangular lattice (Wright et al., 2025).

The general lesson: an ADP that is much larger or more elongated than the chemistry suggests is often the first sign that a single average site is the wrong model.

# Refining ADPs in TOPAS

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso11.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

TOPAS refines isotropic displacements by default, through the `beq` term at the end of each `site` line. To switch a site to anisotropic displacements, delete `beq @ 0.1` and type `adps`. After one refinement cycle TOPAS replaces this with the full `ADPs(...)` macro, listing U₁₁, U₂₂, U₃₃, U₁₂, U₁₃ and U₂₃ with the site-symmetry constraints already applied. Check that those constraints match the Wyckoff site; general positions have none. By default TOPAS keeps every site positive definite.

To write the results to a CIF, use `Out_PowderCIFDataBlock` for an IUCr-style CIF, `Out_CIF_ADPs_diamond` for Diamond (`Out_CIF_diamond` gives only isotropic B), or `Out_CIF_crystalmaker` for CrystalMaker. Alternatively, write a basic CIF with `Out_CIF_STR(...)` and a separate ADP file with `Out_CIF_ADPs(...)`, then merge them with a script.

# Viewing ellipsoids in VESTA

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso12.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

In VESTA, open Edit → Edit Data → Structure Parameters, choose U in the anisotropic drop-down and check that the Uij boxes are populated. Then use Objects → Properties to display atoms as displacement ellipsoids. A 50% probability surface is standard for publication, while 99% exaggerates the shapes, which is useful for teaching. Drawing the principal axes makes tilts much easier to see.

# Troubleshooting

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso13.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Cubes, flat plates or other odd symbols in place of ellipsoids mean the refined tensor is not physically sensible. Look for negative diagonal terms (never allowed) and values stuck at zero or at their limits. A shallow local minimum can sometimes be escaped by resetting the ADPs and refining again; otherwise the problem may lie in the structural model itself.

Be deliberate about what you refine simultaneously, in what order, and whether anything can be constrained, restrained or fixed. The correlation matrix is the best diagnostic: switch it on before refining and look for values close to ±100%, which mark parameters the data cannot separate. Naming parameters with `prm` makes the matrix much easier to read.

# Known TOPAS issues and workarounds

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso14.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Some refinement programs fail to impose site-symmetry constraints on ADPs, so always check. A few space group and Wyckoff site combinations can also cause TOPAS to crash, including the common Fd–3m (No. 227). The TOPAS wiki provides a set of macros (`ADP_0` to `ADP_18`) that apply the constraints for each site type by hand, and an `adp_no_limits` macro that lets ADPs move outside positive-definite limits. Only allow negative ADPs if you have a physical reason; conversely, `ADPs_Keep_PD` can be used to keep the tensor positive definite and stabilise a refinement. Macros credit: Matthew Rowles.

# Further reading and resources

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/aniso15.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

- *TOPAS wiki* – [ADPs with symmetry constraints](https://topas.awh.durham.ac.uk/doku.php?id=adps_with_symmetry_constraints) and [anisotropic temperature factors](https://topas.awh.durham.ac.uk/doku.php?id=anisotropic_temperature_factors)
- *UCL powder diffraction course* – [pd.chem.ucl.ac.uk](http://pd.chem.ucl.ac.uk/)
- *VESTA* – [jp-minerals.org/vesta](https://jp-minerals.org/vesta/)

# References

- Trueblood, K. N. et al. (1996). *Acta Cryst.* A52, 770–781. Atomic displacement parameter nomenclature.
- Peterse, W. J. A. M. & Palm, J. H. (1966). *Acta Cryst.* 20, 147–150. [Link](https://journals.iucr.org/paper?a04978)
- Coelho, A. A. (2018). *J. Appl. Cryst.* 51, 210–218. TOPAS.
- Momma, K. & Izumi, F. (2011). *J. Appl. Cryst.* 44, 1272–1276. VESTA 3.
- Jorgensen, J. D. et al. (1987). *Phys. Rev. B* 36, 3608.
- Deng, Y. et al. (2018). *Chem. Mater.* 30, 2618–2630.
- Newnham, J. A. et al. (2023). *J. Mater. Chem. A* 11, 15739–15748.
- Wright, M. A. et al. (2025). Strong, yet split hydrogen bonding with ice rules in delafossite (H/D)RhO₂. *Angew. Chem.* e15471.
- Tian, H. et al. Structural propensities in Cs₂MBiX₆ (M = Na, Ag; X = Cl, Br) bismuth halide double perovskites. Submitted (2025).

*Image credits:* ellipsoid renderings, structure images and screenshots are from the original lecture slides, "Anisotropic Displacement Parameters: Probing Atomic Motion in Crystals" (M. A. Wright, 2025). Case-study figures are reproduced from the publications cited on each slide. Title image is adapted from George Sheldricks [*Methods in Chemistry III*](https://www.ccdc.cam.ac.uk/media/resources/mc3_10_10e.pdf). 
