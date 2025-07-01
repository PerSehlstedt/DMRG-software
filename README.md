# The Software Landscape for the Density Matrix Renormalization Group

Per Sehlstedt, Jan Brandejs, Lars Karlsson and Paolo Bientinesi\
pers at cs.umu.se 

This list covers the rapidly expanding DMRG software landscape, comprehensively comparing features of many existing packages. We aim to raise awareness of existing packages and guide researchers in finding a suitable package for their needs while helping developers identify opportunities for collaboration, modularity standardization, and optimization. Despite DMRG’s broad applicability across fields like materials science, quantum chemistry, and quantum computing, many independent implementations have been developed, leading to duplicated efforts and limited interoperability. We highlight key aspects, including parallelism strategies for high-performance computing and symmetry-adapted formulations that enhance efficiency. 

We invite the community to contribute in case of missing software.

Please consider citing the original paper [arXiv:2506.12629](https://arxiv.org/abs/2506.12629).
<!-- [![ArXiv:2506.12629](https://img.shields.io/badge/arXiv-2506.12629-b31b1b)](https://arxiv.org/abs/2506.12629) -->

## Table of Contents

1. [Packages Implementing DMRG](#packages-implementing-dmrg)
2. [Feature Comparisons](#feature-comparisons)
    1. [High-level Overview](#high-level-overview)
    2. [Parallelism and Mixed-Precision](#parallelism-and-mixed-precision)
    3. [Symmetries](#symmetries)
    4. [Hamiltonians](#hamiltonians)
    5. [Eigensolvers](#eigensolvers)
3. [References](#references)


## Packages Implementing DMRG 

TODO: Something something packages in alphabetical order.

TODO: Somehow make separate (sub)section/list for the packages that are not compared.

TODO: Add descriptions for all the packages. As a start, only take the first sentence from arXiv paper and add references? (i.e., don't include the developer info?). Potentially take the last sentence as well.   

NOTE: How to do with references? Bad for maintainability to have global numbering? Also don't want to take up too much space by having full titles?

NOTE: As a start, probably include the minimum necessary, and if the developers feel like somthing is missing they can add it themself?

NOTE: Badges?
[![ArXiv](https://img.shields.io/badge/arXiv-2506.15460-b31b1b)](https://arxiv.org/abs/2503.15460)

- [ALPS](https://github.com/ALPSim/ALPS) (Algorithms and Libraries for Physics Simulations) is a software package aiming to provide standardized components for numerical simulations of condensed matter systems. It contains two separate DMRG packages: *ALPS DMRG* and *ALPS MPS*. [ALPS Webpage](https://alps.comp-phys.org)

    Publications/References/Articles(?):

    [doi:10.1016/j.jmmm.2006.10.304](http://dx.doi.org/10.1016/j.jmmm.2006.10.304), 
    [doi:10.1088/1742-5468/2011/05/p05001](http://dx.doi.org/10.1088/1742-5468/2011/05/P05001), 
    [doi:10.1016/j.cpc.2014.08.019](http://dx.doi.org/10.1016/j.cpc.2014.08.019)


- [BAGEL](https://github.com/qsimulate-open/bagel)
- [Block2](https://github.com/block-hczhai/block2-preview)
- [CheMPS2](https://github.com/SebWouters/CheMPS2)
- [ChemTensor](https://github.com/qc-tum/chemtensor)
- Chen et al.
- [Cytnx](https://github.com/Cytnx-dev/Cytnx)
- DMRG-Budapest
- [DMRG++](https://github.com/g1257/dmrgpp)
- [DMRGPy](https://github.com/joselado/dmrgpy)
- FOCUS
- Hong et al.
- [ITensor](https://github.com/ITensor/ITensor)
- [ITensorMPS.jl](https://github.com/ITensor/ITensorMPS.jl)
- Kylin
- MOLMPS
- [MPSKit.jl](https://github.com/QuantumKitHub/MPSKit.jl)
- [MPToolkit](https://github.com/mptoolkit/mptoolkit)
- [OSMPS](https://sourceforge.net/projects/openmps/)
- [PyTeNet](https://github.com/cmendl/pytenet)
- [QCMaquis](https://github.com/qcscine/qcmaquis)
- [QSpace](https://bitbucket.org/qspace4u/workspace/repositories/)
- [Quantum TEA](https://baltig.infn.it/quantum_tea/quantum_tea)
- [quimb](https://github.com/jcmgray/quimb)
- [Renormalizer](https://github.com/shuaigroup/Renormalizer)
- [SeeMPS2](https://github.com/juanjosegarciaripoll/seemps2)
- [SUNDMRG.jl](https://github.com/MGYamada/SUNDMRG.jl)
- [SymMPS](https://www.symmps.eu/)
- SyTen
- [TeNPy](https://github.com/tenpy/tenpy)
- [tensor-tools](https://github.com/ClarkResearchGroup/tensor-tools)
- [TensorTrack](https://github.com/quantumghent/TensorTrack)
- [UltraDMRG](https://github.com/QuantumLiquids/UltraDMRG)
- [xDMRG++](https://github.com/DavidAce/xDMRGpp)

    <!-- [doi:]() -->


## Feature Comparisons


### High-level Overview

High-level aspects of each package. This includes the implementation language and scheme, support for symmetries, and HPC capabilities. Note that support for multiple features does not imply that they can be utilized simultaneously.

| Name | Language | OSS | Gen. | Sym. | | HPC | | |
|---|---|:---:|---|:---:|:---:|:---:|:---:|:---:|
| | | | | A | NA | SM | DM | GPU |
| [ALPS DMRG](https://github.com/ALPSim/ALPS) | C++, Python<sup>i</sup> | ✓ | 1<sup>st</sup> | ✓ | - | ✓ | - | - |
| [ALPS MPS](https://github.com/ALPSim/ALPS) | C++, Python<sup>i</sup> | ✓ | 2<sup>nd</sup> | ✓ | - | ✓ | - | - |
| [BAGEL](https://github.com/qsimulate-open/bagel) | C++ | ✓ | 1<sup>st</sup> | ✓ | - | ✓ | ✓ | - |
| [Block2](https://github.com/block-hczhai/block2-preview) | C++, Python<sup>i</sup> | ✓ | 2<sup>nd</sup>‡ | ✓ | ✓ | ✓ | ✓ | - |
| [CheMPS2](https://github.com/SebWouters/CheMPS2) | C++, Python<sup>i</sup> | ✓ | 1<sup>st</sup> | ✓ | ✓ | ✓ | ✓ | - |
| [ChemTensor](https://github.com/qc-tum/chemtensor) | C, Python<sup>i</sup> | ✓ | 2<sup>nd</sup>† | ✓ | ✓ | ✓ | - | - |
| Chen et al. | C++ | - | 1<sup>st</sup> | ✓ | - | ✓ | - | S |
| [Cytnx](https://github.com/Cytnx-dev/Cytnx) | C++, Python<sup>i</sup> | ✓ | 2<sup>nd</sup>† | ✓ | - | ✓ | - | S |
| DMRG-Budapest | C++, MATLAB<sup>i</sup> | - | 2<sup>nd</sup>‡ | ✓ | ✓ | ✓ | ✓ | M |
| [DMRG++](https://github.com/g1257/dmrgpp) | C++ | ✓ | 1<sup>st</sup> | ✓ | - | ✓ | - | S |
| [DMRGPy](https://github.com/joselado/dmrgpy) | Python | ✓ | 2<sup>nd</sup> | - | - | ✓ | - | - |
| FOCUS | C++ | - | 1<sup>st</sup> | ✓ | ✓ | ✓ | ✓ | M |
| Hong et al. | C++ | - | 2<sup>nd</sup> | - | - | - | - | S |
| [ITensor](https://github.com/ITensor/ITensor) | C++ | ✓ | 2<sup>nd</sup> | ✓ | - | ✓ | - | - |
| [ITensorMPS.jl](https://github.com/ITensor/ITensorMPS.jl) | Julia | ✓ | 2<sup>nd</sup> | ✓ | - | ✓ | - | S |
| Kylin | C++ | - | 2<sup>nd</sup> | ✓ | ✓ | ✓ | - | - |
| MOLMPS | C++ | - | 1<sup>st</sup> | ✓ | - | ✓ | ✓ | S |
| [MPSKit.jl](https://github.com/QuantumKitHub/MPSKit.jl) | Julia | ✓ | 2<sup>nd</sup> | ✓ | ✓ | ✓ | - | - |
| [MPToolkit](https://github.com/mptoolkit/mptoolkit) | C++ | ✓ | 2<sup>nd</sup> | ✓ | ✓ | ✓ | - | - |
| [OSMPS](https://sourceforge.net/projects/openmps/) | Fortran, Python<sup>i</sup> | ✓ | 2<sup>nd</sup> | ✓ | - | ✓ | ✓ | - |
| [PyTeNet](https://github.com/cmendl/pytenet) | Python | ✓ | 2<sup>nd</sup> | ✓ | - | ✓ | - | - |
| [QCMaquis](https://github.com/qcscine/qcmaquis) | C++ | ✓ | 2<sup>nd</sup> | ✓ | ✓ | ✓ | - | - |
| [QSpace](https://bitbucket.org/qspace4u/workspace/repositories/) | C++, MATLAB<sup>i</sup> | ✓ | 2<sup>nd</sup>‡ | ✓ | ✓ | ✓ | - | - |
| [Quantum TEA](https://baltig.infn.it/quantum_tea/quantum_tea) | Fortran, Python<sup>i</sup> | ✓ | 2<sup>nd</sup>† | ✓ | - | ✓ | - | S |
| [quimb](https://github.com/jcmgray/quimb) | Python | ✓ | 2<sup>nd</sup> | - | - | ✓ | - | - |
| [Renormalizer](https://github.com/shuaigroup/Renormalizer) | Python | ✓ | 2<sup>nd</sup>† | ✓ | - | ✓ | - | S |
| [SeeMPS2](https://github.com/juanjosegarciaripoll/seemps2) | Python | ✓ | 2<sup>nd</sup> | - | - | ✓ | - | - |
| [SUNDMRG.jl](https://github.com/MGYamada/SUNDMRG.jl) | Julia | ✓ | 1<sup>st</sup> | - | ✓ | ✓ | ✓ | S |
| [SymMPS](https://www.symmps.eu/) | C++ | ✓ | 2<sup>nd</sup> | ✓ | - | ✓ | - | - |
| SyTen | C++, Python<sup>i</sup> | - | 2<sup>nd</sup> | ✓ | ✓ | ✓ | ✓ | S |
| [TeNPy](https://github.com/tenpy/tenpy) | Python | ✓ | 2<sup>nd</sup> | ✓ | - | ✓ | ✓ | - |
| [tensor-tools](https://github.com/ClarkResearchGroup/tensor-tools) | C++ | ✓ | 2<sup>nd</sup> | ✓ | - | ✓ | ✓ | - |
| [TensorTrack](https://github.com/quantumghent/TensorTrack) | MATLAB | ✓ | 2<sup>nd</sup> | ✓ | ✓ | ✓ | - | - |
| [UltraDMRG](https://github.com/QuantumLiquids/UltraDMRG) | C++ | ✓ | 2<sup>nd</sup> | ✓ | - | ✓ | ✓ | S |
| [xDMRG++](https://github.com/DavidAce/xDMRGpp) | C++ | ✓ | 2<sup>nd</sup> | - | - | ✓ | - | - |

Table key:

* **Name:** The official name of the package, if available; otherwise, the authors of an associated publication. Names link to source code if the package is open source.

* **Language:** The programming languages used for implementation and interfaces. Languages marked with <sup>i</sup>-superscripts are those mainly used as interfaces.

<!-- Could potentially remove this column if names are hyperlinked to source code or change it to show what licence is used? -->
* **Open Source Software (OSS):** Indicates whether the package is open source and available for download.

* **Implementation Formalism (Gen.):** Specifies which view the DMRG implementation is based on: \
  1<sup>st</sup> for the traditional RG perspective using renormalized operators and \
  2<sup>nd</sup> for the tensor network perspective using MPO/MPS. \
  ‡-superscripts mark those who support both views, and \
  †-superscripts mark those who support the usage of TTNO/TTNS.

* **Symmetry Support (Sym.):** Indicates whether the package is symmetry-adapted to support abelian (A) and/or non-abelian (NA) symmetries or not.

* **High-Performance Computing (HPC):** Indicates support for HPC platforms, categorized as shared-memory parallelism (SM), distributed-memory parallelism (DM), and single- (S) or multi- (M) GPU acceleration (GPU).


### Parallelism and Mixed-Precision

Support for parallelism strategies and mixed-precision optimization techniques.

| Name | HPC | | | Parallelism | | | | | MP |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| | SM | DM | GPU | i | ii | iii | iv | v | |
| ALPS DMRG | ✓ | - | - | ✓ | - | - | - | - | - |
| ALPS MPS | ✓ | - | - | ✓ | ✓ | - | - | - | - |
| BAGEL | ✓ | ✓ | - | ✓ | - | - | - | - | - |
| Block2 | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| CheMPS2 | ✓ | ✓ | - | - | ✓ | ✓ | - | - | - |
| ChemTensor | ✓ | - | - | - | ✓ | - | ✓ | - | - |
| Chen et al. | ✓ | - | S | ✓ | ✓ | - | - | ✓ | - |
| Cytnx | ✓ | - | S | ✓ | ✓ | ✓ | - | - | - |
| DMRG-Budapest | ✓ | ✓ | M | ✓ | ✓ | ✓ | ✓ | - | ✓ |
| DMRG++ | ✓ | - | S | ✓ | ✓ | - | - | - | - |
| DMRGPy | ✓ | - | - | ✓ | - | - | - | - | - |
| FOCUS | ✓ | ✓ | M | ✓ | ✓ | ✓ | - | - | - |
| Hong et al. | - | - | S | ✓ | - | - | - | - | - |
| ITensor | ✓ | - | - | ✓ | ✓ | - | - | - | - |
| ITensorMPS.jl | ✓ | - | S | ✓ | ✓ | - | - | - | ✓ |
| Kylin | ✓ | - | - | - | ✓ | ✓ | - | - | ✓ |
| MOLMPS | ✓ | ✓ | S | ✓ | ✓ | ✓ | - | - | - |
| MPSKit.jl | ✓ | - | - | ✓ | ✓ | - | ✓ | - | - |
| MPToolkit | ✓ | - | - | ✓ | ✓ | - | - | - | - |
| OSMPS | ✓ | ✓ | - | ✓ | ✓ | - | - | - | - |
| PyTeNet | ✓ | - | - | ✓ | - | - | - | - | - |
| QCMaquis | ✓ | - | - | - | ✓ | ✓ | ✓ | - | - |
| QSpace | ✓ | - | - | ✓ | ✓ | - | - | - | ✓ |
| Quantum TEA | ✓ | - | S | ✓ | - | - | - | - | ✓ |
| quimb | ✓ | - | - | ✓ | - | - | - | - | - |
| Renormalizer | ✓ | - | S | ✓ | - | - | - | - | - |
| SeeMPS2 | ✓ | - | - | ✓ | - | - | - | - | - |
| SUNDMRG.jl | ✓ | ✓ | S | ✓ | ✓ | - | - | - | - |
| SymMPS | ✓ | - | - | ✓ | ✓ | - | - | - | - |
| SyTen | ✓ | ✓ | S | ✓ | ✓ | - | ✓ | ✓ | - |
| TeNPy | ✓ | ✓ | - | ✓ | ✓ | - | ✓ | - | - |
| tensor-tools | ✓ | ✓ | - | ✓ | - | - | - | - | - |
| TensorTrack | ✓ | - | - | ✓ | - | - | - | - | - |
| UltraDMRG | ✓ | ✓ | S | ✓ | ✓ | - | ✓ | - | - |
| xDMRG++ | ✓ | - | - | ✓ | - | - | - | - | - |

Table key:

We closely follow the classification summary and five-level hierarchy of parallelism first introduced by Zhai and Chan [[1]](#references) and then further discussed by Tian and Ma [[2]](#references). The following describes the HPC strategies:

* **Parallel strategies (Parallelism):** Indicates support for the following types of parallelism:
    * **Parallelism within matrix operations (i):** The most fine-grained and lowest-level source of parallelism is the data parallelism found primarily within the matrix–matrix and matrix–vector multiplications that underpin the tensor algebra in the DMRG algorithm.
    * **Parallelism over symmetry sectors (ii):** The block-sparse tensor representations in symmetry-adapted DMRG implementations enable parallelism across symmetry sectors. The calculations on different blocks are independent, allowing them to run simultaneously.
    * **Parallelism over normal and complementary operators (iii):** In ab initio DMRG, the left-right decomposition of the Hamiltonian is expressed as a summation of products of normal and complementary operators. These operators are distributed over threads and processors, processing the corresponding calculations concurrently.
    * **Parallelism over a sum of sub-Hamiltonians (iv):** The Hamiltonian is rewritten as a sum of sub-Hamiltonians such that each term can be manipulated independently. This coarse-grained, high-level parallelism is easily expressed in the MPO formalism and adds little communication overhead.
    * **Parallelism over sites (v):** The DMRG sequentially sweeps back and forth along a path. The path can be partitioned into sections that can be processed simultaneously at the expense of extra communication at the section boundaries. This coarse-grained parallelism is especially useful for large systems with many sites.

* **Mixed-precision (MP):** Indicates support for the recently developed mixed-precision optimization technique introduced by Tian et al., where the initial sweeps are accelerated by using reduced floating-point precision. Later sweeps restore full precision by switching to full floating-point precision.

### Symmetries

Support for various types of symmetries. Note that support for multiple features does not imply that they can be utilized simultaneously.

| Name | U(1) | Z | SU | P | Z<sub>2</sub><sup>f</sup> | Other |
|---|:---:|:---:|:---:|:---:|:---:|---|
| ALPS DMRG | ✓ | - | - | - | ✓ | - |
| ALPS MPS | ✓ | 2 | - | - | ✓ | - |
| BAGEL | ✓ | - | - | - | ✓ | - |
| Block2 | ✓ | n | 2 | ✓ | ✓ | - |
| CheMPS2 | ✓ | - | 2 | ✓ | ✓ | - |
| ChemTensor | ✓ | - | 2 | - | - | - |
| Chen et al. | ✓ | - | - | - | ✓ | - |
| Cytnx | ✓ | n | - | - | ✓ | - |
| DMRG-Budapest | ✓ | n | n | ✓ | ✓ | - |
| DMRG++ | ✓ | - | - | - | ✓ | - |
| DMRGPy | - | - | - | - | ✓ | - |
| FOCUS | ✓ | - | 2 | - | ✓ | - |
| Hong et al. | - | - | - | - | - | - |
| ITensor | ✓ | n | - | - | ✓ | - |
| ITensorMPS.jl | ✓ | n | - | - | ✓ | - |
| Kylin | ✓ | - | 2 | ✓ | ✓ | - |
| MOLMPS | ✓ | - | - | ✓ | ✓ | - |
| MPSKit.jl | ✓ | n | n | - | ✓ | Anyonic/Categoric |
| MPToolkit | ✓ | n | 2 | - | ✓ | - |
| OSMPS | ✓ | 2 | - | - | ✓ | - |
| PyTeNet | ✓ | - | - | - | - | - |
| QCMaquis | ✓ | 2 | 2 | ✓ | ✓ | - |
| QSpace | ✓ | n | n | - | ✓ | SO(n), Sp(2n) |
| Quantum TEA | ✓ | n | - | - | ✓ | - |
| quimb | - | - | - | - | ✓ | - |
| Renormalizer | ✓ | - | - | - | ✓ | - |
| SeeMPS2 | - | - | - | - | - | - |
| SUNDMRG.jl | - | - | n | - | - | - |
| SymMPS | ✓ | - | - | - | ✓ | - |
| SyTen | ✓ | n | 2 | - | ✓ | - |
| TeNPy | ✓ | n | - | - | ✓ | - |
| tensor-tools | ✓ | - | - | - | ✓ | - |
| TensorTrack | ✓ | n | n | - | ✓ | - |
| UltraDMRG | ✓ | n | - | - | ✓ | - |
| xDMRG++ | - | - | - | - | ✓ | - |

Table key:

* **The unitary group** $\mathrm{U}(1)$: Indicates support for the unitary group of degree one, which is the most commonly used symmetry. It typically enforces the conservation of particle numbers (total electrons or separate spin counts) and total spin magnetization.
* **Cyclic groups** ($\mathbb{Z}$): Indicates support for either $\mathbb{Z}_2$ or more general $\mathbb{Z}_n$ symmetries. A common usage for $\mathbb{Z}_2$ is to enforce the spin-flip (parity) symmetry in the transverse-field Ising model, where flipping all spins leaves the Hamiltonian unchanged. The more general $\mathbb{Z}_n$ group is common in models with an $n$-fold rotational or cyclic invariance.
* **Special unitary groups** ($\mathrm{SU}$): Indicates support for either $\mathrm{SU}(2)$ or more generally $\mathrm{SU}(n)$. The $\mathrm{SU}(2)$ group is most common and is often applied to preserve the total spin, often referred to as spin $\mathrm{SU}(2)$. An example of $\mathrm{SU}(n)$ is the channel $\mathrm{SU}(3)$ symmetry considered by Weichselbaum.
* **Point groups** ($\mathrm{P}$): Indicates support for abelian point group symmetries $\mathrm{P} \in \{C_1, C_i, C_2, C_s, C_{2h}, D_2, C_{2v}, D_{2h}\}$ with real-valued character tables. They are often used for molecular systems to enforce spatial symmetries.
* **Fermion parity** ($\mathbb{Z}_2^\mathrm{f}$): Indicates support for the fermion parity, which captures the anti-commuting nature of fermionic degrees of freedom. The parity is a $\mathbb{Z}_2$ quantum number that yields an additional sign when exchanging two fermions (each carrying odd parity).

* **Other**: Indicates support for less common symmetries, such as the special orthogonal group $\mathrm{SO}(n)$, the symplectic group $\mathrm{Sp}(2n)$, and Anyonic symmetries. Anyons are particles with non-trivial exchange statistics that are neither fermions nor bosons.

### Hamiltonians

Support for custom Hamiltonian constructions and the variety of fields for built-in models.

| Name | Construction | | Built-in |
|---|:---:|:---:|---|
| |  Custom | Operator | |
| ALPS DMRG | ✓ | ✓ | Specific |
| ALPS MPS | - | - | Specific |
| BAGEL | - | - | Specific |
| Block2 | ✓ | ✓ | Broad |
| CheMPS2 | - | - | Specific |
| ChemTensor | ✓ | ✓ | Broad |
| Chen et al. | - | - | Broad |
| Cytnx | ✓ | ✓ | - |
| DMRG-Budapest | ✓ | ✓ | Broad |
| DMRG++ | ✓ | - | Specific |
| DMRGPy | ✓ | ✓ | - |
| FOCUS | - | - | Specific |
| Hong et al. | - | - | Specific |
| ITensor | ✓ | ✓ | - |
| ITensorMPS.jl | ✓ | ✓ | - |
| Kylin | - | - | Specific |
| MOLMPS | - | - | Broad |
| MPSKit.jl | ✓ | ✓ | Specific |
| MPToolkit | ✓ | - | Broad |
| OSMPS | ✓ | ✓ | - |
| PyTeNet | ✓ | ✓ | Broad |
| QCMaquis | - | - | Broad |
| QSpace | ✓ | ✓ | Specific |
| Quantum TEA | ✓ | ✓ | Specific |
| quimb | ✓ | ✓ | Specific |
| Renormalizer | ✓ | ✓ | Broad |
| SeeMPS2 | ✓ | ✓ | - |
| SUNDMRG.jl | - | - | Specific |
| SymMPS | ✓ | - | - |
| SyTen | ✓ | - | - |
| TeNPy | ✓ | ✓ | Broad |
| tensor-tools | ✓ | ✓ | - |
| TensorTrack | ✓ | ✓ | Specific |
| UltraDMRG | ✓ | ✓ | - |
| xDMRG++ | - | - | Specific |


Table key:

* **Construction:** Indicates if and how a user can define custom Hamiltonians.
    * **Custom:** Indicates support for some generic custom Hamiltonian construction interface.
    * **Operator:** Indicates support for constructing custom Hamiltonians using local $n$-body operators defined on the different site-indices upon which the operators act.
* **Built-in:** Indicates whether the package contains built-in Hamiltonians that target a specific or broad range of fields.


### Eigensolvers

The eigensolvers used by each package and a comment for bespoke implementations.

| Name | Eigensolver | Comment |
|---|---|---|
| ALPS DMRG | Own | Lanczos  |
| ALPS MPS | IETL in ALPS | Jacobi–Davidson  |
| BAGEL | Own | Davidson |
| Block2 | Own | Davidson  |
| CheMPS2 | Own | Davidson  |
| ChemTensor | Own | Lanczos |
| Chen et al. | Own | Davidson |
| Cytnx | Own | Lanczos |
| DMRG-Budapest | Own, ARPACK | Lanczos, Davidson, etc. |
| DMRG++ | Own | Lanczos |
| DMRGPy | ITensor (C++/Julia) | - |
| FOCUS | Own | Davidson |
| Hong et al. | Own | Lanczos |
| ITensor | Own | Davidson |
| ITensorMPS.jl | KrylovKit.jl | Lanczos, Arnoldi |
| Kylin | Own | Lanczos, Davidson |
| MOLMPS | Own | Davidson |
| MPSKit.jl | KrylovKit.jl | Lanczos, Arnoldi |
| MPToolkit | ARPACK | Lanczos, Davidson, etc. |
| OSMPS | Own, ARPACK | Lanczos |
| PyTeNet | Own | Lanczos |
| QCMaquis | ALPS | Jacobi–Davidson |
| QSpace | Own | Davidson |
| Quantum TEA | Own, SciPy | Lanczos |
| quimb | SciPy, slepc4py | Krylov-Schur, Davidson, etc. |
| Renormalizer | Own, SciPy | Davidson |
| SeeMPS2 | SciPy | Lanczos |
| SUNDMRG.jl | Own | Lanczos |
| SymMPS | Own | Lanczos |
| SyTen | Own | Lanczos, Davidson |
| TeNPy | Own, SciPy | Lanczos |
| tensor-tools | Own | Davidson |
| TensorTrack | Own | Krylov-Schur |
| UltraDMRG | Own | Lanczos |
| xDMRG++ | PRIMME | Arnoldi, Davidson, etc. |

Table key:

* **Eigensolver:** Indicates if the eigensolver is a bespoke implementation or provided by some external dependency. Some packages include both, often implementing their own sparse solver complemented by an external dense solver.
* **Comment:** Short comment regarding the method used, mainly for packages that implement their own eigensolver, as they can be less flexible regarding method changes.
  

## References

[1] Zhai, H., & Chan, G. K.-L. (2021). Low communication high performance ab initio density matrix renormalization group algorithms. *The Journal of Chemical Physics*, *154*(22), 224107. [doi:10.1063/5.0050902](https://doi.org/10.1063/5.0050902)

[2] Tian, Y., Xie, Z., Luo, Z., & Ma, H. (2022). Mixed-Precision Implementation of the Density Matrix Renormalization Group. *Journal of Chemical Theory and Computation*, *18*(12), 7260–7271. [doi:10.1021/acs.jctc.2c00632](https://doi.org/10.1021/acs.jctc.2c00632)

