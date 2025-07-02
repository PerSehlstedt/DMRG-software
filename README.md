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
    1. [High-Level Overview](#high-level-overview)
    2. [Parallelism and Mixed-Precision](#parallelism-and-mixed-precision)
    3. [Symmetries](#symmetries)
    4. [Hamiltonians](#hamiltonians)
    5. [Eigensolvers](#eigensolvers)
3. [References](#references)


## Packages Implementing DMRG 

TODO: Something something packages in alphabetical order.

TODO: Somehow make separate (sub)section/list for the packages that are not compared.

TODO: Make list collapsable (?) Could make each item collapsable (?)

NOTE: How to do with references? Bad for maintainability to have global numbering? Also don't want to take up too much space by having full titles?

NOTE: As a start, probably include the minimum necessary, and if the developers feel like somthing is missing they can add it themself?

Publications/References/Articles(?):

[doi:10.1016/j.jmmm.2006.10.304](http://dx.doi.org/10.1016/j.jmmm.2006.10.304), 
[doi:10.1088/1742-5468/2011/05/p05001](http://dx.doi.org/10.1088/1742-5468/2011/05/P05001), 
[doi:10.1016/j.cpc.2014.08.019](http://dx.doi.org/10.1016/j.cpc.2014.08.019)

- [ALPS](https://github.com/ALPSim/ALPS) (Algorithms and Libraries for Physics Simulations) is a software package aiming to provide standardized components for numerical simulations of condensed matter systems. It contains two separate DMRG packages: *ALPS DMRG* and *ALPS MPS*. [ALPS Webpage](https://alps.comp-phys.org).

- [BAGEL](https://github.com/qsimulate-open/bagel) (Brilliantly Advanced General Electronic-structure Library) is an electronic structure package. In its DMRG implementation, sites are individual molecules that collect multiple orbitals. [BAGEL Webpage](http://www.nubakery.org).

- [Block2](https://github.com/block-hczhai/block2-preview) aims to provide a comprehensive set of DMRG algorithms for use in electronic structure methods and other applications. It can interface with other quantum chemistry packages to enable hybrid DMRG methods, including [PySCF](https://github.com/pyscf/pyscf), [OpenMOLCAS](https://github.com/Molcas/OpenMolcas), and [Forte](https://github.com/evangelistalab/forte).

- [CheMPS2](https://github.com/SebWouters/CheMPS2) is a library containing a DMRG implementation for ab initio quantum chemistry. It can interface with quantum chemistry packages that can handle R(O)HF calculations and molecular orbital matrix elements, and this has been done for [Psi4](https://github.com/psi4/psi4) and [PySCF](https://github.com/pyscf/pyscf).

- [ChemTensor](https://github.com/qc-tum/chemtensor) is a package for tensor network algorithms centered around chemical systems.

- Chen et al. presents a hybrid parallel implementation of DMRG with custom subroutines for vector operations on the GPU for improved performance. More recently, they also presented a novel approach to real-space parallel DMRG, building upon the work of Stoudenmire and White.

- [Cytnx](https://github.com/Cytnx-dev/Cytnx) is a tensor network library designed for classical and quantum physics simulations. The package has interfaces similar to popular libraries like [NumPy](https://github.com/numpy/numpy), [SciPy](https://github.com/scipy/scipy), and [PyTorch](https://github.com/pytorch/pytorch).

- DMRG-Budapest is a package for general quantum many-body problems. It features various novel in-house optimization techniques to improve performance.

- [DMRG++](https://github.com/g1257/dmrgpp) implements the DMRG algorithm with an emphasis on generic programming and minimal software dependencies. Additionally, the package has a plug-in, [DMRG++PluginSc](https://code.ornl.gov/gonzalo_3/dmrgppPluginSc), to extend its capabilities to GPUs. [DMRG++ Webpage](https://g1257.github.io/dmrgPlusPlus/).

- [DMRGPy](https://github.com/joselado/dmrgpy) is a library to simulate quasi-one-dimensional spin chains and fermionic systems.  The library relies on ITensor (either the Julia or the C++ version).

- FOCUS implements an ab initio DMRG algorithm. It supports both non-relativistic and relativistic Hamiltonians, utilizing time-reversal symmetry in the latter case to reduce computational costs

- Hong et al. presents a DMRG implementation using various optimization strategies, specifically targeting GPUs with tensor cores.

- ITensor is a package for programming tensor network calculations, allowing users to focus on the connectivity of a tensor network without manually tracking indices. ITensor was initially implemented in C++ but later fully ported to Julia, with most new features first being developed there. The C++ version, [ITensor](https://github.com/ITensor/ITensor), includes DMRG in the main library, while the Julia version provides DMRG through the [ITensorMPS.jl](https://github.com/ITensor/ITensorMPS.jl) extension of [ITensors.jl](https://github.com/ITensor/ITensors.jl). [ITensor Webpage](https://itensor.org/).

- Kylin is an ab initio quantum chemistry software package for estimating the electronic structures of molecular systems. It is specially designed for calculations with large active spaces. [Kylin Webpage](https://kylin-qc.com/).

- MOLMPS is a parallel implementation of DMRG for quantum chemistry. The parallel scheme is based on an in-house MPI global memory library and supports various hybrid electronic structure methods.

- [MPSKit.jl](https://github.com/QuantumKitHub/MPSKit.jl) contains tensor network algorithms for one-dimensional quantum and two-dimensional statistical mechanics problems. It mainly builds upon [TensorKit.jl](https://github.com/Jutho/TensorKit.jl), which provides functionality for generic symmetries, and its capabilities can be extended with packages like [SUNRepresentations.jl](https://github.com/QuantumKitHub/SUNRepresentations.jl) and [MPSKitModels.jl](https://github.com/QuantumKitHub/MPSKitModels.jl). [QuantumGroup@Ugent Webpage](https://quantumghent.github.io/software/).

- [MPToolkit](https://github.com/mptoolkit/mptoolkit) (Matrix Product Toolkit) is a package for creating and manipulating MPS. It was initially envisioned as a "next-generation" DMRG code that integrates non-abelian symmetries and emphasizes a flexible, general approach to constructing Hamiltonian operators and measuring observables.

- [OSMPS](https://sourceforge.net/projects/openmps/) (Open Source MPS) is a collection of tensor network algorithms for simulating entangled one-dimensional many-body quantum systems. The initial focus was to offer a broad set of methods for quantum simulators based on atomic, molecular, and optical physics architectures.

- [PyTeNet](https://github.com/cmendl/pytenet) implements quantum tensor network operations and simulations structured around MPS and MPO classes. It acts as a facilitator of algorithmic experimentation. 

- [QCMaquis](https://github.com/qcscine/qcmaquis) is a SCINE module that builds upon the *ALPS MPS* code and implements various DMRG-based algorithms. Key features include vibrational, time-dependent, and nuclear-electron DMRG, and it accommodates non-relativistic and relativistic electronic structure calculations. [QCMaquis Webpage](https://scine.ethz.ch/download/qcmaquis).

- [QSpace](https://bitbucket.org/qspace4u/workspace/repositories/) is a tensor library designed as a bottom-up approach for non-abelian symmetries, starting from the defining representation and the respective Lie algebra. A distinctive feature is its versatility in operations across all symmetries, permitting arbitrary combinations.

- [Quantum TEA](https://baltig.infn.it/quantum_tea/quantum_tea) (Quantum Tensor network Emulator Applications) is a set of tensor network packages for quantum simulation, circuit emulation, and machine learning applications. Supplementary libraries extend their capabilities with diverse tensor backends to enable computations on CPUs, GPUs, and TPUs. [Quantum TEA Webpage](https://www.quantumtea.it/).

- [quimb](https://github.com/jcmgray/quimb) is a library for quantum information and many-body calculations, focusing primarily on tensor networks. While its DMRG routine does not currently support features commonly found in other packages, [quimb](https://github.com/jcmgray/quimb) is compatible with complementary libraries like [cotengra](https://github.com/jcmgray/cotengra), [autoray](https://github.com/jcmgray/autoray), and [symmray](https://github.com/jcmgray/symmray) to support efficient tensor network contraction, and various backend array libraries supporting block-sparse, abelian-symmetric, and fermionic representations.

- [Renormalizer](https://github.com/shuaigroup/Renormalizer) is a tensor network package with a focus on electron-phonon quantum dynamics. It implements an original MPO/TTNO construction algorithm that leverages bipartite graph theory to automate and optimize the selection of normal and complementary operators for custom Hamiltonians in the sum-of-products form, a feature later adopted by several other software packages.

- [SeeMPS2](https://github.com/juanjosegarciaripoll/seemps2) is the second iteration of the SElf-Explaining Matrix-Product-State library. It aims to enable rapid prototyping and testing of MPS and DMRG-inspired algorithms.

- [SUNDMRG.jl](https://github.com/MGYamada/SUNDMRG.jl) is a DMRG implementation specializing in a full $\mathrm{SU}(n)$ symmetry.

- [SymMPS](https://www.symmps.eu/) builds upon the Scientific Parallel Algorithms Library ([SciPAL](https://github.com/SciPAL/SciPAL)). It features an original construction scheme for MPO representations of arbitrary $\mathrm{U}(1)$-symmetric operators whenever there is an expression of the local structure in terms of a finite-state machine. [SymMPS Webpage](https://www.symmps.eu/)

- SyTen aims to be a tensor network toolkit with standard MPS, binary TTNS, and infinite PEPS utilities. [SyTen Webpage](https://syten.eu)

- [TeNPy](https://github.com/tenpy/tenpy) (Tensor Network Python) is a library for simulating strongly correlated quantum systems with tensor networks. TeNPy's philosophy is to balance readability and usability for newcomers while providing powerful algorithms for experts.

- [tensor-tools](https://github.com/ClarkResearchGroup/tensor-tools) is a tensor network library that builds upon the Cyclops Tensor Framework ([CTF](https://github.com/cyclops-community/ctf)).

- [TensorTrack](https://github.com/quantumghent/TensorTrack) is a package implementing various elementary algorithms that arise in the context of tensor networks. The package supports generic symmetries, including symmetry groups with multiplicities, which can have either bosonic or fermionic braiding rules.

- [UltraDMRG](https://github.com/QuantumLiquids/UltraDMRG) is a library for performing large-scale calculations using one-dimensional tensor network algorithms. It uses [TensorToolkit](https://github.com/QuantumLiquids/TensorToolkit) for tensor operations and is specifically designed to tackle two-dimensional strongly correlated electron systems.

- [xDMRG++](https://github.com/DavidAce/xDMRGpp) is a package that includes various MPS algorithms for studying one-dimensional quantum spin chains.

    <!-- [doi:]() -->


## Feature Comparisons


### High-Level Overview

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

