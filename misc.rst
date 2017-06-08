++++++++++++++
Unsorted Notes
++++++++++++++

.. image:: great_flamingo.jpg
   :alt: Great Flamingo
   :align: right
   :target: http://www.flickr.com/photos/haypo/11915292626/

GitHub
======

Fedora::

    sudo dnf install -y hub

Download a pull request::

    git checkout -b pr104
    git am -3 https://github.com/python/cpython/pull/104

URLs:

* Add ``?w=1`` in a pull request to ignore whitespace changes
* Add ``.patch`` to a pull request to get the change as an unified diff
* In a message, ``<details> ... </details>`` creates a drop-down

vim for developer
=================

In these examples, I'm using Mercurial with the command "hg". To use git, just
replace "hg" with "git". I prefer the graphical editor gvim. To use the console
version, replace "gvim" with "vim".

View differences::

    hg diff | gvim -

Shortcuts:

* ``a/asyncio/events.py``: to open the file, delete ``a\``, put the cursor
  on the file type, type ``vs`` for a vertial split, and type ``gf`` (goto
  file) to open the file
* ``%bd``: close all buffers

Python:

* ``[[``, ``]]``: jump to previous/next of the class or fnuction



Fedora
======

Search a package without updating yum cache::

    yum search -C pattern

Which package provides the program route? ::

    $ rpm -qf $(which route)
    net-tools-2.0-0.15.20131119git.fc20.x86_64

Or if the package is not installed::

    $ yum whatprovides route
    ...
    net-tools-2.0-0.15.20131119git.fc20.x86_64 : Basic networking tools
    ...
    Nom de fichier: /usr/sbin/route

Listing the files in a package::

     rpm -ql mongodb-server

Install dependencies to build the package digikam::

    yum-builddep digikam

Rebuild a Fedora package
------------------------

Rebuild a package: `Fedora Source RPM <http://hacktux.com/fedora/source/rpm>`_.

If you get a .src.rpm package, you can rebuild it with::

    rpmbuild --rebuild wrk-3.1.0-1.fc21.src.rpm

Unpack RPM
----------

Unpack file.rpm in a new dir/ subdirectory::

    mkdir dir
    cp file.rpm dir/
    cd dir
    rpm2cpio file.rpm | cpio -idmv


Code search
===========

* http://code.ohloh.net/
* https://github.com/search/
* http://searchcode.com/
* https://codesearch.debian.net/
* http://stackoverflow.com/search?q=codecs.encode
* specific to OpenStack: http://codesearch.openstack.org/


Git
===

Remove latest commit
--------------------

::

    git reset --hard HEAD~1

List tags containing a specific commit
--------------------------------------

::

    nova$ git tag --contains 94a3b83f9f1fd52a78b9d49b32ddfae40182f852
    12.0.0.0b1
    12.0.0a0
    2014.2
    2014.2.1
    2014.2.2
    2014.2.3
    2014.2.b1
    2014.2.b2
    2014.2.b3
    2014.2.rc1
    2014.2.rc2
    2015.1.0
    2015.1.0b1
    2015.1.0b2
    2015.1.0b3
    2015.1.0rc1
    2015.1.0rc2
    2015.1.0rc3


Remote branches
---------------

* List remote branches: ``git branch -r``
* Create a new branch ``fix_1369426_icehouse`` tracking the remote branch
  ``origin/stable/icehouse``::

    git branch --track fix_1369426_icehouse origin/stable/icehouse

* (Track and) Pull a remote branch::

    git branch --track NAME_REMOTE_BRANCH
    git fetch --all   # or: git pull --all

Send email
----------

First install ``git send-email``. On Fedora::

    yum install -y git-email

Generate a .patch file for a single commit::

    git format-patch origin/master

Generate a patch serie for multiple commits::

    git format-patch origin/master --cover-letter

Now modify ``0000-cover-letter.patch``: replace ``*** BLURB HERE ***``. By
default, patches create a thread on a mailing list: ``[PATCH 0/n]`` is the top
message, ``[PATCH 1/n]``, ``[PATCH 2/n]``, etc. are replied to the top message.
See ``Message-Id`` and ``In-Reply-To`` headers in emails.

