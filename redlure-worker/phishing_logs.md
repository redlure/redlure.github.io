# Phishing Logs
While a campaign is active, the worker creates a temporary directory in `redlure-worker/campaigns/{id}`. The gunicorn3 web logs are output to `gunicorn3.log`. If you enjoy monitoring your phishing web server for hits, you can keep a `tail` going on this file during the campaign.

When the campaign is stopped, the entire temporary campaign folder will be deleted from disk on the worker.