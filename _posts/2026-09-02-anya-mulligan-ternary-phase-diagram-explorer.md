---
layout: post
title: "Anya Mulligan's ternary phase diagram explorer"
date: 2026-09-02 09:00:00-0700
description: A tool from our group that queries the Materials Project across whole families of ternary systems at once, and returns CSVs and phase diagrams
tags: software materials-project phase-diagrams crystallography tools
categories: tools
giscus_comments: true
related_posts: true
---

Anyone who has gone looking for a compound in an unfamiliar corner of the periodic table knows the drill. Open the Materials Project, type in a ternary, scroll the results, note the space groups, check for an ICSD entry, repeat. With five rare earths, six transition metals and three anions, that is ninety systems and an afternoon you will not get back.

**[Anya S. Mulligan](https://github.com/seshadri-group/MP-query-ternaries), a graduate student in our group at UC Santa Barbara, has built a tool that does the entire sweep in one go** — and has done it properly, with a GUI, a one-click installer, and documentation that assumes nothing. It is genuinely excellent work, and the kind of thing that quietly saves everyone around her a great deal of time. Get it here: [seshadri-group/MP-query-ternaries](https://github.com/seshadri-group/MP-query-ternaries).

## What it does

You define three element *groups* rather than three elements: a set of alkali metals, say, a set of transition metals, and a set of anions. Anya's workflow takes the full combinatorial product, queries the Materials Project for every resulting ternary, and pulls the bounding binaries along each edge.

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

Six systems, so a good first run to confirm your setup works. The blank template triangle is a characteristically thoughtful touch for anyone annotating a diagram by hand for a talk.

<!--
FIGURE SLOT: ask Anya for a summary.png from a real run, or a GUI screenshot.
Save to assets/img/ and uncomment:

<div class="row mt-3">
  <div class="col-sm mt-3 mt-md-0">
    {% include figure.liquid loading="eager" path="assets/img/mp-query-ternaries-summary.png" class="img-fluid rounded z-depth-1" zoomable=true %}
  </div>
</div>
<div class="caption">
  Summary grid of ternary phase diagrams. Reproduced with permission from A. S. Mulligan.
</div>
-->

## Getting it running

This is where most academic code loses its users, and where Anya has put in the work. There is no environment to build by hand. Download the repository as a ZIP from the green Code button, unzip it somewhere local, install [conda](https://conda-forge.org/download/), and double-click `MP-query-ternaries_GUI.command` on macOS or `MP-query-ternaries_GUI.bat` on Windows. The first launch builds the environment for you.

macOS will show an "unidentified developer" warning the first time. Apple menu → System Settings → Privacy & Security, scroll down, Open Anyway, then double-click again. That is Gatekeeper doing its job on an unsigned script.

Then get a free API key from [materialsproject.org/api](https://materialsproject.org/api), paste it into the GUI and press Save. It stays on your machine in `~/.mp_api_key`. Fill in your element groups, press Run workflow.

A command line route exists too:

```bash
git clone https://github.com/seshadri-group/MP-query-ternaries.git
cd MP-query-ternaries
conda env create -f environment.yml
conda activate mp-ternaries
python gui.py
```

For headless runs, copy `f.args.example` to `f.args`, edit it, and run `python workflow.py`. The GUI and the config file read and write the same thing and preserve each other's keys, so you can mix the two freely — a small design decision that says a lot about the care that went into this.

## A few notes

The `[timing]` lines in the log show where a run is spending itself; normally the Materials Project query dominates. Avoid running large jobs inside Box or Dropbox folders, which will try to sync every PNG as it appears — point `out_dir` somewhere local instead.

On the data rather than the tool: Materials Project energies are DFT-derived, so hull distances are a good ranking metric and a poor absolute one, and a missing ICSD ID means the Materials Project has no link rather than that nobody has made the compound. Cite the Materials Project if the results reach a paper.

Take it for a run, and send Anya your bugs.

---

*Developed by Anya S. Mulligan, with assistance from Claude (Anthropic). Issues and pull requests welcome on [the repository](https://github.com/seshadri-group/MP-query-ternaries).*
