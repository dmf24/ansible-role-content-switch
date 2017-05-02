# ansible-role-content-switch
An ansible role to configure a content-switch/load balancer using nginx

It was written for a specific environment and probably does not work as a generic role yet.

This role expects the following vars to be set:

```
# Defines backends for the content-switch/loadbalancer

nginx_backends:
  - name: <arbitrary identifier for backend>
    endpoints:
      - <hostname>:<port>

#Specifies which content-switch.conf template to use to generate nginx config.

nginx_content_switch: generic

sites:
  - name: <fqdn>
    instance: <reference to backend identifier>
    protocol: [http|https|http_and_https]
    allow_networks:
      - <network/netmask>
    certificate: <name of certificate> # relative to certspath
    # see templates/content-switch.conf/generic.j2. 
```
