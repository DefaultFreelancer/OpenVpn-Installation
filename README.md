# openvpn-install

OpenVPN installer for Debian, Ubuntu, Fedora, CentOS and Arch Linux.

This script will let you setup your own secure VPN server in just a few seconds.
<!-- 
You can also check out [wireguard-install](https://github.com/DefaultFreelancer/wireguard-vpn), a simple installer for a simpler, safer, faster and more modern VPN protocol.
 -->
## Usage

First, get the script and make it executable:

```bash
curl -O https://raw.githubusercontent.com/DefaultFreelancer/openvpn-install/master/openvpn-install.sh
chmod +x openvpn-install.sh
```

Then run it:

```sh
./openvpn-install.sh
```

You need to run the script as root and have the TUN module enabled.

The first time you run it, you'll have to follow the assistant and answer a few questions to setup your VPN server.

When OpenVPN is installed, you can run the script again, and you will get the choice to:

- Add a client
- Remove a client
- Uninstall OpenVPN

In your home directory, you will have `.ovpn` files. These are the client configuration files. Download them from your server and connect using your favorite OpenVPN client.

### Headless install

It's also possible to run the script headless, e.g. without waiting for user input, in an automated manner.

Example usage:

```bash
AUTO_INSTALL=y ./openvpn-install.sh

# or

export AUTO_INSTALL=y
./openvpn-install.sh
```

A default set of variables will then be set, by passing the need for user input.

If you want to customise your installation, you can export them or specify them on the same line, as shown above.

- `APPROVE_INSTALL=y`
- `APPROVE_IP=y`
- `IPV6_SUPPORT=n`
- `PORT_CHOICE=1`
- `PROTOCOL_CHOICE=1`
- `DNS=1`
- `COMPRESSION_ENABLED=n`
- `CUSTOMIZE_ENC=n`
- `CLIENT=clientname`
- `PASS=1`

If the server is behind NAT, you can specify its endpoint with the `ENDPOINT` variable. If the endpoint is the public IP address which it is behind, you can use `ENDPOINT=$(curl -4 ifconfig.co)` (the script will default to this). The endpoint can be an IPv4 or a domain.