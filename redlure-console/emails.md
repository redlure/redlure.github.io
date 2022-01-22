# Emails
The emails component is used to create HTML emails for your campaigns. redlure does not come with any email templates so you must supply your own or create new ones. redlure does not natively support importing emails, however, you can simply grab the source of an email from your email client and paste it into a redlure email template.

### Variables
Variables can be used within your email templates to insert text when sent that may be unique to each recipient.
* ```{{ fname }}``` - The first name of the recipient
* ```{{ lname }}``` - The last name of the recipient
* ```{{ name }}``` - First and last name of the recipient
* ```{{ email }}``` - The email address of the recipient
* ```{{ id }}``` - The unique tracking ID used to identify each recipient
* ```{{ url }}``` - The URL to your initial landing page (`http[s]://yourdomain.com/custom/page1/path?id={{ id }}`)
* `{{ payload_url }}` - The URL to your payload, assuming a payload will be configured for your campaign (`http[s]://yourdomain.com/custom/payload/path?id={{ id }}`)


