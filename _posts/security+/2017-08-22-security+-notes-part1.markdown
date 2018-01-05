---
layout: post
title:  "security+ notes p1"
date:  2017-08-22
categories: certifications
---
# Security Threats and Controls

## CIA Triade 
Data needs to be the following:
- Confidentiality 
- Integrity
- Availability



## Security Policy Steps
- obtain support & committment for policy proposed throughout entire org
- analyze risks to security within the org that the policy proposes
- implement controls that detect and prevent losses & procedures that enable
  the org to recover from losses
- review, test, and update procedures continually. continued compliance.



## Security Controls
- National Institute of Standards and Technolog (NIST)
- Federal Information Processing Standards [(FIPS)](http://csrc.nist.gov/publications/PubsFIPS.html)



## Control Types
- Fips 200 (Minimum Security Requirements)
- security control will belong to 1 of 18 families of classes. 
- Access Control, Awareness and Training, Audit and Accountability, Security
  Assessment and Authorization, Configuration Management, Contingency Planning,
  Identification and Authentication, Incident Response, Maintenance, Media
  Protection, Physical and Environmental Protection, Planning, Personnel
  Security, Risk Assessment, Systems and Services Aquisition, System and
  Communications Protection, System and Information Integrity, Program
  Management



## Physical Security Control Types
- Administrative - controls that determine the way people act, including
  policies, procedures, and guidance. 
- Technical - controls implemented in operating systems, software, and hardware
  devices. 
- Preventative -  the control physically or logically restricts unauthorized
  access. A directive can be thought of as an administrative version of a
  preventive control. 
- Deterrent - the control may not physically or logically prevent access, but
  psychologically discourages an attacker from attempting an intrusion.
- Detective - the control may not prevent or deter access, but it will identify
  and record any attempted or successful intrusion. 
- Corrective - the control responds to and fixes an incident and may also
  prevent its reoccurrence. 
- Compensating - the control does not prevent the attack but restores the
  function of the system through some other means, such as using data backup or
  an alternative site. 



## Access Control and ACL 
- Identification
- Authentication
- Authorization
- Accounting



## Formal Access Control Models
- DAC - Discretionary Access Control - The owner is granted full control over
  the resource, meaning that s/he can modify its ACL to grant rights to others. 
- RBAC - Rule Based Access Control - Under RBAC, a set of organizational roles
  are defined and users allocated to those roles. 
- MAC - Mandatory Access Control - based on the idea of security clearance
  levels. Rather than defining access control lists on resources, each object
  and each subject is granted a clearance level (referred to as a label). 


# Crypto:

## Bit length of hashing algorithm 
 - sha-1, 160 bits
 - sha-2, up to 512 bits
 - md5, 128 bits
 - ripemd-160 - 160 bits



##  Stream ciphers and block ciphers
 - 3DES / Triple DES - block cipher - 56 bit key - 64 bit blocks
 - AES / AES25 - block cipher - 128 bit block size, variable key length 
 - RC4 stream cipher - from 40 to 128 bits, variable length key - used in SSL / WEP 
 - Blowfish - 64 bits, variable length key
 - Twofish - 128 bits, variable length key 
 - RSA - finds prime factors of large sets of number. variable key size. 2048
   key size ( 2048 / 8 ) - 11
 - DSA (Digital Signature Algorithm) 


## Asymmetric vs Symmetric encryption
### Asymmetric 
 - uses pki. two keys, one key is needed to encrypt & decrypt the other
 - public key, private key 
### Symmetric 
 - uses the same key for encryption & decryption

## PKI (Public Key Infrastructure)
Three main elements to a PKI:
- Organization
- Servers
- Client

## Key Management
Stages of a key lifecycle. Key mgmt can either be centralized(admin controls
all of it) or decentralized(each user controls own keys).
- Key Generation
- Certificate Generation
- Distribution
- Storage
- Revocation
- Expiration

## Public Key Crypto Standards
- PKCS #1 - defines the properties of public/private key pairs and the
  algorithms for RSA encryption. 
- PKCS #3 - defines Diffie-Hellman key agreeement.
- PKCS #6 - the original (v1) standard for X.509 certificates. As noted above,
  the latest X.509 v3 standard is published as RFC 5280 . 
- PKCS #7 - provides the basis for S/MIME (Secure Multipart Internet Mail
  Extensions), allowing users to sign and encrypt email messages using digital
  certificates. S/MIME is published as the Cryptographic Message Standard (CMS)
  in RFC 5652 . 
- PKCS #10 - format for requests certificates from a CA

## RFCS
- [2104](https://tools.ietf.org/html/rfc2104) hashbased message authentication code (HMAC)
- [5280](https://tools.ietf.org/html/rfc5280) x.509 public key infrastructure
- [2527](https://tools.ietf.org/html/rfc2527) certificate policies
- [4880](https://tools.ietf.org/html/rfc4880) pretty good privacy (pgp)
- [5280](https://tools.ietf.org/html/rfc5280) 
- [5652](https://tools.ietf.org/html/rfc5652)
- [4120](https://tools.ietf.org/html/rfc4120) kerberos
- [1334](https://tools.ietf.org/html/rfc1334) PAP - password authentication protocol
- [1994](https://tools.ietf.org/html/rfc1994) CHAP - challenge handshake authentication protocol
- [4226](https://tools.ietf.org/html/rfc4226) HOTP - HMAC based one-time password algorithm
- [6238](https://tools.ietf.org/html/rfc6238) TOTP - Timebased one-time password algorithm
- [3748](https://tools.ietf.org/html/rfc3748) EAP - Extensible Authentication Protocol
- [5216](https://tools.ietf.org/html/rfc5216) EAP-TLS 
- [2865](https://tools.ietf.org/html/rfc2865) RADIUS - Remote Authentication Dial-in User Service

## FIPS - Federal Information Processing Standards
- FIPS 180
- FIPS 198 
- FIPS 186
- FIPS 140
- FIPS 201

## Suite B
Suite B is a set of cryptographic algorithms mandated by the National Security
Agency (NSA) for use by US government agencies. Suite A is an unpublished list
of classified algorithms. 
- Encryption AES-128 & AES-256
- Digital Signature - ECDSA with 256 and 384 bit keys
- Key Exchange - Diffie Hellman with 256 and 384 bit keys
- Cryptographic Hash - SHA-256 and SHA-384
