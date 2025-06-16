# SecurByte

SecurByte 1.1 is a lightweight command-line tool for encrypting and decrypting files using AES-256-CBC.

## Usage

```bash
SecurByte [--encrypt-file/-ef | --decrypt-file/-df <filepath>] [--passwd/-p <password>] [--nobanner/-n] [--help/-h]
```

## Options

- `-ef, --encrypt-file <filepath>` → Encrypts the specified file.
- `-df, --decrypt-file <filepath>` → Decrypts the specified file.
- `-p, --passwd <password>` → Specifies the password for encryption/decryption.
- `-n, --nobanner` → Suppresses the startup banner.
- `-h, --help` → Displays the help message.

## Download exe for Windows

This tool is part of the [8gudbitsKit](https://github.com/8gudbits/8gudbitsKit) project. To download the executable for Windows, visit the [8gudbitsKit](https://github.com/8gudbits/8gudbitsKit) repository.

## For the Tech People

### **Encryption Process**

- Reads the file and applies PKCS7 padding.
- Hashes the password using SHA-256 to derive the encryption key.
- Generates a random IV and encrypts the data using AES-256-CBC.
- Prepends the "securbyte_1.1" header to the encrypted output.
- Saves the encrypted file.

**Note:** The reason for prepending the "securbyte_1.1" header is to identify the file as a SecurByte-encrypted file. This is useful for future compatibility and to ensure that the file can be decrypted using the same version of the tool or a compatible version. This also helps to understand if the correct password is being used for decryption.

### **Decryption Process**

- Reads the file and verifies the "securbyte_1.1" header.
- Extracts the IV and decrypts the data using AES-256-CBC.
- Removes PKCS7 padding.
- Saves the decrypted file.

**Note:** If the header is missing or incorrect, the tool warns that the file may not have been encrypted using SecurByte or has been modified.
