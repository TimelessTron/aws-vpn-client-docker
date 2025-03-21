# aws-vpn-client-docker

> [!IMPORTANT]
> This repository is largely simply packaging other authors' work!
> 
> ## Credits
> 
> ### [samm-git/aws-vpn-client](https://github.com/samm-git/aws-vpn-client)
> 
> Alex Samorukov is the mastermind behind this implementation. He figured out how AWS patches the openvpn client and
> created the first implementations. Be sure to read his [blog](https://smallhacks.wordpress.com/2020/07/08/aws-client-vpn-internals/)
> on for more details.
> 
> ### [botify-labs/aws-vpn-client](https://github.com/botify-labs/aws-vpn-client)
> 
> Botify Labs maintains the `.patch` files for more recent versions of OpenVPN than what are available originally
> in Alex's repository.
>
> ### [kpalang/aws-vpn-client-docker](https://github.com/kpalang/aws-vpn-client-docker)
> Kaur Palang packaged the work of Alex Samorukov and Botify Labs into a Docker container format,
> making OpenVPN compatible with AWS VPN SAML while providing consistent deployment across environments.

---

This fork embeds the OpenVPN profile directly into the Docker image at build time instead of using runtime volume mounts,
avoiding SELinux context conflicts while maintaining security isolation. Tested on Fedora Asahi Linux.

## How to use

### Build the container yourself
1. Clone this repository
2. Download your AWS VPN client profile into a directory
3. Place your AWS VPN client profile (`cvpn-endpoint-*.ovpn`) in the same directory as the Dockerfile, renaming it to `profile.ovpn`
4. Run `docker compose up --build`
5. Authenticate to the login link you can find in the log output of this container
