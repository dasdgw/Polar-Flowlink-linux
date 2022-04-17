# Supported OS

GNU/Linux

# Requirements

## driver
libusb-dev, libudev-dev, libpq-dev
### install for ubuntu
```
sudo apt install libusb-dev libudev-dev libpq-dev
```

## web interface
apache2 with apache2-mod-php5 (or other web browser with php support), postgresql  

TODO: install cmds
```
sudo apt install apache2 apache2-mod-php5 postgresql
```

For database handling postgresql server is also required. psql client is recommended for debugging purposes.

##  ubuntu install PostgreSQL
https://www.digitalocean.com/community/tutorials/how-to-install-postgresql-on-ubuntu-20-04-quickstart-de
```
sudo apt install postgresql postgresql-contrib
```


# How to compile

firstly create 'bin' directory in the project tree,
then run 'make' in command line.
```
mkdir bin
make
```

# Installing web page

Run postgresql as user postgres and add user as role. Create database and allow user to do anything with the database.  
Basically you need to do (change <username> with your username):
```
sudo -u postgres createuser --interactive
sudo -u postgres psql
```

Run psql and within the psql shell type in:
```
create database <username>;
\c dasdgw;
create table <username>;
grant all privileges on database <username> to <username>;
```

I would also recommend:
```
grant all privileges on database <username> to root;
```

Finish with
```
\q
```

As normal user type in bash shell:
```
psql
\i sql-tables/polar-createtable
```

Copy directory web where it can be found by web browser. Edit config.php and enter your username and password required to access database.

# Inclusion of files from other authors

Part of package includes hidapi project, licensed under GPLv3, BSD and HIDAPI license. Terms under GPLv3 are chosen in this project.

# License

This work is licenced under GPL v3 or later. Please read LICENSE for more information.

# TODO
- Make a simple portal with excercise analysis. Make a better analyses and provide user feedback.

- Parse training program data.

- Parse data from footpod. I don't have it handy, so if you need this functionality consider lending me one ;).

- Daemonize process of reading from flowlink.
