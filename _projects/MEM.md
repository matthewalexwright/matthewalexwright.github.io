---
layout: page
title: The Maximum Entropy Method with Jana, BayMEM and VESTA
img: assets/img/projects/MEM.png
importance: 2
category: research
giscus_comments: false
---


# The Maximum Entropy Method with Jana, BayMEM and VESTA

This guide is for students who already have a Rietveld refinement and want to look *beyond* the model at the actual electron density in their material. It is built on three sources: the BayMEM user manual (Palatinus & van Smaalen, 2005), and Chapter 4.8 of *International Tables for Crystallography* Vol. H (Magdysyuk, van Smaalen & Dinnebier, 2019), and the Jana2006/BayMEM screenshot tutorial by T. Wesley Surta (2020). 

The guide is organised around four questions. 

1. What is MEM, when is it used, and why?
2. How do we perform the calculation?
3. How do we analyse the result?
4. Where can we go for more?

## The problem with Fourier maps.

The electron density is the Fourier transform of the structure factors. In principle, if we knew every structure factor (amplitude *and* phase) we could calculate the density exactly. In practice we only measure a finite number of reflections, each with noise, and powder data are further limited by peak overlap.
Cutting off the Fourier sum produces *series-termination* artefacts: ripples, spurious peaks and regions of negative electron density that are not physical. International Tables notes that a ripple-free Fourier map would need data out to about sin θ/λ = 6 Å⁻¹, far beyond any real experiment. The silicon example on the slide shows how badly this can obscure the bonding density that MEM recovers from the same data.


<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM2.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>


### The principle of maximum entropy

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM3.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

MEM divides the unit cell into a grid of pixels and looks for the set of pixel densities ρᵢ that maximises the entropy S = −Σ ρᵢ ln(ρᵢ/τᵢ), while still agreeing with the measured structure factors to within their uncertainties (the *F constraint*) and containing the right number of electrons.

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM4.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Three consequences are worth remembering:

- **Positivity.** The solution is exponential in form, so the density can never become negative.
- **Least bias.** Among all maps consistent with the data, MEM picks the one that adds the least extra information, so it does not invent correlations the data do not require.
- **The prior τ matters.** With no data, MEM simply returns the prior. A flat prior assumes nothing; a *procrystal* prior (superposed free atoms from your model) reduces artefacts and is needed if you want to study bonding or charges.

MEM shines when the average structural model is too simple: disordered or split sites, anharmonic or off-centre displacements, missing atoms (such as guest molecules in pores), ion diffusion pathways and, with high-resolution data and a good prior, the redistribution of density in chemical bonds. The LiCp* example on the slide resolves fifteen disordered methyl positions that the Fourier map smears into a ring.

Be cautious when the data resolution is low, when many reflections overlap, or when the background and scale are poorly determined. MEM cannot fix bad data, and its sharp-looking maps can make noise look convincing.

### Every MEM map carries some model bias

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM5.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

MEM needs phased structure factors. For powder data the phases, and the way intensity is shared between overlapping peaks, usually come from the structural model. The flow chart (Int. Tables Fig. 4.8.6, after Samy et al., 2010) ranks different choices from "completely biased" to "unbiased".

The Jana → BayMEM route described below uses **Fobs with φcalc**, which is *partially* biased. It is very good at revealing what the model is missing, but you should always ask whether a feature could simply be your model reflected back at you.

## 2. How to perform the calculation

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM6.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

The whole procedure has five steps: fit the pattern in Jana, export a BayMEM input file, run BayMEM, load the resulting map back into Jana, and visualise it in VESTA.

You need Jana2006 or Jana2020 (free), BayMEM (free for academic use by licence request from the University of Bayreuth), and VESTA (free). Tell Jana where VESTA is installed (Tools → Programs) before you start, otherwise the 3D map step will not work.

### Step 1 – get a good fit in Jana

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM7.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Start with a Le Bail fit ("Make only profile matching" in the Refine options) to get the lattice parameters, zero shift and peak shape right. Where possible, take instrumental profile parameters from the beamline. Then switch to a Rietveld refinement: scale factor first, then ADPs, occupancies and any constraints.

