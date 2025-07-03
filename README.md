# The Software Landscape for the Density Matrix Renormalization Group

Per Sehlstedt, Jan Brandejs, Lars Karlsson and Paolo Bientinesi  
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

<!-- IDEA: Potentially give "Related publications:" a more encompassing name to enable inclusion of webpages and other 'useful' links (?) -->

- [ALPS](https://github.com/ALPSim/ALPS) (Algorithms and Libraries for Physics Simulations) is a software package aiming to provide standardized components for numerical simulations of condensed matter systems. It contains two separate DMRG packages: *ALPS DMRG* and *ALPS MPS*.
[ALPS Webpage](https://alps.comp-phys.org).
    <details><summary><i> Related publications: </i></summary>
    The ALPS project release 1.3: Open-source software for strongly correlated systems, 2007, <a href="http://dx.doi.org/10.1016/j.jmmm.2006.10.304">doi:10.1016/j.jmmm.2006.10.304</a><br>
    The ALPS project release 2.0: open source software for strongly correlated systems, 2011, <a href="http://dx.doi.org/10.1088/1742-5468/2011/05/P05001">doi:10.1088/1742-5468/2011/05/p05001</a><br>
    Matrix product state applications for the ALPS project, 2014, <a href="http://dx.doi.org/10.1016/j.cpc.2014.08.019">doi:10.1016/j.cpc.2014.08.019</a><br>
</details>

- [BAGEL](https://github.com/qsimulate-open/bagel) (Brilliantly Advanced General Electronic-structure Library) is an electronic structure package. In its DMRG implementation, sites are individual molecules that collect multiple orbitals.
[BAGEL Webpage](http://www.nubakery.org).
    <details><summary><i> Related publications: </i></summary>
    Communication: Active space decomposition with multiple sites: Density matrix renormalization group algorithm, 2014, <a href="http://dx.doi.org/10.1063/1.4902991">doi:10.1063/1.4902991</a><br>
    BAGEL: Brilliantly Advanced General Electronic‐structure Library, 2017, <a href="http://dx.doi.org/10.1002/wcms.1331">doi:10.1002/wcms.1331</a><br>
</details>

- [Block2](https://github.com/block-hczhai/block2-preview) aims to provide a comprehensive set of DMRG algorithms for use in electronic structure methods and other applications. It can interface with other quantum chemistry packages to enable hybrid DMRG methods, including [PySCF](https://github.com/pyscf/pyscf), [OpenMOLCAS](https://github.com/Molcas/OpenMolcas), and [Forte](https://github.com/evangelistalab/forte).
    <details><summary><i> Related publications: </i></summary>
    Low communication high performance ab initio density matrix renormalization group algorithms, 2021, <a href="http://dx.doi.org/10.1063/5.0050902">doi:10.1063/5.0050902</a><br>
    Matrix Product States with Large Sites, 2022, <a href="http://dx.doi.org/10.1021/acs.jctc.1c00957">doi:10.1021/acs.jctc.1c00957</a><br>
    A comparison between the one- and two-step spin–orbit coupling approaches based on the ab initio density matrix renormalization group, 2022, <a href="http://dx.doi.org/10.1063/5.0107805">doi:10.1063/5.0107805</a><br>
    Block2: A comprehensive open source framework to develop and apply state-of-the-art DMRG algorithms in electronic structure and beyond, 2023, <a href="http://dx.doi.org/10.1063/5.0180424">doi:10.1063/5.0180424</a><br>
</details>

- [CheMPS2](https://github.com/SebWouters/CheMPS2) is a library containing a DMRG implementation for ab initio quantum chemistry. It can interface with quantum chemistry packages that can handle R(O)HF calculations and molecular orbital matrix elements, and this has been done for [Psi4](https://github.com/psi4/psi4) and [PySCF](https://github.com/pyscf/pyscf).
    <details><summary><i> Related publications: </i></summary>
    CheMPS2: A free open-source spin-adapted implementation of the density matrix renormalization group for ab initio quantum chemistry, 2014, <a href="http://dx.doi.org/10.1016/j.cpc.2014.01.019">doi:10.1016/j.cpc.2014.01.019</a><br>
    Communication: DMRG-SCF study of the singlet, triplet, and quintet states of oxo-Mn(Salen), 2014, <a href="http://dx.doi.org/10.1063/1.4885815">doi:10.1063/1.4885815</a><br>
    The density matrix renormalization group for ab initio quantum chemistry, 2014, <a href="http://dx.doi.org/10.1140/epjd/e2014-50500-1">doi:10.1140/epjd/e2014-50500-1</a><br>
    CheMPS2: Improved DMRG-SCF routine and correlation functions, 2015, <a href="http://dx.doi.org/10.1016/j.cpc.2015.01.007">doi:10.1016/j.cpc.2015.01.007</a><br>
    DMRG-CASPT2 study of the longitudinal static second hyperpolarizability of all-trans polyenes, 2016, <a href="http://dx.doi.org/10.1063/1.4959817">doi:10.1063/1.4959817</a><br>
</details>

- [ChemTensor](https://github.com/qc-tum/chemtensor) is a package for tensor network algorithms centered around chemical systems.
    <details><summary><i> Related publications: </i></summary>
</details>

- Chen et al. presents a hybrid parallel implementation of DMRG with custom subroutines for vector operations on the GPU for improved performance. More recently, they also presented a novel approach to real-space parallel DMRG, building upon the work of Stoudenmire and White.
    <details><summary><i> Related publications: </i></summary>
    Hybrid parallel optimization of density matrix renormalization group method, 2019, <a href="http://dx.doi.org/10.7498/aps.68.20190586">doi:10.7498/aps.68.20190586</a><br>
    Improved hybrid parallel strategy for density matrix renormalization group method*, 2020, <a href="http://dx.doi.org/10.1088/1674-1056/ab8a42">doi:10.1088/1674-1056/ab8a42</a><br>
    Real-space parallel density matrix renormalization group with adaptive boundaries, 2021, <a href="http://dx.doi.org/10.1088/1674-1056/abeb08">doi:10.1088/1674-1056/abeb08</a><br>
</details>

- [Cytnx](https://github.com/Cytnx-dev/Cytnx) is a tensor network library designed for classical and quantum physics simulations. The package has interfaces similar to popular libraries like [NumPy](https://github.com/numpy/numpy), [SciPy](https://github.com/scipy/scipy), and [PyTorch](https://github.com/pytorch/pytorch).
    <details><summary><i> Related publications: </i></summary>
    The Cytnx library for tensor networks, 2025, <a href="http://dx.doi.org/10.21468/SciPostPhysCodeb.53">doi:10.21468/scipostphyscodeb.53</a><br>
</details>

- DMRG-Budapest is a package for general quantum many-body problems. It features various novel in-house optimization techniques to improve performance.
    <details><summary><i> Related publications: </i></summary>
    Massively Parallel Tensor Network State Algorithms on Hybrid CPU-GPU Based Architectures, 2023, <a href="https://arxiv.org/abs/2305.05581">doi:10.48550/ARXIV.2305.05581</a><br>
    Two-dimensional quantum lattice models via mode optimized hybrid CPU-GPU density matrix renormalization group method, 2024, <a href="http://dx.doi.org/10.1103/PhysRevB.109.195148">doi:10.1103/physrevb.109.195148</a><br>
    Parallel Implementation of the Density Matrix Renormalization Group Method Achieving a Quarter petaFLOPS Performance on a Single DGX-H100 GPU Node, 2024, <a href="http://dx.doi.org/10.1021/acs.jctc.4c00903">doi:10.1021/acs.jctc.4c00903</a><br>
    Tensor Network State Algorithms on AI Accelerators, 2024, <a href="http://dx.doi.org/10.1021/acs.jctc.4c00800">doi:10.1021/acs.jctc.4c00800</a><br>
    Cost optimized ab initio tensor network state methods: industrial perspectives, 2024, <a href="https://arxiv.org/abs/2412.04676">doi:10.48550/ARXIV.2412.04676</a><br>
</details>

- [DMRG++](https://github.com/g1257/dmrgpp) implements the DMRG algorithm with an emphasis on generic programming and minimal software dependencies. Additionally, the package has a plug-in, [DMRG++PluginSc](https://code.ornl.gov/gonzalo_3/dmrgppPluginSc), to extend its capabilities to GPUs.
[DMRG++ Webpage](https://g1257.github.io/dmrgPlusPlus/).
    <details><summary><i> Related publications: </i></summary>
    The density matrix renormalization group for strongly correlated electron systems: A generic implementation, 2009, <a href="http://dx.doi.org/10.1016/j.cpc.2009.02.016">doi:10.1016/j.cpc.2009.02.016</a><br>
    Time evolution with the density-matrix renormalization-group algorithm: A generic implementation for strongly correlated electronic systems, 2011, <a href="http://dx.doi.org/10.1103/PhysRevE.84.056706">doi:10.1103/physreve.84.056706</a><br>
    Implementation of the SU(2) Hamiltonian symmetry for the DMRG algorithm, 2012, <a href="http://dx.doi.org/10.1016/j.cpc.2012.04.025">doi:10.1016/j.cpc.2012.04.025</a><br>
    Production of minimally entangled typical thermal states with the Krylov-space approach, 2013, <a href="http://dx.doi.org/10.1103/PhysRevB.87.245130">doi:10.1103/physrevb.87.245130</a><br>
    MiniApp for Density Matrix Renormalization Group Hamiltonian Application Kernel, 2018, <a href="http://dx.doi.org/10.1109/CLUSTER.2018.00075">doi:10.1109/cluster.2018.00075</a><br>
</details>

- [DMRGPy](https://github.com/joselado/dmrgpy) is a library to simulate quasi-one-dimensional spin chains and fermionic systems.  The library relies on ITensor (either the Julia or the C++ version).
    <details><summary><i> Related publications: </i></summary>
</details>

- FOCUS implements an ab initio DMRG algorithm. It supports both non-relativistic and relativistic Hamiltonians, utilizing time-reversal symmetry in the latter case to reduce computational costs
    <details><summary><i> Related publications: </i></summary>
    Expressibility of comb tensor network states (CTNS) for the P-cluster and the FeMo-cofactor of nitrogenase, 2021, <a href="http://dx.doi.org/10.1088/2516-1075/abe192">doi:10.1088/2516-1075/abe192</a><br>
    Time-reversal symmetry adaptation in relativistic density matrix renormalization group algorithm, 2023, <a href="http://dx.doi.org/10.1063/5.0127621">doi:10.1063/5.0127621</a><br>
    Distributed Multi-GPU Ab Initio Density Matrix Renormalization Group Algorithm with Applications to the P-Cluster of Nitrogenase, 2024, <a href="http://dx.doi.org/10.1021/acs.jctc.3c01228">doi:10.1021/acs.jctc.3c01228</a><br>
</details>

- Hong et al. presents a DMRG implementation using various optimization strategies, specifically targeting GPUs with tensor cores.
    <details><summary><i> Related publications: </i></summary>
    High Performance Single-Site Finite DMRG on GPUs, 2022, <a href="https://ieeexplore.ieee.org/document/10104486">ieeexplore.ieee.org/document/10104486</a><br>
</details>

- ITensor is a package for programming tensor network calculations, allowing users to focus on the connectivity of a tensor network without manually tracking indices. ITensor was initially implemented in C++ but later fully ported to Julia, with most new features first being developed there. The C++ version, [ITensor](https://github.com/ITensor/ITensor), includes DMRG in the main library, while the Julia version provides DMRG through the [ITensorMPS.jl](https://github.com/ITensor/ITensorMPS.jl) extension of [ITensors.jl](https://github.com/ITensor/ITensors.jl).
[ITensor Webpage](https://itensor.org/).
    <details><summary><i> Related publications: </i></summary>
    The ITensor Software Library for Tensor Network Calculations, 2022, <a href="http://dx.doi.org/10.21468/SciPostPhysCodeb.4">doi:10.21468/scipostphyscodeb.4</a><br>
</details>

- Kylin is an ab initio quantum chemistry software package for estimating the electronic structures of molecular systems. It is specially designed for calculations with large active spaces.
[Kylin Webpage](https://kylin-qc.com/).
    <details><summary><i> Related publications: </i></summary>
    Kylin 1.0: An ab‐initio density matrix renormalization group quantum chemistry program, 2023, <a href="http://dx.doi.org/10.1002/jcc.27085">doi:10.1002/jcc.27085</a><br>
</details>

- MOLMPS is a parallel implementation of DMRG for quantum chemistry. The parallel scheme is based on an in-house MPI global memory library and supports various hybrid electronic structure methods.
    <details><summary><i> Related publications: </i></summary>
    Massively parallel quantum chemical density matrix renormalization group method, 2020, <a href="http://dx.doi.org/10.1002/jcc.26476">doi:10.1002/jcc.26476</a><br>
</details>

- [MPSKit.jl](https://github.com/QuantumKitHub/MPSKit.jl) contains tensor network algorithms for one-dimensional quantum and two-dimensional statistical mechanics problems. It mainly builds upon [TensorKit.jl](https://github.com/Jutho/TensorKit.jl), which provides functionality for generic symmetries, and its capabilities can be extended with packages like [SUNRepresentations.jl](https://github.com/QuantumKitHub/SUNRepresentations.jl) and [MPSKitModels.jl](https://github.com/QuantumKitHub/MPSKitModels.jl).
[QuantumGroup@Ugent Webpage](https://quantumghent.github.io/software/).
    <details><summary><i> Related publications: </i></summary>
</details>

- [MPToolkit](https://github.com/mptoolkit/mptoolkit) (Matrix Product Toolkit) is a package for creating and manipulating MPS. It was initially envisioned as a "next-generation" DMRG code that integrates non-abelian symmetries and emphasizes a flexible, general approach to constructing Hamiltonian operators and measuring observables.
    <details><summary><i> Related publications: </i></summary>
    The non-Abelian density matrix renormalization group algorithm, 2002, <a href="http://dx.doi.org/10.1209/epl/i2002-00393-0">doi:10.1209/epl/i2002-00393-0</a><br>
</details>

- [OSMPS](https://sourceforge.net/projects/openmps/) (Open Source MPS) is a collection of tensor network algorithms for simulating entangled one-dimensional many-body quantum systems. The initial focus was to offer a broad set of methods for quantum simulators based on atomic, molecular, and optical physics architectures.
    <details><summary><i> Related publications: </i></summary>
    Out-of-equilibrium dynamics with matrix product states, 2012, <a href="http://dx.doi.org/10.1088/1367-2630/14/12/125015">doi:10.1088/1367-2630/14/12/125015</a><br>
    Open source Matrix Product States: Opening ways to simulate entangled many-body quantum systems in one dimension, 2018, <a href="http://dx.doi.org/10.1016/j.cpc.2017.12.015">doi:10.1016/j.cpc.2017.12.015</a><br>
    Open source matrix product states: exact diagonalization and other entanglement-accurate methods revisited in quantum systems, 2018, <a href="http://dx.doi.org/10.1088/1751-8121/aae4d1">doi:10.1088/1751-8121/aae4d1</a><br>
    One-dimensional many-body entangled open quantum systems with tensor network methods, 2018, <a href="http://dx.doi.org/10.1088/2058-9565/aae724">doi:10.1088/2058-9565/aae724</a><br>
</details>

- [PyTeNet](https://github.com/cmendl/pytenet) implements quantum tensor network operations and simulations structured around MPS and MPO classes. It acts as a facilitator of algorithmic experimentation. 
    <details><summary><i> Related publications: </i></summary>
    PyTeNet: A concise Python implementation of quantum tensor network algorithms, 2018, <a href="http://dx.doi.org/10.21105/joss.00948">doi:10.21105/joss.00948</a><br>
</details>

- [pyTTN](https://gitlab.npl.co.uk/qsm/pyttn) is a package for working with generic TTNS to efficiently compute dynamical properties of quantum systems. It also provides functionality for merging many physical modes into a single site, which can be useful when handling weakly correlated subsystems, where there is a strong correlation between the degrees of freedom in each subsystem. 
    <details><summary><i> Related publications: </i></summary>
    pyTTN: An Open Source Toolbox for Open and Closed System Quantum Dynamics Simulations Using Tree Tensor Network, 2025, <a href="https://arxiv.org/abs/2503.15460">doi:10.48550/ARXIV.2503.15460</a><br>
</details>

- [QCMaquis](https://github.com/qcscine/qcmaquis) is a SCINE module that builds upon the *ALPS MPS* code and implements various DMRG-based algorithms. Key features include vibrational, time-dependent, and nuclear-electron DMRG, and it accommodates non-relativistic and relativistic electronic structure calculations.
[QCMaquis Webpage](https://scine.ethz.ch/download/qcmaquis).
    <details><summary><i> Related publications: </i></summary>
    An efficient matrix product operator representation of the quantum chemical Hamiltonian, 2015, <a href="http://dx.doi.org/10.1063/1.4939000">doi:10.1063/1.4939000</a><br>
    New Approaches for ab initio Calculations of Molecules with Strong Electron Correlation, 2016, <a href="http://dx.doi.org/10.2533/chimia.2016.244">doi:10.2533/chimia.2016.244</a><br>
    Vibrational Density Matrix Renormalization Group, 2017, <a href="http://dx.doi.org/10.1021/acs.jctc.7b00329">doi:10.1021/acs.jctc.7b00329</a><br>
    Efficient Relativistic Density-Matrix Renormalization Group Implementation in a Matrix-Product Formulation, 2018, <a href="http://dx.doi.org/10.1021/acs.jctc.7b01065">doi:10.1021/acs.jctc.7b01065</a><br>
    Optimization of highly excited matrix product states with an application to vibrational spectroscopy, 2019, <a href="http://dx.doi.org/10.1063/1.5068747">doi:10.1063/1.5068747</a><br>
    Large-Scale Quantum Dynamics with Matrix Product States, 2019, <a href="http://dx.doi.org/10.1021/acs.jctc.9b00301">doi:10.1021/acs.jctc.9b00301</a><br>
    Nuclear-electronic all-particle density matrix renormalization group, 2020, <a href="http://dx.doi.org/10.1063/5.0007166">doi:10.1063/5.0007166</a><br>
    Excited-State DMRG Made Simple with FEAST, 2021, <a href="http://dx.doi.org/10.1021/acs.jctc.1c00984">doi:10.1021/acs.jctc.1c00984</a><br>
    Quantum Proton Effects from Density Matrix Renormalization Group Calculations, 2022, <a href="http://dx.doi.org/10.1021/acs.jctc.1c00913">doi:10.1021/acs.jctc.1c00913</a><br>
</details>

- [QSpace](https://bitbucket.org/qspace4u/workspace/repositories/) is a tensor library designed as a bottom-up approach for non-abelian symmetries, starting from the defining representation and the respective Lie algebra. A distinctive feature is its versatility in operations across all symmetries, permitting arbitrary combinations.
    <details><summary><i> Related publications: </i></summary>
    Non-abelian symmetries in tensor networks: A quantum symmetry space approach, 2012, <a href="http://dx.doi.org/10.1016/j.aop.2012.07.009">doi:10.1016/j.aop.2012.07.009</a><br>
    X-symbols for non-Abelian symmetries in tensor networks, 2020, <a href="http://dx.doi.org/10.1103/PhysRevResearch.2.023385">doi:10.1103/physrevresearch.2.023385</a><br>
    QSpace - An open-source tensor library for Abelian and non-Abelian symmetries, 2024, <a href="http://dx.doi.org/10.21468/SciPostPhysCodeb.40">doi:10.21468/scipostphyscodeb.40</a><br>
</details>

- [Quantum TEA](https://baltig.infn.it/quantum_tea/quantum_tea) (Quantum Tensor network Emulator Applications) is a set of tensor network packages for quantum simulation, circuit emulation, and machine learning applications. Supplementary libraries extend their capabilities with diverse tensor backends to enable computations on CPUs, GPUs, and TPUs.
[Quantum TEA Webpage](https://www.quantumtea.it/).
    <details><summary><i> Related publications: </i></summary>
    Benchmarking Quantum Red TEA on CPUs, GPUs, and TPUs, 2024, <a href="https://arxiv.org/abs/2409.03818">doi:10.48550/ARXIV.2409.03818</a><br>
</details>

- [quimb](https://github.com/jcmgray/quimb) is a library for quantum information and many-body calculations, focusing primarily on tensor networks. While its DMRG routine does not currently support features commonly found in other packages, [quimb](https://github.com/jcmgray/quimb) is compatible with complementary libraries like [cotengra](https://github.com/jcmgray/cotengra), [autoray](https://github.com/jcmgray/autoray), and [symmray](https://github.com/jcmgray/symmray) to support efficient tensor network contraction, and various backend array libraries supporting block-sparse, abelian-symmetric, and fermionic representations.
    <details><summary><i> Related publications: </i></summary>
    quimb: A python package for quantum information and many-body calculations, 2018, <a href="http://dx.doi.org/10.21105/joss.00819">doi:10.21105/joss.00819</a><br>
</details>

- [Renormalizer](https://github.com/shuaigroup/Renormalizer) is a tensor network package with a focus on electron-phonon quantum dynamics. It implements an original MPO/TTNO construction algorithm that leverages bipartite graph theory to automate and optimize the selection of normal and complementary operators for custom Hamiltonians in the sum-of-products form, a feature later adopted by several other software packages.
    <details><summary><i> Related publications: </i></summary>
    Time-Dependent Density Matrix Renormalization Group Algorithms for Nearly Exact Absorption and Fluorescence Spectra of Molecular Aggregates at Both Zero and Finite Temperature, 2018, <a href="http://dx.doi.org/10.1021/acs.jctc.8b00628">doi:10.1021/acs.jctc.8b00628</a><br>
    Numerical assessment for accuracy and GPU acceleration of TD-DMRG time evolution schemes, 2020, <a href="http://dx.doi.org/10.1063/1.5135363">doi:10.1063/1.5135363</a><br>
    Finite Temperature Dynamical Density Matrix Renormalization Group for Spectroscopy in Frequency Domain, 2020, <a href="http://dx.doi.org/10.1021/acs.jpclett.0c00905">doi:10.1021/acs.jpclett.0c00905</a><br>
    A general automatic method for optimal construction of matrix product operators using bipartite graph theory, 2020, <a href="http://dx.doi.org/10.1063/5.0018149">doi:10.1063/5.0018149</a><br>
    Time‐dependent density matrix renormalization group method for quantum dynamics in complex systems, 2022, <a href="http://dx.doi.org/10.1002/wcms.1614">doi:10.1002/wcms.1614</a><br>
    Optimal tree tensor network operators for tensor network simulations: Applications to open quantum systems, 2024, <a href="http://dx.doi.org/10.1063/5.0218773">doi:10.1063/5.0218773</a><br>
</details>

- [SeeMPS2](https://github.com/juanjosegarciaripoll/seemps2) is the second iteration of the SElf-Explaining Matrix-Product-State library. It aims to enable rapid prototyping and testing of MPS and DMRG-inspired algorithms.
    <details><summary><i> Related publications: </i></summary>
    Quantum-inspired algorithms for multivariate analysis: from interpolation to partial differential equations, 2021, <a href="http://dx.doi.org/10.22331/q-2021-04-15-431">doi:10.22331/q-2021-04-15-431</a><br>
    Global optimization of MPS in quantum-inspired numerical analysis, 2023, <a href="https://arxiv.org/abs/2303.09430">doi:10.48550/ARXIV.2303.09430</a><br>
</details>

- [SUNDMRG.jl](https://github.com/MGYamada/SUNDMRG.jl) is a DMRG implementation specializing in a full $\mathrm{SU}(n)$ symmetry.
    <details><summary><i> Related publications: </i></summary>
</details>

- [SymMPS](https://www.symmps.eu/) builds upon the Scientific Parallel Algorithms Library ([SciPAL](https://github.com/SciPAL/SciPAL)). It features an original construction scheme for MPO representations of arbitrary $\mathrm{U}(1)$-symmetric operators whenever there is an expression of the local structure in terms of a finite-state machine.
[SymMPS Webpage](https://www.symmps.eu/)
    <details><summary><i> Related publications: </i></summary>
    Automated construction of $U(1)$-invariant matrix-product operators from  graph representations, 2017, <a href="http://dx.doi.org/10.21468/SciPostPhys.3.5.035">doi:10.21468/scipostphys.3.5.035</a><br>
</details>

- SyTen aims to be a tensor network toolkit with standard MPS, binary TTNS, and infinite PEPS utilities.
[SyTen Webpage](https://syten.eu)
    <details><summary><i> Related publications: </i></summary>
    Symmetry-protected tensor networks, 2017, <a href="https://edoc.ub.uni-muenchen.de/id/eprint/21348">doi:10.5282/EDOC.21348</a><br>
</details>

- [TeNPy](https://github.com/tenpy/tenpy) (Tensor Network Python) is a library for simulating strongly correlated quantum systems with tensor networks. TeNPy's philosophy is to balance readability and usability for newcomers while providing powerful algorithms for experts.
    <details><summary><i> Related publications: </i></summary>
    Efficient numerical simulations with Tensor Networks: Tensor Network  Python (TeNPy), 2018, <a href="http://dx.doi.org/10.21468/SciPostPhysLectNotes.5">doi:10.21468/scipostphyslectnotes.5</a><br>
    Tensor network Python (TeNPy) version 1, 2024, <a href="http://dx.doi.org/10.21468/SciPostPhysCodeb.41">doi:10.21468/scipostphyscodeb.41</a><br>
</details>

- [tensor-tools](https://github.com/ClarkResearchGroup/tensor-tools) is a tensor network library that builds upon the Cyclops Tensor Framework ([CTF](https://github.com/cyclops-community/ctf)).
    <details><summary><i> Related publications: </i></summary>
    Distributed-Memory DMRG via Sparse and Dense Parallel Tensor Contractions, 2020, <a href="https://dl.acm.org/doi/10.5555/3433701.3433732">doi:10.1109/SC41405.2020.00028</a><br>
</details>

- [TensorTrack](https://github.com/quantumghent/TensorTrack) is a package implementing various elementary algorithms that arise in the context of tensor networks. The package supports generic symmetries, including symmetry groups with multiplicities, which can have either bosonic or fermionic braiding rules.
    <details><summary><i> Related publications: </i></summary>
</details>

- [UltraDMRG](https://github.com/QuantumLiquids/UltraDMRG) is a library for performing large-scale calculations using one-dimensional tensor network algorithms. It uses [TensorToolkit](https://github.com/QuantumLiquids/TensorToolkit) for tensor operations and is specifically designed to tackle two-dimensional strongly correlated electron systems.
    <details><summary><i> Related publications: </i></summary>
</details>

- [xDMRG++](https://github.com/DavidAce/xDMRGpp) is a package that includes various MPS algorithms for studying one-dimensional quantum spin chains.
    <details><summary><i> Related publications: </i></summary>
</details>

- [YASTN](https://github.com/yastn/yastn) (Yet another symmetric tensor networks) is a package for differentiable linear algebra with block-sparse tensors, supporting abelian symmetries. The package mainly focuses on PEPS, but also supports a range of MPS algorithms.
    <details><summary><i> Related publications: </i></summary>
    YASTN: Yet another symmetric tensor networks; A Python library for Abelian symmetric tensor network calculations, 2025, <a href="http://dx.doi.org/10.21468/SciPostPhysCodeb.52">doi:10.21468/scipostphyscodeb.52</a><br>
</details>

<!-- TODO: Somehow make separate (sub)section/list for the packages that are not compared. -->

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
| [pyTTN](https://gitlab.npl.co.uk/qsm/pyttn) | C++, Python<sup>i</sup> | ✓ | 2<sup>nd</sup> | - | - | ✓ | - | - |
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
| [YASTN](https://github.com/yastn/yastn) | Python | ✓ | 2<sup>nd</sup> | ✓ | - | ✓ | - | S |

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
| pyTTN | ✓ | - | - | ✓ | - | - | ✓ | - | - |
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
| YASTN | ✓ | - | S | ✓ | - | - | - | - | - |

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
| pyTTN | - | - | - | - | ✓ | - |
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
| YASTN | ✓ | n | - | - | ✓ | - |

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
| pyTTN | ✓ | ✓ | Broad |
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
| YASTN | ✓ | ✓ | - |


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
| pyTTN | Own | Arnoldi |
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
| YASTN | Own | Lanczos |

Table key:

* **Eigensolver:** Indicates if the eigensolver is a bespoke implementation or provided by some external dependency. Some packages include both, often implementing their own sparse solver complemented by an external dense solver.
* **Comment:** Short comment regarding the method used, mainly for packages that implement their own eigensolver, as they can be less flexible regarding method changes.
  

## References

[1] Zhai, H., & Chan, G. K.-L. (2021). Low communication high performance ab initio density matrix renormalization group algorithms. *The Journal of Chemical Physics*, *154*(22), 224107. [doi:10.1063/5.0050902](https://doi.org/10.1063/5.0050902)

[2] Tian, Y., Xie, Z., Luo, Z., & Ma, H. (2022). Mixed-Precision Implementation of the Density Matrix Renormalization Group. *Journal of Chemical Theory and Computation*, *18*(12), 7260–7271. [doi:10.1021/acs.jctc.2c00632](https://doi.org/10.1021/acs.jctc.2c00632)

