# Symmetric Encryption, AES, ECB, GCM, ChaCha20

## Symmetric Encryption

Symmetric Encryption: A method of encryption where the same secret key is used to both encrypt and decrypt data.

Use: Used to protect sensitive data during communication and storage so only trusted users can read it.

Example: WhatsApp messages, HTTPS websites, VPN connections.

---------------------------------------------------------

## AES (Advanced Encryption Standard)

AES: A strong symmetric encryption algorithm that converts readable data into secure unreadable ciphertext using a secret key.

Use: Used in banking systems, secure websites, cloud storage, VPNs, and file encryption.

Example: Online banking login and HTTPS secure connections use AES to protect data.

---------------------------------------------------------

## ECB (Electronic Codebook Mode)

ECB: A basic mode of AES where each block of data is encrypted separately using the same key.

Use: Not used in secure systems due to weak security.

Example: If an image is encrypted with ECB, patterns from the original image can still be seen.

Security Note: Same input block always produces same output → leaks patterns → insecure.

---------------------------------------------------------

## GCM (Galois/Counter Mode)

GCM: A modern AES mode that provides both encryption and integrity protection (checks if data is modified).

Use: Used in HTTPS, APIs, VPNs, cloud systems, and modern secure communication.

Example: Modern websites use AES-GCM to ensure data is encrypted and not tampered with during transmission.

Security Note: Very secure and widely used in real-world systems.

---------------------------------------------------------

## ChaCha20

ChaCha20: A modern symmetric stream cipher that encrypts data using a fast generated key stream.

Use: Used in mobile devices, VPNs, messaging apps, and modern internet protocols.

Example: Modern browsers and apps use ChaCha20 for fast and secure encrypted communication.

Security Note: Fast, secure, and efficient alternative to AES in performance-sensitive systems.

#########################################################################################################

# Asymmetric Encryption: RSA, ECDSA, Ed25519

## Asymmetric Encryption

Asymmetric Encryption: A method where two different keys are used: a public key and a private key.

- Public key → used to encrypt or verify
- Private key → used to decrypt or sign

Use: Used to secure communication, verify identity, and enable secure key exchange over the internet.

Example: HTTPS websites, SSH login, digital signatures.

---------------------------------------------------------

## RSA

RSA: A classic asymmetric encryption algorithm based on large prime number factorization.

Use: Used for secure data encryption, key exchange, and digital certificates.

Example: When you visit a secure website (HTTPS), RSA may be used during key exchange.

Security Note: Very secure but slower compared to modern algorithms.

---------------------------------------------------------

## ECDSA (Elliptic Curve Digital Signature Algorithm)

ECDSA: A digital signature algorithm based on elliptic curve cryptography.

Use: Used to verify data authenticity and identity without sending the private key.

Example: Bitcoin transactions use ECDSA to prove ownership of coins.

Security Note: Stronger security with smaller key size compared to RSA.

---------------------------------------------------------

## Ed25519

Ed25519: A modern, fast, and secure digital signature algorithm based on elliptic curve cryptography.

Use: Used in SSH keys, secure software signing, and modern authentication systems.

Example: SSH login keys often use Ed25519 for fast and secure authentication.

Security Note: Very fast, highly secure, and resistant to many attack types.

#########################################################################################################

# Hash Functions: SHA-256/3, bcrypt, Argon2, Rainbow Tables

## Hash Functions

Hash Function:A process that converts input data into a fixed-size string called a hash.

Important property: Hashing is one-way → you cannot reverse it back to original data.

Use: Used for password storage, data integrity, digital signatures, and file verification.

Example: When you set a password, websites store the hash instead of the real password.

---------------------------------------------------------

## SHA-256 / SHA-3

SHA-256 / SHA-3: Cryptographic hash algorithms that generate a fixed-length hash from any input.

Use: Used for data integrity checks, blockchain, digital signatures, and file verification.

