# BioNetGen Tutorial

The files presented here are meant to provide a moderately paced but comprehensive introduction to the syntax and features of the BioNetGen language (BNGL) and modeling software. These examples can be run either using `BNG2.pl` from the command line or using the RuleBender interface. We have made a [short video](https://www.youtube.com/watch?v=MWoY5iaC8W0&t=1s) showing how to get started using RuleBender. 

**Click on the link to see the BNGL code, which can be copy/pasted into a .bngl file in an editor or RuleBender.**

## Basic structure and syntax
[`ABC.bngl`](ABC/ABC.bngl)
: Simple binding model in BNGL using unstructured molecules to represent each species. Demonstrates basic syntax of `simulate` command.

[`ABC_scan.bngl`](ABC/ABC_scan.bngl)
: Simple binding model modified to use`parameters` block, which enables `parameter_scan`. Also demonstrates use of `#` for comments and `\` for line continuation.

[`ABC_ssa.bngl`](ABC/ABC_ssa.bngl)
: Simple binding model with modifed `method` option to `simulate` command to demonstrate `ssa` method for performing stochastic simulation.

[`LV.bngl`](ABC/LV.bngl)
: Lotke-Volterra model in BioNetGen syntax.

## Using structured molecules and rules: Binding
[`AB.bngl`](AB/AB.bngl)
: Simple binding model re-factored to used structured molecules with binding sites and a binding rule that adds or deletes a bond. Things to notice:
* Contact Map panel in RuleBender shows Molecule and Component interactions.
* Clicking tabs associated with Obervables shows Patterns and corresponding mathces. 

[`BAB.bngl`](BAB/BAB.bngl)
: Simple binding model with a bivalent A molecule that has two identical sites for binding of B. Binding at each site is not affected by the status of the other site (noncooperative binding). Things to notice:
* This is a good model to examine the output of network generation, which is found in the file `BAB.net` that is generated by BioNetGen. In this file the `seed species` block is converted to a `species` block, which lists all of the species that result from network generation. The `reaction rules` block is replaced by `reactions`, and the `observables` block is replaced by `groups`. In these blocks species strings are replaced by an index referring to entries in the `species` block. Both rate constants in reactions and entries in `groups` can be preceded by an integer that specifies a pre-factor arising from *symmetry* or *multiplicity*.

[`BAB_scan.bngl`](BAB/BAB_scan.bngl)
: Varying the amount of A reveals nonmonotonic behavior of complexation. This example demonstrates use of the `log_scale` option to `parameter_scan`. Things to notice:
* To observe the behavior of the BAB complex, you will have to turn off display of the other, more abundant observables.
* You will also need to change the X Axis scale from `linear` to `log`.
* You can replicate the behavior of the `parameter_scan` function by switching the `Run File` option to `Parameter Scan` in the Simulation tab in RuleBender and then completing the entries in the form that appears below the selection.

## Using structured molecules and rules: Component state change

[`ABp.bngl`](ABp/ABp.bngl)
: Simple enzyme binding and substrate modification scheme. A is a kinase and B contains a phosphorylable substrate site called `Y`, which has two states, `0` and `P`, which represent the unphosphorylated state and phosphorylated states respectively. This model also demonstrates the use of expressions in the `parameters` block to perform unit conversions and comments to define a consistent set of units. We recommend cubic microns (fL) as the standard volume unit, µM or molecule counts for concentration, µm for length, and µm<sup>2</sup> for area.

[`ABp_approx.bngl`](ABp/ABp_approx.bngl)
: A simplified version of the A-B phosphorylation model in which the explicit binding of A and B is eliminated and the phosphorylation reaction rate is given by the Michaelis-Menten rate law. 

**Exercise:** Try changing the initial amounts of A and B such that A is in ten-fold excess over B and plotting the resulting time courses. What do you observe? (*Hint: Be sure to change the duration of the simulation as well.*)

[More advanced models of substrate modification dynamics](ABp/AdvancedModels.md). Demonstrates additional use of functions in rate laws, how to define a simulation protocol using multiple `simulate` commands and the `setParameter` command, and use of the `bifurcate` command to examine a bistable system. 

## Modeling synthesis and degradation 

[`birth-death.bngl`](SynDeg/birth-death.bngl)
: Simple model illustrating synthesis and degradation of molecules. Also, demonstrates use of `saveConcentrations()` and `resetConcentrations()` to save and restore initial conditions and to compare model simulated with two different methods. Introduces `generate_network()` command.

[`toggle.bngl`](SynDeg/toggle.bngl)
: Simple model of a two-gene toggle switch describing the synthetic circuit of Gardner, Cantor, and Collins. Demonstrates use of the `bifurcate()` command to identify hysteresis loops in a potentially bistable system. Model also demonstrates stochastic transitions between metastable states that could represent cell phenotypes.

**Exercise:** Make a simple model of an auto-regulating gene in which the gene product P dimerizes and binds to the promoter to block transcription. 

[`ComplexDegradation.bngl`](SynDeg/ComplexDegradation.bngl)
: Demonstrates behavior of various rules specifying degradation of complexes and how this can be controlled by the `DeleteMolecules` keyword.

**Exercise:** Modify the model you made in the previous exercise to allow degradation of P even when it's bound to DNA without degrading the DNA.

[More advanced models of gene regulation](SynDeg/AdvancedModels.md)

## Ligand-receptor binding models

These models address issues of unit definition, how to construct models with distinct spatial compartments, and using network-free simulation for models that have a large or potentially infinite number of possible species and reactions.
See the [Quick Reference Guide](https://drive.google.com/file/d/0B2lPm2_GUE01X3ZaamZxUl80NTA/edit) for a brief introduction to the Compartment specification and syntax.

[`LR.bngl`](CBNGL/LR.bngl)
: Non-compartmental model of simple ligand-receptor binding.

[`LR_comp.bngl`](CBNGL/LR_comp.bngl)
: Compartmental model of simple ligand-receptor binding.

[`LRR.bngl`](CBNGL/LRR.bngl)
: Non-compartmental model of ligand-receptor binding and dimerization. Also demonstrates `visualize` command to make `.gml` files for visualization of the rule network using the external tool [yEd](https://www.yworks.com/yed).

[`LRR_comp.bngl`](CBNGL/LRR_comp.bngl)
: Compartmental model of ligand-receptor binding and dimerization.

[`BLBR.bngl`](CBNGL/BLBR.bngl)
: Bivalent ligand - bivalent receptor (BLBR) model, which is a simple model of polymer formation by receptors that can form a chain with infinite length (in the continuum limit). Simulating this model using a generate and simulate approach is problematic because for these parameters the required network of complexes is very large. Using network-free simulation addresses this problem.

## Models for CellBlender

*As of March 7, 2018 the SBML importer in CellBlender does not create the objects corresponding to the specified compartments. These have to be constructed manually in CellBlender.*

[`organelle_transport.bngl`](CBNGL/organelle_transport.bngl)
: Simple model of tranport involving two cell organelles. This model is used in the CellBlender tutorial. The model exported in SBML format can be imported into CellBlender by selecting File->Import->BioNetGen/SBML model (.bngl,.xml)

[`LV_comp.bngl`](CBNGL/LV_comp.bngl)
: Lotke-Volterra model in compartmental form for export to CellBlender. NOTE: The third reaction needs to be modified to set the product to `NULL`.

## cBNGL model of signaling/transcription with negative feedback

[`cBNGL_simple.bngl`](CBNGL/cBNGL_simple.bngl)

**Exercise:** Can you identify two parameters that change the *frequency* of the oscillations? Can you find two parameters that change the *amplitute* of the oscillations?

## Visualization examples

[`visualize.bngl`](Viz/visualize.bngl)
: Demonstrates the various visualization types that can be generated for a BNGL model. 

[`FceRI_viz.bngl`](Viz/FceRI_viz.bngl)
: A complex model of FceRI (immunoreceptor on mast cells and basophils) signaling with over 200 chemical species and 2000 reactions. 

A manuscript on the visualization methods and capabilities available with BioNetGen is available [here](https://doi.org/10.1371/journal.pcbi.1005857).

An extended tutorial on visualization is available in the Supporting information: [S2 Appendix. Tutorial](https://doi.org/10.1371/journal.pcbi.1005857.s007).

## SBML importer

## Larger models

[Larger models](LargerModels)

[`fceri_ji.bngl`](LargerModels/fceri_ji.bngl)
: A more complex immunoreceptor signaling network. Demonstrates use of simulation protocol.

![Flagman](images/Flagman-smaller.gif)
