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

