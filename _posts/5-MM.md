
Section V: Molecular Mechanics

5.1. Force Fields

Molecular mechanics ignores electrons, and instead treats the system with classical mechanics. In quantum mechanics the equation we use to describe the system is the Hamiltonian. The parallel in molecular mechanics is called a force field. The force field for the AMBER method will be used as an example throughout this section. The energy of the system is broken up into terms describing the local structure (ball and spring approach), electrostatics and van der Waals interactions.

, uses a harmonic potential (Hooke's Law) to calculate the energy required to stretch a bond away from the optimal value for two atoms directly bonded to each other. A slightly more accurate predictor of a bond stretch is the Morse potential, but this is much more difficult to calculate.

, uses a harmonic potential to calculate the energy required to bend an angle away from the optimal value for the three connected atoms.

, uses a cosine function to treat the periodic relationship between energy and a (proper) dihedral angle.

, specifically accounts for van der Waals interactions (e.g., London dispersion) using the Lennard-Jones (6-12) function. Hydrogen-bonding interactions can be treated with an additional 10-12 potential.

, uses Coulomb's law to treat the electrostatic attraction/repulsion of atom pairs. The accuracy of this contribution can be enhanced by including a dipole term.

, additional terms (called cross-terms) can be included to treat the dependence of individual terms on nearby motion. For example, when the angle at an sp<sup>3</sup> center is compressed tighter than 109.5° the destabilization is calculated to be artificially too large, since the strain can be reduced by increasing the bond lengths to the substituents.

5.2. Atom Types

If you are going to be using molecular mechanics in HyperChem, the first thing you need to do is tell the program which force field you are using. From the Setup menu, select Molecular Mechanics, then choose AMBER. Next, select Force Field from the setup menu and choose the version of AMBER you wish to use (for example ff99). The program will ask if you want the program to recalculate atom types based on your selection, unless you have already defined them the way you want, this is usually a good idea.

One of the biggest differences between using quantum mechanics versus classical mechanics to treat a system is parameterization. The use of parameterization speeds up calculations by treating atoms in similar environments the same way. This idea is based on, for example, sp<sup>2</sup> carbons having similar optimal bond lengths and bond angles. Atom types are additional information that tell the program what kind of environment each atom experiences. In general, atom types are defined by hybridization and substituent effects (electronegativity). Table 2 contains descriptions for the atom types available with AMBER96. Most interfaces for computational programs can automatically determine atom types, but it can be wrong, so it is up to the user to double check atom types.

In GaussView, atom types can be defined in the Atom List Editor by viewing the MM Types columns and changing the AMBER Type values. In HyperChem, you can view the atom types that have been assigned by selecting Labels from the Display menu and selecting Type. If it is necessary to change an atom type, select the atom then select Set Atom Type… from the Build menu.

5.3. Atom Charges

The second piece of information required to run a molecular mechanics calculation is the partial charge on each atom. This can be calculated by running a single-point calculation on a guess structure. It is recommended that HF/6-31G(d) ESP charges (Merz-Kollman) be utilized for AMBER calculations.

Unless you are using amino acids or nucleic acids, you will have to provide the charges for most programs. In GaussView, you can load charges from an output file in the Atom List Editor by going to the Edit menu à MM Charges à From Mulliken (or From ESP). In HyperChem, select the atom, then Set Charge from the Build menu.

In Gaussian, when using molecular mechanics, the atom type and charge appear as part of the atom in the geometry specification.

{atom}-{atom type}-{charge}

For example, C-CT--0.348712

Table 2. Atom Types Defined for AMBER96<sup>a</sup>

| Atom | Type | Description | Type | Description |
| --- | --- | --- | --- | --- |
| C   | CT  | any sp<sup>3</sup> carbon | CR  | sp<sup>2</sup> aromatic in 5-membered ring next to two nitrogens (C<sub>γ</sub> His) |
|     | C   | any carbonyl sp<sup>2</sup> carbon | CB  | sp<sup>2</sup> aromatic at junction of 5- and 6-membered rings (C<sub>δ</sub> Trp) and both junction atoms in Ade and Gua |
|     | CA  | any aromatic sp<sup>2</sup> carbon (C<sub>ε</sub> of Arg) | C\* | sp<sup>2</sup> aromatic in 5-membered ring next to two carbons (C<sub>γ</sub> Trp) |
|     | CM  | any sp<sup>2</sup> carbon, double bonded | CN  | sp<sup>2</sup> junction between 5- and 6-membered rings and bonded to CH and NH (C<sub>ε</sub> in Trp) |
|     | CC  | sp<sup>2</sup> aromatic in 5-membered ring with one substituent & next to nitrogen (C<sub>γ</sub> of His) | CK  | sp<sup>2</sup> carbon in 5-membered aromatic between N and N-R (C8 in purines) |
|     | CV  | sp<sup>2</sup> aromatic in 5-membered ring next to carbon and lone pair nitrogen (C<sub>δ</sub> of His<sub>δ</sub>) | CQ  | sp<sup>2</sup> carbon in 6-membered ring between lone pair nitrogens (C2 in purines) |
|     | CW  | sp<sup>2</sup> aromatic in 5-membered ring next to carbon and NH (C<sub>δ</sub> of His<sub>ε</sub> and Trp) |     |     |
| N   | N   | sp<sup>2</sup> nitrogen in amides | N\* | sp<sup>2</sup> nitrogen in 5-membered ring with carbon substituent |
|     | NA  | sp<sup>2</sup> nitrogen in aromatic rings with hydrogen attached | N2  | sp<sup>2</sup> nitrogen of aromatic amines and guanidinium ions |
|     | NB  | sp<sup>2</sup> nitrogen in 5-membered ring with lone pair (N7 in purines) | N3  | sp<sup>3</sup> nitrogen |
|     | NC  | sp<sup>2</sup> nitrogen in 6-membered ring with lone pair (N3 in purines) |     |     |
| O   | OW  | sp<sup>3</sup> oxygen in TIP3P water | O   | sp<sup>2</sup> oxygen in amides |
|     | OH  | sp<sup>3</sup> oxygen in alcohols, Tyr, protonated carboxylic acids | O2  | sp<sup>2</sup> oxygen in anionic acids |
|     | OS  | sp<sup>3</sup> oxygen in ethers |     |     |
| S   | S   | sulphur in Met and Cys | SH  | sulphur in Cys |
| P   | P   | phosphorus in phosphates |     |     |
| H   | H   | H attached to N | H1  | H attached to aliphatic carbon with one electron-withdrawing subs. |
|     | HW  | H in TIP3P water | H2  | H attached to aliphatic carbon with two electron-withdrawing subs. |
|     | HO  | H in alcohols and acids | H3  | H attached to aliphatic carbon with three electron-withdrawing subs. |
|     | HS  | H attached to sulphur | HP  | H attached to carbon directly bonded to formally positive atoms |
|     | HA  | H attached to aromatic carbon | H4  | H attached to aromatic carbon with one electronegative neighbour |
|     | HC  | H attached to aliphatic carbon with no electron-withdrawing subs. | H5  | H attached to aromatic carbon with two electronegative neighbours |

<sup>a</sup>adapted from Cornell, W. D.; Cieplak, P.; Bayly, C. I.; Gould, I. R.; Merz, K. M.; Ferguson, D. M.; Spellmeyer, D. C.; Fox, T.; Caldwell, J. W.; Kollman, P. A. _J. Am. Chem. Soc._ **1995**, _117_, 5179-5197.
