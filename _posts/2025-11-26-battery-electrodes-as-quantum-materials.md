---
layout: distill
title: Batteries as a knob for quantum matter
description: Ion (de)insertion is a room-temperature, reversible, bulk way to change electron count. That makes battery electrodes an unusually good platform for controlling spin, charge, and orbital order.
tags: batteries magnetism correlated-electrons
categories: research
giscus_comments: true
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

# Section names below must match the headings in the body exactly,
# or the TOC links will not resolve.
toc:
  - name: Electron count is the knob
  - name: Why electrodes are correlated-electron problems
  - name: LiCoO2, from band insulator to Pauli metal
  - name: Sodium tells a different story
  - name: LiNiO2, disorder, and the ligand hole
  - name: Olivines, a Mott insulator that refuses to mix
  - name: Spinels, charge order and switchable magnetization
  - name: Less conventional hosts
  - name: The A-site is a design variable
  - name: What makes this hard
  - name: Read more
---

## Electron count is the knob

Almost everything interesting about a correlated or quantum material — whether it is a metal or an insulator, whether the spins order or stay frustrated, whether it superconducts — depends on how many electrons sit on the transition metal site <d-cite key="dagotto2005"></d-cite>. Conventionally that number is fixed at the moment of synthesis, by composition and by whatever the high-temperature thermodynamics allows. Afterwards you are stuck with it.

There are ways around this. Pressure, high magnetic fields, strong electric fields, and electrostatic gating all shift the electronic structure of an existing sample <d-cite key="basov2017"></d-cite>. Each has limits: gating reaches only a few unit cells from an interface, pressure cells are cramped, and none of them leave you with a material you can take out and measure at leisure.

Electrochemistry does something the others cannot. Pulling lithium or sodium out of a host oxide changes the electron count of the entire bulk, by up to a full electron per formula unit, at room temperature, reversibly, and with a precision set by how much charge you passed. The framework of transition metal and oxide ions stays put; only the mobile guest ions and the electrons move. That is a remarkably clean handle, and it has been sitting in plain sight inside every lithium-ion battery for forty years.

Our perspective in *Physical Review Materials* <d-cite key="wright2025"></d-cite> makes the case that the battery community and the quantum materials community are studying the same compounds with different vocabularies, and that both would gain from noticing.

## Why electrodes are correlated-electron problems

This is not an analogy. Electrode voltages are quantitatively wrong unless you put correlation in by hand. Zhou and coworkers showed that the calculated potential of olivine LiMPO<sub>4</sub> cathodes depends strongly on the Hubbard $$U$$, and that without on-site Coulomb repulsion the voltage of an LiFePO<sub>4</sub> cathode would be at least 0.5 V lower than what is measured <d-cite key="zhou2004,hubbard1963"></d-cite>. Battery electrodes are arguably the most commercially consequential manifestation of Hubbard physics anywhere.

<!-- FIGURE 1 SLOT: Fig. 1 from the paper (voltage vs Hubbard U for LiMPO4). See notes at the bottom of this file for the include syntax. -->

The rest follows from standard ligand field arguments. In an octahedral oxide environment the $$d$$ orbitals split into a lower $$t_{2g}$$ set and a higher $$e_g$$ set, separated by $$\Delta_\mathrm{oct}$$. Because O<sup>2−</sup> is a weak-field ligand, 3$$d$$ oxides usually end up high spin. When the $$e_g$$ set is unevenly occupied — high-spin $$d^4$$, low-spin $$d^7$$, or $$d^9$$ — the configuration is unstable and the octahedron distorts to break the degeneracy. That Jahn–Teller distortion is simultaneously the origin of orbital ordering in a correlated oxide and the reason Mn<sup>3+</sup>-containing cathodes crack.