Example: Bitcoin uses SHA-256 to secure transactions.

Security Note: Fast and secure for integrity, but NOT safe for password storage alone.

---------------------------------------------------------

## bcrypt

bcrypt: A password hashing function designed to be slow and resistant to brute-force attacks.

Use: Used for securely storing passwords in databases.

Example: Websites store your password as bcrypt hash instead of plain text.

Security Note: Slow by design → makes brute-force attacks difficult.

---------------------------------------------------------

## Argon2

Argon2: A modern password hashing algorithm that is memory-hard and highly secure.

Use: Used for secure password storage in modern applications.

Example: Security systems and modern apps use Argon2 to protect user passwords.

Security Note: Stronger than bcrypt and resistant to GPU/ASIC attacks.

---------------------------------------------------------

## Rainbow Tables

Rainbow Tables: Precomputed tables of hashes used to reverse weak password hashes.

Use (Attacker side): Used to crack weak or unsalted password hashes quickly.

Example: If a password is simple like “123456”, attackers may find its hash in a rainbow table.

Security Note: Salted and strong hashes (bcrypt/Argon2) prevent rainbow table attacks.

---------------------------------------------------------

## Salting

Salting: Adding random data (salt) to a password before hashing it.

Use: Prevents identical passwords from producing identical hashes.

Example: password + salt → hash

Security Note: Protects against rainbow table attacks.

---------------------------------------------------------

## Hashing vs Encryption

Hashing:
- One-way process
- Cannot be reversed
- Used for passwords

Encryption:
- Two-way process
- Can be decrypted with a key
- Used for communication

---------------------------------------------------------

## Hash Attacks
- Brute Force Attack: Trying all possible passwords
- Dictionary Attack: Using common password lists
- Rainbow Table Attack: Using precomputed hashes

#########################################################################################################

# HMAC and Authenticated Encryption

## HMAC (Hash-based Message Authentication Code)

HMAC: A method that uses a cryptographic hash function along with a secret key to ensure data integrity and authenticity.

Use: Used to verify that data is not modified and comes from a trusted sender.

How it works: Data is combined with a secret key and processed through a hash function (like SHA-256). The receiver repeats the same process and compares results. If they match, data is valid.

Example: API authentication, secure service-to-service communication.

---------------------------------------------------------

## MAC (Basic Concept)

MAC: A general method used to verify data integrity and authenticity using a shared secret key.

Note: HMAC is a specific type of MAC that uses hash functions.

---------------------------------------------------------

## Authenticated Encryption (AEAD)

Authenticated Encryption: A cryptographic method that provides both encryption (confidentiality) and authentication (integrity) in a single system.

Use: Used to protect data from being read or modified by attackers.

How it works: Data is encrypted and an authentication tag is generated together. If data is changed, verification fails.

Example: HTTPS (TLS using AES-GCM or ChaCha20-Poly1305), secure messaging apps.

---------------------------------------------------------

## AEAD (Authenticated Encryption with Associated Data)

AEAD: An advanced form of authenticated encryption that also protects additional data (like headers) without encrypting them.

Examples: AES-GCM, ChaCha20-Poly1305.

---------------------------------------------------------

## Attack Protection
- Prevents data tampering
- Prevents impersonation
- Helps protect against replay attacks (with nonce/IV usage)

#########################################################################################################

# PKI (Public Key Infrastructure): Certificates, CAs, Chain of Trust, CRL, OCSP

## PKI (Public Key Infrastructure)

PKI: A system that manages digital certificates and public-key encryption to verify identities and secure communication over the internet.

Use: Used to ensure secure and trusted communication between clients and servers (like HTTPS).

How it works: A trusted authority issues a digital certificate that binds a public key with an identity (like a domain name).

Example: HTTPS websites use PKI to prove they are legitimate and secure.

---------------------------------------------------------

## Digital Certificates

Certificates: Digital documents that contain a public key, identity information, and are signed by a Certificate Authority.

