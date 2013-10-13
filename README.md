# gitlab-dpkg
Debian-Folder to build GitLab DPKG-Package.

## Prepare Build-Folder

    git clone https://github.com/gitlabhq/gitlabhq gitlab_6.1.0

    cd gitlab_6.1.0 && git checkout v6.1.0

    git clone https://github.com/gitlabhq/gitlab-shell

    cd gitlab-shell && git checkout v1.7.1

    cd ../.. && tar -zcf gitlab_6.1.0.orig.tar.gz gitlab_6.1.0

    cd gitlab_6.1.0 && git clone https://github.com/Danie/gitlab-dpkg debian

    cd debian && git checkout squeeze-6-1-stable

## Prepare Debian Squeeze

    cat > /etc/apt/sources.list.d/daniels.list << EOF
    deb http://176.28.19.74/ squeeze-daniels-backports main contrib non-free
    deb-src http://176.28.19.74/ squeeze-daniels-backports main contrib non-free
    EOF

    cat > /etc/apt/preferences.d/daniels.pref << EOF
    Package: *
    Pin: release n=squeeze-daniels-backports
    Pin-Priority: 50
    EOF

    wget -O - http://176.28.19.74/key.asc | apt-key add - && apt-get update

    apt-get install autoconf automake bundler debhelper libcurl4-openssl-dev libffi-dev libgdbm-dev libicu-dev libmagic-dev libmysqlclient-dev libncurses5-dev libpq-dev libreadline-dev libruby libssl-dev libxml2-dev libxslt1-dev libyaml-dev quilt ruby ruby-dev zlib1g-dev

## Build Package:

    cd .. && dpkg-buildpackage
