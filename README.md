# Password Manager

A simple local password manager written in Python and MariaDB.

# Installation
You need to have python3 to run this on Windows

## Windows
### Install Python Requirements
```pip install -r requirements.txt```

### MariaDB
#### Install
Follow [these instructions](https://www.mariadbtutorial.com/getting-started/install-mariadb/) to install MariaDB on Windows
#### Create user and grant privileges
- Navigate to MariaDB bin directory
```
C:\Program Files\MariaDB\bin
```
- Login as root with the password you chose while installation
```
mysql.exe -u root -p
```
- Create user
```
CREATE USER 'pm'@localhost IDENTIFIED BY 'password';
```
- Grant privileges
```
GRANT ALL PRIVILEGES ON *.* TO 'pm'@localhost IDENTIFIED BY 'password';
```


## Run
### Configure

first we need to configure the by choosing a MASTER PASSWORD.
```
python config.py make
```
To configure by Master Password
```
python config.py delete
```
To delete all existing configuration. - All data will be lose
```
python config.py remake
```
To delete all existing configuration and create new configuration by MASTER Password.
### Usage
```
python pm.py -h
usage: pm.py [-h] [-s NAME] [-u URL] [-e EMAIL] [-l LOGIN] [--length LENGTH] [-c] option

Description

positional arguments:
  option                (a)dd / (e)xtract / (g)enerate

optional arguments:
  -h, --help            show this help message and exit
  -s NAME, --name NAME  Site name
  -u URL, --url URL     Site URL
  -e EMAIL, --email EMAIL
                        Email
  -l LOGIN, --login LOGIN
                        Username
  --length LENGTH       Length of the password to generate
  -c, --copy            Copy password to clipboard
```


### Add entry
```
python pm.py add -s mysite -u mysite.com -e hello@email.com -l myusername
```
### Retrieve entry
```
python pm.py extract
```
command to retrieves all the entries
```
python pm.py e -s mysite
```
command to retrieves all the entries with site name is "mysite"
```
python pm.py e -s mysite -l myusername
```
command to retrieves the entry whose site name is "mysite" and username is "myusername"
```
python pm.py e -s mysite -l myusername --copy
```
command to copies the password of the site "mysite" and username "myusername" into the clipboard
### Generate Password
```
python pm.py g --length 15
```
command auto generates a password of length 15 and copies to clipboard
