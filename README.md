gitlab-dpkg
===========
Debian-Folder to build GitLab DPKG-Package.

Prepare Build-Folder:

1. git clone https://github.com/gitlabhq/gitlabhq gitlab_5.1.0

2. cd gitlab_5.1.0 && git checkout 5-1-stable

3. git clone https://github.com/gitlabhq/gitlab-shell

4. cd gitlab-shell && git checkout v1.3.0

5. cd ../.. && tar -zcf gitlab_5.1.0.orig.tar.gz gitlab_5.1.0

6. cd gitlab_5.1.0 && git clone https://github.com/Danie/gitlab-dpkg debian

7. cd debian && git checkout squeeze-5-1-stable

Prepare Debian Wheezy:

1. apt-get install debhelper build-essential git bundler ruby ruby-dev libruby libicu-dev libmagic-dev libmysqlclient-dev libpq-dev autoconf automake quilt libxml2-dev libxslt1-dev

Build Package:

1. cd .. && dpkg-buildpackage

