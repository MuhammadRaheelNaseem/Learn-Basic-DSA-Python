# **Lecture on `hashlib` in Python**

### **Objective of the Lecture**
By the end of this lecture, students will:
- Understand the concept of hashing.
- Learn how to use Python’s `hashlib` library.
- Understand real-world use cases for hashing, like password hashing and integrity checks.
- Explore basic to advanced examples of using hashing.

---

### **1. Introduction to Hashing**

**What is Hashing?**

- Hashing is the process of converting data (such as text, files, or even passwords) into a fixed-size string of characters, which is typically a hexadecimal number.
- The result of hashing is called a **hash value** or **digest**.

**Real-world analogy**: Think of hashing like a fingerprint: It uniquely represents the data, but even a small change in the data will result in a completely different hash.

---

### **2. Why is Hashing Important?**

- **Data Integrity**: Hashing is used to verify that the data hasn’t been altered.
- **Password Storage**: Instead of storing the actual password, websites store the hashed password for security.
- **Digital Signatures**: Hashing is used in cryptographic applications to ensure the authenticity and integrity of messages.

---

### **3. Introduction to `hashlib` Module**

Python provides the `hashlib` module, which offers common hashing algorithms like SHA-1, SHA-256, MD5, etc.

#### **Common Hashing Algorithms in `hashlib`:**
- `SHA-1`
- `SHA-256`
- `SHA-512`
- `MD5` (though not recommended for cryptographic purposes)
- `BLAKE2`

#### **Basic Syntax for Hashing:**

```python
import hashlib

# Example of creating a hash using SHA-256
hash_object = hashlib.sha256()
hash_object.update(b'hello world')  # Input data should be in bytes
hex_dig = hash_object.hexdigest()
print(hex_dig)
```

---

### **4. Basic Example: Hashing Text Data**

Let’s start with the simplest example of hashing a string using SHA-256.

#### **Exercise 1: Hash a String Using SHA-256**

```python
import hashlib

def hash_string(input_string):
    # Create a hash object
    hash_object = hashlib.sha256()
    # Update the hash object with the bytes of the input string
    hash_object.update(input_string.encode())
    # Get the hexadecimal representation of the digest
    return hash_object.hexdigest()

input_text = input("Enter a string to hash: ")
hashed_value = hash_string(input_text)
print(f"SHA-256 hash of '{input_text}' is: {hashed_value}")
```

**Explanation**: 
- `update()` accepts bytes, which is why we need to encode the string.
- `hexdigest()` returns the hash as a hexadecimal string.

---

### **5. Exploring Different Hashing Algorithms**

Now that you understand the basics of hashing, let's look at a few different algorithms available in `hashlib`.

#### **Exercise 2: Compare Different Hashing Algorithms**

```python
import hashlib

def compare_hashing_algorithms(input_string):
    hash_algorithms = ['md5', 'sha1', 'sha256', 'sha512']
    
    for algo in hash_algorithms:
        hash_object = hashlib.new(algo)  # Create a hash object of the specified algorithm
        hash_object.update(input_string.encode())
        print(f"{algo.upper()} hash: {hash_object.hexdigest()}")

input_text = input("Enter a string to compare hash algorithms: ")
compare_hashing_algorithms(input_text)
```

**Explanation**:
- This program compares how different hashing algorithms represent the same string.
- The `new()` method allows you to specify the algorithm by its name.

---

### **6. Hashing Files**

In real-world scenarios, we might need to hash files, for instance, to verify file integrity.

#### **Exercise 3: Hash a File Using SHA-256**

```python
import hashlib

def hash_file(file_path):
    hash_object = hashlib.sha256()
    try:
        with open(file_path, 'rb') as file:
            chunk = file.read(4096)  # Read in chunks to avoid memory overload
            while chunk:
                hash_object.update(chunk)
                chunk = file.read(4096)
        return hash_object.hexdigest()
    except FileNotFoundError:
        return "File not found."

file_path = input("Enter the file path to hash: ")
file_hash = hash_file(file_path)
print(f"SHA-256 hash of the file: {file_hash}")
```

**Explanation**:
- This script reads a file in binary mode (`'rb'`) and hashes it in chunks.
- This is important for large files, as it prevents loading the entire file into memory.

---

### **7. Hashing Passwords (Secure Storage)**

When hashing passwords, it is critical to use a strong hashing algorithm and add **salting** to prevent rainbow table attacks.

#### **Exercise 4: Password Hashing with Salt**

```python
import hashlib
import os

def hash_password(password):
    salt = os.urandom(16)  # Generate a random salt
    hash_object = hashlib.sha256(salt + password.encode())  # Combine salt and password
    return salt + hash_object.digest()  # Store salt along with the hash

def verify_password(stored_hash, input_password):
    salt = stored_hash[:16]  # Extract the salt (first 16 bytes)
    stored_password_hash = stored_hash[16:]
    hash_object = hashlib.sha256(salt + input_password.encode())  # Rehash with input password and salt
    return stored_password_hash == hash_object.digest()

# Example Usage:
password = input("Enter a password to hash: ")
stored_hash = hash_password(password)
print(f"Password hash: {stored_hash.hex()}")

input_password = input("Re-enter password for verification: ")
if verify_password(stored_hash, input_password):
    print("Password verified successfully!")
else:
    print("Invalid password.")
```

