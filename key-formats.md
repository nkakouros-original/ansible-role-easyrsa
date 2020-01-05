# Key formats memo

According to [Wikipedia](https://en.wikipedia.org/wiki/PKCS), PKCS is a group of
standards describing, among others, how to store private keys and other
public-key cryptography items. Below, the standards that are relevant for
EasyRSA and this role are listed. The list is not meant to fully cover the
capabilities of each standard, it is only meant as quick reference for a PKI
user.

`key header` below means the human text you see when you open the file with
a text editor.

## Private key storage

Two standards are used to store private keys:

- __PKCS#1__:
  - This is the plain old RSA syntax for storing keys.
  - _key header_:
    - _unencrypted_: `BEGIN RSA PRIVATE KEY`
    - _encrypted_: `BEGIN RSA PRIVATE KEY + encryption info header`
  - _easyrsa commands_:
    - `easyrsa build-ca`
    - `easyrsa export-p1`
  - _openssl commands_:
    - _produce_: `openssl genrsa`
    - _read_: `openssl rsa -in file -text`
- __PKCS#8__:
  - A private key format that, in the key data, also include the key type. The
    key type may be RSA, in which case the PKCS#8 file contains:
    `key-type(RSA) + PKCS#1`
  - _key header_:
    - _unencrypted_: `BEGIN RSA PRIVATE KEY`
    - _encrypted_: `BEGIN RSA PRIVATE KEY`
  - _easyrsa commands_:
    - `easyrsa gen-req`
    - `easyrsa export-p8`
  - _openssl commands_:
    - _produce_: `openssl pkcs8`
    - _read_: `openssl rsa -in file -text`

## Certificate storage

- __X.509__:
  - The classic certificate format.
  - _key header_: `BEGIN CERTIFICATE`
  - _easyrsa commands_:
    - `easyrsa build-ca`
    - `easyrsa gen-req`
  - _openssl commands_:
    - _produce_: `openssl req -x509`
    - _read_: `openssl x509 -in file -text`
- __PKCS#7__:
  - A format to bundle signed/encryppted __data__, usually together with the
    certificate in order to allow verification of the authenticity. Omitting the
    data, leaves just a certificate, making PKCS#7 a way to distribute
    certificates.
  - _key header_: `BEGIN PKCS7`
  - _easyrsa commands_: `easyrsa export-p7`
  - _openssl commands_:
    - _produce_: `openssl crl2pkcs7`
    - _read_: `openssl pkcs7`

## Private key and Certificate Bundles

- __PKCS#12__:
  - Puts together private keys with their corresponding certificates, always
    protected by an, even empty, password.
  - _key header_: -
  - _easyrsa commands_: `easyrsa export-p12`
  - _openssl commands_:
    - _produce_: `openssl pkcs12`
    - _read_: `openssl pkcs12 -info -in file`
