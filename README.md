# Jellyfin Operator (k8s)

## Description

[Jellyfin][Jellyfin source] is a media system for streaming to any device from 
your own server.

## Usage

To use Jellyfin, need to have a working Kubernetes environment, and have bootstrapped a
Juju controller of version 2.9+, with a model ready to use with the Kubernetes
cloud.

Example deployment:

```shell
charmcraft pack
juju deploy ./jellyfin-k8s_ubuntu-20.04-amd64.charm jellyfin --resource jellyfin-image=jellyfin/jellyfin:unstable
juju deploy nginx-ingress-integrator ingress
juju relate jellyfin ingress
```

### Scale Out Usage
To add additional Jellyfin units for high availability,

```shell
juju add-unit jellyfin-k8s
```

## Relations
Currently, supported relations are:
- `ingress`, for interfacing with [nginx-ingress-integrator][nginx-ingress-integrator operator].

## OCI Images
This charm can be used with the following image:
- `jellyfin/jellyfin:unstable`


[Jellyfin source]: https://github.com/jellyfin/jellyfin
[nginx-ingress-integrator operator]: https://charmhub.io/nginx-ingress-integrator
