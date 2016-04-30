# MySQL CLI Administration

## Users

### Create
#### Passwordless
```sql
CREATE USER 'robr3rd'@'localhost';
```

#### Password
MySQL will automatically hash the password using the assigned authentication plugin (by default, `mysql_native_password` which uses a 41-bit salted SHA-1, although a third-party tool can be specified if the need exists).

```sql
CREATE USER 'robr3rd'@'localhost' IDENTIFIED BY 'notes';
```

#### Password (pre-hashed)
MySQL will insert the *literal* values of the password string with this command, performing *no* actions on it. That being said, anytime the user tries to authenticate, MySQL will still apply its authentication plugin to their login password and will expect it to match. As such, it is important that this string matches what MySQL would have produced on its own since it will apply those operations to input to match this stored value regardless.

```sql
CREATE USER 'robr3rd'@'localhost' IDENTIFIED BY PASSWORD '*605B9A238B144A9D5E6D8C08558960EC65BBB981';
```

##### Examples
To pre-hash the password, it is quite simple (since MySQL's `mysql_native_password` hashing algorithm is quite simple, itself).

###### PHP
```php
<?php echo strtoupper(sha1(sha1('notes', true))); ?>
```



### Delete
#### Simple
```sql
DROP USER 'robr3rd'@'localhost';
```

#### Advanced
For more complex situations, especially involving multiple user rows, a simple `DELETE` statement will do the trick.

```sql
DELETE FROM mysql.user WHERE User = 'robr3rd' AND Host = 'localhost';
```



## Privileges
[List of Privileges](http://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html)

### Grant
[docs](http://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html)

#### All
```sql
GRANT ALL ON db1.* TO 'robr3rd'@'localhost';
```

#### Single
```sql
GRANT SELECT ON db2.data TO 'robr3rd'@'localhost';
```

### Revoke
[docs](http://dev.mysql.com/doc/refman/5.7/en/revoke.html)

#### All
```sql
REVOKE ALL PRVILEGES, GRANT OPTION FROM 'robr3rd'@'localhost';
```

#### Single
```sql
REVOKE SELECT ON db2.data FROM 'robr3rd'@'localhost';
```

## Backup and Restore / Import
### Backup
> Note: The timestamp is *not* necssary; rather, it is simply a (rather helpful) suggestion.

```shell
mysqldump db1 > db1.dump.$(date +%Y-%m-%d_%H:%M:%S).sql --user=robr3rd --password
```

### Restore / Import
To "restore" from a `mysqldump` backup file (or *any* `*.sql` file that defines the structure of your database), you start by simply connecting to MySQL the same way that you normally would (`mysql -h [host] -u [user] -p [database]`) but then you pipe the contents of the backup into that:

```shell
mysql -u robr3rd -p db1 < db1.dump.[timestamp].sql
```

> Note: This should generally be performed on a *fresh* database. For instance, after `DROP DATABASE db1` and `CREATE DATASE db1` to fully reset everything.
