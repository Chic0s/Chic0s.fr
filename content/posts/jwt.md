---
title: "Jwt Token"
date: 2023-12-03T21:23:42+01:00
draft: false
categories: "Web"
tags: ["pentest", "web", "jwt"]
---
# What is JWT Token ? 

A JSON Web Token (JWT) consists of three parts separated by periods (`.`): the header, the payload, and the signature. Each part is Base64-encoded.

## **Example JWT:**

1. **Header:**

```json
{
	 "alg": "HS256",
	 "typ": "JWT" 
}
```

Encoded in Base64, the header becomes: `eyJhbGciOiAiSFMyNTYiLCAidHlwIjogIkpXVCJ9`

2. **Payload:**

 ```json
 {
	"sub": "1234567890",
	"name": "John Doe",
	"iat": 1516239022 
 }
 ```

Encoded in Base64, the payload becomes:  
```css
eyJzdWIiOiAiMTIzNDU2Nzg5MCIsICJuYW1lIjogIkpvaG4gRG9lIiwgICJpYXQiOiAxNTE2MjM5MDIyfQ
 ```
3. **Signature:** The signature is generated using the algorithm specified in the header (here, "HS256"). It is created by taking the concatenation of the encoded header, the encoded payload, and a secret key, and then applying the signature algorithm.

The signature depends on the secret key and the token's content, ensuring the token's integrity. In this example, the signature is not provided, but in a real context, it would be added after Base64 encoding.


**Complete JWT:**

```css
eyJhbGciOiAiSFMyNTYiLCAidHlwIjogIkpXVCJ9.eyJzdWIiOiAiMTIzNDU2Nzg5MCIsICJuYW1lIjogIkpvaG4gRG9lIiwgICJpYXQiOiAxNTE2MjM5MDIyfQ.
```
The signature is generated by taking the concatenation of the encoded header, the encoded payload, and a secret key, then applying the signature algorithm. Note that in a real context, the signature would be added after Base64 encoding the signature.

## Algorithm :

The algorithms used in JSON Web Tokens (JWT) determine how the token's signature is generated. Here's an explanation of some commonly used algorithms:

1. **HS256 (HMAC SHA-256):**
   - This algorithm uses a shared secret key between the issuer and the recipient.
   - The signature is generated using the SHA-256 hash function.

2. **RS256 (RSA Signature with SHA-256):**
   - This algorithm uses a public-private key pair based on RSA.
   - The issuer signs the token with the private key, and the recipient verifies the signature using the public key.

3. **ES256 (ECDSA using P-256 curve and SHA-256):**
   - This algorithm uses elliptic curves for asymmetric cryptography.
   - Similar to RS256, it uses a public-private key pair but with different mathematical properties.

4. **PS256 (RSA-PSS Signature with SHA-256):**
   - A variant of RS256 that uses the RSA-PSS signature scheme, providing enhanced security properties compared to simple RSA.

5. **None:**
   - Indicates that the JWT is not signed. This is generally not recommended in production as it makes the token insecure.

Each algorithm has its own advantages and use cases. Asymmetric algorithms like RS256 are often used in scenarios where the issuer and recipient may have different keys, while symmetric algorithms like HS256 are used when both parties share a common secret key. The choice of algorithm depends on the specific security requirements of the application and system.


## How to edit JWT Token 

#### You can use https://jwt.io 

  
*JWT.io is an online platform for JSON Web Tokens (JWT). It provides an interactive decoder for visualizing and analyzing JWTs, decoding headers and payloads, and verifying signatures. It's a handy tool for developers working with JWTs in authentication and authorization scenarios.*

![targets](/img/jwtio.png)

#### You can use Burpsuite extension 

#### JWT Editor

![targets](/img/ext_jwt.png)


You can use the Burp Suite extension called "JWT Editor" to manipulate JSON Web Tokens (JWTs) in your requests. For instance, you have the ability to create a new RSA key and directly edit the token within the request.

![targets](/img/ext_request.png)


Upon selecting the key, you are presented with options to perform various actions such as:

- **Attack**: This includes different types of attacks to test the JWT's security.
- **Sign**: You can sign the JWT with a private key.
- **Encrypt**: Options for encrypting the JWT.

Under the "Attack" category, there are several techniques you can employ:

- **Embedded JWT**: Imagine you have a secret note (JWT) hidden within another note. The system should be smart enough to find and validate the hidden note.

- **"none" Signing Algorithm**: In the world of secret codes (JWTs), using "none" as the code to seal a note isn't secure. It's like having a lock that anyone can open without a key.

- **HMAC Key Confusion**: If you have multiple keys to open a lock, confusion might arise. The system should be smart enough to use the correct key.

- **Sign with Empty Key**: Signing a note with an invisible key doesn’t make sense. The system should recognize this and not trust notes signed with an empty key.

- **Sign with Psychic Signature**: If someone claims to predict the future, the system should be skeptical. It's like making sure a fortune teller is reliable before believing their predictions.
- **Embed Collaborator Payload**: Imagine sending a secret message that includes a friend's contact information. If the system leaks this information, it's like accidentally revealing your friend's details.


More ressources : 
- https://book.hacktricks.xyz/pentesting-web/hacking-jwt-json-web-tokens
- https://portswigger.net/web-security/jwt