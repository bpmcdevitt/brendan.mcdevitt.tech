## LDAP
- everything is done in plaintext
- there is a TLS version of it. LDAPS
- port 636

## Windows Active Directory
- tree and forest type of hierarchical design
- For example, the widget.com parent domain (the root of the tree) could
  contain child domains (sales.widget.com, mis.widget.com, partners.widget.com,
  and so on). These domains have twoway transitive trusts, meaning that (for
  example) a user account in one domain in the tree could access resources (an
  application or file server for instance) in another domain. 

### Security Accounts Manager
- database on windows systems up to windows 7 that stored hashed version
  usually ntlm hash of passwords. stored in the registry path:
  %SystemRoot%/system32/config/SAM  

### Naming Strategy
- how will AD namespace integrate with public dns entries?
- consider grouping OU by location & group info

### Group Management
AGDLP (Accounts go into Global groups, which go into Domain Local groups,
which get Permissions)
- domain local - privileges only assigned to members in same domain. Accounts
  or universal and global groups from any trusted domain can be a member of a
  domain local group.
- global - groups can contain only user and global or universal group accounts
  from the same domain but can be used to assign rights to resources in any
  trusted domain (essentially, the opposite of domain local scope). 
- univesal - can contain accounts from any trusted domain and can also be used
  to grant permissions on any object in any trusted domain.
- other groups: security, distribution, system

### Group Policy and Local Security Policy
- password policy: min age, complexity, min length, password history (y/n),
  change pass option, pass expire (y/n)
- account restrictions: time, workstation, # consecutive logins, expiration
  date, disable account, max # incorrect login attempt before lockout

## Secure Network Topologies
topology - a description of how a computer network is physically or logically
organized.

### Subnetting
- useful because traffic that passes through each subnet can be subject to
filtering and access control at the router. 
- also can make it harder to sniff traffic on the network due to it being
  divided. 

### Zones
an area of the network where the security configuration is the same for all
hosts within it.
- Firewalls block traffic based on zones - example zones: intranet, exranet
  (semi-trusted hosts, who must auth with extranet), internet
- Uses ACL
- DMZ - demilitarized zone. traffic cannot pass through.

### Tunneling
VPNs are biggest example. a tunnel is often used as example to describe a VPN's
functionality.

### Switches
- VLAN protocols: VTP (VLAN Trunking Protocol), GARP (Generic Attribute
  Registration Protocol), GVRP (Generic VLAN Registration Protocol)
- Pruning - removing broadcasts related to particular VLANs from a trunk to
  preserve bandwidth
- Vulnerabilities: MAC flooding, ARP poisoning, VLAN hopping: this exploits the
  native VLAN feature of 802.1Q. Native VLANs are designed to provide
  compatibility with non-VLAN capable switches. The attacker (using a device
  placed in the native VLAN) crafts a frame with two VLAN tag headers. The
  first trunk switch to inspect the frame strips the first header and the frame
  gets forwarded to the target VLAN. VTP attacks (attacker masquerades as
  another switch to try to have the configuration replicated to it), Spanning
  Tree Attacks

### Routers
- fault tolerant
- dynamic router protocols: bgp (big isp), opsf - link state algorithm used,
  rip - distance vector algorithm. less efficient than link state algorithm. 
- attacks: fingerprinting, exploits in the OS running the router, spoofed
  routing info, denial of service, arp poisoning, icmp redirect

### Network Address Translation
Types: 
- Static 1:1 mapping made between inside / outside address ip space 
- Dynamic - has pool of addresses. assigns and relases them as needed
- Overloaded
- Destinaton 
- NAPT - assigning ports to internal ip 
- DNAT - destination port forwarding to open up internal port to interwebs

### Firewalls
basic function of a firewall is traffic filtering
- types: packet filtering, stateful, stateful inspection, application aware
devices
- packet filtering: can inspect the headers of ip packets
- packet filtering: block traffic with ip filtering, protocol type, port
  filtering
- stateful inspection: records up to layer 5 (session) layer. Stores state
  information in a statet table
- application aware: records up to layer 7 (application) layer. 

### Proxies and Gateways
- Proxy can be setup as man-in-the-middle to filter traffic or simply monitor
  outbound traffic
- can work as a caching engine to store frequently requested web pages in an
  effort to speed up load times 
- Reverse Proxy - a way to take internal facing applications and make them face
  the public internet

### Implementing a Firewall or Gateway
- Appliance Firewall - uses dedicated hardware 
- Router Firewall - built into router
- Switch Firewall - some layer 3 switches can perform packet filtering
- NOS Firewall - designed to run under a network server
- Application Firewall - software based firewall running on a host
- Personal Firewall - software based firewall only running on a single host

