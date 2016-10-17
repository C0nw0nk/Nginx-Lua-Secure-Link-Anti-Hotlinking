# Nginx-Lua-Anti-Hotlinking-Config
My soloution to those who try to use proxies to hotlink / steal or waste bandwidth from your sites and servers it works the same as the secure_link module but i did it using entirely Lua.

The reason i did this was because my PHP / CMS / Web Applications that i run all use caching and because they serve that same cached page to users with different IP addresses etc it means if my web app was to generate a secure link instead of Nginx they will be served 403 forbidden errors when ever they went to access any file.

If you have a problem make a Issue request or if you fix something make a pull request and i will push it to the main repo. Thanks for any contributions that will help others <3

The way this works is a rather than hack the core of your PHP, ASP.net, Javascript, HTML etc what ever your web application / CMS uses to generate it's link's, I rewrite the output links in the html body contents so you don't need to hack your web application and risk making it incompatible with other servers.

Only uses the following Lua syntaxes
```
body_filter_by_lua_block {}
header_filter_by_lua_block {}
access_by_lua_block {}
```

#HTML Example output
Lua will use regex to match src="*" and replace the link on the page output contents with its generated secure link for what ever file format types you choose.
```
<!DOCTYPE html>
<html>
<head>
<title>NetworkFlare.com | Test Page!</title>
<style>
body {
width: 35em;
margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif;
}
</style>
</head>
<body>
<h1>Test Page</h1>
<p><em>NetworkFlare.com Test page</em></p>
<video width="320" height="240" controls>

<!-- Video source link that should be caught by lua -->
<source src="/1.mp4" type="video/mp4">
<!-- This should be changed -->
<!-- Output url should be /1.mp4?md5=encrypted&expires=unix_timestamp -->

Your browser does not support the video tag.
</video>
</body>
</html>
```

## Known Issue's :
None :) <3

## TODO :
Make the regex recognize when a src="*" link contains "../" for back tracking directories currently it does not pick up on these link formats within the quotations so the hash encoded key generated will differ to the one generated in the file location resulting in the http 403 forbidden error.
The same goes for src="http://www.*" it needs to be more universal than just basic src="/*"
