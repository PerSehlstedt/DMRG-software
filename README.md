The Software Landscape for the Density Matrix
Renormalization Group
===
Per Sehlstedt, Jan Brandejs, Lars Karlsson and Paolo Bientinesi\
pers at cs.umu.se 

Table of contents
1. [High-level overview](#high-level-overview)
2. [Parallelization strategy](#parallelization-strategy)
3. [Symmetry support](#symmetry-support)
4. [Hamiltonians](#hamiltonians)
5. [Eigensolvers](#eigensolvers)
6. [References](#references)

This list covers the rapidly expanding DMRG software landscape, comprehensively comparing features of many existing packages. We aim to raise awareness of existing packages and guide researchers in finding a suitable package for their needs while helping developers identify opportunities for collaboration, modularity standardization, and optimization. Despite DMRG’s broad applicability across fields like materials science, quantum chemistry, and quantum computing, many independent implementations have been developed, leading to duplicated efforts and limited interoperability. We highlight key aspects, including parallelism strategies for high-performance computing and symmetry-adapted formulations that enhance efficiency. 

We invite the community to contribute, especially in case of missing open-source software.


## High-level overview

High-level aspects of each package. This includes the implementation language and scheme, support for symmetries, and HPC capabilities. Note that support for multiple features does not imply that they can be utilized simultaneously.

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

Table key:

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


## Parallelization strategy

Support for parallelism strategies and mixed-precision optimization techniques.

| ID | Name | HPC | | | Parallelism | | | | | MP |
|---|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| | | SM | DM | GPU | i | ii | iii | iv | v | |
| 1 | ALPS DMRG | ✓ | - | - | ✓ | - | - | - | - | - |
| 2 | ALPS MPS | ✓ | - | - | ✓ | ✓ | - | - | - | - |
| 3 | BAGEL | ✓ | ✓ | - | ✓ | - | - | - | - | - |
| 4 | Block2 | ✓ | ✓ | - | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| 5 | CheMPS2 | ✓ | ✓ | - | - | ✓ | ✓ | - | - | - |
| 6 | ChemTensor | ✓ | - | - | - | ✓ | - | ✓ | - | - |
| 7 | Chen et al. | ✓ | - | S | ✓ | ✓ | - | - | ✓ | - |
| 8 | Cytnx | ✓ | - | S | ✓ | ✓ | ✓ | - | - | - |
| 9 | DMRG-Budapest | ✓ | ✓ | M | ✓ | ✓ | ✓ | ✓ | - | ✓ |
| 10 | DMRG++ | ✓ | - | S | ✓ | ✓ | - | - | - | - |
| 11 | DMRGPy | ✓ | - | - | ✓ | - | - | - | - | - |
| 12 | FOCUS | ✓ | ✓ | M | ✓ | ✓ | ✓ | - | - | - |
| 13 | Hong et al. | - | - | S | ✓ | - | - | - | - | - |
| 14 | ITensor | ✓ | - | - | ✓ | ✓ | - | - | - | - |
| 15 | ITensorMPS.jl | ✓ | - | S | ✓ | ✓ | - | - | - | ✓ |
| 16 | Kylin | ✓ | - | - | - | ✓ | ✓ | - | - | ✓ |
| 17 | MOLMPS | ✓ | ✓ | S | ✓ | ✓ | ✓ | - | - | - |
| 18 | MPSKit.jl | ✓ | - | - | ✓ | ✓ | - | ✓ | - | - |
| 19 | MPToolkit | ✓ | - | - | ✓ | ✓ | - | - | - | - |
| 20 | OSMPS | ✓ | ✓ | - | ✓ | ✓ | - | - | - | - |
| 21 | PyTeNet | ✓ | - | - | ✓ | - | - | - | - | - |
| 22 | QCMaquis | ✓ | - | - | - | ✓ | ✓ | ✓ | - | - |
| 23 | QSpace | ✓ | - | - | ✓ | ✓ | - | - | - | ✓ |
| 24 | Quantum TEA | ✓ | - | S | ✓ | - | - | - | - | ✓ |
| 25 | quimb | ✓ | - | - | ✓ | - | - | - | - | - |
| 26 | Renormalizer | ✓ | - | S | ✓ | - | - | - | - | - |
| 27 | SeeMPS2 | ✓ | - | - | ✓ | - | - | - | - | - |
| 28 | SUNDMRG.jl | ✓ | ✓ | S | ✓ | ✓ | - | - | - | - |
| 29 | SymMPS | ✓ | - | - | ✓ | ✓ | - | - | - | - |
| 30 | SyTen | ✓ | ✓ | S | ✓ | ✓ | - | ✓ | ✓ | - |
| 31 | TeNPy | ✓ | ✓ | - | ✓ | ✓ | - | ✓ | - | - |
| 32 | tensor-tools | ✓ | ✓ | - | ✓ | - | - | - | - | - |
| 33 | TensorTrack | ✓ | - | - | ✓ | - | - | - | - | - |
| 34 | UltraDMRG | ✓ | ✓ | S | ✓ | ✓ | - | ✓ | - | - |
| 35 | xDMRG++ | ✓ | - | - | ✓ | - | - | - | - | - |

Table key:

We closely follow the classification summary and five-level hierarchy of parallelism first introduced by Zhai and Chan [R28] and then further discussed by Tian and Ma [R31]. The following describes the HPC strategies:

* **Parallel strategies (Parallelism):** Indicates support for the following types of parallelism:
    * **Parallelism within matrix operations (i):** The most fine-grained and lowest-level source of parallelism is the data parallelism found primarily within the matrix–matrix and matrix–vector multiplications that underpin the tensor algebra in the DMRG algorithm.
    * **Parallelism over symmetry sectors (ii):** The block-sparse tensor representations in symmetry-adapted DMRG implementations enable parallelism across symmetry sectors. The calculations on different blocks are independent, allowing them to run simultaneously.
    * **Parallelism over normal and complementary operators (iii):** In ab initio DMRG, the left-right decomposition of the Hamiltonian is expressed as a summation of products of normal and complementary operators. These operators are distributed over threads and processors, processing the corresponding calculations concurrently.
    * **Parallelism over a sum of sub-Hamiltonians (iv):** The Hamiltonian is rewritten as a sum of sub-Hamiltonians such that each term can be manipulated independently. This coarse-grained, high-level parallelism is easily expressed in the MPO formalism and adds little communication overhead.
    * **Parallelism over sites (v):** The DMRG sequentially sweeps back and forth along a path. The path can be partitioned into sections that can be processed simultaneously at the expense of extra communication at the section boundaries. This coarse-grained parallelism is especially useful for large systems with many sites.

* **Mixed-precision (MP):** Indicates support for the recently developed mixed-precision optimization technique introduced by Tian et al., where the initial sweeps are accelerated by using reduced floating-point precision. Later sweeps restore full precision by switching to full floating-point precision.

## Symmetry support

Support for various types of symmetries. Note that support for multiple features does not imply that they can be utilized simultaneously.


| ID | Name | U(1) | Z | SU | P | Z2f | Other |
|---|---|---|---|---|---|---|---|
| 1 | ALPS DMRG | ✓ | - | - | - | ✓ | - |
| 2 | ALPS MPS | ✓ | 2 | - | - | ✓ | - |
| 3 | BAGEL | ✓ | - | - | - | ✓ | - |
| 4 | Block2 | ✓ | n | 2 | ✓ | ✓ | - |
| 5 | CheMPS2 | ✓ | - | 2 | ✓ | ✓ | - |
| 6 | ChemTensor | ✓ | - | 2 | - | - | - |
| 7 | Chen et al. | ✓ | - | - | - | ✓ | - |
| 8 | Cytnx | ✓ | n | - | - | ✓ | - |
| 9 | DMRG-Budapest | ✓ | n | n | ✓ | ✓ | - |
| 10 | DMRG++ | ✓ | - | - | - | ✓ | - |
| 11 | DMRGPy | - | - | - | - | ✓ | - |
| 12 | FOCUS | ✓ | - | 2 | - | ✓ | - |
| 13 | Hong et al. | - | - | - | - | - | - |
| 14 | ITensor | ✓ | n | - | - | ✓ | - |
| 15 | ITensorMPS.jl | ✓ | n | - | - | ✓ | - |
| 16 | Kylin | ✓ | - | 2 | ✓ | ✓ | - |
| 17 | MOLMPS | ✓ | - | - | ✓ | ✓ | - |
| 18 | MPSKit.jl | ✓ | n | n | - | ✓ | Anyonic/Categoric |
| 19 | MPToolkit | ✓ | n | 2 | - | ✓ | - |
| 20 | OSMPS | ✓ | 2 | - | - | ✓ | - |
| 21 | PyTeNet | ✓ | - | - | - | - | - |
| 22 | QCMaquis | ✓ | 2 | 2 | ✓ | ✓ | - |
| 23 | QSpace | ✓ | n | n | - | ✓ | SO(n), Sp(2n) |
| 24 | Quantum TEA | ✓ | n | - | - | ✓ | - |
| 25 | quimb | - | - | - | - | ✓ | - |
| 26 | Renormalizer | ✓ | - | - | - | ✓ | - |
| 27 | SeeMPS2 | - | - | - | - | - | - |
| 28 | SUNDMRG.jl | - | - | n | - | - | - |
| 29 | SymMPS | ✓ | - | - | - | ✓ | - |
| 30 | SyTen | ✓ | n | 2 | - | ✓ | - |
| 31 | TeNPy | ✓ | n | - | - | ✓ | - |
| 32 | tensor-tools | ✓ | - | - | - | ✓ | - |
| 33 | TensorTrack | ✓ | n | n | - | ✓ | - |
| 34 | UltraDMRG | ✓ | n | - | - | ✓ | - |
| 35 | xDMRG++ | - | - | - | - | ✓ | - |

Table key:

* **The unitary group** $\mathrm{U}(1)$: Indicates support for the unitary group of degree one, which is the most commonly used symmetry. It typically enforces the conservation of particle numbers (total electrons or separate spin counts) and total spin magnetization.
* **Cyclic groups** ($\mathbb{Z}$): Indicates support for either $\mathbb{Z}_2$ or more general $\mathbb{Z}_n$ symmetries. A common usage for $\mathbb{Z}_2$ is to enforce the spin-flip (parity) symmetry in the transverse-field Ising model, where flipping all spins leaves the Hamiltonian unchanged. The more general $\mathbb{Z}_n$ group is common in models with an $n$-fold rotational or cyclic invariance.
* **Special unitary groups** ($\mathrm{SU}$): Indicates support for either $\mathrm{SU}(2)$ or more generally $\mathrm{SU}(n)$. The $\mathrm{SU}(2)$ group is most common and is often applied to preserve the total spin, often referred to as spin $\mathrm{SU}(2)$. An example of $\mathrm{SU}(n)$ is the channel $\mathrm{SU}(3)$ symmetry considered by Weichselbaum.
* **Point groups** ($\mathrm{P}$): Indicates support for abelian point group symmetries $\mathrm{P} \in \{C_1, C_i, C_2, C_s, C_{2h}, D_2, C_{2v}, D_{2h}\}$ with real-valued character tables. They are often used for molecular systems to enforce spatial symmetries.
* **Fermion parity** ($\mathbb{Z}_2^\mathrm{f}$): Indicates support for the fermion parity, which captures the anti-commuting nature of fermionic degrees of freedom. The parity is a $\mathbb{Z}_2$ quantum number that yields an additional sign when exchanging two fermions (each carrying odd parity).

* *Other:* Indicates support for less common symmetries, such as the special orthogonal group $\mathrm{SO}(n)$, the symplectic group $\mathrm{Sp}(2n)$, and Anyonic symmetries. Anyons are particles with non-trivial exchange statistics that are neither fermions nor bosons.

## Hamiltonians

Support for custom Hamiltonian constructions and the variety of fields for built-in models.

| ID | Name | Construction Custom | Construction Operator | Built-in |
|---|---|---|---|---|
| 1 | ALPS DMRG | &#10003; | &#10003; | Specific |
| 2 | ALPS MPS | - | - | Specific |
| 3 | BAGEL | - | - | Specific |
| 4 | Block2 | &#10003; | &#10003; | Broad |
| 5 | CheMPS2 | - | - | Specific |
| 6 | ChemTensor | &#10003; | &#10003; | Broad |
| 7 | Chen et al. | - | - | Broad |
| 8 | Cytnx | &#10003; | &#10003; | - |
| 9 | DMRG-Budapest | &#10003; | &#10003; | Broad |
| 10 | DMRG++ | &#10003; | - | Specific |
| 11 | DMRGPy | &#10003; | &#10003; | - |
| 12 | FOCUS | - | - | Specific |
| 13 | Hong et al. | - | - | Specific |
| 14 | ITensor | &#10003; | &#10003; | - |
| 15 | ITensorMPS.jl | &#10003; | &#10003; | - |
| 16 | Kylin | - | - | Specific |
| 17 | MOLMPS | - | - | Broad |
| 18 | MPSKit.jl | &#10003; | &#10003; | Specific |
| 19 | MPToolkit | &#10003; | - | Broad |
| 20 | OSMPS | &#10003; | &#10003; | - |
| 21 | PyTeNet | &#10003; | &#10003; | Broad |
| 22 | QCMaquis | - | - | Broad |
| 23 | QSpace | &#10003; | &#10003; | Specific |
| 24 | Quantum TEA | &#10003; | &#10003; | Specific |
| 25 | quimb | &#10003; | &#10003; | Specific |
| 26 | Renormalizer | &#10003; | &#10003; | Broad |
| 27 | SeeMPS2 | &#10003; | &#10003; | - |
| 28 | SUNDMRG.jl | - | - | Specific |
| 29 | SymMPS | &#10003; | - | - |
| 30 | SyTen | &#10003; | - | - |
| 31 | TeNPy | &#10003; | &#10003; | Broad |
| 32 | tensor-tools | &#10003; | &#10003; | - |
| 33 | TensorTrack | &#10003; | &#10003; | Specific |
| 34 | UltraDMRG | &#10003; | &#10003; | - |
| 35 | xDMRG++ | - | - | Specific |


Table key:

* Firstly, we only indicate the presence of some interface for custom Hamiltonian construction and do not distinguish based on their implementation. Moreover, standard operators include spin, spin exchange, bosonic, and fermionic operators for the operator-type construction interfaces. But again, we do not make distinctions based on how many or which operators each package offers.
* Secondly, we acknowledge that classifying the variety of built-in Hamiltonians is somewhat subjective. Currently, the column reflects the developers' views on their package. We provided them with the following examples of what we considered fields: quantum chemistry, condensed matter physics, and nuclear structure.


## Eigensolvers

The eigensolvers used by each package and a comment for bespoke implementations.

| ID | Name | Eigensolver | Comment |
|---|---|---|---|
| 1 | ALPS DMRG | Own | Lanczos  |
| 2 | ALPS MPS | IETL in ALPS | Jacobi–Davidson  |
| 3 | BAGEL | Own | Davidson |
| 4 | Block2 | Own | Davidson  |
| 5 | CheMPS2 | Own | Davidson  |
| 6 | ChemTensor | Own | Lanczos |
| 7 | Chen et al. | Own | Davidson |
| 8 | Cytnx | Own | Lanczos |
| 9 | DMRG-Budapest | Own, ARPACK | Lanczos, Davidson, etc. |
| 10 | DMRG++ | Own | Lanczos |
| 11 | DMRGPy | ITensor (C++/Julia) | - |
| 12 | FOCUS | Own | Davidson |
| 13 | Hong et al. | Own | Lanczos |
| 14 | ITensor | Own | Davidson |
| 15 | ITensorMPS.jl | KrylovKit.jl | Lanczos, Arnoldi |
| 16 | Kylin | Own | Lanczos, Davidson |
| 17 | MOLMPS | Own | Davidson |
| 18 | MPSKit.jl | KrylovKit.jl | Lanczos, Arnoldi |
| 19 | MPToolkit | ARPACK | Lanczos, Davidson, etc. |
| 20 | OSMPS | Own, ARPACK | Lanczos |
| 21 | PyTeNet | Own | Lanczos |
| 22 | QCMaquis | ALPS | Jacobi–Davidson |
| 23 | QSpace | Own | Davidson |
| 24 | Quantum TEA | Own, SciPy | Lanczos |
| 25 | quimb | SciPy, slepc4py | Krylov-Schur, Davidson, etc. |
| 26 | Renormalizer | Own, SciPy | Davidson |
| 27 | SeeMPS2 | SciPy | Lanczos |
| 28 | SUNDMRG.jl | Own | Lanczos |
| 29 | SymMPS | Own | Lanczos |
| 30 | SyTen | Own | Lanczos, Davidson |
| 31 | TeNPy | Own, SciPy | Lanczos |
| 32 | tensor-tools | Own | Davidson |
| 33 | TensorTrack | Own | Krylov-Schur |
| 34 | UltraDMRG | Own | Lanczos |
| 35 | xDMRG++ | PRIMME | Arnoldi, Davidson, etc. |

Table key:

* **Eigensolver:** Indicates if the eigensolver is a bespoke implementation or provided by some external dependency. Some packages include both, often implementing their own sparse solver complemented by an external dense solver.
* **Comment:** Short comment regarding the method used, mainly for packages that implement their own eigensolver, as they can be less flexible regarding method changes.
  

## References

[R28] Zhai, H., & Chan, G. K.-L. (2021). Low communication high performance ab initio density matrix renormalization group algorithms. *The Journal of Chemical Physics*, *154*(22), 224107. [doi:10.1063/5.0050902](https://doi.org/10.1063/5.0050902)

[R31] Tian, Y., Xie, Z., Luo, Z., & Ma, H. (2022). Mixed-Precision Implementation of the Density Matrix Renormalization Group. *Journal of Chemical Theory and Computation*, *18*(12), 7260–7271. [doi:10.1021/acs.jctc.2c00632](https://doi.org/10.1021/acs.jctc.2c00632)