**Explanation**:
- **Salting**: Adds randomness to the password before hashing, ensuring that even identical passwords will produce different hashes.
- The `os.urandom()` function is used to generate a secure salt.

---

### **8. Advanced Example: File Integrity Check Using Hashing**

In some applications, like software distribution or backups, you can use hashing to verify that the file hasn’t been tampered with.

#### **Exercise 5: File Integrity Check**

```python
import hashlib

def file_integrity_check(original_file, current_file):
    # Hash the original file
    original_hash = hash_file(original_file)
    
    # Hash the current file
    current_hash = hash_file(current_file)
    
    if original_hash == current_hash:
        print("File is intact, no changes detected.")
    else:
        print("Warning! File integrity compromised.")

# Example usage
original_file = input("Enter the original file path: ")
current_file = input("Enter the file path to check: ")
file_integrity_check(original_file, current_file)
```

**Explanation**:
- You can use this script to compare the hash of a file at two different points in time to check if it has been altered. Commonly used in digital forensics and software distribution.

---

### **9. Practical Considerations: Security Risks and Best Practices**

- **MD5 and SHA-1** are **not secure** for cryptographic purposes due to vulnerabilities such as collision attacks (where two different inputs produce the same hash).
- Always use **SHA-256** or **BLAKE2** for better security.
- When hashing passwords, **always use salting**, and for even stronger security, consider **PBKDF2** or **bcrypt** (which are built for password storage).

---

### **10. Hashing for Checking Data Integrity (Real-World Use)**

In real-world applications, hashing is often used to check if the data has been tampered with during transmission. For example, files or messages might be hashed, and the hash is sent along with the data. Upon receipt, the hash is recalculated and compared to the original hash to verify integrity.

#### **Exercise 6: Data Integrity Using Hashing**

```python
def verify_integrity(message, original_hash):
    hash_object = hashlib.sha256(message.encode())  # Hash the incoming message
    message_hash = hash_object.hexdigest()  # Get the hash
    
    if message_hash == original_hash:
        print("The data is intact and unaltered.")
    else:
        print("Data integrity check failed. The data may have been tampered with.")

# Example usage
message = input("Enter a message to verify: ")
original_hash = input("Enter the original hash of the message: ")
verify_integrity(message, original_hash)
```

**Explanation**:
- This example checks if the content (such as a message) has been altered by comparing the hash of the received data to the original hash.

---

Sure! Let's dive deeper into **`hashlib`** for the following advanced use cases:

1. **Hashing other data types** like images and documents.
2. **Hashing for authentication systems** (storing and verifying passwords).
3. Exploring more **secure password hashing algorithms** like **bcrypt** and **PBKDF2**.

---

### **1. Hashing Other Data Types (Images and Documents)**

Hashing can be applied to different data types, not just strings. You can use it to hash files (like images, documents, etc.) to verify their integrity or to ensure that no changes have been made.

#### **Hashing an Image File**

In this example, we will hash an image file (e.g., `.jpg` or `.png`) using SHA-256 to ensure its integrity.

```python
import hashlib

def hash_image(file_path):
    # Create a SHA-256 hash object
    hash_object = hashlib.sha256()

    try:
        with open(file_path, 'rb') as image_file:
            # Read the file in binary mode
            chunk = image_file.read(4096)  # Read the file in chunks to save memory
            while chunk:
                hash_object.update(chunk)  # Update the hash with the chunk of the file
                chunk = image_file.read(4096)  # Read the next chunk

        # Return the hexadecimal digest of the file's hash
        return hash_object.hexdigest()
    
    except FileNotFoundError:
        return "File not found!"

# Example Usage:
image_path = input("Enter the path of the image to hash: ")
hashed_image = hash_image(image_path)
print(f"SHA-256 hash of the image: {hashed_image}")
```

**Explanation**:
- The file is read in **binary mode** (`'rb'`), and chunks are used to prevent memory overload with large files.
- The **SHA-256 hash** is computed, and the digest is returned.

#### **Hashing a Document (Text File)**

Now, let's hash a text document. We can apply the same concept to documents (e.g., `.txt`, `.pdf`) by reading them and hashing their content.

```python
def hash_document(file_path):
    hash_object = hashlib.sha256()
    
    try:
        with open(file_path, 'rb') as doc_file:
            chunk = doc_file.read(4096)  # Read the file in chunks
            while chunk:
                hash_object.update(chunk)
                chunk = doc_file.read(4096)

        return hash_object.hexdigest()
    
    except FileNotFoundError:
        return "File not found!"

# Example Usage:
document_path = input("Enter the path of the document to hash: ")
hashed_document = hash_document(document_path)
print(f"SHA-256 hash of the document: {hashed_document}")
```

**Explanation**:
- This script can be used for documents as well. It's the same process as the image example: read the file in chunks and update the hash.

---

