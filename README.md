# role-pivpn-install

An Ansible role to install Wireguard or OpenVPN with [PiVPN](https://github.com/pivpn/pivpn).

## Variables for WireGuard

| Variable                   | Description                                      | Required  |
|----------------------------|--------------------------------------------------|-----------|
| `pivpn_ipv4dev`            | Network interface for IPv4.                      | Yes       |
| `pivpn_ipv6dev`            | Network interface for IPv6.                      | No       
| `pivpn_install_user`       | User account for installation.                   | Yes       |
| `pivpn_vpn`                | VPN technology to use (openvpn or wireguard).    | Yes       |
| `pivpnenableipv6`          | Enable or disable IPv6 (1 for true, 0 for false).| Yes        |
| `pivpn_pivpnNET`           | Private network for the VPN.                     | No        |
| `pivpn_subnetClass`        | Subnet class for the VPN.                        | No        |
| `pivpnforceipv6route`      | Force IPv6 routing (1 for true, 0 for false).    | No        |
| `pivpnforceipv6`           | Force enable IPv6 (1 for true, 0 for false).     | No        |
| `pivpnNETv6`               | Private IPv6 network for the VPN.                | No        |
| `subnetClassv6`            | Subnet class for the IPv6 network.               | No        |
| `ALLOWED_IPS`              | Allowed IP addresses for the VPN.                | No        |
| `pivpnMTU`                 | Maximum Transmission Unit (MTU) for the VPN.     | No        |
| `pivpnPORT`                | Port used by the WireGuard VPN.                  | No        |
| `pivpnDNS1`                | Primary DNS server for the VPN.                  | No        |
| `pivpnDNS2`                | Secondary DNS server for the VPN.                | No        |
| `pivpnHOST`                | IP or domain for the VPN server.           | No        |
| `pivpnPERSISTENTKEEPALIVE`  | Persistent keep-alive interval for WireGuard.    | No        |
| `pivpn_UNATTUPG`           | Enable unattended upgrades (1 for true, 0 for false).| No    |

## Variables for OpenVPN

| Variable                   | Description                                      | Required  |
|----------------------------|--------------------------------------------------|-----------|
| `pivpn_vpn`                | VPN technology to use (openvpn or wireguard).    | Yes       |
| `pivpn_ipv4dev`            | Network interface for IPv4.                      | Yes       |
| `pivpn_ipv6dev`            | Network interface for IPv6.                      | No        |
| `pivpn_pivpnenableipv6`    | Enable or disable IPv6 (0 for false, 1 for true).| Yes       |
| `pivpn_install_user`       | User account for installation.                   | Yes       |
| `pivpn_ipv4addr`           | IPv4 address assigned to the server.             | No        |
| `pivpn_ipv4gw`             | IPv4 gateway address.                            | No        |
| `pivpn_dhcpReserv`         | DHCP reservation flag (0 for false, 1 for true). | No        |
| `pivpn_pivpnNET`           | Private network for the VPN.                     | No        |
| `pivpn_subnetClass`        | Subnet class for the VPN.                        | No        |
| `pivpn_pivpnPROTO`         | Protocol used by the VPN (udp or tcp).           | No        |
| `pivpn_pivpnPORT`          | Port used by the VPN.                            | No        |
| `pivpn_pivpnDNS1`          | Primary DNS server for the VPN.                  | No        |
| `pivpn_pivpnDNS2`          | Secondary DNS server for the VPN.                | No        |
| `pivpn_pivpnHOST`          | IP or domain for the VPN server.           | No        |
| `pivpn_pivpnENCRYPT`       | Encryption key size (e.g., 256).     | No        |
| `pivpn_pivpnSEARCHDOMAIN`  | Search domain for DNS resolution in the VPN.     | No        |
| `pivpn_TWO_POINT_FOUR`     | Use version 2.4 of OpenVPN (1 for true, 0 for false).| No    |
| `pivpn_USE_PREDEFINED_DH_PARAM`| Use predefined Diffie-Hellman parameters (1 for true, 0 for false).| No|
| `pivpn_UNATTUPG`           | Enable unattended upgrades (1 for true, 0 for false).| No    |


# Example Playbook

```yaml
- hosts: target_servers
  roles:
    - role: role-pivpn-install
      become: true
      vars:
        pivpn_vpn: wireguard
        pivpn_IPv4dev: eth0
        pivpn_install_user: admin
        pivpn_pivpnenableipv6: "0"