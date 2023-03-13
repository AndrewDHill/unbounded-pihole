# Pi-Hole + Unbound on Docker

### Use Docker to run [Pi-Hole](https://pi-hole.net) with an upstream [Unbound](https://nlnetlabs.nl/projects/unbound/about/) resolver.

This repo has ~~2 different~~ one `docker-compose` config-- ~~choose your favorite~~. The ~~`two-container` config may work better on Synology due to usage of `macvlan` networking which helps prevent port conflicts with the host~~ other container which I deleted, didn't work for me.

- [`one-container`](one-container/) (new) - Install Unbound directly into the Pi-Hole container
  - This configuration contacts the DNS root servers directly, please read the Pi-Hole docs on [Pi-hole as All-Around DNS Solution](https://docs.pi-hole.net/guides/unbound/) to understand what this means.
  - With this approach, we can also simplify our Docker networking since `macvlan` is no longer necessary.
- ~~[`two-container`](two-container/) (legacy) - Use separate containers for Pi-Hole and Unbound~~
  ~~- This configuration uses MatthewVance's [unbound-docker](https://github.com/MatthewVance/unbound-docker) container to implement encrypted DNS to third party DNS resolvers (eg Cloudflare). This is arguably less privacy-friendly since you're handing your DNS queries to those 3rd party providers.~~

Also, thank you [ChrisCrowe](https://github.com/chriscrowe) and PiHole and Unbound!