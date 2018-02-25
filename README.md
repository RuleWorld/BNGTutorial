# BioNetGen Tutorial

The files presented here are meant to provide a moderately paced but comprehensive introduction to the syntax and features of the BioNetGen language (BNGL) and modeling software. During the workshop, these examples will be used in a hand-on demonstration using the RuleBender interface.

**Click on the link to see the BNGL code.**

[`ABC.bngl`](ABC/ABC.bngl)
: Simple binding model in BNGL using unstructured molecules to represent each species. Demonstrates basic syntax of `simulate` command.

[`ABC_scan.bngl`](ABC/ABC_scan.bngl)
: Simple binding model modified to use`parameters` block, which enables `parameter_scan`. Also demonstrates use of `#` for comments and `\` for line continuation.

[`AB.bngl`](AB/AB.bngl)
: Simple binding model re-factored to used structured molecules with binding sites and a binding rule that adds or deletes a bond.

![Flagman](images/Flagman.gif)