Use: Used to verify that a website or service is authentic.

How it works: When you visit a website, your browser checks its certificate to ensure it is valid and trusted.

---------------------------------------------------------

## CA (Certificate Authority)

CA: A trusted organization that issues and signs digital certificates.

Use: Acts as a trusted identity verifier for websites and organizations.

Example: Let’s Encrypt, DigiCert.

---------------------------------------------------------

## Chain of Trust

Chain of Trust: A hierarchy of trust starting from Root CA → Intermediate CA → End Entity Certificate.

Use: Ensures every certificate can be traced back to a trusted root authority.

How it works: Browser trusts Root CA → Root CA trusts Intermediate CA → Intermediate CA signs website certificate.

---------------------------------------------------------

## Root CA (Trust Anchor)

Root CA: The highest level of trust already built into browsers and operating systems.

Use: Acts as the starting point of trust for all certificates.

---------------------------------------------------------

## Self-Signed Certificates

Self-Signed Certificate: A certificate signed by its own creator instead of a CA.

Use: Used in testing, development, or internal systems.

Security Note: Not trusted by browsers by default.

---------------------------------------------------------

## CRL (Certificate Revocation List)

CRL: A list of certificates that have been revoked before expiration.

Use: Blocks compromised or invalid certificates.

Example: If a private key is stolen, the certificate is added to CRL.

---------------------------------------------------------

## OCSP (Online Certificate Status Protocol)

OCSP: A real-time protocol used to check whether a certificate is valid or revoked.

Use: Faster and more efficient alternative to CRL.

How it works: Browser asks OCSP server → receives certificate status (valid/revoked).

---------------------------------------------------------

## Certificate Fields

A certificate typically contains:
- Public key
- Domain name (CN / SAN)
- Issuer (CA information)
- Expiry date
- Digital signature

---------------------------------------------------------

## TLS Integration (Real-World Flow)

PKI is used in TLS/HTTPS:
- Server sends certificate
- Browser verifies it using CA chain
- Secure session key is generated
- Encrypted communication starts

#########################################################################################################

# TLS 1.3: Cipher Suites & Certificate Pinning

## TLS 1.3 (Transport Layer Security)

TLS 1.3: The latest major version of the TLS protocol used to secure communication over the internet.

Use: Used to protect data exchanged between clients and servers by providing encryption, integrity, and authentication.

How it works: The client and server perform a TLS handshake, verify certificates, securely exchange keys, and then use symmetric encryption for communication.

Example: HTTPS websites, online banking, cloud services, APIs.

---------------------------------------------------------

## TLS Handshake

TLS Handshake: The process used to establish a secure connection before any data is exchanged.

Use: Used to verify identity and create shared encryption keys.

How it works:
- Client connects to server
- Server sends certificate
- Client verifies certificate
- Secure session keys are generated
- Encrypted communication begins

Example: Opening a secure HTTPS website in a browser.

---------------------------------------------------------

## Cipher Suite

Cipher Suite: A collection of cryptographic algorithms used by TLS to secure a connection.

Use: Defines how key exchange, encryption, and integrity protection are performed.

TLS 1.3 Cipher Suites:
- TLS_AES_128_GCM_SHA256
- TLS_AES_256_GCM_SHA384
- TLS_CHACHA20_POLY1305_SHA256

Components:
- AES-GCM or ChaCha20-Poly1305 → Encryption
- SHA-256 / SHA-384 → Integrity and handshake security

Example: A browser and server may agree to use TLS_AES_128_GCM_SHA256 during a TLS handshake.

---------------------------------------------------------

## AES-GCM

AES-GCM: An authenticated encryption algorithm used in TLS 1.3.

Use: Provides both encryption and integrity protection.

Security Note: One of the most common algorithms used in HTTPS today.

---------------------------------------------------------

## ChaCha20-Poly1305