So when you deinsert lithium, you are not only changing an oxidation state. You are changing spin state, orbital occupancy, superexchange pathways, and the degree of electron localization, all at once. Readers who want the magnetism background in more depth are well served by tutorials on measuring <d-cite key="mozur2023"></d-cite> and interpreting <d-cite key="mugiraneza2022"></d-cite> susceptibility data.

## LiCoO2, from band insulator to Pauli metal

The canonical cathode is also the cleanest demonstration. Fully lithiated O3-LiCoO<sub>2</sub> <d-cite key="mizushima1980"></d-cite> contains low-spin $$d^6$$ Co<sup>3+</sup>, a filled $$t_{2g}$$ shell, $$S = 0$$, and a 2.7 eV gap. It is a diamagnetic insulator, with only a small temperature-independent Van Vleck susceptibility.

Start removing lithium and the susceptibility responds immediately. Taking out just 0.02 Li per formula unit nearly doubles $$\chi_0$$. At the commensurate compositions $$x = 0.67$$ and $$x = 0.5$$, Li/vacancy ordering sets in near 175 K, visible as latent heat in calorimetry and as sharp anomalies in the susceptibility. These transitions are believed to reflect partial Co<sup>3+</sup>/Co<sup>4+</sup> charge ordering rather than full charge separation, since the measured entropies fall short of what complete disproportionation would require. At $$x = 0.5$$ the 1:1 vacancy order drives a hexagonal-to-monoclinic distortion to $$P2/m$$ <d-cite key="hertz2008,motohashi2009"></d-cite>.

Push all the way to the $$x = 0$$ end member and you get CoO<sub>2</sub>, a phase-pure, oxygen-stoichiometric compound made by electrochemistry alone <d-cite key="devaulx2007"></d-cite>. Its susceptibility is large, temperature independent, and Pauli-like; the effective moment of 0.18 $$\mu_\mathrm{B}$$ per Co is far below the $$S = 1/2$$ expected for localized low-spin Co<sup>4+</sup> <d-cite key="motohashi2007"></d-cite>. The system does not support local moments at all. One electrochemical sweep therefore walks the material from an orbitally filled, localized, $$S = 0$$ insulator to a delocalized paramagnetic metal.

<!-- FIGURE 2 SLOT: Fig. 4(d) from the paper, the electronic phase diagram of LixCoO2. -->

Worth flagging for the theory-minded: static DFT+$$U$$ artificially stabilizes charge-ordered solutions here, and DMFT is needed to get the phase stability right and to suppress the spurious order <d-cite key="isaacs2020"></d-cite>.

## Sodium tells a different story

Na<sub>x</sub>CoO<sub>2</sub> is isostructural, but the larger Na<sup>+</sup> radius (1.02 Å against 0.76 Å) makes the layers far more responsive, with substantial octahedral distortion and interlayer expansion on cycling <d-cite key="hertz2008"></d-cite>. Rather than the smooth evolution seen in the lithium system, the sodium phase diagram is a sequence of commensurate ordered states: a charge-ordered insulator at $$x = 0.5$$ <d-cite key="foo2004"></d-cite>, a correlated paramagnetic metal near $$x = 0.3$$, and NMR evidence that the charge and spin disproportionation is intrinsic to the CoO<sub>2</sub> plane rather than merely imposed by the sodium order.

And at that same doping, hydrate it and it superconducts. Na<sub>0.35</sub>CoO<sub>2</sub>·1.3H<sub>2</sub>O has $$T_\mathrm{c} \approx 4.5$$ K <d-cite key="schaak2003,takada2003"></d-cite>, with water molecules sandwiching the sodium and pushing the CoO<sub>2</sub> layers apart. The resulting two-dimensionality mirrors the CuO<sub>2</sub> planes of the cuprates, and the $$T_\mathrm{c}$$ traces a dome against sodium content. The hydrate is chemically fragile and useless as an electrode, but as a demonstration that guest-ion content tunes carrier concentration into a superconducting regime, it is hard to beat.

## LiNiO2, disorder, and the ligand hole

