# Installing the redlure-console
Requires Python3.9 and uses `pipenv` to manage dependencies. The server's functionality does not require root privileges to run but may need them to access custom SSL certs or listen on the desired port. Use the following commands to install the console:

```
apt-get install python3.9
pip3 install pipenv
git clone https://github.com/redlure/redlure-console.git
cd redlure-console
pipenv install
sudo pipienv run ./redlure-console.py
```

The first time you boot the console, you will be prompted to enter a cipher passphrase. *Don't forget this.* The passphrase will be used to encrypt sensivite data in the database, like victim-submitted POST data and SMTP credentials. Each subsequent time you start the console, you'll be prompted to enter this passphrase so DB data can be properly decrypted.

## Configuration
Make changes to `config.py`:
* Set `CERT_PATH` and `KEY_PATH` to custom SSL certificates (recommended). If using self-signed certs, some browers may require you to browse to and accept the risk before client to console traffic will work.
* Set the value of `SECRET_KEY` (a suggested random value will be given on startup if not set)

## Default Login
Use the username `admin` and the password `redlure` the first time you log in.
