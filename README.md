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


Prepare Debian Squeeze:

1. echo 'deb http://176.28.19.74/debian/ squeeze main non-free contrib' >> /etc/apt/sources.list.d/danie-repo.list

2. wget -O - http://176.28.19.74/009F5154.key | apt-key add - && apt-get update

3. apt-get install debhelper build-essential git bundler ruby ruby-dev libruby libicu-dev libmagic-dev libmysqlclient-dev libpq-dev autoconf automake quilt libxml2-dev libxslt1-dev

Build Package:

1. cd .. && dpkg-buildpackage