To generate a version 2 of a patch (use ``[PATCH v2]`` subject prefix instead
of ``[PATCH]``)::

    git format-patch origin/master --subject-prefix 'PATCH v2'

Send patches::

    git send-email --to=EMAIL --suppress-cc=all *.patch

For your first try, just send emails to yourself ;-)


OpenStreetMap
=============

Map of the town Peypin:

* `OpenStreetMap <http://www.openstreetmap.org/relation/93723>`_
* `Google Maps <https://maps.google.com/maps?ll=43.384146,5.577428&spn=0.005544,0.013368&sll=37.0625,-95.677068&sspn=49.089956,109.511719>`_
* `Yahoo Maps <https://maps.yahoo.com/place/?lat=43.38477800510547&lon=5.580840110778809&bb=43.391405312706%2C5.564478635787964%2C43.37816556912287%2C5.597201585769653&addr=Peypin%2C France>`_
* `OSMOSE <http://osmose.openstreetmap.fr/fr/map/#zoom=15&lat=43.38312&lon=5.57648&layer=Mapnik&overlays=FFFFFFFFFFFFFFFFFFFT&item=xxxx&level=1%2C2%2C3&tags=&fixable=&bbox=0.1373291015625%2C42.53689200787317%2C7.0751953125%2C45.98169518512228>`_
* `BANO <http://layers.openstreetmap.fr/?zoom=16&lat=43.38333&lon=5.5835&layers=B0000FFFFFFFFFFFFFFFFFFFFFFT>`_
* `KeepItRight <http://keepright.at/report_map.php?lang=fr&ch30=1&ch40=1&ch50=1&ch70=1&ch90=1&ch100=1&ch110=1&ch120=1&ch130=1&ch150=1&ch160=1&ch170=1&ch180=1&ch191=1&ch192=1&ch193=1&ch194=1&ch195=1&ch196=1&ch197=1&ch198=1&ch201=1&ch202=1&ch203=1&ch204=1&ch205=1&ch206=1&ch207=1&ch208=1&ch210=1&ch220=1&ch231=1&ch232=1&ch270=1&ch281=1&ch282=1&ch283=1&ch284=1&ch285=1&ch291=1&ch292=1&ch293=1&ch294=1&ch295=1&ch296=1&ch297=1&ch298=1&ch311=1&ch312=1&ch313=1&ch320=1&ch350=1&ch370=1&ch380=1&ch401=1&ch402=1&ch411=1&ch412=1&ch413=1&number_of_tristate_checkboxes=8&highlight_error_id=0&highlight_schema=0&lat=43.38304&lon=5.57771&zoom=16&show_ign=1&show_tmpign=1&layers=B0T&ch=0%2C30%2C40%2C50%2C70%2C90%2C100%2C110%2C120%2C130%2C150%2C160%2C170%2C180%2C191%2C192%2C193%2C194%2C195%2C196%2C197%2C198%2C201%2C202%2C203%2C204%2C205%2C206%2C207%2C208%2C210%2C220%2C231%2C232%2C270%2C281%2C282%2C283%2C284%2C285%2C291%2C292%2C293%2C294%2C295%2C296%2C297%2C298%2C311%2C312%2C313%2C320%2C350%2C370%2C380%2C401%2C402%2C411%2C412%2C413>`_
* `viamichelin <http://www.viamichelin.fr/web/Cartes-plans/Carte_plan-Peypin-13124-Bouches_du_Rhone-France-D46A?strLocid=35MTE1NHRhajA2MjdldzF5NjMyaGtuYTQyOTljMTAyMnNjTkRNdU16ZzBNems9Y05TNDFOemMyTnc9PQ==&loc=no&layers=00000001&zoomLevel=12&strCoord=5.57767*43.38439>`_
* `Cadastre <http://www.cadastre.gouv.fr/scpc/afficherCarteCommune.do?c=80073&dontSaveLastForward&keepVolatileSession=>`_

Marseille user group:

