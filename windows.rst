.. _windows:

++++++++++++++++++++++++++++++++++++
Survivor Guide to Develop on Windows
++++++++++++++++++++++++++++++++++++

Guide written for Linux developers.

See also :ref:`Python Packaging <python_packaging>` which contains specific
information for Python on Windows.

Useful tools
============

* `ConEmu <https://conemu.github.io/>`_
* `Firefox <http://www.mozilla.com/fr/firefox/>`_
* `7-zip <http://www.7-zip.org/>`_: archive manager (.zip, .tar.gz, .7z, .rar, etc.)
* `Gvim <http://www.vim.org/download.php#pc>`_: text editor gvim (Gtk+ version for Windows)
* `Python <http://www.python.org/>`_
* `MSYS <http://www.mingw.org/wiki/MSYS>`_: terminal using bash for Windows
* `WinSCP <http://winscp.net/>`_: secury file copy on the network (SSH protocl)
* `tortoisehg <http://tortoisehg.bitbucket.org/>`_


Windows console
===============

* Kill a blocked command (harder than CTRL+c): CTRL + Scroll Lock key. (send a
  ``SIGBREAK`` signal)

Note: On my Lenovo T430 laptop, I have to use the "Fn" key:

* Fn + B: Break
* Fn + P: Pause
* Fn + S: SysRq


cmd.exe (Windows "shell", Windows console, the MS-DOS black window)
===================================================================

* Redirect stdout and stderr into the file ``outlog.log``:
  ``command >output.log 2>&1``

====================  ==================  ==========================================================
Windows command       UNIX command        Comment
====================  ==================  ==========================================================
``set``               ``env``             Display all environment variables
``type file.exe``     ``cat file.txt``    Display the content of ``file.txt``
``echo %PATH%``       ``echo $PATH``      Display the value of the ``PATH`` environment variable
``RMDIR /S /Q dir``   ``rm -rf dir``      Remove a directory and its content
``cmd > log``         ``cmd > log``       Redirect command stdout into a new ``log`` file
``cmd >log 2>&1``     ``cmd >log 2>&1``   Redirect command stdout and stderr into a new ``log`` file
``cmd >NUL``          ``cmd >/dev/null``  Ignore command stdout (redirect it to null)
====================  ==================  ==========================================================


Configure vim on Windows
========================

* Right click on gvim: Run as administrator
* Open /program files (x86)/vim/_vimrc
* Comment the lines ``source $VIMRUNTIME/mswin.vim`` and ``behave mswin``
* Add custom config


Mount Windows directory on Linux
================================

Command to mount the Widows "test" directory locally to ``~/mnt``, local
files will be owned by the user ``haypo:haypo``::

    sudo mount.cifs '//192.168.0.14/test' ~/mnt -o 'user=USERNAME,pass=PASSWORD,uid=haypo,gid=haypo'

.. _visual-studio:

Visual Studio
=============

Flavors:

* Express
* Professional: enough to build Python
* Ultimate

Versions:

=============  ======  ========
Visual Studio  MSVC++  _MSC_VER
=============  ======  ========
         2017    14.1      1910
         2015    14.0      1900
         2013    12.0      1800
         2012    11.0      1700
         2010    10.0      1600
         2008     9.0      1500
         2005     8.0      1400
         2003     7.1      1310
         ---      7.0      1300
         ---      6.0      1200
         ---      5.0      1100
=============  ======  ========

Configure a shell to use the VS C compiler in 64-bit mode::

    "%VS140COMNTOOLS%\..\..\VC"\vcvarsall.bat amd64

Argument:

* ``x86``: compile in 32-bit mode
* ``amd64``: compile in 64-bit mode
* ``x86_amd64``: cross-compile to 64-bit mode on a 32-bit system


Git configuration file
======================

Filename: ``C:\Users\haypo\.gitconfig``. Run cmd.exe as administrator to be
allowed to create symbolic links.

See also
========

* :ref:`Compile Python extensions on Windows <py-windows>`
* :ref:`Operating systems <operating-systems>`
