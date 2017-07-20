.. _cpython:

+++++++
CPython
+++++++


Compile CPython on Windows
==========================

See also :ref:`Windows <windows>`.

Compile CPython 3 on Windows
----------------------------

To build the Python ssl extension:

Need:

* Visual Studio 2015 (for Python 3.6)
* CPython source code: get it using Mercurial (TortoiseHG on Windows)
* svn.exe in PATH: install TortoiseSVN, but check the [x] command line tools in
  the installer
* ActivePerl: Community Edition, 64-bit

Commands::

    PCbuild\build -p x64 -d -e

See also: PCbuild/readme.txt.

Compile CPython 2.7 on Windows
------------------------------

* Install Visual Studio 2008: XXX how to get it?
* Open a Visual Studio 2008 Prompt
* In this prompt, run ``VS\9.0\build.bat -e -d -p x64`` to build Python 2.7 in
  debug mode for 64-bit, and install dependencies like OpenSSL sources if
  needed


Developer mode
==============

https://mail.python.org/pipermail/python-ideas/2016-March/039314.html

Enable all runtime debug checks in strict mode::

   PYTHONMALLOC=debug python3.6 -Wd -bb -X faulthandler script.py


CPython infra
=============

Python infrastructure
---------------------

* http://infra.psf.io/
* https://status.python.org/ Status of services maintained by the Python infra
  team
* https://github.com/python/psf-chef/

  - `doc/nodes.rst
    <https://github.com/python/psf-chef/blob/master/doc/nodes.rst>`_
  - `doc/roles.rst
    <https://github.com/python/psf-chef/blob/master/doc/roles.rst>`_

* https://github.com/python/psf-salt/
* PSF pays a full-time sysadmin to maintain the Python infra: XXX
* https://www.python.org/psf/league/
* Managed services: http://infra.psf.io/overview/#details-of-various-services
* http://www.pythontest.net/ used by the test suite, see
  https://github.com/python/pythontestdotnet/

Services used by unit tests
---------------------------

pythontest.net services:

* test_urllib2net: http://www.pythontest.net/index.html#frag, tcp/80 (HTTP)
* FTP: ftp://www.pythontest.net/README
* Copies of unicode text files like http://www.pythontest.net/unicode/EUC-CN.TXT
* test_hashlib test files like http://www.pythontest.net/hashlib/blake2b.txt
* test_httplib: self-signed.pythontest.net, tcp/443 (HTTPS)
* test_robotparser: http://www.pythontest.net/elsewhere/robots.txt
* test_socket: испытание.pythontest.net

See `pythontestdotnet <https://github.com/python/pythontestdotnet>`_: source of
pythontest.net (resources used for Python test suite).

snakebite.net::

    # Testing connect timeout is tricky: we need to have IP connectivity
    # to a host that silently drops our packets.  We can't simulate this
    # from Python because it's a function of the underlying TCP/IP stack.
    # So, the following Snakebite host has been defined:
    blackhole = resolve_address('blackhole.snakebite.net', 56666)

    # Blackhole has been configured to silently drop any incoming packets.
    # No RSTs (for TCP) or ICMP UNREACH (for UDP/ICMP) will be sent back
    # to hosts that attempt to connect to this address: which is exactly
    # what we need to confidently test connect timeout.

    # However, we want to prevent false positives.  It's not unreasonable
    # to expect certain hosts may not be able to reach the blackhole, due
    # to firewalling or general network configuration.  In order to improve
    # our confidence in testing the blackhole, a corresponding 'whitehole'
    # has also been set up using one port higher:
    whitehole = resolve_address('whitehole.snakebite.net', 56667)


Package Index (PyPI)
--------------------

* https://pypi.org/ "Warehouse", the new Python Package Index,

  - https://github.com/pypa/warehouse

* https://pypi.python.org/ "Python Cheeseshop", the old Python Package Index
* Python CDN: http://infra.psf.io/services/cdn/

cpython GitHub project
----------------------

* https://github.com/python/cpython/
* GitHub uses mention-bot: https://github.com/facebook/mention-bot

  * https://github.com/mention-bot/how-to-unsubscribe
  * userBlacklist, userBlacklistForPR in `CPython .mention-bot
    <https://github.com/python/cpython/blob/master/.mention-bot>`_
  * Adding you GitHub login to userBlacklistForPR stops the mention bot from
    mentioning anyone on your PRs.

* https://github.com/python/core-workflow/tree/master/cherry_picker/

Misc
----

* http://bugs.python.org/ Bug tracker (modified instance of Roundup)

  * https://pypi.python.org/pypi/roundup
  * Meta bug tracker: http://psf.upfronthosting.co.za/roundup/meta/
    (bug in the bug tracker software)

* Mailing lists: https://mail.python.org/mailman/listinfo

  - python-dev
  - python-ideas
  - python-list
  - lot of Special Interest Groups (SIG)
  - etc.

* http://buildbot.python.org/

  * `CPython 3.6
    <http://buildbot.python.org/all/waterfall?category=3.6.stable&category=3.6.unstable>`_
  * `CPython 3.x (master)
    <http://buildbot.python.org/all/waterfall?category=3.x.stable&category=3.x.unstable>`_
  * `Custom builders
    <https://docs.python.org/devguide/buildbots.html#custom-builders>`_
  * `buildmaster-config
    <https://github.com/python/buildmaster-config/tree/master/master>`_
    (configuration)
  * `Fork of BuildBot running on buildbot.python.org
    <https://github.com/python/buildbot/>`_

* GitHub CLA bot: XXX

Documentation
-------------

* https://docs.python.org/ Python online documentation
* https://github.com/python/docsbuild-scripts/
* Mirror: http://python.readthedocs.io/en/latest/ Still use the old Mercurial repository.
* https://www.python.org/dev/peps/pep-0545/ i18n doc


Python developer mode
=====================

https://mail.python.org/pipermail/python-ideas/2016-March/039314.html

Strict developer mode::

    PYTHONMALLOC=debug python3.6 -Werror -bb -X faulthandler script.py

Developer mode::

    PYTHONMALLOC=debug python3.6 -Wd -b -X faulthandler script.py

* Show ``DeprecationWarning`` and ``ResourceWarning warnings``: ``python -Wd``
* Show ``BytesWarning`` warning: ``python -b``
* Enable ``faulthandler`` to get a Python traceback on segfault and fatal
  errors: ``python -X faulthandler``
* Debug hooks on Python memory allocators: ``PYTHONMALLOC=debug``
* Enable Python assertions (assert) and set ``__debug__`` to ``True``: remove
  (or just ignore) -O or -OO command line arguments

See also ``PYTHONASYNCIODEBUG=1`` for asyncio.