ChaCha20-Poly1305: An authenticated encryption algorithm combining ChaCha20 encryption and Poly1305 authentication.

Use: Used as a fast alternative to AES-GCM, especially on devices without AES hardware acceleration.

Example: Mobile devices and modern browsers often use ChaCha20-Poly1305.

---------------------------------------------------------

## Certificate Pinning

Certificate Pinning: A security technique where an application trusts only a specific certificate or public key instead of any trusted CA.

Use: Used to reduce the risk of man-in-the-middle attacks.

How it works: The application stores an expected certificate or public key and compares it against the server's certificate during connection.

Example: Mobile banking applications may pin a server's public key.

Security Note: Even if a CA is compromised, a pinned certificate can prevent attackers from presenting fake certificates.

---------------------------------------------------------

## Benefits of TLS 1.3
- Faster handshake
- Stronger security
- Fewer outdated algorithms
- Forward secrecy by default
- Reduced attack surface

#########################################################################################################

# Common Cryptographic Failures: Weak Keys, IV Reuse, Padding Oracles, and More

## Weak Keys

Weak Keys: Encryption keys that are short, predictable, reused, or generated from poor randomness.

Use (Attacker Perspective): Attackers can guess or brute-force weak keys more easily.

How it happens: Using simple passwords, weak random number generators, or hardcoded keys.

Example: Using 123456 or password as an encryption key.

Security Risk: Weak keys can completely break encryption.

---------------------------------------------------------

## IV Reuse (Initialization Vector Reuse)

IV Reuse: Using the same Initialization Vector (IV) multiple times with the same encryption key.

Use: IVs are meant to add randomness to encryption.

How it happens: Developers reuse the same IV instead of generating a new random one.

Example: Encrypting multiple messages with the same AES key and IV.

Security Risk: Can reveal patterns and, in some cases, expose encrypted data.

---------------------------------------------------------

## Padding Oracle Attack

Padding Oracle Attack: An attack that exploits error messages from improperly implemented encryption systems.

Use (Attacker Perspective): Used to gradually decrypt encrypted data without knowing the key.

How it works: The attacker modifies ciphertext and observes server responses to learn information about the plaintext.

Example: Older web applications using vulnerable CBC-mode encryption.

Security Risk: Can allow attackers to recover sensitive encrypted information.

---------------------------------------------------------

## Hardcoded Keys

Hardcoded Keys: Encryption keys stored directly inside application source code.

How it happens: Developers place keys in scripts, applications, or configuration files.

Example: An API key or encryption key embedded in a mobile application.

Security Risk: Anyone who obtains the code can obtain the key.

---------------------------------------------------------

## Poor Random Number Generation

Poor Randomness: Using predictable values when generating cryptographic keys, IVs, or nonces.

Example: Generating keys based only on current time.

Security Risk: Attackers may predict secret values and break security.

---------------------------------------------------------

## Using Outdated Algorithms

Outdated Algorithms: Using cryptographic algorithms that are no longer considered secure.

Examples:
- DES
- MD5
- SHA-1
- RC4

Security Risk: Known weaknesses can allow attackers to bypass security.

---------------------------------------------------------

## Missing Authentication

Missing Authentication: Encrypting data without verifying its integrity.

How it happens: Using encryption alone instead of authenticated encryption (AEAD).

Example: Using AES-CBC without integrity protection.

Security Risk: Attackers may modify encrypted data without detection.

---------------------------------------------------------

## Insecure Certificate Validation

Insecure Certificate Validation: Failing to properly verify certificates during TLS connections.

Example: Ignoring certificate warnings or accepting any certificate.

Security Risk: Can enable Man-in-the-Middle (MITM) attacks.

---------------------------------------------------------

## Key Reuse

Key Reuse: Using the same encryption key for multiple purposes or for a long period of time.

Example: Using one key for all users in an application.

Security Risk: A single key compromise can expose large amounts of data.

#########################################################################################################



