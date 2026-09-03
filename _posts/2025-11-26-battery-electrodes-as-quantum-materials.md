---
layout: distill
title: Linking battery electrode science with correlated and quantum materials
description: Electrochemical alkali-ion (de)insertion provides dynamic, room-temperature control over spin state, charge ordering, and electron localization in transition metal oxides.
tags: batteries quantum
categories: research
giscus_comments: false
date: 2025-11-26
featured: true

authors:
  - name: Matthew A. Wright
    url: "mailto:matthew-wright@ucsb.edu"
    affiliations:
      name: Materials Department and MRL, UC Santa Barbara
  - name: Ram Seshadri
    url: "mailto:seshadri@mrl.ucsb.edu"
    affiliations:
      name: Materials Department and MRL, UC Santa Barbara

bibliography: 2025-11-26-battery-quantum.bib

# Post-specific CSS. Constrains figure widths so that tall, near-square
# plots do not fill the whole text column. Adjust the max-width values
# to taste; they cap the figure and its caption together.
_styles: >
  .fig-sm,
  .fig-md {
    margin-left: auto;
    margin-right: auto;
  }
  .fig-sm {
    max-width: 340px;
  }
  .fig-md {
    max-width: 560px;
  }
  .fig-sm .caption,
  .fig-md .caption {
    margin-top: 0.6rem;
    font-size: 0.8rem;
    line-height: 1.4;
  }

# Section names must match the headings in the body exactly.
# Headings are deliberately plain ASCII so that the slugified anchors resolve.
toc:
  - name: Introduction
  - name: Crystal field theory and Jahn-Teller distortions
  - name: Layered oxides - LixCoO2
  - name: LixCoO2 versus NaxCoO2
  - name: LixNiO2 and the role of antisite disorder
  - name: AMnO2 and mixed metal layered oxides
  - name: A-site control of properties in layered oxides
  - name: Olivine phosphates
  - name: Spinel oxides
  - name: Wadsley-Roth oxide anodes
  - name: Electrode materials with metal-metal bonds
  - name: Geometric frustration in breathing kagome networks
  - name: Challenges and outlook
---

## Introduction

Quantum materials, including superconductors and quantum spin liquids, as well as correlated oxides displaying coupled charge, spin, and magnetic order, possess properties that are exquisitely controlled by the electron count <d-cite key="dagotto2005"></d-cite>. The ability to control the properties of such a material is therefore directly related to the ability to control its electronic structure. Conventionally this is dictated at the point of synthesis, through elemental composition, synthetic conditions, and stoichiometry. A number of options are nevertheless available to researchers who wish to modify the properties of quantum materials postsynthesis <d-cite key="basov2017"></d-cite>, including the application of high pressures, high magnetic fields, high electric fields, or electrostatic gating.

One method that remains underutilized, despite being well understood, is electrochemistry. In a transition metal oxide the position and quantity of metal and oxide ions is determined by high-temperature thermodynamics and is almost impossible to change at room temperature. In contrast, the relative amounts of electrochemically transportable ions such as lithium or sodium are readily controllable, provided the structure supplies diffusion paths for ion transport and the chemistry supplies transition metals capable of serving as electron reservoirs. Under these conditions the electron count of the bulk material may be varied continuously, reversibly, and at ambient temperature.

