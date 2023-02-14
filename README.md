# db-dump
Demo databases, subset of real world ones.

The database dump files in this repo may be used to create
sample databases to toy around with, and learn the essential
features of the PostgreSQL DBMS.

## Credits
| File        	| Source                                              	|
|-------------	|-----------------------------------------------------	|
| `films.sql` 	| Downloaded from DataCamp; data extracted from IMDb 	|

## Usage
Before we begin, you may want to assign yourself
as the owner of the database.
On a Unix-like system, you can do so using the `sed` utility program.

```shell
sed -i 's/mani/<your name>/g' films.sql
```

`mani` is the name I chose to assign to myself in my DB instance and 
you should replace `<your name>` with a name of your choice (the name must
already exist as a user in your DB cluster).

Beware that the above line will edit the file **in-place**. If you do
not wish to do so, simply remove the `-i` flag to output the content to
the terminal.

Now that the file is ready, create a new database by running

```
createdb demo
```

You may replace `demo` with a database name of your choice.

Finally, from the command-line, run
```
psql demo -f films.sql
```
to add the data to your `demo` database.

You may now open your database by running `psql demo` and verify that the 
tables have been added by typing
```
demo=# \dt
        List of relations
 Schema |  Name   | Type  | Owner 
--------+---------+-------+-------
 public | films   | table | mani
 public | people  | table | mani
 public | reviews | table | mani
 public | roles   | table | mani
(4 rows)
```
