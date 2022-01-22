# The redlure-console

[GitHub Repo](https://github.com/redlure/redlure-console)

The redlure-console is the main component of redlure. It is designed to be long-running and persistent across engagements to avoid the need to spin up a new one for each phishing engagement and the work that comes along with that (i.e. reimporting templates and data you use frequently). To make this realistic, the console component's ideal exposure is small to avoid the IP or domain being burned or phishing activity being traced to your console. How this works:
- The console can complete all its functions with a firewall strictly configured to let your required IPs and redlure-worker IPs inbound. 
- The actual hosting of phishing web pages is farmed out to the redlure-workers, which are expendable by design.
- The console serves as your hub for consolidating phishing results, templates and other data associated with your phishing campaigns.
- The most exposure your console should really have is its communication to your configured SMTP servers to send the phishing emails.

The console should alleviate the need to SSH out to phishing servers to configure SSL/domain changes and allow you to keep a single point of interaction for most of your phishing engagments. This has been a huge time saver and convenience for me when using redlure for phishing.  