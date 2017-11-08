++++++++++++++++++++++
C programming language
++++++++++++++++++++++

Issues with types
=================

* comparison between signed and unsigned: who wins? cast signed to unsigned,
  or cast unsigned to signed? => obvious integer overflow
* integer overflow: undefined behaviour, the compiler is free to optimize.
  Check if an operation will overflow is hard, **especially** for signed
  numbers. GCC added builtin functions to check that in a portable and
  efficient way.
* portability: int==long==void*, no warning. if int and long have the same
  size, downcasting a long into an int is allowed, and don't emit any warning.
* int stored in void*
* void* vs intptr_t vs uintptr_t
* Use "int" to access an item of an array in a loop: the compiler may
  have to handle integer overflow. size_t or ssize_t preferred here?

Portability
===========

* Perl still uses C89
* Python only started to move to C99 with Python 3.6, only CPython is
  restricted to a **subset** of C99, the most portable parts of C99...
* GNU extensions of GCC
* glibc vs all other C libraries (ex: musl libc and uclibc). GNU extensions,
  again. Implementation bugs. Errno is sometimes set to 0 on success, sometimes
  it is not set on failure, it depends on the called function and the libc.

Undefined Behaviour
===================

* `What Every C Programmer Should Know About Undefined Behavior #1/3
  <http://blog.llvm.org/2011/05/what-every-c-programmer-should-know.html>`_
* `What Every C Programmer Should Know About Undefined Behavior #2/3
  <http://blog.llvm.org/2011/05/what-every-c-programmer-should-know_14.html>`_
* `What Every C Programmer Should Know About Undefined Behavior #3/3
  <http://blog.llvm.org/2011/05/what-every-c-programmer-should-know_21.html>`_
* GCC Undefined Behavior Sanitizer, ``ubsan``: ``-fsanitize=undefined``
* `Clang UndefinedBehaviorSanitizer
  <https://clang.llvm.org/docs/UndefinedBehaviorSanitizer.html>`_

Strict Aliasing
===============

* `Understanding Strict Aliasing
  <http://cellperformance.beyond3d.com/articles/2006/06/understanding-strict-aliasing.html>`_ (Mike Acton, June 1, 2006)
* `Demystifying The Restrict Keyword
  <http://cellperformance.beyond3d.com/articles/2006/05/demystifying-the-restrict-keyword.html>`_ (Mike Acton, May 29, 2006)

GCC warnings
============

* ``-Wall``: some warnings
* ``-Wall -Wextra``: more warnings
* ``-Wall -Wextra -O3``: even more warnings. Some warnings are only emitted
  when the compiler optimizes the code, like dead code or unused variables.
* There are even more. GCC is able to emit even more warnings, but they must
  be enabled explictly!

Interesting warnings:

* Comparison between signed and unsigned
* Downcasting a type

Platforms #define
=================

* AIX: ``#ifdef _AIX``
* FreeBSD: ``#ifdef __FreeBSD__``
* Linux: ``#ifdef __linux__``
* NetBSD: ``#ifdef __NetBSD__``
* Solaris: ``#ifdef sun``
* Windows: ``_WIN32`` or ``_WIN64``
* macOS: ``#ifdef __APPLE__``


Compiler defines
================

* `GCC <https://gcc.gnu.org/>`_:
  ``#if defined(__GNUC__) && ((__GNUC__ > 4) || ((__GNUC__ == 4) && (__GNUC_MINOR__ > 5)))``
* `Clang <https://clang.llvm.org/>`_:
  ``#ifdef __clang__``
* :ref:`Visual Studio <visual-studio>`:
  ``#if defined(_MSC_VER) && _MSC_VER >= 1800``
