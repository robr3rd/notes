# MySQL
## Cheat Sheets
- [Reserved Words](https://dev.mysql.com/doc/refman/en/keywords.html)

## Alternatives
A few alternatives exist for MySQL (excluding Oracle). In the case of the two below, they both began life as MySQL forks and continue to do so to this day, so any upstream fixes are free.

- [MariaDB](https://mariadb.com/kb/en/mariadb/what-is-mariadb-53/#query-optimizer)
	- Coomunity-driven with a focus on speed and features, leaving full MySQL compatibility behind (if migrating FROM Maria TO MySQL) in acceptance of being the only way if features are desired.
	- Nearly every Linux distro is now using this as the default install even though the package may still be labelled as `mysql`.
- [Percona Server](https://www.percona.com/software/mysql-database/percona-server/feature-comparison)
	- Company-driven with a focus on speed, stability, and maximal compatibility with MySQL (due to the nature of their customers generally being corporations).
	- Percona develops a multitude of MySQL tools, which have deep integrations with Percona Server.
