---
layout: post
title:  "security+ notes p3"
date:  2017-08-24
categories: certifications
---

## Host Security
- Common Criteria (CC)
- Security Target (ST)
- baseline: snapshot of the typical activity on your network on any given host.

### OS Hardening 
- Windows: Group Policy, Local Security Policy
- Unix: SystemV (AT&T), BSD (All the BSDS YES!) 
- Linux: Many distributions. 
- Patch Management - make sure you patch your shit yo
- Windows: Windows update to update the OS
- Linux/Unix: System package manager or recompile packages based on needs
- Hotfixes: specific customer request for a piece of software to be fixed.
  Usuaully hurried in nature. 
- Windows: Service packs 
- Windows Update Services: basically an update server that works like a proxy
  server. you can centralize and speed up windows updates times in your organization
- Firmware Updates: you have seen examples via IPMI updates on servers. Routers
  / Switches very important to have latest firmware updates applied. 
- Driver updates: Make sure all the crapp windows software has been updated to
  latest drivers. linux will take care via the pkg manager.
- Endpoint Security: If they can't get to your individual hardended server
  because you have something like a firewall setup at your network endpoint,
  then you are doing it right! 
- Physical Security: Access to USB port / network ports on servers, switches, routers 
- Mac Filtering: Specifying which MAC addresses are allowed to connect to a
  specific network port. 
- PNAC (Port Based Network Access Control) - performs some sort of
  authentication of the attached device before activating the port. 
- EAPoL (Extensible Authentication Protocol over LAN) - authenticating devices
  using EAP or with PKI to pass authentication portion over to a RADIUS server.
  RADIUS server will check creds and give access denied or allow access. If
  access granted, switch will enable the VLAN tag that the port is setup with
  to enable network access. 

### Data Security
- data policy: describes the security controls that will be applied to protect
  data at each stage of its lifecycle. 
- information classification and access control: unclassified (public) data,
  classified (private/restricted) data, confidential aka highly sensitive data,
  secret data, top-secret. 
- classified, confidential, secret, and top-secret should be encrypted
- publication and distribution: storage and retrieval, distribution - what
  restrictions are there on making copies of the data, security - what is the
  security process if the document is compromised 
- data states: data at rest, data in-transit, data in-use 
- retention, storage, and destruction: retention aka archiving the data,
  destruction aka destroying the data

### Personally Identifiable Information (PII)
Protect yourself from identity theft yo, limit the use of PII! 
- PII - data that can be used to identify, contact, or locate an individual (or
  in the case of identity theft, to impersonate them).
- Examples: tattoos, social security number, usernames, passwords, email
  addresses, dobs, cc #

### Data Encryption
Encrypt all the things
- file / folder encryption - many different filesystems that support
  encryption, efs and luks are some examples
- disk encryption: BitLocker, TrueCrypt(discontinued), Symantec Drive
  Encryption
- Hardware based encryption: TPM (Trusted Platform Module) - a little piece of
  hardware that stores the encryption key on it. starting to also be hardware
  based solutions that are meant to be installed as add-ons to bring load away
  from CPU. 
- Removable media encryption: usb devices, yubikeys, many different kinds. 
- Database encryption: most of the time it is better to encrypt files on the
  disk. encryption usually done at the column level so this is very CPU
  intensive. 

### Data Loss Prevention
Dont lose that data!
- a database that identifies confidential data that should not be lost. 
- requires the following components: policy server - to configure
  confidentiality ruleset, endpoint agents - to enforce policy on client
  computers, network
  agents - scan communications at network borders and interface with web and
  messaging servers to enforce policy.
- rights management services: assigns file permissions based on different
  document roles(such as author, editor, or reviewer). Restrict printing and
  forwarding of documents, event when sent as file attachments, Restrict
  printing and forwarding of email documents. 

### Big Data
The new buzzword to throw around in todays IT world
- big data: an unstructured database set, usually setup into some sort of
  database management system.

### Backup Plans and Policies
Do you have backups of your backups? 
- backup types: full, incremental, differential 
- keep your stuff backed up versionally - use version control, stupid. 
- snapshots - meant to keep copies of open files, zfs, btrfs filesystems have
  this feature built-in to the filesystem. 
- tapes: tapes are mainly used for archiving purposes. they use an autoloader
  to preload tapes. tapes are rotated. a good rotation policy - monthly,
  weekly, daily. 
- is there an offsite backup solution in place? 
- make you sure that you are testing backups to make sure you can restore
  everything from them 
