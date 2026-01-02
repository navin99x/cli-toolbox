# GNU Privacy Guard (GPG)

## Key Management

```bash
# generate new key pair
gpg --full-generate-key

# list keys
gpg --list-keys  # public keys
gpg --list-secret-keys  # private keys

# delete keys
gpg --delete-key email@example.com  # public key
gpg --delete-secret-key email@example.com  # private key

# export key
gpg --armor --export email@example.com  # public key
gpg --armor --export-secret-key email@example.com  # private key

# import someone's public key
gpg --import pubkey.asc
```

---

## Symmetric Encryption/Decryption

```bash
# Encryption
gpg --symmetric file.txt  # Outputs: file.txt.gpg

# Decryption
gpg file.txt.gpg
```

---

## Asymmetric Encryption/Decryption

```bash
# encrypt a file for someone (binary output)
gpg --encrypt -r email@example.com file.txt  # Outputs: file.txt.gpg

# encrypt with ASCII-armored output
gpg --armor --encrypt -r email@example.com file.txt  # Outputs: file.txt.asc

# decrypt file sent to you (works for .gpg or .asc)
gpg --decrypt file.txt.gpg
```

---

## Signing

```bash
# sign a file (creates signed binary)
gpg --sign file.txt  # Outputs: file.txt.gpg

# create detached signature
gpg --detach-sign file.txt  # Outputs: file.txt.sig

# verify a signature (for detached .sig or signed .gpg)
gpg --verify file.txt.sig file.txt  # For detached
gpg --verify file.txt.gpg  # For signed file

# clear signed file (extract original from signed binary)
gpg --decrypt file.txt.gpg > original.txt
```

## Key Servers

```bash
# search for a public key
gpg --keyserver keys.openpgp.org --search-keys email@example.com

# import key from server
gpg --keyserver keys.openpgp.org --recv-keys KEYID
```