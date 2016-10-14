# Nginx-Lua-Anti-Hotlinking-Config
My soloution to those who try to use proxies to hotlink / steal or waste bandwidth from your sites and servers it works the same as the secure_link module but i did it using entirely Lua

The way this works is a rather than hack the core of your PHP, ASP.net, Javascript, HTML etc what ever your web application / CMS uses to generate it's link's, I rewrite the output links in the html body contents so you don't need to hack your web application and risk making it incompatible with other servers.
