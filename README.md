# gitlab-dpkg
Debian-Folder to build GitLab DPKG-Package.

## Prepare Build-Folder

    git clone https://github.com/gitlabhq/gitlabhq gitlab_5.0.1

    cd gitlab_5.0.1 && git checkout v5.0.1

    git clone https://github.com/gitlabhq/gitlab-shell

    cd gitlab-shell && git checkout v1.1.0

    cd ../.. && tar -zcf gitlab_5.0.1.orig.tar.gz gitlab_5.0.1

    cd gitlab_5.0.1 && git clone https://github.com/Danie/gitlab-dpkg debian

    cd debian && git checkout squeeze-5-0-stable

## Prepare Debian Squeeze

    cat > /etc/apt/sources.list.d/daniels.list << EOF
    deb http://176.28.19.74/ squeeze main contrib non-free
    deb-src http://176.28.19.74/ squeeze main contrib non-free
    EOF

    wget -O - http://176.28.19.74/key.asc | apt-key add - && apt-get update

    apt-get install autoconf automake bundler debhelper libicu-dev libmagic-dev libmysqlclient-dev libpq-dev libruby libxml2-dev libxslt1-dev quilt ruby ruby-dev

## Build Package:

    cd .. && dpkg-buildpackage
