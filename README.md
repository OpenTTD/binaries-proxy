# Binaries Proxy

OpenTTD uses the CDN (Spaces) from DigitalOcean.
Currently they have a drawback: only IPv4 is supported.
To still ensure we can deliver IPv6 connectivity, this repository exists.

With this small Docker container we create a nginx proxy on [proxy.binaries.openttd.org](https://proxy.binaries.openttd.org).
If the request is via IPv4, it will be redirected to the CDN (with a 301).
If the request is via IPv6, it will serve the binary file directly, via proxy_pass, from the CDN.

Hopefully DigitalOcean supports IPv6 soon, so we can remove this unneeded hop completely.
