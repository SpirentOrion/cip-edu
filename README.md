# Cloud & IP Engineering Educational Resources

- [Introduction](#introduction)
- [Software Subject Areas](#software-subject-areas)
- [Hardware Subject Areas](#hardware-subject-areas)
- [Contributors](#contributors)

---

## Introduction

The `cip-edu` repository is a curated collection of subject areas that Cloud &
IP engineers and managers can use for career development purposes.

This is not an exhaustive list of what engineers need to know in order to be
successful at Cloud & IP. Nor do all engineers need to know all of this
material. Really, it is just a list that people can use for inspiration or
discovery.

You might notice a general lack of networking-related or STC product-related
subjects. Those things are important, but we tend to always focus on them. Here
we're putting a strong focus on subject areas that pertain to craftsmanship and
implementation.

Subjects areas are loosely categorized, but that's subjective, so take those
categories with a grain of salt. Where possible, specific resources (books,
articles, podcasts, etc.) are linked.

### How to Use

Scan this document. Cherry-pick areas and resources. Learn. Contribute back.

### Please Contribute!

A list like this could never be complete. Please add to it and get your name on the
contributors list! Or fill in some of the sparse spots below. You can do this by
forking the repository, committing a change, and opening a pull request. Don't
know what a pull request is or how they work? Here's a guide:
https://www.thinkful.com/learn/github-pull-request-tutorial/.

---

## Software Subject Areas

### General Knowledge	

POSIX systems programming fundamentals: Systems programming is one of those
bedrock knowledge areas that every SW engineer should have. There are many good
books and tutorials. Stevens' [Advanced Programming in the UNIX
Environment](http://a.co/dMRuNBG) is classic. Also check out the Unix man pages
themselves (sections 2 and 3).

UNIX system administration: Similar to systems programming, every SW engineer
could benefit from knowing a bit about system administration. There are a lot of
older (i.e. early 2000's) books on this topic which are good historical
background. For more modern systems, check out the [Debian Administrator's
Handbook](https://debian-handbook.info/browse/stable/) which is well-written and
maintained. This is a good guide for Debian-based systems (which includes
Ubuntu).

Virtualization fundamentals: The [Wikipedia article on
hypervisors](https://en.wikipedia.org/wiki/Hypervisor) is a great place to start
and you can spider out from there. But there's no substitute for getting your
hands dirty. You've probably already used a hosted hypervisor (VirtualBox,
VMware Desktop, QEMU). If you've never played with a bare metal hypervisor, try
KVM or grab a copy of ESXi (you can get a free copy for personal use by
registering at VMware.com) and set it up on an old PC.

Containerization fundamentals:
[Namespaces](https://en.wikipedia.org/wiki/Linux_namespaces) and [control
groups](https://en.wikipedia.org/wiki/Cgroups) form the basis of
containerization, so it's worth knowing what those kernel subsystems can do. But
what really made containerization take off in the industry were Docker's
innovations around using a simple configuration file (the `Dockerfile`) and
overlay/union filesystems to build container images that can be easily shared.
That, and creative use of overlay networking to allow for service isolation. The
[Docker documentation](https://docs.docker.com/) is the best place to start. You
can learn a lot by reading through the docs and trying some examples. It's easy
to install Docker on modern Linux systems and you can also get Docker for
Windows or Mac. But keep in mind that most examples and tutorials you'll find
are written for Linux. Also, check out how top-tier open source projects
approach containerization by looking at their Dockerfiles on
[hub.docker.com](https://hub.docker.com/explore/).

Code craft: Or, "how not to piss off your co-workers by writing shoddy code". It
is a classic and a bit dated, but you can't really go wrong with [Code Complete
2](http://a.co/cPZxSKz).

["What Every Programmer Should Know About
Memory"](https://www.akkadia.org/drepper/cpumemory.pdf): This "paper" (it's more
like a book) explains modern memory architectures. You may need to skim. It is a
good companion piece for studying in conjunction with "Mechanical sympathy" or
"Data-oriented design" below.

["What Every Computer Scientist Should Know About Floating-Point
Arithmetic"](https://orion.math.iastate.edu/alex/502/doc/p5-goldberg.pdf): This
is a "real" CS paper, with quite a bit of math. Even if that's not your thing,
you can skim this and still learn a great deal. Also, familiarize yourself with
your language's support for arbitrary-precision numbers.

["Latency Numbers Every Programmer Should
Know"](https://gist.github.com/jboner/2841832): This is another aged classic.
Some of the absolute numbers are off now, but those were never the point. If
you're interested in building performant systems, it's the ratios that matter.

Test-Driven Development: TDD arguments can turn into religious wars. Without
getting into that, let's just say that if you're a SW engineer and you're not
writing tests of _some sort_, then you're doing it wrong. The [Wikipedia article
on TDD](https://en.wikipedia.org/wiki/Test-driven_development) will lead you to
all the details, including variations like Behavior-Driven Development. You
should at least know what the `xUnit`-style testing framework is for your
programming language and how to use it.

### Stuff You Probably Learned In School, Have Since Forgotten, But Really Matters

Data structures and complexity analysis: Every practicing SW engineer should
have at least a working knowledge of the typical undergrad CS curriculum in this
area. The classic reference is [Introduction to Algorithms](http://a.co/c9BByD1)
but [The Algorithm Design Manual](http://a.co/5x9ywTY) is more readable and even
entertaining in spots. Bookmark the [Big-O Reference](http://bigoref.com/).
Also, if you can find a way to model your problem as a graph, then you can
probably solve it using a [graph
algorithm](https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/).

Operating system fundamentals: This is the more theoretical side of "POSIX
systems programming". Keep your old OS course textbook around to use as a
reference or borrow someone's. [Editor's note: if anyone has a favorite
reference, please add via a PR].

Concurrent programming models and primitives: This relates to OS fundamentals.
You've got to know the difference between a process, thread, and green thread
(among other things). But you also need to know what your language runtime
offers in terms of concurrency models and primitives. It is difficult to find
one reference that surveys the entire range of concurrent programming models.
You could start by contrasting [shared memory
approaches](https://en.wikipedia.org/wiki/Shared_memory) vs [message-passing
approaches](https://en.wikipedia.org/wiki/Message_passing). Shared memory will
tend to lead you into explorations of threads and synchronization primitives.
Message passing will lead you to channels, actors, coroutines, and processes.
Related, you should also look into
[immutability](https://en.wikipedia.org/wiki/Immutable_object), and whatever
support your language has for immutable variables and data structures.

Lexers and parsers: Why does this matter if you're not writing a compiler?
Because of [that old JWZ quote](http://regex.info/blog/2006-09-15/247) and SW
engineers' tendency to want to hit every nail with a regex sledgehammer. You
absolutely should know regular expressions ([Mastering Regular
Expressions](http://a.co/eksTL7i)), but knowing when not to use them, and being
able to use a parser instead will separate you from the masses. If you have
spare time, read Steve Yegge's epic ["Rich Programmer
Food"](http://steve-yegge.blogspot.com/2007/06/rich-programmer-food.html) for
inspiration. Depending on what language you're using, you may be able to find a
good lexer/parser library and those docs may get you through. If you want a
theoretical text, you could check out ["The Dragon Book"](http://a.co/7esF4Po).
It's the text everyone says to read but it's over-priced and if you try to read
it then you'll find out why everyone hates it. A better alternative might be the
first couple chapters of [Engineering a Compiler](http://a.co/ckTxbne). When it
comes to practical guides, [The Definitive ANTLR4
Reference](http://a.co/0ckAGPs) is good, as is the ANTLR4 parser generator
itself. If you know Golang, or are willing to learn a little bit of it, then
[Writing an Interpreter in Go](http://a.co/4bMlGvM) will teach you what you need
to know in bite-sized pieces. And then you'll be ready to reach for ANTLR4 or
some other parser generator library.

Finite state machines: Most of us know from reading RFCs that state machines
form the basis of many protocols. But they're useful for modeling all sorts of
processes and computations -- especially those that have to interact with the
outside world via I/O. We've probably all written or maintained code that's
trying to manage this sort of thing ad-hoc. Without the rigor of state machines,
how do you make this sort of code reliable and maintainable? Start with the
[Wikipedia article](https://en.wikipedia.org/wiki/Finite-state_machine), and at
least read through the "Classification" section. You can spider out from there.
Depending on your language, you may be able to find libraries that help you
implement state machines. But even if not, thinking about a problem in terms of
an FSM, documenting the FSM, and coming up with any sort of code that mirrors
the FSM would be a huge win compared to the ad hoc approach.

Basic statistics: Fundamentally, our products make measurements and these need
to be processed, interpreted, and presented using statistics. SW engineers
should at least understand [measures of central
tendency](https://en.wikipedia.org/wiki/Central_tendency), [statistical
significance](https://en.wikipedia.org/wiki/Statistical_significance), and
[probability
distributions](https://en.wikipedia.org/wiki/Probability_distribution). It's not
necessary to know how to calculate all of these but you should know that they
exist and what they mean. This is another area where it might be a good idea to
keep that old college textbook around. [Editor's note: if anyone has a favorite
reference, please add via a PR].

Basic queuing theory: Obviously queuing theory is fundamental to performance of
network devices. The [Wikipedia
article](https://en.wikipedia.org/wiki/Queueing_theory) is a good starting
point. The classic text is [Introduction to Queueing
Theory](http://www.cse.fau.edu/~bob/publications/IntroToQueueingTheory_Cooper.pdf),
available for free online. This is "just math", so there are many more reference
texts available.

### Systems Thinking	

["The Architecture of Open Source
Applications"](http://www.aosabook.org/en/index.html): This is actually a series
of books that explore how open source projects are structured, and why. There
are large and small examples. Learning how other people approach system design
is a great place to start.

["Fallacies of Distributed
Systems"](https://pages.cs.wisc.edu/~zuyu/files/fallacies.pdf): Most modern
systems involve more than one CPU and are thus distributed systems. This paper
will give you an appreciation for all the things that ~~can~~ will go wrong.

["End-to-End Arguments in System
Design"](http://web.mit.edu/Saltzer/www/publications/endtoend/endtoend.pdf).
This is an important principle in system design. Eliminate low-level functions
or subsystems that are redundant, unless their cost is justified by performance
improvements.

Mechanical sympathy / Data-oriented design: Martin Thompson popularized the use
of the term "mechanical sympathy" as applied to SW design. He has an [entire
blog about it](https://mechanical-sympathy.blogspot.com/) and he's given many
[conference talks](https://www.infoq.com/presentations/mechanical-sympathy) on
it as well. The concept of "data-oriented design" is related. The best video on
this comes from a talk that Mike Acton gave at [CppCon
2014](https://www.youtube.com/watch?v=92KFSD3ObrY). This is a long video, so if
you're in a hurry you can at least skip over the intro where Mike talks about
how much fun the game development industry is. He starts talking about the title
topic around `10:24`.

["The Tail at
Scale"](http://www.cs.duke.edu/courses/cps296.4/fall13/838-CloudPapers/dean_longtail.pdf):
Large-scale systems have many components that can introduce latency. Even one
such component can dramatically impact a large portion of requests.

[CAP Theorem](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed):
The CAP theorem is often described as "Consistency, availability, or
partition-tolerance. Pick two." That's fun to throw around and leads to debates
about whether "AP" or "CP" is better for this or that. But it is also a
mis-characterization because you can't not pick "P". In a real-world system,
network partitions will happen (see "Fallacies..." above). But the CAP theorem
is still really interesting, and it spawned a lot of thinking that has led to
extensions like ["PACELC"](https://en.wikipedia.org/wiki/PACELC_theorem). Also
check out Kyle Kingsbury's ["Call Me Maybe"](https://aphyr.com/tags/jepsen) blog
series where he absolutely destroys database vendors' claims re: consistency.
Kyle also has some good conference videos.

["A Collection of Postmortems"](https://github.com/danluu/post-mortems): This is
Dan Luu's curated collection of postmortems (write ups that document system
failures). It is interesting reading re: all the ways that real systems have
failed.

["How Complex Systems
Fail"](http://web.mit.edu/2.75/resources/random/How%20Complex%20Systems%20Fail.pdf):
This short paper comes from outside our industry (it was written by an MD!) so
it reads a bit differently. But it is often quoted when it comes to reliability
engineering. It's interesting to think about if you're dealing with system
correctness when people are involved.

["Systems Performance: Enterprise and the Cloud"](http://a.co/56Gy3Lv): This is
a huge book that is packed with good techniques for understanding and improving
system performance. Written by Brendan Gregg, ex-Sun engineer, now at Netflix.
Creator of latency/utilization heatmaps and flamegraphs. Also a DTrace expert.

### Systematic Debugging

Systematic debugging: Dan Luu believes that [systematic debugging can be
taught](https://danluu.com/teach-debugging/). This is a good read. This is also
perhaps an area where we can learn by reading anecdotes. Similar to the
postmortem collection linked above, Dan also maintains a [collection of
debugging stories](https://github.com/danluu/debugging-stories).

["Three Questions About Each Bug You
Find"](http://multicians.org/thvv/threeq.html): Just like with snakes, where
there is one bug, there are probably more. This is a good reminder and some
inspiration for making a bigger system impact when you're debugging.

Code benchmarking: It's not exactly debugging, but since we often have to deal
with performance problems that manifest themselves as CRs, it is good to know
what's available in your language for micro-benchmarking. Check out [Google's
benchmark library](https://github.com/google/benchmark) for C++, the [Golang
profiler](https://blog.golang.org/profiling-go-programs), or [Python's profile
packages](https://docs.python.org/2/library/profile.html).

### Technology-Specific	

Golang: If you want to learn Go, start with the [online
tutorial](https://tour.golang.org/). The [standard
packages](https://golang.org/pkg/) are well-documented and at some point you
should read ["Effective Go"](https://golang.org/doc/effective_go.html) and ["50
Shades of Go"](http://devs.cloudimmunity.com/gotchas-and-common-mistakes-in-go-golang/).

C (at least C99, up to C11): It covers ANSI C, which is older than C99, but
["K&R"](http://cs.indstate.edu/~cbasavaraj/cs559/the_c_programming_language_2.pdf)
should be on every C programmer's shelf. The Wikipedia articles for
[C99](https://en.wikipedia.org/wiki/C99) and
[C11](https://en.wikipedia.org/wiki/C_(programming_language)#C11) are good
references for what is new in each of those specs since K&R.

C++ (at least C++03, up to C++14): The language specifications themselves are
brutal. Check out [The Definitive C++ Book Guide and List
](https://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list/388282#388282)
for a pile of resources that you can use to grok C++.

Design patterns: You probably already have seen ["Gang of
Four"](http://a.co/eSC1not) but if not, you need to be familiar with this
material in order to deal with STC's C++ codebase.

Debugging and profiling tools (gdb, gprof, valgrind, perf): TODO

X86 assembly language: TODO

ARM assembly language: TODO

Python scripting: TODO

Bash scripting: [Google's Shell Style
Guide](https://google.github.io/styleguide/shell.xml) has really useful advice,
not the least of which is "Shell should only be used for small utilities or
simple wrapper scripts". If you're working on shell scripts that will be
committed to any repository anywhere, then you should also get yourself a copy
of [shellcheck](https://github.com/koalaman/shellcheck).

Pros and cons of various encodings (JSON, YAML, XML, Protobuf): The book goes
well beyond encodings, but Chapter 4 of [Designing Data-Intensive
Applications](http://a.co/gnvGlRm) contains a good discussion about when and why
you'd want to use certain encodings. The rest of the book is good too, and the
author, Martin Kleppmann, has some great conference talks.

ZeroMQ: ZeroMQ is a networking library that goes well beyond basic BSD socket
operations and also solves problems at higher layers of abstraction. Its
[guide](http://zguide.zeromq.org/page:all) is a "must read" if you're going to
do any work with ZeroMQ.

Basic and intermediate use of Git: Git has a long tail in terms of tips and
tricks, but you can come up to speed for basic usage with [Pro
Git](https://git-scm.com/book/en/v2), available for free online.

SCons internals: If you're extending our SCons build environment in any
non-trivial way, then you need to understand [builders, actions, and
emitters](http://scons.org/doc/production/HTML/scons-user/ch18.html).

Linux package management (.rpm and .deb): Linux packaging is a solved problem.
Check out the [RPM Packaging Guide](https://rpm-packaging-guide.github.io/) for
RHEL/Centos systems and the [Debian Packaging
Tutorial](https://www.debian.org/doc/manuals/packaging-tutorial/packaging-tutorial.en.pdf)
for Debian/Ubuntu systems.

### Firmware-Specific	

Basics of the major Linux subsystems: TODO

DPDK and PCI hardware/DMA interfacing: TODO
	
### Web-Specific	

Resource-based API design (REST APIs): Resource-based APIs are a different ball
game compared to RPC-style interfaces. "REST" was discovered by Roy Fielding and
is introduced in [Chapter 5 of his PhD
Thesis](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).
This an academic description of an architectural style. As far as the real world
goes, the devil is in the details. You can read about our opinionated choices in
the [Orion REST API
Standards](https://github.com/SpirentOrion/orion-api/blob/master/doc/api/api-standards.md).

Distributed computing models and approaches: [Designing Distributed Control
Systems](http://a.co/6Lcp5p4) takes a pattern-based approach to reasoning about
distributed systems. It won't keep you out of trouble but it will definitely
give you a broad overview. Then you can reach for "Release It!" to help keep you
out of trouble. You may have seen the ["Glider Book"](http://a.co/7Rpw4vY) in
the bookstore and thought that it had something to do with release engineering.
It's nothing of the sort. The [Second Edition](http://a.co/5gNSesh) was released
in January 2018, de-emphasizing capacity management and updating for cloud
deployments.

Fundamentals of SSL/TLS

Relational databases: Schaum's series are a good beginner resource with large
numbers of examples and solved problems: [Fundamentals of Relational
Databases](http://a.co/g1YeTjq) and [Fundamentals of SQL
Programming](http://a.co/hZOHTBN). For further, in-depth reading, check out
[Fundamentals of Database Systems](http://a.co/15RmOLj) or [Database Management
Systems](http://a.co/3a2ODCY).

Data warehousing and star schemas: These warrant a separate set of resources.
Start with [The Star
Schema](http://www.vertabelo.com/blog/technical-articles/data-warehouse-modeling-the-star-schema)
and related articles in that blog.

Time-series/metrics databases (InfluxDB, Prometheus)

Cloud platform basics (AWS, Azure, GCE, OpenStack)

["Twelve Factor Apps"](https://12factor.net/)

["Dapper, A Large Scale Distributed Systems Tracing Infrastructure"](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/36356.pdf)
	
### Soft skills	

Time/task management and efficiency

---

## Hardware Subject Areas

TODO

---

## Contributors

* Barry Andrews
* Cliff Cordeiro
* David Joyner
* Rahul Patel
* Timmons Player
* Vasu Sankaran
* Brian Silverman
