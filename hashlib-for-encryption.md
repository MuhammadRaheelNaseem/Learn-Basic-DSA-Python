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

---
# Advance Part


---

### **1. Experimenting with Different Hashing Algorithms and Handling Larger Files**

We will experiment with different hashing algorithms such as **MD5**, **SHA-1**, and **SHA-256** and then hash a large file to observe the performance. 

Here’s how you can hash larger files and experiment with different algorithms.

#### **Hashing Larger Files with Multiple Algorithms**

```python
import hashlib
import time

def hash_file(file_path, hash_algorithm):
    hash_object = hash_algorithm()
    
    try:
        with open(file_path, 'rb') as file:
            chunk = file.read(4096)  # Read in chunks
            while chunk:
                hash_object.update(chunk)  # Update the hash with the chunk of the file
                chunk = file.read(4096)  # Read the next chunk
        
        return hash_object.hexdigest()
    
    except FileNotFoundError:
        return "File not found!"

def compare_hash_algorithms(file_path):
    algorithms = [hashlib.md5, hashlib.sha1, hashlib.sha256]
    
    for algo in algorithms:
        start_time = time.time()
        file_hash = hash_file(file_path, algo)
        end_time = time.time()
        print(f"{algo().name.upper()} hash: {file_hash}")
        print(f"Time taken: {end_time - start_time:.5f} seconds")
        
# Example Usage:
file_path = input("Enter the path of the large file to hash: ")
compare_hash_algorithms(file_path)
```

**Explanation**:
- This script hashes a file in chunks (to avoid memory overload) using **MD5**, **SHA-1**, and **SHA-256**.
- It measures the time taken for each hashing algorithm, allowing you to observe performance differences, especially for larger files.
- **MD5** is faster but not suitable for security purposes. **SHA-256** is more secure but might take a bit longer for larger files.

---

### **2. Implementing Password Verification for Web or Desktop Applications**

We’ll build a simple **password verification system** that can be easily integrated into both **desktop** and **web applications**.

#### **Password Verification Using SHA-256 (for simplicity)**

This example demonstrates password verification using SHA-256 hashing, which is common for simpler systems. You could later replace it with **bcrypt** or **PBKDF2** for stronger security.

```python
import hashlib
import os

def hash_password(password):
    """Hash a password using SHA-256."""
    hash_object = hashlib.sha256()
    hash_object.update(password.encode())
    return hash_object.hexdigest()

def store_password():
    """Simulate storing a password (e.g., in a database)."""
    password = input("Enter a password to store: ")
    hashed_password = hash_password(password)
    # Here we would normally store the hashed password in a database
    print(f"Stored hashed password: {hashed_password}")
    return hashed_password

def verify_password(stored_hash):
    """Simulate password verification."""
    password = input("Enter password to verify: ")
    hashed_input_password = hash_password(password)
    if stored_hash == hashed_input_password:
        print("Password verified successfully!")
    else:
        print("Incorrect password.")

# Example Usage:
stored_hash = store_password()  # Store password securely
verify_password(stored_hash)    # Verify password using stored hash
```

**Explanation**:
- The `hash_password` function uses **SHA-256** to hash passwords.
- In the `store_password` function, the password is hashed and **stored** in a database (in practice, you'd store the hash in a database).
- The `verify_password` function hashes the input password and compares it with the stored hash to verify the password.

#### **For Web Applications (Flask Example)**

For a web application, you would likely use **bcrypt** or **PBKDF2** to securely hash and verify passwords. Here's an example using **Flask** for password hashing with **bcrypt**.

```bash
pip install flask bcrypt
```

```python
from flask import Flask, request, render_template_string
import bcrypt

app = Flask(__name__)

# Home route where user can enter password to store or verify
@app.route("/", methods=["GET", "POST"])
def index():
    if request.method == "POST":
        password = request.form["password"]
        hashed_password = bcrypt.hashpw(password.encode(), bcrypt.gensalt())
        return render_template_string("""
            <h1>Password Hashed and Stored!</h1>
            <p>Hashed password: {{ hashed_password }}</p>
            <form method="POST" action="/verify">
                <input type="password" name="password" placeholder="Enter password to verify">
                <input type="submit" value="Verify Password">
            </form>
        """, hashed_password=hashed_password.decode())

    return '''
        <form method="POST">
            <input type="password" name="password" placeholder="Enter password to store">
            <input type="submit" value="Store Password">
        </form>
    '''

# Route for verifying password
@app.route("/verify", methods=["POST"])
def verify():
    stored_hash = request.form["stored_hash"]  # Ideally stored in a database
    password = request.form["password"]

    if bcrypt.checkpw(password.encode(), stored_hash.encode()):
        return "<h1>Password Verified!</h1>"
    else:
        return "<h1>Incorrect Password</h1>"

if __name__ == "__main__":
    app.run(debug=True)
```

**Explanation**:
- The user stores a password on the homepage, which is hashed using **bcrypt**.
- The user can then verify their password on the `/verify` route by comparing the input with the stored hash.
- **Flask** is used to create the web application.

---

### **3. Real-World Use Cases of Hashing Algorithms**

#### **a. Database Management**

Hashing is used in databases to store passwords securely. **Salting** and **hashing** passwords before storing them ensures that even if the database is compromised, the actual passwords cannot be easily retrieved.

In a real-world scenario, here’s how **password hashing** works:
1. **Storing a password**: Instead of storing the plain password, a salted hash is stored.
2. **Verifying a password**: The password is hashed again with the same salt, and the hash is compared with the stored hash.

#### **b. File Integrity Checking**

Hashing is widely used in **file integrity checking**. For example, software distributions often provide the **hash** of the file (e.g., SHA-256), so users can check if their downloaded file matches the hash. If the hash doesn’t match, the file may have been altered or corrupted.

Here’s a typical process in software distribution:
1. The software provider releases a file with its hash value (e.g., SHA-256).
2. The user downloads the file and calculates the hash of the downloaded file.
3. The user compares their calculated hash with the provided hash to ensure integrity.

#### **c. Digital Signatures**

Hashing algorithms are used in **digital signatures** to verify that a message or document has not been tampered with. The hash of the message is encrypted using a private key to create the digital signature.

For example, the process is:
1. The sender creates a hash of the message.
2. The sender encrypts the hash with their private key.
3. The receiver decrypts the hash using the sender’s public key and compares it with the hash of the received message to verify integrity.

---

### **Summary**

1. **Hashing Larger Files**: We experimented with hashing algorithms like MD5, SHA-1, and SHA-256 to hash large files.
2. **Password Verification**: Implemented a secure password verification system for both desktop and web applications using hashing and salt.
3. **Real-World Applications**:
   - **Database Management**: Using hashing and salting for storing passwords securely.
   - **File Integrity**: Ensuring the integrity of files by comparing hashes.
   - **Digital Signatures**: Using hashing for authentication and data verification.

---