Goodenough was studying magnetism in Li<sub>x</sub>NiO<sub>2</sub> long before he proposed LiCoO<sub>2</sub> as a cathode <d-cite key="goodenough1958"></d-cite>, which is a nice reminder of how tangled these two fields already are.

The full composition range from NiO to LiNiO<sub>2</sub> is a study in how chemical order controls magnetism. NiO is a charge-transfer insulator and antiferromagnet with $$T_\mathrm{N} = 525$$ K. Lithium insertion collapses the resistivity by eight orders of magnitude by $$x = 0.2$$. In the intermediate regime nanoscale ordered domains appear, Ni<sup>2+</sup> defects in the lithium layer bridge adjacent NiO<sub>2</sub> sheets and produce uncompensated ferrimagnetism, exchange bias, and Griffiths-like behavior <d-cite key="barton2013"></d-cite>. At the LiNiO<sub>2</sub> end member you get a glassy antiferromagnet with no magnetic Bragg peaks down to 1.4 K <d-cite key="reimers1993"></d-cite>.

What Ni<sup>3+</sup> actually *is* in this compound remains contested. Recent DMFT and GW work argues for Ni<sup>2+</sup> plus a negative charge-transfer ligand hole on oxygen rather than a clean Ni<sup>3+</sup> <d-cite key="genreith2023,banerjee2024"></d-cite>. Much of the historical confusion appears to come from defects: preparing genuinely defect-free LiNiO<sub>2</sub> by low-temperature ion exchange from NaNiO<sub>2</sub> reveals a monoclinic, collinear Jahn–Teller ordered ground state that is simply hidden in conventionally synthesized powders <d-cite key="phillips2025"></d-cite>. The sodium analog, meanwhile, shows a predominantly displacive Jahn–Teller transition <d-cite key="naglecocco2024"></d-cite>, and desodiation produces a honeycomb charge-ordered, zigzag vacancy-ordered phase at Na<sub>0.67</sub>NiO<sub>2</sub> <d-cite key="steele2025"></d-cite>.

Manganese behaves differently again: in O3-NaMnO<sub>2</sub> the magnetic correlations are quasi-one-dimensional at high temperature and become collinear antiferromagnetic below 22 K <d-cite key="dally2018"></d-cite>, while sodium vacancies drive an antiferromagnetic-to-ferromagnetic and metal-to-semiconductor transition through Mn<sup>3+</sup>/Mn<sup>4+</sup> double exchange. For the commercial mixed-metal layered oxides, Chernova and coworkers laid out how the magnetic response tracks nickel content and antisite disorder <d-cite key="chernova2007"></d-cite>.

## Olivines, a Mott insulator that refuses to mix

LiFePO<sub>4</sub> <d-cite key="padhi1997"></d-cite> is a Curie–Weiss paramagnet at room temperature that becomes an antiferromagnetic Mott insulator below 50 K, with high-spin Fe<sup>2+</sup> moments collinear along $$b$$ <d-cite key="santoro1967"></d-cite>. Delithiation does not give you a mixed-valence solid solution. It gives you a first-order separation into LiFePO<sub>4</sub> and FePO<sub>4</sub>, precisely because correlation effects stabilize the two end members and penalize Fe<sup>2+</sup>/Fe<sup>3+</sup> coexistence. FePO<sub>4</sub> then orders at 125 K with the spins realigned near $$a$$ <d-cite key="rousse2003"></d-cite>.

The two-phase behavior is not absolute. Below about 100 nm, or above 350 °C, surface energy and elastic strain can stabilize a metastable single phase, and operando work has caught these transient states in the act <d-cite key="liu2014,lim2016"></d-cite>. On the theory side, extended Hubbard functionals with both onsite $$U$$ and intersite $$V$$ give the best account of the electronic structure, correcting for the nonlocal screening and ligand–metal hybridization that plain DFT+$$U$$ misses <d-cite key="timrov2022"></d-cite>.

