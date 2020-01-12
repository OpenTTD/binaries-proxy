# Binaries Proxy

[![GitHub License](https://img.shields.io/github/license/OpenTTD/binaries-proxy)](https://github.com/OpenTTD/binaries-proxy/blob/master/LICENSE)
[![GitHub Tag](https://img.shields.io/github/v/tag/OpenTTD/binaries-proxy?include_prereleases&label=stable)](https://github.com/OpenTTD/binaries-proxy/releases)
[![GitHub commits since latest release](https://img.shields.io/github/commits-since/OpenTTD/binaries-proxy/latest/master)](https://github.com/OpenTTD/binaries-proxy/commits/master)

[![GitHub Workflow Status (Testing)](https://img.shields.io/github/workflow/status/OpenTTD/binaries-proxy/Testing/master?label=master)](https://github.com/OpenTTD/binaries-proxy/actions?query=workflow%3ATesting)
[![GitHub Workflow Status (Publish Image)](https://img.shields.io/github/workflow/status/OpenTTD/binaries-proxy/Publish%20image?label=publish)](https://github.com/OpenTTD/binaries-proxy/actions?query=workflow%3A%22Publish+image%22)
[![GitHub Workflow Status (Deployments)](https://img.shields.io/github/workflow/status/OpenTTD/binaries-proxy/Deployment?label=deployment)](https://github.com/OpenTTD/binaries-proxy/actions?query=workflow%3A%22Deployment%22)

[![GitHub deployments (Staging)](https://img.shields.io/github/deployments/OpenTTD/binaries-proxy/staging?label=staging)](https://github.com/OpenTTD/binaries-proxy/deployments)
[![GitHub deployments (Production)](https://img.shields.io/github/deployments/OpenTTD/binaries-proxy/production?label=production)](https://github.com/OpenTTD/binaries-proxy/deployments)

OpenTTD uses the CDN (Spaces) from DigitalOcean.
Currently they have a drawback: only IPv4 is supported.
To still ensure we can deliver IPv6 connectivity, this repository exists.

With this small Docker container we create a nginx proxy on [proxy.binaries.openttd.org](https://proxy.binaries.openttd.org).
If the request is via IPv4, it will be redirected to the CDN (with a 301).
If the request is via IPv6, it will serve the binary file directly, via proxy_pass, from the CDN.

Hopefully DigitalOcean supports IPv6 soon, so we can remove this unneeded hop completely.
