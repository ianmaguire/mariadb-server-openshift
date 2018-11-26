## Maintained by: [MariaDB](https://mariadb.com/)

This is the Git repo of OpenShift compliant docker images for MariaDB Server, [mariadb-server-docker](https://github.com/ianmaguire/mariadb-server-openshift)

---

-	[Travis CI:  
	![build status badge](https://img.shields.io/travis/ianmaguire/mariadb-server-openshift/master.svg)](https://travis-ci.org/ianmaguire/mariadb-server-openshift/branches)

---

### Installation
Include the the version number as a docker tag.

To pull MariaDB Server version 10.3 run the following command:
```
docker pull mariadb/server-openshift:10.3
```

To run MariaDB Server version 10.3 run the following command:
```
docker run -d --name mariadb -e MARIADB_ROOT_PASSWORD=mypassword mariadb/server-openshift:10.3
```

### Configuration
The following environment variables can be utilized to configure behavior (one of the first three must be specified):
* MARIADB_ROOT_PASSWORD : specify the password for the root user
* MARIADB_ALLOW_EMPTY_PASSWORD : allow empty password for the root user
* MARIADB_RANDOM_ROOT_PASSWORD : generate a random password for the root user (output to logs)
* MARIADB_INITDB_SKIP_TZINFO : skip timezone setup
* MARIADB_ROOT_HOST : host for root user, defaults to '%'
* MARIADB_DATABASE : create a database with this name
* MARIADB_USER : create a user with this name, with all privileges on MARIADB_DATABASE if specified
* MARIADB_PASSWORD : password for above user

For backward compatibility, environment variables starting MYSQL_ rather than MARIADB_ will also work.

Custom scripts can be mapped as a host volume to /docker-entrypoint-initdb.d for execution post initialization in named / directory order. The following extensions are supported:
* .sh : shell script
* .sql : sql script
* .sql.gz : gzip compressed sql script