## Spinels, charge order and switchable magnetization

LiMn<sub>2</sub>O<sub>4</sub> <d-cite key="thackeray1983"></d-cite> is cubic and Curie–Weiss-like at high temperature, with Mn valence fluctuating between 3+ and 4+. Cool it through about 290 K and it undergoes a first-order transition to orthorhombic $$Fddd$$, driven by partial charge ordering of Jahn–Teller active Mn<sup>3+</sup> against Mn<sup>4+</sup> — an electronic crystallization directly analogous to what happens in half-doped manganites <d-cite key="rodriguez1998"></d-cite>. Despite strong antiferromagnetic exchange, the pyrochlore-like Mn sublattice is geometrically frustrated and no long-range magnetic order appears down to 5 K <d-cite key="wills1999"></d-cite>.

The most striking spinel result is Dasgupta and coworkers' demonstration of reversible on/off magnetism in ferrites <d-cite key="dasgupta2016"></d-cite>. Inserting Li<sup>+</sup> into CuFe<sub>2</sub>O<sub>4</sub> reduces octahedral Cu<sup>2+</sup> ($$S = 1/2$$) to nonmagnetic Cu<sup>+</sup>, killing the Cu–O–Fe superexchange and cutting room-temperature magnetization roughly in half, with $$T_\mathrm{N}$$ falling from 610 to 530 K. In ZnFe<sub>2</sub>O<sub>4</sub> the effect is larger still, about a 70% reduction, as many particles are pushed from ordered to disordered at room temperature. Both are fully reversible over cycling.

This is worth dwelling on. Conventional magnetoelectric control is an interfacial, volatile effect confined to surface layers or thin films. Here the modified magnetic state is a bulk property and it persists with no applied field — which is exactly what a magnetic memory element needs.

## Less conventional hosts

Three systems in the paper go beyond the commercial cathodes and, to us, show where the idea has the most room to run.

**Wadsley–Roth shear phases.** PNb<sub>9</sub>O<sub>25</sub> charges to 85% of theoretical capacity in half an hour <d-cite key="preefer2020"></d-cite>, via stepwise reduction of Nb<sup>5+</sup> to Nb<sup>4+</sup> to Nb<sup>3+</sup>. At low lithium content the susceptibility indicates localized paramagnetic Nb $$d$$ electrons; beyond $$x = 5$$ Curie–Weiss behavior is suppressed and Pauli paramagnetism sets in. The smoking gun is a large Knight shift in the <sup>31</sup>P solid-state NMR of the fully inserted phase, direct evidence of finite spin density at the Fermi level. The material also changes color from white through gray and blue to black as it goes. Not every member behaves this way — TiNb<sub>2</sub>O<sub>7</sub> gains four orders of magnitude in conductivity but stays semiconducting <d-cite key="griffith2019,griffith2018"></d-cite>.

**Metal–metal bonded layers.** In P2-Na<sub>x</sub>VO<sub>2</sub>, desodiation displaces the vanadium atoms and opens up $$t_{2g}$$–$$t_{2g}$$ overlap, forming pseudo-trimers with V–V distances of 2.58–2.69 Å that lock in cooperatively with the Na/vacancy order at $$x = 0.5$$ <d-cite key="guignard2013"></d-cite>. Most of the $$d$$ electrons get sequestered into cluster bonding states rather than acting as local moments, which is why the Curie constant is anomalously small. Warm through 322 K, the trimers dissolve, and the conductivity jumps by two orders of magnitude.