This post summarizes a recent perspective titled [Linking battery electrode science with correlated and quantum materials](https://doi.org/10.1103/zwkw-zc5n) in *Physical Review Materials* <d-cite key="wright2025"></d-cite> in which we review how alkali-ion (de)insertion has been used to alter spin states, induce charge ordering, and drive transitions between insulating, metallic, and magnetically frustrated phases across a range of battery electrode materials.

The connection is not merely conceptual. First-principles calculations have shown that electronic correlations significantly impact the redox behavior of electrode materials, owing to the localized nature of the relevant states and to strong on-site Coulomb interactions <d-cite key="zhou2004"></d-cite>. In the absence of such correlations, the calculated voltage of an LiFePO<sub>4</sub> cathode is diminished by at least 0.5 V. Battery electrodes may therefore reasonably be described as one of the most useful real-world manifestations of electronic correlations of the Hubbard-*U* variety <d-cite key="hubbard1963"></d-cite>.

<div class="l-body fig-sm">
  {% include figure.liquid
     loading="eager"
     path="assets/img/2025-11-26-battery-quantum/fig1-hubbard-u-voltage.png"
     class="img-fluid rounded z-depth-1"
     zoomable=true %}
  <div class="caption">
    Electrochemical potential as a function of the on-site Coulomb interaction, modeled by
    the Hubbard <em>U</em>, in olivine-structured LiMPO<sub>4</sub> (M = Fe, Mn, Co, Ni). The
    experimental potential is given by the short black dashes. The average potential (star)
    is derived from the calculated potential for the material in an oxidized and reduced
    state (triangles). Adapted with permission from F. Zhou, M. Cococcioni, C. A. Marianetti,
    D. Morgan and G. Ceder, <em>Phys. Rev. B</em> <b>70</b>, 235121 (2004). Copyright 2004
    American Physical Society.
  </div>
</div>

## Crystal field theory and Jahn-Teller distortions

The majority of the *d* electrons residing on a transition metal do not partake in bond formation, but do influence the coordination environment of the metal atom and are responsible for properties such as electronic structure and magnetism. In an octahedral environment the *d* orbitals split into the lower-lying $t_{2g}$ set, which lies between the ligands, and the higher-lying $e_g$ set, which points directly towards them. The energy difference between the two is the crystal field splitting energy, $\Delta_\mathrm{oct}$. Since O<sup>2−</sup> is a weak field ligand, high-spin configurations are common for 3*d* metal oxides.

Significant Jahn-Teller distortions occur when electrons are unevenly distributed within the $e_g$ set, as is the case for high-spin $d^4$, low-spin $d^7$, and $d^9$ configurations, which results in an unstable electronic configuration. The instability is relieved by altering the energies of the orbitals so as to remove the orbital degeneracy, typically by lengthening the metal-oxygen bonds along one axis and compressing those perpendicular to it. Such distortions can have a profound effect on physical properties, and can give rise to cooperative distortion, orbital ordering, and modification of magnetic superexchange pathways.

Electrochemical (de)insertion therefore does not simply modulate the formal charge state of the transition metal. It also alters spin configuration and orbital occupancy, influencing electron localization and spin-state energetics. Readers seeking a more comprehensive treatment of magnetism in solids are directed to articles discussing the measurement <d-cite key="mozur2023"></d-cite> and interpretation <d-cite key="mugiraneza2022"></d-cite> of magnetic data.

## Layered oxides - LixCoO2

<div class="l-body fig-md">
  {% include figure.liquid
     loading="eager"
     path="assets/img/2025-11-26-battery-quantum/licoo2-electrochemical-states.png"
     class="img-fluid rounded z-depth-1"
     zoomable=true %}
  <div class="caption">
    Crystal structures of O3-LiCoO<sub>2</sub>, vacancy-ordered O3-Li<sub>0.55</sub>CoO<sub>2</sub>
    (shown schematically), and O1-CoO<sub>2</sub>, viewed along the [100] direction. Charging and
    discharging carry the material between a diamagnetic insulator, a charge-ordered
    antiferromagnet, and a paramagnetic metal. Reproduced from M. A. Wright and R. Seshadri,
    <em>Phys. Rev. Materials</em> <b>9</b>, 110302 (2025).
  </div>
</div>

Given the commercial and technological relevance of Li<sub>x</sub>CoO<sub>2</sub> <d-cite key="mizushima1980"></d-cite>, the mechanism of Li<sup>+</sup> (de)insertion across the whole range of *x* has been thoroughly investigated by detailed structural and spectroscopic studies. Fully lithiated O3-LiCoO<sub>2</sub> is an insulator with a band gap of 2.7 eV, containing Co<sup>3+</sup> in a low-spin $d^6$ configuration with a filled $t_{2g}$ manifold and no unpaired spins. Despite this diamagnetic ground state, the material displays a small temperature-independent susceptibility attributed to Van Vleck paramagnetism.

A significant increase in magnetic susceptibility is observed immediately upon Li<sup>+</sup> deinsertion. The temperature-independent part of the susceptibility rises from $1.4 \times 10^{-4}$ emu mol<sup>−1</sup> Oe<sup>−1</sup> for LiCoO<sub>2</sub> to $2.5 \times 10^{-4}$ emu mol<sup>−1</sup> Oe<sup>−1</sup> for Li<sub>0.98</sub>CoO<sub>2</sub>, corresponding to the removal of only 0.02 Li<sup>+</sup> per formula unit, and continues to increase thereafter <d-cite key="hertz2008"></d-cite>.

Lithium and vacancy ordering phenomena emerge at the commensurate compositions $x = 0.67$ and $x = 0.5$ near 175 K, evidenced by latent heat in differential scanning calorimetry and by sharp anomalies in the magnetic susceptibility. These are first-order transitions and are believed to originate from partial charge ordering of Co<sup>3+</sup> and Co<sup>4+</sup>, since the observed transition entropies are smaller than the mixing entropy expected for full charge separation. At $x = 0.5$, 1:1 lithium and vacancy ordering causes a hexagonal to monoclinic distortion that lowers the symmetry to $P2/m$, although O3-type layering is maintained <d-cite key="motohashi2009"></d-cite>.

The end member CoO<sub>2</sub> can be synthesized by complete electrochemical Li<sup>+</sup> deinsertion, yielding a phase-pure, oxygen-stoichiometric compound with an O1-stacking sequence <d-cite key="devaulx2007"></d-cite>. Magnetic susceptibility measurements reveal a large temperature-independent susceptibility of $5.7 \times 10^{-4}$ emu mol<sup>−1</sup> Oe<sup>−1</sup> characteristic of Pauli paramagnetism. The effective moment of 0.18 $\mu_\mathrm{B}$ per Co is far lower than expected for localized low-spin Co<sup>4+</sup>, confirming that the system does not support localized spin moments and is best described as a Pauli paramagnetic metal <d-cite key="motohashi2007"></d-cite>. This contrasts sharply with the diamagnetic insulating behavior of LiCoO<sub>2</sub>, and demonstrates an evolution from an orbitally filled, insulating $S = 0$ configuration with localized electrons to a metallic quantum paramagnetic state with delocalized electrons.

<div class="l-body">
  {% include figure.liquid
     loading="lazy"
     path="assets/img/2025-11-26-battery-quantum/fig4d-lixcoo2-phase-diagram.png"
     class="img-fluid rounded z-depth-1"
     zoomable=true %}
</div>
<div class="caption">
  The electronic phase diagram of Li<sub>x</sub>CoO<sub>2</sub>, derived from dc magnetic
  susceptibility and <sup>59</sup>Co NMR data. Adapted with permission from T. Motohashi,
  T. Ono, Y. Sugimoto, Y. Masubuchi, S. Kikkawa, R. Kanno, M. Karppinen and H. Yamauchi,
  <em>Phys. Rev. B</em> <b>80</b>, 165114 (2009). Copyright 2009 American Physical Society.
</div>

Electron correlation in Li<sub>x</sub>CoO<sub>2</sub> also highlights the limitations of static DFT+*U* calculations, which artificially stabilize charge-ordered solutions, and instead require DMFT to correctly capture phase stability and suppress spurious charge order <d-cite key="isaacs2020"></d-cite>.

## LixCoO2 versus NaxCoO2

NaCoO<sub>2</sub> is isostructural with LiCoO<sub>2</sub>, and Na<sup>+</sup> can likewise be chemically and electrochemically (de)inserted. Changes in quantum properties as a function of alkali metal content nevertheless differ significantly between the two materials. The larger ionic radius of Na<sup>+</sup> compared with Li<sup>+</sup> (1.02 against 0.76 Å) results in more dynamic changes to the CoO<sub>2</sub> layers, with significant octahedral distortion and expanded interlayer spacing observed during (de)insertion <d-cite key="hertz2008"></d-cite>.

At $x = 0.5$ a well-defined Co<sup>3+</sup>/Co<sup>4+</sup> charge-ordering and Na<sup>+</sup>/vacancy site-ordering transition occurs. This phase displays insulating behavior and a sharp decrease in Pauli susceptibility <d-cite key="foo2004"></d-cite>. An increased Pauli susceptibility is observed for $x = 0.3$, consistent with a correlated paramagnetic metal.

This latter composition also forms the basis for the hydrated superconductor Na<sub>0.35</sub>CoO<sub>2</sub>·1.3H<sub>2</sub>O, with a critical temperature of approximately 4.5 K <d-cite key="schaak2003"></d-cite>. Partial deinsertion of Na<sup>+</sup> in aqueous environments is accompanied by insertion of guest H<sub>2</sub>O molecules, which occupy either side of the sodium and spatially separate it from the CoO<sub>2</sub> layer. The resulting *c*-axis expansion gives rise to a strong two-dimensional character similar to that observed between CuO<sub>2</sub> planes in layered cuprates, which is understood to be important for superconductivity <d-cite key="takada2003"></d-cite>. The critical temperature traces a domed profile against sodium content, mirroring the behavior of high-*T*<sub>C</sub> cuprates. The hydrated phase is chemically fragile and is not a practical electrode, but it serves as an instructive example of how ion and water content can be used to tune carrier concentration and emergent phases.

## LixNiO2 and the role of antisite disorder

Prior to his work on Li<sup>+</sup> (de)insertion in LiCoO<sub>2</sub>, Goodenough investigated the magnetic properties of disordered layered oxides for memory storage applications <d-cite key="goodenough1958"></d-cite>, a point that underscores how closely the two fields were once connected.

NiO is an antiferromagnetic charge-transfer insulator with a Néel temperature of 525 K and a room temperature resistivity of order $10^8$ Ω cm. Insertion of Li<sup>+</sup> leads to a rapid decrease in electrical resistivity to approximately 1 Ω cm by $x = 0.2$. As more lithium is introduced, nanoscale domains of layered Li and Ni ordering begin to form, leading to chemical inhomogeneity and the emergence of complex magnetic phenomena <d-cite key="barton2013"></d-cite>. In this regime, Ni<sup>2+</sup> defects residing in the lithium layer mediate interlayer magnetic coupling and give rise to uncompensated ferrimagnetism, magnetic exchange bias, and Griffiths-phase-like behavior. At the end-member composition, chemical disorder caused by mixing of Ni<sup>2+</sup> and Li<sup>+</sup> sites disrupts long-range ordering, and LiNiO<sub>2</sub> exhibits a low-temperature glassy antiferromagnetic state with no magnetic Bragg peaks observed in neutron diffraction down to 1.4 K <d-cite key="reimers1993"></d-cite>.

In contrast to the well-understood transitions of LiCoO<sub>2</sub>, there remains no consensus on the exact nature of the Ni<sup>3+</sup> electronic state in LiNiO<sub>2</sub>. Recent theoretical work employing advanced GW approximations as well as DMFT suggests the existence of Ni<sup>2+</sup> together with a negative charge-transfer ligand hole on oxygen, with theory matching experimental spectra <d-cite key="genreith2023,banerjee2024"></d-cite>. Much of the historical ambiguity appears attributable to defects. Highly ordered LiNiO<sub>2</sub> can be obtained by low-temperature ion exchange from defect-free NaNiO<sub>2</sub>, revealing a monoclinic, collinear Jahn-Teller ordered ground state that is otherwise hidden by defects in conventionally prepared samples <d-cite key="phillips2025"></d-cite>. Exchanging Li<sup>+</sup> for larger Na<sup>+</sup> reduces antisite inversion by expanding the interlayer distance beyond the size that Ni<sup>2+</sup> can readily occupy.

The sodium analog is instructive in its own right. NaNiO<sub>2</sub> adopts a defect-free O'3-layered structure, and neutron pair distribution function analysis, EXAFS, and variable temperature NMR point to a predominantly displacive Jahn-Teller transition with vanishing local static distortions above the transition temperature <d-cite key="naglecocco2024"></d-cite>. Electrochemical desodiation produces the commensurate vacancy-ordered phase Na<sub>0.67</sub>NiO<sub>2</sub>, which possesses in-plane honeycomb Ni charge ordering and zigzag Na/vacancy motifs <d-cite key="steele2025"></d-cite>.

## AMnO2 and mixed metal layered oxides

Manganese-based layered oxides are theoretically desirable owing to the low cost and low toxicity of Mn, but in practice LiMnO<sub>2</sub> and NaMnO<sub>2</sub> have not proved successful as electrode materials. This is because of the orbital degeneracy associated with the high-spin Mn<sup>3+</sup> $d^4$ configuration, which leads to significant Jahn-Teller distortions and drives an irreversible transition to the spinel structure during oxidation.

The magnetism is correspondingly rich. In O3-NaMnO<sub>2</sub>, magnetic order is quasi-one-dimensional at high temperatures; at low temperatures, short-range incommensurate correlations give way to collinear antiferromagnetic order below 22 K, driven by strong in-plane exchange, structural anisotropy, and orbital ordering <d-cite key="dally2018"></d-cite>. The introduction of Na<sup>+</sup> vacancies at $x = 0.8$ induces an antiferromagnetic to ferromagnetic transition, together with a metal-to-semiconductor transition, arising from double-exchange interactions between Mn<sup>3+</sup> and Mn<sup>4+</sup>.

For the mixed-metal materials that dominate commercial cells, the magnetic response of LiNi<sub>x</sub>Mn<sub>y</sub>Co<sub>z</sub>O<sub>2</sub> varies greatly with transition metal composition and lithium content. At high nickel content these materials exhibit complex ferrimagnetic-like behavior, since nickel ions in the lithium layer introduce strong antiferromagnetic coupling via 180° Ni-O-Ni bonds and weaker ferromagnetic coupling via 90° bonds, producing small ferromagnetic clusters embedded in a larger antiferromagnetic framework. The evolution of magnetic response across this compositional range is discussed in detail by Chernova and coworkers <d-cite key="chernova2007"></d-cite>.

## A-site control of properties in layered oxides

The alkali cation modulates the behavior of layered oxide electrodes through three linked effects: interlayer spacing and steric constraints, site-preference and defect energetics, and ionic mobility.

Larger A-site cations such as Na<sup>+</sup> and K<sup>+</sup> expand the interlayer gap and suppress antisite disorder, favoring long-range cooperative Jahn-Teller and vacancy-ordering motifs that are often frustrated or nanoscale in the lithium-rich analogs. Smaller Li<sup>+</sup> favors closer-packed stacking, resulting in increased metal-oxygen covalency that raises working potentials, but also lowering the energetic cost of antisite defects that fragment cooperative ordering. Consequently, sodium-rich phases tend to show pronounced, commensurate vacancy and charge ordering together with sharp voltage plateaus, while lithium-rich phases more commonly exhibit disorder-smeared transitions, higher voltages, frustrated or glassy magnetic states, and a stronger sensitivity to synthesis route and defect concentration.

## Olivine phosphates

LiFePO<sub>4</sub> <d-cite key="padhi1997"></d-cite> is a Curie-Weiss paramagnet at room temperature but undergoes a transition below a Néel temperature of 50 K, becoming an antiferromagnetic Mott insulator in which the moments of high-spin Fe<sup>2+</sup> order collinearly along the *b* axis <d-cite key="santoro1967"></d-cite>. Upon Li<sup>+</sup> deinsertion the system exhibits a first-order phase separation between LiFePO<sub>4</sub> and FePO<sub>4</sub> rather than forming mixed-valence intermediate compositions. This arises from strong electron correlation effects which stabilize the two end members and inhibit the coexistence of Fe<sup>2+</sup> and Fe<sup>3+</sup>. The transition to high-spin Fe<sup>3+</sup> modifies the superexchange and crystal field environments, resulting in an increased Néel temperature of 125 K and a realignment of spins at a slight angle to the *a* axis <d-cite key="rousse2003"></d-cite>.

While first-principles calculations confirm that intermediate compositions are energetically unstable as homogeneous phases, nanoscale particles below 100 nm or elevated temperatures can suppress this behavior, stabilizing a metastable single-phase state through surface energy and elastic strain effects. Operando studies have captured such metastable structures during high-rate cycling and mapped the compositional spatiodynamics within individual primary particles <d-cite key="liu2014,lim2016"></d-cite>.

Recent theoretical work has shown that extended Hubbard treatments including both onsite *U* and intersite *V* parameters provide the most accurate description of the electronic structure of LiFePO<sub>4</sub>, correcting for the nonlocal charge screening and ligand-metal hybridization that static DFT+*U* can miss <d-cite key="timrov2022"></d-cite>.

## Spinel oxides

At high temperatures, stoichiometric LiMn<sub>2</sub>O<sub>4</sub> <d-cite key="thackeray1983"></d-cite> adopts cubic symmetry and behaves as a Curie-Weiss paramagnet, with Mn fluctuating between 3+ and 4+ valence. Upon cooling, a first-order structural transition is observed near 290 K in which the material undergoes symmetry lowering to an orthorhombic $Fddd$ phase due to partial charge ordering of Jahn-Teller active Mn<sup>3+</sup> and Mn<sup>4+</sup> cations <d-cite key="rodriguez1998"></d-cite>. This electronic crystallization localizes electrons at the ordered sites, disrupting carrier mobility and producing a metal-to-insulator-like transition, in direct analogy with charge-ordering manganites such as La<sub>0.5</sub>Ca<sub>0.5</sub>MnO<sub>3</sub>. Despite strong antiferromagnetic exchange, the geometrically frustrated pyrochlore-like Mn sublattice suppresses long-range magnetic ordering down to 5 K <d-cite key="wills1999"></d-cite>.

A particularly direct demonstration of electrochemical control over magnetism is provided by the spinel ferrites. Dasgupta and coworkers demonstrated control over the bulk magnetic properties of CuFe<sub>2</sub>O<sub>4</sub> and ZnFe<sub>2</sub>O<sub>4</sub> via reversible electrochemical (de)insertion of Li<sup>+</sup> <d-cite key="dasgupta2016"></d-cite>. In inverse-spinel CuFe<sub>2</sub>O<sub>4</sub>, lithium insertion partially reduces octahedral Cu<sup>2+</sup> to nonmagnetic Cu<sup>+</sup>, disrupting the Cu-O-Fe superexchange interactions and decreasing the room temperature magnetization by approximately 50%, with the Néel temperature falling from 610 to 530 K. In ZnFe<sub>2</sub>O<sub>4</sub>, insertion produces a significant broadening in the onset of magnetic ordering and an even larger decrease in room temperature magnetization of approximately 70%.

In both cases the modulation of magnetization is fully reversible. Conventional magnetoelectric approaches rely primarily on voltage-induced polarization at interfaces, limiting effective control to surface atoms or thin films. The magnetic states achieved through Li<sup>+</sup> insertion are representative of the bulk material and are nonvolatile, removing the necessity for continuous application of an electric field.

## Wadsley-Roth oxide anodes

Wadsley-Roth structures, derived from the crystallographic shear phases of ReO<sub>3</sub>, have garnered interest for their record-breaking rate capabilities <d-cite key="griffith2018"></d-cite>. PNb<sub>9</sub>O<sub>25</sub> achieves 85% of its theoretical charge capacity in 30 minutes, enabled by a multielectron redox mechanism involving stepwise reduction of niobium from Nb<sup>5+</sup> to Nb<sup>4+</sup> and finally to Nb<sup>3+</sup> <d-cite key="preefer2020"></d-cite>.

One of the most striking observations is an insulator-to-metal transition upon lithium insertion. At low lithium content, magnetic susceptibility measurements show behavior consistent with localized, paramagnetic Nb *d* electrons. As more lithium is inserted the system undergoes a delocalization of *d* electrons, and beyond $x = 5$ it transitions to a band-like metallic regime, evidenced by a suppression of Curie-Weiss behavior and the onset of Pauli paramagnetism. This is observed experimentally as a large Knight shift in the <sup>31</sup>P solid-state NMR spectra, as conduction electrons induce a strong hyperfine field at the phosphorus nuclei. The emergence of a large Knight shift is direct evidence of finite spin density at the Fermi level.

Not all members of the family behave in this way. Although the electronic conductivity of TiNb<sub>2</sub>O<sub>7</sub> increases by over four orders of magnitude on lithiation, it remains semiconducting even at full Li<sup>+</sup> insertion <d-cite key="griffith2019"></d-cite>.

## Electrode materials with metal-metal bonds

Electrode materials featuring direct metal-metal bonding offer a platform for emergent magnetic phenomena arising from the interplay between charge ordering, orbital overlap, and structural distortion.

Electrochemical (de)insertion of Na<sup>+</sup> in P2-Na<sub>x</sub>VO<sub>2</sub> results in metal-metal bond formation <d-cite key="guignard2013"></d-cite>. Deinsertion raises the average valence on the vanadium site and leads to displacement of the metal atoms, forming distorted octahedra and allowing $t_{2g}$ overlap through the edge-sharing framework. This gives rise to pseudo-trimers with short V-V distances of 2.58 to 2.69 Å, which couple to the Na<sup>+</sup>/vacancy ordering such that at $x = 0.5$ full sodium order and vanadium displacement jointly minimize the total energy.

The metal-metal clusters change how electrons are shared among the vanadium sites, producing drastic changes in electronic structure and transport. P2-Na<sub>0.5</sub>VO<sub>2</sub> possesses an anomalously small Curie constant compared with a naive mixture of V<sup>3+</sup> and V<sup>4+</sup> spins, consistent with most *d* electrons being sequestered into nonmagnetic or weakly magnetic cluster bonding states rather than acting as independent local moments. A first-order structural and electronic transition near 322 K is accompanied by an increase in electrical conductivity of roughly two orders of magnitude, as the vanadium atoms move back towards their ideal positions in the triangular lattice and the trimer motif is lost.

## Geometric frustration in breathing kagome networks

Kagome networks represent the maximally frustrated structure possible in two dimensions and have yielded exotic properties including frustrated magnetism, quantum spin liquids, and superconductivity <d-cite key="balents2010"></d-cite>.

Both O1-LiScMo<sub>3</sub>O<sub>8</sub> and O2-Li<sub>2</sub>ScMo<sub>3</sub>O<sub>8</sub> contain two-dimensional kagome networks formed from layers of Mo-Mo bonded triangles. Spin-polarized density of states calculations show that the two *d* electrons per Mo are completely localized within the Mo-Mo bonds in LiScMo<sub>3</sub>O<sub>8</sub>, making the material a diamagnetic insulator <d-cite key="wyckoff2022"></d-cite>. The addition of one extra *d* electron per cluster results in the spins becoming polarized, giving magnetic frustration and spin-liquid behavior with no sign of magnetic ordering down to 0.5 K <d-cite key="haraguchi2015"></d-cite>.

Reversible electrochemical insertion of Li<sup>+</sup> has been demonstrated across the range $1 \leq x \leq 3$, providing a new means of soft-chemical synthesis <d-cite key="wyckoff2023"></d-cite>. Notably, low-temperature susceptibility measurements show a magnetic ordering peak at 12 K, reaching a maximum at $x = 2$, for samples prepared electrochemically, which is absent in Li<sub>2</sub>ScMo<sub>3</sub>O<sub>8</sub> synthesized directly at high temperature. This ordering is attributed to Li<sup>+</sup> site ordering that is only possible within the structures of electrochemically prepared samples, which retain the O1-type layering and symmetry of the parent phase rather than adopting the offset cluster stacking of the directly synthesized product.

The magnetic behavior correlates not only with electron count but also with subtle changes in Mo-Mo bond distances across the breathing kagome network. Electrochemical insertion leads to a systematic decrease in the breathing ratio, defined as the ratio of the longest to the shortest Mo-Mo bonding distance, from 1.27 in LiScMo<sub>3</sub>O<sub>8</sub> to 1.24 in Li<sub>3</sub>ScMo<sub>3</sub>O<sub>8</sub>, indicating that the Mo<sub>3</sub> clusters become more geometrically uniform with increasing lithium content.

## Challenges and outlook

Several fundamental challenges remain, and these may be broadly separated into experimental challenges and measurement limitations.

Only a small subset of materials can simultaneously accommodate mobile guest ions and support redox-active transition metals. While Li<sup>+</sup> and Na<sup>+</sup> (de)insertion has proven effective in materials with open frameworks, extending this to larger or multivalent ions such as Mg<sup>2+</sup> and Ca<sup>2+</sup> presents difficulties relating to sluggish kinetics. Furthermore, the emergence of phase coexistence during cycling, together with the frequently inhomogeneous nature of ion (de)insertion, can result in spatial variance, defect concentrations, and interfacial gradients that mask intrinsic electronic or magnetic transitions. Many of the most interesting quantum phenomena are sensitive to symmetry, topology, and precise stoichiometry, yet these are precisely the properties most susceptible to disorder. It is uncommon, for instance, for LiCoO<sub>2</sub> to exhibit ideal diamagnetism despite the $S = 0$ configuration of $d^6$ Co<sup>3+</sup>, owing to trace cation disorder and oxidation-state heterogeneity. This highlights a mismatch in scale between the physical phenomena, which emerge from spatially local effects, and the macroscopic mechanism of electrochemical control.

Equally pressing practical challenges limit the measurement of physical properties. The four-point-probe method remains conventional for transport measurements but requires single-crystal samples, and advances in contactless techniques offer a promising route for polycrystalline electrode materials. Spectroscopic probes such as SQUID magnetometry and solid-state NMR remain essential, but are highly sensitive to contamination from the conductive additives, binders, and metallic components frequently employed in electrochemical cells. Development of quantum-compatible cell architectures permitting operando magnetometry <d-cite key="topolovec2016"></d-cite> and operando NMR <d-cite key="marker2020"></d-cite> will be a key innovation.

It should also be noted that electrochemically driven quantum phenomena carry direct performance consequences. Electron localization and charge ordering reduce intrinsic conductivity, increase voltage hysteresis, and limit rate performance; Jahn-Teller and orbital ordering drive cooperative lattice distortions that raise mechanical strain and result in irreversible capacity loss. By contrast, reversible band-filling transitions or deliberate metal-metal bonding may enhance conduction.

Perhaps the most interesting challenge is to develop predictive control. Static Kohn-Sham DFT and DFT+*U* are useful starting points but can misrepresent dynamic screening, spectral weight, and phase stability in strongly correlated electrode oxides. Many-body techniques such as DMFT capture time-dependent correlations and Mott or charge-transfer physics <d-cite key="paul2019"></d-cite>, while GW and related self-energy methods improve quasiparticle energies and nonlocal screening. We conclude that electrochemistry can provide a powerful platform for exploring and manipulating physical phenomena in correlated and quantum materials, and that continued electrochemical modulation of quantum ground states can serve as a proving ground not only for new materials, but for the fundamental models that seek to describe them.

The full perspective, with complete treatment of each material system, is published in *Physical Review Materials* <d-cite key="wright2025"></d-cite>.
