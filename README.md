# BioNetGen Tutorial

The files presented here are meant to provide a moderately paced but comprehensive introduction to the syntax and features of the BioNetGen language (BNGL) and modeling software. During the workshop, these examples will be used in a hand-on demonstration using the RuleBender interface.

**Click on the link to see the BNGL code.**

## Basic structure and syntax
[`ABC.bngl`](ABC/ABC.bngl)
: Simple binding model in BNGL using unstructured molecules to represent each species. Demonstrates basic syntax of `simulate` command.

[`ABC_scan.bngl`](ABC/ABC_scan.bngl)
: Simple binding model modified to use`parameters` block, which enables `parameter_scan`. Also demonstrates use of `#` for comments and `\` for line continuation.

[`ABC_ssa.bngl`](ABC/ABC_ssa.bngl)
: Simple binding model with modifed `method` option to `simulate` command to demonstrate `ssa` method for performing stochastic simulation.

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

[More advanced models of substrate modification dynamics](ABp/AdvancedModels.md). Demonstrates additional use of functions in rate laws and use of the `bifurcate` command to examine a bistable system.

![Flagman](images/Flagman-smaller.gif)