**Breathing kagome networks.** LiScMo<sub>3</sub>O<sub>8</sub> is built from Mo–Mo bonded triangles forming a 2D kagome net, and is a diamagnetic insulator with its $$d$$ electrons locked into the metal–metal bonds <d-cite key="wyckoff2022"></d-cite>. Add one electron per Mo<sub>3</sub>O<sub>8</sub> cluster and you get spin-liquid behavior with no ordering down to 0.5 K <d-cite key="haraguchi2015,balents2010"></d-cite>. The interesting result is that electrochemically inserting lithium to reach Li<sub>2</sub>ScMo<sub>3</sub>O<sub>8</sub> gives a *different material* than making it in a furnace <d-cite key="wyckoff2023"></d-cite>: the electrochemical route preserves the parent O1 stacking and $$P\bar{3}m1$$ symmetry, which allows a mixture of tetrahedral and octahedral Li sites, short-range charge order, and a 12 K magnetic ordering peak that is simply absent in the high-temperature product. Insertion also shrinks the kagome breathing ratio from 1.27 to 1.24. Electrochemistry here is not just a tuning knob, it is a synthesis route to phases the furnace cannot reach.

<!-- FIGURE 3 SLOT (optional): Fig. 12 from the paper, the LixScMo3O8 breathing kagome network. -->

## The A-site is a design variable

Pulling the layered oxide results together, the choice of alkali cation controls three linked things: interlayer spacing and steric constraint, the energetics of antisite defects, and ionic mobility.

Larger cations such as Na<sup>+</sup> and K<sup>+</sup> expand the interlayer gap enough to make antisite occupation unfavorable, which lets long-range cooperative Jahn–Teller and vacancy ordering survive. That is why sodium phases tend to show sharp voltage plateaus and commensurate, well-defined charge-ordered states. Smaller Li<sup>+</sup> packs the layers closer, raising M–O covalency and working potential, but also lowering the cost of M/Li antisites that fragment cooperative order. Lithium-rich phases consequently give higher voltages but disorder-smeared transitions, frustrated or glassy magnetism, and a strong sensitivity to synthesis route.

If you want conventional, well-ordered magnetic ground states, use the big cation. If you want frustration and glassiness, use the small one.

## What makes this hard

We would be overselling this if we did not say what stands in the way.

*Chemistry.* Only a modest set of materials both host mobile guest ions and have redox-active metals. Multivalent ions such as Mg<sup>2+</sup> and Ca<sup>2+</sup> would open up new chemistry but suffer badly from sluggish kinetics.

*Homogeneity.* Phase coexistence and inhomogeneous insertion mean your "sample" often is not one thing. Defect concentrations, interfacial gradients, and spatial variance smear out exactly the intrinsic transitions you were trying to see. It is uncommon even to observe ideal diamagnetism in LiCoO<sub>2</sub>, despite $$S = 0$$ Co<sup>3+</sup>, because of trace cation disorder. There is a real scale mismatch here between phenomena that are local and a control mechanism that is macroscopic.

*Measurement.* Four-point-probe transport wants single crystals, which electrode powders are not; contactless millimeter-wave reflection is a promising alternative. SQUID magnetometry and solid-state NMR are indispensable but are easily contaminated by the conductive additives, binders, and metallic cell components that a working electrochemical cell is full of. Quantum-compatible cell architectures for operando magnetometry <d-cite key="topolovec2016"></d-cite> and operando NMR <d-cite key="marker2020"></d-cite> are, we think, a key enabling technology.

*Theory.* Predicting correlated, low-temperature, or topological states under nonequilibrium conditions in disordered materials is genuinely hard. Static DFT+$$U$$ is a starting point, not an answer; DMFT for dynamic correlations <d-cite key="paul2019"></d-cite>, GW for quasiparticle energies, and DFT+$$U$$+$$V$$ for strongly hybridized polyanionic systems all have roles to play.

There is also a two-way street worth noting: these quantum phenomena have direct performance consequences. Charge ordering and electron localization reduce conductivity and increase hysteresis; cooperative Jahn–Teller distortions raise mechanical strain and cost capacity. Understanding them is not a detour from making better batteries.

## Read more

The full perspective, with all 196 references and the complete treatment of each material system, is published in *Physical Review Materials* <d-cite key="wright2025"></d-cite>. Comments and disagreements are welcome.
