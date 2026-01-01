# age — Simple, Modern & Secure File Encryption

> 🔐 A simple, modern, and secure file encryption tool.

---

## Installation

```bash
# Debian/Ubuntu
sudo apt install age

# Arch Linux
sudo pacman -S age

# macOS
brew install age
```

**Verify installation:**
```bash
age --version
```

---

## 🔑 Key Generation

```bash
# Generate a new key pair
age-keygen -o id_age

# Output public key only
age-keygen -y id_age
```

> **Note:** The private key file (`id_age`) contains both the public key (in a comment) and the private key.

---

## 🔒 Passphrase Encryption

### Encrypt with Passphrase
```bash
age --passphrase -o encrypted.file unencrypted.file
```

### Decrypt with Passphrase
```bash
age --decrypt -o unencrypted.file encrypted.file
```

---

## 🔐 Public Key Encryption

### Encrypt to a Recipient
```bash
# Using public key directly
age -r age1xxxxxxxxxx... -o encrypted.file unencrypted.file

# Using public key file
age -R id_age.pub -o encrypted.file unencrypted.file
```

### Encrypt to Multiple Recipients
```bash
age -r age1xxx... -r age1yyy... -o encrypted.file unencrypted.file

# Or using multiple key files
age -R recipient1.pub -R recipient2.pub -o encrypted.file unencrypted.file
```

### Decrypt with Private Key
```bash
age -d -i id_age -o unencrypted.file encrypted.file
```

---

## 🔄 Streaming & Pipes

```bash
# Encrypt from stdin
cat secret.txt | age -r age1xxx... > secret.txt.age

# Decrypt to stdout
age -d -i id_age secret.txt.age

# Pipe through tar for directory encryption
tar czf - folder/ | age -r age1xxx... > folder.tar.gz.age

# Decrypt and extract
age -d -i id_age folder.tar.gz.age | tar xzf -
```

---

## 💡 Common Options

| Option | Description |
|--------|-------------|
| `-o FILE` | Write output to FILE |
| `-r RECIPIENT` | Encrypt to specified recipient (public key) |
| `-R FILE` | Encrypt to recipients listed in FILE |
| `-i FILE` | Use identity (private key) file for decryption |
| `-d, --decrypt` | Decrypt the input |
| `-p, --passphrase` | Use passphrase-based encryption |
| `-a, --armor` | Output ASCII-armored (PEM-like) format |

---

## 📚 Resources

- 📘 [age GitHub](https://github.com/FiloSottile/age)
- 📖 [age Specification](https://age-encryption.org/v1)
- 🔧 [rage](https://github.com/str4d/rage) — Rust implementation of age