### Web Application Firewall (WAF)
Designed to specifically block threats over https and https

### Web and Security Gateways 
- Designed for corporate control over websites employees visit on a network.
- Is usually implemented via a stand-alone appliance or proxy server software. 
- Can also be used to filter email attachments 

### Intrusion Detection System (IDS) / Network Intrusion Detection Systems
(NIDS)
- will detect an attack and log, usually creating and alerting the
  administrator
- uses an analysis engine: usually with console access. 
- passive in nature: there to be able to alert and notify the administrator of
  the event triggered
- some have active detection: will end the TCP session 

### Intrusion Prevention System (IPS)
Designed to detect an attack, log it, and put a stop to it! Usually by
completely ending the TCP connection and/or session. 

### Unified Threat Management (UTM)
All-in-one merger of roles of NIDS / IDS / IPS / NIPS
usually will be very high end machines capable or accepting lots of traffic and
analyzing it along with signature checking against a database. 

### Host Based IDS (HIDS)
captures information from a single host on a network

### IDS Analysis Engines
- signature based detection or pattern matching. engine is loaded with a DB of
  attack patterns or malware signatures and checks incoming traffic against
  this DB. 
- behavior based detection: engine is trained to first recognize a baseline
  'normal' behavior, and then acts on incoming traffic that deviates from the
  baseline or 'normal' behavior
- anomaly based detection: acts if the engine detects things that are anomolous
  in nature or irregularities occurring in protocols. 

### Wifi Security
- Wardriving - driving around looking for insecure wireless access points
- Warchalking - marking locations with something so you can come back later to
  pwn the wifi network. 
- WEP cracking - aircrack-ng suite of tools can be used to listen to ARP IV's
  since the encryption key is transfered via plaintext. encryption is an rc4
  cipher. 
- WPA2 - AES put in place to encrypt instead of RC4. 
- WPA2 - attacker can get pre-shared encryption key by associating with access
  point. then the attacker will brute force the passphrase using the pre-shared
  encryption key. 
 
### Open Authentication and Captive Portals
open wifi basically an unecrypted open network.
- captive portal: on an open network, making a secondary login usually with
  https via a web browser so clients have to login.
- mac address filtering could work to better secure an open wifi network
- another method to secure: disable dhcp and enforce users connceting to use a static ip
- signal strength: increase / decrease power of wifi antenna based on site-survey for the
  physical space

### IPSEC
- layer 3 
- two core protocols: AH (authentication header), ESP(encapsulation security
  payload). 
- AH will encrypt the IP header in the packet
- ESP will encrypt the entire payload. 
- HMAC-MD5, HMAC-SHA-1, or HMAC-SHA-2 and 3DES or AES (symmetric encryption
  ciphers) are the algorithms typically used by ESP.

#### Internet Key Exchange / ISAKMP
- AH and ESP both depend on a shared secret key that is only known to the two
  hosts
- phase 1: establishes identity of two hosts & key agreement with diffie hellmen key exchange.
- phase 2: diffie-hellmen key agreement establishes shared key used to sign
  packets for msg integrity. diffie-hellmen however does not authenticate the
  endpoints.
- phase 3: authenticatin endpoint kicks in. endpoints are: pki, pre-shared
  key, kerberos

#### Transport and Tunnel Modes
- Transport mode - ip header is not encrypted, only the payload is
- Tunnel mode - entire ip packet. header + payload all encrypted

### Remote Access Hardening
things to look for on servers in regards to hardening: 
- malware protection - is antivirus installed?
- security information - is authentication info stored on the server?
- data transfer - files copied to remote hosts can no longer be secured
- local privileges - sudo users and what not that can escalate privileges
- weak authentication - users that use weak passwds get pwned

## RFC
- [1123](https://tools.ietf.org/html/rfc1123)
- [3022](https://tools.ietf.org/html/rfc3022) NAT
- [1918](https://tools.ietf.org/html/rfc1918) Private IP address classes
- [2637](https://tools.ietf.org/html/rfc2637) PPTP 
- [2661](https://tools.ietf.org/html/rfc2661) L2TP
- [3193](https://tools.ietf.org/html/rfc3193) IPSec in conjuction with L2TP as
  a vpn solution
- [4301](https://tools.ietf.org/html/rfc4301) IPSec 
- [4385](https://tools.ietf.org/html/rfc4385) Algorithms that an implementation
  must adhere to be standards-compliant.
- [1001](https://tools.ietf.org/html/rfc1001) NETBios
- [1002](https://tools.ietf.org/html/rfc1002) NetBios
- [4942](https://tools.ietf.org/html/rfc4942) IPv6 Vulnerabilities

