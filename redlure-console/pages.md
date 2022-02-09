# Pages
The pages component is where you can store HTML templates to serve with your phishing campaigns. redlure lets you chain up to 4 templates together in 1 campaign (through the use of buttons or your mechanism of choice).

You can attempt to clone an existing webpage or build your own template in the [CodeMirror](https://codemirror.net/) editor.
![](../gitbook/images/newpage.png)

# IMPORTANT
Templates have three requirements to function the way you want, assuming you are collecting form data:
1. The HTML `form` tag must have the `method` attribute set to `POST`
2. The HTML `form` tag must have the `action` attribute set to `{{ next_url }}`
3. `Input` fields you want to capture must have the `name` attribute set.
4. The HTML form must include a button that submits the form (i.e. `input` tag with `type="submit"`)

Example:
```html
<form action="{{ next_url }}" method="POST">
    <input class="input-box" name="username" type="text">
    <input class="input-box" name="password" type="password"> 
    <input class="submit" type="submit" value="Sign In">
</form>
```

## Chaining Templates
The `{{ next_url }}` variable is used within page templates to direct visitors to the next phishing template in sequence. You'll likely use this most with form submissions, like the above, but two other quick examples are standalone buttons or a rudimentary redirector.

```html
<html>
    <body>
        Loading...
        <meta http-equiv="refresh" content="1; url={{ next_url }}">
    </body>
</html>
```

```html
<form action="{{ next_url }}" method="GET">
    <button class="submit" type="submit">Click to Enter!</button>
</form>
```

# Variable (Username/Email) Passthrough
To mimic multi-page logins that display your username on the password form page (think Office365, Google), you can use to following variables within your HTML. These __*cannot*__ be used on your first landing page in a sequence; a form with an input field named one of these values must be submitted on the prior page.
- {%raw%}`{{ loginfmt }}`{%endraw%} - Will display value from the prior page's form input where `name="loginfmt"`
- {%raw%}`{{ email }}`{%endraw%} - Will display value from the prior page's form input where `name="email"`
- {%raw%}`{{ username }}`{%endraw%} - Will display value from the prior page's form input where `name="username"`

# Serving a payload
When you configure a campaign you can optionally select a payload you've uploaded to your server/worker and set a URL path for it to be served at. A link to the payload route can be sent directly via email or it can be referenced as a variable in your HTML page template, in 1 of 2 ways:
1. Automatically download file when your page is browsed to
2. Download the file when a button is pressed or another action is taken

## Auto Download on Page Visit
To drop a payload when a visitor hits your redlure page, add the `{{ serve_payload }}` to your HTML page template. Example:
```html
<!DOCTYPE html>
<html>
<head></head>
<body>

     <!-- SNIPPED HTML CONTENT -->

</body>

{{ serve_payload }}

</html>
```
 When your page is rendered the variable with be replaced with:
 `<meta http-equiv="refresh" content="0; url=http[s]://yourdomain.com/custom/payload/path?id=[visitor_id]">`
This could be done by other means, such as directly inserting the `<meta>` tag in the page template, but I've found this will usually throw WYSIWYG editors for a loop when previewing your page.
## Download on Action
If you want to place your payload download behind a click using a button or hyperlink, you can use the `{{ payload_url }}` within your page template. Example:
```html
<p><a href="{{ payload_url }}" style="cursor: pointer;">Click here</a> if the download does not begin.</p>

<!-- OR -->

<form action="{{ payload_url }}" method="GET">
    <button class="submit" type="submit">Download</button>
</form>
```



