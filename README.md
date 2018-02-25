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

## Using structured molecules and rules
[`AB.bngl`](AB/AB.bngl)
: Simple binding model re-factored to used structured molecules with binding sites and a binding rule that adds or deletes a bond. Things to notice:
* Contact Map panel in RuleBender shows Molecule and Component interactions.
* Clicking tabs associated with Obervables shows Patterns and corresponding mathces. 

[`BAB.bngl`](BAB/BAB.bngl)
: Simple binding model with a bivalent A molecule that has two identical sites for binding of B. Binding at each site is not affected by the status of the other site (noncooperative binding).

[`BAB_scan.bngl`](BAB/BAB_scan.bngl)
: Varying the amount of A reveals nonmonotonic behavior of complexation. This example demonstrates use of the `log_scale` option to `parameter_scan`.

![Flagman](images/Flagman-smaller.gif)
