The Software Landscape for the Density Matrix
Renormalization Group
===
Per Sehlstedt, Jan Brandejs, Lars Karlsson and Paolo Bientinesi\
pers at cs.umu.se 

This list covers the rapidly expanding DMRG software landscape, comprehensively comparing features of many existing packages. We aim to raise awareness of existing packages and guide researchers in finding a suitable package for their needs while helping developers identify opportunities for collaboration, modularity standardization, and optimization. Despite DMRG’s broad applicability across fields like materials science, quantum chemistry, and quantum computing, many independent implementations have been developed, leading to duplicated efforts and limited interoperability. We highlight key aspects, including parallelism strategies for high-performance computing and symmetry-adapted formulations that enhance efficiency. 

We invite the community to contribute, especially when a key software is missing.

## High-Level Overview

High-level aspects of each package. This includes the implementation language and scheme, support for symmetries, and HPC capabilities.

| ID | Name | Language | OSS | Gen. | Sym. A | Sym. NA | HPC SM | HPC DM | HPC GPU |
|---|---|---|---|---|---|---|---|---|---|
| 1 | ALPS DMRG | C++, Pythonⁱ | [1](https://github.com/ALPS/alps) | 1ˢᵗ | ✓ | - | ✓ | - | - |
| 2 | ALPS MPS | C++, Pythonⁱ | [2](https://github.com/ALPS/alps) | 2ⁿᵈ | ✓ | - | ✓ | - | - |
| 3 | BAGEL | C++ | [3](https://github.com/BAGEL-FDE/bagel-fde) | 1ˢᵗ | ✓ | - | ✓ | ✓ | - |
| 4 | Block2 | C++, Pythonⁱ | [4](https://github.com/block2/block2) | 2ⁿᵈ‡ | ✓ | ✓ | ✓ | ✓ | - |
| 5 | CheMPS2 | C++, Pythonⁱ | [5](https://github.com/sebwouters/CheMPS2) | 1ˢᵗ | ✓ | ✓ | ✓ | ✓ | - |
| 6 | ChemTensor | C, Pythonⁱ | [6](https://github.com/ChemTensor/ChemTensor) | 2ⁿᵈ† | ✓ | ✓ | ✓ | - | - |
| 7 | Chen et al. | C++ | - | 1ˢᵗ | ✓ | - | ✓ | - | S |
| 8 | Cytnx | C++, Pythonⁱ | [8](https://github.com/Cytnx/Cytnx) | 2ⁿᵈ† | ✓ | - | ✓ | - | S |
| 9 | DMRG-Budapest | C++, MATLABⁱ | - | 2ⁿᵈ‡ | ✓ | ✓ | ✓ | ✓ | M |
| 10 | DMRG++ | C++ | [10](https://github.com/DMRGpp/DMRGpp) | 1ˢᵗ | ✓ | - | ✓ | - | S |
| 11 | DMRGPy | Python | [11](https://github.com/DMRGPy/DMRGPy) | 2ⁿᵈ | - | - | ✓ | - | - |
| 12 | FOCUS | C++ | - | 1ˢᵗ | ✓ | ✓ | ✓ | ✓ | M |
| 13 | Hong et al. | C++ | - | 2ⁿᵈ | - | - | - | - | S |
| 14 | ITensor | C++ | [14](https://github.com/ITensor/ITensor) | 2ⁿᵈ | ✓ | - | ✓ | - | - |
| 15 | ITensorMPS.jl | Julia | [15](https://github.com/ITensor/ITensorMPS.jl) | 2ⁿᵈ | ✓ | - | ✓ | - | S |
| 16 | Kylin | C++ | - | 2ⁿᵈ | ✓ | ✓ | ✓ | - | - |
| 17 | MOLMPS | C++ | - | 1ˢᵗ | ✓ | - | ✓ | ✓ | S |
| 18 | MPSKit.jl | Julia | [18](https://github.com/MPSKit/MPSKit.jl) | 2ⁿᵈ | ✓ | ✓ | ✓ | - | - |
| 19 | MPToolkit | C++ | [19](https://github.com/mpstools/MPToolkit) | 2ⁿᵈ | ✓ | ✓ | ✓ | - | - |
| 20 | OSMPS | Fortran, Pythonⁱ | [20](https://github.com/orbitalscience/OSMPS) | 2ⁿᵈ | ✓ | - | ✓ | ✓ | - |
| 21 | PyTeNet | Python | [21](https://github.com/pytenet/pytenet) | 2ⁿᵈ | ✓ | - | ✓ | - | - |
| 22 | QCMaquis | C++ | [22](https://github.com/qcmaquis/qcmaquis) | 2ⁿᵈ | ✓ | ✓ | ✓ | - | - |
| 23 | QSpace | C++, MATLABⁱ | [23](https://github.com/QSpace/QSpace) | 2ⁿᵈ‡ | ✓ | ✓ | ✓ | - | - |
| 24 | Quantum TEA | Fortran, Pythonⁱ | [24](https://github.com/QuantumTEA/QuantumTEA) | 2ⁿᵈ† | ✓ | - | ✓ | - | S |
| 25 | quimb | Python | [25](https://github.com/quimb-dev/quimb) | 2ⁿᵈ | - | - | ✓ | - | - |
| 26 | Renormalizer | Python | [26](https://github.com/Renormalizer/Renormalizer) | 2ⁿᵈ† | ✓ | - | ✓ | - | S |
| 27 | SeeMPS2 | Python | [27](https://github.com/seemps/seemps2) | 2ⁿᵈ | - | - | ✓ | - | - |
| 28 | SUNDMRG.jl | Julia | [28](https://github.com/SUNDMRG/SUNDMRG.jl) | 1ˢᵗ | - | ✓ | ✓ | ✓ | S |
| 29 | SymMPS | C++ | [29](https://github.com/SymMPS/SymMPS) | 2ⁿᵈ | ✓ | - | ✓ | - | - |
| 30 | SyTen | C++, Pythonⁱ | - | 2ⁿᵈ | ✓ | ✓ | ✓ | ✓ | S |
| 31 | TeNPy | Python | [31](https://github.com/tenpy/tenpy) | 2ⁿᵈ | ✓ | - | ✓ | ✓ | - |
| 32 | tensor-tools | C++ | [32](https://github.com/tensor-tools/tensor-tools) | 2ⁿᵈ | ✓ | - | ✓ | ✓ | - |
| 33 | TensorTrack | MATLAB | [33](https://github.com/TensorTrack/TensorTrack) | 2ⁿᵈ | ✓ | ✓ | ✓ | - | - |
| 34 | UltraDMRG | C++ | [34](https://github.com/ultradmrg/ultradmrg) | 2ⁿᵈ | ✓ | - | ✓ | ✓ | S |
| 35 | xDMRG++ | C++ | [35](https://github.com/xdmrgpp/xdmrgpp) | 2ⁿᵈ | - | - | ✓ | - | - |

Table Key:

* **ID:** A unique identifier for cross-referencing purposes.

* **Name:** The official name of the package, except for unnamed packages 7 and 13.

* **Language:** The programming languages used for implementation and interfaces. Languages marked with <sup>i</sup>-superscripts are those mainly used as interfaces.

* **Open Source Software (OSS):** Indicates whether the package is open-source and available for download.

* **Implementation Formalism (Gen.):** Specifies which view the DMRG implementation is based on: \
  1<sup>st</sup> for the traditional RG perspective using renormalized operators and \
  2<sup>nd</sup> for the tensor network perspective using MPO/MPS. \
  <sup>‡</sup>-superscripts mark those who support both views, and \
  <sup>†</sup>-superscripts mark those who support the usage of TTNO/TTNS.

* **Symmetry Support (Sym.):** Indicates whether the package is symmetry-adapted to support abelian (A) and/or non-abelian (NA) symmetries or not.

* **High-Performance Computing (HPC):** Indicates support for HPC platforms, categorized as shared-memory parallelism (SM), distributed-memory parallelism (DM), and single- (S) or multi- (M) GPU acceleration (GPU).