* https://wiki.openstreetmap.org/wiki/Marseille#Rencontres_mensuelles
* https://wiki.openstreetmap.org/wiki/Marseille/R%C3%A9unions_2014
* http://listes.openstreetmap.fr/wws/info/local-marseille

Wiki:

* http://wiki.openstreetmap.org/wiki/FR:Quality_assurance
* http://wiki.openstreetmap.org/wiki/FR:Map_Features
* `BANO <http://wiki.openstreetmap.org/wiki/WikiProject_France/WikiProject_Base_Adresses_Nationale_Ouverte_(BANO)>`_


Shell script
============

* `bash8 <https://pypi.python.org/pypi/bash8>`_: A pep8 equivalent for bash
  scripts
* `checkbashisms <http://freecode.com/projects/checkbashisms>`_: static
  analysis tool for shell scripts. It looks for particular patterns which
  indicate a script might be relying on /bin/sh being bash.
* `shellcheck <http://www.shellcheck.net/>`_: static analysis and linting tool
  for sh/bash scripts


Ftrace
======

* LWN articles:

  - `Secrets of the Ftrace function tracer <http://lwn.net/Articles/370423/>`_
  - `Debugging the kernel using Ftrace - part 1 <http://lwn.net/Articles/365835/>`_
  - `A look at ftrace <http://lwn.net/Articles/322666/>`_
  - `Debugging the kernel using Ftrace - part 2 <http://lwn.net/Articles/366796/>`_
  - `Ftrace: The hidden light switch <http://lwn.net/Articles/608497/>`_

* `ftrace - Function Tracer
  <https://www.kernel.org/doc/Documentation/trace/ftrace.txt>`_: official
  documentation from the kernel
* `ftrace at elinux.org <http://elinux.org/Ftrace>`_
* `Kernel dynamic memory analysis <http://elinux.org/Kernel_dynamic_memory_analysis>`_
* `Installing and Using Ftrace <http://omappedia.org/wiki/Installing_and_Using_Ftrace>`_


Mercurial
=========

.. _hg-bisect:

bisect with a command
---------------------

Shell script ``cmd.sh``::

    set -e -x
    make
    ./python script.py

where ``script.py`` is the script to reproduce the bug.

Cleanup everything::

    hg bisect --reset
    hg update -C

We know that the most recent version is bad (``./cmd`` fails)::

    ./cmd.sh
    # cmd.sh failed
    hg bisect -b

Find a good revision using a date::

    hg up -r "branch(default) and date('May 2015')"
    ./cmd.sh
    # it's still failing, take an older date
    hg up -r "branch(default) and date('Jan 2015')"
    ./cmd.sh
    # iterate until the test pass
    (...)
    hg bisect -g

Ok, we have a good and a bad revision, and a script to automate the bisection::

    hg bisect --command ./cmd.sh
    # enjoy watching your computer working for you


cannot edit immutable changeset: xxx
------------------------------------

You can force the phase of a changeset back to draft like so::

    hg phase -d -f <changeset_id>

Only do that for private changes!


Find tags containing a specific changeset
-----------------------------------------

