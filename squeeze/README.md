gitlab-dpkg
===========
Debian-Folder to build GitLab DPKG-Package.

Prepare Build-Folder:

1. git clone https://github.com/gitlabhq/gitlabhq gitlab_5.0.1

2. cd gitlab_5.0.1 && git checkout 5-0-stable

3. git clone https://github.com/gitlabhq/gitlab-shell

4. cd gitlab-shell && git checkout v1.1.0

5. cd .. && git clone https://github.com/Danie/gitlab-dpkg debian

6. cd debian && git checkout 5-0-stable

7. cd ../.. && tar -zcf gitlab_5.0.1.orig.tar.gz gitlab_5.0.1

Prepare Debian Squeeze:

1. Insert 'deb http://176.28.19.74/debian/ squeeze main non-free contrib' into /etc/apt/sources.list

2. apt-get install debhelper build-essential git bundler ruby ruby-dev libruby libicu-dev libmagic-dev libmysqlclient-dev libpq-dev autoconf automake quilt libxml2-dev libxslt1-dev

Build Package:

1. cd gitlab_5.0.1 && dpkg-buildpackage

