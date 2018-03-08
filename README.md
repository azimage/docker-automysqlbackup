Docker Image Packaging for AutoMySQLBackup
==========================================

[![Travis](https://img.shields.io/travis/alvistack/docker-automysqlbackup.svg)](https://travis-ci.org/alvistack/docker-automysqlbackup)
[![GitHub release](https://img.shields.io/github/release/alvistack/docker-automysqlbackup.svg)](https://github.com/alvistack/docker-automysqlbackup/releases)
[![GitHub license](https://img.shields.io/github/license/alvistack/docker-automysqlbackup.svg)](https://github.com/alvistack/docker-automysqlbackup/blob/master/LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/alvistack/docker-automysqlbackup.svg)](https://hub.docker.com/r/alvistack/docker-automysqlbackup/)

AutoMySQLBackup with a basic configuration will create Daily, Weekly and Monthly backups of one or more of your MySQL databases from one or more of your MySQL servers.

Learn more about AutoMySQLBackup: <https://sourceforge.net/projects/automysqlbackup/>

Overview
--------

This Docker container makes it easy to get an instance of AutoMySQLBackup up and running.

### Quick Start

For the `BACKUPDIR` directory that is used to store the repository data (amongst other things) we recommend mounting a host directory as a [data volume](https://docs.docker.com/engine/tutorials/dockervolumes/#/data-volumes), or via a named volume if using a docker version &gt;= 1.9.

Volume permission is managed by entry scripts. To get started you can use a data volume, or named volumes.

Start AutoMySQLBackup:

    # Pull latest image
    docker pull alvistack/docker-automysqlbackup

    # Run as detach
    docker run \
        -itd \
        --rm \
        --network mysql \
        --name automysqlbackup \
        --volume /var/lib/automysqlbackup:/var/lib/automysqlbackup \
        -e USERNAME=root \
        -e PASSWORD=secret \
        -e DBHOST=localhost \
        alvistack/docker-automysqlbackup

**Success**. AutoMySQLBackup will now create dumps of all databases from your remote MySQSL into `/var/lib/automysqlbackup` and exit.

### Environment Variables

#### USERNAME

Username to access the MySQL server.

Default: *NONE*

#### PASSWORD

Password to access the MySQL server.

Default: *NONE*

#### DBHOST

Host name (or IP address) of MySQL server.

Default: `localhost`

#### DBNAMES

List of space separated database names for Daily/Weekly Backup. Set to all for all databases.

Default: `all`

#### BACKUPDIR

Backup directory location.

Default: `/var/lib/automysqlbackup`

#### MAILCONTENT

How's backup log managed.

Note: Since send out mail from docker is basically not supported, this option should be useless.

Default: `stdout`

#### MAXATTSIZE

Sets the largest allowed email attachments total (all backup files) you want the script to send.

Note: Since send out mail from docker is basically not supported, this option should be useless.

Default: `4000`

#### MAILADDR

Where backup log goes.

Note: Since send out mail from docker is basically not supported, this option should be useless.

Default: *NONE*

#### MDBNAMES

List of space separated database names for Monthly Backups.

Default: *NONE*

#### DBEXCLUDE

List of DBNAMES to exclude if DBNAMES are set to all (must be in " quotes).

Default: `mysql performance_schema information_schema`

#### CREATE\_DATABASE

Include CREATE DATABASE in backup?

Default: `yes`

#### SEPDIR

Separate backup directory and file for each DB? (yes or no).

Default: `yes`

#### DOWEEKLY

Which day do you want weekly backups? (1 to 7 where 1 is Monday).

Default: `6`

#### COMP

Choose Compression type. (gzip or bzip2)

Default: `gzip`

#### COMMCOMP

Compress communications between backup server and MySQL server?

Default: `no`

#### LATEST

Additionally keep a copy of the most recent backup in a seperate directory.

Default: `yes`

#### MAX\_ALLOWED\_PACKET

The maximum size of the buffer for client/server communication. e.g. 16MB (maximum is 1GB)

Default: *NONE*

#### SOCKET

For connections to localhost. Sometimes the Unix socket file must be specified.

Default: *NONE*

#### PREBACKUP

Command to run before backups.

Default: *NONE*

#### POSTBACKUP

Command run after backups.

Default: *NONE*

#### ROUTINES

Backup of stored procedures and routines.

Default: `yes`

Versioning
----------

The `latest` tag matches the most recent version of this repository. Thus using `alvistack/docker-automysqlbackup:latest` or `alvistack/docker-automysqlbackup` will ensure you are running the most up to date version of this image.

License
-------

-   Code released under [Apache License 2.0](LICENSE)
-   Docs released under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/)

Author Information
------------------

-   Wong Hoi Sing Edison
    -   <https://twitter.com/hswong3i>
    -   <https://github.com/hswong3i>

