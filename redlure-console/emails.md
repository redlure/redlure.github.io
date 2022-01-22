# Emails
The emails component is used to create HTML emails for your campaigns. redlure does not come with any email templates so you must supply your own or create new ones. redlure does not natively support importing emails, however, you can simply grab the source of an email from your email client and paste it into a redlure email template.

### Variables
Variables can be used within your email templates to insert text when sent that may be unique to each recipient.
- {%raw%}`{{ fname }}`{%endraw%} - The first name of the recipient
- {%raw%}`{{ lname }}`{%endraw%} - The last name of the recipient
- {%raw%}`{{ name }}`{%endraw%} - First and last name of the recipient
- {%raw%}`{{ email }}`{%endraw%} - The email address of the recipient
- {%raw%}`{{ id }}`{%endraw%} - The unique tracking ID used to identify each recipient
- {%raw%}`{{ url }}`{%endraw%} - The URL to your initial landing page ({%raw%}`http[s]://yourdomain.com/custom/page1/path?id={{ id }}`{%endraw%})
- {%raw%}`{{ payload_url }}`{%endraw%} - The URL to your payload, assuming a payload will be configured for your campaign ({%raw%}`http[s]://yourdomain.com/custom/payload/path?id={{ id }}`{%endraw%})


