# Nginx-Lua-Anti-Hotlinking-Config
My soloution to those who try to use proxies to hotlink / steal or waste bandwidth from your sites and servers it works the same as the secure_link module but i did it using entirely Lua.

If you have a problem make a Issue request or if you fix something make a pull request and i will push it to the main repo. Thanks for any contributions that will help others <3

The way this works is a rather than hack the core of your PHP, ASP.net, Javascript, HTML etc what ever your web application / CMS uses to generate it's link's, I rewrite the output links in the html body contents so you don't need to hack your web application and risk making it incompatible with other servers.

Only uses the following Lua syntaxes
```
body_filter_by_lua_block {}
header_filter_by_lua_block {}
access_by_lua_block {}
```

#HTML Example output
Lua will use regex to match src="*" and replace the link on the page output contents with its generated secure link
In the config example i provided i show only .MP4 urls to be replace / rewritten but you can litteraly change the .mp4 to .mp3 .m4v .avi .flv .swf what ever the file format you want to force the user getting the file to have to visit your site to get a secure link in the first place.
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

Your browser does not support the video tag.
</video>
</body>
</html>
```

## Known Issue's :
Peseudo Streaming does not seem to wan't to work with any form of secure link generation including Nginx's built in secure_link module if anyone knows a way around this or a fix please do share / feel free to make a pull request post a issue etc.
