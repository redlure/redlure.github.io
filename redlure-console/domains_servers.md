# Servers
Stand up [redlure-workers](https://github.com/redlure/redlure-worker) on separate servers and then add them to the servers page so that the server/console can communicate with them. Adding a new server requires:
* IP address of the server running the redlure-worker API
* Alias or nickname for the server
* Port the worker API is running on

## Functions
The servers page offers the following functions:
* Listening ports - This checks which ports on the server are currently listening. Equivalent of running `netstat -ntlp` on the host
* Upload files - Upload or delete files from a resource folder (specified in the worker's config file) on the server. Payloads added here can be selected to be served during the campaign at a custom URL to be used with the `{{ payload_url }}` and `{{ serve_payload }}` variables
* Refresh status - Checks if the server/console can communicate with the worker. Possible statuses:
    -__Online__ - Communication with the worker is successful
    -__Mismatching API Key__ - indicates the API key needs to be updated in the worker's config file.
    -__Unsupported Worker Version - indicates the worker API is running a version that is not supported by your console version. Upgrade your worker to a newer supported version.


## API Key
The top of the servers section includes an API key. This key must be copied to the config file of each redlure-worker so that the worker and server/console can communicate. *If the API key is changed, all communications to/from workers will fail until workers have the config file updated with the new API key.*

# Domains
Add domains you own and phish from here. Only domains that resolve to an IP address of one of your servers will be usable. 

## Functions
The domains page offers the following functions:
* Edit certs - add the paths to SSL cert and key files. These locations will be checked when you configure a campaign to run using this domain with SSL
* Generate certs - Generate or renew SSL certificates using Let's Encrypt. This will only work if the domain resolves to an IP address of one of your servers. Certs will be generated on the worker the domain currently resolves to.
* Refresh DNS - Check if the IP address the domain points to has changed