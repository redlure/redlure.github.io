# The redlure-worker

[GitHub Repo](https://github.com/redlure/redlure-console)

redlure-workers are desgined to be expendable phishing servers that you can build/destory engagement to engagement, or even on the fly during engagements. The workers host your actual phishing sites and communicate results back to your console, allowing the console to be the central hub for all results and templates while keeping the console's internet exposure to a minimum, increasing its longevity.

Being able to have a variable number of workers connected to a single console at any given time, allows operators the flexibility to host multiple campaigns across multiple domains, depending on needs across simultaneous engagements.

## High-Level Process Overview
Basic flow of what redlure-workers do:
1. The worker will recieve HTTP POST data from your redlure-console containing phishing campaign data (HTML, routes, payloads, etc)
2. The worker takes this campaign data and writes a Flask app to `campaigns/<id>` and copies over static files from the specified `UPLOAD_FOLDER`
3. Start the phishing web server (flask app) using gunicorn3
4. At this point, your phishing targets are ideally beginning to interact with your email link and your phishing site
5. As the phishing web server recieves opens, clicks, downloads and submissions, the worker sends HTTP POST data with results back to your console 
6. When the console communicates to stop the campaign, the worker kills the process bound to the campaign's port and deletes the campaign's template data from disk

All redlure-worker API routes require the API key specified in `config.py` to be provided and all data returned to the console will be sent along with the API key.