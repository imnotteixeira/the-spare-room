# the-spare-room
Where everything research/experimentation happens

## TODO
* Securing access to private components of the tunnels

## Networking

Currently relies on Cloudflare Tunnels:

* lab.* - The Entrypoint. A frontend gateway to all other resources
* split.* - A SplitPro self-hosted instance for bill splitting

The docker-compose starts a `cloudflared` service which allows cloudflare to create the different tunnels to the inside of the docker network. For instance, we can have a route to `http://homelab-frontend:80` as we have docker service dns resolution (the cloudflare daemon is inside the same network as other docker services)

The setup relies on a `TUNNEL_TOKEN` env variable (conveniently not pushed to the repository...) pointing to the token of the cloudflare network connector.