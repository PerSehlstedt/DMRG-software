The Software Landscape for the Density Matrix
Renormalization Group
===
Per Sehlstedt, Jan Brandejs, Lars Karlsson and Paolo Bientinesi\
pers at cs.umu.se 


Table of contents
1. [High-level Overview](#high-level-overview)
2. [Parallelism and Mixed-Precision](#parallelism-and-mixed-precision)
3. [Symmetries](#symmetries)
4. [Hamiltonians](#hamiltonians)
5. [Eigensolvers](#eigensolvers)
6. [References](#references)

This list covers the rapidly expanding DMRG software landscape, comprehensively comparing features of many existing packages. We aim to raise awareness of existing packages and guide researchers in finding a suitable package for their needs while helping developers identify opportunities for collaboration, modularity standardization, and optimization. Despite DMRG’s broad applicability across fields like materials science, quantum chemistry, and quantum computing, many independent implementations have been developed, leading to duplicated efforts and limited interoperability. We highlight key aspects, including parallelism strategies for high-performance computing and symmetry-adapted formulations that enhance efficiency. 

We invite the community to contribute in case of missing open source software.

Please consider citing the original paper [arXiv:2506.12629](https://arxiv.org/abs/2506.12629).


## High-level Overview

High-level aspects of each package. This includes the implementation language and scheme, support for symmetries, and HPC capabilities. Note that support for multiple features does not imply that they can be utilized simultaneously.

| Name | Language | OSS | Gen. | Sym. A | Sym. NA | HPC SM | HPC DM | HPC GPU |
|---|---|---|---|---|---|---|---|---|
| [ALPS DMRG](https://github.com/ALPSim/ALPS) | C++, Pythonⁱ | ✓ | 1ˢᵗ | ✓ | - | ✓ | - | - |
| [ALPS MPS](https://github.com/ALPSim/ALPS) | C++, Pythonⁱ | ✓ | 2ⁿᵈ | ✓ | - | ✓ | - | - |
| [BAGEL](https://github.com/qsimulate-open/bagel) | C++ | ✓ | 1ˢᵗ | ✓ | - | ✓ | ✓ | - |
| [Block2](https://github.com/block-hczhai/block2-preview) | C++, Pythonⁱ | ✓ | 2ⁿᵈ‡ | ✓ | ✓ | ✓ | ✓ | - |
| [CheMPS2](https://github.com/SebWouters/CheMPS2) | C++, Pythonⁱ | ✓ | 1ˢᵗ | ✓ | ✓ | ✓ | ✓ | - |
| [ChemTensor](https://github.com/qc-tum/chemtensor) | C, Pythonⁱ | ✓ | 2ⁿᵈ† | ✓ | ✓ | ✓ | - | - |
| Chen et al. | C++ | - | 1ˢᵗ | ✓ | - | ✓ | - | S |
| [Cytnx](https://github.com/Cytnx-dev/Cytnx) | C++, Pythonⁱ | ✓ | 2ⁿᵈ† | ✓ | - | ✓ | - | S |
| DMRG-Budapest | C++, MATLABⁱ | - | 2ⁿᵈ‡ | ✓ | ✓ | ✓ | ✓ | M |
| [DMRG++](https://github.com/g1257/dmrgpp) | C++ | ✓ | 1ˢᵗ | ✓ | - | ✓ | - | S |
| [DMRGPy](https://github.com/joselado/dmrgpy) | Python | ✓ | 2ⁿᵈ | - | - | ✓ | - | - |
| FOCUS | C++ | - | 1ˢᵗ | ✓ | ✓ | ✓ | ✓ | M |
| Hong et al. | C++ | - | 2ⁿᵈ | - | - | - | - | S |
| [ITensor](https://github.com/ITensor/ITensor) | C++ | ✓ | 2ⁿᵈ | ✓ | - | ✓ | - | - |
| [ITensorMPS.jl](https://github.com/ITensor/ITensorMPS.jl) | Julia | ✓ | 2ⁿᵈ | ✓ | - | ✓ | - | S |
| Kylin | C++ | - | 2ⁿᵈ | ✓ | ✓ | ✓ | - | - |
| MOLMPS | C++ | - | 1ˢᵗ | ✓ | - | ✓ | ✓ | S |
| [MPSKit.jl](https://github.com/QuantumKitHub/MPSKit.jl) | Julia | ✓ | 2ⁿᵈ | ✓ | ✓ | ✓ | - | - |
| [MPToolkit](https://github.com/mptoolkit/mptoolkit) | C++ | ✓ | 2ⁿᵈ | ✓ | ✓ | ✓ | - | - |
| [OSMPS](https://sourceforge.net/projects/openmps/) | Fortran, Pythonⁱ | ✓ | 2ⁿᵈ | ✓ | - | ✓ | ✓ | - |
| [PyTeNet](https://github.com/cmendl/pytenet) | Python | ✓ | 2ⁿᵈ | ✓ | - | ✓ | - | - |
| [QCMaquis](https://github.com/qcscine/qcmaquis) | C++ | ✓ | 2ⁿᵈ | ✓ | ✓ | ✓ | - | - |
| [QSpace](https://bitbucket.org/qspace4u/workspace/repositories/) | C++, MATLABⁱ | ✓ | 2ⁿᵈ‡ | ✓ | ✓ | ✓ | - | - |
| [Quantum TEA](https://baltig.infn.it/quantum_tea/quantum_tea) | Fortran, Pythonⁱ | ✓ | 2ⁿᵈ† | ✓ | - | ✓ | - | S |
| [quimb](https://github.com/jcmgray/quimb) | Python | ✓ | 2ⁿᵈ | - | - | ✓ | - | - |
| [Renormalizer](https://github.com/shuaigroup/Renormalizer) | Python | ✓ | 2ⁿᵈ† | ✓ | - | ✓ | - | S |
| [SeeMPS2](https://github.com/juanjosegarciaripoll/seemps2) | Python | ✓ | 2ⁿᵈ | - | - | ✓ | - | - |
| [SUNDMRG.jl](https://github.com/MGYamada/SUNDMRG.jl) | Julia | ✓ | 1ˢᵗ | - | ✓ | ✓ | ✓ | S |
| [SymMPS](https://www.symmps.eu/) | C++ | ✓ | 2ⁿᵈ | ✓ | - | ✓ | - | - |
| SyTen | C++, Pythonⁱ | - | 2ⁿᵈ | ✓ | ✓ | ✓ | ✓ | S |
| [TeNPy](https://github.com/tenpy/tenpy) | Python | ✓ | 2ⁿᵈ | ✓ | - | ✓ | ✓ | - |
| [tensor-tools](https://github.com/ClarkResearchGroup/tensor-tools) | C++ | ✓ | 2ⁿᵈ | ✓ | - | ✓ | ✓ | - |
| [TensorTrack](https://github.com/quantumghent/TensorTrack) | MATLAB | ✓ | 2ⁿᵈ | ✓ | ✓ | ✓ | - | - |
| [UltraDMRG](https://github.com/QuantumLiquids/UltraDMRG) | C++ | ✓ | 2ⁿᵈ | ✓ | - | ✓ | ✓ | S |
| [xDMRG++](https://github.com/DavidAce/xDMRGpp) | C++ | ✓ | 2ⁿᵈ | - | - | ✓ | - | - |

Table key:

* **Name:** The official name of the package, if available; otherwise, the authors of an associated publication. Names link to source code if the package is open source.

* **Language:** The programming languages used for implementation and interfaces. Languages marked with <sup>i</sup>-superscripts are those mainly used as interfaces.

<!-- Could potentially remove this column if names are hyperlinked to source code or change it to show what licence is used? -->
* **Open Source Software (OSS):** Indicates whether the package is open source and available for download.

* **Implementation Formalism (Gen.):** Specifies which view the DMRG implementation is based on: \
  1<sup>st</sup> for the traditional RG perspective using renormalized operators and \
  2<sup>nd</sup> for the tensor network perspective using MPO/MPS. \
  <sup>‡</sup>-superscripts mark those who support both views, and \
  <sup>†</sup>-superscripts mark those who support the usage of TTNO/TTNS.

* **Symmetry Support (Sym.):** Indicates whether the package is symmetry-adapted to support abelian (A) and/or non-abelian (NA) symmetries or not.

* **High-Performance Computing (HPC):** Indicates support for HPC platforms, categorized as shared-memory parallelism (SM), distributed-memory parallelism (DM), and single- (S) or multi- (M) GPU acceleration (GPU).


## Parallelism and Mixed-Precision

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

We closely follow the classification summary and five-level hierarchy of parallelism first introduced by Zhai and Chan [R28] and then further discussed by Tian and Ma [R31]. The following describes the HPC strategies:

* **Parallel strategies (Parallelism):** Indicates support for the following types of parallelism:
    * **Parallelism within matrix operations (i):** The most fine-grained and lowest-level source of parallelism is the data parallelism found primarily within the matrix–matrix and matrix–vector multiplications that underpin the tensor algebra in the DMRG algorithm.
    * **Parallelism over symmetry sectors (ii):** The block-sparse tensor representations in symmetry-adapted DMRG implementations enable parallelism across symmetry sectors. The calculations on different blocks are independent, allowing them to run simultaneously.
    * **Parallelism over normal and complementary operators (iii):** In ab initio DMRG, the left-right decomposition of the Hamiltonian is expressed as a summation of products of normal and complementary operators. These operators are distributed over threads and processors, processing the corresponding calculations concurrently.
    * **Parallelism over a sum of sub-Hamiltonians (iv):** The Hamiltonian is rewritten as a sum of sub-Hamiltonians such that each term can be manipulated independently. This coarse-grained, high-level parallelism is easily expressed in the MPO formalism and adds little communication overhead.
    * **Parallelism over sites (v):** The DMRG sequentially sweeps back and forth along a path. The path can be partitioned into sections that can be processed simultaneously at the expense of extra communication at the section boundaries. This coarse-grained parallelism is especially useful for large systems with many sites.

* **Mixed-precision (MP):** Indicates support for the recently developed mixed-precision optimization technique introduced by Tian et al., where the initial sweeps are accelerated by using reduced floating-point precision. Later sweeps restore full precision by switching to full floating-point precision.

## Symmetries

Support for various types of symmetries. Note that support for multiple features does not imply that they can be utilized simultaneously.

| Name | U(1) | Z | SU | P | Z2f | Other |
|---|---|---|---|---|---|---|
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

* *Other:* Indicates support for less common symmetries, such as the special orthogonal group $\mathrm{SO}(n)$, the symplectic group $\mathrm{Sp}(2n)$, and Anyonic symmetries. Anyons are particles with non-trivial exchange statistics that are neither fermions nor bosons.

## Hamiltonians

Support for custom Hamiltonian constructions and the variety of fields for built-in models.

| Name | Construction Custom | Construction Operator | Built-in |
|---|---|---|---|
| ALPS DMRG | &#10003; | &#10003; | Specific |
| ALPS MPS | - | - | Specific |
| BAGEL | - | - | Specific |
| Block2 | &#10003; | &#10003; | Broad |
| CheMPS2 | - | - | Specific |
| ChemTensor | &#10003; | &#10003; | Broad |
| Chen et al. | - | - | Broad |
| Cytnx | &#10003; | &#10003; | - |
| DMRG-Budapest | &#10003; | &#10003; | Broad |
| DMRG++ | &#10003; | - | Specific |
| DMRGPy | &#10003; | &#10003; | - |
| FOCUS | - | - | Specific |
| Hong et al. | - | - | Specific |
| ITensor | &#10003; | &#10003; | - |
| ITensorMPS.jl | &#10003; | &#10003; | - |
| Kylin | - | - | Specific |
| MOLMPS | - | - | Broad |
| MPSKit.jl | &#10003; | &#10003; | Specific |
| MPToolkit | &#10003; | - | Broad |
| OSMPS | &#10003; | &#10003; | - |
| PyTeNet | &#10003; | &#10003; | Broad |
| QCMaquis | - | - | Broad |
| QSpace | &#10003; | &#10003; | Specific |
| Quantum TEA | &#10003; | &#10003; | Specific |
| quimb | &#10003; | &#10003; | Specific |
| Renormalizer | &#10003; | &#10003; | Broad |
| SeeMPS2 | &#10003; | &#10003; | - |
| SUNDMRG.jl | - | - | Specific |
| SymMPS | &#10003; | - | - |
| SyTen | &#10003; | - | - |
| TeNPy | &#10003; | &#10003; | Broad |
| tensor-tools | &#10003; | &#10003; | - |
| TensorTrack | &#10003; | &#10003; | Specific |
| UltraDMRG | &#10003; | &#10003; | - |
| xDMRG++ | - | - | Specific |


Table key:

* Firstly, we only indicate the presence of some interface for custom Hamiltonian construction and do not distinguish based on their implementation. Moreover, standard operators include spin, spin exchange, bosonic, and fermionic operators for the operator-type construction interfaces. But again, we do not make distinctions based on how many or which operators each package offers.
* Secondly, we acknowledge that classifying the variety of built-in Hamiltonians is somewhat subjective. Currently, the column reflects the developers' views on their package. We provided them with the following examples of what we considered fields: quantum chemistry, condensed matter physics, and nuclear structure.


## Eigensolvers

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

[R28] Zhai, H., & Chan, G. K.-L. (2021). Low communication high performance ab initio density matrix renormalization group algorithms. *The Journal of Chemical Physics*, *154*(22), 224107. [doi:10.1063/5.0050902](https://doi.org/10.1063/5.0050902)

[R31] Tian, Y., Xie, Z., Luo, Z., & Ma, H. (2022). Mixed-Precision Implementation of the Density Matrix Renormalization Group. *Journal of Chemical Theory and Computation*, *18*(12), 7260–7271. [doi:10.1021/acs.jctc.2c00632](https://doi.org/10.1021/acs.jctc.2c00632)