Let's say that you want to check which versions contains the _FUTURE_CLASSES
variable::

    $ grep '_FUTURE_CLASSES =' trollius/*.py
    trollius/futures.py:    _FUTURE_CLASSES = (Future, events.asyncio.Future)
    trollius/futures.py:    _FUTURE_CLASSES = Future

    $ hg blame trollius/futures.py|grep '_FUTURE_CLASSES ='
    1712:     _FUTURE_CLASSES = (Future, events.asyncio.Future)
    1688:     _FUTURE_CLASSES = Future

    $ hg log -r 1688 --template '{date|isodate}\n'
    2014-07-25 10:05 +0200

Ok, so the _FUTURE_CLASSES was added by the changeset ``1688`` which was made
the 2014-07-25. We pick the oldest changeset, ``1712`` was probably a fix.

Find the tags which contains the changeset ``1688``::

    $ hg log -r "reverse(descendants(1688)) and tag()" --template "{tags}\t{rev}:{node|short}\n"
    trollius-1.0.2  1767:41ac07cd2d03
    trollius-1.0.1  1738:83e574a42e16

    $ hg log -r trollius-1.0.1 --template '{date|isodate}\n'
    2014-07-30 17:45 +0200
    $ hg log -r trollius-1.0.2 --template '{date|isodate}\n'
    2014-10-02 16:47 +0200

The _FUTURE_CLASSES was introduced in trollius-1.0.1 which was released the
2014-07-30.  The following release trollius-1.0.2 (2014-10-02) also contains
it, which is expected since trollius-1.0.2 is based on trollius-1.0.1.

Check versions::

    $ hg up trollius-1.0.1
    $ grep '_FUTURE_CLASSES =' trollius/*.py
    trollius/futures.py:    _FUTURE_CLASSES = (Future, events.asyncio.Future)
    trollius/futures.py:    _FUTURE_CLASSES = Future

    $ hg up trollius-1.0
    $ grep '_FUTURE_CLASSES =' trollius/*.py
    trollius/tasks.py:    _FUTURE_CLASSES = (futures.Future, asyncio.Future)
    trollius/tasks.py:    _FUTURE_CLASSES = futures.Future

Ok, so in fact the variable was moved from the Python module ``trollius.tasks``
to the modle ``trollius.futures`` between versions 1.0 and 1.0.1.

abort: can't rebase public changeset fb6b735060b5
-------------------------------------------------

Error::

    abort: can't rebase public changeset fb6b735060b5
    (see "hg help phases" for details)


Misc
====

* `Linux: detect launching of programs <https://stackoverflow.com/questions/6075013/linux-detect-launching-of-programs>`_ (StackOverflow)
* `MLVPN - MultiLink Virtual Public Network <http://www.mlvpn.fr/>`_
* Docker: https://linuxfr.org/news/docker-tutoriel-pour-manipuler-les-conteneurs
* `Forensically <https://29a.ch/photo-forensics/>`_: tools to check if a photo
  was modified


Share files files from Linux to OSX
===================================

I tried NFS: issues with non-ASCII characters, issue with Unicode NFC
normalization on OS X. Since OS X 10.9, the only way is to use the command line
to pass the option ``-o nfc`` to ``mount -t nfs ...``.

I tried Samba: well, it's not easy. Let's say that the directory to share is
``/data``.

Prepare permissions, readable by everybody, UNIX and SELinux permissions::

    sudo find  /data -type f -print0|xargs -0 chmod 644
    sudo find -type d -print0|xargs -0 chmod 755
    sudo semanage fcontext -a -t samba_share_t "/data(/.*)?"
    sudo restorecon -R -v data/

Install Samba::

    sudo yum install samba samba-common samba-client cups-lib system-config-samba

Use ``system-config-samba`` to share ``/data``:

* run ``sudo system-config-samba``
* add ``/data`` directory as ``public`` and make it readable for everybody
* add a Windows user which is binded to your user (Preference, Samba users)

Start Samba server and run it at boot::

    sudo systemctl start smb.service
    sudo systemctl start nmb.service
    sudo systemctl enable smb.service
    sudo systemctl enable nmb.service

Mac OS X:

* Finder, Go, Access server: use ``smb://192.168.0.1/data`` URL
* Type the user and password
* Enjoy!

Very good tutorial for Fedora 20:  `How to enable samba share for a specific
directory - Fedora 20
<https://ask.fedoraproject.org/en/question/40353/how-to-enable-samba-share-for-a-specific-directory-fedora-20/>`_.


Friends
=======

* http://blog.sileht.net/
* http://www.florentflament.com/
* http://yeknan.free.fr/dc2/

Fun:

* http://tumourrasmoinsbete.blogspot.fr/
* http://www.commitlogsfromlastnight.com/


systemd
=======

list servers
------------

Find the name of the systemd unit for MariaDB or RabbitMQ server.

List all installed services, including disabled services, and search for "maria"::

    systemctl list-unit-files --type=service | grep maria

Alternative if you know the package::

    $ rpm -ql mariadb-server|grep service
    /usr/lib/systemd/system/mariadb.service

List enabled services::

    systemctl list-units

Note: it looks like "list-units" doesn't show mariadb.service, probably because
it is disabled (not started at boot).


system logs (syslogs), journald
-------------------------------

* Show syslog from the most recent to the oldest logs: ``journalctl --reverse``
* Show all logs since the last boot: ``journalctl -b 0``
* List boots: ``journalctl --list-boots``
* ``tail -f /var/log/syslog``: ``journalctl -f``
* ``tail -f /var/log/syslog`` but only for apache: ``journalctl -u apache.service -f``


getaddrinfo
===========

* `A surprising discovery on converting IPv6 addresses: we no longer prefer
  getaddrinfo()
  <http://blog.powerdns.com/2014/05/21/a-surprising-discovery-on-converting-ipv6-addresses-we-no-longer-prefer-getaddrinfo/>`_
  (PowerDNS blog,  May 2014)
* glibc 2.15 (March 2012):
  `Avoid __check_pf calls in getaddrinfo unless really needed
  <https://sourceware.org/git/?p=glibc.git;a=commit;h=fa3fc0fe5f452d0aa7e435d8f32e992958683819>`_
* `Python issue: getaddrinfo is wrongly considered thread safe on linux
  <https://bugs.python.org/issue21216>`_
* `libc6: getaddrinfo() sends DNS queries to random file descriptors
  (CVE-2013-7423) <https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=722075>`_
  (glibc 2.13, fixed at least in glibc 2.19)


PostgreSQL
==========

Install PostgreSQL server on Fedora 21. Type as root::

    yum install postgresql-server
    postgresql-setup initdb

Modify ``/var/lib/pgsql/data/postgresql.conf`` to accept connections from
192.168.0.0/24 network, replace::

    #listen_addresses = 'localhost'         # what IP address(es) to listen on;
    ...
    max_connections = 100                  # (change requires restart)


with::

    listen_addresses = '*'
    ...
    max_connections = 1000                  # (change requires restart)

Modify ``/var/lib/pgsql/data/pg_hba.conf`` to allow login using a password from
192.168.0.0/24 network, replace::

    host    all             all             127.0.0.1/32            ident

with::

    host    all             all             192.168.0.0/24          md5

Start PostgreSQL::

    systemctl start postgresql


Switch to the ``postgres`` user (``sudo -u postgres -H -s``), open the psql
client (``psql``) and type::

    CREATE USER bigdata;
    ALTER ROLE bigdata WITH CREATEDB;
    ALTER USER bigdata WITH ENCRYPTED PASSWORD 'password';
    CREATE DATABASE bigdata;

* http://doc.fedora-fr.org/wiki/Installation_et_configuration_de_PostgreSQL


Google
======

What Google knowns on you:

* https://myactivity.google.com/
* https://myaccount.google.com/
* https://maps.google.fr/locationhistory/


.. _operating-systems:

Operating systems
=================

`macOS (Mac OS X) versions
<https://en.wikipedia.org/wiki/MacOS#Release_history>`_:

==============  ============== ==============  ============
Mac OS X        Name           Darwin Version  Release Year
==============  ============== ==============  ============
Mac OS X 10.12  Sierra         16.x            2016
Mac OS X 10.11  El Capitan     15.x            2015
Mac OS X 10.10  Yosemite       14.x            2014
Mac OS X 10.9   Mavericks      13.x            2013
Mac OS X 10.8   Mountain Lion  12.x            2012
Mac OS X 10.7   Lion           11.x            2010
Mac OS X 10.6   Snow Leopard   10.x            2008
Mac OS X 10.5   Leopard        9.x             2006
Mac OS X 10.4   Tiger          8.x             2004
==============  ============== ==============  ============

* `Microsoft Windows versions
  <https://en.wikipedia.org/wiki/List_of_Microsoft_Windows_versions>`_:

  - Windows 10: (under development)
  - Windows 8.1: 2013
  - Windows 8: 2012
  - Windows 7: 2009
  - Windows Vista: 2007
  - Windows XP: 2001

* `Linux kernel versions
  <https://en.wikipedia.org/wiki/Linux_kernel#Maintenance>`_:

  - 4.0: 2015 (under development)
  - 3.0: 2011
  - 2.6: 2003
  - 2.4: 2001

* `Ubuntu releases
  <https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions>`_:

  - 16.10: Yakkety Yak (not released yet, scheduled for 2016-10-20)
  - 16.04 LTS: Xenial Xerus, 2016-04-21
  - 15.10: Wily Werewolf, 2015-10-22
  - 15.04: Vivid, 2015-04
  - 14.10: Utopic, 2014-10
  - 14.04 LTS: Trusty, 2014-04
  - 12.04 LTS: Precise, 2012-04

* `Fedora releases
  <https://en.wikipedia.org/wiki/Fedora_%28operating_system%29#Releases>`_:

  * Fedora 24: 2016-06-21
  * Fedora 23: 2015-11-03
  * Fedora 22: 2015-05-26
  * Fedora 21: 2014-12
  * Fedora 20: 2013-12, Heisenbug
  * Fedora 19: 2013-07, Schrödinger's Cat

* `FreeBSD releases <https://en.wikipedia.org/wiki/FreeBSD#Version_history>`_:

  * FreeBSD 10: 2014-01
  * FreeBSD 9: 2012-01
  * FreeBSD 8.1: 2010-07
  * FreeBSD 7: 2008-02
  * FreeBSD 6.2: 2007-01

Programming advices
===================

* Coding style: 80 columns, PEP 7 for C, PEP 8 for Python
* Avoid variable globals
* Signal handlers: only use signal-safe functions


Timezones
=========

* Debian issue: `tzdata: Argentina just decided not to move to DST this Sunday :-\
  <https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=551195>`_
* Python issue: `datetime: support leap seconds
  <https://bugs.python.org/issue23574>`_


rsync
=====

Local copy with progress bar and handle sparse files::

    rsync -Sav --progress /mnt/vm/images/ /var/lib/libvirt/images/

Thunderbird
===========

`Checking for new messages in other folders - Thunderbird
<http://kb.mozillazine.org/How_do_I_check_for_new_messages_in_other_folders>`_.

Set ``mail.server.default.check_all_folders_for_new=true`` in advanced settings
(Edit > Preference > Advanced > General tab > Config editor).


Gnome-Terminal
==============

Configure Gnome-Terminal to select a full URL double-click::

    dconf write /org/gnome/terminal/legacy/profiles:/:${Profile_ID}/word-char-exceptions '@ms "-,.;/?%&#_=+@~·:"'

Replace ``${Profile_ID}`` with the profile identifier. To get it::

    $ gsettings get org.gnome.Terminal.ProfilesList list
    ['b1dcc9dd-5262-4d8d-a863-c897e6d979b9']

Example::

    dconf write /org/gnome/terminal/legacy/profiles:/:b1dcc9dd-5262-4d8d-a863-c897e6d979b9/word-char-exceptions '@ms "-,.;/?%&#_=+@~·:"'

It looks like you don't have to restart Gnome-Terminal.

http://fedora.12.x6.nabble.com/gnome-terminal-amp-select-by-word-characters-td5043736.html

* https://bugzilla.redhat.com/show_bug.cgi?id=1165244
* https://bugzilla.redhat.com/show_bug.cgi?id=1227222
* https://bugzilla.gnome.org/show_bug.cgi?id=727743
* https://bugzilla.gnome.org/show_bug.cgi?id=730632#c33


Android
=======

Samsung S2, delete logs on internal storage:

* dial ``*#9900#``
* click on: "Delete dumpstate/logcat"

Free space on the 16 GB SD card:

* install CCleaner
* Free space using CCleaner


IRC
===

List operators of channel::

    /msg ChanServ access #python-fr list

Give operator permission to someone::

    /msg ChanServ flags #python-fr skyice +Aeiortv


SSH keygen
==========

Create an SSH key::

    ssh-keygen -t ed25519 -o -a 100 -C "haypo2017" -f ssh_key

* ``-t``: key type, http://ed25519.cr.yp.to/
* ``-a 100``: use 100 rounds of the key derivation function for the passphrase,
  increase resistance to brute-force password cracking
* ``-C``: comment
* ``-f``: filename
* ``-o``: save private keys using the new OpenSSH format, increased resistance
  to brute-force password cracking (in fact, ``-t ed25519`` already enables
  this option)

Issues with ed25519:

* Launchpad doesn't support ed25519: Launchpad is implemented on top of Twisted
  which doesn't support ed25519 yet.
  https://bugs.launchpad.net/launchpad/+bug/1282220
* gnome-keyrign doesn't support the new SSH key format used by ed25519 by
  default:
  https://bugzilla.gnome.org/show_bug.cgi?id=723274
  https://bugzilla.gnome.org/show_bug.cgi?id=641082

Links:

* https://stribika.github.io/2015/01/04/secure-secure-shell.html
* https://wiki.archlinux.org/index.php/SSH_keys

SSH agent:

* Modify /etc/pam.d/* to lines containing "pam_gnome_keyring.so"
* Make sure that login still works after the change!!!

Gnome and SSH passphrase::

    sudo dnf install -y openssh-askpass

Replace gnome-keyring with ssh-agent to support elliptic curves:

* https://ask.fedoraproject.org/en/question/92448/how-do-i-get-proper-ssh-agent-functionality-in-gnome/

Fedora process::

    /usr/bin/gnome-keyring-daemon --daemonize --login

Disable gnome-keyring::

    mkdir -p ~/.config/autostart/
    cp /etc/xdg/autostart/gnome-keyring-ssh.desktop ~/.config/autostart/
    echo "X-GNOME-Autostart-enabled=false" >>~/.config/autostart/gnome-keyring-ssh.desktop

See also https://wiki.archlinux.org/index.php/GNOME/Keyring#Disable_keyring_daemon_components

Enable pam_ssh in PAM config:

* https://wiki.archlinux.org/index.php/SSH_keys
* https://ask.fedoraproject.org/en/question/92448/how-do-i-get-proper-ssh-agent-functionality-in-gnome/


(FR) Transport aérien
=====================

* March 2014: https://fr.wikipedia.org/wiki/Vol_370_Malaysia_Airlines#Hypoth.C3.A8se_d.27un_incident_technique
* April 2016: Batteries lithium-ion interdites dans le transport de fret
  aérien.


Gnome
=====

My CSS theme for window colored borders: https://github.com/haypo/misc/blob/master/conf/gtk.css

https://wiki.gnome.org/Projects/GnomeShell/CheatSheet

gsettings set org.gnome.desktop.wm.preferences focus-new-windows 'strict'


Yubikey
=======

* Fedora: dnf install -y u2f-hidraw-policy
  See https://gist.github.com/fntlnz/a4513162960e1e9fdb99
* Firefox: https://addons.mozilla.org/fr/firefox/addon/u2f-support-add-on/
  https://github.com/prefiks/u2f4moz
* GitHub: https://github.com/settings/two_factor_authentication/configure click on [Register new device]
* Firefox plugin doesn't work on Google nor Bitbucket


Install FreeBSD CURRENT in a VM
===============================

* Download ftp://ftp.freebsd.org/pub/FreeBSD/releases/amd64/amd64/ISO-IMAGES/11.0/FreeBSD-11.0-RELEASE-amd64-disc1.iso.xz
* Uncompress: unxz FreeBSD-11.0-RELEASE-amd64-disc1.iso.xz
* Create a new VM:

  * Name: FreeBSD
  * Boot from an ISO: specify the path to the .iso file
  * System: select Show all, select UNIX, pick FreeBSD 11
  * 1 cpu, 1 GB of RAM
  * Disk size: 20 GB
  * Select network: shared interface, br0

* FreeBSD installer:


  * <install>
  * Keymap: French ISO-8859-1
  * Hostname: freebsd
  * Distribution: only keep [*] ports
  * Partition: auto, <Entire disk>, MBR, Finish, Commit
  * (choose a root password)
  * network: configure IPv4, use DHCP, yes, configure IPv6, auto, yes
  * Time Zone: 8 Europe, 14 France
  * Date/Time: Skip
  * Service started at boot: sshd
  * (no option)
  * Add a new user: username haypo
  * Exit: Manual config? No
  * Reboot

* (After reboot)
* Log as root
* type "pkg sudo" and install it
* run "visudo" and uncomment "%whell ALL.." without password
* add haypo user to the wheel group: pw group mod wheel -m haypo
* Relog as haypo
* sudo pkg install bash git
* chsh: write /usr/local/bin/bash (check before with "which bash")
* Delog, log again as haypo


C aliasing
==========

* ``-fstrict-aliasing`` vs ``-fno-strict-aliasing``
* ``__restrict__`` (or just ``restrict``)
* clang "bug": `aliasing bug with union in clang 4.0
  <https://bugs.llvm.org//show_bug.cgi?id=31928>`_
* `Understanding Strict Aliasing
  <http://cellperformance.beyond3d.com/articles/2006/06/understanding-strict-aliasing.html>`_
  (Mike Acton, June 1, 2006)
* `Demystifying The Restrict Keyword
  <http://cellperformance.beyond3d.com/articles/2006/05/demystifying-the-restrict-keyword.html>`_
  (Mike Acton, May 29, 2006)
* `Type-punning and strict-aliasing
  <http://blog.qt.io/blog/2011/06/10/type-punning-and-strict-aliasing/>`_
  (Thiago Macieira, June 2011)
* Python 2 slower: the C code base doesn't respect strict aliasing and so must
  be compiled with ``-fno-strict-aliasing`` (to avoid bugs when the compiler
  optimizes the code) which is inefficient. The structure of Python C type has
  been deeply rewritten to fix the root cause.
* `gcc-help: Missed optimization when using a structure
  <https://gcc.gnu.org/ml/gcc-help/2013-04/msg00192.html>`_ (2013-04)
* `GCC -fstrict-aliasing documentation
  <https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html#Type-punning>`_
* `GCC Union documentation
  <https://gcc.gnu.org/onlinedocs/gcc/Structures-unions-enumerations-and-bit-fields-implementation.html#Structures-unions-enumerations-and-bit-fields-implementation>`_
* `Detecting Strict Aliasing Violations
  <http://trust-in-soft.com/wp-content/uploads/2017/01/vmcai.pdf>`_
  by P. Cuoq et. al.

Change which fixed a crash after the merged of the new dict implementation
on a specific platform (don't recall which one!):
https://github.com/python/cpython/commit/186122ead26f3ae4c2bc9f6715d2a29d339fdc5a

Example::

    #include <stdint.h>
    #include <stdio.h>

    uint32_t
    swap_words( uint32_t arg )
    {
      uint16_t* const volatile sp = (uint16_t*)&arg;
      uint16_t        hi = sp[0];
      uint16_t        lo = sp[1];

      sp[1] = hi;
      sp[0] = lo;

      return (arg);
    }

    int main(void)
    {
        uint32_t x = 0xabcd1234;
        uint32_t y = swap_words(x);
        printf("x=%lx\n", (long unsigned int)x);
        printf("y=%lx\n", (long unsigned int)y);
        return 0;
    }

Bug::

    $ LANG= gcc -O3 x.c -o x -fstrict-aliasing -Wstrict-aliasing=2 && ./x
    x.c: In function 'swap_words':
    x.c:7:3: warning: dereferencing type-punned pointer will break strict-aliasing rules [-Wstrict-aliasing]
       uint16_t* const volatile sp = (uint16_t*)&arg;
       ^~~~~~~~
    x=abcd1234
    y=abcd1234


tmux
====

* tmux attach
* tmux ls
* CTRL+b ...

  - ``d``: detach
  - ``c``: new window
  - ``n`` / ``p``: next/previous window
  - ``:``: open the command line ("prompt")
  - ``,``: name the window
  - ``w``: window list
  - ``&``: kill the window

* Command line or "prompt" (opened by CTRL+b :):

  - list-sessions

* `tmux shortcuts & cheatsheet <https://gist.github.com/MohamedAlaa/2961058>`_


Debug Python
============

* Add printf(...) of fprintf(stderr, ...)
* Comment, remove code, add #if 0 ... #endif
* Run git bisect
* Use my new script to bisect test *methods*
