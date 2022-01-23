# Recommended Firewall Setup (Worker)
This is how I typically configure the firewall on redlure-workers, although it may vary depending on your use case. 

*If you are interested in the recommended firewall setup for the redlure-console, it can be found [here](../redlure-console/firewall.md).*

Basics to consider:
- __Target access to your phishing sites__ - make sure to allow access to all ports you intend to host phishing sites from. In the example below I've allowed 80,443 and 4443.
- __Let's Encrypt__ - workers can generate Let's Encrypt certs for you, remotely, using certbot, but this requires access to port 80.
- __SSH access__ - you'll need to perform setup and may want to check logs. Ideally SSH access is limited to your own VPN or infrastructure.
- __redlure-console communications__ - perhaps most importantly, the redlure-console you connect the worker to will need to be able communicate inbound on the port the worker API is hosted on (4445 by default).

![](../gitbook/images/worker-firewall.png)