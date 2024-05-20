# RSA

- It is an asymmetric Key Cipher
- Private Key is used to create unforgeable digital signs
- Public Key is used to authenticate digital signatures

## Steps

1. Choose two large prime number p & q
2. Compute `n = p * q` and `z = (p-1) * (q-1)`
3. Choose number `e` such that ` e < n` and has no common factor other than 1 with z
4. Find `d` such that `(ed - 1)` is exactly divisible by `z`
5. Public key is (n, e) private key is (n, d)
6. `c = m^e mod n` where m is plain text and c is cipher text
7. `m = c^d mod n` where m is decrypted text

# Digital Signature

- Provides Authenitcity, Integrity and Non-repudiation to electronic documents
- Hash the data, and encrypt the message digest with Private Key
- Attach the encrypted digest to the file
- When someone takes the file, hash the file, decrypt digest with public key
- If they match then file is safe, else, it has been tampered
- Bitcoin uses Elliptic Curve Digital Signature Algorithm

## Ensures

- Confidentiality
- Authenticity
- Integrity
- Non-repudiation

# Hash Functions

- Takes data and translates it into a string of letters and numbers
- Data goes into a hash function, function runs, and a string is returned
- In Bitcoin, hashes are 256 bits
- Input can be very short or infinitely long, you'll still get a unique value

## Features

- Takes any input length string
- Produces fixed size output
- Easy to compute
- Impossible to reverse
- Collision resistant
- Hides original string
- No relation between original and final
- Puzzle friendly

## Functions

- MD 5: 128-bit hash
- SHA 1: 160 bit hash
- SHA 256: 256 bit hash used by Bitcoin
- Kaccak 256: 256 bit hash used by Ethereum

## SHA 256

- Pad the message such that message size is 512
- First bit in pad is 1, rest are zeroes
- Append k zero bits where Original Message + 1 + k === 448 mod 512
- Make the remaining 64-bit block the number l in binary
- Total length is divided by 512
- Blocks are processed one at a time
