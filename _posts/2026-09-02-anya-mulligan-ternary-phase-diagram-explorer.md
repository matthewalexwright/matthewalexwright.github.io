---
layout: post
title: "MP-query-ternaries: A ternary phase diagram explorer by Anya S. Mulligan"
date: 2026-09-02 09:00:00-0700
description: A tool from our group that queries the Materials Project across whole families of ternary systems at once, and returns CSVs and phase diagrams
tags: software crystallography
categories: tools
giscus_comments: false
related_posts: true
thumbnail: assets/img/2026-09-02-mp-query-ternaries/icon.png
featured: true
---

<div style="max-width: 130px; margin: 0 auto 2rem;">
  {% include figure.liquid
     loading="eager"
     path="assets/img/2026-09-02-mp-query-ternaries/icon.png"
     class="img-fluid rounded"
     zoomable=false %}
</div>

Anyone who has gone looking for a compound in an unfamiliar corner of the periodic table knows the drill. Open the Materials Project, type in a ternary, scroll the results, note the space groups, check for an ICSD entry, repeat. With five rare earths, six transition metals and three anions, that is ninety systems and an afternoon you will not get back.

**[Anya S. Mulligan](https://github.com/seshadri-group/MP-query-ternaries), a graduate student in our group at UC Santa Barbara, has built a tool that does the entire sweep in one go** — complete with a GUI and a one-click installer. Get it here: [seshadri-group/MP-query-ternaries](https://github.com/seshadri-group/MP-query-ternaries).

## What it does

You define three element *groups*: for instance, a set of alkali metals, a set of transition metals, and a set of anions. Anya's workflow takes the full combinatorial product, queries the Materials Project for every resulting ternary, and pulls the bounding binaries along each edge.

Out come CSVs with one row per Materials Project entry, polymorphs included, carrying space group, ICSD IDs, stability, and formation and decomposition energies — plus a ternary composition diagram for each system, a summary grid of all of them, and a key figure. Crucially, experimentally known compounds are separated from predicted ones at the file level, which is the distinction between a literature search and a research project.

Taking the halide perovskite space as an example, with group 1 = Cs, group 2 = Sn, Pb, group 3 = Cl, Br, I:

```
output_Cs_Sn-Pb_Cl-Br-I/
├── compounds_ternary_exp.csv    # experimentally known ternaries
├── compounds_ternary_all.csv    # + predicted
├── compounds_binary_exp.csv     # bounding binaries
├── compounds_binary_all.csv
└── phase_diagrams/
    ├── <A>-<M>-<X>.png          # one diagram per ternary system
    ├── summary.png              # all diagrams in one grid
    ├── key.png                  # legend + group definitions
    └── blank.png                # empty template triangle
```

Here is one of the six diagrams that run produces, for the Cs–Pb–Cl system:

<div style="max-width: 580px; margin: 0 auto;">
  {% include figure.liquid
     loading="eager"
     path="assets/img/2026-09-02-mp-query-ternaries/Cs-Pb-Cl.png"
     class="img-fluid rounded z-depth-1"
     zoomable=true %}
  <div class="caption">
    A single ternary diagram, labelled and ready to use. Filled markers denote compounds with
    an ICSD entry, open markers denote Materials Project predictions; circles are ternaries,
    squares the bounding binaries. The perovskite CsPbCl<sub>3</sub> sits alongside
    Cs<sub>4</sub>PbCl<sub>6</sub>, Cs<sub>2</sub>PbCl<sub>6</sub> and
    CsPb<sub>2</sub>Cl<sub>5</sub>. Figure by A. S. Mulligan, reproduced with permission.
  </div>
</div>

And here is the summary grid, which puts all six systems side by side. Reading across, the picture is immediately legible: the tin chemistry is entirely experimentally known, while several of the lead bromides and iodides are predictions the Materials Project has not seen in the ICSD.

<div style="max-width: 480px; margin: 0 auto;">
  {% include figure.liquid
     loading="lazy"
     path="assets/img/2026-09-02-mp-query-ternaries/summary.png"
     class="img-fluid rounded z-depth-1"
     zoomable=true %}
  <div class="caption">
    The summary grid for the same run: rows by caesium halide, columns by Sn and Pb. One
    glance replaces what would otherwise be six separate database searches. Figure by
    A. S. Mulligan, reproduced with permission.
  </div>
</div>

## Getting it running

There is no environment to build by hand. Download the repository, unzip it somewhere local, install [conda](https://conda-forge.org/download/), and double-click `MP-query-ternaries_GUI.command` on macOS or `MP-query-ternaries_GUI.bat` on Windows. The first launch builds the environment for you. A command line route exists too. All you need is a Materials Project API key, which you can get for free from [materialsproject.org/api](https://materialsproject.org/api).

---

*Developed by Anya S. Mulligan, with assistance from Claude (Anthropic). Issues and pull requests welcome on [the repository](https://github.com/seshadri-group/MP-query-ternaries).*
