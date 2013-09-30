# gitlab-dpkg
Debian-Folder to build GitLab DPKG-Package.

## Prepare Build-Folder

    git clone https://github.com/gitlabhq/gitlabhq gitlab_5.0.1

    cd gitlab_5.0.1 && git checkout v5.0.1

    git clone https://github.com/gitlabhq/gitlab-shell

    cd gitlab-shell && git checkout v1.1.0

    cd ../.. && tar -zcf gitlab_5.0.1.orig.tar.gz gitlab_5.0.1

    cd gitlab_5.0.1 && git clone https://github.com/Danie/gitlab-dpkg debian

    cd debian && git checkout wheezy-5-0-stable

## Prepare Debian Wheezy

    apt-get install autoconf automake bundler debhelper libicu-dev libmagic-dev libmysqlclient-dev libpq-dev libruby libxml2-dev libxslt1-dev quilt ruby ruby-dev

## Build Package:

    cd .. && dpkg-buildpackage
