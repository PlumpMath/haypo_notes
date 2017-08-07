.. _cpython-windows:

++++++++++++++++++++++++++
Compile CPython on Windows
++++++++++++++++++++++++++

See also :ref:`Windows <windows>` and :ref:`CPython <cpython>`.

Build a Windows VM
==================

* Windows 10 or newer is recommanded
* 60 GB of disk space or more is recommanded


Python and Visual Studio version matrix
=======================================

================  =================
Python version    Visual Studio
================  =================
Python 2.7        2008 **and** 2010
3.5, 3.6, master  2015
================  =================


Dependencies
============

* Python master needs binary dependencies from
  `github.com/python/cpython-bin-deps
  <https://github.com/python/cpython-bin-deps>`_ and source dependencies
  from `github.com/python/cpython-source-deps
  <https://github.com/python/cpython-source-deps>`_ using Git
* Python 2.7 needs dependencies from `svn.python.org/projects/external
  <http://svn.python.org/projects/external/>`_ using Subversion.

See ``PCBuild/get_externals.bat``.


Compile the master branch
=========================

To build the Python ssl extension:

Need:

* Visual Studio 2015
* CPython source code: get it using Git

XXX old requirements, still needed?

* svn.exe in PATH: install TortoiseSVN, but check the [x] command line tools in
  the installer
* ActivePerl: Community Edition, 64-bit

Commands::

    PCbuild\build -p x64 -d -e

See also: ``PCbuild/readme.txt``.


Compile CPython 2.7
===================

Compile CPython 2.7 on Windows using Visual Studio 2008 and 2010
----------------------------------------------------------------

While Visual Studio 2008 is enough to build a basic Python 2.7 binary without
OpenSSL nor Tkinter, installing Visual Studio 2008 **and** Visual Studio 2010
is recommended to get all dependencies including Tkinter.

Requirements:

* MSDN account to get Visual Studio 2008. Maybe it's possible to build Python
  using the Express edition of VS 2008 and 2010, but in 2017, it became
  difficult to get VS 2008 and 2010 Express.
* Windows 10 or newer is recommanded, even if Python 2.7 is supposed to support
  Windows XP!
* Visual Studio 2008 Professional. Visual Studio 2008 Express works too, but
  doesn't provide a 64-bit compiler.
* Visual Studio 2010 Professional. Maybe a lighter flavor works, I didn't try.

Steps:

* Open a Visual Studio 2010 Prompt
* In this prompt, run ``PCBuild\build.bat -e -d -p x64`` to build Python 2.7 in
  debug mode for 64-bit, and install dependencies like OpenSSL, Tcl and Tk
  sources.

Compile CPython 2.7 on Windows using Visual Studio 2008
-------------------------------------------------------

Similar to the previous section, but don't install Visual Studio 2010: only
install Visual Studio 2008.

Without Visual Studio 2010, some features don't work, like Tkinter.

* Project file: PC\VS9.0\pcbuild.sln
* In this prompt, run ``VS\9.0\build.bat -e -d -p x64`` to build Python 2.7 in
  debug mode for 64-bit, and install dependencies like OpenSSL sources if
  needed


