---
layout: page
title: thermodynamics of electrochemical insertion reactions
img: assets/img/projects/thermo1.png
importance: 2
category: research
giscus_comments: false
---

Why does one electrochemical cell hold a flat, steady voltage while another slowly slopes downward as it discharges? The answer lies in thermodynamics. Below are slides that relate phase diagrams to free energy curves that dictate the voltage profile of a battery electrode.

We start with a single-component system. When heat is added to ice, the temperature stops rising while ice and water coexist, because all the energy goes into the phase change. The Gibbs phase rule explains why: with two phases present at constant pressure, there are no degrees of freedom left, so the temperature is pinned until the transition is complete.

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/thermo2.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  <div class="caption">The phase diagram of water and its heating curve. Plateaus appear wherever two phases coexist.</div>
</div>

The same logic applies to batteries. In a Li-ion cathode such as LiCoO<sub>2</sub>, charging pulls Li out of the layers between the CoO<sub>2</sub> sheets and oxidises cobalt, while discharging puts it back. The electrode is therefore a material whose composition, x in Li<sub>x</sub>CoO<sub>2</sub>, changes continuously during cycling.

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/thermo3.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  <div class="caption">Li is removed from and reinserted into the layered LiCoO<sub>2</sub> structure during charge and discharge.</div>
</div>

Because the electrode is effectively a two-component system (LiMA and MA), we can read it like a binary phase diagram at a fixed temperature. With temperature and pressure held constant, the phase rule becomes F = C − P. In a single-phase region there is one degree of freedom, so the voltage changes with composition. In a two-phase region there are none, so the voltage stays flat.

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/thermo4.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  <div class="caption">A slice through a binary phase diagram maps directly onto a voltage profile: sloping in single-phase regions, flat across the α+β two-phase region.</div>
</div>

If the phase diagram contains an additional intermediate phase, the horizontal slice crosses more boundaries. Each new two-phase region produces its own plateau, and each single-phase region between them appears as a sharp step in voltage.

<div class="l-body" style="max-width: 90%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/thermo5.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  <div class="caption">An intermediate β phase splits the voltage curve into two plateaus separated by a step.</div>
</div>

To see where these shapes come from, we need to connect voltage to energy. A cell's voltage reflects the difference in Li chemical potential between the two electrodes. Measured against Li metal, the anode side is constant, so the voltage tracks the chemical potential in the electrode alone, and that chemical potential is simply the slope of the Gibbs free energy, g(x).

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/thermo6.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  <div class="caption">Voltage is set by the Li chemical potential, which is the slope of the free energy curve g(x).</div>
</div>

The simplest case is a solid solution, where Li mixes freely into the host across the full composition range. The free energy is a single smooth, convex curve, its slope changes gradually, and the voltage slopes smoothly as a result.

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/thermo7.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  <div class="caption">Solid solution (e.g. Li<sub>x</sub>TiS<sub>2</sub>): a single convex g(x) gives a smoothly sloping voltage.</div>
</div>

When g(x) has two wells, the system lowers its energy by separating into a Li-poor and a Li-rich phase rather than forming a uniform mixture. The two wells are joined by a common tangent, and because that line has a constant slope, the chemical potential, and therefore the voltage, stays fixed as the reaction proceeds.

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/thermo8.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  <div class="caption">Two-phase reaction (e.g. Li<sub>x</sub>FePO<sub>4</sub>): a common tangent between two wells produces a flat voltage plateau.</div>
</div>

Some materials go further. When Li and vacancies arrange into a particularly favourable ordered pattern at a specific composition, a new, stable intermediate phase appears as an extra well in g(x). This adds another common tangent and gives rise to multiple plateaus separated by distinct voltage steps.

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/thermo9.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  <div class="caption">Ordered intermediate phases (e.g. LiMn<sub>2</sub>O<sub>4</sub>): an extra well in g(x) creates a step between plateaus.</div>
</div>

Side by side, the connection is clear. The shape of the free energy curve fixes the shape of the voltage profile, which means a simple charge–discharge measurement is a window into the underlying thermodynamics of the electrode.

<div class="l-body" style="max-width: 100%; margin: auto;">
  {% include figure.liquid loading="eager" path="assets/img/projects/thermo10.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  <div class="caption">Summary: solid solution, two-phase, and multi-phase free energy curves and their corresponding voltage profiles.</div>
</div>

For a deeper look, see *Understanding Li Diffusion in Li-Intercalation Compounds* by Van der Ven, Bhattacharya and Belak, [Acc. Chem. Res. 46, 1216–1225 (2013)](https://doi.org/10.1021/ar200329r).
