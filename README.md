# ReLibQC Catalog: Reusable Libraries for Quantum Chemistry

This is a community-maintained catalog of open-source libraries that can be
reused in quantum chemistry programs. We want it to be easier to find existing
components, so that people build on shared, well-tested libraries instead of
writing the same functionality again in every code.

Each entry gives the project name, its upstream repository, its license, and a
short description. Entries marked **[ESL]** are also listed in the
software catalog of the
[CECAM Electronic Structure Library](https://esl.cecam.org/en/software/index.html).

At the end there is a list of open-source quantum chemistry programs that use
some of these libraries.

Contributions are welcome. See [Contributing](#contributing).

### A note on licenses

The license decides which libraries a given program can use. For example, a
GPL-licensed library cannot be linked into a program that is distributed under
a permissive or proprietary license. Licenses are given as
[SPDX identifiers](https://spdx.org/licenses/). They were taken from each
project's license files and repository metadata in September 2026.

- `-or-later` is written only where the project states it explicitly.
- A bare `GPL-3.0` or `LGPL-3.0` means the version-upgrade clause was not
  checked.
- Some projects license different parts of the code differently.
- Licenses can change between releases.

Always check the upstream license of the version you use.

## Contents

- [ReLibQC Catalog: Reusable Libraries for Quantum Chemistry](#relibqc-catalog-reusable-libraries-for-quantum-chemistry)
    - [A note on licenses](#a-note-on-licenses)
  - [Contents](#contents)
  - [Molecular integrals](#molecular-integrals)
  - [Basis sets](#basis-sets)
  - [Numerical quadrature and exchange-correlation integration](#numerical-quadrature-and-exchange-correlation-integration)
  - [Density functionals and exchange-correlation](#density-functionals-and-exchange-correlation)
  - [Dispersion corrections and semiempirical methods](#dispersion-corrections-and-semiempirical-methods)
  - [Electrostatics, multipoles, and fast multipole methods](#electrostatics-multipoles-and-fast-multipole-methods)
  - [Solvation, QM/MM, and embedding potentials](#solvation-qmmm-and-embedding-potentials)
  - [Angular momentum algebra and special functions](#angular-momentum-algebra-and-special-functions)
  - [Tensor libraries](#tensor-libraries)
  - [Tensor networks and DMRG](#tensor-networks-and-dmrg)
  - [Second quantization and equation generation](#second-quantization-and-equation-generation)
  - [Coupled cluster, configuration interaction, and perturbation theory](#coupled-cluster-configuration-interaction-and-perturbation-theory)
  - [Quantum Monte Carlo](#quantum-monte-carlo)
  - [Green's functions, GW, RPA, and DMFT](#greens-functions-gw-rpa-and-dmft)
  - [Quantum embedding](#quantum-embedding)
  - [Reduced density matrices and natural orbital functionals](#reduced-density-matrices-and-natural-orbital-functionals)
  - [Response theory, properties, and excited states](#response-theory-properties-and-excited-states)
  - [Quantum computing for chemistry](#quantum-computing-for-chemistry)
  - [SCF and orbital optimization](#scf-and-orbital-optimization)
  - [Eigensolvers, linear algebra, and linear scaling](#eigensolvers-linear-algebra-and-linear-scaling)
  - [Real-space, multiresolution, and plane-wave infrastructure](#real-space-multiresolution-and-plane-wave-infrastructure)
  - [Brillouin zone, k-points, and Wannier functions](#brillouin-zone-k-points-and-wannier-functions)
  - [Pseudopotentials, PAW, and atomic solvers](#pseudopotentials-paw-and-atomic-solvers)
  - [Symmetry](#symmetry)
  - [Geometry optimization and reaction paths](#geometry-optimization-and-reaction-paths)
  - [Data formats, I/O, and interoperability](#data-formats-io-and-interoperability)
  - [Wavefunction and density analysis](#wavefunction-and-density-analysis)
  - [General-purpose utilities](#general-purpose-utilities)
  - [Related standalone tools](#related-standalone-tools)
  - [Quantum chemistry programs that use these libraries](#quantum-chemistry-programs-that-use-these-libraries)
  - [Other catalogs](#other-catalogs)
  - [Contributing](#contributing)

## Molecular integrals

| Project | Repository | License | Description |
|---|---|---|---|
| Libint | <https://github.com/evaleev/libint> | LGPL-3.0 (library), GPL-3.0 (code generator) | Library and code generator for many-body integrals over Gaussian functions: overlap, kinetic, nuclear attraction, multipoles, electron repulsion (2-, 3-, and 4-center), and their derivatives. |
| LibintX | <https://github.com/ValeevGroup/libintx> | LGPL-3.0 | GPU-accelerated evaluation of Gaussian electron repulsion integrals. |
| libcint | <https://github.com/sunqm/libcint> | Apache-2.0 | Open-source library of analytical Gaussian integrals, covering many operators, derivatives, spinor integrals, and GIAO integrals. This is the integral engine of PySCF. |
| qcint | <https://github.com/sunqm/qcint> | GPL-3.0 | SIMD-optimized version of libcint with the same API, for x86-64 CPUs with AVX/AVX2/AVX-512. |
| Simint | <https://github.com/simint-chem/simint-generator> | BSD-3-Clause | Code generator for vectorized electron repulsion integrals, using the Obara–Saika scheme. |
| Libecpint | <https://github.com/robashaw/libecpint> | MIT | Integrals over effective core potentials (ECPs) and their derivatives. |
| libgrpp | <https://github.com/aoleynichenko/libgrpp> | MIT | Integrals over generalized relativistic pseudopotentials (GRPPs), including spin-orbit terms, and conventional ECPs. |
| GBasis | <https://github.com/theochem/gbasis> | LGPL-3.0 | Pure Python library for integrals and evaluation of Gaussian basis functions. |
| LibERI | <https://github.com/gms-bbg/gms_libERI> | MIT | GPU-accelerated electron repulsion integral and Fock build library in Fortran with OpenMP offload (rotated-axis and Rys quadrature), developed for GAMESS and callable through MDI. |
| JoltQC | <https://github.com/ByteDance-Seed/JoltQC> | Apache-2.0 | Just-in-time compiled GPU kernels for Gaussian two-electron integrals and J/K builds, integrated with GPU4PySCF. |
| Gen1Int | <https://gitlab.com/bingao/gen1int> | GPL-3.0 | One-electron integrals (including magnetic, derivative, and London-orbital integrals) over Gaussian functions, used by Dalton and OpenMolcas. |
| GTFock | <https://github.com/psi4/GTFock> | GPL-2.0 | Massively parallel direct Fock matrix construction. |
| DKH | <https://github.com/psi4/dkh> | LGPL-3.0 | Arbitrary-order Douglas–Kroll–Hess scalar-relativistic Hamiltonian by Wolf, Reiher, and Hess. |
| sympleints | <https://github.com/eljost/sympleints> | EUPL-1.2 | SymPy-based generator of molecular integral code over Gaussian basis functions. |
| MolecularIntegrals.jl | <https://github.com/rpmuller/MolecularIntegrals.jl> | MIT | Julia library of one- and two-electron integrals over Gaussian functions. |
| GaussianBasis.jl | <https://github.com/FermiQC/GaussianBasis.jl> | MIT | Julia package for Gaussian basis sets and integrals, with a native implementation and a libcint backend. |
| tad-libcint | <https://github.com/tad-mctc/tad-libcint> | Apache-2.0 | PyTorch interface to libcint with support for automatic differentiation. |
| ERD | <https://github.com/psi4/erd> | GPL-2.0 | Electron repulsion integral package from ACES III, packaged as a standalone library (legacy). |
| OptErd | <https://github.com/hpcgarage/OptErd> | LGPL-2.1 | Optimized, vectorized version of the ERD electron repulsion integral library (legacy). |
| LibRI | <https://github.com/abacusmodeling/LibRI> | LGPL-3.0 | Tensor library for resolution-of-identity (RI) calculations with localized auxiliary bases, used by ABACUS for hybrid functionals and RPA. |

## Basis sets

| Project | Repository | License | Description |
|---|---|---|---|
| Basis Set Exchange | <https://github.com/MolSSI-BSE/basis_set_exchange> | BSD-3-Clause | Library and database of Gaussian basis sets, with conversion to the input formats of many programs. |
| BasisOpt | <https://github.com/robashaw/basisopt> | MIT | Python library for optimizing Gaussian basis sets. |

## Numerical quadrature and exchange-correlation integration

Molecular and atomic quadrature grids, evaluation of basis functions on grids, and numerical integration of exchange-correlation contributions (mainly for DFT).

| Project | Repository | License | Description |
|---|---|---|---|
| IntegratorXX | <https://github.com/wavefunction91/IntegratorXX> | BSD-3-Clause | Reusable C++ library of radial, angular, and product quadratures and molecular grids for DFT. |
| numgrid | <https://github.com/dftlibs/numgrid> | MPL-2.0 | Numerical integration grids for molecules (Becke/Lebedev-type). |
| Grid | <https://github.com/theochem/grid> | LGPL-3.0 | Python library for numerical integration, interpolation, and differentiation on molecular grids. |
| gau2grid | <https://github.com/psi4/gau2grid> | BSD-3-Clause | Fast, code-generated collocation of Gaussian basis functions and their derivatives on grids. |
| cuGBasis | <https://github.com/theochem/cuGBasis> | LGPL-3.0 | GPU evaluation of densities, gradients, electrostatic potentials, and other descriptors from Gaussian-basis wavefunctions. |
| GauXC | <https://github.com/wavefunction91/GauXC> | BSD-3-Clause | Exchange-correlation integration library for Gaussian basis sets on molecular grids: numerical integration of the XC energy, potential, and derivatives (and seminumerical exchange), on CPUs and GPUs. |
| XCint | <https://github.com/dftlibs/xcint> | MPL-2.0 | Numerical integration of exchange-correlation contributions for DFT. |
| libGridXC | <https://gitlab.com/siesta-project/libraries/libgridxc> | BSD-3-Clause | Evaluation of exchange-correlation energies and potentials on uniform real-space grids (as in SIESTA) and on radial atomic grids, including vdW-DF; it does not handle molecular quadrature grids. It can use Libxc. **[ESL]** |

## Density functionals and exchange-correlation

| Project | Repository | License | Description |
|---|---|---|---|
| Libxc | <https://gitlab.com/libxc/libxc> | MPL-2.0 | Library of about 600 exchange-correlation functionals (LDA, GGA, meta-GGA, hybrid, range-separated) with high-order derivatives, for any basis set type. **[ESL]** |
| libxckernel | <https://github.com/susilehtola/libxckernel> | BSD-3-Clause | Automatic code generator for exchange-correlation response kernels on top of Libxc. It uses symbolic differentiation to build the contraction layer needed in linear and higher-order response for any discretization. |
| XCFun | <https://github.com/dftlibs/xcfun> | MPL-2.0 | Exchange-correlation functionals with derivatives to arbitrary order, obtained by automatic differentiation. |
| libvdwxc | <https://gitlab.com/libvdwxc/libvdwxc> | GPL-3.0-or-later | Nonlocal van der Waals density functionals (vdW-DF family) evaluated on real-space grids with FFTs. **[ESL]** |
| ExchCXX | <https://github.com/wavefunction91/ExchCXX> | BSD-3-Clause | Modern C++ exchange-correlation library with CPU and GPU (CUDA, HIP, SYCL) kernels, built on Libxc functional definitions. |
| MCfun | <https://github.com/Multi-collinear/MCfun> | Apache-2.0 | Turns collinear functionals into multicollinear functionals for noncollinear DFT and TDDFT. |
| Libxc.jl | <https://github.com/JuliaMolSim/Libxc.jl> | MIT | Julia bindings to Libxc. |
| DftFunctionals.jl | <https://github.com/JuliaMolSim/DftFunctionals.jl> | MIT | Julia interface to and native implementations of exchange-correlation functionals, used by DFTK.jl. |
| jax_xc | <https://github.com/sail-sg/jax_xc> | MPL-2.0 | Libxc functionals translated to JAX, for differentiable exchange-correlation on accelerators. |
| xcauto | <https://github.com/dftlibs/xcauto> | MPL-2.0 | Arbitrary-order exchange-correlation functional derivatives via automatic differentiation. |
| Skala | <https://github.com/microsoft/skala> | MIT | PyTorch implementation of the Skala deep-learned exchange-correlation functional, with bindings to PySCF, GPU4PySCF, and ASE. |
| DM21 | <https://github.com/google-deepmind/deepmind-research/tree/master/density_functional_approximation_dm21> | Apache-2.0 | PySCF interface and trained weights for the DeepMind DM21 neural exchange-correlation functionals. |
| CiderPress | <https://github.com/cider-dft/CiderPress> | GPL-3.0 | Training and evaluation of CIDER machine-learned exchange-correlation functionals, with PySCF and GPAW interfaces. |
| DeePKS-kit | <https://github.com/deepmodeling/deepks-kit> | LGPL-3.0 | Training and use of DeePHF/DeePKS machine-learned energy and density functional corrections, built on PySCF and PyTorch. |
| NeuralXC | <https://github.com/semodi/neuralxc> | BSD-3-Clause | Machine-learned density functionals built on top of baseline functionals. |
| Libnxc | <https://github.com/semodi/libnxc> | MPL-2.0 | Library for using machine-learned exchange-correlation functionals inside DFT codes. |
| Grad DFT | <https://github.com/XanaduAI/GradDFT> | Apache-2.0 | JAX library for differentiable design and training of machine-learned exchange-correlation functionals. |
| DQC | <https://github.com/diffqc/dqc> | Apache-2.0 | Differentiable quantum chemistry (DFT) in PyTorch, used for training exchange-correlation functionals. |
| DFTpy | <https://gitlab.com/pavanello-research-group/dftpy> | MIT | Python orbital-free DFT framework with kinetic energy density functionals. |

## Dispersion corrections and semiempirical methods

| Project | Repository | License | Description |
|---|---|---|---|
| simple-dftd3 (s-dftd3) | <https://github.com/dftd3/simple-dftd3> | LGPL-3.0 | Reimplementation of the DFT-D3 dispersion correction (zero, BJ, modified, and optimized power damping; three-body terms) as a library (`libs-dftd3`) with C, Fortran, and Python APIs. |
| dftd3-lib | <https://github.com/dftbplus/dftd3-lib> | GPL-1.0-or-later | Library version of Grimme's original DFT-D3 program (the classic "libdftd3"). It is now superseded by simple-dftd3. |
| DFT-D4 | <https://github.com/dftd4/dftd4> | LGPL-3.0 | D4 London dispersion correction with charge-dependent C6 coefficients, as a library (`libdftd4`) with C, Fortran, and Python APIs. |
| multicharge | <https://github.com/grimme-lab/multicharge> | Apache-2.0 | Electronegativity equilibration (EEQ) atomic partial charges, as used by DFT-D4. |
| tad-dftd3 | <https://github.com/dftd3/tad-dftd3> | Apache-2.0 | Fully differentiable PyTorch implementation of DFT-D3. |
| tad-dftd4 | <https://github.com/dftd4/tad-dftd4> | Apache-2.0 | Fully differentiable PyTorch implementation of DFT-D4. |
| torch-dftd | <https://github.com/pfnet-research/torch-dftd> | MIT | PyTorch implementation of DFT-D2 and DFT-D3, with GPU support. |
| gCP | <https://github.com/grimme-lab/gcp> | LGPL-3.0 | Geometrical counterpoise correction for basis set superposition error. |
| libMBD | <https://github.com/libmbd/libmbd> | MPL-2.0 | Many-body dispersion (MBD) method. |
| tblite | <https://github.com/tblite/tblite> | LGPL-3.0 | Light-weight library for tight-binding methods (GFN1-xTB, GFN2-xTB, IPEA1-xTB) with C, Fortran, and Python APIs. |
| DFTB+ | <https://github.com/dftbplus/dftbplus> | LGPL-3.0-or-later | Density-functional tight-binding program that can also be linked as a library (libDFTB+). |
| tad-multicharge | <https://github.com/tad-mctc/tad-multicharge> | Apache-2.0 | Differentiable PyTorch implementation of the electronegativity equilibration charge model used by DFT-D4. |

## Electrostatics, multipoles, and fast multipole methods

| Project | Repository | License | Description |
|---|---|---|---|
| GDMA | <https://github.com/psi4/gdma> | GPL-2.0 | Anthony Stone's Gaussian distributed multipole analysis, packaged as a library. |
| helPME | <https://github.com/andysim/helpme> | BSD-3-Clause | Header-only C++ particle-mesh Ewald library for Coulomb and dispersion terms with arbitrary multipoles; C, Fortran, and Python bindings. |
| FMM3D | <https://github.com/flatironinstitute/FMM3D> | Apache-2.0 | Fast multipole method for Laplace and Helmholtz potentials in 3D. |
| exafmm-t | <https://github.com/exafmm/exafmm-t> | BSD-3-Clause | Kernel-independent fast multipole method library with a Python interface. |
| PVFMM | <https://github.com/dmalhotra/pvfmm> | LGPL-3.0 | Parallel kernel-independent fast multipole method for particle and volume potentials. |
| ScaFaCoS | <https://github.com/scafacos/scafacos> | GPL-3.0 | Parallel fast Coulomb solvers (FMM, P3M, P2NFFT, and others) behind a common interface. |

## Solvation, QM/MM, and embedding potentials

| Project | Repository | License | Description |
|---|---|---|---|
| MOIST | <https://github.com/lukaswittmann/moist> | MPL-2.0 | Implicit solvation library with differentiable cavities (SvdW-, isodensity-DROP), polarizable continuum (IEF-PCM, SS(V)PE, DPCM, C-PCM, SLIC, LPB), pressure (PV, GOSTSHYP), and statistical solvation models (RISM, MOZ). |
| PCMSolver | <https://github.com/PCMSolver/pcmsolver> | LGPL-3.0 | API library for the polarizable continuum model (PCM), including IEFPCM and C-PCM. |
| ddX | <https://github.com/ddsolvation/ddX> | LGPL-3.0 | Domain-decomposition implementations of continuum solvation models (ddCOSMO, ddPCM, ddLPB). |
| CPPE | <https://github.com/maxscheurer/cppe> | LGPL-3.0 | C++ and Python library for polarizable embedding (PE). |
| PElib | <https://gitlab.com/pe-software/pelib-public> | GPL-3.0 | Fortran library for polarizable embedding. |
| PyFraME | <https://gitlab.com/FraME-projects/PyFraME> | GPL-3.0-or-later | Python framework for setting up fragment-based multiscale embedding calculations, such as polarizable embedding potentials. |
| libefp | <https://github.com/libefp2/libefp> | BSD-2-Clause | Effective fragment potential (EFP) method. |
| CPCM-X | <https://github.com/grimme-lab/CPCM-X> | LGPL-3.0 | Extended conductor-like polarizable continuum model (CPCM-X), which combines CPCM with COSMO-RS-type corrections for solvation free energies. |
| openCOSMO-RS | <https://github.com/TUHH-TVT/openCOSMO-RS_py> | LGPL-3.0 | Open-source implementation of COSMO-RS for thermodynamic properties of liquid mixtures. |
| Environ | <https://github.com/environ-developers/Environ> | GPL-2.0 | Fortran library for continuum embedding (solvation, electrolytes, electrochemical interfaces), interfaced with Quantum ESPRESSO. |
| APBS | <https://github.com/Electrostatics/apbs> | BSD-3-Clause | Adaptive Poisson–Boltzmann solver for biomolecular electrostatics and solvation. |
| PyGBe | <https://github.com/pygbe/pygbe> | BSD-3-Clause | GPU-accelerated boundary element solver for implicit-solvent (Poisson–Boltzmann) electrostatics. |
| FraME | <https://gitlab.com/FraME-projects/FraME> | GPL-3.0-or-later | Library for fragment-based multiscale embedding, used by LSDalton. |
| OpenMMPol | <https://github.com/Molecolab-Pisa/OpenMMPol> | LGPL-3.0 | Induced point-dipole polarizable QM/MM (AMOEBA and others) with C, Fortran, and Python interfaces. |
| MiMiC | <https://gitlab.com/mimic-project/mimic> | LGPL-3.0-or-later | Framework for multiscale (QM/MM) simulations that couples separate programs running concurrently. |
| MiMiC Communication Library (MCL) | <https://gitlab.com/mimic-project/mcl> | LGPL-3.0-or-later | Lightweight library through which client programs communicate with MiMiC. |
| LIO | <https://github.com/MALBECC/lio> | GPL-2.0 | CPU and GPU Gaussian-basis DFT library designed for QM/MM with Amber. |
| Janus | <https://github.com/CCQC/janus> | BSD-3-Clause | Python library for adaptive QM/MM that interfaces Psi4 and OpenMM. |
| ASH | <https://github.com/RagnarB83/ash> | GPL-2.0 | Python multiscale and QM/MM environment that drives many QC programs and OpenMM. |
| PyADF | <https://github.com/chjacob-tubs/pyadf-releases> | GPL-3.0 | Python scripting framework for multiscale quantum chemistry, including the PyEmbed frozen-density embedding potentials. |

## Angular momentum algebra and special functions

| Project | Repository | License | Description |
|---|---|---|---|
| libwignernj | <https://github.com/susilehtola/libwignernj> | BSD-3-Clause | Exact evaluation of Wigner 3j, 6j, and 9j symbols, Clebsch–Gordan coefficients, Racah W coefficients, and Gaunt coefficients (for complex and real spherical harmonics), with C, C++, Fortran, and Python interfaces. |
| WIGXJPF | <http://fy.chalmers.se/subatom/wigxjpf/> | LGPL-3.0-or-later | Fast, accurate evaluation of Wigner 3j, 6j, and 9j symbols using prime factorization. |
| sphericart | <https://github.com/lab-cosmo/sphericart> | MIT | Fast evaluation of real spherical harmonics and their derivatives on CPUs and GPUs. |
| WignerSymbols.jl | <https://github.com/Jutho/WignerSymbols.jl> | MIT | Julia package for exact Wigner 3j and 6j symbols, Clebsch–Gordan and Racah coefficients. |
| SHarmonic | <https://gitlab.com/npneq/sharmonic> | MPL-2.0 | Header-only C++ library of spherical harmonics, from inq. |

## Tensor libraries

| Project | Repository | License | Description |
|---|---|---|---|
| libtensor | <https://github.com/epifanovsky/libtensor> | BSL-1.0 | C++ library for block tensors with symmetry, designed for many-body methods. It is the tensor backend of adcc. |
| TiledArray | <https://github.com/ValeevGroup/tiledarray> | GPL-3.0 | Massively parallel block-sparse tensor framework in C++, built on MADNESS runtime/TTG. |
| BTAS | <https://github.com/ValeevGroup/BTAS> | BSD-3-Clause | Basic Tensor Algebra Subroutines, a C++ header-only library for dense tensors. |
| Cyclops Tensor Framework (CTF) | <https://github.com/cyclops-community/ctf> | BSD-2-Clause | Distributed-memory library for dense and sparse tensor contractions. |
| TAMM | <https://github.com/NWChemEx/TAMM> | Apache-2.0 | Tensor Algebra for Many-body Methods, a parallel tensor framework for CPUs and GPUs from NWChemEx. |
| TBLIS | <https://github.com/MatthewsResearchGroup/tblis> | BSD-3-Clause | High-performance tensor contraction built on the BLIS approach, which avoids explicit transposition. |
| HPTT | <https://github.com/springer13/hptt> | BSD-3-Clause | High-performance tensor transposition. |
| Ambit | <https://github.com/jturney/ambit> | LGPL-3.0 | C++ and Python tensor library for quantum chemistry, used in Forte. |
| Einsums | <https://github.com/Einsums/Einsums> | MIT | C++ tensor library with einsum-style contractions dispatched to BLAS and GPU kernels. |
| opt_einsum | <https://github.com/dgasmith/opt_einsum> | MIT | Optimized contraction ordering for `einsum`-style expressions in Python. |
| ExaTENSOR | <https://github.com/ORNL-QCI/ExaTENSOR> | BSD-3-Clause | Numerical tensor algebra for distributed heterogeneous HPC platforms. |
| ExaTN | <https://github.com/ORNL-QCI/exatn> | BSD-3-Clause | Distributed, hierarchical tensor network processing on HPC and GPU systems. |
| TAPP | <https://github.com/TAPPorg/reference-implementation> | BSD-3-Clause | Tensor Algebra Processing Primitives: a proposed standard C interface for tensor operations, with a reference implementation. |
| Global Arrays | <https://github.com/GlobalArrays/ga> | BSD-3-Clause | Partitioned global address space library for distributed arrays, used by NWChem and others. |
| TensorOperations.jl | <https://github.com/QuantumKitHub/TensorOperations.jl> | MIT | Julia package for tensor contractions in index notation. |
| TensorKit.jl | <https://github.com/QuantumKitHub/TensorKit.jl> | MIT | Julia library for symmetric (block-sparse, symmetry-aware) tensor computations. |
| TCL | <https://github.com/springer13/tcl> | LGPL-3.0 | Dense tensor contractions via the transpose-transpose-GEMM-transpose approach. |
| TTC | <https://github.com/HPAC/TTC> | GPL-3.0 | Code generator for high-performance tensor transpositions. |
| LibreTT | <https://github.com/victor-anisimov/Librett> | MIT | GPU tensor transposition for CUDA, HIP, and SYCL (derived from cuTT), used by TiledArray. |
| hipTensor | <https://github.com/ROCm/hipTensor> | MIT | AMD GPU tensor primitives (contraction, permutation). |
| cotengra | <https://github.com/jcmgray/cotengra> | Apache-2.0 | Optimized contraction trees for large tensor networks and einsum expressions. |
| YASTN | <https://github.com/yastn/yastn> | Apache-2.0 | Python library for Abelian-symmetric block-sparse tensors and tensor networks, with NumPy or PyTorch backends. |
| TensorToolkit | <https://github.com/QuantumLiquids/TensorToolkit> | LGPL-3.0 | C++ symmetry-blocked tensor library with MPI and CUDA support. |

## Tensor networks and DMRG

| Project | Repository | License | Description |
|---|---|---|---|
| block2 | <https://github.com/block-hczhai/block2-preview> | GPL-3.0 | Efficient parallel quantum chemistry DMRG and related methods. |
| CheMPS2 | <https://github.com/SebWouters/CheMPS2> | GPL-2.0 | Spin-adapted DMRG library for ab initio quantum chemistry. |
| ITensor | <https://github.com/ITensor/ITensors.jl> | Apache-2.0 | Julia library for tensor network (MPS/DMRG) calculations. |
| QCMaquis | <https://github.com/qcscine/qcmaquis> | BSD-3-Clause | DMRG program for quantum chemistry from the Reiher group (SCINE), interfaced with OpenMolcas. |
| pyblock3 | <https://github.com/block-hczhai/pyblock3-preview> | GPL-3.0 | Python block-sparse, symmetry-aware tensor library with MPS/MPO/DMRG tools (companion to block2). |
| chemtensor | <https://github.com/qc-tum/chemtensor> | Apache-2.0 | C library with a Python interface for tensor network algorithms, including DMRG for chemical Hamiltonians. |
| quimb | <https://github.com/jcmgray/quimb> | Apache-2.0 | Python library for quantum information and many-body calculations with tensor networks. |
| TeNPy | <https://github.com/tenpy/tenpy> | Apache-2.0 | Python library for MPS, DMRG, and TEBD simulations with charge-conserving tensors. |
| MPSKit.jl | <https://github.com/QuantumKitHub/MPSKit.jl> | MIT | Julia matrix product state algorithms (DMRG, VUMPS, TDVP) built on TensorKit.jl. |
| Renormalizer | <https://github.com/shuaigroup/Renormalizer> | Apache-2.0 | Tensor network (MPS, ML-MCTDH) quantum and vibronic dynamics of molecular systems. |

## Second quantization and equation generation

| Project | Repository | License | Description |
|---|---|---|---|
| SeQuant | <https://github.com/ValeevGroup/SeQuant> | LGPL-3.0 | C++ symbolic algebra of tensors over operator-valued rings, for deriving and evaluating many-body equations (coupled-cluster, etc.). |
| pdaggerq | <https://github.com/edeprince3/pdaggerq> | Apache-2.0 | Python package for fermionic (and bosonic) second-quantized algebra; derives coupled-cluster and related equations and generates code. |
| Wick&d (wicked) | <https://github.com/fevangelista/wicked> | MIT | C++/Python program for Wick's theorem with arbitrary reference states, used to derive many-body equations. |
| Drudge | <https://github.com/DrudgeCAS/drudge> | MIT | Symbolic algebra system for noncommutative (second-quantized) algebras, built on SymPy and Spark. |
| gristmill | <https://github.com/DrudgeCAS/gristmill> | MIT | Optimizes and generates code for tensor contraction expressions, such as those from Drudge. |
| GeCCo | <https://github.com/ak-ustutt/GeCCo-public> | MIT | General Contraction Code: symbolic derivation and numerical evaluation of coupled-cluster, internally contracted MRCC, and explicitly correlated theories. |
| SMITH3 | <https://github.com/qsimulate-open/smith3> | GPL-2.0 | Code generator for multireference methods (e.g., CASPT2 gradients, MRCI), used to produce BAGEL code. |
| SQA+ | <https://github.com/sokolov-group/sqa_plus> | GPL-3.0 | Extended Second Quantization Algebra for deriving multireference (e.g., MR-ADC) equations and generating code. |
| wick | <https://github.com/awhite862/wick> | MIT | Pure Python library for applying Wick's theorem and simplifying second-quantized operator strings. |
| SpinAdaptedSecondQuantization.jl | <https://github.com/MarcusTL12/SpinAdaptedSecondQuantization.jl> | MIT | Julia package for symbolic spin-adapted second-quantization algebra. |
| QuantumAlgebra.jl | <https://github.com/jfeist/QuantumAlgebra.jl> | MIT | Julia package for symbolic bosonic and fermionic operator algebra (normal ordering, expectation values). |
| SNEG | <https://github.com/rokzitko/sneg> | GPL-3.0 | Mathematica package for symbolic algebra with noncommuting second-quantization operators (requires Mathematica). |

## Coupled cluster, configuration interaction, and perturbation theory

| Project | Repository | License | Description |
|---|---|---|---|
| libgnme | <https://github.com/hgaburton/libgnme> | MIT | Matrix elements between nonorthogonal determinants (generalized nonorthogonal matrix elements). |
| MACIS | <https://github.com/wavefunction91/MACIS> | BSD-3-Clause | Modern C++ library for high-performance selected configuration interaction. |
| PyCI | <https://github.com/theochem/PyCI> | GPL-3.0 | Python/C++ library for configuration interaction, including selected, seniority-based, and parameterized CI. |
| GQCP | <https://github.com/GQCG/GQCP> | LGPL-3.0 | Ghent Quantum Chemistry Package: C++ library with Python bindings for CI, geminals, and other wavefunction models. |
| FanPy | <https://github.com/theochem/fanpy> | LGPL-3.0 | Python library for projected geminal and flexible CI wavefunctions. |
| hexpr | <https://github.com/emol-project/hexpr> | MIT | C library with Fortran, Python, Julia, and Ruby bindings that generates CSF-based Hamiltonian matrix element expressions for CI. |
| ATRIP | <https://github.com/alejandrogallo/atrip> | Apache-2.0 | Distributed C++ library for the (T) triples correction of CCSD(T). |
| ccpy | <https://github.com/piecuch-group/ccpy> | GPL-3.0 | Python/Fortran coupled-cluster package (CC(P;Q), EOMCC, active-space CC) interfaced with PySCF and GAMESS. |
| PyCC | <https://github.com/CrawfordGroup/pycc> | BSD-3-Clause | Python implementation of ground-state, response, and real-time coupled cluster, built on Psi4. |
| cqcpy | <https://github.com/awhite862/cqcpy> | MIT | Python utilities for quantum chemistry, including coupled-cluster amplitude and integral handling. |
| kelvin | <https://github.com/awhite862/kelvin> | MIT | Python library for finite-temperature coupled cluster and many-body perturbation theory. |
| Fermi.jl | <https://github.com/FermiQC/Fermi.jl> | MIT | Julia quantum chemistry framework with modular HF, MP2, and CCSD(T) implementations. |
| laplace-minimax | <https://github.com/bhelmichparis/laplace-minimax> | LGPL-3.0 | Minimax Laplace quadrature weights and exponents for orbital energy denominators (MP2, RPA, CC). |
| pyscf-forge | <https://github.com/pyscf/pyscf-forge> | Apache-2.0 | PySCF extension modules (e.g., MC-PDFT, LPNO methods) that are not yet part of the PySCF core. |

## Quantum Monte Carlo

| Project | Repository | License | Description |
|---|---|---|---|
| QMCkl | <https://github.com/TREX-CoE/qmckl> | BSD-3-Clause | Kernels for quantum Monte Carlo: evaluation of orbitals, Jastrow factors, and so on. |
| ipie | <https://github.com/JoonhoLee-Group/ipie> | Apache-2.0 | Python/GPU library for phaseless auxiliary-field QMC (AFQMC) of molecules and solids. |
| PyQMC | <https://github.com/WagnerGroup/pyqmc> | MIT | Python library for real-space VMC and DMC, built on PySCF. |
| QMCTorch | <https://github.com/NLESC-JCER/QMCTorch> | Apache-2.0 | PyTorch implementation of real-space QMC for molecules. |
| Rimu.jl | <https://github.com/RimuQMC/Rimu.jl> | MIT | Julia library for FCIQMC, related projector Monte Carlo methods, and exact diagonalization. |
| FermiNet | <https://github.com/google-deepmind/ferminet> | Apache-2.0 | JAX implementation of the Fermionic Neural Network and related neural-network ansätze for VMC. |
| DeepQMC | <https://github.com/deepqmc/deepqmc> | MIT | JAX library for neural-network variational QMC of molecules. |
| JaQMC | <https://github.com/bytedance/jaqmc> | Apache-2.0 | JAX neural-network QMC library (LapNet, DMC, and related methods). |
| DeepErwin | <https://github.com/mdsunivie/deeperwin> | MIT | JAX neural-network wavefunction optimization with weight sharing across geometries. |
| NetKet | <https://github.com/netket/netket> | Apache-2.0 | JAX library for neural quantum states and VMC of many-body systems, including molecular Hamiltonians. |

## Green's functions, GW, RPA, and DMFT

| Project | Repository | License | Description |
|---|---|---|---|
| GreenX | <https://github.com/nomad-coe/greenX> | Apache-2.0 | Library for Green's function methods: minimax time/frequency grids, analytic continuation, and localized-basis GW/RPA building blocks. |
| LibRPA | <https://github.com/AESM-Group/LibRPA> | LGPL-3.0 | RPA correlation energies and GW with localized resolution of identity, interfaced with ABACUS and FHI-aims. |
| momentGW | <https://github.com/BoothGroup/momentGW> | MIT | PySCF-based GW methods using moment-conserving Dyson equation solvers. |
| green-mbpt | <https://github.com/Green-Phys/green-mbpt> | MIT | Finite-temperature fully self-consistent GW and GF2 for molecules and solids. |
| sparse-ir | <https://github.com/SpM-lab/sparse-ir> | MIT | Intermediate representation basis and sparse sampling for imaginary-time and Matsubara Green's functions. |
| Nevanlinna.jl | <https://github.com/SpM-lab/Nevanlinna.jl> | MIT | Nevanlinna analytic continuation of Matsubara Green's functions. |
| libNEGF | <https://github.com/libnegf/libnegf> | LGPL-3.0-or-later | Non-equilibrium Green's functions for quantum transport, used by DFTB+. |
| TRIQS | <https://github.com/TRIQS/triqs> | GPL-3.0 | Toolbox for Research on Interacting Quantum Systems: C++/Python building blocks for Green's functions and DMFT. |
| TRIQS/CTHYB | <https://github.com/TRIQS/cthyb> | GPL-3.0 | Continuous-time hybridization-expansion quantum impurity solver built on TRIQS. |
| EDIpack | <https://github.com/EDIpack/EDIpack> | GPL-3.0 | Lanczos exact diagonalization impurity solver with Fortran, C, and Python interfaces for DMFT. |
| ALPSCore | <https://github.com/ALPSCore/ALPSCore> | MIT | C++ core libraries for many-body simulations (Green's function containers, statistics, HDF5 I/O). |
| fcDMFT | <https://github.com/ZhuGroup-Yale/fcdmft> | GPL-3.0 | PySCF-based full-cell DMFT and GW+DMFT for solids with quantum chemistry impurity solvers. |

## Quantum embedding

| Project | Repository | License | Description |
|---|---|---|---|
| Vayesta | <https://github.com/BoothGroup/Vayesta> | Apache-2.0 | Python package for quantum embedding methods (DMET, EwF, etc.), built on PySCF. |
| libDMET | <https://github.com/gkclab/libdmet_preview> | GPL-3.0 | Density matrix embedding theory for molecules and solids, built on PySCF. |
| QuEmb | <https://github.com/troyvvgroup/quemb> | Apache-2.0 | Bootstrap embedding for molecules and periodic systems, built on PySCF. |
| pDMET | <https://github.com/hungpham2017/pDMET> | Apache-2.0 | Density matrix embedding theory for periodic systems, built on PySCF. |
| PsiEmbed | <https://github.com/danclaudino/PsiEmbed> | MIT | Projection-based wavefunction-in-DFT embedding using Psi4 or PySCF. |
| QSoME | <https://github.com/Goodpaster/QSoME> | Apache-2.0 | Projection-based embedding for molecular and periodic systems, built on PySCF. |

## Reduced density matrices and natural orbital functionals

| Project | Repository | License | Description |
|---|---|---|---|
| v2rdm_casscf | <https://github.com/edeprince3/v2rdm_casscf> | GPL-2.0 | Variational two-electron reduced density matrix driven CASSCF (Psi4 plugin). |
| hilbert | <https://github.com/edeprince3/hilbert> | GPL-3.0 | Psi4 plugin for v2RDM-CASSCF, pair coupled cluster and DOCI-type methods, and QED coupled cluster. |
| PyNOF | <https://github.com/DoNOF/PyNOF> | GPL-3.0 | Python implementation of natural orbital functional theory. |
| DoNOF.jl | <https://github.com/DoNOF/DoNOF.jl> | GPL-3.0-or-later | Julia implementation of natural orbital functional theory. |

## Response theory, properties, and excited states

| Project | Repository | License | Description |
|---|---|---|---|
| adcc | <https://github.com/adc-connect/adcc> | GPL-3.0 | Algebraic-diagrammatic construction (ADC) methods for excited states, with a Python frontend and C++ core. It connects to SCF results from several host programs. |
| respondo | <https://github.com/gator-program/respondo> | GPL-3.0 | Library for response functions and spectroscopic properties, built on adcc. |
| OpenRSP | <https://github.com/openrsp/openrsp> | LGPL-2.1 | Library for arbitrary-order response theory properties. |
| QcMatrix | <https://gitlab.com/bingao/qcmatrix> | GPL-3.0 | Abstract matrix library in C (with C++ and Fortran interfaces) used by OpenRSP. |
| pymolresponse | <https://github.com/berquist/pymolresponse> | BSD-3-Clause | Frequency-dependent molecular linear response properties for arbitrary operators. |
| pyscf-properties | <https://github.com/pyscf/properties> | Apache-2.0 | PySCF extension for molecular and crystal electromagnetic properties (NMR, EPR, polarizabilities). |
| Prism | <https://github.com/sokolov-group/prism> | GPL-3.0 | Multireference ADC and NEVPT methods for spectroscopic properties, built on PySCF. |
| Libra | <https://github.com/Quantum-Dynamics-Hub/libra-code> | GPL-3.0 | C++/Python library for nonadiabatic and excited-state molecular dynamics. |

## Quantum computing for chemistry

| Project | Repository | License | Description |
|---|---|---|---|
| OpenFermion | <https://github.com/quantumlib/OpenFermion> | Apache-2.0 | Library for fermionic operators and electronic structure Hamiltonians, aimed at quantum computing. |
| OpenFermion-PySCF | <https://github.com/quantumlib/OpenFermion-PySCF> | Apache-2.0 | OpenFermion plugin that generates molecular Hamiltonians with PySCF. |
| OpenFermion-Psi4 | <https://github.com/quantumlib/OpenFermion-Psi4> | LGPL-3.0 | OpenFermion plugin that generates molecular Hamiltonians with Psi4. |
| OpenFermion-FQE | <https://github.com/quantumlib/OpenFermion-FQE> | Apache-2.0 | Fermionic Quantum Emulator for simulating fermionic circuits and dynamics. |
| Qiskit Nature | <https://github.com/qiskit-community/qiskit-nature> | Apache-2.0 | Fermionic operators, qubit mappings, and electronic structure problem classes for quantum algorithms. |
| qiskit-addon-sqd | <https://github.com/Qiskit/qiskit-addon-sqd> | Apache-2.0 | Sample-based quantum diagonalization post-processing for chemistry Hamiltonians. |
| ffsim | <https://github.com/qiskit-community/ffsim> | Apache-2.0 | Fast simulation of particle-number-conserving fermionic quantum circuits. |
| PennyLane | <https://github.com/PennyLaneAI/pennylane> | Apache-2.0 | Quantum programming library whose qchem module builds differentiable molecular Hamiltonians and fermion-to-qubit mappings. |
| Tequila | <https://github.com/tequilahub/tequila> | MIT | Python framework for variational quantum algorithms with molecular Hamiltonian tools. |
| QForte | <https://github.com/evangelistalab/qforte> | LGPL-3.0 | C++/Python library for developing quantum algorithms for chemistry (VQE, QPE, QITE, SRQK). |
| Qibochem | <https://github.com/qiboteam/qibochem> | Apache-2.0 | Qibo plugin with molecular Hamiltonians, fermion mappings, and ansätze. |
| Symmer | <https://github.com/qmatter-labs/symmer> | MIT | Qubit subspace methods (tapering, contextual subspace) for reducing qubit counts of molecular Hamiltonians. |
| QDK/Chemistry | <https://github.com/microsoft/qdk-chemistry> | MIT | Toolkit for classical and quantum chemistry workflows, including Hamiltonian construction and qubit mapping. |
| QURI SDK | <https://github.com/QunaSys/quri-sdk> | Apache-2.0 | Modular quantum algorithm libraries (QURI Parts) with chemistry modules interfacing PySCF and OpenFermion. |

## SCF and orbital optimization

| Project | Repository | License | Description |
|---|---|---|---|
| OpenOrbitalOptimizer | <https://github.com/susilehtola/OpenOrbitalOptimizer> | MPL-2.0 | Reusable C++ library for self-consistent field convergence (DIIS, EDIIS, ADIIS, ODA, etc.). It works for any orbital basis. |
| OpenTrustRegion | <https://github.com/eriksen-lab/opentrustregion> | MPL-2.0 | Reusable library for second-order trust-region orbital optimization (SCF, localization, CASSCF). |

## Eigensolvers, linear algebra, and linear scaling

| Project | Repository | License | Description |
|---|---|---|---|
| ELPA | <https://gitlab.mpcdf.mpg.de/elpa/elpa> | LGPL-3.0-only | Massively parallel direct dense eigensolver for symmetric/Hermitian matrices, on CPUs and GPUs. **[ESL]** |
| ELSI | <https://gitlab.com/elsi_project/elsi_interface> | BSD-3-Clause | Unified interface to Kohn–Sham solvers (ELPA, libOMM, PEXSI, NTPoly, etc.). **[ESL]** |
| PEXSI | <https://bitbucket.org/berkeleylab/pexsi> | BSD-3-Clause | Pole expansion and selected inversion; computes the density matrix without diagonalization. **[ESL]** |
| libOMM | <https://gitlab.com/ElectronicStructureLibrary/omm/libomm> | BSD-2-Clause | Orbital minimization method for solving the Kohn–Sham problem. **[ESL]** |
| MatrixSwitch | <https://gitlab.com/ElectronicStructureLibrary/omm/matrixswitch> | BSD-2-Clause | Interface layer between high-level algorithms and low-level matrix storage/operations (dense, sparse, distributed). **[ESL]** |
| NTPoly | <https://github.com/william-dawson/NTPoly> | MIT | Massively parallel sparse matrix functions for linear-scaling electronic structure. |
| DBCSR | <https://github.com/cp2k/dbcsr> | GPL-2.0 | Distributed block compressed sparse row matrix library, from CP2K. |
| DLA-Future | <https://github.com/eth-cscs/DLA-Future> | BSD-3-Clause | Task-based distributed dense linear algebra (eigensolver) for CPUs and GPUs. |
| COSMA | <https://github.com/eth-cscs/COSMA> | BSD-3-Clause | Communication-optimal distributed matrix multiplication. |
| libxsmm | <https://github.com/libxsmm/libxsmm> | BSD-3-Clause | Specialized kernels for small dense and sparse matrix multiplications. |
| PRIMME | <https://github.com/primme/primme> | BSD-3-Clause | Iterative eigensolvers (Davidson-type) and SVD solvers for large sparse problems. |
| diaglib | <https://github.com/Molecolab-Pisa/diaglib> | MPL-2.0 | Fortran library of matrix-free iterative eigensolvers with C and Python interfaces: Davidson–Liu, LOBPCG, and nonsymmetric Davidson. |
| iterative-solver | <https://github.com/molpro/iterative-solver> | MIT | Iterative solvers from Molpro (C++ with Fortran and C wrappers): eigenvalue problems, linear equations, L-BFGS optimization, and DIIS for nonlinear equations. It is templated on the container and provides distributed arrays. |
| SuperLU_DIST | <https://github.com/xiaoyeli/superlu_dist> | BSD-3-Clause | Distributed sparse direct solver; used by PEXSI. |
| BSEPACK | <https://sites.google.com/a/lbl.gov/bsepack/> | not verified | Parallel solver for Bethe–Salpeter eigenvalue problems. The project page may require a Google sign-in. |
| ChASE | <https://github.com/ChASE-library/ChASE> | BSD-3-Clause | Chebyshev accelerated subspace iteration eigensolver for sequences of dense Hermitian eigenproblems, on CPUs and GPUs (GitHub mirror of the JSC GitLab). |
| EigenExa | <https://github.com/RIKEN-RCCS/EigenExa> | BSD-2-Clause | Massively parallel dense symmetric eigensolver from RIKEN. |
| EigenKernel | <https://github.com/eigenkernel/eigenkernel> | MIT | Middleware combining parallel generalized eigensolvers (ScaLAPACK, ELPA, EigenExa). |
| Eigensolver_gpu | <https://github.com/NVIDIA/Eigensolver_gpu> | MIT | GPU generalized symmetric/Hermitian eigensolver used in GPU builds of Quantum ESPRESSO. |
| Fortran_Davidson | <https://github.com/NLESC-JCER/Fortran_Davidson> | Apache-2.0 | Modern Fortran Davidson diagonalization for diagonally dominant matrices. |
| CheSS | <https://gitlab.com/l_sim/chess> | LGPL-3.0-or-later | Chebyshev sparse solvers for density matrices, matrix powers, and eigenvalue windows, used by BigDFT and SIESTA. |
| BML | <https://github.com/lanl/bml> | BSD-3-Clause | Dense and sparse matrix formats and operations for density matrix solvers. |
| PROGRESS | <https://github.com/lanl/qmd-progress> | BSD-3-Clause | Linear-scaling and graph-based electronic structure solvers (SP2 purification and others), built on BML. |
| nlcglib | <https://github.com/simonpintarelli/nlcglib> | BSD-3-Clause | Nonlinear conjugate gradient direct minimization for Kohn–Sham DFT, used by SIRIUS. |
| SpLA | <https://github.com/eth-cscs/spla> | BSD-3-Clause | Specialized distributed matrix multiplications for plane-wave electronic structure. |
| COSTA | <https://github.com/eth-cscs/COSTA> | BSD-3-Clause | Communication-optimal redistribution and transposition of distributed matrices. |

## Real-space, multiresolution, and plane-wave infrastructure

| Project | Repository | License | Description |
|---|---|---|---|
| MADNESS | <https://github.com/m-a-d-n-e-s-s/madness> | GPL-2.0 | Multiresolution adaptive numerical environment for scientific simulation, with a parallel runtime. |
| MRCPP | <https://github.com/MRChemSoft/mrcpp> | LGPL-3.0 | MultiResolution Computation Program Package: multiwavelet function representation and operators. |
| PSolver | <https://gitlab.com/l_sim/psolver> | GPL-2.0-or-later | Interpolating scaling function Poisson solver for various boundary conditions, from BigDFT. |
| SIRIUS | <https://github.com/electronic-structure/SIRIUS> | BSD-3-Clause | Domain-specific library for plane-wave DFT (PP-PW and FP-LAPW), on CPUs and GPUs. |
| SpFFT | <https://github.com/eth-cscs/SpFFT> | BSD-3-Clause | Sparse 3D FFT library for plane-wave codes, on CPUs and GPUs. |
| inq | <https://gitlab.com/npneq/inq> | MPL-2.0 | Library-first, GPU-native C++ engine for real-time and ground-state (TD)DFT. |

## Brillouin zone, k-points, and Wannier functions

| Project | Repository | License | Description |
|---|---|---|---|
| Wannier90 | <https://github.com/wannier-developers/wannier90> | LGPL-2.1 | Maximally localized Wannier functions. **[ESL]** |
| libtetrabz | <https://github.com/mitsuaki1987/libtetrabz> | MIT | Linear tetrahedron method for Brillouin zone integration. |
| kplib | <https://gitlab.com/muellergroup/kplib> | Apache-2.0 | Generation of efficient generalized Monkhorst–Pack k-point grids. |
| autoGR | <https://github.com/msg-byu/autoGR> | MIT | Generalized regular k-point grids with the best folding ratio or fewest irreducible points. |
| SeeK-path | <https://github.com/materialscloud-org/seekpath> | MIT | Standardized primitive cells and high-symmetry k-point paths for band structures. |
| Brillouin.jl | <https://github.com/thchr/Brillouin.jl> | MIT | Julia package for Brillouin zones and k-paths. |
| SymmetryReduceBZ.jl | <https://github.com/jerjorg/SymmetryReduceBZ.jl> | GPL-3.0 | Irreducible Brillouin zones of 2D and 3D crystals. |
| BrillouinZoneMeshes.jl | <https://github.com/numericalEFT/BrillouinZoneMeshes.jl> | MIT | Julia Brillouin zone meshes and integration. |
| Wannier.jl | <https://github.com/qiaojunfeng/Wannier.jl> | MIT | Julia package for constructing and interpolating maximally localized Wannier functions. |
| WannierBerri | <https://github.com/wannier-berri/wannier-berri> | GPL-2.0 | Wannier interpolation and k-space integration of Berry phase properties. |
| TBmodels | <https://github.com/Z2PackDev/TBmodels> | Apache-2.0 | Creation and manipulation of tight-binding models, including those from Wannier90. |
| Z2Pack | <https://github.com/Z2PackDev/Z2Pack> | GPL-3.0 | Topological invariants from hybrid Wannier charge centers of first-principles or tight-binding models. |
| BoltzTraP2 | <https://gitlab.com/sousaw/BoltzTraP2> | GPL-3.0-or-later | Smoothed Fourier band interpolation and Boltzmann transport from DFT eigenvalues. |
| IrRep | <https://github.com/irreducible-representations/irrep> | GPL-3.0 | Symmetry eigenvalues and irreducible representations of ab initio Bloch states. |
| easyunfold | <https://github.com/SMTG-Bham/easyunfold> | MIT | Supercell band structure unfolding. |
| BandUPpy | <https://github.com/band-unfolding/banduppy> | GPL-3.0 | Band unfolding of plane-wave calculations. |
| sisl | <https://github.com/zerothi/sisl> | MPL-2.0 | Python library for tight-binding and DFT Hamiltonians (SIESTA, Wannier90, and others): I/O, analysis, and large-scale tight binding. |
| PyProcar | <https://github.com/romerogroup/pyprocar> | GPL-3.0 | Pre- and post-processing of band structures: projected bands, Fermi surfaces, unfolding. |

## Pseudopotentials, PAW, and atomic solvers

| Project | Repository | License | Description |
|---|---|---|---|
| libpspio | <https://gitlab.com/ElectronicStructureLibrary/libpspio> | MPL-2.0 | Reading and writing pseudopotential files in many formats. **[ESL]** |
| libPSML | <https://gitlab.com/siesta-project/libraries/libpsml> | BSD-3-Clause | Handling of pseudopotentials in the PSML format. |
| libPAW | <https://github.com/abinit/abinit/tree/master/shared/libpaw> | GPL-3.0 | Projector augmented-wave (PAW) library from ABINIT, also used by BigDFT; lives in the ABINIT repository. |
| pseudopod | <https://gitlab.com/npneq/pseudopod> | MPL-2.0 | Parsing and in-memory storage of pseudopotentials, from inq. |
| PseudoPotentialIO.jl | <https://github.com/JuliaMolSim/PseudoPotentialIO.jl> | MIT | Julia reading and evaluation of pseudopotential files (UPF, psp8, and others). |
| pawpyseed | <https://github.com/kylebystrom/pawpyseed> | BSD-3-Clause | C/Python analysis of PAW wavefunctions (overlaps, projections). |
| dftatom | <https://github.com/certik/dftatom> | MIT | Radial Schrödinger, Dirac, and Poisson solvers and an atomic DFT SCF on arbitrary grids. |
| featom | <https://github.com/atomic-solvers/featom> | MIT | Finite element Schrödinger and Dirac solvers for atoms. |

## Symmetry

| Project | Repository | License | Description |
|---|---|---|---|
| spglib | <https://github.com/spglib/spglib> | BSD-3-Clause | Space group symmetry of crystals. |
| libmsym | <https://github.com/mcodev31/libmsym> | MIT | Molecular point group symmetry: detection, symmetrization, and symmetry-adapted linear combinations. |
| MolSym | <https://github.com/NASymmetry/MolSym> | MIT | Molecular point groups including non-Abelian ones: symmetrization, character tables, and SALCs of basis functions and internal coordinates. |
| QSym² | <https://gitlab.com/bangconghuynh/qsym2> | LGPL-3.0-or-later | Rust program and library for symbolic point group and representation analysis of wavefunctions, orbitals, and densities, including magnetic groups. |
| PointGroup | <https://github.com/abelcarreras/pointgroup> | MIT | Determination of molecular point groups in pure Python. |
| posym | <https://github.com/abelcarreras/posym> | MIT | Point symmetry analysis of molecular orbitals, wavefunctions, densities, and vibrations. |
| WFNSYM | <https://github.com/abelcarreras/WFNSYM> | MIT | Continuous symmetry measures of electronic wavefunctions, with the wfnsympy Python module. |
| cosymlib | <https://github.com/GrupEstructuraElectronicaSimetria/cosymlib> | MIT | Continuous shape and symmetry measures of structures and wavefunctions. |
| spgrep | <https://github.com/spglib/spgrep> | BSD-3-Clause | On-the-fly space group irreducible representations, built on spglib. |
| moyo | <https://github.com/spglib/moyo> | Apache-2.0 | Rust crystal symmetry library with Python bindings, from the spglib developers. |
| Crystalline.jl | <https://github.com/thchr/Crystalline.jl> | MIT | Julia tools for crystallographic symmetry, space group irreps, and band representations. |

## Geometry optimization and reaction paths

| Project | Repository | License | Description |
|---|---|---|---|
| geomeTRIC | <https://github.com/leeping/geomeTRIC> | BSD-3-Clause with a non-AI clause | Geometry optimization with translation–rotation internal coordinates. |
| OptKing | <https://github.com/psi-rking/optking> | BSD-3-Clause | Python geometry optimizer for minima and transition states, from Psi4. |
| PyBerny | <https://github.com/pyberny/pyberny> | MPL-2.0 | Molecular geometry optimizer based on the Berny algorithm. |
| DL-FIND | <https://www.chemshell.org/dl-find> | LGPL-3.0 | Fortran geometry optimization library for minima, transition states, reaction paths (NEB), and conical intersections. It ships with ChemShell and GAMESS-UK and is also downloadable as a standalone tarball from the ChemShell site. |
| libdlfind | <https://github.com/digital-chemistry-laboratory/libdlfind> | LGPL-3.0 | C API and Python interface to DL-FIND, for use as an optimization backend. |
| Sella | <https://github.com/zadorlab/sella> | LGPL-3.0 | Saddle point and minimum optimization with an ASE interface. |
| pysisyphus | <https://github.com/eljost/pysisyphus> | GPL-3.0 | Stationary point optimization, IRC, NEB, and growing string methods on ground- and excited-state surfaces (upstream no longer maintained). |
| vc-sqnm | <https://github.com/moritzgubler/vc-sqnm> | GPL-3.0 | Stabilized quasi-Newton (SQNM) and variable-cell SQNM optimizers in C++, Fortran, and Python. |
| GOpt | <https://github.com/theochem/gopt> | LGPL-3.0 | Optimization of molecular structures and reaction paths. |
| DMF | <https://github.com/shin1koda/dmf> | MIT | Direct MaxFlux method for reaction path and transition state searches. |
| geodesic-interpolate | <https://github.com/virtualzx-nad/geodesic-interpolate> | MIT | Geodesic interpolation of molecular geometries in redundant internal coordinates for initial reaction paths. |
| autodE | <https://github.com/duartegroup/autodE> | MIT | Automated reaction profile and transition state generation driving several QC programs. |
| SCINE ReaDuct | <https://github.com/qcscine/readuct> | BSD-3-Clause | Structure optimization, TS search, IRC, and NEB with interchangeable electronic structure backends. |
| TorsionDrive | <https://github.com/lpwgroup/torsiondrive> | MIT | Dihedral scans by wavefront propagation that drive constrained QC optimizations. |
| fromage | <https://github.com/Crespo-Otero-group/fromage> | MIT | Excited states of molecular aggregates with ONIOM embedding and penalty-function MECI optimization. |
| chemcoord | <https://github.com/mcocdawc/chemcoord> | LGPL-3.0 | Cartesian, Z-matrix, and internal coordinate conversions with analytic gradients. |
| irc | <https://github.com/RMeli/irc> | MIT | Header-only C++ transformations between Cartesian and redundant internal coordinates. |

## Data formats, I/O, and interoperability

| Project | Repository | License | Description |
|---|---|---|---|
| TREXIO | <https://github.com/TREX-CoE/trexio> | BSD-3-Clause | File format and library for storing wavefunction data (basis sets, orbitals, integrals, determinants). |
| QCSchema | <https://github.com/MolSSI/QCSchema> | BSD-3-Clause | JSON schema for quantum chemistry inputs and outputs. |
| QCElemental | <https://github.com/MolSSI/QCElemental> | BSD-3-Clause | Periodic table, physical constants, and molecule parsing/validation for quantum chemistry. |
| QCEngine | <https://github.com/MolSSI/QCEngine> | BSD-3-Clause | Unified executor for quantum chemistry programs using QCSchema. |
| MDI Library | <https://github.com/MolSSI-MDI/MDI_Library> | BSD-3-Clause | MolSSI Driver Interface for communication between codes (e.g., QM/MM, MD drivers). |
| ESCDF | <https://gitlab.com/ElectronicStructureLibrary/escdf/libescdf> | LGPL-2.1 | Electronic Structure Common Data Format specification and library. **[ESL]** |
| cclib | <https://github.com/cclib/cclib> | BSD-3-Clause | Parsers and algorithms for computational chemistry output files. |
| IOData | <https://github.com/theochem/iodata> | LGPL-3.0 | Python library for reading, writing, and converting computational chemistry file formats. |
| ASE | <https://gitlab.com/ase/ase> | LGPL-2.1-or-later | Atomic Simulation Environment: Python toolkit and common interface to many electronic structure codes. |
| i-PI | <https://github.com/i-pi/i-pi> | GPL-3.0 or MIT (dual) | Universal force engine for (path-integral) molecular dynamics, driving external electronic structure codes. |
| QCManyBody | <https://github.com/MolSSI/QCManyBody> | BSD-3-Clause | Many-body expansion (MBE) and basis set superposition error (BSSE) treatment for any QC program. |
| libetsf_io | <https://github.com/ElectronicStructureLibrary/libetsf_io> | LGPL-2.1 | Reading and writing files in the ETSF (European Theoretical Spectroscopy Facility) format. |
| EZFIO | <https://gitlab.com/scemama/EZFIO> | GPL-2.0 | Generator of Fortran/Python I/O libraries for a directory-based database, used by Quantum Package. |
| resultsFile | <https://gitlab.com/scemama/resultsFile> | GPL-2.0-or-later | Python parsers for output files of quantum chemistry programs. |
| mctc-lib | <https://github.com/grimme-lab/mctc-lib> | Apache-2.0 | Modular computation toolchain library: structure I/O and shared infrastructure for the Grimme-lab Fortran codes. |
| MOKIT | <https://github.com/1234zou/MOKIT> | Apache-2.0 | Transfer of molecular orbitals between QC programs (fch, molden, and others) and automated multireference workflows. |
| qcdata | <https://github.com/atomsforhumanity/qcdata> | MIT | Pydantic data structures for QC inputs and results (formerly qcio). |
| qccodec | <https://github.com/atomsforhumanity/qccodec> | MIT | Parsing of QC program outputs into qcdata objects and writing of native inputs. |
| qccompute | <https://github.com/atomsforhumanity/qccompute> | MIT | Runs QC programs through standardized qcdata inputs (formerly qcop). |
| qcconst | <https://github.com/atomsforhumanity/qcconst> | MIT | Physical constants and periodic table data for QC. |
| NOMAD electronic-parsers | <https://github.com/nomad-coe/electronic-parsers> | Apache-2.0 | Parsers for the outputs of many electronic structure codes into NOMAD metainfo. |
| PLAMS | <https://github.com/SCM-NV/PLAMS> | LGPL-3.0 | Python library for automating simulations across many QC and MD engines. |
| SCINE Core | <https://github.com/qcscine/core> | BSD-3-Clause | Module interface that lets SCINE programs load electronic structure calculators as plugins. |
| SCINE Utilities | <https://github.com/qcscine/utilities> | BSD-3-Clause | Shared SCINE C++ utilities: geometry optimizers, coordinate systems, file I/O, and calculator interfaces. |
| SCINE Molassembler | <https://github.com/qcscine/molassembler> | BSD-3-Clause | Molecular graph and stereochemistry handling, including inorganic and organometallic structures. |
| AaronTools.py | <https://github.com/QChASM/AaronTools.py> | GPL-3.0 | Building and manipulating structures and handling QC input and output. |
| xyz2mol | <https://github.com/jensengroup/xyz2mol> | MIT | Bond order and connectivity perception from Cartesian coordinates. |
| chemfiles | <https://github.com/chemfiles/chemfiles> | BSD-3-Clause | C++ library with C, Python, Fortran, and Julia bindings for reading and writing chemistry structure and trajectory formats. |
| Open Babel | <https://github.com/openbabel/openbabel> | GPL-2.0 | General chemistry toolbox for converting among more than 100 file formats, including QC formats. |
| fundamental_constants | <https://github.com/vmagnin/fundamental_constants> | MIT | Fortran modules of CODATA fundamental physical constants generated from NIST data. |

## Wavefunction and density analysis

| Project | Repository | License | Description |
|---|---|---|---|
| libwfa | <https://github.com/libwfa/libwfa> | BSD-3-Clause | Wavefunction analysis library: excited-state analysis (natural transition orbitals, exciton analysis, etc.). |
| libvori | <https://brehm-research.de/libvori.php> | LGPL (version not stated) | Voronoi integration of electron densities and compressed volumetric trajectory output, used by CP2K. |
| ChemTools | <https://github.com/theochem/chemtools> | GPL-3.0 | Conceptual DFT and density-based descriptors (ELF, NCI, and others) for QC outputs. |
| DensPart | <https://github.com/theochem/denspart> | GPL-3.0 | Atoms-in-molecules density partitioning with the MBIS stockholder scheme. |
| HORTON-PART | <https://github.com/LISA-partitioning-method/horton-part> | GPL-3.0 | Hirshfeld, Hirshfeld-I, MBIS, LISA, and related atomic density partitioning. |
| HORTON | <https://github.com/theochem/horton> | GPL-3.0 | Python electronic structure library (HORTON 2) with molecular grids, partitioning, and ESP fitting; HORTON 3 was split into Grid, GBasis, and IOData. |
| AtomDB | <https://github.com/theochem/AtomDB> | GPL-3.0 | Database of neutral and charged atomic species (densities, energies) for promolecular models. |
| ORBKIT | <https://github.com/orbkit/orbkit> | LGPL-3.0 | Post-processing of wavefunctions (densities, orbitals, MO overlaps) from many file formats. |
| TheoDORE | <https://github.com/plasser-lab/theodore> | GPL-3.0 | Exciton and charge-transfer analysis of excited-state computations. |
| BaderKit | <https://github.com/SWeav02/baderkit> | BSD-3-Clause | Parallel grid-based Bader (QTAIM) charge analysis in Python. |
| pybader | <https://github.com/adam-kerrigan/pybader> | MIT | Threaded grid-based Bader charge analysis in Python. |
| resp | <https://github.com/cdsgroup/resp> | BSD-3-Clause | RESP electrostatic potential charge fitting (Psi4 plugin). |
| PsiRESP | <https://github.com/lilyminium/psiresp> | LGPL-3.0 | RESP/ESP charge fitting with intra- and intermolecular constraints, using Psi4. |

## General-purpose utilities

These Fortran utilities come from the electronic structure community.

| Project | Repository | License | Description |
|---|---|---|---|
| libfdf | <https://gitlab.com/siesta-project/libraries/libfdf> | BSD-3-Clause | Flexible Data Format input file parser. **[ESL]** |
| xmlf90 | <https://gitlab.com/siesta-project/libraries/xmlf90> | BSD-2-Clause | Fortran XML parsing and writing. |
| flook | <https://github.com/ElectronicStructureLibrary/flook> | MPL-2.0 | Fortran–Lua interface that lets programs be scripted in Lua. **[ESL]** |
| fdict | <https://github.com/zerothi/fdict> | MPL-2.0 | Fortran dictionary and type-free variable container. |
| Futile | <https://gitlab.com/l_sim/futile> | GPL-3.0 | Fortran utilities (I/O, memory management, profiling) from BigDFT. |
| FoX | <https://github.com/pietrodelugas/fox> | BSD-3-Clause | Fortran XML library derived from xmlf90, used by Quantum ESPRESSO. |
| ncdf | <https://github.com/zerothi/ncdf> | LGPL-3.0 | Fortran NetCDF API with handles and an MPI layer, used by SIESTA. |
| MPIFX | <https://github.com/dftbplus/mpifx> | BSD-2-Clause | Modern Fortran wrappers around MPI, from DFTB+. |
| ScaLAPACKFX | <https://github.com/dftbplus/scalapackfx> | BSD-2-Clause | Modern Fortran wrappers around ScaLAPACK, from DFTB+. |
| DeviceXlib | <https://gitlab.com/max-centre/components/devicexlib> | MIT | Fortran wrappers for GPU memory management and linear algebra, used by Quantum ESPRESSO and Yambo. |
| IRPF90 | <https://gitlab.com/scemama/irpf90> | GPL-2.0 | Fortran preprocessor for Implicit Reference to Parameters programming, used by Quantum Package. |
| mstore | <https://github.com/grimme-lab/mstore> | Apache-2.0 | Store of molecular structures for testing QC codes. |

## Related standalone tools

These are standalone programs rather than libraries that other programs link against or import.
They are listed because they produce data or do tasks that quantum chemistry programs commonly rely on,
such as generating pseudopotentials, analyzing densities, or acting as external solvers.

| Project | Repository | License | Description |
|---|---|---|---|
| ONCVPSP | <https://github.com/oncvpsp/oncvpsp> | GPL-3.0 | Generator for optimized norm-conserving Vanderbilt pseudopotentials. |
| APE | <https://gitlab.com/ape/ape> | GPL-2.0-or-later | Atomic Pseudopotentials Engine: generation and testing of nonrelativistic, scalar-relativistic, and fully relativistic norm-conserving pseudopotentials. |
| AtomPAW | <https://github.com/atompaw/atompaw> | GPL-3.0 | Generator of PAW atomic datasets for ABINIT, Quantum ESPRESSO, and others. |
| PseudoDojo | <https://github.com/abinit/pseudo_dojo> | LGPL-2.1-or-later | Framework for generating and validating pseudopotentials; hosts the PseudoDojo tables. |
| postg | <https://github.com/aoterodelaroza/postg> | GPL-3.0 | Exchange-hole dipole moment (XDM) dispersion model, evaluated from wavefunction files. This is a standalone program, not a library. |
| NECI | <https://github.com/fkfest/NECI_STABLE> | GPL-3.0 | Full configuration interaction quantum Monte Carlo (FCIQMC) and related stochastic methods, interfaced with OpenMolcas. |
| Dice | <https://github.com/sanshar/Dice> | GPL-3.0-or-later | Semistochastic heat-bath configuration interaction, used as a CASSCF solver through PySCF. |
| DoNOF | <https://github.com/DoNOF/DoNOFsw> | GPL-3.0 | Donostia Natural Orbital Functional software (Fortran) for PNOF calculations. |
| superdyson | <https://github.com/MBI-Theory/superdyson> | GPL-3.0 | Dyson orbitals and transition moments for general CI expansions. |
| KSSOLV 2.0 | <https://bitbucket.org/berkeleylab/kssolv2.0> | BSD-3-Clause-LBNL | MATLAB toolbox for plane-wave Kohn–Sham DFT with iterative diagonalization and SCF algorithms. |
| eOn | <https://github.com/TheochemUI/eOn> | BSD-3-Clause | Saddle point searches, NEB, and long-timescale dynamics coupled to external codes. |
| pyGSM | <https://github.com/ZimmermanGroup/pyGSM> | MIT | Growing string method for thermal and photochemical reaction paths in Python. |
| molecularGSM | <https://github.com/ZimmermanGroup/molecularGSM> | MIT | Single- and double-ended growing string reaction path searches in C++. |
| critic2 | <https://github.com/aoterodelaroza/critic2> | GPL-3.0 | QTAIM and NCI analysis of molecular and crystal densities from many electronic structure codes. |
| NCIPLOT | <https://github.com/juliacontrerasgarcia/NCIPLOT-4.0> | GPL-3.0-or-later | Noncovalent interaction (NCI) indices and integrals from densities and wavefunctions. |
| DensToolKit | <https://github.com/jmsolano/denstoolkit> | GPL-3.0 | Analysis of molecular electron densities and QTAIM quantities from wfn/wfx files. |

## Quantum chemistry programs that use these libraries

The list below is not complete. It shows how the libraries above are reused in
practice. Only open-source programs are listed.

| Program | Repository | License | Examples of reusable libraries used |
|---|---|---|---|
| Psi4 | <https://github.com/psi4/psi4> | LGPL-3.0 | Libint, Libxc, gau2grid, PCMSolver, ddX, CPPE, libefp, Libecpint, OptKing, simple-dftd3/DFT-D4, gCP, adcc (interface) |
| PySCF | <https://github.com/pyscf/pyscf> | Apache-2.0 | libcint/qcint, Libxc, XCFun, geomeTRIC, PyBerny, block2, CheMPS2 |
| GPU4PySCF | <https://github.com/pyscf/gpu4pyscf> | Apache-2.0 | PySCF, Libxc (CUDA-enabled fork), geomeTRIC, simple-dftd3/DFT-D4 (via pyscf-dispersion) |
| MPQC | <https://github.com/ValeevGroup/mpqc> | GPL-3.0-or-later | Libint, TiledArray, MADNESS, BTAS, SeQuant |
| CP2K | <https://github.com/cp2k/cp2k> | GPL-2.0 | Libint, Libxc, DBCSR, ELPA, SIRIUS, COSMA, libxsmm, spglib, DFT-D4, tblite, TREXIO |
| ERKALE | <https://github.com/susilehtola/erkale> | GPL-2.0-or-later | Libint, Libxc |
| HelFEM | <https://github.com/susilehtola/HelFEM> | BSD-3-Clause | Libxc |
| NWChem | <https://github.com/nwchemgit/nwchem> | ECL-2.0 | Libxc, Simint |
| ExaChem | <https://github.com/ExaChem/exachem> | Apache-2.0 | TAMM, Libint, GauXC |
| Forte | <https://github.com/evangelistalab/forte> | LGPL-3.0 | Psi4, Ambit |
| Serenity | <https://github.com/qcserenity/serenity> | LGPL-3.0 | Libint, Libxc, XCFun |
| eT | <https://gitlab.com/eT-program/eT> | GPL-3.0 | Libint, PCMSolver |
| VeloxChem | <https://github.com/VeloxChem/VeloxChem> | BSD-3-Clause | Libxc, geomeTRIC |
| Gator | <https://github.com/gator-program/gator> | GPL-3.0 | adcc, respondo, VeloxChem |
| OpenMolcas | <https://gitlab.com/Molcas/OpenMolcas> | LGPL-2.1 | Libxc, libwfa, CheMPS2 (interface) |
| DIRAC | <https://gitlab.com/dirac/dirac> | LGPL-2.1 | PCMSolver, XCFun, PElib |
| Dalton | <https://gitlab.com/dalton/dalton> | LGPL-2.1 | PElib |
| MRChem | <https://github.com/MRChemSoft/mrchem> | LGPL-3.0 | MRCPP, XCFun |
| QUICK | <https://github.com/merzlab/QUICK> | MPL-2.0 | Libxc |
| Quantum Package | <https://github.com/QuantumPackage/qp2> | AGPL-3.0 | TREXIO |
| xtb | <https://github.com/grimme-lab/xtb> | LGPL-3.0 | tblite, DFT-D4 |
| DFTB+ | <https://github.com/dftbplus/dftbplus> | LGPL-3.0-or-later | ELSI, libMBD, tblite, DFT-D4 |
| Octopus | <https://gitlab.com/octopus-code/octopus> | GPL-3.0 | Libxc, libvdwxc, ELPA, spglib, libpspio |
| SIESTA | <https://gitlab.com/siesta-project/siesta> | GPL-3.0 | libGridXC, Libxc, ELSI, ELPA, libfdf, libPSML, xmlf90, flook |
| BigDFT | <https://gitlab.com/l_sim/bigdft-suite> | GPL-2.0 | PSolver, Futile, Libxc |
| ABINIT | <https://github.com/abinit/abinit> | GPL-3.0 (some parts Apache-2.0) | Libxc, ELPA, Wannier90, libPSML |
| Quantum ESPRESSO | <https://gitlab.com/QEF/q-e> | GPL-2.0-or-later | Libxc, ELPA, SIRIUS, Wannier90 |
| GPAW | <https://gitlab.com/gpaw/gpaw> | GPL-3.0-or-later | Libxc, libvdwxc, ELPA |
| DFTK.jl | <https://github.com/JuliaMolSim/DFTK.jl> | MIT | Libxc, spglib |

## Other catalogs

- [CECAM Electronic Structure Library (ESL)](https://esl.cecam.org/) and its
  [software list](https://esl.cecam.org/en/software/index.html).
- ESL development sites on [GitLab](https://gitlab.com/ElectronicStructureLibrary)
  and [GitHub](https://github.com/ElectronicStructureLibrary).
- [MolSSI](https://molssi.org/) software projects.

## Contributing

Additions and corrections are welcome as pull requests or issues. For each
new entry, please include:

1. the project name,
2. the SPDX identifier of its license,
3. the link to the upstream repository (not a mirror or a fork, unless the
   original is gone),
4. a one-sentence description of what the project does,

and put it in the most fitting section. The project must be open source.
Libraries that other programs can link against or import go in the topical
sections. Standalone programs go in
[Related standalone tools](#related-standalone-tools).
