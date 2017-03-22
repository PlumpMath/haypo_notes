++++++++++++++++++++++++++++++++++++
Survivor Guide to Develop on Windows
++++++++++++++++++++++++++++++++++++

Guide written for Linux developers.

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


cmd.exe (Windows "shell", Windows console, the MS-DOS black window)
===================================================================

* Redirect stdout and stderr into the file ``outlog.log``:
  ``command >output.log 2>&1``

====================  ==================  ========================================================
Windows command       UNIX command        Comment
====================  ==================  ========================================================
``set``               ``env``             Display all environment variables
``type file.exe``     ``cat file.txt``    Display the content of ``file.txt``
``echo %PATH%``       ``echo $PATH``      Display the value of the ``PATH`` environment variable
``RMDIR /S /Q dir``   ``rm -rf dir``      Remove a directory and its content
====================  ==================  ========================================================


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


See also
========

* :ref:`Compile Python extensions on Windows <py-windows>`
* :ref:`Operating systems <operating-systems>`
