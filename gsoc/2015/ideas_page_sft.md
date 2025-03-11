[CERN SFT Gsoc 2015 ideas page]{property="dc:title"} {#cern-sft-gsoc-2015-ideas-page .page-header}
====================================================

We participated in the Google Summer of Code with success each year
since 2011, so we are applying again in 2015!\
We intend to offer three options - pick one of the Project ideas which
are grouped into categories, have a look to the section dedicated to
[\'Blue sky\'](#bluesky) or propose your own great idea for this summer:
we are looking forward to hearing about **your** perspectives. A list of
our mentors (and their areas of expertise) can be found
[here](#mentors).

We encourage students who plan to apply to **[contact
us](#contact) ** about their interest and explain their project ideas as
early as possible. Our experience from our previous GSoC participation
was that frequently an initial student application either needs to be
reworked in close collaboration with a future mentor, or at least can
benefit from feedback and discussion. **Please do not forget to provide
us with some relevant information about yourself** (for example CV, past
projects, personal page or blog, linkedin profile, github account,
etc.).

Before submitting an application please consult the [official GSoC
FAQ](http://www.google-melange.com/gsoc/document/show/gsoc_program/google/gsoc2015/help_page)
where you can find some good advice on writing a successful application.
The application should be submitted through the [GSoC
webapp](http://www.google-melange.com/gsoc/homepage/google/gsoc2015)
before the **27th of March (19:00 UTC)**.

[Project ideas]{#project}
=========================

CernVM File System
------------------

The CernVM File System (CernVM-FS) is a read-only file system that is
optimized for the distribution of software to world-wide distributed
computing infrastructures.  It is used in the context of large-scale
scientific computing applications that use tens of thousands of
individual computers to process very large data sets in reasonable
time.  All these computers need to access specific data processing
software.  The access to the software is provided by CernVM-FS, a global
and versioning file system that uses HTTP for data transfer.  The file
system content is installed on a central web server from where it can be
mirrored and cached by other web servers and web proxies.  File system
clients download data and meta-data on demand and cache them locally. 
Data integrity and authenticity is ensured by the use use cryptographic
hashes and digital signatures.  CernVM-FS is used, among others, by the
Large Hadron Collider (LHC) experiments for the distribution hundreds of
millions files and directories of experiment software onto tens of
thousands of worldwide distributed nodes.

Source code: <https://github.com/cvmfs/cvmfs>\
Documentation:
<http://cernvm.cern.ch/portal/filesystem/techinformation>,
[Doxygen](https://ecsft.cern.ch/dist/cvmfs/doc/html/)\
Downloads: <http://cernvm.cern.ch/portal/filesystem/downloads>

### HTTP/2 Support

**Description:** CernVM-FS uses HTTP for all data transfers.  This
includes clients requesting files from servers as well as server to
server copies for replication.  Since the file system's workload is
primarily characterized by a large number of small files, reducing the
latency is paramount to performance.  Here, the upcoming
[HTTP/2](https://en.wikipedia.org/wiki/HTTP/2) brings some interesting
new features, in particular connection multiplexing and fixing
head-of-line blocking, which should fix the current problems with
[HTTP/1.1 pipelining](https://en.wikipedia.org/wiki/HTTP_pipelining). 
This project should add support for HTTP/2 in the CernVM-FS network code
and re-arrange the code for data replication to use a multiplexed
connection instead of parallel connections.  The HTTP/2 code itself will
probably be taken from [libcurl](http://curl.haxx.se/libcurl). 
Optionally, this project can be extended to develop a data prefetcher
using multiplexed connections.

**Expected results:** Extend the CernVM-FS download manager by a
vectorized interface, so that a number of download jobs can be sent and
received at once.  Develop the necessary code to automatically decide if
parallel connections (HTTP/1.1 on the other end) or multiplexed
connections (HTTP/2) should be used.  Extend the CernVM-FS replication
module to use the vectorized interface of the download manager.  Extend
the CernVM-FS file system code by a pre-fetch thread, that is able to
prefetch a given list of data chunks in the background.  Extend the file
system\'s meta-data by a table that can store prefetch hints.

**Mentor:** [Jakob
Blomer](mailto:sft-gsoc-AT-cern-dot-ch?subject=CernVM-FS%20HTTP%2F2),
[Gerardo
Ganis](mailto:sft-gsoc-AT-cern-dot-ch?subject=CernVM-FS%20HTTP%2F2)

**Requirements:** Good knowledge of C++, good knowledge of HTTP and
TCP/IP.  Experience with libcurl would be an advantage.

### Key-Value Store Interface for the Client Cache

**Description:** CernVM-FS stores downloaded files in a local cache. 
This is necessary for performance and to keep the load on the web
servers and proxies sufficiently low.  At the moment, the local cache
needs to reside on a POSIX file system.  In order to perform
collaborative caching in a cluster (i.e.: node A can cache a file for
node B and vice versa), the dependency of the local cache on a POSIX
file system should to be relaxed to a pure PUT/GET interface.  That
would allow to store the local cache in a key-value store such as
[RAMCloud](https://ramcloud.stanford.edu) or
[Riak](http://basho.com/riak/).  At the conceptual level, this project
includes to find a way to prevent many clients in a cluster to download
the same file at the same time (i.e.: to find a way to collapse
concurrent requests for the same file). The cache eviction requires
special treatment, too, in case that files marked for deletion are
currently used by a client.  Both problems could be tackled, for
instance, by a locking/lease table that is maintained in the key-value
store.

**Expected results:** Based on the current cache manager implementation,
separate the cache manager interface (open, close, read, exists, delete)
from its implementation.  Plug in the current implementation as a POSIX
cache manager.  Develop a cache manager implementation that uses a
key-value store as backing storage.  Develop locking primitives in the
key-value store that can be used to collaboratively update the cache
from multiple nodes.

**Mentor:** [Jakob
Blomer](mailto:sft-gsoc-AT-cern-dot-ch?subject=CernVM-FS%20Co-operative%20Caching),
[Gerardo
Ganis](mailto:sft-gsoc-AT-cern-dot-ch?subject=CernVM-FS%20Co-operative%20Caching)

**Requirements:** Good knowledge of C++, good knowledge of distributed
systems (e.g. CAP theorem, distributed hash tables, failure modes in
networks).  Experience with distributed key-value stores would be an
advantage.

Geant 4 Simulation Toolkit and Geant Vector Prototype
-----------------------------------------------------

The [Geant4](geant4.cern.ch) toolkit simulates the interactions of
elementary particles and radiation with matter. It is used to simulate
the detectors of the LHC and other High Energy Physics (HEP)
experiments. It finds application in other areas, from assessing the
effects of radiation on the electronics of satellites to improving the
design of medical detectors using domain-specific tools such as the
[GATE](http://www.opengatecollaboration.org/) and
[TOPAS](http://www.topasmc.org/) applications (external links). LHC
experiments use Geant4 to compare the signatures of rare events from new
physics (such as the Higgs boson) to those coming from known
interactions. The open source toolkit is developed by the Geant4
collaboration, which brings together 90 physicists and engineers from
laboratories and universities around the world (link is external).
Developments are ongoing to improve its precision and scope of
application, and to better utilise current and emerging computer
architectures. The simulation programs of the LHC experiments use the
Geant4 simulation toolkit to produce simulated LHC events running on
about 100,000 CPU cores continuously. Their statistics remain a
limitation in the analysis potential for some interesting types of new
physics. As a result the goal of the project is to explore different
ways to reduce the execution time on today's complex commodity CPUs, and
to prototype how to use it efficiently on the many-core hardware of the
future (tens, hundreds of cores, threads or 'warps'). The code required
to model diverse types of particles and interactions, and to model the
complex geometries of detectors is large. Due to this it overwhelms the
caches of current CPUs, significantly reducing the efficiency of
utilisation on today's hardware. This effort is focused on identifying
ways to reorganise the work so that more data (e.g. multiple particles
or rays) is processed by each function. By reusing the code on
\'nearby\' data we aim to use the memory architectures of today's
hardware better. At the same time we prepare the way to obtain good
performance on tomorrow's hardware. The key activity in this effort
involes the [Geant-Vector prototype](http://geant.cern.ch/) (GeantV)
which aims to evolve the simulation toolkit into a framework that is
better adapted to the critical role of memory caches, and makes optimal
use of SIMD vector instructions and accelerator devices.

### VecGeom

[VecGeom](https://github.com/sawenzel/VecGeom) is a novel templated C++
library to describe three-dimensional detector geometries and to offer
\"particle tracing\" APIs (much like in ray-tracing or game engines).
VecGeom goes beyond previously existing libraries (in Geant4 or ROOT) by
offering a strong support for single-instruction multiple data (SIMD)
processing of multiple particles and also offers SIMD-enhanced scalar
algorithms for appropriate shapes. VecGeom is also built to be used as
the geometry tracing library on GPUs and other accelerators. VecGeom is
still a very young open source project and there are several project
ideas, a GSOC student could contribute to:

**Description:**

-   **\"IO:\"** Study and implement support for native serialization of
    the VecGeom geometries using ROOT6/Cling object serialization.
    Implement a module to export and import a geometry description using
    the GDML format ( a XML format for description of geometries.)
    Implement an interface to the
    [DD4HEP](http://aidasoft.web.cern.ch/DD4hep) geometry descriptions.
-   **\"Testing and performance monitoring infrastructure:\"** Review
    and systematically extend the testing infrastructure of the project.
    Develop comprehensive unit tests. Develop a performance monitoring
    system that monitors performance evolution and displays results in a
    web-dashboard or in jenkins.
-   **\"Generalized GPU solid:\"** Extend the list of implemented shape
    primitives by a generalized vectorised/GPU-capable solid which can
    be used in place of the most popular existing solids (box, tube,
    conical & spherical shells) especially on the GPU. Inspired by the
    approach of [James
    Tickner](http://dx.doi.org/10.1016/j.cpc.2010.07.001) .

 

**Requirements:** Very good C++ knowledge; For \"testing\" project:
ctest, database, frontend web development experience; For \"GPU solid\":
some experience with the SIMD/SIMT paradigm and vectorized programming.

**Mentor:** [Sandro
Wenzel](mailto:sft-gsoc-AT-cern-dot-ch?subject=VecGeom)

### Additions to the Vc library for vectorization

[Vc](http://code.compeng.uni-frankfurt.de/projects/vc) is a free
software library to ease explicit SIMD vectorization of C++ code. It has
an intuitive API and provides portability between different compilers
and compiler versions as well as portability between different vector
instruction sets. This is achieved by offering C++ vector types that
hide the platform specific vector assembly instructions. Vc is used as
the primary abstraction layer to achieve vectorized code in the GeantV
simulation prototype and in many other applications in High-Energy
Physics and beyond. Vc is a relatively young project and offers many
opportunities for further development in order to keep up with the
evolution of computing platforms.

**Task ideas:**

-   Add support for 8-bit and 64-bit integer SIMD vectors (in particular
    for AVX2). A thorough investigation of SIMD vectors of char may be
    interesting for vectorization of string processing.
-   Add support for more SIMD (micro)architectures (AVX2, AVX-512,
    AltiVec)
-   Support for GPUs. There are several possibilities for supporting the
    vector types programming model on GPUs. One approach makes Vc codes
    portable to GPUs by supporting Vc types in CUDA kernels as scalar
    values. Thus, the data-parallelism is only expressed via the SIMT
    programming model. The second approach instructs a compiler to
    generate native GPU code, which executes a GPU thread per entry in
    the vector type.

**Requirements:** Working on Vc requires (very) good knowledge of C++
and preferably previous exposure to SIMD assembly or intrinsics
programming. In the course of the project your C++ skills will very
likely improve. It is possible to get gain insight into the work on SIMD
parallelization for the upcoming C++ standards.

**Mentor:** [Matthias Kretz](mailto:sft-gsoc-AT-cern-dot-ch?subject=Vc)

### New methods for integrating trajectory in field

Geant4 and GeantV use Runge-Kutta methods​ to integrate the motion of
charged particles in a non-uniform electromagnetic field. Two aspects of
this use are important: to obtain good accuracy for the integration and
to take a minimum of computation time. Sometimes a step remains in the
same volume, and the integration needs only to estimate the endpoint and
the momentum.  But when a track crosses a boundary, integration is used
also to identify the intersection point between the curved track and the
volume boundaries.  Due to the large number of steps and the cost of the
evaluations of the field, the integration and intersection are a
performance critical part of detector simulation. Adapting RK methods
which reduce the number of field evaluations has the potential to
measurably decrease the computation time in applications as diverse as
the simulation of detectors at the LHC and the development of improved
radiation therapy systems.\
\
**Task ideas:**

-   Introduce RK methods which re-use the last step of one step as the
    first step of the next step (FSAL)​
-   Introduce RK methods which can provide an evaluation at an
    intermediate point of an interval, using an interpolation method
    based on the values calculated by the integration.

**Requirements**: This project requires prior exposure to Numerical
Analysis and some familiarity with C++, C or Java programming.  It would
be helpful to have had either exposure to the numerical methods for
solving Ordinary Differential equations (ODEs) or else to have used a
Computer Algebra program (Maxima, Maple, Mathematica, Sage or similar)
which would enable easier prototyping. Both programming skill and
knowlege of numerical methods for ODEs will be improved by undertaking
this project. 

**Mentor**: [John
Apostolakis](mailto:sft-gsoc-AT-cern-dot-ch?subject=Field%20integration)

 ROOT
----

 

The ROOT system provides a set of OO frameworks with all the
functionality needed to handle and analyze large amounts of data in a
very efficient way. Having the data defined as a set of objects,
specialized storage methods are used to get direct access to the
separate attributes of the selected objects, without having to touch the
bulk of the data. Included are histogramming methods in an arbitrary
number of dimensions, curve fitting, function evaluation, minimization,
graphics and visualization classes to allow the easy setup of an
analysis system that can query and process the data interactively or in
batch mode, as well as a general parallel processing framework, PROOF,
that can considerably speed up an analysis. Thanks to the built-in C++
interpreter the command language, the scripting, or macro, language and
the programming language are all C++. The interpreter allows for fast
prototyping of the macros since it removes the, time consuming,
compile/link cycle. It also provides a good environment to learn C++. If
more performance is needed the interactively developed macros can be
compiled. ROOT\'s new C++11 standard-compliant interpreter is Cling, an
interpreter built on top of Clang (www.clang.llvm.org (link is
external)) and LLVM (www.llvm.org (link is external)) compiler
infrastructure. Cling is being developed at CERN as a standalone
project. It is being integrated into the ROOT data analysis
(root.cern.ch) framework, giving ROOT access to an C++11 standards
compliant interpreter. ROOT is an open system that can be dynamically
extended by linking external libraries. This makes ROOT a premier
platform on which to build data acquisition, simulation and data
analysis systems. ROOT is the de-facto standard data storage and
processing system for all High Energy Phyiscs labs and experiments world
wide. It is also being used in other fields of science and beyond (e.g.
finance, insurance, etc).

### **Extension and optimisation of the ROOT6 autoloading capabilities**

**Description**\
The flexible plug-in architecture of ROOT relies on a powerful mechanism
of \"autoloading\", i.e. the possibility to automatically load shared
libraries only when needed, for example upon the usage of a certain
class, without the need of linking the libraries. The present
infrastructure is rather performant and stable enough to be leveraged by
huge software systems like the LHCb, Atlas or CMS software stacks. On
the other hand, thanks to the procedure of integration of ROOT6 with the
software of the LHC experiments it was possible to conceive possible
functionality extensions and performance improvements. Examples are:

-   The extension of the mechanism of autoloading to accommodate the
    usage of functions and only classes, namespaces, variables and
    enumerators.
-   The usage of more memory and cache efficient data structures for the
    storage of the data necessary for autoload (e.g. exploiting tries or
    implicit sharing)
-   The optimisation of the rootmap files, i.e. the autogenerated
    catalogues containing the data to feed to the autoloading system
-   The improvement of the ROOT startup time with a clever preprocessing
    of the information to be passed to the ROOT interpreter. If time
    allows, the same strategies identified for the autoloading, can be
    applied to a similar procedure, called autoparsing.

*All the new features and changes will be integrated in ROOT by the
candidate together with a complete list of tests.*\
**Expected Results**

-   Implement the autoloading of shared libraries upon usage of
    functions
-   Replace the current implementation of the autoload keys registry
    with one which is faster and with a smaller memory footprint
-   Provide input about the performance of the rootmap format with
    runtime benchmarks and, if needed, provide a new format
-   A program/script for merging rootmaps avoiding duplication of
    information and a runtime procedure to format the rootmaps code
    which minimises the time needed by ROOT to interpret it

**Requirements**\
Strong C++ skills, knowledge in the field of Physics and HEP computation
and/or experience with ROOT are certainly a plus.

**Mentor:** [Danilo
Piparo](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-EnhanceAutoloading)

### **SAS: A tool for static analysis and coding rules checking**

**Description**\
Code maintenance is very much facilitated if the coding and style rules
are followed. Commercial tools can be used to check the code for rule
validations and to present the results in a easy form for developers to
act on them. Unfortunately, such commercial solution might be not
available for all developers especially in the field of research and
adding new rules could become a real problem. SAS
(https://github.com/dpiparo/SAS) is a tool which attempts to make coding
rules checking and clang based static analysis easy. This tool provides:

-   A simple way to build a Clang plugin providing checks which can be
    loaded by the scan-build utility or directly by Clang.
-   A tool to check formatting coding conventions taking advantage of
    clang-format
-   A set of scripts to wrap the compiler calls in order to plug static
    analysis and coding rules checking in any development
    workflow/continuous integration system.

The tool is in beta phase and needs consolidation and expansion of
functionality. This project aims to provide:

-   The implementation via static analyser checkers of the ROOT coding
    conventions (https://root.cern.ch/root/nightly/codecheck/rules.html)
-   The consolidation of the existing static analyser checkers ensuring
    thread safety and potential development of new ones, for example
    imposing absence of thread unsafe operations in methods which are
    const qualified.
-   The integration of clang-modernize targetting suggestions about the
    possible improvements of existing code bases
-   The consolidation of the SAS CMake based build system
-   The development of a ctest based testing system

**Requirements**\
C++, Clang, Cmake/CTest and Python

**Mentor:** [Danilo
Piparo](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-EnhanceAutoloading)

### **Interface between Paraview and ROOT**

**Description:**​Paraview is a powerful visualisation system, based on
VTK, providing a wide range of high level visualisation techniques ROOT
doesn't provide. Paraview is already interfaced to many kind of data
formats. The goal of this project would be to make a ROOT plugin to
Paraview allowing to convert ROOT trees into Paraview data structures in
order to visualise them.

**Requirements:** Knowledge of C++

**Mentor:** [Olivier Couet, Joachim Pouderoux
(Kitware)](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-Paraview)

### **Extend ROOT-R Interface**

**Description: **Using the ROOT-R interface many of the statistical
packages available in R such as those performing multi-variate analysis
can be used in ROOT. The idea of the project is to facilitate the usage
of some of the R packages by creating corresponding interface classes in
the ROOT system. These classes should implement some of the needed
interfaces required to be used by some of the statistical packages of
ROOT and they could be loaded at run-time by the ROOT plugin manager
system.\
**Expected Results:** Develop interface classes for some of the most
used the multi-variate statistical tools in R for classification and
regression. These interface classes should be designed to be used by the
TMVA package of ROOT.

**Requirements: **Knowledge of C++, ROOT and R. Knowledge of
computational statistics would be an advantage.\
**Mentors:** [Lorenzo Moneta, Sergei
Gleyzer](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-R)\
 

### **Prototype of TTreeFormula**

**Description:** TTreeFormula is a class used to parse and interpret the
expression strings used to query and make selections on the ROOT TTree
class with the TTree::Draw function. A new TFormula class has been
integrated in ROOT using the Just In Time compilation provided by Cling
to compile the mathematical expression to evaluate the formula. A
similar class needs to be developed for the expressions used to
analysing the ROOT TTree\'s.\
\
**Expected Results:** Develop a new prototype TTreeFormula class to be
used as an alternative to the existing one and provide some running use
case examples.\
\
**Required knowledge:**Advanced C++, Basic knowledge of Cling and C++11\
\
**Mentors:** [Lorenzo Moneta, Danilo
Piparo](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-R)

### **LINQ 4 ROOT and Cling**

**Description:** LINQ originally referred to the SQL-like syntax in C\#
and VB but it has over time changed its meaning to mean the way you
manipulate lists using the higher-order functions provided by
System.Linq. Working with lists using higher-order functions have been
available for functional and SmallTalk developers since the 70s but has
recently been popularized in mainstream languages such as C\#, VB,
JavaScript, Python, Ruby and so on. There are a few libraries that bring
this style into C++11. We\'d like to investigate their strengths and
weaknesses. We would like to adopt them in our C++11 interpreter and
provide a thorough real-world examples of their. A good starting point
would be https://github.com/vgvassilev/RxCpp. \
\
**Expected results:** Adoption in cling meeting cling\'s QA
requirements. Implement tests for all the realized functionality.
Prepare a final poster of the work and be ready to present it.\
\
**Required knowledge:**Advanced C++, Basic knowledge of Cling and C++11\
\
**Mentors:** [Vasil
Vasiliev](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-LINQ)

### **Extend clad - The Automatic Differentiation**

**Description:** In mathematics and computer algebra, automatic
differentiation (AD) is a set of techniques to numerically evaluate the
derivative of a function specified by a computer program. Automatic
differentiation is an alternative technique to Symbolic differentiation
and Numerical differentiation (the method of finite differences). Clad
(https://github.com/vgvassilev/clad) is based on Clang which will
provides the necessary facilities for code transformation. The AD
library is able to differentiate non trivial functions, to find a
partial derivative for trivial cases and has good unit test coverage.
There was a proof-of-concept implementation for computation offload
using OpenCL.\
\
**Expected results:**The student should teach AD how to generate
OpenCL/CUDA code automatically for a given derivative. The
implementation should be very well tested and documented. Prepare a
final poster of the work and be ready to present it.\
\
**Required knowledge:** Advanced C++, Clang abstract syntax tree (AST),
CUDA/OpenCL basic math.\
\
**Mentor:** [Vasil
Vasiliev](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-LINQ)

### Extension of ROOT I/O customization framework

**Description**\
ROOT includes a extensive, flexible, and performant framework to
automatically serialize C++ objects into a platform independent binary
format.  One of core strength of this framework is the ability to
support evolution in the user\'s data schema and be able to read files
containing older version of this schema.   The frameworks includes
several automatic transformation, including from any C++ standard
collections to another (for example changing for a vector\<UserObject\>
to a list\<UserObject\>) and including from any numerical to another.  
More complex transformation are also supported via I/O customization
rules.   If the core functionality is in placed, some of the intended,
but more complex features (see the end
of <http://indico.cern.ch/event/35523/session/59/material/slides/3?contribId=210>)
have not yet been addressed.\
\
**Expected Results**

-   Implement support for I/O rules for nested objects.
-   Implement support for just-in-time compilation of I/O rules.
-   Complete the functionality supported by the I/O customization rules.

**Requirements**\
Strong C++ skills, knowledge in the field of Physics and HEP computation
and/or experience with ROOT are certainly a plus.

**Mentor:** [Philippe
Canal](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-IO)

### **Modernization of C++ object streaming framework.**

**Description**\
ROOT includes a extensive, flexible, and performant framework to
automatically serialize C++ objects into a platform independent binary
format.  This framework is undergoing a modernization replacing older
construct with newer and more performance techniques made possible by
the newest version of the C++ standard and compiler.   This
modernization has been partially applied to the routines reading the C++
objects out of the platform independent binary format and still need to
be complete.    The same style of modernization needs to be applied to
the routines writing the C++ objects into the platform independent
binary format.  One the major challenge is to not only transform the
code into the new style and infrastructure but also to improve the
algorithm to take advantage of the new facilities to significantly
improve performance.

**Expected Results**

-   Complete modernization of the reading routines. 
-   Implementation the modernization of the writing routines.

**Requirements**\
Strong C++ skills, knowledge in the field of Physics and HEP computation
and/or experience with ROOT are certainly a plus.

**Mentor:** [Philippe
Canal](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-IO)

### **Implement a tool to \'warn\' user of inefficient (for I/O) construct in data model**

**Description**\
ROOT includes a extensive, flexible, and performant framework to
automatically serialize C++ objects into a platform independent binary
format.  One the major strength of this framework is the ability to
support almost all C++ constructs.  The downside of this flexibility is
that the user has the choice can select for a very wide ranges of
constructs and schemas which have very different I/O performance
characteristics.   Some of the recommendations for design an I/O
efficient data schema are straightforward, for example it is better to
use a sorted vector of pair than a map, and some are much more complex,
like the effect of deeper class hierarchy or the order of data
members.   Creating a tool that can analyze a given data model and give
clear recommendation on how to improve its performance would be very
beneficial and improve the productivity of data model designers.

**Expected Results**

-   Implement prototype scanning a user data model and giving simple
    recommendation.
-   Review and expand the list of recommendation to improve I/O
    efficiency.

**Requirements**\
Strong C++ skills, knowledge in the field of Physics and HEP computation
and/or experience with ROOT are certainly a plus.

**Mentor:** [Philippe
Canal](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-IO)

 IgProf
------

IgProf [https://igprof.org](https://igprof.org/) is a lightweight
performance profiling and analysis tool. It can be run in one of three
modes: as a performance profiler, as a memory profiler, or in
instrumentation mode. When used as a performance profiler it provides
statistical sampling based performance profiles of the application. In
the memory profiling mode it can be used to obtain information about the
total number of dynamic memory allocations, profiles of the live\'\'
memory allocations in the heap at any given time and information about
memory leaks. The memory profiling is particularly important for C/C++
programs, where large amounts of dynamic memory allocation can affect
performance and where very complex memory footprints need to be
understood. In nearly all cases no code changes are needed to obtain
profiles. IgProf currently supports Linux and x86 / x86-64 /ARMv7 and
ARMv8 CPU architectures. It correctly handles dynamically loaded shared
libraries, threaded applications and subprocesses. It can be run
entirely in user space without special privileges and produces full
navigable call stacks. The profile reports can be visualised in one of
several ways. A simple text report can be produced from the raw data
saved during the profiling run. Alternatively a web-browsable profile
report can be produced which allows easy navigation of the call stack.
Both allow one to see profile data ordered by symbol in terms of
cumulative\'\' cost (function plus children) and \`\`self\'\' cost (time
in the function itself) as well as a full call graph view showing the
functions which called, and which were called by, any given function. An
important feature of the web-navigable reports is the ability to point
via URL at particular places in the call graph. This facilitates
collaboration between individuals at different locations. While there
are obviously many profilers out there, the goal of IgProf is to provide
a reliable profiler for large applications like the one found in HEP,
and to tackle the challenges posed by heterogenous computing
architectures.

 

### Improve Performance Counters support in IgProf

**Description:** IgProf has initial support for reading performance
counters via the PAPI API. This is currently used to read and profile
energy consumption related counters. The goal of this project is to
extend the current implementation to allow profiling of generic HW
counters, providing the user a simple command line based interface to
select the different kind of counters.

**Required knowledge:** Excellent knowledge of C/C++ programming and
understanding of Linux system programming and software execution in
Linux are required.

### Profiling mixed python / C++ programs

**Description: **IgProf currently supports profiling native
applications, most likely written in C / C++. Profiling scripted
applications which invoke native code (e.g. a python framework which
invokes C++ plugins) is supported in the form of raw profile of the
python interpreter itself, which eventually calls the native code
functions. While this kind of profile can already provide insights, it
is still desireable to be able to profile and visualize the script
stacktraceand the native code one together, in order have a global
picture of the connections between the scripted and native code.

**Expected results**: the first objective is to identify and instrument
the parts of the python interpreter which are responsible for
allocating, deallocating and execute python stackframes, eventually
extending igprof instrumentation capabilities to deal with peculiarities
of the python interpreter. The second objective is to collect enough
information via the above mentioned instrumentation to be able to show
mixed python / C / C++ profiles, first for the performance profiler and
subsequently for the memory profiler.

**Required knowledge**: Excellent knowledge of C/C++ programming and
understanding of Linux system programming and software execution in
Linux are required. Understanding of python interpreter internals a
plus.

**Mentors**: [Giulio Eulisse, Peter Elmer, Vincenzo
Innocente](mailto:sft-gsoc-AT-cern-dot-ch?subject=IgProf)

### Support for CUDA / OpenCL profiling

**Description:** Extend IgProf to gather information from the profiling
APIs of one (or more) of the above mentioned packages. The goal is to be
able to measure the performance cost of mixed CPU / GPU applications,
taking into account the asynchronous behaviour of those applications,
allowing to track the source of GPU workloads.

**Required knowledge:** Excellent knowledge of C/C++ programming and
understanding of Linux system programming and software execution in
Linux are required. Knowledge of the above mentioned toolkits a plus.

**Mentor:** [Giulio Eulisse, Peter Elmer, Vincenzo
Innocente](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-IO)

​

### Enhanced support for POWER, x32 and MacOSX architectures

**Description:** Depending on the specific knowledge of the candidate,
the task is to improve support for profiling Power Architecture (POWER7
and eventually POWER8) applications or, as an alternative, to extend the
x86 support to include x32 (the 32bit pointers, 64bit data ABI for Intel
compatible processors). An additional task would be to resurrect OSX
support (IgProf used to work on PPC based OSX).

**Required knowledge:** Excellent knowledge of C/C++ programming and
understanding of Linux system programming and software execution in
Linux are required. Knowledge of at least one between ARM and x86
assembly language. Knowledge of MacOSX system programming a plus.

**Mentor:**[Giulio Eulisse, Peter Elmer, Vincenzo
Innocente](mailto:sft-gsoc-AT-cern-dot-ch?subject=ROOT-IO)

Sixtrack numerical accelerator simulation​
------------------------------------------

[SixTrack](http://cern.ch/sixtrack) is a software for simulating and
analysing the trajectory of high energy particles in accelerators. It
has been used in the design and optimization of the LHC and is now being
used to design the upgrade that will be installed in the next decade the
High-Luminosity LHC (HL-LHC). Sixtrack has been adapted to take
advantage of large scale volunteer computing resources provided by
the [LHC\@Home](http://sixtrack.web.cern.ch/SixTrack/www/cern.ch/lhcathome) project.
It has been engineered to give the exact same results after millions of
operations on several, very different computer platforms. The source
code is written in Fortran, and is pre-processed by two programs that
assemble the code blocks and provide automatic differentiation of the
equation of motions. The code relies on
the [crlibm](http://lipforge.ens-lyon.fr/www/crlibm/) library, careful
arrangement of parenthesis, dedicated input/output and selected
compilation flags for the most common compilers to provide identical
results on different platforms and operating systems. An option enables
the use of the [Boinc](http://boinc.berkeley.edu/) library for volunteer
computing. A running environment SixDesk is used to generate input
files, split simulations for <LHC@Home> or CERN cluster and collect the
results for the user. SixTrack is licensed under LGPLv2.1.

A strong background in computer science and programming languages as
well the interest to understand computational physics methods
implemented in the code are sought. The unique challenge will be offered
to work with a high-performance production code that is used for the
highest energy accelerator in the world - and thus the code\'s
reliability and backward compatibility cannot be compromised. There will
be the opportunity to learn about methods used in simulating the motion
of particles in accelerators.

### Create a Standalone Tracking Library

**Description**: Complete, test and deploy a standalone tracking library
in C to replace the present inner tracking loop written in fortran with
C one that can target both CPU and GPU. The inner loop uses a simple
array based contiguous data structure that can be generated by SixTrack
or external programs and can be resident in the CPU or GPU main memory.
In case of GPU, the ideal number of particle per core (even one such
that coordinates do not leave internal registers) should be evaluated
for speed.

**Expected results: **Running code which rely only on the newly
rewritten library to perform tracking simulations and test suite that
proves that old and new implementation produce identical results.

**Mentors: **[Ricardo De Maria, Eric
McIntosh](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%20SixTrack%20-%20Standalone%20Tracking%20Library%20)

**Requirements**: Experience with Fortran, C, calculus and a background
of physics are important.

### New physics models

**Description:** Implement, test and put in production a new solver for
exact bending dipoles, combined function magnets, radiation effects,
track total time.

**Expected results:** The user can build accelerator simulations with
more accurate models for low energy machines.

**Mentors: **[Ricardo De Maria, Eric
McIntosh](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%20SixTrack%20-%20New%20Physics%20Models)

**Requirements:** Fortran, calculus, accelerator physics.

 

Methodical Accelerator Design
-----------------------------

[MAD](http://cern.ch/mad) is a tool with a long standing history used to
design, model and optimise particle accelerators beam physics. The
development of a completely new version of MAD (GPLv3) started recently
with the aim to support a wider range of topologies and physics, and to
provide more accurate models with better performance and flexibility. It
relies heavily on the recent improvements performed on
[LuaJIT](http://luajit.org), an implementation of the Lua programming
language embedding an extremely efficient JIT compiler. Still low-level
mathematics and physics modules are implemented in C/C++ with high-level
wrappers written in Lua and using native
[FFI](http://luajit.org/ext_ffi.html) of LuaJIT. Supported platforms are
Linux, MacOSX and Windows.

### **Integration of MAD**

**Description:** As the development evolves, it becomes more and more
important to integrate all the different parts of the new MAD into a
single standalone application with no external dependencies. The work
will consist to embedded LuaJIT, MAD scripts (thousands lines of Lua),
MAD libraries (thousands lines of C/C++) and third party libraries
(C/C++, Fortran) into a single application in a portable manner, still
allowing to load external modules at runtime (user scripts, shared
libraries). The application must be able to run in interactive and batch
mode with multiple internal Lua environments connected either in
parallel or in series. A clear policy will have to be enforced for
errors handling and memory management through the different layers and
technologies of the application.

**Expected results:** A standalone application without external
dependencies embedding all the components and aforementioned features of
MAD, and being able to run in interactive and batch mode in a terminal
on Linux, MacOSX and Windows.

**Requirements:** Good knowledge of C, Lua and OS tools. Good experience
with portable integration and deployment of software. Knowledge of
LuaJIT and FFI would be preferable.

**Mentor:** [Laurent
Deniau](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202015%5D%20Integration%20of%20MAD)

### **Extension of LuaJIT for MAD**

**Description:** Deferred expressions are heavily used in MAD to
describe accelerator lattice while postponing business logic decision
(e.g. circuits) at a later design or optimisation stage. Lua supports
lambda functions as a generalisation of the deferred expressions, but
the syntax is too verbose to be useful. The work will consist to extend
the parser and possibly the semantic of LuaJIT through patches to
support compact syntax of lambda functions and deferred expressions
(lambda without formal  parameter), following the approach of [GSL
Shell](http://www.nongnu.org/gsl-shell). The extension of the semantic
will tag lambdas as special LuaJIT functions that have to be evaluated
instead of referenced when used in expressions without call semantic
(i.e. without parenthesis). This automatic dereferencing will allow to
efficiently emulate the deferred expressions mandatory for the new MAD.

**Expected results:** Set of patches to apply to LuaJIT (C code) after
each update. The patches must be easy to maintain separately as LuaJIT
evolves. A set of test cases to be run after each update to ensure no
regression.

**Requirements:** Good knowledge of C. Good experience with parsers and
interpreters. Knowledge of LuaJIT would be preferable.

**Mentor:** [Laurent
Deniau](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202015%5D%20Iextension%20of%20LuaJIT%20for%20MAD)

Reflection-based Python-C++ language bindings: cppyy
----------------------------------------------------

cppyy is a fully automated, run-time, language bridge between C++ and
Python. It forms the underpinnings for PyROOT, the Python bindings to
ROOT, the main persistency and analysis framework in High Energy Physics
(HEP), is used to drive the frameworks of several HEP experiments, and
is the environment of choice for analysis for many HEP physicists. cppyy
is the only Python-C++ bindings technology that can handle the scale,
complexity, and heterogeneity of HEP codes. There are two
implementations, one for CPython, and one for PyPy.

Source codes, documentation, and downloads: https://root.cern.ch/  and
 https://pypy.org/

Both the CPython and PyPy implementations support the CINT and Reflex
reflection systems, the CPython version also supports Cling, which is
based on Clang/LLVM.\
There are two proposed projects that can proceed independently.

 

### Pythonization API

**Description:** Full automation provides language bindings that cover
the vast number of use cases, especially since the reflection
information can be used to properly treat common patterns such as smart
pointers, STL iterators and so on. We call these treatments
\"pythonizations\", as the strictly bound C++ code is turned into bound
code that has a Python \"feel.\" However, there are always a few corner
cases that can be improved with manual intervention. Currently this is
done by helpers or wrapper code on the C++ or Python side, but a
well-designed API standardizes these manual tasks, improving the
scalability and interoperability.

**Expected results:** Design and implement a \"pythonization\" API that
covers all the common cases such as different memory ownership models,
hand-off of the Global Interpreter Lock (GIL), and user-defined
callbacks that handle more common patterns such as has been done for
STL. Implement this for both CPython (in C++) as well as for PyPy (in
(R)Python). The API should scale up and be able to deal with conflicts.

**Extra:** some patterns, such as return by reference of builtin values,
can not be described in Python code and need C++ wrappers. Extend the
wrapper generator in use by Cling to provide such \"pythonizations\"
automatically.

**Requirements:** Good knowledge of C++, excellent knowledge of Python

**Mentor:** [Wim
Lavrijsen](mailto:sft-gsoc-AT-cern-dot-ch?subject=%20PythenizationAPI%20)

### Integrate the Cling backend into PyPy/cppyy

**Description:** Cling, being based on Clang/LLVM can parse the latest
C++ standard (C++11/C++14). A Cling backend exists for CPython/cppyy,
but not yet for PyPy/cppyy. A common backend could serve both projects,
and would reduce the cost of new features, making them much quicker
available.

**Expected results:** Implement a Cling backend on libCling directly,
using the CPython implementation as a starting point, for use by both
CPython and PyPy. Package this backend for distribution. Design and
implement a method for distribution of Clang modules with the standard
Python distribution tools.

**Requirements:** Working knowledge of C++, good knowledge of Python

**Mentor:** [Wim
Lavrijsen](mailto:sft-gsoc-AT-cern-dot-ch?subject=%20ClingAndPyPy%20)

Xrootd​
-------

Access to extremely large data volumes is a key aspect of many \"Big
Data\" problems in the sciences and for particle physics in particular.
The international character of such projects also leads to the need to
access data located in many geographical locations. The Xrootd project (
<http://xrootd.org> (link is external)) aims at giving high performance,
scalable fault tolerant access to data repositories of many kinds. It is
primarily used to provide access to file system storage over the local
or wide area network; however, it is also used as a building block for
larger storage systems such as CERN EOS (
[http://eos.cern.ch](http://eos.cern.ch/) (link is external)) or the
large-scale global data federations. The Xrootd protocol has many
high-performance features (such as asynchronous requests and request
pipelining) which are analogous to those added to HTTP/2. The Xrootd
client is used throughout High Energy Physics and is well-integrated in
the ROOT data analysis package.

### Implement multi-sourcing interface with the Xrootd client

**Description**:The Xrootd client often has several potential data
sources available. Each source may be of varying quality, and quality
may change over time. To speed up data access - and to decrease the
impact of poor source selection - we would like to investigate the
implementation of a multi-source reading algorithm (reading from several
sources in parallel). This would be implemented as a plug-in to the
existing client and expose identical interfaces; a sample algorithm is
already available from other sources.

**Requirements**: Excellent knowledge of C++ programming and
understanding of basic network and storage architectures.

**Mentors** : [Matevz Tadel, Brian Bockelman, Andy
Hanushevsky](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC-XROOTD-PROJ1)

### Implement a client-side caching library

**Description**: Caching data locally on the client side can be very
important to achieving performance when network latencies are high. This
project involves the implementation of a client side plugin library to
temporarily cache data being read to disk.

**Requirements**: Excellent knowledge of C++ programming and
understanding of basic network and storage architectures.

**Mentors** : [Matevz Tadel, Brian Bockelman, Andy
Hanushevsky](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC-XROOTD-PROJ2)

[\'Blue sky\' ideas]{#bluesky}
==============================

### Binary code browser and tester

**Description:** This is a potential project on tool development for the
benefit of \"low-level\" developers in various other projects. It
proposes the development of a GUI based (web) application with which one
is able to browse through a binary file ( executable, object file,
library file ) and inspect the assembly code on various levels (
functions ). It could also offer an API to perform unit tests on the
assembly code level. To a first instance, this project would be a
convenience tool offering a good alternative to \"objdump etc.\" and
extending on the capabilities of those tools. Use cases are: Quickly
seeing if a certain function contains the right vectorized code or
getting a list of functions that are called from a certain function. The
project can benefit from the portable
[ParseAPI](http://www.dyninst.org/parse) layer which provides the API to
retrieve data from executable files. Initial ideas for the tool include

-   It should be a GUI tool. Possibilities include: plugin for eclipse
    and/or a web application interface
-   Minimal functionality: List all functions in an executable
    file/library. Browse through functions. List disassembly of clicked
    functions. provide histograms on assembly code. Provide a
    configurable dashboard. Provide configurable styling on assembly
    code. Being extensible via a plugin-mechanism.
-   Further idea: provide static call graph (like in valgrind); provide
    high-level interface to unit test on assembly code \...

**Requirement:**Object oriented analysis; (Java) GUI development \...

**Mentor:** [Sandro
Wenzel](mailto:sft-gsoc-AT-cern-dot-ch?subject=BCodeBrowser)

[Mentors]{#mentors}
===================

Here is the list of our mentors and their areas of expertise:

-   [Lorenzo
    Moneta](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%2015%general)
    (programme administrator; ROOT)
-   [Sandro
    Wenzel](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%2015%general)
    (programme administrator; simulation; vectorization)
-   [Jakob Blomer](mailto:sft-gsoc-AT-cern-dot-ch) (CernVM-FS)
-   [Vasil Vasilev](mailto:sft-gsoc-AT-cern-dot-ch) (ROOT)
-   [Danilo Piparo](mailto:sft-gsoc-AT-cern-dot-ch) (ROOT)
-   [Olivier Couet](mailto:sft-gsoc-AT-cern-dot-ch) (ROOT)
-   [Philippe Canal](mailto:sft-gsoc-AT-cern-dot-ch) (ROOT)
-   [John Apostolakis](mailto:sft-gsoc-AT-cern-dot-ch) (Simulation)
-   [Giulio Eulisse](mailto:sft-gsoc-AT-cern-dot-ch) (IgProf)
-   [Riccardo De Maria](mailto:sft-gsoc-AT-cern-dot-ch) (Sixtrack)
-   [Laurent Deniau](mailto:sft-gsoc-AT-cern-dot-ch) (MAD)
-   [Wim Lavrijsen](mailto:sft-gsoc-AT-cern-dot-ch) (PyROOT)
-   [Matthias Kretz](mailto:sft-gsoc-AT-cern-dot-ch?subject=Vc) (Vc)

[Contact information]{#contact}
===============================

Please do not hesitate to contact us if you are planning to apply for
any of the above projects:

-   SFT GSoC mailing list:
    [sft-gsoc-AT-cern-DOT-ch](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%2012)
    (no subscription needed).
