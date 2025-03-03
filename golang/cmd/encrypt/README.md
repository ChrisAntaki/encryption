# Script to Encrypt Documents for the SwG Encryption Project

This script takes in an input HTML document and encrypts
all content within ```<section subscriptions-section="content" encrypted>```
tags using [AES-GCM](https://en.wikipedia.org/wiki/Galois/Counter_Mode). 
The key used to encrypt the content is added
to the output document's head inside of a
```<script cryptokeys type="application/json">``` element. The encrypted
document is outputted to the output_file path given as a flag.

## Example Usage:

```
go get github.com/subscriptions-project/encryption/golang/cmd/encrypt && \
$GOPATH/bin/encrypt \
    --input_html_file=../tmp/sample-encryption.html \
    --output_file=../tmp/sample-encryption-out.html \
    --access_requirement=thenews.com:premium \
    --encryption_key_url=google.com,https://news.google.com/swg/encryption/keys/{dev|prod}/tink/public_key \
    --encryption_key_url=example.com,www.example.com/scs/publickey \
    --encryption_key_url=thenews.com,www.thenews.com/scs/publickey
```
    
Or...

```
go run encryption/golang/cmd/encrypt/script.go \
    --input_html_file=../tmp/sample-encryption.html \
    --output_file=../tmp/sample-encryption-out.html \
    --access_requirement=thenews.com:premium \
    --encryption_key_url=google.com,https://news.google.com/swg/encryption/keys/{dev|prod}/tink/public_key \
    --encryption_key_url=example.com,www.example.com/scs/publickey \
    --encryption_key_url=thenews.com,www.thenews.com/scs/publickey
```
