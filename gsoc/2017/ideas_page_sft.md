[CERN-SFT GSoC 2017 ideas page ]{property="dc:title"} {#cern-sft-gsoc-2017-ideas-page .page-header}
=====================================================

**CERN-SFT** has successfully participated in the Google Summer of Code
program since 2011, and we are taking part again in 2017! This year, we
are applying under the umbrella organization of the [HEP Software
Foundation](http://hepsoftwarefoundation.org/) (HSF). While in this page
we will include the project ideas for CERN-SFT, you can find information
about other HSF-related projects at the new [HSF GSoC
website](http://hepsoftwarefoundation.org/activities/gsoc.html).

At CERN-SFT, we intend to offer three options. Please pick one of the
project ideas grouped into categories, take a look at the section
dedicated to [\'Blue
sky\'](https://ep-dep-sft.web.cern.ch/node/221195/#bluesky) projects, or
propose your own great idea for this summer. We are looking forward to
hearing about **your** proposals. A list of our mentors (and their areas
of expertise) can be found
[here](https://ep-dep-sft.web.cern.ch/node/221195#mentors).\
\
We encourage students who plan to apply to [**contact
us**](https://ep-dep-sft.web.cern.ch/node/221195#contact)  about their
interests and explain their project ideas as early as possible. Our
experience from past GSoCs was that initial student applications either
need to be reworked in close collaboration with a future mentor, or at
least can benefit from feedback and discussion. **Please do not forget
to provide us with some relevant information about yourself** (for
example CV, past projects, personal page or blog, LinkedIn profile,
Github account, etc.).\
\
Before submitting an application please consult the [[official GSoC
FAQ]{.underline}](https://developers.google.com/open-source/gsoc/faq)
where you can find some good advice on writing a successful application.
The application should be submitted through the [[GSoC Web
page]{.underline}](https://summerofcode.withgoogle.com/) before **April
3, 2017**.

[Project ideas]{#project}
=========================

ROOT Projects
=============

Big Data Tools for Physics Analysis
-----------------------------------

[Spark](http://spark.apache.org) is an open-source software framework
for large-scale big data processing on clusters. While it has become
mainstream in industry, its adoption in the field of physics is still in
its infancy. This project intends to explore the use of Spark for
physics analysis at CERN, and in particular its interplay with two
technologies: (i) [ROOT,](http://root.cern) a software toolkit widely
used for high-energy physics analysis, and (ii) the
[Jupyter](http://jupyter.org) notebooks, a well-known interface for
interactive analysis.

The main development of this project will focus on making it easier to
manage Spark computations from a Jupyter notebook. A plugin will be
developed so that notebook users can monitor the status of a Spark job
submitted from a notebook cell, and even cancel it if necessary. The
main use case of the plugin will be a parallel physics analysis with
ROOT and Spark, with a possible second use case in distributed machine
learning. The plugin can then be integrated into the
[SWAN](http://swan.web.cern.ch) notebook pilot service at CERN.

[**Task ideas**:  ]{.s1}

-   [Creation of a testbed for submission of Spark jobs from a Jupyter
    notebook]{#docs-internal-guid-0add3984-d69a-031b-db36-f1810be0f3b2}
-   Design and implementation of a plugin to monitor Spark jobs from a
    notebook
    -   Display information such as progress bars, task statistics and
        errors
    -   Allow to cancel ongoing Spark jobs
-   [Use cases: apply the plugin to a couple of distributed Spark
    applications]{#docs-internal-guid-0add3984-d69b-9d24-3c35-4013ed6fdbee}
    -   [ROOT physics
        analysis]{#docs-internal-guid-0add3984-d69b-c790-bb25-008a5c9c806d}
    -   [Machine
        learning]{#docs-internal-guid-0add3984-d69b-e68c-78e2-89c3f2242b5e}
-   [Tests on CERN IT infrastructure (Spark
    clusters)]{#docs-internal-guid-0add3984-d69c-1a48-a5ae-ef20713c9a92}
-   [Integration of the plugin into the SWAN notebook service at
    CERN]{#docs-internal-guid-0add3984-d69c-4263-ba95-23f52b6f7e6c}

[**Expected results**: ]{.s1}working implementation of the notebook
plugin to manage ROOT-Spark jobs\
\
[**Requirements**: ]{.s1}[Spark, Python, JavaScript, Jupyter
notebooks]{#docs-internal-guid-0add3984-d69e-49c8-fc43-1fe22c7691ca}\
\
**Mentors**: Enric Tejedor (etejedor\@cern.ch), Danilo Piparo
(danilo.piparo\@cern.ch), Prasanth Kothuri (prasanth.kothuri\@cern.ch),
Kacper Surdy (kacper.surdy\@cern.ch)\
\
**Links:**\
[http://root.cern](https://root.cern/)\
[http://spark.apache.org](http://spark.apache.org/)\
[http://jupyter.org](http://jupyter.org/)

Improvements in vectorization and parallelization of ROOT Math libraries {#parvec}
------------------------------------------------------------------------

HEP software applications require a large amount of computing resources,
and their computing performance is an important issue, in particular to
satisfy their ever-increasing requirements. Since 2005, we no longer
benefit from the automatic gains due to the increase in processor clock
frequency. The growth in the number of transistors on a chip now
translates into an increase in the number of cores rather than an
improvement in the performance of each core. To tackle these challenges,
the ROOT project has been undertaking a re-engineering to adapt its Math
libraries to run in multiple concurrent threads and make an efficient
use of the vector units (SIMD).\
\
The chosen candidate will continue the re-engineering made on
vectorization of the Mathematical function interfaces and the fitting
functions plus parallelization of the last one.

[**Task ideas:** ]{.s1}

-   Completion of parallelization and vectorization of all the fitting
    methods available in ROOT. 
-   Adapt gradient function interfaces for thread-based parallelization
    and vectorization.
-   Vectorization of TFormula and "predefined ROOT functions".
-   Vectorization of most used mathematical and statistical functions in
    ROOT::Math and TMath.

**Expected results**: For each one of these areas the student will be
expected to provide tests, reliable benchmarks and speed-up results. At
the end of GSoC, ROOT should be capable of fitting in parallel and
making use of vectorization to evaluate both user-specified and
predefined formulas.\
\
[**Requirements**: ]{.s1}Strong knowledge of C++11; being able to
produce clean, reliable code; No need for background in math, although
basic understanding of equations is expected. Basic notions of
vectorization are a plus.

**Mentors**: [Xavier Valls](mailto:xavier.valls.pla@cern.ch), [Lorenzo
Moneta](mailto:lorenzo.moneta@cern.ch)\
\
**Links:** \
[ROOT](https://root.cern/)\
[VecCore](https://github.com/amadio/vecgeom)\
[Vc](https://github.com/VcDevel/Vc)

Enhance C-Reduce to work with ROOT
----------------------------------

[C-Reduce](https://github.com/csmith-project/creduce) is a tool which
aims to reduce bug reports. It transforms user\'s source files to make
them as minimal as possible. Minimalistic bug reproducers are easy to
debug and convert into regression tests. C-Reduce is fairly mature and
well adapted to minimize crashes in compilers. The project will be
mainly focused towards making C-Reduce easier to use with ROOT and it\'s
interactive C++ interpreter cling.

[**Task ideas and expected results**:  ]{.s1}

-   Extend C-Reduce to be able to reduce easily ROOT bug reports.
-   Optionally extend C-Reduce to minimize ROOT\'s data files.
-   Implement tests for all the realized functionality.
-   Prepare a final poster of the work and be ready to present it

[**Requirements**: ]{.s1}Intermediate level of C++, some experience with
Clang

**Mentors**: [Vassil
Vassilev](mailto:sft-gsoc-AT-cern-dot-ch?subject=Your%20Project%20Title)​

Message Parsing Interface for ROOT (ROOTMpi)
--------------------------------------------

[Project Description: By standardizing the way different machines
communicate during a running process, we can analyze bigger chunks of
data in less time. ROOT MPI allows to communicate ROOT\'s native objects
on top of the C/C++ raw data types. ROOT\'s serialization methods and
optimal design of the new C++ standard permits the user to focus on the
algorithm instead of the low-level syntax. ]{.s1}

[**Task ideas**:  ]{.s1}

-   Extend existing communication schemas
-   Write support for MPI files (may consider some design or idea to
    integrate it to TFile)
-   Write a memory window, shared memory and RMA support
-   Checkpoint support at least in OpenMpi and Mpich
-   Improve the error handler system and messages in the output.
-   User tools:
    -   Write a profiling tool
    -   Write a benchmarking module
    -   Integrate valgrind command to ROOTMpi command for debug

::: {.p1}
[**Expected results**:  ]{.s1}
:::

-   Working implementation with tests and documentation
-   A machine learning example integrated with TMVA that uses ROOTMpi
-   Performance comparison with a basic example between ROOTMpi and
    Proof

[**Requirements**: ]{.s1}advanced skills in C/C++, experience in
parallel programming with MPI

**Mentors**: [Omar
Zapata](mailto:sft-gsoc-AT-cern-dot-ch?subject=Multi-Target%2FObjective%20Regression%20using%20Machine%20Learning%20for%20Particle%20Physics)[,
]{.s1}[Lorenzo
Moneta](mailto:sft-gsoc-AT-cern-dot-ch?subject=Multi-Target%2FObjective%20Regression%20using%20Machine%20Learning%20for%20Particle%20Physics)[
]{.s1}\
\
[**Source code**:  [[ROOT
Mpi]{.s2}](https://github.com/oprojects/root/tree/master-rmpi/mpi)]{.s1}\
 

Integration of Apache Parquet reading capabilities in ROOT data analyses
------------------------------------------------------------------------

ROOT is a C++ software toolkit widely used for high-energy physics (HEP)
analyses. It specializes in reading and writing large amounts of data
efficiently, using a custom storage format known as ROOT files.
TDataFrame is a new tool that allows ROOT users to quickly and
efficiently setup data analyses through a high-level declarative syntax
(i.e. functional chains).\
The aim of this project is to seamlessly interface TDataFrame with
common storage formats other than ROOT files, such as Apache Parquet.
Users of TDataFrame will be able to transparently read data stored in
these formats with minimal or no change required to the analysis code.

[**Task ideas and expected results**:  ]{.s1}

-   design of new internal facilities for ROOT to read from third-party
    file formats such as Apache Parquet
-   design of a user-transparent interface to access these facilities
    through TDataFrame
-   implementation, integration and testing of this interface in ROOT\'s
    TDataFrame, to make this feature readily available to users

[**Requirements**: ]{.s1}strong C++ and C++11 skills, familiarity with
the Apache Parquet file formats. Familiarity with the ROOT software
library is highly desirable.

**Mentors**: [Enrico
Guiraud](mailto:enrico.guiraud@cern.ch?subject=ROOT%20integration%20with%20Apache%20Parquet)​,
[Danilo
Piparo](mailto:danilo.piparo@cern.ch?subject=ROOT%20integration%20with%20Apache%20Parquet)​

[**Links**: ]{.s1}

-   [ROOT](https://root.cern.ch/)
-   [TDataFrame](https://root.cern.ch/doc/master/group__dataframe.html)
-   [Apache Parquet](https://parquet.apache.org/)

::: {.p1}
 
:::

Machine Learning Projects {#machine-learning-projects .p1}
=========================

Machine Learning Project 1. Convolutional Deep Neural Networks on GPUs for Particle Physics Applications
--------------------------------------------------------------------------------------------------------

[Project Description: Toolkit for Multivariate Analysis (TMVA) is a
multi-purpose machine learning toolkit integrated into the ROOT
scientific software framework, used in many particle physics data
analysis and applications. Last year we have expanded TMVA\'s
capabilities to include feed-forward deep learning library (DNN) that
supports interactive training on GPUs. This summer we would like to
expand the toolkit with optimized convolutional deep neural networks
(CNN). CNNs have very promising applications in particle physics such as
particle and event classification, imaging calorimetry and particle
tracking, allowing physicists to use new techniques to identify
particles and search for new physics. ]{.s1}

[**Task ideas and expected results**: ]{.s1}

-   Production-ready convolutional deep learning library
-   Design of first-stage filters
-   Support for GPUs for training
    -   integration with existing low-level interface designed for the
        DNN library

[**Requirements**: strong C++ skills, solid knowledge of deep learning,
understanding of convolutional networks, familiarity with GPU interfaces
a plus]{.s1}

**Mentors**: [Sergei
Gleyzer](mailto:sft-gsoc-AT-cern-dot-ch?subject=Convolutional%20Deep%20Neural%20Networks%20on%20GPUs%20for%20Particle%20Physics)​
and [Lorenzo
Moneta](mailto:sft-gsoc-AT-cern-dot-ch?subject=Convolutional%20Deep%20Neural%20Networks%20on%20GPUs%20for%20Particle%20Physics)\
\
**Web page:**  [TMVA](http://root.cern.ch/tmva)[ ]{.s1}\
\
**Links:**\
[http://root.cern\
http://root.cern/tmva](https://root.cern/)\
\
[**Source code**: 
[[DNN]{.s2}](https://github.com/root-mirror/root/tree/master/tmva/tmva/inc/TMVA/DNN)]{.s1}

Machine Learning Project 2. Multi-target Regression for Particle Physics
------------------------------------------------------------------------

[Project Description: Toolkit for Multivariate Analysis (TMVA) is a
multi-purpose machine learning toolkit integrated into the ROOT
scientific software framework, used in many particle physics data
analysis and applications. We have recently expanded the regression
(continuous function estimation) capabilities of the toolkit to include
multiple loss-functions. One important open area of machine learning
research is multi-target (or multi-objective) regression. In this
project, the goal is to learn to estimate multiple continuous target
functions at once. This summer we would like to expand the toolkit
capabilities in multi-target/multi-objective function estimation. This
has promising applications in particle physics research, such as
particle transformations, fast detector simulation and many more,
enabling particle physicists to make faster discoveries. ]{.s1}

[**Task ideas and expected results**: ]{.s1}

-   Extension of existing single-target estimation/regression
    capabilities to multiple targets
-   Primarily targeting Boosted Decision Trees and Deep Neural Networks

[**Requirements**: strong C++ skills, understanding of machine learning
and in particular, its application to function
estimation/regression]{.s1}

**Mentors**: [Sergei
Gleyzer](mailto:sft-gsoc-AT-cern-dot-ch?subject=Multi-Target%2FObjective%20Regression%20using%20Machine%20Learning%20for%20Particle%20Physics)​,
[Lorenzo
Moneta](mailto:sft-gsoc-AT-cern-dot-ch?subject=Multi-Target%2FObjective%20Regression%20using%20Machine%20Learning%20for%20Particle%20Physics)[,
]{.s1}[Omar
Zapata](mailto:sft-gsoc-AT-cern-dot-ch?subject=Multi-Target%2FObjective%20Regression%20using%20Machine%20Learning%20for%20Particle%20Physics)\
\
**Web page:**  [TMVA](http://root.cern.ch/tmva)\
\
**Links:**\
[http://root.cern\
http://root.cern/tmva](https://root.cern/)\
\
[**Source code**: 
[[TMVA]{.s2}](https://github.com/root-mirror/root/tree/master/tmva)]{.s1}

Additional Machine Learning Project Ideas and Areas of Interest
---------------------------------------------------------------

[Project Description: Toolkit for Multivariate Analysis (TMVA) is a
multi-purpose machine learning toolkit integrated into the ROOT
scientific software framework, used in many particle physics data
analysis and applications. The following are also areas of interest with
impactful applications to particle physics]{.s1}

[**Task ideas and expected results**: ]{.s1}

-   Unsupervised learning: deep auto-encoders, restricted boltzmann
    machines (RBMs)
-   Deep learning: recurrent neural networks (RNNs), LTSM,
    complex-valued neural networks

[**Requirements**: strong C++ skills, good understanding of machine
learning algorithms]{.s1}

**Mentors**: [Sergei
Gleyzer](mailto:sft-gsoc-AT-cern-dot-ch?subject=Other%20Machine%20Learning%20Projects%20in%20TMVA)​,
[Lorenzo
Moneta](mailto:sft-gsoc-AT-cern-dot-ch?subject=Other%20Machine%20Learning%20Projects%20in%20TMVA)​,
[Omar
Zapata](mailto:sft-gsoc-AT-cern-dot-ch?subject=Other%20Machine%20Learning%20Projects%20in%20TMVA)​,
[Stefan
Wunsch](mailto:sft-gsoc-AT-cern-dot-ch?subject=Other%20Machine%20Learning%20Projects%20in%20TMVA)​,
[Enrico
Guiraud](mailto:sft-gsoc-AT-cern-dot-ch?subject=Other%20Machine%20Learning%20Projects%20in%20TMVA)\
\
**Web page:**  [TMVA](http://root.cern.ch/tmva)\
\
**Links:**\
[http://root.cern\
http://root.cern/tmva](https://root.cern/)\
\
[**Source code**: 
[[TMVA]{.s2}](https://github.com/root-mirror/root/tree/master/tmva)]{.s1}

Sixtrack Numerical Accelerator Simulation​ Projects
===================================================

[SixTrack](http://cern.ch/sixtrack) is a software for simulating and
analysing the trajectory of high energy particles in accelerators. It
has been used in the design and optimization of the LHC and is now being
used to design the High-Luminosity LHC (HL-LHC) upgrade that will be
installed in the next decade. Sixtrack has been adapted to take
advantage of large scale volunteer computing resources provided by
the [LHC\@Home](http://sixtrack.web.cern.ch/SixTrack/www/cern.ch/lhcathome) project.
It has been engineered to give the exact same results after millions of
operations on several, very different computer platforms. The source
code is written in Fortran, and is pre-processed by two programs that
assemble the code blocks and provide automatic differentiation of the
equation of motions. The code relies on the [crlibm[[ (link is
external)]{.element-invisible}]{.ext}](http://lipforge.ens-lyon.fr/www/crlibm/){.ext} library,
careful arrangement of parenthesis, dedicated input/output and selected
compilation flags for the most common compilers to provide identical
results on different platforms and operating systems. An option enables
the use of the [Boinc[[ (link is
external)]{.element-invisible}]{.ext}](http://boinc.berkeley.edu/){.ext} library
for volunteer computing. A running environment SixDesk is used to
generate input files, split simulations for [LHC\@Home[[ (link sends
e-mail)]{.element-invisible}]{.mailto}](mailto:LHC@Home){.mailto} or
CERN cluster and collect the results for the user. SixTrack is licensed
under LGPLv2.1.

A strong background in computer science and programming languages as
well the interest to understand computational physics methods
implemented in the code are sought. The unique challenge will be offered
to work with a high-performance production code that is used for the
highest energy accelerator in the world - and thus the code\'s
reliability and backward compatibility cannot be compromised. There will
be the opportunity to learn about methods used in simulating the motion
of particles in accelerators.

Optimize and Integrate Standalone Tracking Library (SixTrackLib)
----------------------------------------------------------------

**Description**: Optimize data structure and source code of a standalone
tracking library in C in order to take advantage of automatic
vectorization offered by GCC and CLang for CPU and explicit
vectorization from OpenCL and CUDA for GPU. The code must then be linked
with the legacy SixTrack code and replace the inner loop.

**Expected results:** Demonstrate that the C code can run existing
simulation at the same or faster speed on CPU and can saturate the
computing capacity of GPU, while keeping bit-level identical results.

**Mentors:** [Riccardo De Maria](mailto:Riccardo.De.Maria@cern.ch),
[Giovanni Iadarola](mailto:giovanni.iadarola@cern.ch)

**Requirements**: Experience with Fortran, C, OpenCL, CUDA,
vectorization techniques.

**Web Page:** [cern.ch/sixtrack](http://cern.ch/sixtrack)

**Source Code:**
[github.com/SixTrack/SixTrack](http://github.com/SixTrack/SixTrack)

New physics models
------------------

**Description:** Implement, test and put in production a new solvers for
generic RF-mulitpole,  combined function magnets and radiation effects.

**Expected results:** The user can build accelerator simulations with
more accurate models for low energy machines and/or machines with
radiation effects.

**Mentors:** [Riccardo De Maria](mailto:Riccardo.De.Maria@cern.ch),
[Kyrre Sjobak](mailto:kyrre.ness.sjoebaek@cern.ch)

**Requirements:** Fortran, calculus, accelerator physics.

**Web Page:** [cern.ch/sixtrack](http://cern.ch/sixtrack)

**Source Code:**
[github.com/SixTrack/SixTrack](http://github.com/SixTrack/SixTrack)

Code Benchmark and Consolidation
--------------------------------

**Description:** Benchmark simulation size against result throughput on
different architectures and identify I/O, memory and CPU bottleneck.
Evaluate the impact of merging branches on these performance figures.

**Expected results:** An analysis of result throughput depending on the
architecture, identification of bottlenecks in the source code,
assessment on impact of branches.

**Mentors:** [Riccardo De Maria](mailto:Riccardo.De.Maria@cern.ch),
[Kyrre Sjobak](mailto:kyrre.ness.sjoebaek@cern.ch)

**Requirements:** Fortran, calculus, accelerator physics.

**Web Page:** [cern.ch/sixtrack](http://cern.ch/sixtrack)

**Source Code:**
[github.com/SixTrack/SixTrack](http://github.com/SixTrack/SixTrack)

Continuous integration and test coverage with CDash and coverity
----------------------------------------------------------------

**Description:** SixTrack building system has been recently updated
using CMake and integrate in CDash. This enables us to implement best
practices in testing by improving the test coverage, test speed and
nightly test cycles.

**Expected results:** Approaching 100% code coverage with test and at
the same time reducing testing running time. Implement automatic
triggers for each commit that will launch the test suite and CDash
update.

**Mentors:** [Riccardo De Maria](mailto:Riccardo.De.Maria@cern.ch),
[Kyrre Sjobak](mailto:kyrre.ness.sjoebaek@cern.ch)

**Requirements:** Fortran, calculus, accelerator physics.

**Web Page:** [cern.ch/sixtrack](http://cern.ch/sixtrack)

**Source Code:**
[github.com/SixTrack/SixTrack](http://github.com/SixTrack/SixTrack)

Detector simulation projects
============================

[Optimisation of GeantV HPC workload balancing by use of unsupervised machine learning]{#docs-internal-guid-bdc75105-fb4d-5218-43dc-6aeac8fd7f3f}
-------------------------------------------------------------------------------------------------------------------------------------------------

[Description:]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}

[GeantV is a project aiming to deploy massively parallel detector
simulation workloads from workstations to distributed computing
resources, including HPC clusters. The GeantV concurrency model\[1\]
exploits optimally a single node using threads and features such as
vectorization and machine topology discovery. We are developing a model
to adapt GeantV to make efficient use also of HPC resources, minimizing
the processing tails due to the inhomogeneity of distributed
environments. The goal of the summer project is to test and optimize the
HPC deployment model, using the idea of optimized job scheduling  based
on evolutionary tuning of GeantV job parameters and spectral
clustering\[3\] of HPC resources in optimal subregions based on a graph
representation of
them.]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}

 

[Task ideas:]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}

-   [Implement multi-tier master-worker communication layer using MPI or
    alternative communication protocol (ZeroMQ or
    others).]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}
-   [Design and implement multi-layer graph workflow\[2\] for HPC layer,
    integrate spectral clustering \[3\] in job processing
    schema.]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}
-   [Deploy and test the code on a cluster, adding evolutionary tuning
    module and deploy spectral clustering \[4\].
    ]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}

[Expected deliverables: Deployment of GeantV in a cluster, demonstrating
improvement in workload balancing compared to naive workload
deployment.]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}

[Optimization based on ML techniques demonstrating improvements with
respect to the initial heuristic-based
implementation.]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}

 

[Desired programming experience:
C/C++]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}

 

[Desired knowledge: HPC, linear algebra, machine learning
algorithms]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}

\
[Link to relevant websites:
[geant.web.cern.ch](http://geant.web.cern.ch)\
\
**Mentors:** [Andrei
Gheata](mailto:andrei.gheata@cern.ch?subject=Interested%20in%20optimisation%20of%20GeantV%20HPC%20workload%20balancing),
[Oksana Shadura\
​](mailto:oksana.shadura@cern.ch?subject=Interested%20in%20optimisation%20of%20GeantV%20HPC%20workload%20balancing)]{#docs-internal-guid-bdc75105-fb4f-c26e-7cfd-92a5eea9d3b5}

[References: ]{#docs-internal-guid-bdc75105-0484-d433-3db3-274c0f480ccd}

1.  [Apostolakis, J and Bandieramonte, M and Bitzes, G and Brun, R and
    Canal, P and Carminati, F and Licht, JC De Fine and Duhem, L and
    Elvira, VD and Gheata, A and others, Adaptive track scheduling to
    optimize concurrency and vectorization in GeantV, Journal of
    Physics: Conference Series, 608, 1, 012003, 2015, IOP
    Publishing]{#docs-internal-guid-bdc75105-0484-d433-3db3-274c0f480ccd}

2.  [Mikko Kivelä, Alex Arenas, Marc Barthelemy, James P. Gleeson, Yamir
    Moreno, Mason A. Porter; Multilayer networks. J Complex Netw 2014; 2
    (3): 203-271. doi:
    10.1093/comnet/cnu016]{#docs-internal-guid-bdc75105-0484-d433-3db3-274c0f480ccd}

3.  [Andrew Y. Ng, Michael I. Jordan, and Yair Weiss. 2001. On spectral
    clustering: analysis and an algorithm. In Proceedings of the 14th
    International Conference on Neural Information Processing Systems:
    Natural and Synthetic (NIPS\'01), T. G. Dietterich, S. Becker,
    and Z. Ghahramani (Eds.). MIT Press, Cambridge, MA, USA, 849-856.
    ]{#docs-internal-guid-bdc75105-0484-d433-3db3-274c0f480ccd}

4.  [Xiaowen Dong and Pascal Frossard and Pierre Vandergheynst and
    Nikolai Nefedov, Clustering with Multi-Layer Graphs: A Spectral
    Perspective, CoRR, abs/1106.2233, 2011,
    http://arxiv.org/abs/1106.2233]{#docs-internal-guid-bdc75105-0484-d433-3db3-274c0f480ccd}

[**New error control methods for integration of trajectories**]{.s1} {#new-error-control-methods-for-integration-of-trajectories .p1}
--------------------------------------------------------------------

[Geant4 and GeantV use Runge-Kutta methods to integrate the motion of
charged particles in a non-uniform electromagnetic field.  Methods must
provide good integration accuracy for the integration and to cost a
minimum of computation time.  Integration is used to identify the
intersection point between the curved track and the volume
boundaries.  Due to the large number of steps and the cost of the
evaluations of the field, the integration and intersection are a
performance critical part of detector simulation. Recent work has
introduced new RK methods which reduce the number of field evaluations
required, and has the potential to decreased the computation time.]{.s1}

[**Task ideas:**]{.s1}

-   [Introduce new methods for the control of integration error of
    existing integration Runge Kutta ]{.s1}methods[, ]{.s1}
-   [Create heuristics for choosing an appropriate method (helix, RK of
    particular order, Burlich/Stoer), using knowledge of the accuracy
    requirements and the variation of the derivative in the proposed
    step.]{.s1}

[**Expected results: **Working implementation of a) improved alternative
error control methods for RK integration, and/or b) integration
methods which combine different methods, e.,g. RK methods of different
order for improved performance.]{.s1}

[**Requirements**: This project requires prior exposure to Numerical
Analysis and familiarity with either C++, C or Java programming.
 Exposure to either numerical methods for solving Ordinary Differential
equations (ODEs) or tools for analysing data such as ROOT or R will be
valuable. Both programming skill and knowledge of numerical methods
for ODEs will be improved by undertaking this project.]{.s1}

[**Mentor**: [[John Apostolakis​](mailto:sft-gsoc-AT-cern-dot-ch?subject=Field%20integration)\
**Web site**: http://cern.ch/geant4\
**Source
code**: ]{.s3}]{.s2}https://github.com/jonapost/field\_propagation\
\
Using Pseudo-random numbers repeateably in a fine-grain multithreaded
simulation

**[Description:]{.s1}**

Particle transport Monte Carlo simulations are a key tool for High
Energy Physics experiments, including the LHC experiments at CERN. All
Monte Carlo (MC) simulations depend vitaly on Pseudo-Random Number
Generators (PRNGs) used to sample many distributions. Each LHC
experiments generates 5-10 Billion sampled physics events a year using
around 10\^18 sampled values from PRNGs. PRNGs take 1-5% of CPU time.
PRNGs used must possess very large periods, fast execution, the ability
to create a large number of streams, and very good correlation
properties between streams and sampled values. It must be possible to
reproduced a simulated event any time, for reexamination or debugging.

[**Task ideas and expected results**:  ]{.s1}

-     Create a prototype that changes the use of random number
    generation in a Geant simulation so that the RNG state is associated
    with each track:
    -   When a secondary is created, attach to it either a seed or a new
        state for PRNG, for use in that track.
    -   Participating in extending the interface different PRNGs to
        provide different ways to choose the state of PRNG for a
        secondary
    -   Create implementations including MCRGs, counter-based PRNGs and
        novel PRNGs with guarantees of stream independence.

[**Requirements**: ]{.s1}programming in C/C++ or Java at least for class
projects is required. Use of Linux/Unix, cmake and/or a coding IDE
(Eclipse, Xcode) will be assets.\
Knowledge gained: use of Pseudo-Random Number Generators and state of
the art of PRNGs.

**Mentors**: [John
Apostolakis](mailto:sft-gsoc-AT-cern-dot-ch?subject=Using%20Pseudo-random%20number%20repeatably%20in%20a%20fine-grain%20%20multithreaded%20simulation)​,
[Sandro
Wenzel](mailto:sft-gsoc-AT-cern-dot-ch?subject=Using%20Pseudo-random%20number%20repeatably%20in%20a%20fine-grain%20%20multithreaded%20simulation)\
\
**Web page:**  [Geant4](https://cern.ch/geant4)

[**Source code**:  ]{.s1}\"<https://github.com/Geant4/geant4/>\
\
References:\
 

Pseudo-Random Number Generator Projects
=======================================

Extend the TestU01 suite for PRNGs
----------------------------------

**Description**: \
The TestU01 suite is an established suite of empirical tests for
pseudorandom number generators. It has been used since 200x as a litmus
test for potential PRNG algorithms and implementations.  Given the power
of current computers, the length of the tests only probes number
sequences which can be generated in tens of minutes on the fastest
machines. The idea of this project is to select a larger set of
configurations, improve the implementations and create a new
\'standard\' for tests of PRNGs.\
\
**Potential project topics** \
1. Creating a 64-bit version of the software, so that more than 32 bits
of the output values are tested.\
2. Use faster algorithms ot improve the implementation of certain
tests.\
3. Design and implement specific tests for parallel RNGs.\
4. Construct a parallel version of TestU01, that can run on parallel
 processors. \
\
References: \
\[1\] P. L\'Ecuyer and R. Simard. TestU01: A C library for empirical
 testing of random number \
generators. ACM Transactions on Mathematical Software, 33(4):Article 22,
 August 2007. \
**Mentors**: [John Apostolakis](mailto:sft-gsoc-AT-cern-dot-ch?subject=Extend%20the%20TestU01%20suite%20for%20PRNGs)​, [Pierre
L\'Ecuyer](mailto:sft-gsoc-AT-cern-dot-ch?subject=Extend%20the%20TestU01%20suite%20for%20PRNGs)

**Web page:**[ ]{.s1}<http://simul.iro.umontreal.ca/testu01/tu01.html>\
[**Source
code**:  ]{.s1}<http://simul.iro.umontreal.ca/testu01/tu01.html>

 

Other Projects
==============

 Extend clad - The Automatic Differentiation
-------------------------------------------

In mathematics and computer algebra, automatic differentiation (AD) is a
set of techniques to numerically evaluate the derivative of a function
specified by a computer program. Automatic differentiation is an
alternative technique to Symbolic differentiation and Numerical
differentiation (the method of finite differences).
 [CLAD ](https://C-Reduce%20https://github.com/vgvassilev/clad) is based
on Clang which will provide the necessary facilities for code
transformation. The AD library is able to differentiate non trivial
functions, to find a partial derivative for trivial cases and has good
unit test coverage. There was a proof-of-concept implementation for
computation offload using OpenCL.

[**Task ideas and expected results**:  ]{.s1}

-   The student should teach AD how to generate OpenCL/CUDA code
    automatically for a given derivative.
-   The implementation should be very well tested and documented.
    Prepare a final poster of the work and be ready to present it.

[**Requirements**: ]{.s1}Advanced C++, Clang abstract syntax tree (AST),
CUDA/OpenCL basic math

**Mentors**: [Vassil
Vassilev](mailto:sft-gsoc-AT-cern-dot-ch?subject=Your%20Project%20Title)​\
 

[\'Blue sky\' ideas]{#bluesky}
==============================

 

[**Mentors**]{#mentors}
=======================

Here is the list of our mentors and their areas of expertise:

-   [Sergei
    Gleyzer](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%20general)
    (programme administrator; Machine Learning)
-   [Enric Tejedor
    Saavedra](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%20general)
    (programme administrator; ROOT, Spark)
-   [Lorenzo
    Moneta](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%20general)
    (ROOT, Machine Learning)
-   [Omar Zapata
    Mesa](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%20general)
    (Machine Learning, MPI)
-   [Stefan
    Wunsch](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%20general)
    (Machine Learning)
-   [Enrico
    Guiraud](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%20general)
    (Machine Learning)
-   [Danilo
    Piparo](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%20general)
    (ROOT, Spark)
-   [Prasanth
    Kathuri](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%20general)
    (Spark)
-   [Kacper
    Surdy](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%20general)
    (Spark)
-   [Xavier Valls](mailto:xavier.valls.pla@cern.ch) (ROOT)
-   [Riccardo De Maria](mailto:Riccardo.De.Maria@cern.ch) (Sixtrack)
-   [Giovanni Iadarola](mailto:giovanni.iadarola@cern.ch) (Sixtrack)
-   [Kyrre Sjobak](mailto:kyrre.ness.sjoebaek@cern.ch) (Sixtrack)
-   [Vassil Vassilev](mailto:vvasilev@cern.ch) (ROOT, CLAD, C-Reduce)
-   [Andrei Gheata](mailto:andrei.gheata@cern.ch?subject=Interested%20in%20detector%20simulation%20projects) (Detector
    simulation)
-   [John
    Apostolakis](mailto:andrei.gheata@cern.ch?subject=Interested%20in%20detector%20simulation%20projects) (Detector
    simulation/Pseudo-Random Number Generators)
-   [Sandro
    Wenzel](mailto:andrei.gheata@cern.ch?subject=Interested%20in%20detector%20simulation%20projects) (Detector
    simulation/Pseudo-Random Number Generators)
-   [Pierre
    L\'Ecuyer](mailto:andrei.gheata@cern.ch?subject=Interested%20in%20detector%20simulation%20projects) (Pseudo-Random
    Number Generators)

[**Contact information**]{#contact}
===================================

Please do not hesitate to contact us if you are planning to apply for
any of the above projects:

-   SFT GSoC mailing list:
    [sft-gsoc-AT-cern-DOT-ch](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%2012)
    (no subscription needed)
