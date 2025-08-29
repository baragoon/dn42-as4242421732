# DN42 AS4242421732 - BGP Peers
Welcome to the official [repository](https://github.com/baragoon/dn42-as4242421732) for DN42 AS4242421732! This repository contains details about the BGP peering configuration for this Autonomous System within the DN42 network.

DN42 is a virtual private network (VPN) connecting enthusiasts and professionals globally. It is designed to be a testing and development environment for networking, BGP, and related technologies.

## How to Use

This section provides detailed instructions for setting up BGP peering with AS4242421732, viewing current peerings, and contributing updates to the repository.
Nodes information including IPs, WireGuard info can be found [**here**](https://as215887.net/dn42)
### 1. Clone the Repository
```
git clone https://github.com/baragoon/dn42-as4242421732.git
cd dn42-as4242421732
```
This will download the repository to your local machine and navigate into the repository directory.
### 2. Review Existing Peerings
The repository contains a files called $location.yaml, which lists all the current BGP peerings and WireGuard tunnels for AS4242421732 nodes.
```
amsterdam.yaml
frankfurt.yaml
kansas.yaml
london.yaml
lviv.yaml
new-york.yaml
toronto.yaml
zurich.yaml
```
### 3. Add New Peer
To add a new peering with AS4242421732, follow these steps:
1. Edit the desired location file: Add your new peering information (name, IPv4, IPv6 (link-local or dn42 IPv6), AS number, session type, WireGuard data, email/other contact).

> [!IMPORTANT]
> **If you're using WireGuard preshared key**
> Add ```preshared_key``` to the WireGuard section:
```
    wireguard:
      endpoint_address: '1.1.1.1'
      endpoint_port: '15887'
      preshared_key: 'oTpSP6Hr4/bGtnJJu/xrcqtiVA0c+Ql9yv7yGYGE1t0='
      public_key: 'yZO+2Fo7uHikVC2VUPYwkk9IBzojUqrJlTU2fyfzfgI='
```

#### Example BGP Configuration for Multi-prototol session:
```
  - name: 'fr1.g-load.eu'
    contacts: 'https://dn42.g-load.eu'
    wireguard:
      endpoint_address: 'fr1.g-load.eu'
      endpoint_port: '21732'
      public_key: 'sLbzTRr2gfLFb24NPzDOpy8j09Y6zI+a7NkeVMdVSR8='
    address:
      ipv6: 'fe80::ade0'
      ipv4: '172.20.53.102'
    bgp:
      asn: '4242423914'
      session: 'mp'
```
> [!IMPORTANT]
> **BGP enhanced next hop is enabled by default for MP sessions**. If you wish not to use it, set "enhe: 'no'" for the BGP part like this:

```
    bgp:
      asn: '4242423914'
      session: 'mp'
      enhe: 'no'
```
#### Example BGP Configuration for IPv6 only session:
```
  - name: 'fr1.g-load.eu'
    contacts: 'https://dn42.g-load.eu'
    wireguard:
      endpoint_address: 'fr1.g-load.eu'
      endpoint_port: '21732'
      public_key: 'sLbzTRr2gfLFb24NPzDOpy8j09Y6zI+a7NkeVMdVSR8='
    address:
      ipv6: 'fe80::ade0'
    bgp:
      asn: '4242423914'
      session: 'ipv6'
```
#### Example BGP Configuration for IPv4 only session:
```
  - name: 'fr1.g-load.eu'
    contacts: 'https://dn42.g-load.eu'
    wireguard:
      endpoint_address: 'fr1.g-load.eu'
      endpoint_port: '21732'
      public_key: 'sLbzTRr2gfLFb24NPzDOpy8j09Y6zI+a7NkeVMdVSR8='
    address:
      ipv4: '172.20.53.102'
    bgp:
      asn: '4242423914'
      session: 'ipv4'
```
#### Example BGP Configuration for two separate IPv4 & IPv6 sessions:
```
  - name: 'fr1.g-load.eu'
    contacts: 'https://dn42.g-load.eu'
    wireguard:
      endpoint_address: 'fr1.g-load.eu'
      endpoint_port: '21732'
      public_key: 'sLbzTRr2gfLFb24NPzDOpy8j09Y6zI+a7NkeVMdVSR8='
    address:
      ipv6: 'fe80::ade0'
      ipv4: '172.20.53.102'
    bgp:
      asn: '4242423914'
      session: 'ipv4+ipv6'
```

2. Push Changes: After you've added the new peer configuration, you can commit your changes to your local copy of the repository:
```
git add .
git commit -m "Added peering with $your_peer_name"
```
Then push your changes to GitHub (you must fork the repository first if you haven't):
```
git push origin main
```
Once approved and merged, we automatically distribute your configuration to the routers in our network. Please allow some time (up to 5 minutes) for the process to complete.
### 4. How to Remove a Peering
#### WIP...

