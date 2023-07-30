# Crypto Module - Complete Documentation**

The `crypto` module is a core module in Node.js that provides cryptographic functionality. It allows you to perform various cryptographic operations, such as creating secure hashes, encrypting and decrypting data, and generating random bytes.

**Importing the Crypto Module:**
To use the `crypto` module, you need to import it first. In Node.js, you can import core modules using the `require()` function:

```javascript
const crypto = require('Node/23-crypto');
```

**Generating Secure Random Values:**

1. **`crypto.randomBytes(size[, callback])`**:
   Generates cryptographically secure random bytes. The `size` parameter determines the number of bytes to generate. Optionally, you can provide a `callback` function to handle the result asynchronously.

   Example:
   ```javascript
   const randomBytes = crypto.randomBytes(16);
   console.log(randomBytes.toString('hex')); // Print the bytes in hexadecimal format
   ```

**Hashing Functions:**

1. **`crypto.createHash(algorithm)`**:
   Creates a hash object using the specified `algorithm`. The hash object can be used to compute a hash digest of data.

   Example:
   ```javascript
   const hash = crypto.createHash('sha256');
   hash.update('Hello, World!');
   const digest = hash.digest('hex');
   console.log(digest);
   ```

**Symmetric Encryption and Decryption:**

1. **`crypto.createCipheriv(algorithm, key, iv)`**:
   Creates a Cipher object using the specified `algorithm`, `key`, and optional `iv` (initialization vector). The Cipher object is used for encryption.

2. **`crypto.createDecipheriv(algorithm, key, iv)`**:
   Creates a Decipher object using the specified `algorithm`, `key`, and optional `iv`. The Decipher object is used for decryption.

**Asymmetric Encryption and Decryption:**

1. **`crypto.publicEncrypt(key, buffer)`**:
   Encrypts data using the specified `key`. The `key` should be a public key in PEM format.

   Example:
   ```javascript
   const publicKey = fs.readFileSync('public_key.pem');
   const encryptedData = crypto.publicEncrypt(publicKey, Buffer.from('Hello, World!'));
   ```

2. **`crypto.privateDecrypt(key, buffer)`**:
   Decrypts data using the specified `key`. The `key` should be a private key in PEM format.

   Example:
   ```javascript
   const privateKey = fs.readFileSync('private_key.pem');
   const decryptedData = crypto.privateDecrypt(privateKey, encryptedData);
   ```

**Summary:**
- The `crypto` module in Node.js provides cryptographic functionality.
- You can import the `crypto` module using `const crypto = require('crypto');`.
- The module offers methods for generating secure random values, hashing data, and performing symmetric and asymmetric encryption/decryption.
- To generate secure random bytes, use `randomBytes()`.
- For hashing data, use `createHash()` and `digest()`.
- For symmetric encryption and decryption, use `createCipheriv()` and `createDecipheriv()`.
- For asymmetric encryption and decryption, use `publicEncrypt()` and `privateDecrypt()`.

The `crypto` module is essential for securing sensitive data in your Node.js applications. It provides the tools necessary for generating random numbers, creating secure hashes, and performing encryption/decryption operations. It is widely used in applications that require data security and privacy, such as password hashing, secure communication, and digital signatures.