**The background is critical.** The observed structure factors are extracted from the pattern, so a poor background gives wrong Fobs and therefore a wrong map. Use enough Chebyshev terms or Jana's manual background tool. Keep "Automatic refinement keys" switched off and refine step by step, saving backups as you go.

The model does not need to be perfect – MEM is there to show you what it misses – but peak positions and overall intensities must be well described.

### Step 2 – write the BayMEM input from Jana

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM8.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Use **Tools → Files for MEM → BayMEM**. Select *MEM* and include the phased, observed structure factors. The most important setting is the **pixel division**, which defines the grid. It must be fine enough to resolve the features you are interested in (roughly 0.05–0.1 Å per pixel is a reasonable target), must respect the symmetry (for example a multiple of 2 along a 2₁ screw axis), and is fastest when the numbers have only small prime factors. Finer grids need much more memory.

Jana writes `jobname.BayMEM` into your refinement folder.

### Inside the .BayMEM input file

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM9.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

The input is a plain keyword file, so it is worth opening and checking. `algorithm` chooses the Sakata–Sato method (built in) or the Cambridge algorithm (requires the commercial MemSys5 library). `voxel` and `cell` define the grid, `electrons` normalises the map and must match F(000), `initialdensity` selects a flat or file-based prior, and the reflection list lives between `fbegin` and `endf`.

Useful optional keywords include `conweight` (static weighting), `conorder` (generalised F constraint), `priorsf` (prior-derived F constraints) and `gbegin…endg` (groups of overlapping reflections). See Chapter 5 of the BayMEM manual for the full list.

### Step 3 – run BayMEM

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM10.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Run `BayMEM jobname` from a terminal (no file extension), or place the `.BayMEM` file next to `BayMEM.exe`, double-click it and type the job name. If the window closes immediately, something is wrong with the input – look at the `.BMlog` file.

The key outputs are the density map (`.m81`, in Jana format), a summary (`.BMout`), the detailed log (`.BMlog`) and a histogram of residuals (`.BMhst`). To stop a long run early and still write the output, create a file `jobname.BMcom` containing the word `STOP`.

### Choices that change your map

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM11.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

The Sakata–Sato algorithm is fast and flexible but not guaranteed to converge; the Cambridge algorithm is more rigorous but less flexible. A flat prior is simplest, but International Tables warns that it can produce artefacts larger than bonding features; a procrystal prior is better for fine detail.

The stopping value χ²aim is also a choice: too small and you fit noise, too large and you leave real signal unfitted. If a handful of strong low-angle reflections have very large residuals, static weights or a fourth-order constraint usually give a more Gaussian residual distribution and a cleaner map.

---

## 3. How to analyse the result

did it converge sensibly?

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM12.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>
Before looking at pictures, open `.BMlog`. The run has converged when the constraint value drops below the aim. Check that the final R values are low, that the odd moments of the residual distribution (FCon(1), FCon(3)…) are close to zero and the even ones close to one, and that the histogram in `.BMhst` looks roughly Gaussian.

If convergence stalls, the most common causes (manual Chapter 8) are an electron count inconsistent with F(000), symmetry operators that do not form a group or disagree with `centro`, or systematically absent reflections left in the list.

### Step 4 – load the map back into Jana

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM13.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Copy `jobname.m81` into the refinement folder, making sure it has the same base name as the structure. Open the refinement, go to **Contour**, and choose **New plot**. "Use old maps" is now available because Jana finds the `.m81` file. The 2D view in Jana is fine for a quick check; **Run 3d maps** sends the density and structure to VESTA.

### Step 5 – 3D isosurfaces in VESTA

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM14.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

VESTA opens the MEM density on top of the Rietveld structure. Hide the atoms and bonds when judging the density so that the model does not guide your eye.

**Save the map straight away** with File → Export Data as a `.grd` file; the temporary map is otherwise lost. Then explore different isosurface levels (Objects → Properties → Isosurfaces) and always report the level you show, in e Å⁻³.

### Step 6 – 2D slices through the density

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM15.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

