# Installing the redlure-console
Requires Python3.9 and uses `pipenv` to manage dependencies. The server's functionality does not require root privileges to run but may need them to access custom SSL certs or listen on the desired port. Use the following commands to install the console:

```shell
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

*Usernames are case sensitive.*

## Hardware and OS
I typically deploy the client and console on the same host. Usually running Ubuntu LTS or Debian images from Digital Ocean or Vultr. The minimum memory I'd run this server with is 2 GB. Full specs are generally around 2 GB Memory/1 CPU and 50-65 GB disk space. My console/client server costs roughly $10-15 per month depending on the cloud provider.

__If you run the console/client with less than 2GB memory, you are almost guaranteed to experience [issues](https://github.com/redlure/redlure-console/issues/10).__ 