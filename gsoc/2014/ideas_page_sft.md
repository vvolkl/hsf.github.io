[CERN SFT Gsoc 2014 ideas page]{property="dc:title"} {#cern-sft-gsoc-2014-ideas-page .page-header}
====================================================


Following the great experiences in Google Summer of Code in 2011, 2012
and 2013 we are applying again in 2014!\
Project ideas are grouped into categories (ideas related to the SixTrack
accelerator simulation engine used in the LHC\@Home application, to the
cling interpreter inside Root, to the performant and versatile IgProf
profiler, to the [CERN Virtual Machine](#cernvmideas), and to the [Geant
4](#geantideas) simulation tools). We also have a so-called [\'Blue
sky\'](#bluesky) ideas which are rather raw and must be worked on
further before they become projects. And we are open to other great
ideas, and are looking forward to hearing from students with new
perspectives on our projects. The list of our mentors (and their areas
of expertise) can be found [below](#mentors).

![LHC Experiment Software Stack](http://sftweb.cern.ch/img/swstack.png)

Our projects are all related to codes which are used for the LHC
accelerator and its experiments. They are almost as diverse as software
stack of the LHC experiments ranging from adapting the the CernVM file
system to the tracking precisesly hundreds of protons over millions of
times around a model of the LHC accelerator.  The LHC experiments have
software frameworks that make use of common scientific software
libraries for high-energy physics (HEP) and many other open source
tools.  CernVM and CernVM-FS provide a uniform runtime environment based
on Scientific Linux.  The software stack is fully open sourced; many
parts of it are used outside the world of particle physics, as in
simulating medical physics detectors for medical imaging or estimating
the dose deposited in the sensitive electronics of satelites as they fly
through the earth\'s radiation belts.

 

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
FAQ](http://www.google-melange.com/gsoc/document/show/gsoc_program/google/gsoc2014/help_page)
where you can find some good advice on writing a successful application.
The application should be submitted through the [GSoC
webapp](http://www.google-melange.com/gsoc/homepage/google/gsoc2014)
before the **21st of March (19:00 UTC)**.

 

 

[Project ideas]{#project}
=========================

 

[ROOT Object-Oriented data analysis framework]{#rootideas}
----------------------------------------------------------

------------------------------------------------------------------------

The [ROOT](http://root.cern.ch/) system provides a set of OO frameworks
with all the functionality needed to handle and analyze large amounts of
data in a very efficient way. Having the data defined as a set of
objects, specialized storage methods are used to get direct access to
the separate attributes of the selected objects, without having to touch
the bulk of the data. Included are histograming methods in an arbitrary
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
compiled.

 

ROOT\'s new C++11 standard-compliant interpreter
is [Cling](http://root.cern.ch/drupal/content/cling), an interpreter
built on top of Clang ([www.clang.llvm.org](http://www.clang.llvm.org/))
and LLVM ([www.llvm.org](http://www.llvm.org/)) compiler infrastructure.
Cling is being developed at CERN as a standalone project. It is being
integrated into the ROOT data analysis
([root.cern.ch](http://root.cern.ch/)) framework, giving ROOT access to
an C++11 standards compliant interpreter.

ROOT is an open system that can be dynamically extended by linking
external libraries. This makes ROOT a premier platform on which to build
data acquisition, simulation and data analysis systems. ROOT is the
de-facto standard data storage and processing system for all High Energy
Phyiscs labs and experiments world wide. It is also being used in other
fields of science and beyond (e.g. finance, insurance, etc).

### Complete ROOT --- R interface

**Description**: Complete the interface in ROOT to call R function using
the R C++ interface  (Rcpp,
see <http://dirk.eddelbuettel.com/code/rcpp.html>). Make available in
ROOT many of the statistical packages available in ROOT such as those
performing regression and.or multi-variate analysis. Developing this
interface opens the possibility in ROOT to use the very large set of
mathematical and statistical tools provided by R.

**Expected Results**: Make some class(es) implementing some of the
existing algorithm interface in ROOT, so that the R functionality can be
used directly from the ROOT classes or statistical studies (e.g.
multivariate analysis) without knowing the low-level details. Another
objective will be to package the ROOT-R interface in a library which
will be can be optionally distributed with ROOT

**Mentor**: [Lorenzo
Moneta](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2013%20-%20Root%20R%20Interface)

**Requirements**: Basic knowledge of C++.  Knowledge of ROOT and/or R
would be advantages.

 

### Coding rules and style checker based on the Clang Static Analyzer

**Description**: Code maintenance is very much facilitated if the coding
and style rules are followed. This is the case for the ROOT project for
which a number of rules have been defined since the early days of the
project. A commercial tool was used to check the code for rule
validations and to present the results in a easy form for developers to
act on them. With a commercial solution, adding new rules has become a
real problem. The idea is to re-implemement the existing rules with a
open source tool, which can be extended and adapted to also fulfill the
needs of other software development projects.

**Expected Results**: Develop a new C++ code checker tool,  possibly
based on the Clang Static Analyzer, which is initially inplementing the
set of ROOT code rules and is extendible to other set of rules for
diffrent proejcts.  The current coding rules that will need to be
implemented are listed here
 <http://root.cern.ch/root/nightly/codecheck/rules.html> and results of
the analysis should be presented in a easy and accessible way for
developers to identify what rules has been violated by the latest commit
to the repository. The existing tool (commercial) produces the following
table   <http://root.cern.ch/root/nightly/codecheck/codecheck.html>

**Mentor**: Pere Mato, Olivier Couet

**Requirements**: Basic knowledge of C++, basic knowledge of Clang/Clang
Static Analyzer

 

### Code copy/paste detection

<div>

**Description**:The copy/paste is common programming practice. Most of
the programmers start from a code snippet that already exists in the
system and modify it to match their needs. Easily some of the code
snippets end up being copied dozens of times, which leads to worse
maintainability, understandability and logical design.
[Clang](http://clang.llvm.org) and [clang\'s static
analyzer](http://http://clang-analyzer.llvm.org/) provide all the
building blocks to build a generic C/C++ copy/paste detector.

</div>

<div>

**Expected results**:Build a standalone tool or clang plugin being able
to detect copy/pasted code. Lay the foundations of detection of slightly
modified code (semantic analysis required). Implement tests for all the
realized functionality. Prepare a final poster of the work and be ready
to present it.

</div>

<div>

**Required knowledge**: Advanced C++, Basic knowledge of Clang/Clang
Static Analyzer.

</div>

**Mentor**: [Vasil
Vasiliev](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202014%20Extending%20Cling)

 

### Cling projects

<div>

 

</div>

ROOT\'s new C++11 standard-compliant interpreter
is [Cling](http://root.cern.ch/drupal/content/cling), an interpreter
built on top of Clang
([www.clang.llvm.org](http://www.clang.llvm.org "www.clang.llvm.org"))
and LLVM ([www.llvm.org](http://www.llvm.org "www.llvm.org")) compiler
infrastructure. Cling is being developed at CERN as a standalone
project. It is being integrated into the ROOT data analysis
(root.cern.ch) framework, giving ROOT access to an C++11 standards
compliant interpreter.

 

### Cling bundle for most popular platforms

<div>

**Description**: Cling standalone is in fairly stable state. We\'d like
to ship it to the end users as a package through apt-get, yum and so on
(Windows installer included).

</div>

<div>

**Expected results**:an automatic tool (script) wrapping newest version
of cling into a \'installable\' package and registering it in the
repositories. Implement tests for all the realized functionality.
Prepare a final poster of the work and be ready to present it.

</div>

<div>

**Required knowledge**:Basic knowledge of package managers, Shell, Bash,
Python

</div>

**Mentor**: [Vasil
Vasiliev](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202014%20Extending%20Cling)

 

### Cling name autodetection and library autoloading

<div>

**Description**: We propose to improve Cling\'s interactive prompt to
provide hints where the names are. Eg. \[cling\] std::vector a; error
std::vector is missing. Please type \#include Alongside with this we
also would like a hint which library needs to be loaded.

</div>

<div>

**Expected results**: Be able to detect a missing include and its
corresponding library. Implement tests for all the realized
functionality. Prepare a final poster of the work and be ready to
present it.

</div>

<div>

**Required knowledge**:Advanced C++, Intermediary knowledge of
compilers/interpreters, Basic knowledge of Clang and Cling.

</div>

**Mentor**: [Vasil
Vasiliev](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202014%20Extending%20Cling)

 

### LINQ 4 ROOT and Cling

<div>

**Description**: LINQ originally referred to the SQL-like syntax in C\#
and VB but it has over time changed its meaning to mean the way you
manipulate lists using the higher-order functions provided by
System.Linq. Working with lists using higher-order functions have been
available for functional and SmallTalk developers since the 70s but has
recently been popularized in mainstream languages such as C\#, VB,
JavaScript, Python, Ruby and so on. There are a few libraries that bring
this style into C++11. We\'d like to investigate their strengths and
weaknesses. We would like to adopt them in our C++11 interpreter and
provide a thorough real-world examples of their.

</div>

<div>

**Expected results**:Thorough analysis of the pros and cons of the
available C++ LINQ libraries. Adoption in cling meeting cling\'s QA
requirements. Implement tests for all the realized functionality.
Prepare a final poster of the work and be ready to present it.

</div>

<div>

**Required knowledge**:Advanced C++, Basic knowledge of Cling and C++11

</div>

**Mentor**: [Vasil
Vasiliev](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202014%20Extending%20Cling)

 

### Cling language support

<div>

**Description**:Clang (the underlying compiler library) supports various
programming languages besided C and C++. It offers OpenCL, CUDA,
ObjectiveC and ObjectiveC++. Cling\'s design and implementation are not
bound to support only C/C++. We propose to improve the inherited
language support in the interpreter by supporting as many languages as
the underlying compiler library (clang) supports.

</div>

<div>

**Expected results**:adjustment of cling\'s custom AST transform passes,
implementing loading of the corresponding language runtime environment
and adding corresponding test cases. Prepare a final poster of the work
and be ready to present it.

</div>

<div>

**Required knowledge**: Intermediate C++, Clang abstract syntax tree
(AST), basic ObjectiveC/C++.

</div>

**Mentor**: [Vasil
Vasiliev](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202014%20Extending%20Cling)

###  

### Implement Automatic Differentiation library using Cling

<div>

**Description**: In mathematics and computer algebra, automatic
differentiation (AD) is a set of techniques to numerically evaluate the
derivative of a function specified by a computer program. Automatic
differentiation is an alternative technique to Symbolic differentiation
and Numerical differentiation (the method of finite differences). The
automatic differentiation library is to be based on Cling which will
provides the necessary facilities for code transformation.

</div>

<div>

**Expected results**: The AD library is able to differentiate non
trivial functions, to find a partial derivative for trivial cases and
has good unit test coverage.

</div>

<div>

**Required knowledge**: Advanced C++, Clang abstract syntax tree (AST),
basic math.

</div>

**Mentor**: [Vasil
Vasiliev](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202014%20Extending%20Cling)

 

 

[CernVM & CernVM-FS]{#cernvmideas}
----------------------------------

------------------------------------------------------------------------

CernVM is a Virtual Software Appliance designed to provide a complete
and portable environment for developing and running the data analysis of
the [CERN Large Hadron Collider
(LHC)](http://public.web.cern.ch/public/en/lhc/lhc-en.html) on any
end-user computer (laptop, desktop) as well as on the Grid and on Cloud
resources, independently of host operating systems. This \"thin\"
appliance contains only a minimal operating system required to bootstrap
and run the experiment software. The experiment software is delivered
using the CernVM File System (CernVM-FS),  a
[Fuse](http://fuse.sourceforge.net) file system developed to deliver
High Energy Physics (HEP) software stacks onto (virtual) worker nodes.

 

CernVM-FS is used for instance by LHC experiments on their world-wide
distributed computing infrastructure. HEP software is quite complex with
tens of gigabytes per release and 1-2 releases per week while, at the
same time, almost all the individual files are very small resulting in
hundreds of thousands of files per release. CernVM-FS uses [content
addressable
storage](http://en.wikipedia.org/wiki/Content-addressable_storage) (like
the GIT versioning system). For distribution it uses
[HTTP](http://curl.haxx.se/libcurl). File meta data are organized in
trees of [SQlite](http://sqlite.org) file catalogs. Files and file meta
data are downloaded on demand and aggressively cached. The CernVM File
System is part of the CernVM appliance but it compiles and runs on
physical Linux/OS X boxes as well. It is mostly BSD licensed with small
GPL parts. CernVM-FS source code of the current development branch can
be downloaded from [here](https://github.com/cvmfs/cvmfs), the
documentation is available
[here](http://cernvm.cern.ch/portal/filesystem/techinformation).

 

### Streamline CernVM Contextualization Plug-ins

**Description:** CernVM is a virtual appliance that can be used by the
four LHC experiments in order to run simulation and data processing
applications in the Cloud. Unlike standard virtual machine images,
CernVM provides a uniform configuration interface across the most
relevant cloud infrastructures (Amazon EC2, Google Compute Engine, CERN
OpenStack, Nimbus ScienceCloud, \...). This is achieved by so called
\"contextualization plugins\", light-weight agents inside the virtual
machine that detect the infrastructure at hand and dynamically adapt the
image. With the transition of most cloud infrastructures from an early
exploitation phase to a production service, the contextualization
plugins also need to be evolved, streamlined, and optimized. For this
project, the student develops or evolves a common framework for
contextualization plugins. The student is supposed to measures and
optimizes the virtual machine boot time delay due to these plugins. The
student will also get in touch with the computing groups of LHC
experiments to ensure CernVM fits within their distributed computing
environment.

**Expected Result:** .\
**Mentors:** [Gerardo
Ganis ](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2012)\
**Requirements:**  Good knowledge of Linux/Unix, experience with
scripting languages (Perl/Python/BASH). Experience with virtualization
technology is a plus.

 

[Geant 4 Simulation Toolkit and Geant Vector Prototype]{#geantideas}
--------------------------------------------------------------------

------------------------------------------------------------------------

The [Geant4 toolkit](http://cern.ch/geant4) simulates the interactions
of elementary particles and radiation with matter. It is used to
simulate the detectors of the LHC and other High Energy Physics (HEP)
experiments. It finds application in other areas, from assessing the
effects of radiation on the electronics of satellites to improving the
design of medical detectors with the custom [GATE
application](http://www.opengatecollaboration.org). LHC experiments use
Geant4 to compare the signatures of rare events from new physics (such
as the Higgs boson) to those coming from known interactions. The open
source toolkit is developed by the Geant4 collaboration, which brings
together 90 physicists and engineers from laboratories and universities
around the [world](http://www.geant4.org/geant4/collaboration/).
Developments are ongoing to improve its precision and scope of
application, and to better utilise current and emerging computer
architectures. The simulation programs of the LHC experiments use the
Geant4 simulation toolkit to produce simulated LHC events continuously
running with on about 100,000 CPU cores throughout the year. These
statistics remain a limitation in the analysis potential for some
interesting types of new physics. As a result the goal of the project is
to explore different ways to reduce the execution time of Geant4 on
today's complex commodity CPUs, and to prototype how to use it
efficiently on the many-core hardware of the future (tens, hundreds of
cores, threads or 'warps'). The code required to model diverse types of
particles and interactions, and to model the complex geometries of
detectors is large. Due to this it overwhelms the caches of current
CPUs, significantly reducing the efficiency of utilisation of today's
hardware. This effort is focused on identifying ways to spread the work
between threads and/or to reorganise the work. By using less code in
each core we aim to use the memory architectures of today's hardware
better. At the same time we prepare the way to obtain good performance
on tomorrow's hardware.

 

### Reengineer Propagation of Charged Tracks in a Magnetic Field for Vector and GPU

**Description:** A significant part of the CPU time in simulations of
large detectors is taken in integrating the motion of particles in an
electromagnetic field, using numerical integration techniques.  Our idea
is to redesign the classes used in propagation, to avoid virtual
function calls and aid optimization including vectorisation. We target
common code which can be used in several modes: in sequential simulation
for a single particle, in vector mode for a set of tracks or on a GPU
for a single track.

**Expected Result**: Created new implementations using template
techniques and vectorization that can be used across vector and
non-vector CPUs and GPUs, and benchmark the speed for a vector of
particles propagating in a magnetic field against the existing
sequential version.

**Mentors:** [John Apostolakis, Sandro
Wenzel ](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2013%20-%20Geant4%20Geometry)\
**Requirements:** Good knowledge of C++, Object-Oriented Programming,
parallel programming using for vectors or on GPUs are essential.
Knowledge of solution of ordinar differential equations will be
beneficial.

[]{#SixTrack}Sixtrack numerical accelerator simulation
------------------------------------------------------

------------------------------------------------------------------------

[SixTrack](http://cern.ch/sixtrack) is a simulation tool for the
trajectory of high energy particles in accelerators. It has been used in
the design and optimization of the LHC and is now being used to design
the upgrade that will be installed in the next decade the High-Luminsity
LHC (HL-LHC). Sixtrack has been adapted to take advantage of large scale
volunteer computing resources provided by
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
files, split simulations for LHC\@Home or CERN cluster and collect the
results for the user. SixTrack is licensed under LGPLv2.1.

 

A strong background in computer science and programming languages as
well the interest to understand computational physics methods
implemented in the code are sought. The unique challenge will be
offerred to work with a high-performance production code that is used
for the highest energy accelerator in the world - and thus the
code\'s reliability and backward compatibility cannot be compromised.
 There will be the opportunity to learn about methods used in simulating
the motion of particles in accelerators.

 

### Simulating time dependent functions

**Description:** Implement, test and put in production the ability to
change the strength, misalignment of any element by applying a function
composed by predefined branch like linear, parabolic, sinusoidal, withe
noise, colored noise.

**Expected results:** The user will have the option to define magnet
strength as a function of time from the input files.

**Mentors:** [Ricardo De Maria, Eric
McIntosh](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%20SixTrack%20-%20Simulating%20Time%20Dependent%20Functions)

**Requirements:** Fortran, calculus.

 

### New physics models

**Description:** Implement, test and put in production a new solver for
exact bending dipoles, include per-particle mass and charge state, track
total time.

**Expected results:** The user can build accelerator simulations with
more accurate models for low energy machines.

**Mentors: **[Ricardo De Maria, Eric
McIntosh](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%20SixTrack%20-%20New%20Physics%20Models)

**Requirements:** Fortran, calculus, accelerator physics.

 

### Database infrastructure for large scale simulation

**Description:** Develop a database interface to collect the results
sent from volunteers or computer clusters and provide them to the users.
The code will allow to split a study in smaller unit, submit the study,
query the state, re-submit missing or invalid results, collect the data
in users\' SQLite database.

**Expected results:** The user will have a complete set of tools to
submit, follow and collect results from distributed computer resources.

**Mentors: **[Ricardo De Maria, Eric
McIntosh](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%20SixTrack%20-%20Database%20Infrastructure%20for%20large%20scale%20simulation)

**Requirements:** SQL, python, C/C++, Linux.

 

### Create a Standalone Tracking Library 

**Description**: : Define an API for particle tracking, implemented the
existing model as a standalone module in C and re-factor existing code
to use it. The API and the module should open the way to GPU
calculations.

**Expected results: ** Test runs which rely only on the newly rewritten
library to perform tracking simulations.

**Mentors: **[Ricardo De Maria, Eric
McIntosh](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%20SixTrack%20-%20Standalone%20Tracking%20Library%20)

**Requirements**: Experience with Fortran, C, calculus and a background
of physics are important.

 

[]{#IgProf}Performance Monitoring
---------------------------------

------------------------------------------------------------------------

IgProf (<https://igprof.org>) is a lightweight performance profiling and
analysis tool. It can be run in one of three modes: as a performance
profiler, as a memory profiler, or in instrumentation mode. When used as
a performance profiler it provides statistical sampling based
performance profiles of the application. In the memory profiling mode it
can be used to obtain information about the total number of dynamic
memory allocations, profiles of the \`\`live\'\' memory allocations in
the heap at any given time and information about memory leaks. The
memory profiling is particularly important for C/C++ programs, where
large amounts of dynamic memory allocation can affect performance and
where very complex memory footprints need to be understood. In nearly
all cases no code changes are needed to obtain profiles. IgProf
currently supports Linux and x86/x86-64 architectures, and provides
initial support for ARMv7 one. It correctly handles dynamically loaded
shared libraries, threaded applications and subprocesses. It can be run
entirely in user space without special privileges and produces full
navigable call stacks. The profile reports can be visualized in one of
several ways. A simple text report can be produced from the raw data
saved during the profiling run. Alternatively a web-browsable profile
report can be produced which allows easy navigation of the call stack.
Both allow one to see profile data ordered by symbol in terms of
\`\`cumulative\'\' cost (function plus children) and \`\`self\'\' cost
(time in the function itself) as well as a full call graph view showing
the functions which called, and which were called by, any given
function. An important feature of the web-navigable reports is the
ability to point via URL at particular places in the call graph. This
facilitates collaboration between individuals at different locations.
While there are obviouly many profilers out there, the goal of IgProf is
to provide a reliable profiler for large applications like the one found
in HEP, and to tackle the challenges posed by heterogenous compututing
architectures.

### Profiling mixed python / C++ programs

<div>

**Description**:IgProf currently supports profiling native applications,
most likely written in C / C++. Profiling scripted applications which
invoke native code (e.g. a python framework which invokes C++ plugins)
is supported in the form of raw profile of the python interpreter
itself, which eventually calls the native code functions. While this
kind of profile can already provide insights, it is still desiderable to
be able to profile and visualize the script stacktrace and the native
code one together, in order have a global picture of the connections
between the scripted and native code.

</div>

<div>

**Expected results**: the first objective is to identify and instrument
the parts of the python interpreter which are responsible for
allocating, deallocating and execute python stackframes, eventually
extending igprof instrumentation capabilities to deal with peculiarities
of the python interpreter. The second objective is to collect enough
information via the above mentioned instrumentation to be able to show
mixed python / C / C++ profiles, first for the performance profiler and
subsequently for the memory profiler.

</div>

<div>

**Required knowledge**: Excellent knowledge of C/C++ programming and
understanding of Linux system programming and software execution in
Linux are required. Understanding of python interpreter internals a
plus.

</div>

**Mentors**: [Giulio Eulisse, Peter Elmer, Vincenzo
Innocente](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2012)

 

### Data driven profiling

<div>

**Description**:Most low overhead profilers, including IgProf, only
consider the code being profiled as always behaving in the same way,
regardless of the input data it processes. While this is often the case,
sometimes it is of interest to be able to associate cost of a given
function to its input parameters and / or data sections passed to the
code being profiled in order to identify not only hot code sections, but
hot data patterns too

</div>

<div>

**Expected results**: The first objective is extend igprof so that
different profiling context can be defined, with each context associated
to some interesting data processing. This could be done initially by
code instrumentation (i.e. calling a function which identifies the data
being processed) and then in a more automated manner, e.g. by monitoring
the arguments of user specified functions. The second objective is to
extend the profile visualization to keep the information so collected
into account.

</div>

<div>

**Required knowledge**:Excellent knowledge of C/C++ programming and
understanding of Linux system programming and software execution in
Linux are required.

</div>

**Mentor**: [Giulio Eulisse, Peter Elmer, Vincenzo
Innocente](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2012)

### Support for CUDA / OpenCL profiling

<div>

**Description**:Extend IgProf to gather information from the profiling
APIs of one (or more) of the above mentioned packages. The goal is to be
able to measure the performance cost of mixed CPU / GPU applications,
keeping into account the asynchronous behaviour of those applications,
allowing to track the source of GPU workloads.

</div>

<div>

**Required knowledge**:Excellent knowledge of C/C++ programming and
understanding of Linux system programming and software execution in
Linux are required. Knowledge of the above mentioned toolkits a plus.

</div>

**Mentor**: [Giulio Eulisse, Peter Elmer, Vincenzo
Innocente](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2012)

 

### Enhanced support for ARM, x32 and MacOSX architectures.

<div>

**Description**:Depending on the specific knowledge of the candidate,
the task is to improve support for profiling ARMv7 applications and
introduce initial support for 64bit ARMv8 one or, as an alternative, to
extend the x86 support to include x32 (the 32bit pointers, 64bit data
ABI for Intel compatible processors). An additional task would be to
resurrect OSX support (IgProf used to work on PPC based OSX).

</div>

<div>

**Required knowledge**: Excellent knowledge of C/C++ programming and
understanding of Linux system programming and software execution in
Linux are required. Knowledge of at least one between ARM and x86
assembly language. Knowledge of MacOSX system programming a plus.

</div>

**Mentor**: [Giulio Eulisse, Peter Elmer, Vincenzo
Innocente](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2012)

 

 

[\'Blue sky\' ideas]{#bluesky}
==============================

------------------------------------------------------------------------

 

 

-   **General GPU-vectorized solid:** Create a vectorised/GPU-capable
    solid that can be used in place of the most popular existing solids
    (box, tube, conical & spherical shells), for use in Geant4-GPU and
    vector simulation. Inspired by the approach of James Tickner (see
    article in Computer Physics Communications, Vol 181, Issue 11, Nov
    2010, pages 1821--1832 available at
    <http://dx.doi.org/10.1016/j.cpc.2010.07.001> ).

**Mentor:** [John Apostolakis, Gabriele
Cosmo](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2012%3A%20Vectorised%20Solid)\
**Requirements:** Experience with C/C++, vectorization

-   **New simulation engine:** Create a prototype geometry navigation
    for one particle type with a limited geometry choice (1-2 types of
    volume types) using a high-productivity parallel language ( Chapel,
    X10 ). Benchmark this against existing solutions for the same
    problem. Document the development effort and the pitfalls of the
    language, tools and implementation (potential for a scientific
    report on the coding experience, in addition to the results).

**Mentor:** [John
Apostolakis](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2012)\
**Requirements:** Experience with C/C++ and either Chapel, X10, Cilk+,
SplitC or a similar language is required.

 

 

 

[Mentors]{#mentors}
===================

Here is the list of our mentors and their areas of experitse:

-   [John
    Apostolakis](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%202014%3A%20Geant%20Simulation%20-%20or%20General%20Question), Geant
    simulation (admin)
-   [Lorenzo
    Moneta](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%5D%20Root%20projects), Root
    (admin)
-   [Peter
    Elmer](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%20in%20SFT%5D%20IgProf),
    IgProf
-   [Guilio
    Eulisse](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202014%20in%20SFT%3A%20IgProf%20and%20Profiling),
    IgProf
-   [Vincenzo
    Innocente](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202014%20in%20SFT%3A%20IgProf%20and%20Profiling),
    IgProf
-   [G](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%20CernVM)[errardo
    Ganis](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%20CernVM), CernVM
-   [Vincenzo
    Innocente](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%5D%3A%20Linux-perf%20Blue%20Sky),
    IgProf
-   [Riccardo De
    Maria](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%3A%20SixTrack%20Accelerator%20Simulation), Sixtrack 
-   [E](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%3A%20SixTrack%20)[ric
    McIntosh](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202014%3A%20Sixtrack%20Accelerator%20Simulation),
    Sixtrack
-   [Vassil
    Vassilev](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%20Cling),
    Cling
-   [S](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%202013%3A%20Geant4)[andro
    Wenzel](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202014%5D%20%3A%20Geant%20Simulation),
    Geant simulation

 

[Contact information]{#contact}
===============================

Please do not hesitate to contact us if you are planning to apply for
any of the above projects:

-   SFT GSoC mailing list:
    [sft-gsoc-AT-cern-DOT-ch](mailto:sft-gsoc-AT-cern-DOT-ch?subject=GSOC%2012)
    (no subscription needed).
-   SFT GSoC Jabber/XMPP chat room: <gsoc-sft@conference.jabber.org> .
    We noticed that Gmail/Gtalk XMPP accounts have problems posting
    messages to the chat room, so please register yourself an XMPP
    account on some other server (it takes no time to register an
    account at http://www.jabber.org).
-   IRC is restricted at CERN - please use Jabber instead.
