# December 16

Not sure where the past few months went .. trying to get back into it.

Working on creating a Python library for reading neutron data files (cross sections, multiplicity, more?) directly to be able to calculate quantities and probabilities within scripts.

Thought of several options
* Query the NNDC website directly for each quantity.
* Download / Read ENDF files, either downloaded from NNDC or a local MCNP install
* Download / Read ACE formatted files, either downloaded from NNDC or a local MCNP install

Of the options reading ACE formatted files seemed to be the simplest, basically because ENDF data files may contain several errors.

In the MCNP format the latest data release from ENDF/B-VII.1 Release 0 is stored in ACE format at: $MCNP_DIR\MCNP_DATA\xdata\endf71x

From inspection, I think the data description is done through the file name and the ACE file contains a simple header and then plain tabulated cross-section data.

With ENDF/B-VII.1 a new ACE filename format was created called SZAX identifiers, in addition to a modified header format. This is detailed in LA-UR-12-25177

SSSZZZAAA.dddCC

SSS - Excited State
ZZZ - Atomic Number
AAA - Atomic Mass Number
ddd - Library Identifier
CC  - Class of Data

Given S (excited state), Z and A the SZA identifier can be structed as

SZA = S * 1000000 + Z * 1000 + A

The suffix (dddCC) described the data classes and is listed as

Class (CC) | Incident Particle | Description
---------- | ----------------- | -----------
nc         | Neutron           | Transport, continuous-energy
nd         | Neutron           | Transport, discrete-reaction
nm         | Neutron           | Transport, multigroup
pp         | Photon            | Photoatomic, continuous-energy
pu         | Photon            | Photonuclear, continuous-energy
ny         | Neutron           | Dosimetry
nt         | Neutron           | Thermal S(alpha, beta) discrete or continuous-energy
