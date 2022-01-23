![](gitbook/images/redlure.png)
# Introduction to redlure
redlure is a phishing framework designed with concurrent offensive engagements in mind. redlure utilizes a distributed architecture that allows for multiple campaigns to be run on different ports and/or servers, while results are aggregated in a single interface. This allows you to generate phishing templates, target lists, start/stop campaigns, change domains, change ports and generate Let's Encrypt certs on multiple workers all from one interface. 

redlure was released as a part of DEFCON 28 Demo Labs. ([Associated presentation/demo](https://www.youtube.com/watch?v=ZtCMnKHZJUM)) 

To get started, check out the [Initial Install](Initial_Install.md) page.

# Features
- Manage phishing campaigns running in parallel across multiple servers, ports and domains.
- Chain webpage templates together for multi-step phishing (e.g. Office365, Gmail).
- Workspaces to manage results and templates separately for each engagement.
- Partial database encryption (for sensitive data, such as cleartext passwords).
- Generate Let's Encrypt certs remotely (other certificates can be manually specified)
- Manage payload delivery via automatic downloads or links and buttons
- Role-based authentication

# The redlure Ecosystem
redlure is comprised of three components:

1. __redlure-console__ - Centralized Python API that the operator interacts with. The console stores all your phishing templates and data while also aggregating your campaigns results. It manages your redlure-workers, along with their hosted phishing campaings.
2. __redlure-worker__ - Skeletal Python API that manages the web server for hosting phishing campaigns. These are designed to be burnable and scalable. This is the only component that phishing targets interact with. Multiple redlure-workers can and should be managed from a single console.
3. __redlure-client__ - Web interface for interacting with the console API. Written with the Angular 10 framework (Typescript and HTML).

Below is an example of a fully setup redlure environment. Typically, I'd setup 3 cloud servers for the infrastructure seen below: one server to host both the console and client and two servers for the redlure-workers (one per worker).

![](gitbook/images/diagram-v2.png)
