本次测试使用了aws，貌似不用三分钟就构建完所有镜像了···
```
[root@localhosts zabbix-docker]# docker-compose -f docker-compose_v3_alpine_mysql_local.yaml build
WARNING: Some services (zabbix-agent, zabbix-java-gateway, zabbix-proxy-mysql, zabbix-proxy-sqlite3, zabbix-server, zabbix-snmptraps, zabbix-web-apache-mysql, zabbix-web-nginx-mysql) use the 'deploy' key, which will be ignored. Compose does not support 'deploy' configuration - use `docker stack deploy` to deploy to a swarm.
mysql-server uses an image, skipping
db_data_mysql uses an image, skipping
Building zabbix-java-gateway
Step 1/19 : FROM alpine:3.10
3.10: Pulling from library/alpine

89d9c30c1d48: Downloading [>                                                  ]  28.75kB/2.89d9c30c1d48: Downloading [==================================================>]  2.787MB/2.89d9c30c1d48: Extracting [>                                                  ]  32.77kB/2.789d9c30c1d48: Extracting [===================>                               ]  1.114MB/2.789d9c30c1d48: Extracting [==================================================>]  2.787MB/2.7Digest: sha256:c19173c5ada610a5989151111163d28a67368362762534d8a8121ce95cf2bd5a
Status: Downloaded newer image for alpine:3.10
 ---> 965ea09ff2eb
Step 2/19 : LABEL org.opencontainers.image.title="Zabbix Java Gateway"       org.opencontainers.image.authors="Alexey Pustovalov <alexey.pustovalov@zabbix.com>"       org.opencontainers.image.vendor="Zabbix LLC"       org.opencontainers.image.url="https://zabbix.com/"       org.opencontainers.image.description="Zabbix Java Gateway performs native support for monitoring JMX applications"       org.opencontainers.image.licenses="GPL v2.0"
 ---> Running in b662ff2b8a80
Removing intermediate container b662ff2b8a80
 ---> 8cf7e59bffd3
Step 3/19 : STOPSIGNAL SIGTERM
 ---> Running in 47b50f43bc57
Removing intermediate container 47b50f43bc57
 ---> 58e382e6b19d
Step 4/19 : RUN set -eux &&     addgroup -S -g 1000 zabbix &&     adduser -S             -D -G zabbix             -u 999             -h /var/lib/zabbix/         zabbix &&     mkdir -p /etc/zabbix/ &&     chown --quiet -R zabbix:root /etc/zabbix &&     apk add --clean-protected --no-cache             bash             openjdk8-jre-base &&     rm -rf /var/cache/apk/*
 ---> Running in 6de54b7bb4b8
+ addgroup -S -g 1000 zabbix
+ adduser -S -D -G zabbix -u 999 -h /var/lib/zabbix/ zabbix
+ mkdir -p /etc/zabbix/
+ chown --quiet -R zabbix:root /etc/zabbix
+ apk add --clean-protected --no-cache bash openjdk8-jre-base
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/28) Installing ncurses-terminfo-base (6.1_p20190518-r0)
(2/28) Installing ncurses-terminfo (6.1_p20190518-r0)
(3/28) Installing ncurses-libs (6.1_p20190518-r0)
(4/28) Installing readline (8.0.0-r0)
(5/28) Installing bash (5.0.0-r0)
Executing bash-5.0.0-r0.post-install
(6/28) Installing openjdk8-jre-lib (8.222.10-r0)
(7/28) Installing java-common (0.2-r0)
(8/28) Installing libffi (3.2.1-r6)
(9/28) Installing p11-kit (0.23.16.1-r0)
(10/28) Installing libtasn1 (4.14-r0)
(11/28) Installing p11-kit-trust (0.23.16.1-r0)
(12/28) Installing ca-certificates (20190108-r0)
(13/28) Installing java-cacerts (1.0-r0)
(14/28) Installing libgcc (8.3.0-r0)
(15/28) Installing nspr (4.20-r0)
(16/28) Installing sqlite-libs (3.28.0-r2)
(17/28) Installing libstdc++ (8.3.0-r0)
(18/28) Installing nss (3.44.3-r0)
(19/28) Installing libjpeg-turbo (2.0.4-r0)
(20/28) Installing krb5-conf (1.0-r1)
(21/28) Installing libcom_err (1.45.2-r1)
(22/28) Installing keyutils-libs (1.6-r1)
(23/28) Installing libverto (0.3.1-r0)
(24/28) Installing krb5-libs (1.17-r0)
(25/28) Installing lcms2 (2.9-r1)
(26/28) Installing pcsc-lite-libs (1.8.25-r1)
(27/28) Installing liblksctp (1.0.18-r0)
(28/28) Installing openjdk8-jre-base (8.222.10-r0)
Executing busybox-1.30.1-r2.trigger
Executing java-common-0.2-r0.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 85 MiB in 42 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 6de54b7bb4b8
 ---> 9a7d226dc2a7
Step 5/19 : ARG MAJOR_VERSION=4.4
 ---> Running in a8c554df6a54
Removing intermediate container a8c554df6a54
 ---> 57921a5867c4
Step 6/19 : ARG ZBX_VERSION=${MAJOR_VERSION}.4
 ---> Running in 20614c19e059
Removing intermediate container 20614c19e059
 ---> 3182bdec6a93
Step 7/19 : ARG ZBX_SOURCES=https://git.zabbix.com/scm/zbx/zabbix.git
 ---> Running in c774fe8064ab
Removing intermediate container c774fe8064ab
 ---> fd3c4e5d2ce1
Step 8/19 : ENV TERM=xterm ZBX_VERSION=${ZBX_VERSION} ZBX_SOURCES=${ZBX_SOURCES}     PATH=${PATH}:/usr/lib/jvm/default-jvm/bin/ JAVA_HOME=/usr/lib/jvm/default-jvm
 ---> Running in bd576f2ed1dd
Removing intermediate container bd576f2ed1dd
 ---> 3a148c4f8266
Step 9/19 : LABEL org.opencontainers.image.documentation="https://www.zabbix.com/documentation/${MAJOR_VERSION}/manual/installation/containers"       org.opencontainers.image.version="${ZBX_VERSION}"       org.opencontainers.image.source="${ZBX_SOURCES}"
 ---> Running in 46efe01c0916
Removing intermediate container 46efe01c0916
 ---> e6d5ee8f5440
Step 10/19 : RUN set -eux &&     apk add --no-cache --virtual build-dependencies             autoconf             automake             coreutils             pkgconf             git             g++             make             openjdk8 &&     cd /tmp/ &&     git clone ${ZBX_SOURCES} --branch ${ZBX_VERSION} --depth 1 --single-branch zabbix-${ZBX_VERSION} &&     cd /tmp/zabbix-${ZBX_VERSION} &&     zabbix_revision=`git rev-parse --short HEAD` &&     sed -i "s/{ZABBIX_REVISION}/$zabbix_revision/g" include/version.h &&     sed -i "s/{ZABBIX_REVISION}/$zabbix_revision/g" src/zabbix_java/src/com/zabbix/gateway/GeneralInformation.java &&     ./bootstrap.sh &&     ./configure             --datadir=/usr/lib             --libdir=/usr/lib/zabbix             --sysconfdir=/etc/zabbix             --prefix=/usr             --enable-java             --silent &&     make -j"$(nproc)" -s &&     mkdir -p /usr/sbin/zabbix_java/ &&     cp -r src/zabbix_java/bin /usr/sbin/zabbix_java/ &&     cp -r src/zabbix_java/lib /usr/sbin/zabbix_java/ &&     rm -rf /usr/sbin/zabbix_java/lib/*.xml &&     cd /tmp/ &&     rm -rf /tmp/zabbix-${ZBX_VERSION}/ &&     apk del --purge --no-network             build-dependencies &&     rm -rf /var/cache/apk/*
 ---> Running in 895c3a447361
+ apk add --no-cache --virtual build-dependencies autoconf automake coreutils pkgconf git g++ make openjdk8
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/46) Installing m4 (1.4.18-r1)
(2/46) Installing libbz2 (1.0.6-r7)
(3/46) Installing perl (5.28.2-r1)
(4/46) Installing autoconf (2.69-r2)
(5/46) Installing automake (1.16.1-r0)
(6/46) Installing libacl (2.2.52-r6)
(7/46) Installing libattr (2.4.48-r0)
(8/46) Installing coreutils (8.31-r0)
(9/46) Installing pkgconf (1.6.1-r1)
(10/46) Installing nghttp2-libs (1.39.2-r0)
(11/46) Installing libcurl (7.66.0-r0)
(12/46) Installing expat (2.2.8-r0)
(13/46) Installing pcre2 (10.33-r0)
(14/46) Installing git (2.22.2-r0)
(15/46) Installing perl-error (0.17027-r0)
(16/46) Installing perl-git (2.22.2-r0)
(17/46) Installing git-perl (2.22.2-r0)
(18/46) Installing binutils (2.32-r0)
(19/46) Installing gmp (6.1.2-r1)
(20/46) Installing isl (0.18-r0)
(21/46) Installing libgomp (8.3.0-r0)
(22/46) Installing libatomic (8.3.0-r0)
(23/46) Installing mpfr3 (3.1.5-r1)
(24/46) Installing mpc1 (1.1.0-r0)
(25/46) Installing gcc (8.3.0-r0)
(26/46) Installing musl-dev (1.1.22-r3)
(27/46) Installing libc-dev (0.7.1-r0)
(28/46) Installing g++ (8.3.0-r0)
(29/46) Installing make (4.2.1-r2)
(30/46) Installing libxau (1.0.9-r0)
(31/46) Installing libbsd (0.9.1-r0)
(32/46) Installing libxdmcp (1.1.3-r0)
(33/46) Installing libxcb (1.13.1-r0)
(34/46) Installing libx11 (1.6.8-r1)
(35/46) Installing libxcomposite (0.4.5-r0)
(36/46) Installing libxext (1.3.4-r0)
(37/46) Installing libxi (1.7.9-r2)
(38/46) Installing libxrender (0.9.10-r3)
(39/46) Installing libxtst (1.2.3-r3)
(40/46) Installing alsa-lib (1.1.9-r0)
(41/46) Installing libpng (1.6.37-r1)
(42/46) Installing freetype (2.10.0-r0)
(43/46) Installing giflib (5.1.9-r0)
(44/46) Installing openjdk8-jre (8.222.10-r0)
(45/46) Installing openjdk8 (8.222.10-r0)
(46/46) Installing build-dependencies (20200116.013445)
Executing busybox-1.30.1-r2.trigger
Executing java-common-0.2-r0.trigger
OK: 322 MiB in 88 packages
+ cd /tmp/
+ git clone https://git.zabbix.com/scm/zbx/zabbix.git --branch 4.4.4 --depth 1 --single-branch zabbix-4.4.4
Cloning into 'zabbix-4.4.4'...
Note: checking out '3131fdac04eb1ce833315164258c00a6c565372e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

+ cd /tmp/zabbix-4.4.4
+ git rev-parse --short HEAD
+ zabbix_revision=3131fda
+ sed -i 's/{ZABBIX_REVISION}/3131fda/g' include/version.h
+ sed -i 's/{ZABBIX_REVISION}/3131fda/g' src/zabbix_java/src/com/zabbix/gateway/GeneralInformation.java
+ ./bootstrap.sh
configure.ac:40: installing './compile'
configure.ac:32: installing './config.guess'
configure.ac:32: installing './config.sub'
configure.ac:24: installing './install-sh'
configure.ac:24: installing './missing'
src/libs/zbxalgo/Makefile.am: installing './depcomp'
+ ./configure '--datadir=/usr/lib' '--libdir=/usr/lib/zabbix' '--sysconfdir=/etc/zabbix' '--prefix=/usr' --enable-java --silent


Configuration:

  Detected OS:           linux-gnu
  Install path:          /usr
  Compilation arch:      linux

  Compiler:              cc
  Compiler flags:         -g -O2 

  Library-specific flags:

  Enable server:         no

  Enable proxy:          no

  Enable agent:          no

  Enable agent 2:        no

  Enable Java gateway:   yes
  Java gateway details:
    Java compiler:         javac
    Java archiver:         jar

  LDAP support:          no
  IPv6 support:          no

***********************************************************
*            Now run 'make install'                       *
*                                                         *
*            Thank you for using Zabbix!                  *
*              <http://www.zabbix.com>                    *
***********************************************************

+ nproc
+ make -j4 -s
Making all in src
Making all in zabbix_java
Making all in database
Making all in ibm_db2
Making all in mysql
Making all in oracle
Making all in postgresql
Making all in sqlite3
Making all in man
Making all in misc
+ mkdir -p /usr/sbin/zabbix_java/
+ cp -r src/zabbix_java/bin /usr/sbin/zabbix_java/
+ cp -r src/zabbix_java/lib /usr/sbin/zabbix_java/
+ rm -rf /usr/sbin/zabbix_java/lib/logback-console.xml /usr/sbin/zabbix_java/lib/logback.xml
+ cd /tmp/
+ rm -rf /tmp/zabbix-4.4.4/
+ apk del --purge --no-network build-dependencies
WARNING: Ignoring APKINDEX.00740ba1.tar.gz: No such file or directory
WARNING: Ignoring APKINDEX.d8b2a6f4.tar.gz: No such file or directory
(1/46) Purging git-perl (2.22.2-r0)
(2/46) Purging perl-git (2.22.2-r0)
(3/46) Purging perl-error (0.17027-r0)
(4/46) Purging build-dependencies (20200116.013445)
(5/46) Purging autoconf (2.69-r2)
(6/46) Purging m4 (1.4.18-r1)
(7/46) Purging automake (1.16.1-r0)
(8/46) Purging perl (5.28.2-r1)
(9/46) Purging coreutils (8.31-r0)
Executing coreutils-8.31-r0.post-deinstall
(10/46) Purging pkgconf (1.6.1-r1)
(11/46) Purging git (2.22.2-r0)
(12/46) Purging g++ (8.3.0-r0)
(13/46) Purging gcc (8.3.0-r0)
(14/46) Purging binutils (2.32-r0)
(15/46) Purging libatomic (8.3.0-r0)
(16/46) Purging libgomp (8.3.0-r0)
(17/46) Purging libc-dev (0.7.1-r0)
(18/46) Purging musl-dev (1.1.22-r3)
(19/46) Purging make (4.2.1-r2)
(20/46) Purging openjdk8 (8.222.10-r0)
(21/46) Purging openjdk8-jre (8.222.10-r0)
(22/46) Purging freetype (2.10.0-r0)
(23/46) Purging libbz2 (1.0.6-r7)
(24/46) Purging libacl (2.2.52-r6)
(25/46) Purging libattr (2.4.48-r0)
(26/46) Purging libcurl (7.66.0-r0)
(27/46) Purging nghttp2-libs (1.39.2-r0)
(28/46) Purging expat (2.2.8-r0)
(29/46) Purging pcre2 (10.33-r0)
(30/46) Purging mpc1 (1.1.0-r0)
(31/46) Purging mpfr3 (3.1.5-r1)
(32/46) Purging isl (0.18-r0)
(33/46) Purging gmp (6.1.2-r1)
(34/46) Purging libxi (1.7.9-r2)
(35/46) Purging libxtst (1.2.3-r3)
(36/46) Purging libxext (1.3.4-r0)
(37/46) Purging libxrender (0.9.10-r3)
(38/46) Purging libxcomposite (0.4.5-r0)
(39/46) Purging libx11 (1.6.8-r1)
(40/46) Purging libxcb (1.13.1-r0)
(41/46) Purging libxau (1.0.9-r0)
(42/46) Purging libxdmcp (1.1.3-r0)
(43/46) Purging libbsd (0.9.1-r0)
(44/46) Purging alsa-lib (1.1.9-r0)
(45/46) Purging libpng (1.6.37-r1)
(46/46) Purging giflib (5.1.9-r0)
Executing busybox-1.30.1-r2.trigger
Executing java-common-0.2-r0.trigger
OK: 85 MiB in 42 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 895c3a447361
 ---> 9a265cdc2342
Step 11/19 : EXPOSE 10052/TCP
 ---> Running in 64f7f67d8325
Removing intermediate container 64f7f67d8325
 ---> ac0a2e3192d0
Step 12/19 : WORKDIR /var/lib/zabbix
 ---> Running in 312dfe7174ae
Removing intermediate container 312dfe7174ae
 ---> dda13b635e98
Step 13/19 : VOLUME ["/usr/sbin/zabbix_java/ext_lib"]
 ---> Running in 3acd69ba28aa
Removing intermediate container 3acd69ba28aa
 ---> 59dfeb22008b
Step 14/19 : COPY ["conf/etc/zabbix/zabbix_java_gateway_logback.xml", "/etc/zabbix/"]
 ---> 206ab64719ac
Step 15/19 : COPY ["conf/usr/sbin/zabbix_java_gateway", "/usr/sbin/"]
 ---> 8f4101c08df1
Step 16/19 : COPY ["docker-entrypoint.sh", "/usr/bin/"]
 ---> 438f2a303cc9
Step 17/19 : ENTRYPOINT ["docker-entrypoint.sh"]
 ---> Running in 83eeb3ca7699
Removing intermediate container 83eeb3ca7699
 ---> 6fd2dbdc4b0d
Step 18/19 : USER zabbix
 ---> Running in 2b8f4d863ceb
Removing intermediate container 2b8f4d863ceb
 ---> 9666cda22240
Step 19/19 : CMD ["/usr/sbin/zabbix_java_gateway"]
 ---> Running in 7e724a6c3a9e
Removing intermediate container 7e724a6c3a9e
 ---> 478a9ab53569

Successfully built 478a9ab53569
Successfully tagged zabbix-java-gateway:alpine-local
Building zabbix-snmptraps
Step 1/17 : FROM alpine:3.10
 ---> 965ea09ff2eb
Step 2/17 : ARG APK_FLAGS_PERSISTENT="--clean-protected --no-cache"
 ---> Running in b51ee4fc1ee2
Removing intermediate container b51ee4fc1ee2
 ---> 1886c7a6a01e
Step 3/17 : ARG APK_FLAGS_DEV="--no-cache"
 ---> Running in 241878d11040
Removing intermediate container 241878d11040
 ---> d93ea519c6ca
Step 4/17 : ARG MAJOR_VERSION=4.4
 ---> Running in 6f01de304bc0
Removing intermediate container 6f01de304bc0
 ---> af7f9d9dbd79
Step 5/17 : ARG ZBX_VERSION=${MAJOR_VERSION}.4
 ---> Running in 8345aa0f190d
Removing intermediate container 8345aa0f190d
 ---> 72e631f88985
Step 6/17 : ARG ZBX_SOURCES=https://git.zabbix.com/scm/zbx/zabbix.git
 ---> Running in 52e9357e6b29
Removing intermediate container 52e9357e6b29
 ---> 0a512b467be8
Step 7/17 : ENV TERM=xterm ZBX_VERSION=${ZBX_VERSION} ZBX_SOURCES=${ZBX_SOURCES}     MIBDIRS=/usr/share/snmp/mibs:/var/lib/zabbix/mibs MIBS=+ALL
 ---> Running in 87aaccb6a567
Removing intermediate container 87aaccb6a567
 ---> ba2ddbcfc29e
Step 8/17 : LABEL org.opencontainers.image.title="zabbix-snmptraps-alpine"       org.opencontainers.image.authors="Alexey Pustovalov <alexey.pustovalov@zabbix.com>"       org.opencontainers.image.vendor="Zabbix LLC"       org.opencontainers.image.url="https://zabbix.com/"       org.opencontainers.image.description="Zabbix server with MySQL database support"       org.opencontainers.image.licenses="GPL v2.0"       org.opencontainers.image.documentation="Zabbix SNMP traps receiver"       org.opencontainers.image.version="${ZBX_VERSION}"       org.opencontainers.image.source="https://anonscm.debian.org/gitweb/?p=collab-maint/snmptrapfmt.git"
 ---> Running in 20f819c96bfa
Removing intermediate container 20f819c96bfa
 ---> 9adb4b0f127d
Step 9/17 : STOPSIGNAL SIGTERM
 ---> Running in 167c9dee1d4e
Removing intermediate container 167c9dee1d4e
 ---> c7703e3f852d
Step 10/17 : COPY ["snmptrapfmt_1.14+nmu1ubuntu2.tar.gz", "/tmp/"]
 ---> 48ae0f570b07
Step 11/17 : RUN set -eux &&     addgroup zabbix &&     adduser -S             -D -G zabbix             -h /var/lib/zabbix/         zabbix &&     apk update &&     apk add ${APK_FLAGS_PERSISTENT}             net-snmp             supervisor &&     apk add ${APK_FLAGS_DEV} --virtual build-dependencies             alpine-sdk             autoconf             automake             libnsl-dev             net-snmp-dev &&     mkdir -p /var/lib/zabbix &&     mkdir -p /var/lib/zabbix/snmptraps &&     mkdir -p /var/lib/zabbix/mibs &&     chown --quiet -R zabbix:root /var/lib/zabbix &&     cd /tmp/ &&     tar -zxvf snmptrapfmt_1.14+nmu1ubuntu2.tar.gz &&     cd /tmp/snmptrapfmt-1.14+nmu1ubuntu1/ &&     patch -p1 < ./patches/makefile.patch &&     make -j"$(nproc)" -s &&     cp snmptrapfmthdlr /usr/sbin/snmptrapfmthdlr &&     cp snmptrapfmt /usr/sbin/snmptrapfmt &&     cp snmptrapfmt.conf /etc/snmp/snmptrapfmt.conf &&     echo "disableAuthorization yes" >> "/etc/snmp/snmptrapd.conf" &&     echo "traphandle default /usr/sbin/snmptrapfmthdlr" >> "/etc/snmp/snmptrapd.conf" &&     sed -i             -e "/^VARFMT=/s/=.*/=\"%n %v \"/"             -e '/^LOGFMT=/s/=.*/=\"$x ZBXTRAP $R $G $S $e $*\"/'             -e "/^LOGFILE=/s/=.*/=\"\/var\/lib\/zabbix\/snmptraps\/snmptraps.log\"/"         "/etc/snmp/snmptrapfmt.conf" &&     rm -rf /tmp/snmptrapfmt_1.14+nmu1ubuntu2.tar.gz &&     rm -rf /tmp/snmptrapfmt-1.14+nmu1ubuntu1/ &&     apk del --purge --no-network             build-dependencies &&     rm -rf /var/cache/apk/*
 ---> Running in fa9cf2ea3791
+ addgroup zabbix
+ adduser -S -D -G zabbix -h /var/lib/zabbix/ zabbix
+ apk update
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
v3.10.3-129-g58d7b94f01 [http://dl-cdn.alpinelinux.org/alpine/v3.10/main]
v3.10.3-127-g5d75746816 [http://dl-cdn.alpinelinux.org/alpine/v3.10/community]
OK: 10347 distinct packages available
+ apk add --clean-protected --no-cache net-snmp supervisor
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/16) Installing net-snmp-libs (5.8-r2)
(2/16) Installing net-snmp-agent-libs (5.8-r2)
(3/16) Installing net-snmp (5.8-r2)
(4/16) Installing libbz2 (1.0.6-r7)
(5/16) Installing expat (2.2.8-r0)
(6/16) Installing libffi (3.2.1-r6)
(7/16) Installing gdbm (1.13-r1)
(8/16) Installing ncurses-terminfo-base (6.1_p20190518-r0)
(9/16) Installing ncurses-terminfo (6.1_p20190518-r0)
(10/16) Installing ncurses-libs (6.1_p20190518-r0)
(11/16) Installing readline (8.0.0-r0)
(12/16) Installing sqlite-libs (3.28.0-r2)
(13/16) Installing python2 (2.7.16-r2)
(14/16) Installing py-meld3 (1.0.2-r1)
(15/16) Installing py-setuptools (40.8.0-r1)
(16/16) Installing supervisor (3.3.5-r0)
Executing busybox-1.30.1-r2.trigger
OK: 65 MiB in 30 packages
+ apk add --no-cache --virtual build-dependencies alpine-sdk autoconf automake libnsl-dev net-snmp-dev
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/73) Upgrading libcrypto1.1 (1.1.1d-r0 -> 1.1.1d-r2)
(2/73) Upgrading libssl1.1 (1.1.1d-r0 -> 1.1.1d-r2)
(3/73) Installing fakeroot (1.23-r0)
(4/73) Installing sudo (1.8.27-r0)
(5/73) Installing libcap (2.27-r0)
(6/73) Installing pax-utils (1.2.3-r0)
(7/73) Installing openssl (1.1.1d-r2)
(8/73) Installing libattr (2.4.48-r0)
(9/73) Installing attr (2.4.48-r0)
(10/73) Installing tar (1.32-r0)
(11/73) Installing pkgconf (1.6.1-r1)
(12/73) Installing patch (2.7.6-r6)
(13/73) Installing libgcc (8.3.0-r0)
(14/73) Installing libstdc++ (8.3.0-r0)
(15/73) Installing lzip (1.21-r0)
(16/73) Installing ca-certificates (20190108-r0)
(17/73) Installing nghttp2-libs (1.39.2-r0)
(18/73) Installing libcurl (7.66.0-r0)
(19/73) Installing curl (7.66.0-r0)
(20/73) Installing abuild (3.4.0-r0)
Executing abuild-3.4.0-r0.pre-install
(21/73) Installing binutils (2.32-r0)
(22/73) Installing libmagic (5.37-r1)
(23/73) Installing file (5.37-r1)
(24/73) Installing gmp (6.1.2-r1)
(25/73) Installing isl (0.18-r0)
(26/73) Installing libgomp (8.3.0-r0)
(27/73) Installing libatomic (8.3.0-r0)
(28/73) Installing mpfr3 (3.1.5-r1)
(29/73) Installing mpc1 (1.1.0-r0)
(30/73) Installing gcc (8.3.0-r0)
(31/73) Installing musl-dev (1.1.22-r3)
(32/73) Installing libc-dev (0.7.1-r0)
(33/73) Installing g++ (8.3.0-r0)
(34/73) Installing make (4.2.1-r2)
(35/73) Installing fortify-headers (1.1-r0)
(36/73) Installing build-base (0.5-r1)
(37/73) Installing pcre2 (10.33-r0)
(38/73) Installing git (2.22.2-r0)
(39/73) Installing alpine-sdk (1.0-r0)
(40/73) Installing m4 (1.4.18-r1)
(41/73) Installing perl (5.28.2-r1)
(42/73) Installing perl-error (0.17027-r0)
(43/73) Installing perl-git (2.22.2-r0)
(44/73) Installing git-perl (2.22.2-r0)
(45/73) Installing autoconf (2.69-r2)
(46/73) Installing automake (1.16.1-r0)
(47/73) Installing libintl (0.19.8.1-r4)
(48/73) Installing krb5-conf (1.0-r1)
(49/73) Installing libcom_err (1.45.2-r1)
(50/73) Installing keyutils-libs (1.6-r1)
(51/73) Installing libverto (0.3.1-r0)
(52/73) Installing krb5-libs (1.17-r0)
(53/73) Installing libtirpc (1.1.4-r0)
(54/73) Installing libnsl (1.2.0-r0)
(55/73) Installing libuuid (2.33.2-r0)
(56/73) Installing libblkid (2.33.2-r0)
(57/73) Installing libfdisk (2.33.2-r0)
(58/73) Installing libmount (2.33.2-r0)
(59/73) Installing libsmartcols (2.33.2-r0)
(60/73) Installing util-linux-dev (2.33.2-r0)
(61/73) Installing e2fsprogs-libs (1.45.2-r1)
(62/73) Installing e2fsprogs-dev (1.45.2-r1)
(63/73) Installing db (5.3.28-r1)
(64/73) Installing libsasl (2.1.27-r4)
(65/73) Installing libldap (2.4.48-r0)
(66/73) Installing krb5-server-ldap (1.17-r0)
(67/73) Installing krb5-dev (1.17-r0)
(68/73) Installing bsd-compat-headers (0.7.1-r0)
(69/73) Installing libtirpc-dev (1.1.4-r0)
(70/73) Installing libnsl-dev (1.2.0-r0)
(71/73) Installing openssl-dev (1.1.1d-r2)
(72/73) Installing net-snmp-dev (5.8-r2)
(73/73) Installing build-dependencies (20200116.013523)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 323 MiB in 101 packages
+ mkdir -p /var/lib/zabbix
+ mkdir -p /var/lib/zabbix/snmptraps
+ mkdir -p /var/lib/zabbix/mibs
+ chown --quiet -R zabbix:root /var/lib/zabbix
+ cd /tmp/
+ tar -zxvf snmptrapfmt_1.14+nmu1ubuntu2.tar.gz
snmptrapfmt-1.14+nmu1ubuntu1/
snmptrapfmt-1.14+nmu1ubuntu1/snmptrapfmt.conf
snmptrapfmt-1.14+nmu1ubuntu1/log.h
snmptrapfmt-1.14+nmu1ubuntu1/COPYING
snmptrapfmt-1.14+nmu1ubuntu1/Makefile
snmptrapfmt-1.14+nmu1ubuntu1/.gitignore
snmptrapfmt-1.14+nmu1ubuntu1/snmptrapfmthdlr.c
snmptrapfmt-1.14+nmu1ubuntu1/snmptrapfmt.c
snmptrapfmt-1.14+nmu1ubuntu1/snmptrapfmt.8
snmptrapfmt-1.14+nmu1ubuntu1/log.c
snmptrapfmt-1.14+nmu1ubuntu1/.pc/
snmptrapfmt-1.14+nmu1ubuntu1/.pc/.quilt_patches
snmptrapfmt-1.14+nmu1ubuntu1/.pc/.version
snmptrapfmt-1.14+nmu1ubuntu1/.pc/applied-patches
snmptrapfmt-1.14+nmu1ubuntu1/.pc/ip_address_fix.patch/
snmptrapfmt-1.14+nmu1ubuntu1/.pc/ip_address_fix.patch/snmptrapfmt.c
snmptrapfmt-1.14+nmu1ubuntu1/.pc/ip_address_fix.patch/.timestamp
snmptrapfmt-1.14+nmu1ubuntu1/.pc/.quilt_series
snmptrapfmt-1.14+nmu1ubuntu1/test/
snmptrapfmt-1.14+nmu1ubuntu1/test/snmptrapfmt.conf
snmptrapfmt-1.14+nmu1ubuntu1/test/testtraps.sh
snmptrapfmt-1.14+nmu1ubuntu1/patches/
snmptrapfmt-1.14+nmu1ubuntu1/patches/makefile.patch
snmptrapfmt-1.14+nmu1ubuntu1/patches/ip_address_fix.patch
snmptrapfmt-1.14+nmu1ubuntu1/patches/series
snmptrapfmt-1.14+nmu1ubuntu1/snmptrapfmthdlr.8
snmptrapfmt-1.14+nmu1ubuntu1/snmptrapfmt.h
snmptrapfmt-1.14+nmu1ubuntu1/debian/
snmptrapfmt-1.14+nmu1ubuntu1/debian/rules
snmptrapfmt-1.14+nmu1ubuntu1/debian/compat
snmptrapfmt-1.14+nmu1ubuntu1/debian/snmptrapfmt.examples
snmptrapfmt-1.14+nmu1ubuntu1/debian/README.debian
snmptrapfmt-1.14+nmu1ubuntu1/debian/examples/
snmptrapfmt-1.14+nmu1ubuntu1/debian/examples/snmptrapd.conf
snmptrapfmt-1.14+nmu1ubuntu1/debian/changelog
snmptrapfmt-1.14+nmu1ubuntu1/debian/init.d
snmptrapfmt-1.14+nmu1ubuntu1/debian/patches/
snmptrapfmt-1.14+nmu1ubuntu1/debian/patches/ip_address_fix.patch
snmptrapfmt-1.14+nmu1ubuntu1/debian/patches/series
snmptrapfmt-1.14+nmu1ubuntu1/debian/copyright
snmptrapfmt-1.14+nmu1ubuntu1/debian/dirs
snmptrapfmt-1.14+nmu1ubuntu1/debian/control
snmptrapfmt-1.14+nmu1ubuntu1/debian/postrm
+ cd /tmp/snmptrapfmt-1.14+nmu1ubuntu1/
+ patch -p1
patching file Makefile
+ nproc
+ make -j4 -s
/bin/sh: dpkg-buildflags: not found
/bin/sh: dpkg-buildflags: not found
/bin/sh: dpkg-buildflags: not found
/bin/sh: dpkg-buildflags: not found
/bin/sh: dpkg-buildflags: not found
/bin/sh: dpkg-buildflags: not found
snmptrapfmt.c:59: warning: "LOGFILE" redefined
 #define LOGFILE "/var/tmp/snmptrapfmt.trc"
 
In file included from snmptrapfmt.c:48:
/usr/include/net-snmp/net-snmp-config.h:2358: note: this is the location of the previous definition
 # define LOGFILE NETSNMP_LOGFILE
 
/bin/sh: dpkg-buildflags: not found
/bin/sh: dpkg-buildflags: not found
+ cp snmptrapfmthdlr /usr/sbin/snmptrapfmthdlr
+ cp snmptrapfmt /usr/sbin/snmptrapfmt
+ cp snmptrapfmt.conf /etc/snmp/snmptrapfmt.conf
+ echo 'disableAuthorization yes'
+ echo 'traphandle default /usr/sbin/snmptrapfmthdlr'
+ sed -i -e '/^VARFMT=/s/=.*/="%n %v "/' -e '/^LOGFMT=/s/=.*/=\"$x ZBXTRAP $R $G $S $e $*\"/' -e '/^LOGFILE=/s/=.*/="\/var\/lib\/zabbix\/snmptraps\/snmptraps.log"/' /etc/snmp/snmptrapfmt.conf
+ rm -rf /tmp/snmptrapfmt_1.14+nmu1ubuntu2.tar.gz
+ rm -rf /tmp/snmptrapfmt-1.14+nmu1ubuntu1/
+ apk del --purge --no-network build-dependencies
(1/71) Purging git-perl (2.22.2-r0)
(2/71) Purging perl-git (2.22.2-r0)
(3/71) Purging perl-error (0.17027-r0)
(4/71) Purging build-dependencies (20200116.013523)
(5/71) Purging alpine-sdk (1.0-r0)
(6/71) Purging abuild (3.4.0-r0)
(7/71) Purging fakeroot (1.23-r0)
(8/71) Purging sudo (1.8.27-r0)
(9/71) Purging pax-utils (1.2.3-r0)
(10/71) Purging openssl (1.1.1d-r2)
(11/71) Purging attr (2.4.48-r0)
(12/71) Purging tar (1.32-r0)
(13/71) Purging patch (2.7.6-r6)
(14/71) Purging lzip (1.21-r0)
(15/71) Purging curl (7.66.0-r0)
(16/71) Purging build-base (0.5-r1)
(17/71) Purging file (5.37-r1)
(18/71) Purging g++ (8.3.0-r0)
(19/71) Purging gcc (8.3.0-r0)
(20/71) Purging binutils (2.32-r0)
(21/71) Purging libatomic (8.3.0-r0)
(22/71) Purging libgomp (8.3.0-r0)
(23/71) Purging libstdc++ (8.3.0-r0)
(24/71) Purging make (4.2.1-r2)
(25/71) Purging libc-dev (0.7.1-r0)
(26/71) Purging musl-dev (1.1.22-r3)
(27/71) Purging fortify-headers (1.1-r0)
(28/71) Purging git (2.22.2-r0)
(29/71) Purging autoconf (2.69-r2)
(30/71) Purging m4 (1.4.18-r1)
(31/71) Purging automake (1.16.1-r0)
(32/71) Purging perl (5.28.2-r1)
(33/71) Purging libnsl-dev (1.2.0-r0)
(34/71) Purging libnsl (1.2.0-r0)
(35/71) Purging net-snmp-dev (5.8-r2)
(36/71) Purging openssl-dev (1.1.1d-r2)
(37/71) Purging libcap (2.27-r0)
(38/71) Purging libattr (2.4.48-r0)
(39/71) Purging libtirpc-dev (1.1.4-r0)
(40/71) Purging bsd-compat-headers (0.7.1-r0)
(41/71) Purging libtirpc (1.1.4-r0)
(42/71) Purging krb5-dev (1.17-r0)
(43/71) Purging krb5-server-ldap (1.17-r0)
(44/71) Purging e2fsprogs-dev (1.45.2-r1)
(45/71) Purging util-linux-dev (2.33.2-r0)
(46/71) Purging libfdisk (2.33.2-r0)
(47/71) Purging libmount (2.33.2-r0)
(48/71) Purging libsmartcols (2.33.2-r0)
(49/71) Purging e2fsprogs-libs (1.45.2-r1)
(50/71) Purging pkgconf (1.6.1-r1)
(51/71) Purging libgcc (8.3.0-r0)
(52/71) Purging libcurl (7.66.0-r0)
(53/71) Purging ca-certificates (20190108-r0)
Executing ca-certificates-20190108-r0.post-deinstall
(54/71) Purging nghttp2-libs (1.39.2-r0)
(55/71) Purging libmagic (5.37-r1)
(56/71) Purging mpc1 (1.1.0-r0)
(57/71) Purging mpfr3 (3.1.5-r1)
(58/71) Purging isl (0.18-r0)
(59/71) Purging gmp (6.1.2-r1)
(60/71) Purging pcre2 (10.33-r0)
(61/71) Purging libintl (0.19.8.1-r4)
(62/71) Purging krb5-libs (1.17-r0)
(63/71) Purging krb5-conf (1.0-r1)
(64/71) Purging libcom_err (1.45.2-r1)
(65/71) Purging keyutils-libs (1.6-r1)
(66/71) Purging libverto (0.3.1-r0)
(67/71) Purging libblkid (2.33.2-r0)
(68/71) Purging libuuid (2.33.2-r0)
(69/71) Purging libldap (2.4.48-r0)
(70/71) Purging libsasl (2.1.27-r4)
(71/71) Purging db (5.3.28-r1)
Executing busybox-1.30.1-r2.trigger
OK: 65 MiB in 30 packages
+ rm -rf /var/cache/apk/APKINDEX.00740ba1.tar.gz /var/cache/apk/APKINDEX.d8b2a6f4.tar.gz
Removing intermediate container fa9cf2ea3791
 ---> 45f7621ecb71
Step 12/17 : EXPOSE 162/UDP
 ---> Running in d916fd3ea577
Removing intermediate container d916fd3ea577
 ---> 8671b012d109
Step 13/17 : WORKDIR /var/lib/zabbix/snmptraps/
 ---> Running in 39d6b086e086
Removing intermediate container 39d6b086e086
 ---> 7b59066c2102
Step 14/17 : VOLUME ["/var/lib/zabbix/snmptraps", "/var/lib/zabbix/mibs"]
 ---> Running in a9309627f9d6
Removing intermediate container a9309627f9d6
 ---> 569a664e144c
Step 15/17 : COPY ["conf/etc/supervisor/", "/etc/supervisor/"]
 ---> ea2244e3a6f7
Step 16/17 : COPY ["conf/etc/logrotate.d/zabbix_snmptraps", "/etc/logrotate.d/"]
 ---> 9c77e53232b0
Step 17/17 : CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/supervisord.conf"]
 ---> Running in 09436918b999
Removing intermediate container 09436918b999
 ---> da63fa65d940

Successfully built da63fa65d940
Successfully tagged zabbix-snmptraps:alpine-local
Building zabbix-server
Step 1/19 : FROM alpine:3.10
 ---> 965ea09ff2eb
Step 2/19 : LABEL org.opencontainers.image.title="Zabbix server (MySQL)"       org.opencontainers.image.authors="Alexey Pustovalov <alexey.pustovalov@zabbix.com>"       org.opencontainers.image.vendor="Zabbix LLC"       org.opencontainers.image.url="https://zabbix.com/"       org.opencontainers.image.description="Zabbix server with MySQL database support"       org.opencontainers.image.licenses="GPL v2.0"
 ---> Running in f82d8a8d3b47
Removing intermediate container f82d8a8d3b47
 ---> 25898d547119
Step 3/19 : STOPSIGNAL SIGTERM
 ---> Running in 137531cb61dc
Removing intermediate container 137531cb61dc
 ---> d924698ae239
Step 4/19 : RUN set -eux &&     addgroup -S -g 1000 zabbix &&     adduser -S             -D -G zabbix             -u 999             -h /var/lib/zabbix/         zabbix &&     adduser zabbix dialout &&     mkdir -p /etc/zabbix &&     mkdir -p /var/lib/zabbix &&     mkdir -p /usr/lib/zabbix/alertscripts &&     mkdir -p /var/lib/zabbix/enc &&     mkdir -p /usr/lib/zabbix/externalscripts &&     mkdir -p /var/lib/zabbix/mibs &&     mkdir -p /var/lib/zabbix/modules &&     mkdir -p /var/lib/zabbix/snmptraps &&     mkdir -p /var/lib/zabbix/ssh_keys &&     mkdir -p /var/lib/zabbix/ssl &&     mkdir -p /var/lib/zabbix/ssl/certs &&     mkdir -p /var/lib/zabbix/ssl/keys &&     mkdir -p /var/lib/zabbix/ssl/ssl_ca &&     chown --quiet -R zabbix:root /var/lib/zabbix &&     mkdir -p /usr/share/doc/zabbix-server-mysql &&     apk add --clean-protected --no-cache             tini             bash             fping             iputils             libcurl             libevent             libldap             libssh2             libxml2             mariadb-client             mariadb-connector-c             net-snmp-agent-libs             openipmi-libs             pcre             unixodbc &&     rm -rf /var/cache/apk/*
 ---> Running in 897b6910af81
+ addgroup -S -g 1000 zabbix
+ adduser -S -D -G zabbix -u 999 -h /var/lib/zabbix/ zabbix
+ adduser zabbix dialout
+ mkdir -p /etc/zabbix
+ mkdir -p /var/lib/zabbix
+ mkdir -p /usr/lib/zabbix/alertscripts
+ mkdir -p /var/lib/zabbix/enc
+ mkdir -p /usr/lib/zabbix/externalscripts
+ mkdir -p /var/lib/zabbix/mibs
+ mkdir -p /var/lib/zabbix/modules
+ mkdir -p /var/lib/zabbix/snmptraps
+ mkdir -p /var/lib/zabbix/ssh_keys
+ mkdir -p /var/lib/zabbix/ssl
+ mkdir -p /var/lib/zabbix/ssl/certs
+ mkdir -p /var/lib/zabbix/ssl/keys
+ mkdir -p /var/lib/zabbix/ssl/ssl_ca
+ chown --quiet -R zabbix:root /var/lib/zabbix
+ mkdir -p /usr/share/doc/zabbix-server-mysql
+ apk add --clean-protected --no-cache tini bash fping iputils libcurl libevent libldap libssh2 libxml2 mariadb-client mariadb-connector-c net-snmp-agent-libs openipmi-libs pcre unixodbc
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/34) Installing ncurses-terminfo-base (6.1_p20190518-r0)
(2/34) Installing ncurses-terminfo (6.1_p20190518-r0)
(3/34) Installing ncurses-libs (6.1_p20190518-r0)
(4/34) Installing readline (8.0.0-r0)
(5/34) Installing bash (5.0.0-r0)
Executing bash-5.0.0-r0.post-install
(6/34) Installing fping (4.2-r0)
(7/34) Installing libcap (2.27-r0)
(8/34) Installing iputils (20180629-r1)
(9/34) Installing ca-certificates (20190108-r0)
(10/34) Installing nghttp2-libs (1.39.2-r0)
(11/34) Installing libcurl (7.66.0-r0)
(12/34) Installing libevent (2.1.10-r0)
(13/34) Installing db (5.3.28-r1)
(14/34) Installing libsasl (2.1.27-r4)
(15/34) Installing libldap (2.4.48-r0)
(16/34) Installing libssh2 (1.9.0-r1)
(17/34) Installing libxml2 (2.9.9-r3)
(18/34) Installing mariadb-common (10.3.20-r0)
(19/34) Installing libgcc (8.3.0-r0)
(20/34) Installing libstdc++ (8.3.0-r0)
(21/34) Installing mariadb-client (10.3.20-r0)
(22/34) Installing mariadb-connector-c (3.0.10-r0)
(23/34) Installing net-snmp-libs (5.8-r2)
(24/34) Installing net-snmp-agent-libs (5.8-r2)
(25/34) Installing libffi (3.2.1-r6)
(26/34) Installing libintl (0.19.8.1-r4)
(27/34) Installing libuuid (2.33.2-r0)
(28/34) Installing libblkid (2.33.2-r0)
(29/34) Installing libmount (2.33.2-r0)
(30/34) Installing pcre (8.43-r0)
(31/34) Installing glib (2.60.4-r0)
(32/34) Installing openipmi-libs (2.0.25-r1)
(33/34) Installing tini (0.18.0-r0)
(34/34) Installing unixodbc (2.3.7-r1)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 63 MiB in 48 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 897b6910af81
 ---> e285dcfdf3cd
Step 5/19 : ARG MAJOR_VERSION=4.4
 ---> Running in d21fd89aa65c
Removing intermediate container d21fd89aa65c
 ---> 85d8e80889b4
Step 6/19 : ARG ZBX_VERSION=${MAJOR_VERSION}.4
 ---> Running in 4dbbf613a84b
Removing intermediate container 4dbbf613a84b
 ---> 58cd0a33c3dd
Step 7/19 : ARG ZBX_SOURCES=https://git.zabbix.com/scm/zbx/zabbix.git
 ---> Running in 13f0c5fa924d
Removing intermediate container 13f0c5fa924d
 ---> eef90a37b044
Step 8/19 : ENV TERM=xterm ZBX_VERSION=${ZBX_VERSION} ZBX_SOURCES=${ZBX_SOURCES}     MIBDIRS=/usr/share/snmp/mibs:/var/lib/zabbix/mibs MIBS=+ALL
 ---> Running in cb77683be73a
Removing intermediate container cb77683be73a
 ---> c9cfe19782cb
Step 9/19 : LABEL org.opencontainers.image.documentation="https://www.zabbix.com/documentation/${MAJOR_VERSION}/manual/installation/containers"       org.opencontainers.image.version="${ZBX_VERSION}"       org.opencontainers.image.source="${ZBX_SOURCES}"
 ---> Running in f97b05cd3537
Removing intermediate container f97b05cd3537
 ---> 5adcc989ed42
Step 10/19 : RUN set -eux &&     apk add --no-cache --virtual build-dependencies             autoconf             automake             coreutils             curl-dev             libevent-dev             libssh2-dev             libxml2-dev             mysql-dev             net-snmp-dev             openipmi-dev             openldap-dev             pcre-dev             git             g++             make             unixodbc-dev &&     cd /tmp/ &&     git clone ${ZBX_SOURCES} --branch ${ZBX_VERSION} --depth 1 --single-branch zabbix-${ZBX_VERSION} &&     cd /tmp/zabbix-${ZBX_VERSION} &&     zabbix_revision=`git rev-parse --short HEAD` &&     sed -i "s/{ZABBIX_REVISION}/$zabbix_revision/g" include/version.h &&     ./bootstrap.sh &&     export CFLAGS="-fPIC -pie -Wl,-z,relro -Wl,-z,now" &&     ./configure             --datadir=/usr/lib             --libdir=/usr/lib/zabbix             --prefix=/usr             --sysconfdir=/etc/zabbix             --enable-agent             --enable-server             --with-mysql             --with-ldap             --with-libcurl             --with-libxml2             --with-net-snmp             --with-openipmi             --with-openssl             --with-ssh2             --with-unixodbc             --enable-ipv6             --silent &&     make -j"$(nproc)" -s dbschema &&     make -j"$(nproc)" -s &&     cp src/zabbix_server/zabbix_server /usr/sbin/zabbix_server &&     cp src/zabbix_get/zabbix_get /usr/bin/zabbix_get &&     cp src/zabbix_sender/zabbix_sender /usr/bin/zabbix_sender &&     cp conf/zabbix_server.conf /etc/zabbix/zabbix_server.conf &&     chown --quiet -R zabbix:root /etc/zabbix &&     cat database/mysql/schema.sql > database/mysql/create.sql &&     cat database/mysql/images.sql >> database/mysql/create.sql &&     cat database/mysql/data.sql >> database/mysql/create.sql &&     gzip database/mysql/create.sql &&     cp database/mysql/create.sql.gz /usr/share/doc/zabbix-server-mysql/ &&     cd /tmp/ &&     rm -rf /tmp/zabbix-${ZBX_VERSION}/ &&     apk del --purge --no-network             build-dependencies &&     rm -rf /var/cache/apk/*
 ---> Running in 30e432fa0ef3
+ apk add --no-cache --virtual build-dependencies autoconf automake coreutils curl-dev libevent-dev libssh2-dev libxml2-dev mysql-dev net-snmp-dev openipmi-dev openldap-dev pcre-dev git g++ make unixodbc-dev
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/60) Upgrading libcrypto1.1 (1.1.1d-r0 -> 1.1.1d-r2)
(2/60) Upgrading libssl1.1 (1.1.1d-r0 -> 1.1.1d-r2)
(3/60) Installing m4 (1.4.18-r1)
(4/60) Installing libbz2 (1.0.6-r7)
(5/60) Installing perl (5.28.2-r1)
(6/60) Installing autoconf (2.69-r2)
(7/60) Installing automake (1.16.1-r0)
(8/60) Installing libacl (2.2.52-r6)
(9/60) Installing libattr (2.4.48-r0)
(10/60) Installing coreutils (8.31-r0)
(11/60) Installing pkgconf (1.6.1-r1)
(12/60) Installing openssl-dev (1.1.1d-r2)
(13/60) Installing nghttp2-dev (1.39.2-r0)
(14/60) Installing zlib-dev (1.2.11-r1)
(15/60) Installing curl-dev (7.66.0-r0)
(16/60) Installing expat (2.2.8-r0)
(17/60) Installing gdbm (1.13-r1)
(18/60) Installing sqlite-libs (3.28.0-r2)
(19/60) Installing python2 (2.7.16-r2)
(20/60) Installing libevent-dev (2.1.10-r0)
(21/60) Installing libssh2-dev (1.9.0-r1)
(22/60) Installing libxml2-dev (2.9.9-r3)
(23/60) Installing mariadb-connector-c-dev (3.0.10-r0)
(24/60) Installing libaio (0.3.111-r0)
(25/60) Installing xz-libs (5.2.4-r0)
(26/60) Installing mariadb-embedded (10.3.20-r0)
(27/60) Installing mariadb-dev (10.3.20-r0)
(28/60) Installing net-snmp-dev (5.8-r2)
(29/60) Installing popt (1.16-r7)
(30/60) Installing openipmi-lanserv (2.0.25-r1)
(31/60) Installing ncurses-dev (6.1_p20190518-r0)
(32/60) Installing openipmi-dev (2.0.25-r1)
(33/60) Installing cyrus-sasl-dev (2.1.27-r4)
(34/60) Installing libfdisk (2.33.2-r0)
(35/60) Installing libsmartcols (2.33.2-r0)
(36/60) Installing util-linux-dev (2.33.2-r0)
(37/60) Installing openldap-dev (2.4.48-r0)
(38/60) Installing libpcre16 (8.43-r0)
(39/60) Installing libpcre32 (8.43-r0)
(40/60) Installing libpcrecpp (8.43-r0)
(41/60) Installing pcre-dev (8.43-r0)
(42/60) Installing pcre2 (10.33-r0)
(43/60) Installing git (2.22.2-r0)
(44/60) Installing perl-error (0.17027-r0)
(45/60) Installing perl-git (2.22.2-r0)
(46/60) Installing git-perl (2.22.2-r0)
(47/60) Installing binutils (2.32-r0)
(48/60) Installing gmp (6.1.2-r1)
(49/60) Installing isl (0.18-r0)
(50/60) Installing libgomp (8.3.0-r0)
(51/60) Installing libatomic (8.3.0-r0)
(52/60) Installing mpfr3 (3.1.5-r1)
(53/60) Installing mpc1 (1.1.0-r0)
(54/60) Installing gcc (8.3.0-r0)
(55/60) Installing musl-dev (1.1.22-r3)
(56/60) Installing libc-dev (0.7.1-r0)
(57/60) Installing g++ (8.3.0-r0)
(58/60) Installing make (4.2.1-r2)
(59/60) Installing unixodbc-dev (2.3.7-r1)
(60/60) Installing build-dependencies (20200116.013536)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 377 MiB in 106 packages
+ cd /tmp/
+ git clone https://git.zabbix.com/scm/zbx/zabbix.git --branch 4.4.4 --depth 1 --single-branch zabbix-4.4.4
Cloning into 'zabbix-4.4.4'...
Note: checking out '3131fdac04eb1ce833315164258c00a6c565372e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

+ cd /tmp/zabbix-4.4.4
+ git rev-parse --short HEAD
+ zabbix_revision=3131fda
+ sed -i 's/{ZABBIX_REVISION}/3131fda/g' include/version.h
+ ./bootstrap.sh
configure.ac:40: installing './compile'
configure.ac:32: installing './config.guess'
configure.ac:32: installing './config.sub'
configure.ac:24: installing './install-sh'
configure.ac:24: installing './missing'
src/libs/zbxalgo/Makefile.am: installing './depcomp'
+ export 'CFLAGS=-fPIC -pie -Wl,-z,relro -Wl,-z,now'
+ ./configure '--datadir=/usr/lib' '--libdir=/usr/lib/zabbix' '--prefix=/usr' '--sysconfdir=/etc/zabbix' --enable-agent --enable-server --with-mysql --with-ldap --with-libcurl --with-libxml2 --with-net-snmp --with-openipmi --with-openssl --with-ssh2 --with-unixodbc --enable-ipv6 --silent


Configuration:

  Detected OS:           linux-gnu
  Install path:          /usr
  Compilation arch:      linux

  Compiler:              cc
  Compiler flags:         -fPIC -pie -Wl,-z,relro -Wl,-z,now 

  Library-specific flags:
    database:               -I/usr/include/mysql -I/usr/include/mysql   
    libXML2:               -I/usr/include/libxml2
    unixODBC:              -I/usr/include
    Net-SNMP:               -I. -I/usr/include
    OpenIPMI:              -I/usr/include
    libssh2:               -I/usr/include
    TLS:                   -I/usr/include
    LDAP:                  -I/usr/include

  Enable server:         yes
  Server details:
    With database:         MySQL
    WEB Monitoring:        cURL
      SSL certificates:      /usr/lib/zabbix/ssl/certs
      SSL keys:              /usr/lib/zabbix/ssl/keys
    SNMP:                  yes
    IPMI:                  yes
    SSH:                   yes
    TLS:                   OpenSSL
    ODBC:                  yes
    Linker flags:             -L/usr/lib/     -L/lib -L/usr/lib  -L/usr/lib -L/usr/lib -L/usr/lib    -L/usr/lib -L/usr/lib    
    Libraries:               -lmariadb  -lz -lssl -lcrypto    -lxml2  -lodbc  -lnetsnmp -lssh2 -lOpenIPMI -lOpenIPMIposix -lz -lpthread -levent -lssl -lcrypto -lldap -llber   -lcurl -lnghttp2 -lssl -lcrypto -lssl -lcrypto -lz -lm   -lpcre 
    Configuration file:    /etc/zabbix/zabbix_server.conf
    External scripts:      /usr/lib/zabbix/externalscripts
    Alert scripts:         /usr/lib/zabbix/alertscripts
    Modules:               /usr/lib/zabbix/modules

  Enable proxy:          no

  Enable agent:          yes
  Agent details:
    TLS:                   OpenSSL
    Linker flags:             -L/usr/lib -L/usr/lib    
    Libraries:              -lz -lpthread -lssl -lcrypto -lldap -llber   -lcurl -lnghttp2 -lssl -lcrypto -lssl -lcrypto -lz -lm   -lpcre 
    Configuration file:    /etc/zabbix/zabbix_agentd.conf
    Modules:               /usr/lib/zabbix/modules

  Enable agent 2:        no

  Enable Java gateway:   no

  LDAP support:          yes
  IPv6 support:          yes

***********************************************************
*            Now run 'make install'                       *
*                                                         *
*            Thank you for using Zabbix!                  *
*              <http://www.zabbix.com>                    *
***********************************************************

+ nproc
+ make -j4 -s dbschema
+ nproc
+ make -j4 -s
Making all in src
Making all in libs
Making all in zbxcrypto
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcommon
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxlog
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxalgo
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxnix
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxconf
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxhttp
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxsysinfo
Making all in agent
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in common
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in simple
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in linux
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxsys
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcomms
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxjson
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxexec
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxmodules
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxregexp
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxipcservice
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcompress
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcommshigh
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdb
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdbupgrade
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdbcache
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdbhigh
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxhttp
Making all in zbxmemory
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxserver
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxicmpping
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxmedia
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxself
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxtasks
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxhistory
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcompress
Making all in zbxembed
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxprometheus
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_agent
Making all in logfiles
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_get
Making all in zabbix_sender
Making all in zabbix_server
Making all in alerter
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in dbsyncer
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in dbconfig
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in discoverer
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in housekeeper
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in httppoller
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in pinger
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in poller
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in snmptrapper
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in timer
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in trapper
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in escalator
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in proxypoller
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in selfmon
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in vmware
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in taskmanager
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in ipmi
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in odbc
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in scripts
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in preprocessor
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in lld
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in database
Making all in ibm_db2
Making all in mysql
Making all in oracle
Making all in postgresql
Making all in sqlite3
Making all in man
Making all in misc
+ cp src/zabbix_server/zabbix_server /usr/sbin/zabbix_server
+ cp src/zabbix_get/zabbix_get /usr/bin/zabbix_get
+ cp src/zabbix_sender/zabbix_sender /usr/bin/zabbix_sender
+ cp conf/zabbix_server.conf /etc/zabbix/zabbix_server.conf
+ chown --quiet -R zabbix:root /etc/zabbix
+ cat database/mysql/schema.sql
+ cat database/mysql/images.sql
+ cat database/mysql/data.sql
+ gzip database/mysql/create.sql
+ cp database/mysql/create.sql.gz /usr/share/doc/zabbix-server-mysql/
+ cd /tmp/
+ rm -rf /tmp/zabbix-4.4.4/
+ apk del --purge --no-network build-dependencies
WARNING: Ignoring APKINDEX.00740ba1.tar.gz: No such file or directory
WARNING: Ignoring APKINDEX.d8b2a6f4.tar.gz: No such file or directory
(1/58) Purging git-perl (2.22.2-r0)
(2/58) Purging perl-git (2.22.2-r0)
(3/58) Purging perl-error (0.17027-r0)
(4/58) Purging build-dependencies (20200116.013536)
(5/58) Purging autoconf (2.69-r2)
(6/58) Purging m4 (1.4.18-r1)
(7/58) Purging automake (1.16.1-r0)
(8/58) Purging perl (5.28.2-r1)
(9/58) Purging coreutils (8.31-r0)
Executing coreutils-8.31-r0.post-deinstall
(10/58) Purging curl-dev (7.66.0-r0)
(11/58) Purging nghttp2-dev (1.39.2-r0)
(12/58) Purging libevent-dev (2.1.10-r0)
(13/58) Purging python2 (2.7.16-r2)
(14/58) Purging libssh2-dev (1.9.0-r1)
(15/58) Purging libxml2-dev (2.9.9-r3)
(16/58) Purging net-snmp-dev (5.8-r2)
(17/58) Purging openipmi-dev (2.0.25-r1)
(18/58) Purging openipmi-lanserv (2.0.25-r1)
(19/58) Purging openldap-dev (2.4.48-r0)
(20/58) Purging cyrus-sasl-dev (2.1.27-r4)
(21/58) Purging util-linux-dev (2.33.2-r0)
(22/58) Purging libfdisk (2.33.2-r0)
(23/58) Purging libsmartcols (2.33.2-r0)
(24/58) Purging pcre-dev (8.43-r0)
(25/58) Purging libpcre16 (8.43-r0)
(26/58) Purging libpcre32 (8.43-r0)
(27/58) Purging libpcrecpp (8.43-r0)
(28/58) Purging git (2.22.2-r0)
(29/58) Purging g++ (8.3.0-r0)
(30/58) Purging gcc (8.3.0-r0)
(31/58) Purging binutils (2.32-r0)
(32/58) Purging libatomic (8.3.0-r0)
(33/58) Purging libgomp (8.3.0-r0)
(34/58) Purging libc-dev (0.7.1-r0)
(35/58) Purging musl-dev (1.1.22-r3)
(36/58) Purging make (4.2.1-r2)
(37/58) Purging unixodbc-dev (2.3.7-r1)
(38/58) Purging libbz2 (1.0.6-r7)
(39/58) Purging libacl (2.2.52-r6)
(40/58) Purging libattr (2.4.48-r0)
(41/58) Purging mariadb-dev (10.3.20-r0)
(42/58) Purging mariadb-embedded (10.3.20-r0)
(43/58) Purging mariadb-connector-c-dev (3.0.10-r0)
(44/58) Purging zlib-dev (1.2.11-r1)
(45/58) Purging openssl-dev (1.1.1d-r2)
(46/58) Purging ncurses-dev (6.1_p20190518-r0)
(47/58) Purging pkgconf (1.6.1-r1)
(48/58) Purging expat (2.2.8-r0)
(49/58) Purging gdbm (1.13-r1)
(50/58) Purging sqlite-libs (3.28.0-r2)
(51/58) Purging libaio (0.3.111-r0)
(52/58) Purging xz-libs (5.2.4-r0)
(53/58) Purging popt (1.16-r7)
(54/58) Purging pcre2 (10.33-r0)
(55/58) Purging mpc1 (1.1.0-r0)
(56/58) Purging mpfr3 (3.1.5-r1)
(57/58) Purging isl (0.18-r0)
(58/58) Purging gmp (6.1.2-r1)
Executing busybox-1.30.1-r2.trigger
OK: 63 MiB in 48 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 30e432fa0ef3
 ---> ce143659aec4
Step 11/19 : EXPOSE 10051/TCP
 ---> Running in a92d82a6a28c
Removing intermediate container a92d82a6a28c
 ---> 2412ef4c6141
Step 12/19 : WORKDIR /var/lib/zabbix
 ---> Running in e85d8e0062cd
Removing intermediate container e85d8e0062cd
 ---> aec75267b9bf
Step 13/19 : VOLUME ["/usr/lib/zabbix/alertscripts", "/usr/lib/zabbix/externalscripts", "/var/lib/zabbix/enc", "/var/lib/zabbix/mibs", "/var/lib/zabbix/modules"]
 ---> Running in ceba6404e5a9
Removing intermediate container ceba6404e5a9
 ---> f9744de53f39
Step 14/19 : VOLUME ["/var/lib/zabbix/snmptraps", "/var/lib/zabbix/ssh_keys", "/var/lib/zabbix/ssl/certs", "/var/lib/zabbix/ssl/keys", "/var/lib/zabbix/ssl/ssl_ca"]
 ---> Running in 0ea56982f776
Removing intermediate container 0ea56982f776
 ---> 3dba054aae8e
Step 15/19 : VOLUME ["/var/lib/zabbix/export"]
 ---> Running in 482856b1cc7e
Removing intermediate container 482856b1cc7e
 ---> a9fc0e0df3ca
Step 16/19 : COPY ["docker-entrypoint.sh", "/usr/bin/"]
 ---> f13c8e996a61
Step 17/19 : ENTRYPOINT ["/sbin/tini", "--", "/usr/bin/docker-entrypoint.sh"]
 ---> Running in 27028cb67c09
Removing intermediate container 27028cb67c09
 ---> 7a1f7fe3205e
Step 18/19 : USER zabbix
 ---> Running in ae82156b1d05
Removing intermediate container ae82156b1d05
 ---> 65fa1ab77810
Step 19/19 : CMD ["/usr/sbin/zabbix_server", "--foreground", "-c", "/etc/zabbix/zabbix_server.conf"]
 ---> Running in 26691a9de766
Removing intermediate container 26691a9de766
 ---> 9308d5c6b07d

Successfully built 9308d5c6b07d
Successfully tagged zabbix-server-mysql:alpine-local
Building zabbix-agent
Step 1/17 : FROM alpine:3.10
 ---> 965ea09ff2eb
Step 2/17 : LABEL org.opencontainers.image.title="Zabbix agent"       org.opencontainers.image.authors="Alexey Pustovalov <alexey.pustovalov@zabbix.com>"       org.opencontainers.image.vendor="Zabbix LLC"       org.opencontainers.image.url="https://zabbix.com/"       org.opencontainers.image.description="Zabbix agent is deployed on a monitoring target to actively monitor local resources and applications"       org.opencontainers.image.licenses="GPL v2.0"
 ---> Running in 6943d43b7e2b
Removing intermediate container 6943d43b7e2b
 ---> 4b74d3dd84b4
Step 3/17 : STOPSIGNAL SIGTERM
 ---> Running in 9ec1f3b45231
Removing intermediate container 9ec1f3b45231
 ---> f0fedfcb3892
Step 4/17 : RUN set -eux &&     addgroup -S -g 1000 zabbix &&     adduser -S             -D -G zabbix             -u 999             -h /var/lib/zabbix/         zabbix &&     mkdir -p /etc/zabbix &&     mkdir -p /etc/zabbix/zabbix_agentd.d &&     mkdir -p /var/lib/zabbix &&     mkdir -p /var/lib/zabbix/enc &&     mkdir -p /var/lib/zabbix/modules &&     chown --quiet -R zabbix:root /var/lib/zabbix &&     apk add --no-cache --clean-protected             tini             bash             coreutils             iputils             pcre             libcurl             libldap &&     rm -rf /var/cache/apk/*
 ---> Running in 12634dbbb8e5
+ addgroup -S -g 1000 zabbix
+ adduser -S -D -G zabbix -u 999 -h /var/lib/zabbix/ zabbix
+ mkdir -p /etc/zabbix
+ mkdir -p /etc/zabbix/zabbix_agentd.d
+ mkdir -p /var/lib/zabbix
+ mkdir -p /var/lib/zabbix/enc
+ mkdir -p /var/lib/zabbix/modules
+ chown --quiet -R zabbix:root /var/lib/zabbix
+ apk add --no-cache --clean-protected tini bash coreutils iputils pcre libcurl libldap
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/18) Installing ncurses-terminfo-base (6.1_p20190518-r0)
(2/18) Installing ncurses-terminfo (6.1_p20190518-r0)
(3/18) Installing ncurses-libs (6.1_p20190518-r0)
(4/18) Installing readline (8.0.0-r0)
(5/18) Installing bash (5.0.0-r0)
Executing bash-5.0.0-r0.post-install
(6/18) Installing libacl (2.2.52-r6)
(7/18) Installing libattr (2.4.48-r0)
(8/18) Installing coreutils (8.31-r0)
(9/18) Installing libcap (2.27-r0)
(10/18) Installing iputils (20180629-r1)
(11/18) Installing ca-certificates (20190108-r0)
(12/18) Installing nghttp2-libs (1.39.2-r0)
(13/18) Installing libcurl (7.66.0-r0)
(14/18) Installing db (5.3.28-r1)
(15/18) Installing libsasl (2.1.27-r4)
(16/18) Installing libldap (2.4.48-r0)
(17/18) Installing pcre (8.43-r0)
(18/18) Installing tini (0.18.0-r0)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 20 MiB in 32 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 12634dbbb8e5
 ---> 75777ae1981b
Step 5/17 : ARG MAJOR_VERSION=4.4
 ---> Running in 49fe7c0449d4
Removing intermediate container 49fe7c0449d4
 ---> 1d05afd5c846
Step 6/17 : ARG ZBX_VERSION=${MAJOR_VERSION}.4
 ---> Running in 8b800a6b8a1f
Removing intermediate container 8b800a6b8a1f
 ---> 98d91293bff7
Step 7/17 : ARG ZBX_SOURCES=https://git.zabbix.com/scm/zbx/zabbix.git
 ---> Running in 1a25e207183d
Removing intermediate container 1a25e207183d
 ---> a09dbc26db2b
Step 8/17 : ENV TERM=xterm ZBX_VERSION=${ZBX_VERSION} ZBX_SOURCES=${ZBX_SOURCES}
 ---> Running in 266d9a89118a
Removing intermediate container 266d9a89118a
 ---> 1b56fb44db0e
Step 9/17 : LABEL org.opencontainers.image.documentation="https://www.zabbix.com/documentation/${MAJOR_VERSION}/manual/installation/containers"       org.opencontainers.image.version="${ZBX_VERSION}"       org.opencontainers.image.source="${ZBX_SOURCES}"
 ---> Running in e8c30c2692bb
Removing intermediate container e8c30c2692bb
 ---> 42d07f58017c
Step 10/17 : RUN set -eux &&     apk add --no-cache --virtual build-dependencies             autoconf             automake             curl-dev             openssl-dev             openldap-dev             g++             pcre-dev             make             git             coreutils &&     cd /tmp/ &&     git clone ${ZBX_SOURCES} --branch ${ZBX_VERSION} --depth 1 --single-branch zabbix-${ZBX_VERSION} &&     cd /tmp/zabbix-${ZBX_VERSION} &&     zabbix_revision=`git rev-parse --short HEAD` &&     sed -i "s/{ZABBIX_REVISION}/$zabbix_revision/g" include/version.h &&     ./bootstrap.sh &&     export CFLAGS="-fPIC -pie -Wl,-z,relro -Wl,-z,now" &&     ./configure             --datadir=/usr/lib             --libdir=/usr/lib/zabbix             --prefix=/usr             --sysconfdir=/etc/zabbix             --prefix=/usr             --enable-agent             --with-libcurl             --with-ldap             --with-openssl             --enable-ipv6             --silent &&     make -j"$(nproc)" -s &&     cp /tmp/zabbix-${ZBX_VERSION}/src/zabbix_agent/zabbix_agentd /usr/sbin/zabbix_agentd &&     cp /tmp/zabbix-${ZBX_VERSION}/src/zabbix_get/zabbix_get /usr/bin/zabbix_get &&     cp /tmp/zabbix-${ZBX_VERSION}/src/zabbix_sender/zabbix_sender /usr/bin/zabbix_sender &&     cp /tmp/zabbix-${ZBX_VERSION}/conf/zabbix_agentd.conf /etc/zabbix/zabbix_agentd.conf &&     chown -R zabbix:zabbix /etc/zabbix/ &&     cd /tmp/ &&     rm -rf /tmp/zabbix-${ZBX_VERSION}/ &&     apk del --purge --no-network             build-dependencies &&     rm -rf /var/cache/apk/*
 ---> Running in 18c3cad986b4
+ apk add --no-cache --virtual build-dependencies autoconf automake curl-dev openssl-dev openldap-dev g++ pcre-dev make git coreutils
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/45) Upgrading libcrypto1.1 (1.1.1d-r0 -> 1.1.1d-r2)
(2/45) Upgrading libssl1.1 (1.1.1d-r0 -> 1.1.1d-r2)
(3/45) Installing m4 (1.4.18-r1)
(4/45) Installing libbz2 (1.0.6-r7)
(5/45) Installing perl (5.28.2-r1)
(6/45) Installing autoconf (2.69-r2)
(7/45) Installing automake (1.16.1-r0)
(8/45) Installing pkgconf (1.6.1-r1)
(9/45) Installing openssl-dev (1.1.1d-r2)
(10/45) Installing nghttp2-dev (1.39.2-r0)
(11/45) Installing zlib-dev (1.2.11-r1)
(12/45) Installing curl-dev (7.66.0-r0)
(13/45) Installing cyrus-sasl-dev (2.1.27-r4)
(14/45) Installing libuuid (2.33.2-r0)
(15/45) Installing libblkid (2.33.2-r0)
(16/45) Installing libfdisk (2.33.2-r0)
(17/45) Installing libmount (2.33.2-r0)
(18/45) Installing libsmartcols (2.33.2-r0)
(19/45) Installing util-linux-dev (2.33.2-r0)
(20/45) Installing openldap-dev (2.4.48-r0)
(21/45) Installing libgcc (8.3.0-r0)
(22/45) Installing libstdc++ (8.3.0-r0)
(23/45) Installing binutils (2.32-r0)
(24/45) Installing gmp (6.1.2-r1)
(25/45) Installing isl (0.18-r0)
(26/45) Installing libgomp (8.3.0-r0)
(27/45) Installing libatomic (8.3.0-r0)
(28/45) Installing mpfr3 (3.1.5-r1)
(29/45) Installing mpc1 (1.1.0-r0)
(30/45) Installing gcc (8.3.0-r0)
(31/45) Installing musl-dev (1.1.22-r3)
(32/45) Installing libc-dev (0.7.1-r0)
(33/45) Installing g++ (8.3.0-r0)
(34/45) Installing libpcre16 (8.43-r0)
(35/45) Installing libpcre32 (8.43-r0)
(36/45) Installing libpcrecpp (8.43-r0)
(37/45) Installing pcre-dev (8.43-r0)
(38/45) Installing make (4.2.1-r2)
(39/45) Installing expat (2.2.8-r0)
(40/45) Installing pcre2 (10.33-r0)
(41/45) Installing git (2.22.2-r0)
(42/45) Installing perl-error (0.17027-r0)
(43/45) Installing perl-git (2.22.2-r0)
(44/45) Installing git-perl (2.22.2-r0)
(45/45) Installing build-dependencies (20200116.013629)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 258 MiB in 75 packages
+ cd /tmp/
+ git clone https://git.zabbix.com/scm/zbx/zabbix.git --branch 4.4.4 --depth 1 --single-branch zabbix-4.4.4
Cloning into 'zabbix-4.4.4'...
Note: checking out '3131fdac04eb1ce833315164258c00a6c565372e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

+ cd /tmp/zabbix-4.4.4
+ git rev-parse --short HEAD
+ zabbix_revision=3131fda
+ sed -i 's/{ZABBIX_REVISION}/3131fda/g' include/version.h
+ ./bootstrap.sh
configure.ac:40: installing './compile'
configure.ac:32: installing './config.guess'
configure.ac:32: installing './config.sub'
configure.ac:24: installing './install-sh'
configure.ac:24: installing './missing'
src/libs/zbxalgo/Makefile.am: installing './depcomp'
+ export 'CFLAGS=-fPIC -pie -Wl,-z,relro -Wl,-z,now'
+ ./configure '--datadir=/usr/lib' '--libdir=/usr/lib/zabbix' '--prefix=/usr' '--sysconfdir=/etc/zabbix' '--prefix=/usr' --enable-agent --with-libcurl --with-ldap --with-openssl --enable-ipv6 --silent


Configuration:

  Detected OS:           linux-gnu
  Install path:          /usr
  Compilation arch:      linux

  Compiler:              cc
  Compiler flags:         -fPIC -pie -Wl,-z,relro -Wl,-z,now 

  Library-specific flags:
    TLS:                   -I/usr/include
    LDAP:                  -I/usr/include

  Enable server:         no

  Enable proxy:          no

  Enable agent:          yes
  Agent details:
    TLS:                   OpenSSL
    Linker flags:             -L/usr/lib -L/usr/lib    
    Libraries:                -lssl -lcrypto -lldap -llber   -lcurl -lnghttp2 -lssl -lcrypto -lssl -lcrypto -lz -lm   -lpcre 
    Configuration file:    /etc/zabbix/zabbix_agentd.conf
    Modules:               /usr/lib/zabbix/modules

  Enable agent 2:        no

  Enable Java gateway:   no

  LDAP support:          yes
  IPv6 support:          yes

***********************************************************
*            Now run 'make install'                       *
*                                                         *
*            Thank you for using Zabbix!                  *
*              <http://www.zabbix.com>                    *
***********************************************************

+ nproc
+ make -j4 -s
Making all in src
Making all in libs
Making all in zbxcrypto
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcommon
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxlog
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxalgo
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxnix
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxconf
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxhttp
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxsysinfo
Making all in agent
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in common
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in simple
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in linux
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxsys
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcomms
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxjson
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxexec
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxmodules
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxregexp
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxipcservice
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcompress
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_agent
Making all in logfiles
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_get
Making all in zabbix_sender
Making all in database
Making all in ibm_db2
Making all in mysql
Making all in oracle
Making all in postgresql
Making all in sqlite3
Making all in man
Making all in misc
+ cp /tmp/zabbix-4.4.4/src/zabbix_agent/zabbix_agentd /usr/sbin/zabbix_agentd
+ cp /tmp/zabbix-4.4.4/src/zabbix_get/zabbix_get /usr/bin/zabbix_get
+ cp /tmp/zabbix-4.4.4/src/zabbix_sender/zabbix_sender /usr/bin/zabbix_sender
+ cp /tmp/zabbix-4.4.4/conf/zabbix_agentd.conf /etc/zabbix/zabbix_agentd.conf
+ chown -R zabbix:zabbix /etc/zabbix/
+ cd /tmp/
+ rm -rf /tmp/zabbix-4.4.4/
+ apk del --purge --no-network build-dependencies
WARNING: Ignoring APKINDEX.00740ba1.tar.gz: No such file or directory
WARNING: Ignoring APKINDEX.d8b2a6f4.tar.gz: No such file or directory
(1/43) Purging git-perl (2.22.2-r0)
(2/43) Purging perl-git (2.22.2-r0)
(3/43) Purging perl-error (0.17027-r0)
(4/43) Purging build-dependencies (20200116.013629)
(5/43) Purging autoconf (2.69-r2)
(6/43) Purging m4 (1.4.18-r1)
(7/43) Purging automake (1.16.1-r0)
(8/43) Purging perl (5.28.2-r1)
(9/43) Purging curl-dev (7.66.0-r0)
(10/43) Purging nghttp2-dev (1.39.2-r0)
(11/43) Purging zlib-dev (1.2.11-r1)
(12/43) Purging openldap-dev (2.4.48-r0)
(13/43) Purging openssl-dev (1.1.1d-r2)
(14/43) Purging cyrus-sasl-dev (2.1.27-r4)
(15/43) Purging util-linux-dev (2.33.2-r0)
(16/43) Purging libfdisk (2.33.2-r0)
(17/43) Purging libmount (2.33.2-r0)
(18/43) Purging libsmartcols (2.33.2-r0)
(19/43) Purging g++ (8.3.0-r0)
(20/43) Purging gcc (8.3.0-r0)
(21/43) Purging binutils (2.32-r0)
(22/43) Purging libatomic (8.3.0-r0)
(23/43) Purging libgomp (8.3.0-r0)
(24/43) Purging libc-dev (0.7.1-r0)
(25/43) Purging musl-dev (1.1.22-r3)
(26/43) Purging pcre-dev (8.43-r0)
(27/43) Purging libpcre16 (8.43-r0)
(28/43) Purging libpcre32 (8.43-r0)
(29/43) Purging libpcrecpp (8.43-r0)
(30/43) Purging make (4.2.1-r2)
(31/43) Purging git (2.22.2-r0)
(32/43) Purging libbz2 (1.0.6-r7)
(33/43) Purging pkgconf (1.6.1-r1)
(34/43) Purging libblkid (2.33.2-r0)
(35/43) Purging libuuid (2.33.2-r0)
(36/43) Purging libstdc++ (8.3.0-r0)
(37/43) Purging libgcc (8.3.0-r0)
(38/43) Purging mpc1 (1.1.0-r0)
(39/43) Purging mpfr3 (3.1.5-r1)
(40/43) Purging isl (0.18-r0)
(41/43) Purging gmp (6.1.2-r1)
(42/43) Purging expat (2.2.8-r0)
(43/43) Purging pcre2 (10.33-r0)
Executing busybox-1.30.1-r2.trigger
OK: 20 MiB in 32 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 18c3cad986b4
 ---> 7a8b6b4609d6
Step 11/17 : EXPOSE 10050/TCP
 ---> Running in f89d8798cef3
Removing intermediate container f89d8798cef3
 ---> 964268b5da83
Step 12/17 : WORKDIR /var/lib/zabbix
 ---> Running in 561bffcec2bf
Removing intermediate container 561bffcec2bf
 ---> e3e5952185ad
Step 13/17 : VOLUME ["/var/lib/zabbix/enc"]
 ---> Running in 8084e236ded3
Removing intermediate container 8084e236ded3
 ---> 8804f6a4a728
Step 14/17 : COPY ["docker-entrypoint.sh", "/usr/bin/"]
 ---> f3b714a3fdb9
Step 15/17 : ENTRYPOINT ["/sbin/tini", "--", "/usr/bin/docker-entrypoint.sh"]
 ---> Running in a3cffb1e5d4d
Removing intermediate container a3cffb1e5d4d
 ---> 30d8591d89e5
Step 16/17 : USER zabbix
 ---> Running in 93e592ccdc9a
Removing intermediate container 93e592ccdc9a
 ---> a3aa09dc3d23
Step 17/17 : CMD ["/usr/sbin/zabbix_agentd", "--foreground", "-c", "/etc/zabbix/zabbix_agentd.conf"]
 ---> Running in 350ca5db3de0
Removing intermediate container 350ca5db3de0
 ---> a3b39ce492b7

Successfully built a3b39ce492b7
Successfully tagged zabbix-agent:alpine-local
Building zabbix-web-nginx-mysql
Step 1/29 : FROM alpine:3.10
 ---> 965ea09ff2eb
Step 2/29 : LABEL maintainer="Alexey Pustovalov <alexey.pustovalov@zabbix.com>"
 ---> Running in 1703db6efd49
Removing intermediate container 1703db6efd49
 ---> 14c543a8ce10
Step 3/29 : ARG BUILD_DATE
 ---> Running in f71ce627dc6e
Removing intermediate container f71ce627dc6e
 ---> a25fe4a242d7
Step 4/29 : ARG VCS_REF
 ---> Running in 7cc156358f6e
Removing intermediate container 7cc156358f6e
 ---> facc84a934d0
Step 5/29 : ARG APK_FLAGS_COMMON=""
 ---> Running in 7336b654b628
Removing intermediate container 7336b654b628
 ---> a4790ceae110
Step 6/29 : ARG APK_FLAGS_PERSISTENT="${APK_FLAGS_COMMON} --clean-protected --no-cache"
 ---> Running in a5537dbc85a5
Removing intermediate container a5537dbc85a5
 ---> f3251bef964e
Step 7/29 : ARG APK_FLAGS_DEV="${APK_FLAGS_COMMON} --no-cache"
 ---> Running in 18bbe3c94cb4
Removing intermediate container 18bbe3c94cb4
 ---> dc9492c444c9
Step 8/29 : ENV TERM=xterm     ZBX_TYPE=frontend ZBX_DB_TYPE=mysql ZBX_OPT_TYPE=nginx
 ---> Running in 727d6c9b6ec9
Removing intermediate container 727d6c9b6ec9
 ---> 9d95077735a6
Step 9/29 : LABEL org.label-schema.name="zabbix-web-${ZBX_OPT_TYPE}-${ZBX_DB_TYPE}-alpine"       org.label-schema.vendor="Zabbix LLC"       org.label-schema.url="https://zabbix.com/"       org.label-schema.description="Zabbix web-interface based on Nginx web server with MySQL database support"       org.label-schema.vcs-ref="${VCS_REF}"       org.label-schema.build-date="${BUILD_DATE}"       org.label-schema.schema-version="1.0"       org.label-schema.license="GPL v2.0"
 ---> Running in 56ef2725c66d
Removing intermediate container 56ef2725c66d
 ---> f053f44d374a
Step 10/29 : STOPSIGNAL SIGTERM
 ---> Running in 700bc4709857
Removing intermediate container 700bc4709857
 ---> ca9b5c6f7d54
Step 11/29 : RUN set -eux &&     addgroup zabbix &&     adduser -S             -D -G zabbix             -h /var/lib/zabbix/             -H         zabbix &&     mkdir -p /etc/zabbix &&     mkdir -p /etc/zabbix/web &&     chown --quiet -R zabbix:root /etc/zabbix &&     apk update &&     apk add ${APK_FLAGS_PERSISTENT}             bash             curl             mariadb-client             mariadb-connector-c             nginx             php7-bcmath             php7-ctype             php7-fpm             php7-gd             php7-gettext             php7-json             php7-ldap             php7-mbstring             php7-mysqli             php7-session             php7-simplexml             php7-sockets             php7-fileinfo             php7-xmlreader             php7-xmlwriter             supervisor &&     rm -f /etc/nginx/conf.d/*.conf &&     rm -rf /var/cache/apk/*
 ---> Running in 8a47bc1b4325
+ addgroup zabbix
+ adduser -S -D -G zabbix -h /var/lib/zabbix/ -H zabbix
+ mkdir -p /etc/zabbix
+ mkdir -p /etc/zabbix/web
+ chown --quiet -R zabbix:root /etc/zabbix
+ apk update
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
v3.10.3-129-g58d7b94f01 [http://dl-cdn.alpinelinux.org/alpine/v3.10/main]
v3.10.3-127-g5d75746816 [http://dl-cdn.alpinelinux.org/alpine/v3.10/community]
OK: 10347 distinct packages available
+ apk add --clean-protected --no-cache bash curl mariadb-client mariadb-connector-c nginx php7-bcmath php7-ctype php7-fpm php7-gd php7-gettext php7-json php7-ldap php7-mbstring php7-mysqli php7-session php7-simplexml php7-sockets php7-fileinfo php7-xmlreader php7-xmlwriter supervisor
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/67) Installing ncurses-terminfo-base (6.1_p20190518-r0)
(2/67) Installing ncurses-terminfo (6.1_p20190518-r0)
(3/67) Installing ncurses-libs (6.1_p20190518-r0)
(4/67) Installing readline (8.0.0-r0)
(5/67) Installing bash (5.0.0-r0)
Executing bash-5.0.0-r0.post-install
(6/67) Installing ca-certificates (20190108-r0)
(7/67) Installing nghttp2-libs (1.39.2-r0)
(8/67) Installing libcurl (7.66.0-r0)
(9/67) Installing curl (7.66.0-r0)
(10/67) Installing mariadb-common (10.3.20-r0)
(11/67) Installing libgcc (8.3.0-r0)
(12/67) Installing libstdc++ (8.3.0-r0)
(13/67) Installing mariadb-client (10.3.20-r0)
(14/67) Installing mariadb-connector-c (3.0.10-r0)
(15/67) Installing pcre (8.43-r0)
(16/67) Installing nginx (1.16.1-r1)
Executing nginx-1.16.1-r1.pre-install
(17/67) Installing php7-common (7.3.13-r0)
(18/67) Installing php7-bcmath (7.3.13-r0)
(19/67) Installing php7-ctype (7.3.13-r0)
(20/67) Installing php7-fileinfo (7.3.13-r0)
(21/67) Installing argon2-libs (20171227-r2)
(22/67) Installing libedit (20190324.3.1-r0)
(23/67) Installing pcre2 (10.33-r0)
(24/67) Installing libxml2 (2.9.9-r3)
(25/67) Installing php7-fpm (7.3.13-r0)
(26/67) Installing libxau (1.0.9-r0)
(27/67) Installing libbsd (0.9.1-r0)
(28/67) Installing libxdmcp (1.1.3-r0)
(29/67) Installing libxcb (1.13.1-r0)
(30/67) Installing libx11 (1.6.8-r1)
(31/67) Installing libxext (1.3.4-r0)
(32/67) Installing libice (1.0.9-r3)
(33/67) Installing libuuid (2.33.2-r0)
(34/67) Installing libsm (1.2.3-r0)
(35/67) Installing libxt (1.1.5-r2)
(36/67) Installing libxpm (3.5.12-r0)
(37/67) Installing libbz2 (1.0.6-r7)
(38/67) Installing libpng (1.6.37-r1)
(39/67) Installing freetype (2.10.0-r0)
(40/67) Installing libjpeg-turbo (2.0.4-r0)
(41/67) Installing libwebp (1.0.2-r0)
(42/67) Installing php7-gd (7.3.13-r0)
(43/67) Installing libintl (0.19.8.1-r4)
(44/67) Installing php7-gettext (7.3.13-r0)
(45/67) Installing php7-json (7.3.13-r0)
(46/67) Installing db (5.3.28-r1)
(47/67) Installing libsasl (2.1.27-r4)
(48/67) Installing libldap (2.4.48-r0)
(49/67) Installing php7-ldap (7.3.13-r0)
(50/67) Installing php7-mbstring (7.3.13-r0)
(51/67) Installing php7-openssl (7.3.13-r0)
(52/67) Installing php7-mysqlnd (7.3.13-r0)
(53/67) Installing php7-mysqli (7.3.13-r0)
(54/67) Installing php7-session (7.3.13-r0)
(55/67) Installing php7-simplexml (7.3.13-r0)
(56/67) Installing php7-sockets (7.3.13-r0)
(57/67) Installing php7-dom (7.3.13-r0)
(58/67) Installing php7-xmlreader (7.3.13-r0)
(59/67) Installing php7-xmlwriter (7.3.13-r0)
(60/67) Installing expat (2.2.8-r0)
(61/67) Installing libffi (3.2.1-r6)
(62/67) Installing gdbm (1.13-r1)
(63/67) Installing sqlite-libs (3.28.0-r2)
(64/67) Installing python2 (2.7.16-r2)
(65/67) Installing py-meld3 (1.0.2-r1)
(66/67) Installing py-setuptools (40.8.0-r1)
(67/67) Installing supervisor (3.3.5-r0)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 122 MiB in 81 packages
+ rm -f /etc/nginx/conf.d/default.conf
+ rm -rf /var/cache/apk/APKINDEX.00740ba1.tar.gz /var/cache/apk/APKINDEX.d8b2a6f4.tar.gz
Removing intermediate container 8a47bc1b4325
 ---> 298fa493ccd8
Step 12/29 : ARG MAJOR_VERSION=4.4
 ---> Running in 498fef8ca7ec
Removing intermediate container 498fef8ca7ec
 ---> 878e73a5c523
Step 13/29 : ARG ZBX_VERSION=${MAJOR_VERSION}.4
 ---> Running in cfe6a07fecc7
Removing intermediate container cfe6a07fecc7
 ---> 621b2fec73f7
Step 14/29 : ARG ZBX_SOURCES=https://git.zabbix.com/scm/zbx/zabbix.git
 ---> Running in 938e7a7fc21a
Removing intermediate container 938e7a7fc21a
 ---> e87cd8f6fbe8
Step 15/29 : ENV ZBX_VERSION=${ZBX_VERSION} ZBX_SOURCES=${ZBX_SOURCES}
 ---> Running in 9d072644bd37
Removing intermediate container 9d072644bd37
 ---> 4a5e0c30f850
Step 16/29 : LABEL org.label-schema.usage="https://www.zabbix.com/documentation/${MAJOR_VERSION}/manual/installation/containers"       org.label-schema.version="${ZBX_VERSION}"       org.label-schema.vcs-url="${ZBX_SOURCES}"       org.label-schema.docker.cmd="docker run --name zabbix-web-${ZBX_OPT_TYPE}-${ZBX_DB_TYPE} --link mysql-server:mysql --link zabbix-server:zabbix-server -p 80:80 -d zabbix-web-${ZBX_OPT_TYPE}-${ZBX_DB_TYPE}:alpine-${ZBX_VERSION}"
 ---> Running in 7273096b46cf
Removing intermediate container 7273096b46cf
 ---> d20bc6524ca3
Step 17/29 : RUN set -eux &&     apk add ${APK_FLAGS_DEV} --virtual build-dependencies             coreutils             gettext             git &&     cd /usr/share/ &&     git clone ${ZBX_SOURCES} --branch ${ZBX_VERSION} --depth 1 --single-branch zabbix-${ZBX_VERSION} &&     mkdir /usr/share/zabbix/ &&     cp -R /usr/share/zabbix-${ZBX_VERSION}/frontends/php/* /usr/share/zabbix/ &&     rm -rf /usr/share/zabbix-${ZBX_VERSION}/ &&     cd /usr/share/zabbix/ &&     rm -f conf/zabbix.conf.php &&     rm -rf tests &&     ./locale/make_mo.sh &&     chown --quiet -R nginx:nginx /usr/share/zabbix &&     apk del ${APK_FLAGS_COMMON} --purge --no-network             build-dependencies &&     rm -rf /var/cache/apk/*
 ---> Running in b208933e8921
+ apk add --no-cache --virtual build-dependencies coreutils gettext git
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/8) Installing libacl (2.2.52-r6)
(2/8) Installing libattr (2.4.48-r0)
(3/8) Installing coreutils (8.31-r0)
(4/8) Installing libgomp (8.3.0-r0)
(5/8) Installing libunistring (0.9.10-r0)
(6/8) Installing gettext (0.19.8.1-r4)
(7/8) Installing git (2.22.2-r0)
(8/8) Installing build-dependencies (20200116.013712)
Executing busybox-1.30.1-r2.trigger
OK: 140 MiB in 89 packages
+ cd /usr/share/
+ git clone https://git.zabbix.com/scm/zbx/zabbix.git --branch 4.4.4 --depth 1 --single-branch zabbix-4.4.4
Cloning into 'zabbix-4.4.4'...
Note: checking out '3131fdac04eb1ce833315164258c00a6c565372e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

+ mkdir /usr/share/zabbix/
+ cp -R /usr/share/zabbix-4.4.4/frontends/php/actionconf.php /usr/share/zabbix-4.4.4/frontends/php/adm.gui.php /usr/share/zabbix-4.4.4/frontends/php/adm.housekeeper.php /usr/share/zabbix-4.4.4/frontends/php/adm.iconmapping.php /usr/share/zabbix-4.4.4/frontends/php/adm.images.php /usr/share/zabbix-4.4.4/frontends/php/adm.macros.php /usr/share/zabbix-4.4.4/frontends/php/adm.other.php /usr/share/zabbix-4.4.4/frontends/php/adm.regexps.php /usr/share/zabbix-4.4.4/frontends/php/adm.triggerdisplayoptions.php /usr/share/zabbix-4.4.4/frontends/php/adm.triggerseverities.php /usr/share/zabbix-4.4.4/frontends/php/adm.valuemapping.php /usr/share/zabbix-4.4.4/frontends/php/adm.workingtime.php /usr/share/zabbix-4.4.4/frontends/php/api_jsonrpc.php /usr/share/zabbix-4.4.4/frontends/php/app /usr/share/zabbix-4.4.4/frontends/php/applications.php /usr/share/zabbix-4.4.4/frontends/php/assets /usr/share/zabbix-4.4.4/frontends/php/audio /usr/share/zabbix-4.4.4/frontends/php/auditacts.php /usr/share/zabbix-4.4.4/frontends/php/auditlogs.php /usr/share/zabbix-4.4.4/frontends/php/browserwarning.php /usr/share/zabbix-4.4.4/frontends/php/chart.php /usr/share/zabbix-4.4.4/frontends/php/chart2.php /usr/share/zabbix-4.4.4/frontends/php/chart3.php /usr/share/zabbix-4.4.4/frontends/php/chart4.php /usr/share/zabbix-4.4.4/frontends/php/chart5.php /usr/share/zabbix-4.4.4/frontends/php/chart6.php /usr/share/zabbix-4.4.4/frontends/php/chart7.php /usr/share/zabbix-4.4.4/frontends/php/charts.php /usr/share/zabbix-4.4.4/frontends/php/conf /usr/share/zabbix-4.4.4/frontends/php/conf.import.php /usr/share/zabbix-4.4.4/frontends/php/correlation.php /usr/share/zabbix-4.4.4/frontends/php/disc_prototypes.php /usr/share/zabbix-4.4.4/frontends/php/discoveryconf.php /usr/share/zabbix-4.4.4/frontends/php/favicon.ico /usr/share/zabbix-4.4.4/frontends/php/graphs.php /usr/share/zabbix-4.4.4/frontends/php/history.php /usr/share/zabbix-4.4.4/frontends/php/host_discovery.php /usr/share/zabbix-4.4.4/frontends/php/host_prototypes.php /usr/share/zabbix-4.4.4/frontends/php/host_screen.php /usr/share/zabbix-4.4.4/frontends/php/hostgroups.php /usr/share/zabbix-4.4.4/frontends/php/hostinventories.php /usr/share/zabbix-4.4.4/frontends/php/hostinventoriesoverview.php /usr/share/zabbix-4.4.4/frontends/php/hosts.php /usr/share/zabbix-4.4.4/frontends/php/httpconf.php /usr/share/zabbix-4.4.4/frontends/php/httpdetails.php /usr/share/zabbix-4.4.4/frontends/php/image.php /usr/share/zabbix-4.4.4/frontends/php/imgstore.php /usr/share/zabbix-4.4.4/frontends/php/include /usr/share/zabbix-4.4.4/frontends/php/index.php /usr/share/zabbix-4.4.4/frontends/php/index_http.php /usr/share/zabbix-4.4.4/frontends/php/items.php /usr/share/zabbix-4.4.4/frontends/php/js /usr/share/zabbix-4.4.4/frontends/php/jsLoader.php /usr/share/zabbix-4.4.4/frontends/php/jsrpc.php /usr/share/zabbix-4.4.4/frontends/php/latest.php /usr/share/zabbix-4.4.4/frontends/php/local /usr/share/zabbix-4.4.4/frontends/php/locale /usr/share/zabbix-4.4.4/frontends/php/maintenance.php /usr/share/zabbix-4.4.4/frontends/php/map.import.php /usr/share/zabbix-4.4.4/frontends/php/map.php /usr/share/zabbix-4.4.4/frontends/php/overview.php /usr/share/zabbix-4.4.4/frontends/php/queue.php /usr/share/zabbix-4.4.4/frontends/php/report2.php /usr/share/zabbix-4.4.4/frontends/php/report4.php /usr/share/zabbix-4.4.4/frontends/php/robots.txt /usr/share/zabbix-4.4.4/frontends/php/screen.import.php /usr/share/zabbix-4.4.4/frontends/php/screenconf.php /usr/share/zabbix-4.4.4/frontends/php/screenedit.php /usr/share/zabbix-4.4.4/frontends/php/screens.php /usr/share/zabbix-4.4.4/frontends/php/services.php /usr/share/zabbix-4.4.4/frontends/php/setup.php /usr/share/zabbix-4.4.4/frontends/php/slideconf.php /usr/share/zabbix-4.4.4/frontends/php/slides.php /usr/share/zabbix-4.4.4/frontends/php/srv_status.php /usr/share/zabbix-4.4.4/frontends/php/sysmap.php /usr/share/zabbix-4.4.4/frontends/php/sysmaps.php /usr/share/zabbix-4.4.4/frontends/php/templates.php /usr/share/zabbix-4.4.4/frontends/php/tests /usr/share/zabbix-4.4.4/frontends/php/toptriggers.php /usr/share/zabbix-4.4.4/frontends/php/tr_events.php /usr/share/zabbix-4.4.4/frontends/php/trigger_prototypes.php /usr/share/zabbix-4.4.4/frontends/php/triggers.php /usr/share/zabbix-4.4.4/frontends/php/usergrps.php /usr/share/zabbix-4.4.4/frontends/php/zabbix.php /usr/share/zabbix/
+ rm -rf /usr/share/zabbix-4.4.4/
+ cd /usr/share/zabbix/
+ rm -f conf/zabbix.conf.php
+ rm -rf tests
+ ./locale/make_mo.sh
+ chown --quiet -R nginx:nginx /usr/share/zabbix
+ apk del --purge --no-network build-dependencies
WARNING: Ignoring APKINDEX.00740ba1.tar.gz: No such file or directory
WARNING: Ignoring APKINDEX.d8b2a6f4.tar.gz: No such file or directory
(1/8) Purging build-dependencies (20200116.013712)
(2/8) Purging coreutils (8.31-r0)
Executing coreutils-8.31-r0.post-deinstall
(3/8) Purging gettext (0.19.8.1-r4)
(4/8) Purging git (2.22.2-r0)
(5/8) Purging libacl (2.2.52-r6)
(6/8) Purging libattr (2.4.48-r0)
(7/8) Purging libgomp (8.3.0-r0)
(8/8) Purging libunistring (0.9.10-r0)
Executing busybox-1.30.1-r2.trigger
OK: 122 MiB in 81 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container b208933e8921
 ---> bf2ba87870df
Step 18/29 : EXPOSE 80/TCP 443/TCP
 ---> Running in abe2f485c126
Removing intermediate container abe2f485c126
 ---> ed03c77454b0
Step 19/29 : WORKDIR /usr/share/zabbix
 ---> Running in 05fa1bc00420
Removing intermediate container 05fa1bc00420
 ---> 7b856f6c6ff9
Step 20/29 : VOLUME ["/etc/ssl/nginx"]
 ---> Running in 35f87f3dc635
Removing intermediate container 35f87f3dc635
 ---> 47da988a32c9
Step 21/29 : COPY ["conf/etc/supervisor/", "/etc/supervisor/"]
 ---> ab27b2bacee2
Step 22/29 : COPY ["conf/etc/zabbix/nginx.conf", "/etc/zabbix/"]
 ---> 79f058e306a2
Step 23/29 : COPY ["conf/etc/zabbix/nginx_ssl.conf", "/etc/zabbix/"]
 ---> f0e5285a43de
Step 24/29 : COPY ["conf/etc/zabbix/web/zabbix.conf.php", "/etc/zabbix/web/"]
 ---> 1c87ac58af07
Step 25/29 : COPY ["conf/etc/nginx/nginx.conf", "/etc/nginx/"]
 ---> 82218b2e538d
Step 26/29 : COPY ["conf/etc/php7/php-fpm.conf", "/etc/php7/"]
 ---> ced8874477c5
Step 27/29 : COPY ["conf/etc/php7/conf.d/99-zabbix.ini", "/etc/php7/conf.d/"]
 ---> 48ef15d56835
Step 28/29 : COPY ["docker-entrypoint.sh", "/usr/bin/"]
 ---> 036f2af34ed0
Step 29/29 : ENTRYPOINT ["docker-entrypoint.sh"]
 ---> Running in 72317578d386
Removing intermediate container 72317578d386
 ---> 6f39ef10c9e5

Successfully built 6f39ef10c9e5
Successfully tagged zabbix-web-nginx-mysql:alpine-local
Building zabbix-web-apache-mysql
Step 1/20 : FROM alpine:3.10
 ---> 965ea09ff2eb
Step 2/20 : LABEL org.opencontainers.image.title="Zabbix web-interface (Apache, MySQL)"       org.opencontainers.image.authors="Alexey Pustovalov <alexey.pustovalov@zabbix.com>"       org.opencontainers.image.vendor="Zabbix LLC"       org.opencontainers.image.url="https://zabbix.com/"       org.opencontainers.image.description="abbix web-interface based on Apache2 web server with MySQL database support"       org.opencontainers.image.licenses="GPL v2.0"
 ---> Running in 0804c9aa008d
Removing intermediate container 0804c9aa008d
 ---> 5d8e28276015
Step 3/20 : STOPSIGNAL SIGTERM
 ---> Running in 9a3e5f42c3ca
Removing intermediate container 9a3e5f42c3ca
 ---> af7b2e4172b9
Step 4/20 : RUN set -eux &&     addgroup -S -g 1000 zabbix &&     adduser -S             -D -G zabbix             -u 999             -h /var/lib/zabbix/             -H         zabbix &&     mkdir -p /etc/zabbix &&     mkdir -p /etc/zabbix/web &&     chown --quiet -R zabbix:root /etc/zabbix &&     apk add --clean-protected --no-cache             apache2             bash             curl             mariadb-client             mariadb-connector-c             php7-apache2             php7-bcmath             php7-ctype             php7-gd             php7-gettext             php7-json             php7-ldap             php7-mbstring             php7-mysqli             php7-session             php7-simplexml             php7-sockets             php7-fileinfo             php7-xmlreader             php7-xmlwriter &&     apk add --clean-protected --no-cache --no-scripts apache2-ssl &&     rm -f "/etc/apache2/conf.d/default.conf" &&     rm -f "/etc/apache2/conf.d/ssl.conf" &&     sed -ri         -e 's!^(\s*CustomLog)\s+\S+!\1 /proc/self/fd/1!g'         -e 's!^(\s*ErrorLog)\s+\S+!\1 /proc/self/fd/2!g'         "/etc/apache2/httpd.conf" &&     sed -ri         -e 's!^(\s*PidFile)\s+\S+!\1 "/var/run/httpd.pid"!g'         "/etc/apache2/conf.d/mpm.conf" &&     rm -f "/var/run/apache2/apache2.pid" &&     rm -rf /var/cache/apk/*
 ---> Running in 1d7453cef80f
+ addgroup -S -g 1000 zabbix
+ adduser -S -D -G zabbix -u 999 -h /var/lib/zabbix/ -H zabbix
+ mkdir -p /etc/zabbix
+ mkdir -p /etc/zabbix/web
+ chown --quiet -R zabbix:root /etc/zabbix
+ apk add --clean-protected --no-cache apache2 bash curl mariadb-client mariadb-connector-c php7-apache2 php7-bcmath php7-ctype php7-gd php7-gettext php7-json php7-ldap php7-mbstring php7-mysqli php7-session php7-simplexml php7-sockets php7-fileinfo php7-xmlreader php7-xmlwriter
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/62) Installing libuuid (2.33.2-r0)
(2/62) Installing apr (1.6.5-r0)
(3/62) Installing expat (2.2.8-r0)
(4/62) Installing apr-util (1.6.1-r6)
(5/62) Installing pcre (8.43-r0)
(6/62) Installing apache2 (2.4.41-r0)
Executing apache2-2.4.41-r0.pre-install
(7/62) Installing ncurses-terminfo-base (6.1_p20190518-r0)
(8/62) Installing ncurses-terminfo (6.1_p20190518-r0)
(9/62) Installing ncurses-libs (6.1_p20190518-r0)
(10/62) Installing readline (8.0.0-r0)
(11/62) Installing bash (5.0.0-r0)
Executing bash-5.0.0-r0.post-install
(12/62) Installing ca-certificates (20190108-r0)
(13/62) Installing nghttp2-libs (1.39.2-r0)
(14/62) Installing libcurl (7.66.0-r0)
(15/62) Installing curl (7.66.0-r0)
(16/62) Installing mariadb-common (10.3.20-r0)
(17/62) Installing libgcc (8.3.0-r0)
(18/62) Installing libstdc++ (8.3.0-r0)
(19/62) Installing mariadb-client (10.3.20-r0)
(20/62) Installing mariadb-connector-c (3.0.10-r0)
(21/62) Installing php7-common (7.3.13-r0)
(22/62) Installing argon2-libs (20171227-r2)
(23/62) Installing libedit (20190324.3.1-r0)
(24/62) Installing pcre2 (10.33-r0)
(25/62) Installing libxml2 (2.9.9-r3)
(26/62) Installing php7-apache2 (7.3.13-r0)
(27/62) Installing php7-bcmath (7.3.13-r0)
(28/62) Installing php7-ctype (7.3.13-r0)
(29/62) Installing php7-fileinfo (7.3.13-r0)
(30/62) Installing libxau (1.0.9-r0)
(31/62) Installing libbsd (0.9.1-r0)
(32/62) Installing libxdmcp (1.1.3-r0)
(33/62) Installing libxcb (1.13.1-r0)
(34/62) Installing libx11 (1.6.8-r1)
(35/62) Installing libxext (1.3.4-r0)
(36/62) Installing libice (1.0.9-r3)
(37/62) Installing libsm (1.2.3-r0)
(38/62) Installing libxt (1.1.5-r2)
(39/62) Installing libxpm (3.5.12-r0)
(40/62) Installing libbz2 (1.0.6-r7)
(41/62) Installing libpng (1.6.37-r1)
(42/62) Installing freetype (2.10.0-r0)
(43/62) Installing libjpeg-turbo (2.0.4-r0)
(44/62) Installing libwebp (1.0.2-r0)
(45/62) Installing php7-gd (7.3.13-r0)
(46/62) Installing libintl (0.19.8.1-r4)
(47/62) Installing php7-gettext (7.3.13-r0)
(48/62) Installing php7-json (7.3.13-r0)
(49/62) Installing db (5.3.28-r1)
(50/62) Installing libsasl (2.1.27-r4)
(51/62) Installing libldap (2.4.48-r0)
(52/62) Installing php7-ldap (7.3.13-r0)
(53/62) Installing php7-mbstring (7.3.13-r0)
(54/62) Installing php7-openssl (7.3.13-r0)
(55/62) Installing php7-mysqlnd (7.3.13-r0)
(56/62) Installing php7-mysqli (7.3.13-r0)
(57/62) Installing php7-session (7.3.13-r0)
(58/62) Installing php7-simplexml (7.3.13-r0)
(59/62) Installing php7-sockets (7.3.13-r0)
(60/62) Installing php7-dom (7.3.13-r0)
(61/62) Installing php7-xmlreader (7.3.13-r0)
(62/62) Installing php7-xmlwriter (7.3.13-r0)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 77 MiB in 76 packages
+ apk add --clean-protected --no-cache --no-scripts apache2-ssl
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/2) Installing openssl (1.1.1d-r2)
(2/2) Installing apache2-ssl (2.4.41-r0)
OK: 78 MiB in 78 packages
+ rm -f /etc/apache2/conf.d/default.conf
+ rm -f /etc/apache2/conf.d/ssl.conf
+ sed -ri -e 's!^(\s*CustomLog)\s+\S+!\1 /proc/self/fd/1!g' -e 's!^(\s*ErrorLog)\s+\S+!\1 /proc/self/fd/2!g' /etc/apache2/httpd.conf
+ sed -ri -e 's!^(\s*PidFile)\s+\S+!\1 "/var/run/httpd.pid"!g' /etc/apache2/conf.d/mpm.conf
+ rm -f /var/run/apache2/apache2.pid
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 1d7453cef80f
 ---> 86e3e89ad762
Step 5/20 : ARG MAJOR_VERSION=4.4
 ---> Running in 430ed2a3a4f0
Removing intermediate container 430ed2a3a4f0
 ---> bfe83df02640
Step 6/20 : ARG ZBX_VERSION=${MAJOR_VERSION}.4
 ---> Running in 3502cbad974e
Removing intermediate container 3502cbad974e
 ---> 098b21fbb172
Step 7/20 : ARG ZBX_SOURCES=https://git.zabbix.com/scm/zbx/zabbix.git
 ---> Running in 541e759be6dc
Removing intermediate container 541e759be6dc
 ---> 76ae14a34acc
Step 8/20 : ENV TERM=xterm ZBX_VERSION=${ZBX_VERSION} ZBX_SOURCES=${ZBX_SOURCES}
 ---> Running in bab6a5b850db
Removing intermediate container bab6a5b850db
 ---> ce8da6509be2
Step 9/20 : LABEL org.opencontainers.image.documentation="https://www.zabbix.com/documentation/${MAJOR_VERSION}/manual/installation/containers"       org.opencontainers.image.version="${ZBX_VERSION}"       org.opencontainers.image.source="${ZBX_SOURCES}"
 ---> Running in 86b7dc679c13
Removing intermediate container 86b7dc679c13
 ---> 764241b9f34f
Step 10/20 : RUN set -eux &&     apk add --no-cache --virtual build-dependencies             gettext             git &&     cd /usr/share/ &&     git clone ${ZBX_SOURCES} --branch ${ZBX_VERSION} --depth 1 --single-branch zabbix-${ZBX_VERSION} &&     mkdir /usr/share/zabbix/ &&     cp -R /usr/share/zabbix-${ZBX_VERSION}/frontends/php/* /usr/share/zabbix/ &&     rm -rf /usr/share/zabbix-${ZBX_VERSION}/ &&     cd /usr/share/zabbix/ &&     rm -f conf/zabbix.conf.php &&     rm -rf tests &&     ./locale/make_mo.sh &&     ln -s "/etc/zabbix/web/zabbix.conf.php" "/usr/share/zabbix/conf/zabbix.conf.php" &&     apk del --purge --no-network             build-dependencies &&     rm -rf /var/cache/apk/*
 ---> Running in 4b8c3969b60e
+ apk add --no-cache --virtual build-dependencies gettext git
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/5) Installing libgomp (8.3.0-r0)
(2/5) Installing libunistring (0.9.10-r0)
(3/5) Installing gettext (0.19.8.1-r4)
(4/5) Installing git (2.22.2-r0)
(5/5) Installing build-dependencies (20200116.013732)
Executing busybox-1.30.1-r2.trigger
OK: 95 MiB in 83 packages
+ cd /usr/share/
+ git clone https://git.zabbix.com/scm/zbx/zabbix.git --branch 4.4.4 --depth 1 --single-branch zabbix-4.4.4
Cloning into 'zabbix-4.4.4'...
Note: checking out '3131fdac04eb1ce833315164258c00a6c565372e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

+ mkdir /usr/share/zabbix/
+ cp -R /usr/share/zabbix-4.4.4/frontends/php/actionconf.php /usr/share/zabbix-4.4.4/frontends/php/adm.gui.php /usr/share/zabbix-4.4.4/frontends/php/adm.housekeeper.php /usr/share/zabbix-4.4.4/frontends/php/adm.iconmapping.php /usr/share/zabbix-4.4.4/frontends/php/adm.images.php /usr/share/zabbix-4.4.4/frontends/php/adm.macros.php /usr/share/zabbix-4.4.4/frontends/php/adm.other.php /usr/share/zabbix-4.4.4/frontends/php/adm.regexps.php /usr/share/zabbix-4.4.4/frontends/php/adm.triggerdisplayoptions.php /usr/share/zabbix-4.4.4/frontends/php/adm.triggerseverities.php /usr/share/zabbix-4.4.4/frontends/php/adm.valuemapping.php /usr/share/zabbix-4.4.4/frontends/php/adm.workingtime.php /usr/share/zabbix-4.4.4/frontends/php/api_jsonrpc.php /usr/share/zabbix-4.4.4/frontends/php/app /usr/share/zabbix-4.4.4/frontends/php/applications.php /usr/share/zabbix-4.4.4/frontends/php/assets /usr/share/zabbix-4.4.4/frontends/php/audio /usr/share/zabbix-4.4.4/frontends/php/auditacts.php /usr/share/zabbix-4.4.4/frontends/php/auditlogs.php /usr/share/zabbix-4.4.4/frontends/php/browserwarning.php /usr/share/zabbix-4.4.4/frontends/php/chart.php /usr/share/zabbix-4.4.4/frontends/php/chart2.php /usr/share/zabbix-4.4.4/frontends/php/chart3.php /usr/share/zabbix-4.4.4/frontends/php/chart4.php /usr/share/zabbix-4.4.4/frontends/php/chart5.php /usr/share/zabbix-4.4.4/frontends/php/chart6.php /usr/share/zabbix-4.4.4/frontends/php/chart7.php /usr/share/zabbix-4.4.4/frontends/php/charts.php /usr/share/zabbix-4.4.4/frontends/php/conf /usr/share/zabbix-4.4.4/frontends/php/conf.import.php /usr/share/zabbix-4.4.4/frontends/php/correlation.php /usr/share/zabbix-4.4.4/frontends/php/disc_prototypes.php /usr/share/zabbix-4.4.4/frontends/php/discoveryconf.php /usr/share/zabbix-4.4.4/frontends/php/favicon.ico /usr/share/zabbix-4.4.4/frontends/php/graphs.php /usr/share/zabbix-4.4.4/frontends/php/history.php /usr/share/zabbix-4.4.4/frontends/php/host_discovery.php /usr/share/zabbix-4.4.4/frontends/php/host_prototypes.php /usr/share/zabbix-4.4.4/frontends/php/host_screen.php /usr/share/zabbix-4.4.4/frontends/php/hostgroups.php /usr/share/zabbix-4.4.4/frontends/php/hostinventories.php /usr/share/zabbix-4.4.4/frontends/php/hostinventoriesoverview.php /usr/share/zabbix-4.4.4/frontends/php/hosts.php /usr/share/zabbix-4.4.4/frontends/php/httpconf.php /usr/share/zabbix-4.4.4/frontends/php/httpdetails.php /usr/share/zabbix-4.4.4/frontends/php/image.php /usr/share/zabbix-4.4.4/frontends/php/imgstore.php /usr/share/zabbix-4.4.4/frontends/php/include /usr/share/zabbix-4.4.4/frontends/php/index.php /usr/share/zabbix-4.4.4/frontends/php/index_http.php /usr/share/zabbix-4.4.4/frontends/php/items.php /usr/share/zabbix-4.4.4/frontends/php/js /usr/share/zabbix-4.4.4/frontends/php/jsLoader.php /usr/share/zabbix-4.4.4/frontends/php/jsrpc.php /usr/share/zabbix-4.4.4/frontends/php/latest.php /usr/share/zabbix-4.4.4/frontends/php/local /usr/share/zabbix-4.4.4/frontends/php/locale /usr/share/zabbix-4.4.4/frontends/php/maintenance.php /usr/share/zabbix-4.4.4/frontends/php/map.import.php /usr/share/zabbix-4.4.4/frontends/php/map.php /usr/share/zabbix-4.4.4/frontends/php/overview.php /usr/share/zabbix-4.4.4/frontends/php/queue.php /usr/share/zabbix-4.4.4/frontends/php/report2.php /usr/share/zabbix-4.4.4/frontends/php/report4.php /usr/share/zabbix-4.4.4/frontends/php/robots.txt /usr/share/zabbix-4.4.4/frontends/php/screen.import.php /usr/share/zabbix-4.4.4/frontends/php/screenconf.php /usr/share/zabbix-4.4.4/frontends/php/screenedit.php /usr/share/zabbix-4.4.4/frontends/php/screens.php /usr/share/zabbix-4.4.4/frontends/php/services.php /usr/share/zabbix-4.4.4/frontends/php/setup.php /usr/share/zabbix-4.4.4/frontends/php/slideconf.php /usr/share/zabbix-4.4.4/frontends/php/slides.php /usr/share/zabbix-4.4.4/frontends/php/srv_status.php /usr/share/zabbix-4.4.4/frontends/php/sysmap.php /usr/share/zabbix-4.4.4/frontends/php/sysmaps.php /usr/share/zabbix-4.4.4/frontends/php/templates.php /usr/share/zabbix-4.4.4/frontends/php/tests /usr/share/zabbix-4.4.4/frontends/php/toptriggers.php /usr/share/zabbix-4.4.4/frontends/php/tr_events.php /usr/share/zabbix-4.4.4/frontends/php/trigger_prototypes.php /usr/share/zabbix-4.4.4/frontends/php/triggers.php /usr/share/zabbix-4.4.4/frontends/php/usergrps.php /usr/share/zabbix-4.4.4/frontends/php/zabbix.php /usr/share/zabbix/
+ rm -rf /usr/share/zabbix-4.4.4/
+ cd /usr/share/zabbix/
+ rm -f conf/zabbix.conf.php
+ rm -rf tests
+ ./locale/make_mo.sh
+ ln -s /etc/zabbix/web/zabbix.conf.php /usr/share/zabbix/conf/zabbix.conf.php
+ apk del --purge --no-network build-dependencies
WARNING: Ignoring APKINDEX.00740ba1.tar.gz: No such file or directory
WARNING: Ignoring APKINDEX.d8b2a6f4.tar.gz: No such file or directory
(1/5) Purging build-dependencies (20200116.013732)
(2/5) Purging gettext (0.19.8.1-r4)
(3/5) Purging git (2.22.2-r0)
(4/5) Purging libgomp (8.3.0-r0)
(5/5) Purging libunistring (0.9.10-r0)
Executing busybox-1.30.1-r2.trigger
OK: 78 MiB in 78 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 4b8c3969b60e
 ---> 0b36ec318419
Step 11/20 : EXPOSE 80/TCP 443/TCP
 ---> Running in f81110165b6b
Removing intermediate container f81110165b6b
 ---> 0da224aece8c
Step 12/20 : WORKDIR /usr/share/zabbix
 ---> Running in 772d0299172b
Removing intermediate container 772d0299172b
 ---> c38c47bd97c9
Step 13/20 : VOLUME ["/etc/ssl/apache2"]
 ---> Running in 88097a34c7b4
Removing intermediate container 88097a34c7b4
 ---> 799e8e2fba43
Step 14/20 : COPY ["conf/etc/zabbix/apache.conf", "/etc/zabbix/"]
 ---> baddb0233d9b
Step 15/20 : COPY ["conf/etc/zabbix/apache_ssl.conf", "/etc/zabbix/"]
 ---> 291e5200eb34
Step 16/20 : COPY ["conf/etc/zabbix/web/zabbix.conf.php", "/etc/zabbix/web/"]
 ---> 395557549b8f
Step 17/20 : COPY ["conf/etc/php7/conf.d/99-zabbix.ini", "/etc/php7/conf.d/"]
 ---> 496260a364d4
Step 18/20 : COPY ["docker-entrypoint.sh", "/usr/bin/"]
 ---> 299a5a118b94
Step 19/20 : ENTRYPOINT ["docker-entrypoint.sh"]
 ---> Running in 91d5b98eb1bb
Removing intermediate container 91d5b98eb1bb
 ---> dc531e5b29c5
Step 20/20 : CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
 ---> Running in 408155d43a53
Removing intermediate container 408155d43a53
 ---> 6a47039037ad

Successfully built 6a47039037ad
Successfully tagged zabbix-web-apache-mysql:alpine-local
Building zabbix-proxy-mysql
Step 1/18 : FROM alpine:3.10
 ---> 965ea09ff2eb
Step 2/18 : LABEL org.opencontainers.image.title="Zabbix proxy (MySQL)"       org.opencontainers.image.authors="Alexey Pustovalov <alexey.pustovalov@zabbix.com>"       org.opencontainers.image.vendor="Zabbix LLC"       org.opencontainers.image.url="https://zabbix.com/"       org.opencontainers.image.description="Zabbix proxy with MySQL database support"       org.opencontainers.image.licenses="GPL v2.0"
 ---> Running in 0b90d9444858
Removing intermediate container 0b90d9444858
 ---> 6bacb329cc7d
Step 3/18 : STOPSIGNAL SIGTERM
 ---> Running in 98d9968aa489
Removing intermediate container 98d9968aa489
 ---> 2d808fd65929
Step 4/18 : RUN set -eux &&     addgroup -S -g 1000 zabbix &&     adduser -S             -D -G zabbix             -u 999             -h /var/lib/zabbix/         zabbix &&     mkdir -p /etc/zabbix &&     mkdir -p /var/lib/zabbix &&     mkdir -p /var/lib/zabbix/enc &&     mkdir -p /usr/lib/zabbix/externalscripts &&     mkdir -p /var/lib/zabbix/mibs &&     mkdir -p /var/lib/zabbix/modules &&     mkdir -p /var/lib/zabbix/snmptraps &&     mkdir -p /var/lib/zabbix/ssh_keys &&     mkdir -p /var/lib/zabbix/ssl &&     mkdir -p /var/lib/zabbix/ssl/certs &&     mkdir -p /var/lib/zabbix/ssl/keys &&     mkdir -p /var/lib/zabbix/ssl/ssl_ca &&     chown --quiet -R zabbix:root /var/lib/zabbix &&     mkdir -p /usr/share/doc/zabbix-proxy-mysql &&     apk add --clean-protected --no-cache             tini             bash             iputils             libcurl             libevent             libldap             libssh2             libxml2             mariadb-client             mariadb-connector-c             net-snmp-agent-libs             openipmi-libs             pcre             unixodbc             fping &&     rm -rf /var/cache/apk/*
 ---> Running in 1269bb8cd328
+ addgroup -S -g 1000 zabbix
+ adduser -S -D -G zabbix -u 999 -h /var/lib/zabbix/ zabbix
+ mkdir -p /etc/zabbix
+ mkdir -p /var/lib/zabbix
+ mkdir -p /var/lib/zabbix/enc
+ mkdir -p /usr/lib/zabbix/externalscripts
+ mkdir -p /var/lib/zabbix/mibs
+ mkdir -p /var/lib/zabbix/modules
+ mkdir -p /var/lib/zabbix/snmptraps
+ mkdir -p /var/lib/zabbix/ssh_keys
+ mkdir -p /var/lib/zabbix/ssl
+ mkdir -p /var/lib/zabbix/ssl/certs
+ mkdir -p /var/lib/zabbix/ssl/keys
+ mkdir -p /var/lib/zabbix/ssl/ssl_ca
+ chown --quiet -R zabbix:root /var/lib/zabbix
+ mkdir -p /usr/share/doc/zabbix-proxy-mysql
+ apk add --clean-protected --no-cache tini bash iputils libcurl libevent libldap libssh2 libxml2 mariadb-client mariadb-connector-c net-snmp-agent-libs openipmi-libs pcre unixodbc fping
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/34) Installing ncurses-terminfo-base (6.1_p20190518-r0)
(2/34) Installing ncurses-terminfo (6.1_p20190518-r0)
(3/34) Installing ncurses-libs (6.1_p20190518-r0)
(4/34) Installing readline (8.0.0-r0)
(5/34) Installing bash (5.0.0-r0)
Executing bash-5.0.0-r0.post-install
(6/34) Installing fping (4.2-r0)
(7/34) Installing libcap (2.27-r0)
(8/34) Installing iputils (20180629-r1)
(9/34) Installing ca-certificates (20190108-r0)
(10/34) Installing nghttp2-libs (1.39.2-r0)
(11/34) Installing libcurl (7.66.0-r0)
(12/34) Installing libevent (2.1.10-r0)
(13/34) Installing db (5.3.28-r1)
(14/34) Installing libsasl (2.1.27-r4)
(15/34) Installing libldap (2.4.48-r0)
(16/34) Installing libssh2 (1.9.0-r1)
(17/34) Installing libxml2 (2.9.9-r3)
(18/34) Installing mariadb-common (10.3.20-r0)
(19/34) Installing libgcc (8.3.0-r0)
(20/34) Installing libstdc++ (8.3.0-r0)
(21/34) Installing mariadb-client (10.3.20-r0)
(22/34) Installing mariadb-connector-c (3.0.10-r0)
(23/34) Installing net-snmp-libs (5.8-r2)
(24/34) Installing net-snmp-agent-libs (5.8-r2)
(25/34) Installing libffi (3.2.1-r6)
(26/34) Installing libintl (0.19.8.1-r4)
(27/34) Installing libuuid (2.33.2-r0)
(28/34) Installing libblkid (2.33.2-r0)
(29/34) Installing libmount (2.33.2-r0)
(30/34) Installing pcre (8.43-r0)
(31/34) Installing glib (2.60.4-r0)
(32/34) Installing openipmi-libs (2.0.25-r1)
(33/34) Installing tini (0.18.0-r0)
(34/34) Installing unixodbc (2.3.7-r1)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 63 MiB in 48 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 1269bb8cd328
 ---> d4ed5229f6ce
Step 5/18 : ARG MAJOR_VERSION=4.4
 ---> Running in 766e03fa0924
Removing intermediate container 766e03fa0924
 ---> a4d70e531d0f
Step 6/18 : ARG ZBX_VERSION=${MAJOR_VERSION}.4
 ---> Running in 8ff21d4a58e5
Removing intermediate container 8ff21d4a58e5
 ---> 95449e4a7745
Step 7/18 : ARG ZBX_SOURCES=https://git.zabbix.com/scm/zbx/zabbix.git
 ---> Running in c2c8d98083b3
Removing intermediate container c2c8d98083b3
 ---> ca411bb21a97
Step 8/18 : ENV TERM=xterm ZBX_VERSION=${ZBX_VERSION} ZBX_SOURCES=${ZBX_SOURCES}     MIBDIRS=/usr/share/snmp/mibs:/var/lib/zabbix/mibs MIBS=+ALL
 ---> Running in f88a83063620
Removing intermediate container f88a83063620
 ---> 0ec28ef43bcf
Step 9/18 : LABEL org.opencontainers.image.documentation="https://www.zabbix.com/documentation/${MAJOR_VERSION}/manual/installation/containers"       org.opencontainers.image.version="${ZBX_VERSION}"       org.opencontainers.image.source="${ZBX_SOURCES}"
 ---> Running in e24d142be2ba
Removing intermediate container e24d142be2ba
 ---> 21c1df66c6f3
Step 10/18 : RUN set -eux &&     apk add --no-cache --virtual build-dependencies             autoconf             automake             coreutils             curl-dev             libevent-dev             g++             git             make             libssh2-dev             libxml2-dev             mysql-dev             net-snmp-dev             openipmi-dev             openldap-dev             pcre-dev             unixodbc-dev &&     cd /tmp/ &&     git clone ${ZBX_SOURCES} --branch ${ZBX_VERSION} --depth 1 --single-branch zabbix-${ZBX_VERSION} &&     cd /tmp/zabbix-${ZBX_VERSION} &&     zabbix_revision=`git rev-parse --short HEAD` &&     sed -i "s/{ZABBIX_REVISION}/$zabbix_revision/g" include/version.h &&     ./bootstrap.sh &&     export CFLAGS="-fPIC -pie -Wl,-z,relro -Wl,-z,now" &&     ./configure             --datadir=/usr/lib             --libdir=/usr/lib/zabbix             --sysconfdir=/etc/zabbix             --prefix=/usr             --enable-agent             --enable-proxy             --with-mysql             --with-ldap             --with-libcurl             --with-libxml2             --with-net-snmp             --with-openipmi             --with-openssl             --with-ssh2             --with-unixodbc             --enable-ipv6             --silent &&     make -j"$(nproc)" -s dbschema &&     make -j"$(nproc)" -s &&     cp src/zabbix_proxy/zabbix_proxy /usr/sbin/zabbix_proxy &&     cp src/zabbix_get/zabbix_get /usr/bin/zabbix_get &&     cp src/zabbix_sender/zabbix_sender /usr/bin/zabbix_sender &&     cp conf/zabbix_proxy.conf /etc/zabbix/zabbix_proxy.conf &&     chown --quiet -R zabbix:root /etc/zabbix &&     cat database/mysql/schema.sql > database/mysql/create.sql &&     gzip database/mysql/create.sql &&     cp database/mysql/create.sql.gz /usr/share/doc/zabbix-proxy-mysql/ &&     cd /tmp/ &&     rm -rf /tmp/zabbix-${ZBX_VERSION}/ &&     apk del --purge --no-network             build-dependencies &&     rm -rf /var/cache/apk/*
 ---> Running in 399d3c371eba
+ apk add --no-cache --virtual build-dependencies autoconf automake coreutils curl-dev libevent-dev g++ git make libssh2-dev libxml2-dev mysql-dev net-snmp-dev openipmi-dev openldap-dev pcre-dev unixodbc-dev
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/60) Upgrading libcrypto1.1 (1.1.1d-r0 -> 1.1.1d-r2)
(2/60) Upgrading libssl1.1 (1.1.1d-r0 -> 1.1.1d-r2)
(3/60) Installing m4 (1.4.18-r1)
(4/60) Installing libbz2 (1.0.6-r7)
(5/60) Installing perl (5.28.2-r1)
(6/60) Installing autoconf (2.69-r2)
(7/60) Installing automake (1.16.1-r0)
(8/60) Installing libacl (2.2.52-r6)
(9/60) Installing libattr (2.4.48-r0)
(10/60) Installing coreutils (8.31-r0)
(11/60) Installing pkgconf (1.6.1-r1)
(12/60) Installing openssl-dev (1.1.1d-r2)
(13/60) Installing nghttp2-dev (1.39.2-r0)
(14/60) Installing zlib-dev (1.2.11-r1)
(15/60) Installing curl-dev (7.66.0-r0)
(16/60) Installing expat (2.2.8-r0)
(17/60) Installing gdbm (1.13-r1)
(18/60) Installing sqlite-libs (3.28.0-r2)
(19/60) Installing python2 (2.7.16-r2)
(20/60) Installing libevent-dev (2.1.10-r0)
(21/60) Installing binutils (2.32-r0)
(22/60) Installing gmp (6.1.2-r1)
(23/60) Installing isl (0.18-r0)
(24/60) Installing libgomp (8.3.0-r0)
(25/60) Installing libatomic (8.3.0-r0)
(26/60) Installing mpfr3 (3.1.5-r1)
(27/60) Installing mpc1 (1.1.0-r0)
(28/60) Installing gcc (8.3.0-r0)
(29/60) Installing musl-dev (1.1.22-r3)
(30/60) Installing libc-dev (0.7.1-r0)
(31/60) Installing g++ (8.3.0-r0)
(32/60) Installing pcre2 (10.33-r0)
(33/60) Installing git (2.22.2-r0)
(34/60) Installing perl-error (0.17027-r0)
(35/60) Installing perl-git (2.22.2-r0)
(36/60) Installing git-perl (2.22.2-r0)
(37/60) Installing make (4.2.1-r2)
(38/60) Installing libssh2-dev (1.9.0-r1)
(39/60) Installing libxml2-dev (2.9.9-r3)
(40/60) Installing mariadb-connector-c-dev (3.0.10-r0)
(41/60) Installing libaio (0.3.111-r0)
(42/60) Installing xz-libs (5.2.4-r0)
(43/60) Installing mariadb-embedded (10.3.20-r0)
(44/60) Installing mariadb-dev (10.3.20-r0)
(45/60) Installing net-snmp-dev (5.8-r2)
(46/60) Installing popt (1.16-r7)
(47/60) Installing openipmi-lanserv (2.0.25-r1)
(48/60) Installing ncurses-dev (6.1_p20190518-r0)
(49/60) Installing openipmi-dev (2.0.25-r1)
(50/60) Installing cyrus-sasl-dev (2.1.27-r4)
(51/60) Installing libfdisk (2.33.2-r0)
(52/60) Installing libsmartcols (2.33.2-r0)
(53/60) Installing util-linux-dev (2.33.2-r0)
(54/60) Installing openldap-dev (2.4.48-r0)
(55/60) Installing libpcre16 (8.43-r0)
(56/60) Installing libpcre32 (8.43-r0)
(57/60) Installing libpcrecpp (8.43-r0)
(58/60) Installing pcre-dev (8.43-r0)
(59/60) Installing unixodbc-dev (2.3.7-r1)
(60/60) Installing build-dependencies (20200116.013747)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 377 MiB in 106 packages
+ cd /tmp/
+ git clone https://git.zabbix.com/scm/zbx/zabbix.git --branch 4.4.4 --depth 1 --single-branch zabbix-4.4.4
Cloning into 'zabbix-4.4.4'...
Note: checking out '3131fdac04eb1ce833315164258c00a6c565372e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

+ cd /tmp/zabbix-4.4.4
+ git rev-parse --short HEAD
+ zabbix_revision=3131fda
+ sed -i 's/{ZABBIX_REVISION}/3131fda/g' include/version.h
+ ./bootstrap.sh
configure.ac:40: installing './compile'
configure.ac:32: installing './config.guess'
configure.ac:32: installing './config.sub'
configure.ac:24: installing './install-sh'
configure.ac:24: installing './missing'
src/libs/zbxalgo/Makefile.am: installing './depcomp'
+ export 'CFLAGS=-fPIC -pie -Wl,-z,relro -Wl,-z,now'
+ ./configure '--datadir=/usr/lib' '--libdir=/usr/lib/zabbix' '--sysconfdir=/etc/zabbix' '--prefix=/usr' --enable-agent --enable-proxy --with-mysql --with-ldap --with-libcurl --with-libxml2 --with-net-snmp --with-openipmi --with-openssl --with-ssh2 --with-unixodbc --enable-ipv6 --silent


Configuration:

  Detected OS:           linux-gnu
  Install path:          /usr
  Compilation arch:      linux

  Compiler:              cc
  Compiler flags:         -fPIC -pie -Wl,-z,relro -Wl,-z,now 

  Library-specific flags:
    database:               -I/usr/include/mysql -I/usr/include/mysql   
    libXML2:               -I/usr/include/libxml2
    unixODBC:              -I/usr/include
    Net-SNMP:               -I. -I/usr/include
    OpenIPMI:              -I/usr/include
    libssh2:               -I/usr/include
    TLS:                   -I/usr/include
    LDAP:                  -I/usr/include

  Enable server:         no

  Enable proxy:          yes
  Proxy details:
    With database:         MySQL
    WEB Monitoring:        cURL
      SSL certificates:      /usr/lib/zabbix/ssl/certs
      SSL keys:              /usr/lib/zabbix/ssl/keys
    SNMP:                  yes
    IPMI:                  yes
    SSH:                   yes
    TLS:                   OpenSSL
    ODBC:                  yes
    Linker flags:             -L/usr/lib/     -L/lib -L/usr/lib  -L/usr/lib -L/usr/lib -L/usr/lib    -L/usr/lib -L/usr/lib    
    Libraries:               -lmariadb  -lz -lssl -lcrypto    -lxml2  -lodbc  -lnetsnmp -lssh2 -lOpenIPMI -lOpenIPMIposix -lz -lpthread -levent -lssl -lcrypto -lldap -llber   -lcurl -lnghttp2 -lssl -lcrypto -lssl -lcrypto -lz -lm   -lpcre 
    Configuration file:    /etc/zabbix/zabbix_proxy.conf
    External scripts:      /usr/lib/zabbix/externalscripts
    Modules:               /usr/lib/zabbix/modules

  Enable agent:          yes
  Agent details:
    TLS:                   OpenSSL
    Linker flags:             -L/usr/lib -L/usr/lib    
    Libraries:              -lz -lpthread -lssl -lcrypto -lldap -llber   -lcurl -lnghttp2 -lssl -lcrypto -lssl -lcrypto -lz -lm   -lpcre 
    Configuration file:    /etc/zabbix/zabbix_agentd.conf
    Modules:               /usr/lib/zabbix/modules

  Enable agent 2:        no

  Enable Java gateway:   no

  LDAP support:          yes
  IPv6 support:          yes

***********************************************************
*            Now run 'make install'                       *
*                                                         *
*            Thank you for using Zabbix!                  *
*              <http://www.zabbix.com>                    *
***********************************************************

+ nproc
+ make -j4 -s dbschema
+ nproc
+ make -j4 -s
Making all in src
Making all in libs
Making all in zbxcrypto
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcommon
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxlog
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxalgo
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxnix
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxconf
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxhttp
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxsysinfo
Making all in agent
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in common
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in simple
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in linux
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxsys
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcomms
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxjson
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxexec
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxmodules
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxregexp
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxipcservice
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcompress
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcommshigh
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdb
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdbupgrade
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdbcache
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdbhigh
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxhttp
Making all in zbxmemory
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxserver
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxicmpping
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxself
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxtasks
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxhistory
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcompress
Making all in zbxembed
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxprometheus
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_agent
Making all in logfiles
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_get
Making all in zabbix_sender
Making all in zabbix_server/dbsyncer
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/dbconfig
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/discoverer
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/httppoller
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/pinger
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/poller
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/trapper
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/selfmon
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/snmptrapper
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/vmware
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/ipmi
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/odbc
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/scripts
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/preprocessor
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_proxy
Making all in heart
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in housekeeper
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in proxyconfig
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in datasender
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in taskmanager
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in database
Making all in ibm_db2
Making all in mysql
Making all in oracle
Making all in postgresql
Making all in sqlite3
Making all in man
Making all in misc
+ cp src/zabbix_proxy/zabbix_proxy /usr/sbin/zabbix_proxy
+ cp src/zabbix_get/zabbix_get /usr/bin/zabbix_get
+ cp src/zabbix_sender/zabbix_sender /usr/bin/zabbix_sender
+ cp conf/zabbix_proxy.conf /etc/zabbix/zabbix_proxy.conf
+ chown --quiet -R zabbix:root /etc/zabbix
+ cat database/mysql/schema.sql
+ gzip database/mysql/create.sql
+ cp database/mysql/create.sql.gz /usr/share/doc/zabbix-proxy-mysql/
+ cd /tmp/
+ rm -rf /tmp/zabbix-4.4.4/
+ apk del --purge --no-network build-dependencies
WARNING: Ignoring APKINDEX.00740ba1.tar.gz: No such file or directory
WARNING: Ignoring APKINDEX.d8b2a6f4.tar.gz: No such file or directory
(1/58) Purging git-perl (2.22.2-r0)
(2/58) Purging perl-git (2.22.2-r0)
(3/58) Purging perl-error (0.17027-r0)
(4/58) Purging build-dependencies (20200116.013747)
(5/58) Purging autoconf (2.69-r2)
(6/58) Purging m4 (1.4.18-r1)
(7/58) Purging automake (1.16.1-r0)
(8/58) Purging perl (5.28.2-r1)
(9/58) Purging coreutils (8.31-r0)
Executing coreutils-8.31-r0.post-deinstall
(10/58) Purging curl-dev (7.66.0-r0)
(11/58) Purging nghttp2-dev (1.39.2-r0)
(12/58) Purging libevent-dev (2.1.10-r0)
(13/58) Purging python2 (2.7.16-r2)
(14/58) Purging g++ (8.3.0-r0)
(15/58) Purging gcc (8.3.0-r0)
(16/58) Purging binutils (2.32-r0)
(17/58) Purging libatomic (8.3.0-r0)
(18/58) Purging libgomp (8.3.0-r0)
(19/58) Purging libc-dev (0.7.1-r0)
(20/58) Purging musl-dev (1.1.22-r3)
(21/58) Purging git (2.22.2-r0)
(22/58) Purging make (4.2.1-r2)
(23/58) Purging libssh2-dev (1.9.0-r1)
(24/58) Purging libxml2-dev (2.9.9-r3)
(25/58) Purging net-snmp-dev (5.8-r2)
(26/58) Purging openipmi-dev (2.0.25-r1)
(27/58) Purging openipmi-lanserv (2.0.25-r1)
(28/58) Purging openldap-dev (2.4.48-r0)
(29/58) Purging cyrus-sasl-dev (2.1.27-r4)
(30/58) Purging util-linux-dev (2.33.2-r0)
(31/58) Purging libfdisk (2.33.2-r0)
(32/58) Purging libsmartcols (2.33.2-r0)
(33/58) Purging pcre-dev (8.43-r0)
(34/58) Purging libpcre16 (8.43-r0)
(35/58) Purging libpcre32 (8.43-r0)
(36/58) Purging libpcrecpp (8.43-r0)
(37/58) Purging unixodbc-dev (2.3.7-r1)
(38/58) Purging libbz2 (1.0.6-r7)
(39/58) Purging libacl (2.2.52-r6)
(40/58) Purging libattr (2.4.48-r0)
(41/58) Purging mariadb-dev (10.3.20-r0)
(42/58) Purging mariadb-embedded (10.3.20-r0)
(43/58) Purging mariadb-connector-c-dev (3.0.10-r0)
(44/58) Purging zlib-dev (1.2.11-r1)
(45/58) Purging openssl-dev (1.1.1d-r2)
(46/58) Purging ncurses-dev (6.1_p20190518-r0)
(47/58) Purging pkgconf (1.6.1-r1)
(48/58) Purging expat (2.2.8-r0)
(49/58) Purging gdbm (1.13-r1)
(50/58) Purging sqlite-libs (3.28.0-r2)
(51/58) Purging mpc1 (1.1.0-r0)
(52/58) Purging mpfr3 (3.1.5-r1)
(53/58) Purging isl (0.18-r0)
(54/58) Purging gmp (6.1.2-r1)
(55/58) Purging pcre2 (10.33-r0)
(56/58) Purging libaio (0.3.111-r0)
(57/58) Purging xz-libs (5.2.4-r0)
(58/58) Purging popt (1.16-r7)
Executing busybox-1.30.1-r2.trigger
OK: 63 MiB in 48 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 399d3c371eba
 ---> 031e9f699b3b
Step 11/18 : EXPOSE 10051/TCP
 ---> Running in 6f8134bfdf84
Removing intermediate container 6f8134bfdf84
 ---> 0415d67369b5
Step 12/18 : WORKDIR /var/lib/zabbix
 ---> Running in 2a8c0ad8b920
Removing intermediate container 2a8c0ad8b920
 ---> 2818ef0bb843
Step 13/18 : VOLUME ["/usr/lib/zabbix/externalscripts", "/var/lib/zabbix/enc", "/var/lib/zabbix/modules", "/var/lib/zabbix/snmptraps"]
 ---> Running in 90215572efa1
Removing intermediate container 90215572efa1
 ---> 3b8a60ade073
Step 14/18 : VOLUME ["/var/lib/zabbix/ssh_keys", "/var/lib/zabbix/ssl/certs", "/var/lib/zabbix/ssl/keys", "/var/lib/zabbix/ssl/ssl_ca"]
 ---> Running in dfd9acc77bd2
Removing intermediate container dfd9acc77bd2
 ---> 7f97b8a1d5cf
Step 15/18 : COPY ["docker-entrypoint.sh", "/usr/bin/"]
 ---> 2210bd9c6ada
Step 16/18 : ENTRYPOINT ["/sbin/tini", "--", "/usr/bin/docker-entrypoint.sh"]
 ---> Running in 5b0fd72d694b
Removing intermediate container 5b0fd72d694b
 ---> 1dee71c893a7
Step 17/18 : USER zabbix
 ---> Running in 0f52151bcbc3
Removing intermediate container 0f52151bcbc3
 ---> 94e6ebd60296
Step 18/18 : CMD ["/usr/sbin/zabbix_proxy", "--foreground", "-c", "/etc/zabbix/zabbix_proxy.conf"]
 ---> Running in 8486f4181837
Removing intermediate container 8486f4181837
 ---> 339255aff93f

Successfully built 339255aff93f
Successfully tagged zabbix-proxy-mysql:alpine-local
Building zabbix-proxy-sqlite3
Step 1/19 : FROM alpine:3.10
 ---> 965ea09ff2eb
Step 2/19 : LABEL org.opencontainers.image.title="Zabbix proxy (SQLite3)"       org.opencontainers.image.authors="Alexey Pustovalov <alexey.pustovalov@zabbix.com>"       org.opencontainers.image.vendor="Zabbix LLC"       org.opencontainers.image.url="https://zabbix.com/"       org.opencontainers.image.description="Zabbix proxy with SQLite3 database support"       org.opencontainers.image.licenses="GPL v2.0"
 ---> Running in 332d57b6b2c3
Removing intermediate container 332d57b6b2c3
 ---> 78d9b523d831
Step 3/19 : STOPSIGNAL SIGTERM
 ---> Running in 45a90f635b83
Removing intermediate container 45a90f635b83
 ---> cc15b56cff34
Step 4/19 : RUN set -eux &&     addgroup -S -g 1000 zabbix &&     adduser -S             -D -G zabbix             -u 999             -h /var/lib/zabbix/         zabbix &&     mkdir -p /etc/zabbix &&     mkdir -p /var/lib/zabbix &&     mkdir -p /var/lib/zabbix/enc &&     mkdir -p /usr/lib/zabbix/externalscripts &&     mkdir -p /var/lib/zabbix/mibs &&     mkdir -p /var/lib/zabbix/modules &&     mkdir -p /var/lib/zabbix/snmptraps &&     mkdir -p /var/lib/zabbix/ssh_keys &&     mkdir -p /var/lib/zabbix/ssl &&     mkdir -p /var/lib/zabbix/ssl/certs &&     mkdir -p /var/lib/zabbix/ssl/keys &&     mkdir -p /var/lib/zabbix/ssl/ssl_ca &&     chown --quiet -R zabbix:root /var/lib/zabbix &&     apk add --clean-protected --no-cache             tini             bash             fping             iputils             libcurl             libevent             libldap             libssh2             libxml2             net-snmp-agent-libs             openipmi-libs             pcre             sqlite-libs             unixodbc &&     rm -rf /var/cache/apk/*
 ---> Running in 33d2ec03902f
+ addgroup -S -g 1000 zabbix
+ adduser -S -D -G zabbix -u 999 -h /var/lib/zabbix/ zabbix
+ mkdir -p /etc/zabbix
+ mkdir -p /var/lib/zabbix
+ mkdir -p /var/lib/zabbix/enc
+ mkdir -p /usr/lib/zabbix/externalscripts
+ mkdir -p /var/lib/zabbix/mibs
+ mkdir -p /var/lib/zabbix/modules
+ mkdir -p /var/lib/zabbix/snmptraps
+ mkdir -p /var/lib/zabbix/ssh_keys
+ mkdir -p /var/lib/zabbix/ssl
+ mkdir -p /var/lib/zabbix/ssl/certs
+ mkdir -p /var/lib/zabbix/ssl/keys
+ mkdir -p /var/lib/zabbix/ssl/ssl_ca
+ chown --quiet -R zabbix:root /var/lib/zabbix
+ apk add --clean-protected --no-cache tini bash fping iputils libcurl libevent libldap libssh2 libxml2 net-snmp-agent-libs openipmi-libs pcre sqlite-libs unixodbc
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/30) Installing ncurses-terminfo-base (6.1_p20190518-r0)
(2/30) Installing ncurses-terminfo (6.1_p20190518-r0)
(3/30) Installing ncurses-libs (6.1_p20190518-r0)
(4/30) Installing readline (8.0.0-r0)
(5/30) Installing bash (5.0.0-r0)
Executing bash-5.0.0-r0.post-install
(6/30) Installing fping (4.2-r0)
(7/30) Installing libcap (2.27-r0)
(8/30) Installing iputils (20180629-r1)
(9/30) Installing ca-certificates (20190108-r0)
(10/30) Installing nghttp2-libs (1.39.2-r0)
(11/30) Installing libcurl (7.66.0-r0)
(12/30) Installing libevent (2.1.10-r0)
(13/30) Installing db (5.3.28-r1)
(14/30) Installing libsasl (2.1.27-r4)
(15/30) Installing libldap (2.4.48-r0)
(16/30) Installing libssh2 (1.9.0-r1)
(17/30) Installing libxml2 (2.9.9-r3)
(18/30) Installing net-snmp-libs (5.8-r2)
(19/30) Installing net-snmp-agent-libs (5.8-r2)
(20/30) Installing libffi (3.2.1-r6)
(21/30) Installing libintl (0.19.8.1-r4)
(22/30) Installing libuuid (2.33.2-r0)
(23/30) Installing libblkid (2.33.2-r0)
(24/30) Installing libmount (2.33.2-r0)
(25/30) Installing pcre (8.43-r0)
(26/30) Installing glib (2.60.4-r0)
(27/30) Installing openipmi-libs (2.0.25-r1)
(28/30) Installing sqlite-libs (3.28.0-r2)
(29/30) Installing tini (0.18.0-r0)
(30/30) Installing unixodbc (2.3.7-r1)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 32 MiB in 44 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 33d2ec03902f
 ---> 4b284acb8eb7
Step 5/19 : ARG MAJOR_VERSION=4.4
 ---> Running in 20d6b033101c
Removing intermediate container 20d6b033101c
 ---> d42865973125
Step 6/19 : ARG ZBX_VERSION=${MAJOR_VERSION}.4
 ---> Running in 91e518a44876
Removing intermediate container 91e518a44876
 ---> 9b3aafa25420
Step 7/19 : ARG ZBX_SOURCES=https://git.zabbix.com/scm/zbx/zabbix.git
 ---> Running in 9b9cbc573b90
Removing intermediate container 9b9cbc573b90
 ---> 216eaae618a4
Step 8/19 : ENV ZBX_VERSION=${ZBX_VERSION} ZBX_SOURCES=${ZBX_SOURCES}
 ---> Running in c9657c394314
Removing intermediate container c9657c394314
 ---> 6a6100457aa7
Step 9/19 : ENV TERM=xterm ZBX_VERSION=${ZBX_VERSION} ZBX_SOURCES=${ZBX_SOURCES}     MIBDIRS=/usr/share/snmp/mibs:/var/lib/zabbix/mibs MIBS=+ALL
 ---> Running in 5c424ca74083
Removing intermediate container 5c424ca74083
 ---> 382eb3c0456a
Step 10/19 : LABEL org.opencontainers.image.documentation="https://www.zabbix.com/documentation/${MAJOR_VERSION}/manual/installation/containers"       org.opencontainers.image.version="${ZBX_VERSION}"       org.opencontainers.image.source="${ZBX_SOURCES}"
 ---> Running in 651a91899eaf
Removing intermediate container 651a91899eaf
 ---> de0f20b5de6d
Step 11/19 : RUN set -eux &&     apk add --no-cache --virtual build-dependencies             autoconf             automake             coreutils             curl-dev             libevent-dev             libssh2-dev             libxml2-dev             net-snmp-dev             openipmi-dev             openldap-dev             pcre-dev             sqlite-dev             git             g++             make             unixodbc-dev &&     cd /tmp/ &&     git clone ${ZBX_SOURCES} --branch ${ZBX_VERSION} --depth 1 --single-branch zabbix-${ZBX_VERSION} &&     cd /tmp/zabbix-${ZBX_VERSION} &&     zabbix_revision=`git rev-parse --short HEAD` &&     sed -i "s/{ZABBIX_REVISION}/$zabbix_revision/g" include/version.h &&     ./bootstrap.sh &&     export CFLAGS="-fPIC -pie -Wl,-z,relro -Wl,-z,now" &&     ./configure             --datadir=/usr/lib             --libdir=/usr/lib/zabbix             --sysconfdir=/etc/zabbix             --prefix=/usr             --enable-agent             --enable-proxy             --with-sqlite3             --with-ldap             --with-libcurl             --with-libxml2             --with-net-snmp             --with-openipmi             --with-openssl             --with-ssh2             --with-unixodbc             --enable-ipv6             --silent &&     make -j"$(nproc)" -s dbschema &&     make -j"$(nproc)" -s &&     cp src/zabbix_proxy/zabbix_proxy /usr/sbin/zabbix_proxy &&     cp src/zabbix_get/zabbix_get /usr/bin/zabbix_get &&     cp src/zabbix_sender/zabbix_sender /usr/bin/zabbix_sender &&     cp conf/zabbix_proxy.conf /etc/zabbix/zabbix_proxy.conf &&     chown --quiet -R zabbix:root /etc/zabbix &&     cd /tmp/ &&     rm -rf /tmp/zabbix-${ZBX_VERSION}/ &&     apk del --purge --no-network             build-dependencies &&     rm -rf /var/cache/apk/*
 ---> Running in 9d45c4933b15
+ apk add --no-cache --virtual build-dependencies autoconf automake coreutils curl-dev libevent-dev libssh2-dev libxml2-dev net-snmp-dev openipmi-dev openldap-dev pcre-dev sqlite-dev git g++ make unixodbc-dev
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.10/community/x86_64/APKINDEX.tar.gz
(1/57) Upgrading libcrypto1.1 (1.1.1d-r0 -> 1.1.1d-r2)
(2/57) Upgrading libssl1.1 (1.1.1d-r0 -> 1.1.1d-r2)
(3/57) Installing m4 (1.4.18-r1)
(4/57) Installing libbz2 (1.0.6-r7)
(5/57) Installing perl (5.28.2-r1)
(6/57) Installing autoconf (2.69-r2)
(7/57) Installing automake (1.16.1-r0)
(8/57) Installing libacl (2.2.52-r6)
(9/57) Installing libattr (2.4.48-r0)
(10/57) Installing coreutils (8.31-r0)
(11/57) Installing pkgconf (1.6.1-r1)
(12/57) Installing openssl-dev (1.1.1d-r2)
(13/57) Installing nghttp2-dev (1.39.2-r0)
(14/57) Installing zlib-dev (1.2.11-r1)
(15/57) Installing curl-dev (7.66.0-r0)
(16/57) Installing expat (2.2.8-r0)
(17/57) Installing gdbm (1.13-r1)
(18/57) Installing python2 (2.7.16-r2)
(19/57) Installing libevent-dev (2.1.10-r0)
(20/57) Installing libssh2-dev (1.9.0-r1)
(21/57) Installing libxml2-dev (2.9.9-r3)
(22/57) Installing net-snmp-dev (5.8-r2)
(23/57) Installing popt (1.16-r7)
(24/57) Installing openipmi-lanserv (2.0.25-r1)
(25/57) Installing ncurses-dev (6.1_p20190518-r0)
(26/57) Installing openipmi-dev (2.0.25-r1)
(27/57) Installing cyrus-sasl-dev (2.1.27-r4)
(28/57) Installing libfdisk (2.33.2-r0)
(29/57) Installing libsmartcols (2.33.2-r0)
(30/57) Installing util-linux-dev (2.33.2-r0)
(31/57) Installing openldap-dev (2.4.48-r0)
(32/57) Installing libpcre16 (8.43-r0)
(33/57) Installing libpcre32 (8.43-r0)
(34/57) Installing libgcc (8.3.0-r0)
(35/57) Installing libstdc++ (8.3.0-r0)
(36/57) Installing libpcrecpp (8.43-r0)
(37/57) Installing pcre-dev (8.43-r0)
(38/57) Installing sqlite-dev (3.28.0-r2)
(39/57) Installing pcre2 (10.33-r0)
(40/57) Installing git (2.22.2-r0)
(41/57) Installing perl-error (0.17027-r0)
(42/57) Installing perl-git (2.22.2-r0)
(43/57) Installing git-perl (2.22.2-r0)
(44/57) Installing binutils (2.32-r0)
(45/57) Installing gmp (6.1.2-r1)
(46/57) Installing isl (0.18-r0)
(47/57) Installing libgomp (8.3.0-r0)
(48/57) Installing libatomic (8.3.0-r0)
(49/57) Installing mpfr3 (3.1.5-r1)
(50/57) Installing mpc1 (1.1.0-r0)
(51/57) Installing gcc (8.3.0-r0)
(52/57) Installing musl-dev (1.1.22-r3)
(53/57) Installing libc-dev (0.7.1-r0)
(54/57) Installing g++ (8.3.0-r0)
(55/57) Installing make (4.2.1-r2)
(56/57) Installing unixodbc-dev (2.3.7-r1)
(57/57) Installing build-dependencies (20200116.013845)
Executing busybox-1.30.1-r2.trigger
Executing ca-certificates-20190108-r0.trigger
OK: 325 MiB in 99 packages
+ cd /tmp/
+ git clone https://git.zabbix.com/scm/zbx/zabbix.git --branch 4.4.4 --depth 1 --single-branch zabbix-4.4.4
Cloning into 'zabbix-4.4.4'...
Note: checking out '3131fdac04eb1ce833315164258c00a6c565372e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

+ cd /tmp/zabbix-4.4.4
+ git rev-parse --short HEAD
+ zabbix_revision=3131fda
+ sed -i 's/{ZABBIX_REVISION}/3131fda/g' include/version.h
+ ./bootstrap.sh
configure.ac:40: installing './compile'
configure.ac:32: installing './config.guess'
configure.ac:32: installing './config.sub'
configure.ac:24: installing './install-sh'
configure.ac:24: installing './missing'
src/libs/zbxalgo/Makefile.am: installing './depcomp'
+ export 'CFLAGS=-fPIC -pie -Wl,-z,relro -Wl,-z,now'
+ ./configure '--datadir=/usr/lib' '--libdir=/usr/lib/zabbix' '--sysconfdir=/etc/zabbix' '--prefix=/usr' --enable-agent --enable-proxy --with-sqlite3 --with-ldap --with-libcurl --with-libxml2 --with-net-snmp --with-openipmi --with-openssl --with-ssh2 --with-unixodbc --enable-ipv6 --silent


Configuration:

  Detected OS:           linux-gnu
  Install path:          /usr
  Compilation arch:      linux

  Compiler:              cc
  Compiler flags:         -fPIC -pie -Wl,-z,relro -Wl,-z,now 

  Library-specific flags:
    database:                  -I/usr/include
    libXML2:               -I/usr/include/libxml2
    unixODBC:              -I/usr/include
    Net-SNMP:               -I. -I/usr/include
    OpenIPMI:              -I/usr/include
    libssh2:               -I/usr/include
    TLS:                   -I/usr/include
    LDAP:                  -I/usr/include

  Enable server:         no

  Enable proxy:          yes
  Proxy details:
    With database:         SQLite v3.x
    WEB Monitoring:        cURL
      SSL certificates:      /usr/lib/zabbix/ssl/certs
      SSL keys:              /usr/lib/zabbix/ssl/keys
    SNMP:                  yes
    IPMI:                  yes
    SSH:                   yes
    TLS:                   OpenSSL
    ODBC:                  yes
    Linker flags:               -L/usr/lib  -L/lib -L/usr/lib  -L/usr/lib -L/usr/lib -L/usr/lib    -L/usr/lib -L/usr/lib    
    Libraries:                  -lsqlite3 -lxml2  -lodbc  -lnetsnmp -lssh2 -lOpenIPMI -lOpenIPMIposix -lz -lpthread -levent -lssl -lcrypto -lldap -llber   -lcurl -lnghttp2 -lssl -lcrypto -lssl -lcrypto -lz -lm   -lpcre 
    Configuration file:    /etc/zabbix/zabbix_proxy.conf
    External scripts:      /usr/lib/zabbix/externalscripts
    Modules:               /usr/lib/zabbix/modules

  Enable agent:          yes
  Agent details:
    TLS:                   OpenSSL
    Linker flags:             -L/usr/lib -L/usr/lib    
    Libraries:              -lz -lpthread -lssl -lcrypto -lldap -llber   -lcurl -lnghttp2 -lssl -lcrypto -lssl -lcrypto -lz -lm   -lpcre 
    Configuration file:    /etc/zabbix/zabbix_agentd.conf
    Modules:               /usr/lib/zabbix/modules

  Enable agent 2:        no

  Enable Java gateway:   no

  LDAP support:          yes
  IPv6 support:          yes

***********************************************************
*            Now run 'make install'                       *
*                                                         *
*            Thank you for using Zabbix!                  *
*              <http://www.zabbix.com>                    *
***********************************************************

+ nproc
+ make -j4 -s dbschema
+ nproc
+ make -j4 -s
Making all in src
Making all in libs
Making all in zbxcrypto
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcommon
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxlog
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxalgo
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxnix
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxconf
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxhttp
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxsysinfo
Making all in agent
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in common
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in simple
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in linux
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxsys
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcomms
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxjson
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxexec
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxmodules
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxregexp
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxipcservice
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcompress
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcommshigh
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdb
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdbupgrade
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdbcache
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxdbhigh
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxhttp
Making all in zbxmemory
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxserver
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxicmpping
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxself
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxtasks
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxhistory
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxcompress
Making all in zbxembed
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zbxprometheus
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_agent
Making all in logfiles
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_get
Making all in zabbix_sender
Making all in zabbix_server/dbsyncer
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/dbconfig
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/discoverer
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/httppoller
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/pinger
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/poller
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/trapper
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/selfmon
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/snmptrapper
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/vmware
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/ipmi
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/odbc
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/scripts
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_server/preprocessor
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in zabbix_proxy
Making all in heart
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in housekeeper
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in proxyconfig
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in datasender
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in taskmanager
ar: `u' modifier ignored since `D' is the default (see `U')
ar: `u' modifier ignored since `D' is the default (see `U')
Making all in database
Making all in ibm_db2
Making all in mysql
Making all in oracle
Making all in postgresql
Making all in sqlite3
Making all in man
Making all in misc
+ cp src/zabbix_proxy/zabbix_proxy /usr/sbin/zabbix_proxy
+ cp src/zabbix_get/zabbix_get /usr/bin/zabbix_get
+ cp src/zabbix_sender/zabbix_sender /usr/bin/zabbix_sender
+ cp conf/zabbix_proxy.conf /etc/zabbix/zabbix_proxy.conf
+ chown --quiet -R zabbix:root /etc/zabbix
+ cd /tmp/
+ rm -rf /tmp/zabbix-4.4.4/
+ apk del --purge --no-network build-dependencies
WARNING: Ignoring APKINDEX.00740ba1.tar.gz: No such file or directory
WARNING: Ignoring APKINDEX.d8b2a6f4.tar.gz: No such file or directory
(1/55) Purging git-perl (2.22.2-r0)
(2/55) Purging perl-git (2.22.2-r0)
(3/55) Purging perl-error (0.17027-r0)
(4/55) Purging build-dependencies (20200116.013845)
(5/55) Purging autoconf (2.69-r2)
(6/55) Purging m4 (1.4.18-r1)
(7/55) Purging automake (1.16.1-r0)
(8/55) Purging perl (5.28.2-r1)
(9/55) Purging coreutils (8.31-r0)
Executing coreutils-8.31-r0.post-deinstall
(10/55) Purging curl-dev (7.66.0-r0)
(11/55) Purging nghttp2-dev (1.39.2-r0)
(12/55) Purging libevent-dev (2.1.10-r0)
(13/55) Purging python2 (2.7.16-r2)
(14/55) Purging libssh2-dev (1.9.0-r1)
(15/55) Purging libxml2-dev (2.9.9-r3)
(16/55) Purging zlib-dev (1.2.11-r1)
(17/55) Purging net-snmp-dev (5.8-r2)
(18/55) Purging openipmi-dev (2.0.25-r1)
(19/55) Purging openipmi-lanserv (2.0.25-r1)
(20/55) Purging openldap-dev (2.4.48-r0)
(21/55) Purging openssl-dev (1.1.1d-r2)
(22/55) Purging cyrus-sasl-dev (2.1.27-r4)
(23/55) Purging util-linux-dev (2.33.2-r0)
(24/55) Purging libfdisk (2.33.2-r0)
(25/55) Purging libsmartcols (2.33.2-r0)
(26/55) Purging pcre-dev (8.43-r0)
(27/55) Purging libpcre16 (8.43-r0)
(28/55) Purging libpcre32 (8.43-r0)
(29/55) Purging libpcrecpp (8.43-r0)
(30/55) Purging sqlite-dev (3.28.0-r2)
(31/55) Purging git (2.22.2-r0)
(32/55) Purging g++ (8.3.0-r0)
(33/55) Purging gcc (8.3.0-r0)
(34/55) Purging binutils (2.32-r0)
(35/55) Purging libatomic (8.3.0-r0)
(36/55) Purging libgomp (8.3.0-r0)
(37/55) Purging libc-dev (0.7.1-r0)
(38/55) Purging musl-dev (1.1.22-r3)
(39/55) Purging libstdc++ (8.3.0-r0)
(40/55) Purging make (4.2.1-r2)
(41/55) Purging unixodbc-dev (2.3.7-r1)
(42/55) Purging libbz2 (1.0.6-r7)
(43/55) Purging libacl (2.2.52-r6)
(44/55) Purging libattr (2.4.48-r0)
(45/55) Purging ncurses-dev (6.1_p20190518-r0)
(46/55) Purging pkgconf (1.6.1-r1)
(47/55) Purging expat (2.2.8-r0)
(48/55) Purging gdbm (1.13-r1)
(49/55) Purging popt (1.16-r7)
(50/55) Purging libgcc (8.3.0-r0)
(51/55) Purging pcre2 (10.33-r0)
(52/55) Purging mpc1 (1.1.0-r0)
(53/55) Purging mpfr3 (3.1.5-r1)
(54/55) Purging isl (0.18-r0)
(55/55) Purging gmp (6.1.2-r1)
Executing busybox-1.30.1-r2.trigger
OK: 32 MiB in 44 packages
+ rm -rf '/var/cache/apk/*'
Removing intermediate container 9d45c4933b15
 ---> 0ad81ad2ef1c
Step 12/19 : EXPOSE 10051/TCP
 ---> Running in 36f9c9dbfb6e
Removing intermediate container 36f9c9dbfb6e
 ---> 099763483d52
Step 13/19 : WORKDIR /var/lib/zabbix
 ---> Running in d14b0bc7be7e
Removing intermediate container d14b0bc7be7e
 ---> 34865c632de9
Step 14/19 : VOLUME ["/usr/lib/zabbix/externalscripts", "/var/lib/zabbix/enc", "/var/lib/zabbix/modules", "/var/lib/zabbix/snmptraps"]
 ---> Running in fd4ddc6c8903
Removing intermediate container fd4ddc6c8903
 ---> df41286e1e92
Step 15/19 : VOLUME ["/var/lib/zabbix/ssh_keys", "/var/lib/zabbix/ssl/certs", "/var/lib/zabbix/ssl/keys", "/var/lib/zabbix/ssl/ssl_ca"]
 ---> Running in cf6b3889a127
Removing intermediate container cf6b3889a127
 ---> 40e92834aca3
Step 16/19 : COPY ["docker-entrypoint.sh", "/usr/bin/"]
 ---> 596d039c6081
Step 17/19 : ENTRYPOINT ["/sbin/tini", "--", "/usr/bin/docker-entrypoint.sh"]
 ---> Running in a3497d3216e2
Removing intermediate container a3497d3216e2
 ---> 92dd90fc6984
Step 18/19 : USER zabbix
 ---> Running in 504e54d08c94
Removing intermediate container 504e54d08c94
 ---> 1778384c030a
Step 19/19 : CMD ["/usr/sbin/zabbix_proxy", "--foreground", "-c", "/etc/zabbix/zabbix_proxy.conf"]
 ---> Running in ccf205b3c149
Removing intermediate container ccf205b3c149
 ---> c878a343e32c

Successfully built c878a343e32c
Successfully tagged zabbix-proxy-sqlite3:alpine-local
```