Slices are often more informative than isosurfaces. Use Utilities → 2D Data Display, add a slice through the plane of interest, and set sensible saturation levels (the default scale is dominated by the heaviest atoms). Slices can be overlaid on the 3D view via Edit → Lattice Planes. Use identical levels when comparing samples or temperatures.

### Interpreting the map: a worked example

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM16.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

In the KBMN example (Surta et al., *J. Am. Chem. Soc.* 2021, 143, 1386–1398), slices through the Bi site show clearly non-spherical density: the cation is displaced away from the ideal position, something a single atom with a large ADP hides.

Off-centre maxima indicate static or dynamic displacements; peak heights track occupancy for split sites. Use what you learn to improve the model and re-refine. Most importantly, test whether a feature is robust: does it survive a different prior, grid, χ²aim or isosurface level? If not, treat it as noise.

### Going further, and common pitfalls

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM17.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

The MEM/Rietveld or *REMEDY* cycle alternates Rietveld refinement and MEM, using each map to improve the model until the R factors stop improving. Strictly it bends MEM's statistical rules, but International Tables notes it has worked in many applications.

Keep the pitfall checklist on the slide handy – most bad MEM maps trace back to the background, the grid, the electron count, the symmetry, or over-interpreting a single isosurface.

---

## 4. Further reading and support

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM18.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

### Software, manuals and help

- **BayMEM** – [crystal.uni-bayreuth.de/en/baymem](https://www.crystal.uni-bayreuth.de/en/baymem/) (free academic licence on request)
- **Jana2020 / Jana2006** – [jana.fzu.cz](http://jana.fzu.cz)
- **VESTA** – [jp-minerals.org/vesta](https://jp-minerals.org/vesta/)
- **Dysnomia** – an alternative MEM program for use with RIETAN-FP (Momma et al., 2013)
- **International Tables Vol. H, Ch. 4.8** – [it.iucr.org](https://it.iucr.org) – the best single overview of MEM for powder data

If you get stuck, check `.BMlog` and Chapter 8 of the BayMEM manual first, then ask your group with your `.BayMEM` input and `.BMlog` attached.

### Key references

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/MEM19.png" class="img-fluid rounded z-depth-1" zoomable=true %}
</div>

- Magdysyuk, O. V., van Smaalen, S. & Dinnebier, R. E. (2019). *International Tables for Crystallography* Vol. H, Ch. 4.8, 473–488.
- Palatinus, L. & van Smaalen, S. (2005). *BayMEM user manual.*
- Sakata, M. & Sato, M. (1990). *Acta Cryst.* A46, 263–270.
- van Smaalen, S., Palatinus, L. & Schneider, M. (2003). *Acta Cryst.* A59, 459–469.
- Palatinus, L. & van Smaalen, S. (2002). *Acta Cryst.* A58, 559–567.
- Palatinus, L. & van Smaalen, S. (2005). *Acta Cryst.* A61, 363–372.
- de Vries, R. Y., Briels, W. J. & Feil, D. (1994). *Acta Cryst.* A50, 383–391.
- Hofmann, A., Netzel, J. & van Smaalen, S. (2007). *Acta Cryst.* B63, 285–295.
- Samy, A., Dinnebier, R. E., van Smaalen, S. & Jansen, M. (2010). *Acta Cryst.* B66, 184–195.
- Takata, M. (2008). *Acta Cryst.* A64, 232–245.
- Petříček, V., Dušek, M. & Palatinus, L. (2014). *Z. Kristallogr.* 229, 345–352.
- Surta, T. W. et al. (2021). *J. Am. Chem. Soc.* 143, 1386–1398. [doi:10.1021/jacs.0c10572](https://doi.org/10.1021/jacs.0c10572)

**Image credits:** screenshots are from T. W. Surta, "Maximum Entropy Method using Jana2006 and BayMEM" (2020). Figures 4.8.2, 4.8.3, 4.8.6 and 4.8.8 are reproduced from *International Tables for Crystallography* Vol. H (2019), © International Union of Crystallography, with original sources as credited on each slide. The KBMN figure is from Surta et al. (2021), published under CC-BY.
