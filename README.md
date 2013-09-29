gitlab-dpkg
===========
Debian-Folder to build GitLab DPKG-Package.

Prepare Build-Folder:

1. git clone https://github.com/gitlabhq/gitlabhq gitlab_5.0.1

2. cd gitlab_5.0.1 && git checkout v5.0.1

3. git clone https://github.com/gitlabhq/gitlab-shell

4. cd gitlab-shell && git checkout v1.1.0

5. cd ../.. && tar -zcf gitlab_5.0.1.orig.tar.gz gitlab_5.0.1

6. cd gitlab_5.0.1 && git clone https://github.com/Danie/gitlab-dpkg debian

7. cd debian && git checkout squeeze-5-0-stable


Prepare Debian Squeeze:

1. cat > /etc/apt/sources.list.d/daniels.list << EOF
deb http://176.28.19.74/ squeeze main contrib non-free
deb-src http://176.28.19.74/ squeeze main contrib non-free
EOF

2. wget -O - http://176.28.19.74/key.asc | apt-key add - && apt-get update

3. apt-get install debhelper build-essential git bundler ruby ruby-dev libruby libicu-dev libmagic-dev libmysqlclient-dev libpq-dev autoconf automake quilt libxml2-dev libxslt1-dev

Build Package:

1. cd .. && dpkg-buildpackage

