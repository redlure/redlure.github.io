# Installing the redlure-client
The redlure-client is built with Angular10 and requires node package manager to install. To install the client use the following commands:
```shell
git clone https://github.com/redlure/redlure-client.git
sudo apt-get install npm
sudo npm i -g @angular/cli
cd redlure-client && npm install
```

The most painful part of setting up the client is getting the right version of Node installed. If starting the client gives you an error about the minimum required Node version, the most pain-free way I've found to fix this is using [Node Version Manager](https://github.com/nvm-sh/nvm).
```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
nvm install <required version>
```

The client interface can be started with:
```shell
./redlure-client.py
```
By default, this will start the client on port 4200.

## Configuration
Make changes to `config.py`
* `SSL` - Toggle the use of SSL
* `CERT_PATH` - set path of custom SSL cert 
* `KEY_PATH` - set path of custom SSL key
* `HOST` - Interface that the client will be served on
* `PORT` - Port the client will be served on

If `CERT_PATH` and `KEY_PATH` are left with their default values, self-signed certs will be generated and used

## Default Login
Once you have setup a console and client, you can log into redlure with the username `admin` and the password `redlure`.

*Usernames are case sensitive.*

## Hardware and OS
I typically deploy the client and console on the same host. Usually running Ubuntu LTS or Debian images from Digital Ocean or Vultr. The minimum memory I'd run this server with is 2 GB. Usually the specs are around 2 GB Memory/1 CPU and 50-65 GB disk space. Usually my console/client server costs roughly $10-15 per month depending on the cloud provider.

__If you run the console/client with less than 2GB memory, you are almost guaranteed to experience [issues](https://github.com/redlure/redlure-console/issues/10).__ 