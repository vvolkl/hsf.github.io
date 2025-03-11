[CERN SFT Gsoc 2013 ideas page]{property="dc:title"} {#cern-sft-gsoc-2013-ideas-page .page-header}
====================================================

After experiencing great Google Summer of Code [in
2011](http://google-opensource.blogspot.com/2011/12/cernvms-fruitful-summer.html)
and[ 2012](http://google-opensource.blogspot.fr/2012/12/cern-summer-thrills.html)
we have decided to apply again!

As last year, the project ideas are grouped into categories (ideas
related to [CERN Virtual Machine](#cernvmideas), [Geant 4](#geantideas)
related ideas, and [ROOT](#rootideas) related ideas). We also have a
so-called [\'Blue sky\'](#bluesky) ideas which are rather raw and must
be worked on further before they become projects. The list of ideas is
by no means complete, so if you think you have have a great idea
regarding our projects we are certainly certainly looking forward to
hear from you. The list of our mentors (and their areas of expertise)
can be found [below](#mentors).

![LHC Experiment Software Stack](http://sftweb.cern.ch/img/swstack.png)

The project ideas are (almost) as diverse as the software stack for LHC
experiments is, ranging from twisting the Linux file system layer to the
tracking of an electron through a silicon detector.  All experiments
have software frameworks that make themselves use of common scientific
software libraries for high-energy physics (HEP).  CernVM and CernVM-FS
provide a uniform runtime environment based on Scientific Linux.  The
software stack is fully open sourced and many of its bits and pieces are
used outside the world of particle physics.

 

We encourage students who are planning to apply to do that (and
[**contact us**](#contact)) as early as possible because we have learned
from our previous GSoC experience that an initial student application
often needs to be reworked in close collaboration with a future mentor.
**Please do not forget to provide us with some relevant information
about yourself** (for example CV, past projects, personal page or blog,
linkedin profile, github account, etc.).

 

Before submitting an application please consult the [official GSoC
FAQ](http://www.google-melange.com/gsoc/document/show/gsoc_program/google/gsoc2013/help_page)
where you can find some good advice on writing a successful application.
The application should be submitted through the [GSoC
webapp](http://www.google-melange.com/gsoc/homepage/google/gsoc2013)
before the **3rd of May (19:00 UTC)**.

[Project ideas]{#project}
=========================

[ROOT Object-Oriented data analysis framework]{#rootideas}
----------------------------------------------------------

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

 

#### **Extend Cling\'s Language Support**

<div>

**Description**: Clang (the underlying compiler library) supports
various programming languages besided C and C++. It offers OpenCL, CUDA,
ObjectiveC and ObjectiveC++.  Cling\'s design and implementation are not
bound to support only C/C++.  We propose to improve the inherited
language support in the interpreter by supporting as many languages as
the underlying compiler library (clang) supports.

</div>

<div>

**Expected results**: adjustment of cling\'s custom AST transform
passes, implementing loading of the corresponding language runtime
environment and adding corresponding test cases.

</div>

<div>

**Required knowledge**: intermediate C++, Clang abstract syntax tree
(AST), basic ObjectiveC/C++.

</div>

**Mentor**: [Fons
Rademakers](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%20Extending%20Cling)

 

#### **Implement Pre-run Verification In Cling**

**Description**: The cling interpreter\'s interactive prompt allows a
user to type statements and see the results of their execution. We
propose to enhance Cling\'s execution engine with pre-run verification,
including the detection of a dereference of a null pointer.

**Expected results**: the execution of a NULL pointer dereference does
not causes a crash.

**Mentor:** [Vassil
Vassilev](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20Cling%20Pre-run%20Verification)

<div>

**Required knowledge:** intermediate C++,  knowledge of Clang AST and
LLVM IR.

</div>

 

#### **ROOT --- R interface**

**Description**: Develop an interface in ROOT to call R function using
the R C++ interface  (Rcpp,
see <http://dirk.eddelbuettel.com/code/rcpp.html>). As a proof of
concept implement the Minimizer interface of ROOT to use a R package for
minimization. Developing this interface opens the possibility in ROOT to
use the very large set of mathematical and statistical tools provided by
R.

Implement C++ class(es) to perform a conversion of ROOT C++ object to R
objects, transform the returned R objects into ROOT C++ objects. 

**Expected Results**: One or more C++ classes which perform the
conversion of ROOT C++ object to R objects, able to call R functions and
transform the returned R objects in ROOT C++ objects. The class(es)
should implement some of the existing algorithm interface in ROOT, so
that the R functionality can be used directly for fitting or statistical
studies in ROOT.

**Mentor**: [Lorenzo
Moneta](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2013%20-%20Root%20R%20Interface)

**Requirements**: Basic knowledge of C++.  Knowledge of ROOT and/or R
would be advantages.

 

#### **New Formula class**

**Description**: Develop a new parallel version of the TFormula class in
ROOT using the capabilities of the new Cling interpreter. Having such a
class will allow the user to introduce more complex code, even based on
C++ 11, in defining a formula for a function class.

**Expected Results**: Provide a complete new TFormula class capable of
creating a function with and without parameters from C++ code which can
be parsed and compiled on the fly using Cling.

**Mentor**: [Lorenzo
Moneta](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2013%20-%20Root%20New%20Formula%20Class)

**Requirements**: Basic knowledge of C++.

####  

#### **Implement Automatic Differentiation library using Cling**

<div>

**Description:** In mathematics and computer algebra, automatic
differentiation (AD) is a set of techniques to numerically evaluate the
derivative of a function specified by a computer program. Automatic
differentiation is an alternative technique to Symbolic differentiation
and Numerical differentiation (the method of finite differences). The
automatic differentiation library is to be based on Cling which will
provides the necessary facilities for code transformation.

</div>

<div>

**Expected Result**:  - The AD library is able to differentiate non
trivial functions, to find a partial derivative for trivial cases and
has good unit test coverage.

</div>

<div>

**Mentors**: Vassil Vassilev, Lorenzo Moneta.

</div>

<div>

**Required knowledge**: advanced C++, Clang abstract syntax tree (AST),
basic math.

</div>

<div>

 

</div>

[CernVM & CernVM-FS]{#cernvmideas}
----------------------------------

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

 

#### **Marketplace for VM Contextualization Artifacts**

**Description:** The versatility required to run many different tasks
using the very same virtual machine hard disk image is provided by
\"contextualization\".  By contextualizing a CernVM, one can for
instance specify that a specific virtual machine instance should run
simulation jobs for the ATLAS experiment, or it should connect to the
analysis task queue of the CMS experiment, or it should act as a storage
proxy for other CernVMs.  The contextualization is typically a brief,
textual specification of key value pairs (environment variables), kernel
settings, services to start and scriptlets to run at boot.\
One can easily imagine that quickly one needs to deal with very many
contextualization artifacts, in particular given that not only a single
CernVM can be contextualized but also ensembles of virtual machines can
be defined by contextualization.  Often, the same work has to be done
multiple times by multiple users.  It would be better to consolidate the
contextualization artifacts on a common marketplace.  Contextualization
artifacts could be described, rated, exchanged, and indexed, similar to
an app store, to the recipe repository on puppet forge, or to the
collection of virtual machines provided by TurnKey.

**Expected Result:** Extension of the
[cernvm-online.cern.ch](http://cernvm-online.cern.ch) web application by
functionality to index, exchange, rate, and find contextualization
artifacts.\
**Mentors:** [Jakob Blomer, Predrag
Buncic](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2012)

**Requirements:** Good knowledge of web technologies. Experience with
virtualization and virtual machines will be an asset.

 

#### **CernVM Zookeeper**

A virtual analysis facility (VAF) is an ensemble of virtual machines
running on IaaS resources which, as a whole, offer a data analysis
cluster to physicists.  Such a virtual analysis facility comprises
several virtual machine types, e.g. a storage proxy, a job server, and
worker nodes that do the actual number crunching.  While such an
ensemble of virtual machines can be relatively easily bootstrapped using
the right contextualization artifacts, it is more difficult to maintain
and monitor the cluster, in particular as every physicist might have
several VAFs on several independent IaaS clouds running in parallel.  On
top of that, not all virtual machines have public IP addresses.\
**Description**: This project should extend CernVM by a XMPP component
that, upon boot, connects to an XMPP server and joins a group chat. 
This group chat can then be used by a physicists to control and monitor
its virtual machines, possibly through a web interface but also through
his or her instant messaging client.  (This project can benefit from
previous work on the CernVM Co-Pilot system, a job server for CernVM
based on XMPP.)

**Mentors:** [Jakob Blomer, Predrag
Buncic](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2013)\
**Requirements:** Good knowledge of XMPP and scripting lanugages (Perl,
Python). Experience with virtualization and virtual machines will be an
asset.

 

#### **Garbage Collection for the CernVM File System**

**Context:** In the CernVM-FS internal storage, every file is addressed
by its cryptographic content hash.  Whenever a file is modified, a new
file with a new content is stored internally.  Naturally, this design
results in a versioning file system, i.e. previous versions of files
remain accessible.  In many cases, this can be considered a desirable
feature.\
In some cases, however, it would be better to automatically remove
previous file system versions. Such a case is the hosting of nightly
snapshots of an experiment software development tree on CernVM-FS. The
problem of gathering and removing older revisions of the file system is
amplified by the fact that CernVM-FS repositories can grow to a large
number of files (tens or hundreds of millions) and that any automatic
garbage collection need to be performed online.  Possible approaches can
be the implementation of reference counting or a mark and sweep
algorithm on the CernVM-FS storage.

**Expected Result:** Extension of the CernVM-FS server toolkit (C++ and
bash) that is able to detect garbage generation during regular file
system updates and incrementally removes garbage.\
**Mentors:** [Jakob
Blomer](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2013%20CernVM%20Garbage%20Collection)\
**Requirements:** Good knowledge of C++, file systems, and storage
technologies.\
 

 

-   [Geant 4 Simulation Toolkit]{#geantideas}
    -----------------------------------------

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

\
**Improve Geometry Navigation in Sequential and GPU versions**

**Description:** Locating the volume which corresponds to a position,
and the next boundary along a ray are computationally expensive
operations in a complex geometry.  Geant4 uses a voxelisation technique
which precompute the volumes in 3-d slices of a setup. The first
objective of this project is to investigate how to speedup the
sequential Geant4 navigation. The second objective is to refine the
algorithms used for navigation in a voxelised geometry in the GPU
version of Geant4.

**Mentors:** [John Apostolakis, Gabriele
Cosmo ](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2013%20-%20Geant4%20Geometry)\
**Requirements:** Good knowledge of C++, Object-Oriented Programming,
parallel programming using GPUs are needed. Knowledge of ray tracing
algorithms will be very beneficial.

 

#### **Evaluate language or annotation options for Simulation kernels**

<div>

**Description**: Port key kernels of simulation code to a parallel C++
variant ( Cilk+, SplitC ) and/or OpenAcc/OpenMP and benchmark the effort
and computing speedup obtained.

</div>

<div>

**Mentors:** [John
Apostolakis ](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2013%20-%20Geant4%20Geometry)

####  

**Requirements:** Good knowledge of C++ and exposure to
parallel/vector programming are needed. Experience with OpenMP or
similar technologies, or a parallel C++ variant will be beneficial. 

</div>

<div>

 

</div>

#### **Vectorised implementations of Solids**

**Description: **create vectorised versions of the implementations of
new library of solides (USolids), which is the future library of Solids
for Geant4 and Root.

**Expected result**: Vector versions of UBox and UTubs solid.

**Mentors:** [John Apostolakis, Gabriele
Cosmo](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%2013%20-%20Geant4%20Geometry)

**Requirements**: Knowledge of C++ and vectorisation.

 

Performance Monitoring
----------------------

Linux-perf is a performance tuning component of the Linux kernel. It is
the go-to system for performance tuning activities on Linux, ranging
from software events such as OS context switches to the hardware counter
level (instructions executed, cache misses, etc). CERN, as numerous
other large organizations and companies, makes extensive use of such
performance monitoring features in its daily work. Large portions of the
software powering the Large Hadron Collider science go through systems
such as linux-perf every day.

The main components of a setup with linux-perf are a kernel part and a
userspace tool called "perf", supported by the libpfm library. Work on
the project will provide world-class experience in performance tuning,
Linux software architecture and computer architecture. The student(s)
can also find out how CERN uses its computers to further large-scale
scientific goals.

#### Performance Self Monitoring

**Description: **While external tools for tuning exist today, some
applications need to have performance monitoring facilities built in.
That means that the application - by itself -- can report on its usage
of various hardware features of the platform it runs on. This project
will involve a design and implementation of a C/C++ API to linux-perf
and to libpfm that will allow applications to monitor their own
behavior. Software developments will be preceded by performance studies
of the linux-perf system itself, to establish practical bounds of such
improvements. All work will involve and impact real-world High Energy
Physics software.\
**Mentor**: [Vincenzo Innocente, Andrzej
Nowak](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%3A%20Linux-perf%20Blue%20Sky%5D)\
**Requirements**: Knowledge of C/C++ programming and understanding of
Linux programming and software execution in Linux are required.
Experience with perf and Python is beneficial.

#### Performance tuning: organizing performance data

**Description**: The goal of this project is to design and develop
efficient mechanisms to organize performance data. One problem is that
collected performance data can only be referenced by its location in the
code, but cannot be described by user-defined names or in any other way.
Another issue is that data is collected on the whole program rather than
only some pre-selected routines -- improvements on this will help focus
performance studies. The work will involve developing software solutions
to these challenges, in close collaboration with CERN experts. All work
will focus on and impact real-world High Energy Physics software.\
**Mentor**: [Vincenzo Innocente, Andrzej
Nowak](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%5D%3A%20Linux-perf%20Blue%20Sky)

**Requirements**: Knowledge of C/C++ programming and understanding of
Linux programming and software execution in Linux are required.
Experience with perf and Python is beneficial.\
 

Miscellaneous
-------------

#### **CERN app on Android**

**Description**: A prototype iOS app was created by a GSoC student in
2012 (see
<http://ph-news.web.cern.ch/content/new-ios-application-cern> ) which
provides a wide range of (real-time) information on CERN, the
accelerators, the detectors, the physics, the history, the latest news,
etc. This project foresees to create a similar app for Android. One goal
is to make it extensible so that additional aspects relevant to CERN and
particle physics could be added in future, including displays of LHC
events, mini-simulations or science quizzes. There is the potential for
tens to hundreds of thousands of downloads as the public follows the
restart of the upgraded LHC in 2015.

**Mentors**: [Fons Rademakers, Timur
Pocheptsov](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20CERN%20app%20on%20Android)

**Requirements**: Experience with Android development.

 

#### **Parallelisation of Core Services for High Energy Physics Data Processing**

 The software frameworks for High Energy Physics (HEP) data processing
are C++ programs of millions of lines of code which transform the
electric signals coming from the particle detectors into the building
blocks of exciting discoveries. Frameworks such as Gaudi
([cern.ch/proj-gaudi/](http://proj-gaudi.web.cern.ch/proj-gaudi/))
provide a variety of services: from connection to databases, the
management of the execution of physicists\' code to the interaction with
accelerators and coprocessors.\
With multiple petabytes of experiment data recorded each year, the
overall performance of such frameworks is essential. The partially
interdependent services mentioned above are rather complex entities,
which need considerable time for their initialization, before the actual
physics data processing can start.

**Description**: As the parallelisation of the physics processing
improves, the overhead due to sequential startup becomes an important
issue.  To address this we propose to parallelise the service
initialization in the widely used,  in the GaudiHive
([concurrency.web.cern.ch/GaudiHive](http://concurrency.web.cern.ch/GaudiHive))
multi-threaded extension of the cross-experiment HEP framework Gaudi.\
The task should be accomplished using the functionalities offered by the
C++ language (C++11 standard) and taking advantage of highly optimised,
lock free algorithms and data structures.

**Mentors:** [Danillo Piparo, Benedikt
Hegner](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20Gaudi%20Hive)

**Requirements:** Good knowledge of C++ and parallel programming.
Experience with Python is a plus.

 

#### **Extending Indico**

Indico
([http://indico-software.org](http://indico-software.org/)\<<http://indico-software.org/>\>)
is a web-based event lifecycle management system, room booking
application and collaboration hub (video conference, chat, webcast and
others). It is used at many High Energy Physics laboratories for long
term archival of documents and metadata related to all kinds of events.
 CERN installation
 ([http://indico.cern.ch](http://indico.cern.ch/)\<<http://indico.cern.ch/>\>),
hosts more than 210.000 events, more than 1 million uploaded files and
receives around 14.000 visitors per day. It is installed in more than
100 institutes world-wide
([http://indico-software.org/wiki/IndicoWorldWide).](http://indico-software.org/wiki/IndicoWorldWide%29.)
This generates a need for permanent improvement and development.\
\
The student will gain expertise in web development, acquiring skills in
software engineering good practices, and both development of front-end
(using modern JavaScript-based web technologies and libraries) and
back-end web (Python programming language, Object Oriented Database
(ZODB), Flask, WSGI,\...).  Indico\'s GitHub address
is <https://github.com/indico/indico.>

 

#### **Indico: Abstract editor**

**Description:** Indico is mainly used for events by the physics
community. Physicists, like some other scientists, often need to write
very complex formulas in their paper abstracts, as well adding images
and other types of content. Indico currently provides only a simple web
form to submit plain-text abstracts for a conference. The project is to
enable users to write in different formats (Markdown + MathJax for
formulas, LaTeX, etc) that will allow the generation of beautiful
conference abstracts, which can be published in a Book of Abstracts.

**Mentor**: [Jose Benito Gonzalez Lopez, Pedro
Ferreira](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20Indico)

**Requirements**: Knowledge of Web development and Javascript (jQuery)
technologies are required. Knowledge of Python, git, Markdown, MathJax
for formulas, and/or LaTeX would be beneficial.

 

#### **Indico: On-line Proceedings**

**Description**: The final step for almost every big conference is the
publication of the conference\'s proceedings. Basically, this means a
big book with all the accepted papers of a conference. This final step
is the only one that Indico is missing in order to provide the full
functionality needed to complete the lifecycle of conference
organization. We do not intend to be able to publish a real book but
instead to create digital proceedings. The goal would be to be able to
retrieve all the papers of a given conference and build a very
user-friendly interface with all the publications as well as many
different indexes, filters and search capabilities by content.

**Mentor**: [Jose Benito Gonzalez Lopez, Pedro
Ferreira](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20Indico)

**Requirements**: Knowledge of Web development and Javascript (jQuery)
technologies are required. 

 

[\'Blue sky\' ideas]{#bluesky}
==============================

-   **\"HEPunion\" filesystem implementation as Linux module:** Adapt
    and extend union file system to address the requirements of a HEP
    experiment\'s dedicated farm.\
    **Mentors:** [Pierre Schweitzer, Loic
    Brada](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20Union%20file%20system%20for%20HEP%20Experiment)\
    **Requirements:** Good knowledge of C, Linux and (Linux) Kernel
    development.

<!-- -->

-   **Extend Geant 4 on GPUs:** Extend the Geant4 GPU prototype\'s
    geometry or physics.  Geometry navigation can be extended by
    devoloping additional types of volumes, starting from the geometry
    developed by Otto Seiskari (2010) and Dhruva Tirumala (GSoC 2012) in
    OpenCL/Cuda.  Extending physics can create new processes or
    integrate models from other authors.

**Mentor:** [John
Apostolakis](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%202013%20Geant4%20GPU%20-%20Blue%20sky%20ideas)\
**Requirements:** Experience with C/C++, OpenCL/Cuda

-   **General GPU-vectorized solid:** Create a vectorised/GPU-capable
    solid that can be used in place of the most popular existing solids
    (box, tube, conical & spherical shells), for use in Geant4-GPU and
    vector simulation. Inspired by the approach of James Tickner (see
    article in Computer Physics Communications, Vol 181, Issue 11, Nov
    2010, pages 1821--1832 available at
    <http://dx.doi.org/10.1016/j.cpc.2010.07.001>).

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

-   [John Apostolakis](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC)
    Geant 4 (admin)
-   [Jakob Blomer](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC) CERN
    Virtual Machine, CernVM File System (admin)
-   [Loic
    Brada](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20Union%20file%20system%20for%20HEP%20Experiment) HepUnion
-   [Gabriele
    Cosmo](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSOC%202013%3A%20Geant4) Geant
    4
-   [Pedro
    Ferreira](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20Indico)
    Indico

-   [Jose Benito Gonzalez
    Lopez](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20Indico) Indico
-   [Benedikt
    Hegner](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%5D%20Gaudi%20Hive) Gaudi
    Hive
-   [Vincenzo
    Innocente](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%5D%3A%20Linux-perf%20Blue%20Sky) Performance
    monitoring
-   [Lorenzo
    Moneta](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%5D%20Root%20projects)
    Root
-   [Andrzej
    Nowak](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%5D%3A%20Linux-perf%20Blue%20Sky) Performance
    monitoring
-   [Danillo
    Piparo](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%5D%20Gaudi%20Hive)
    Gaudi Hive
-   [Timur
    Pocheptsov](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20CERN%20app%20on%20Android) Android
    app
-   [Fons
    Rademakers](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%5D%20Android%20App%20or%20Root)
    Portal/Cling
-   [Pierre
    Schweitzer](mailto:sft-gsoc-AT-cern-dot-ch?subject=GSoC%202013%3A%20Union%20file%20system%20for%20HEP%20Experiment) HepUnion
-   [Vassil
    Vassilev](mailto:sft-gsoc-AT-cern-dot-ch?subject=%5BGSoC%202013%5D%20Cling)
    Cling

 
=

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
