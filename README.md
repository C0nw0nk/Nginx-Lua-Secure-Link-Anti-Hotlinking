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

## Known Issue's :
Peseudo Streaming does not seem to wan't to work with any form of secure link generation including Nginx's built in secure_link module if anyone knows a way around this or a fix please do share / feel free to make a pull request post a issue etc.