### **2. Hashing for Authentication Systems (Storing and Verifying Passwords)**

For authentication systems, it's important to **hash passwords** instead of storing them directly to prevent unauthorized access. We'll cover basic password hashing using `hashlib` and later look into more advanced methods.

#### **Basic Password Hashing Using SHA-256**

```python
import hashlib

def hash_password(password):
    # Create a SHA-256 hash object
    hash_object = hashlib.sha256()
    # Update the hash object with the encoded password
    hash_object.update(password.encode())
    # Return the hexadecimal digest of the password
    return hash_object.hexdigest()

def verify_password(stored_hash, input_password):
    # Hash the input password and compare with the stored hash
    return stored_hash == hash_password(input_password)

# Example Usage:
password = input("Enter a password to hash: ")
stored_hash = hash_password(password)  # Hash the password and store it securely

print(f"Stored password hash: {stored_hash}")

# Verifying the password
input_password = input("Enter the password to verify: ")
if verify_password(stored_hash, input_password):
    print("Password verified successfully!")
else:
    print("Incorrect password.")
```

**Explanation**:
- The `hash_password` function takes a plaintext password and hashes it using SHA-256.
- **Storing** the hash value ensures the original password is never saved in plain text.
- The `verify_password` function compares the stored hash with the hash of the input password.

---

### **3. Advanced Password Hashing Algorithms: bcrypt and PBKDF2**

While SHA-256 works for many use cases, **bcrypt** and **PBKDF2** are more secure for password hashing because they add **salt** (random data) and are computationally expensive, making them more resistant to brute-force and rainbow table attacks.

#### **Using bcrypt for Password Hashing**

**bcrypt** is designed specifically for hashing passwords and includes a salt by default.

```python
import bcrypt

def hash_password_bcrypt(password):
    # bcrypt automatically salts and hashes the password
    salt = bcrypt.gensalt()
    hashed_password = bcrypt.hashpw(password.encode(), salt)
    return hashed_password

def verify_password_bcrypt(stored_hash, input_password):
    # bcrypt hashpw() returns a hashed password
    return stored_hash == bcrypt.hashpw(input_password.encode(), stored_hash)

# Example Usage:
password = input("Enter a password to hash: ")
hashed_password = hash_password_bcrypt(password)
print(f"Hashed password using bcrypt: {hashed_password}")

# Verifying the password
input_password = input("Enter the password to verify: ")
if verify_password_bcrypt(hashed_password, input_password):
    print("Password verified successfully!")
else:
    print("Incorrect password.")
```

**Explanation**:
- `bcrypt.gensalt()` generates a salt automatically, making it much more secure.
- The `hashpw` method hashes the password with the salt.
- bcrypt hashing is slower and designed to make brute-force attacks more difficult.

#### **Using PBKDF2 for Password Hashing**

**PBKDF2 (Password-Based Key Derivation Function 2)** is another secure password hashing method that iteratively hashes the password multiple times to slow down brute-force attempts.

```python
from cryptography.hazmat.primitives import hashes
from cryptography.hazmat.primitives.kdf.pbkdf2 import PBKDF2HMAC
import os

def hash_password_pbkdf2(password):
    # Generate a salt
    salt = os.urandom(16)  # 16-byte salt
    # Derive the key using PBKDF2 with 100,000 iterations
    kdf = PBKDF2HMAC(
        algorithm=hashes.SHA256(),
        length=32,  # Desired key length
        salt=salt,
        iterations=100000
    )
    hashed_password = kdf.derive(password.encode())
    return salt + hashed_password  # Store salt + hash

def verify_password_pbkdf2(stored_hash, input_password):
    salt = stored_hash[:16]  # Extract the salt (first 16 bytes)
    stored_hash_value = stored_hash[16:]
    
    # Derive the hash from the input password using the extracted salt
    kdf = PBKDF2HMAC(
        algorithm=hashes.SHA256(),
        length=32,
        salt=salt,
        iterations=100000
    )
    try:
        kdf.verify(input_password.encode(), stored_hash_value)
        return True
    except Exception:
        return False

# Example Usage:
password = input("Enter a password to hash: ")
stored_hash = hash_password_pbkdf2(password)
print(f"Hashed password using PBKDF2: {stored_hash.hex()}")

# Verifying the password
input_password = input("Enter the password to verify: ")
if verify_password_pbkdf2(stored_hash, input_password):
    print("Password verified successfully!")
else:
    print("Incorrect password.")
```

**Explanation**:
- `PBKDF2HMAC` is used to generate a hash of the password with 100,000 iterations (to slow down attacks).
- The salt is stored along with the hash to verify future login attempts.

---

### **Summary of Advanced Topics**
1. **Hashing Other Data Types**:
   - You can hash not just strings, but also files like images or documents by reading them in chunks.
2. **Password Hashing**:
   - Store the **hashed** password rather than the password itself for better security.
   - Use **salted** hashes to prevent rainbow table attacks.
3. **Advanced Hashing Algorithms**:
   - **bcrypt** is specifically designed for secure password hashing and includes salt.
   - **PBKDF2** adds an iterative process to make password cracking slower and harder.

---
