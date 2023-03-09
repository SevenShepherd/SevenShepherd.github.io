---
layout: post
title: "🔒 Exercises In Digital Discipleship, Puzzle III: Modern Cryptography"
date: 2023-03-08 3:10:00 -0500
categories: cryptography aes rijndael
published: true
---

This is an **intermediate to advanced** exercise in file encryption, written 10/08/2020 on a separate blog, and repurposed for the digital discipleship program created by SevenShepherd. If you are new or haven't gone through our fundamentals course, you may want to check that out before attempting this exercise.

# **Advanced Encryption Standard ([AES](https://csrc.nist.gov/projects/cryptographic-standards-and-guidelines/archived-crypto-projects/aes-development))**

AES is the first publicly accessible cipher approved by the NSA for encrypting top secret information, provided that a 192-bit (24-byte) or 256-bit (32-byte) key length is used.

> "The design and strength of all key lengths of the AES algorithm (i.e., 128, 192 and
256) are sufficient to protect classified information up to the SECRET level. **TOP
SECRET** information will require use of either the **192 or 256** key lengths..." ― [NSA](https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Module-Validation-Program/documents/CNSS15FS.pdf)

On `January 02, 1997`, NIST announced the need for a new encryption standard to supersede the `Data Encryption Standard (DES)`, which was becoming vulnerable to brute-force attacks because of its relatively small key size (56-bit). DES was originally designed for hardware and when it was translated to software it resulted in a slow implementation. `Triple-DES`, which applied DES three times to each data block, attempted to avoid the problem of a small key size, but naturally it was even slower. The answer was to initiate a new standard called AES.

> "A process to develop a
Federal Information Processing
Standard (FIPS) for Advanced
Encryption Standard (AES)
incorporating an Advanced Encryption
Algorithm (AEA) is being initiated by
the National Institute of Standards and
Technology (NIST)." ― [NIST](https://www.govinfo.gov/content/pkg/FR-1997-01-02/pdf/96-32494.pdf)

On `August 20, 1998`, fifteen candidate designs are made public: CAST-256, CRYPTON, DEAL, DFC, E2, FROG, HPC, LOKI97, MAGENTA, MARS, RC6, Rijndael, SAFER+, Serpent, and Twofish.

> "Twenty-one algorithms were submitted to NIST by
the June 15, 1998 deadline. After review, NIST determined that 15 of these met the minimum acceptability
requirements and were accompanied by a complete
submission package. These algorithms were made
public by NIST on August 20, 1998 at AES1 for the first
evaluation period." ― [NIST](https://nvlpubs.nist.gov/nistpubs/jres/104/1/j41ce-rob.pdf)

On `April 13-14, 2000`, only five finalist algorithms remained MARS, RC6, Rijndael, Serpent, and Twofish. 

> "The five finalist algorithms are MARS, RC6™, Rijndael, Serpent, and Twofish. MARS was
submitted by the International Business Machines Corporation (U.S.). RC6 was submitted by
RSA Laboratories (U.S.). Rijndael was submitted by Joan Daemen and Vincent Rijmen
(Belgium). Serpent was submitted by Ross Anderson (U.K.), Eli Biham (Israel), and Lars
Knudsen (Norway). Twofish was submitted by Bruce Schneier, John Kelsey, Doug Whiting,
David Wagner, Chris Hall, and Niels Ferguson (U.S.)." ― [NIST](https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Standards-and-Guidelines/documents/aes-development/aes3report.pdf)

On `October 2, 2000`, `Rijandael` takes the prize.

> "... NIST announced that it has selected Rijndael to propose for the AES." ― [NIST](https://csrc.nist.gov/projects/cryptographic-standards-and-guidelines/archived-crypto-projects/aes-development#overview)
 

# **Modern Cryptography** 

Modern cryptography can be broken down into two types of algorithms: 

- `Symmetric-key algorithms` which use one key (shared secret) to encrypt plaintext (resulting in ciphertext) and decrypt ciphertext (resulting in plaintext). Symmetric algorithms can be further subdivided into two categories:
    - `block ciphers` which operate on plaintext in groups of bits called blocks.
    - `stream ciphers` which operate on plaintext a single bit (or sometimes byte) at a time.
- `Asymmetric-key algorithms` (also called public-key algorithms) which use a key pair consisting of a public-key & private-key.

# **Modern Modes Of Operation**

Modes of operation exist to define behavior beyond applying a cipher to a single block of data and, in the case of `AES which has a fixed block size of 128 bits (16 bytes)` the restriction would severely limit our ability to encrypt things beyond this size limitation. In order to securely transform multiple blocks of data we rely on a mode of operation. Modern day modes of operation include: `CCM, EAX, GCM, SIV, and OCB`. 

Modern modes of operation combine encryption and authentication into `a single, efficient primitive`. Compare this to classic modes of operation that only provide guarantees over the confidentiality of the message but not over its integrity. Because classic modes lack authentication, we are forced to implement our own MAC primitive, usually `Hash-based Message Authentication Code (HMAC)`, to achieve the same goal. Suffice it to say, the implementation of a modern mode is much simpler for this reason, ergo the implementation of a classic mode is not always intuitive, efficient or secure. *Let's take GCM for example*:

# Galois/Counter Mode ([GCM](http://csrc.nist.gov/publications/nistpubs/800-38D/SP-800-38D.pdf)):

> "GCM provides assurance of the confidentiality of data using a variation of the Counter mode of
operation for encryption. GCM provides assurance of the authenticity of the confidential data
(up to about 64 gigabytes per invocation) using a universal hash function that is defined over a binary Galois (i.e., finite) field..." ― [NIST Special Publication 800-38D](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38d.pdf)


```python
from Crypto.Cipher       import AES
from Crypto.Protocol.KDF import scrypt

def main():
    data = {
        "header"   : b"authenticate only",
        "plaintext": b"secret message",
        "key"      : b"password"
    }

    encrypt_gcm(data)
    decrypt_gcm(data)

# Function Definitions

if __name__ == "__main__":
    main()
```
During encryption the cipher object is created and used to generate the ciphertext from the plaintext and produce the digest which will be used to verify it's integrity upon future decryption. We write this data to a file by creating a raw binary file format of our own, the default GCM nonce size is 16 bytes and so the first 16 bytes of our file will be the nonce value. The next 16 bytes of our file will be dedicated to our authentication digest, the rest will be devoted to our ciphertext.

```python
def encrypt_gcm(data):
    password = key_derivation_scrypt( data['key'] )
    encipher = AES.new(password, AES.MODE_GCM)
    encipher.update(data['header'])
    ciphertext, tag = encipher.encrypt_and_digest(data['plaintext'])

    with open("encrypted.bin", "wb") as out:
        [ out.write(x) for x in (encipher.nonce, tag, ciphertext) ]
```

When it comes time to decrypt, the nonce will be extracted from the first 16 bytes of our binary file to help us recreate the cipher object for decryption. The tag (digest) is how we verify that the encrypted data has not been tampered with, this section will be extracted next. The -1 passed into f.read(x) is the default value, it just means to read everything, or in this position, read the rest of the file in as the ciphertext.

```python
def decrypt_gcm(data):
    password  = key_derivation_scrypt( data['key'] )
    with open("encrypted.bin", "rb") as f:
        nonce, tag, ciphertext = [ f.read(x) for x in (16, 16, -1) ]

        decipher = AES.new(password, AES.MODE_GCM, nonce)
        decipher.update(data['header'])
        plaintext = decipher.decrypt_and_verify(ciphertext, tag)
        print(plaintext)
```

A `Key-Derivation Function (KDF)` will be used to both perform key strengthening and key stretching, so a password that does not conform to AES key size specification, or is deficient in length can still be used without compromising the security or operation of the encryption<br>(more on this later).

```python
def key_derivation_scrypt(key, salt=""):
    """
    Key Stretching Implementation
    Produces a 32 Byte / 256-bit Key
    """
    return scrypt(
        password = key,
        salt     = salt,
        key_len  = AES.key_size[-1],
        N        = 2**AES.block_size,
        r        = AES.block_size,
        p        = 1
    )
```

# **Classic Modes Of Operation**

Being the precursor to the modern modes of operation, these classic modes still exist to define behavior for applying a cipher beyond a single block of data. however, unlike modern modes of operation classic modes do not combine encryption and authentication into a single, efficient primitive. Remember that because classic modes lack authentication, we are forced to implement our own MAC primitive, usually `Hash-based Message Authentication Code (HMAC)`, to achieve the same goal. *Let's take CBC for an example:*

- ***Ciphertext Block Chaining*** ([CBC](http://csrc.nist.gov/publications/nistpubs/800-38a/sp800-38a.pdf))
> "The Cipher Block Chaining (CBC) mode is a confidentiality mode whose encryption process
features the combining (“chaining”) of the plaintext blocks with the previous ciphertext blocks.
The CBC mode requires an IV to combine with the first plaintext block. The IV need not be
secret, but it must be unpredictable..." ― [NIST Special Publication 800-38A, 6.2](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-38a.pdf)


- ***Padding*** ([PKCS#7](https://www.pycryptodome.org/en/latest/src/util/util.html#crypto-util-padding-module))
> "The method encrypt() (and likewise decrypt()) of a CBC cipher object expects data to have length multiple of the block size (e.g. 16 bytes for AES). You might need to use Crypto.Util.Padding to align the plaintext to the right boundary." ― [CBC Mode](https://www.pycryptodome.org/en/latest/src/cipher/classic.html#cbc-mode)

- **HMAC**
> "A message authentication code (MAC), also known as a data authentication code (DAC), is a one-way hash function with the addition of a secret key (see Section 18.14). The hash value is a function of both the pre-image and the key. The theory is exactly the same as hash functions, except only someone with the key can verify the hash value. You can create a MAC out of a hash function or a 
block encryption algorithm; there are also dedicated MACs." ― Applied Cryptography (Bruce Schneier)

```python
from Crypto.Cipher       import AES
from Crypto.Protocol.KDF import scrypt
from Crypto.Util.Padding import pad, unpad
from Crypto.Hash         import HMAC, SHA256

def main():
    data = {
        "plaintext": b"secret message",
        "key"      : b"password"
    }

    encrypt_cbc(data)
    decrypt_cbc(data)

# Function Definitions

if __name__ == "__main__":
    main()
```

For the remainder of this article, all classic mode ciphers will implement Encrypt-the-MAC.

> - **Encrypt-and-MAC**: The ciphertext is generated by encrypting the plaintext and then appending a MAC of the plaintext. This is approximately how SSH works.
- **MAC-then-encrypt**: The ciphertext is generated by appending a MAC to the plaintext and then encrypting everything. This is approximately how SSL works.
- **Encrypt-then-MAC**: The ciphertext is generated by encrypting the plaintext and then appending a MAC of the encrypted plaintext. This is approximately how IPSEC works.
>
Of these three, only Encrypt-then-MAC is provably secure ― [daemonology.net](http://www.daemonology.net/blog/2009-06-24-encrypt-then-mac.html)

The encryption function definition is as follows.

```python
def encrypt_cbc(data):
    password   = key_derivation_scrypt( data['key'] )
    encipher   = AES.new(password, AES.MODE_CBC)
    ciphertext = encipher.encrypt(pad(
        data['plaintext'], AES.block_size
    ))

    hmac = HMAC.new(password, ciphertext, SHA256)
    tag  = hmac.digest()

    with open("encrypted.bin", "wb") as out:
        [ out.write(x) for x in (encipher.iv, tag, ciphertext) ]
```

Similar to the example of the GCM implementation the iv takes the place of the nonce in recreating the cipher object.

```python
def decrypt_cbc(data):
    password  = key_derivation_scrypt( data['key'] )

    with open("encrypted.bin", "rb") as f:
        iv, tag, ciphertext = [ f.read(x) for x in (16, 32, -1) ]

    decipher = AES.new(password, AES.MODE_CBC, iv)
    hmac     = HMAC.new(password, ciphertext, SHA256)
    tag      = hmac.digest()
    try:
        hmac.verify( tag )
        plaintext = unpad(
            decipher.decrypt(ciphertext), AES.block_size
        )
        print(plaintext)
    except ValueError:
        print("Compromised!")
```

# **File Encryption & Decryption**

So far we've been working with a tiny associative array data structure called a dictionary in python to represent our data to encrypt and decrypt to and from a file. What we would like to accomplish is something a bit more practical, like the encryption and decryption of an entire file no matter how large. Let's continue with Cipher Block Chaining (CBC) to better illustrate what's happening under the hood.

..but first a quick digression where we examine a few simple code snippets involving the reading of a file by buffer size.

# Hash Checking

You may be tempted to read the entire file in at once when doing simple tasks like checking the hash of a file for instance. This is alright for small files but a problem arises when addressing larger files. Imagine reading in and entire movie file, that's like trying to swallow all the food on your dinner plate at once, the computer will likewise choke if the file is big enough.

```python
with open(path, "rb") as inFile:
    print(
        hashlib.sha256(
            inFile.read()
        ).hexdigest()
    )
```
Analogous to our aforementioned food example, we avoid choking the computer by breaking the data down into smaller chunks that we can then process piece by piece. 

```python
import hashlib

sha256 = hashlib.sha256()
with open(path, "rb") as inFile:

    while True:
        buffer    = inFile.read(16)
        bytesRead = len(buffer)

        if not bytesRead:
            break
        
        sha256.update(buffer)

        print(f"[{bytesRead:02d}-bytes]: {buffer}")

    size      = len(sha256.digest())
    hexdigest = sha256.hexdigest()
    print(f"[{size}-bytes]: {hexdigest}")
```
```python
[16-bytes]: b'"Unbeing dead is'
[16-bytes]: b"n't being alive."
[16-bytes]: b'" - E. E. Cummin'
[02-bytes]: b'gs'
[32-bytes]: fb90c351c7df9998454dfff2aff31c6838aaeaf55d5877c1b694c22a6168ad59
```

# Copying a File

Another example would be the copying of a file.

```python
with open(fromFile, "rb") as inFile, \
     open(toFile  , "wb") as outFile:

        while True:
            buffer    = inFile.read(16)
            bytesRead = len(buffer)

            if not bytesRead:
                break

            outFile.write(buffer)

            print(f"[{bytesRead:02d}-bytes]: {buffer}")
```
```python
[16-bytes]: b'"Unbeing dead is'
[16-bytes]: b"n't being alive."
[16-bytes]: b'" - E. E. Cummin'
[02-bytes]: b'gs'
```

# **Libraries & Dependencies**

This article will make heavy use of the [PyCryptodome](https://www.pycryptodome.org/en/latest/) module which was designed by Matthew Green, a cryptographer and professor at Johns Hopkins University.

```python
from Crypto.Cipher       import AES
from Crypto.Protocol.KDF import scrypt
from Crypto.Util.Padding import pad, unpad
from Crypto.Hash         import HMAC, SHA256
from Crypto.Random       import get_random_bytes
from functools           import wraps
import os.path
```

<!-- ```python
def main():
    path    = "..."
    inFile  = os.path.join(path, "plaintext.txt")
    outFile = os.path.join(path, "ciphertext.bin")
    final   = os.path.join(path, "recovered.txt")

    aes     = Rijndael("password")

    try:
        aes.encrypt_file(inFile, outFile, 2**16)
        aes.decrypt_file(outFile, final, 2**16)
    except IOError as e:
        print(e)
``` -->

Before we start constructing the class, I first want to create a function decorator. This decorator will eventually be used to make sure our file encryption and decryption adheres to a strict set of principals that will allow our methods to behave in a predefined manner so as not to overstep any bounds and cause errors. Specifically we want to make sure that when we are reading from a file, that it does in fact first exist! We also need to make certain that our buffer size is a multiple of AES 128-bit (16-byte) blocksize or else the provided algorithms and primitives will fail.

```python
def file_checks(func):
    @wraps(func)
    def wrapper(self, inF, outF, bufS):
        if not os.path.isfile(inF):
            raise FileNotFoundError("No File!")

        if os.path.exists(outF):
            if os.path.samefile(inF, outF):
                raise ValueError("Same File Path!")

        if bufS % AES.block_size != 0:
            raise ValueError("BufSize Not A Multiple Of AES Block Size!")
        
        return func(self, inF, outF, bufS)
    return wrapper
```
# **Initializer**

In the Initializer within our Rijndael class, we will be defining some private (name mangled) instance variables to handle the encryption and decryption of the internal encryption mechanism which will be further explained as we walk through the programs class. There is also one class variable named padChr which will be used to pad our encrypted binaries custom file format we will develop as we progress. Normally, I would make use of the default iv generated by the AES.new cipher object (self.__eCipher.iv); however, the reason that we cannot in this program is because the Key-Derivation Function requires the iv as its salt and is defined before the eCipher object is created. The cipher object also requires that the kdf password already be generated in order to construct the cipher object.

```python
class Rijndael:
    padChr = b'`'
    def __init__(self, key):
        self.__eIV       = get_random_bytes(AES.block_size)
        self.__eKey      = self._to_bytes(key)
        self.__ePassword = self._key_derivation_scrypt(self.__eKey)
        self.__eCipher   = AES.new(self.__ePassword, AES.MODE_CBC, self.__eIV)
        self.__eHMAC     = HMAC.new(self.__ePassword, digestmod=SHA256)
        
```
# **Instance Methods**

Our first method will be one such that checks & transforms, if need be, byte strings & strings to byte strings only. More simply, it takes a variable called value, checks to see if its in byte string format, if not it will check to see if it's a string, if so then it will convert it to a byte string, if not then we raise TypeError. If it's a byte string to begin with it will simply return the byte string.

```python
@staticmethod
def _to_bytes(value):
    if not isinstance(value, (bytes, bytearray)):
        if not isinstance( value, str ):
            raise TypeError("Bytes or Str Only!")
        value = bytes(value, "utf-8")
    return value
```
# **Key-Deriviation Function**

The `Key-Derivation Function (KDF)` we will be using is a slightly tweaked version of the one we made use of in our Galois/Counter Mode (GCM) mode example. The difference is we will be salting with our external `Initialization Vector`.

```python
def _key_derivation_scrypt(self, key, ivSalt=None):
    """
    Key Stretching Implementation
    Produces a 32 Byte / 256-bit Key
    """
    return scrypt(
        password = key,
        salt     = ivSalt or self.__eIV,
        key_len  = AES.key_size[-1],
        N        = 2**AES.block_size,
        r        = AES.block_size,
        p        = 1
    )
```

# **CBC Encryption & PKCS#7 Padding**

Remember that `Ciphertext Block Chaining (CBC)` expects data to have length multiple of AES blocksize. We can ensure this is the case with PKCS#7 pad and unpad. We will define two function methods to handle two different needs. When we are handling large files in buffer size chunks, we end up breaking the plaintext and ciphertext into separate pieces that cannot be handled the same exact way all the time. Most of the file will not be utilizing PKCS#7 padding since we will be reading the majority of the file in perfect multiples of AES blocksize.

```python
def _encrypt_without_padding(self, plaintext, newCipherObj=None):
    """
    encrypt_without_padding implements a variation 
    of encrypt that does not utilize padding, for 
    the express purpose of chaining ciphertexts 
    correctly when encrypting files.
    """
    plaintext = self._to_bytes(plaintext)

    if not newCipherObj:
        return self.__eCipher.encrypt( plaintext )
    else:
        return newCipherObj.encrypt( plaintext )
```

The problem becomes apparent when we reach the final pieces of data that are variable in size and not multiples of AES blocksize, it is these pieces of data that we will apply padding to.

```python
def _encrypt_with_padding(self, plaintext, newCipherObj=None):
    """
    newCipherObj is only to be used when you wish to
    encrypt a new cipher object not supplied by
    the constructor, otherwise just ignore.
    """
    plaintext = self._to_bytes(plaintext)

    if not newCipherObj:
        return self.__eCipher.encrypt(
            pad( plaintext, AES.block_size )
        )
    else:
        return newCipherObj.encrypt(
            pad( plaintext, AES.block_size )
        )
```
We can further construct a smart encrypt function that understands when to apply padding and when it should not. During our iteration of buffer size data we can check to see if that datas size is a multiple of AES blocksize, if not we can then apply padding, if so then padding is not needed.

```python
def _encrypt(self, bytesRead, plaintext, newCipherObj=None):
    # Encrypt bufSize Data (Multiple of AES Blocksize)
    if bytesRead % AES.block_size == 0:
        return self._encrypt_without_padding(plaintext, newCipherObj)
    # Encrypt PKCS#7 "Padded" Plaintext buffer
    else:
        return self._encrypt_with_padding(plaintext, newCipherObj)
```
# **CBC Decryption & PKCS#7 Padding**

With decryption we follow the same principals as encryption; however, we will not be implementing smart decryption functionality because when it comes time to unpack data we will be using a different method.
```python
def _decrypt_with_padding(self, ciphertext, newCipherObj=None):
    """
    newCipherObj is only to be used when you wish to
    decrypt a new cipher object not supplied by
    the constructor, otherwise just ignore.
    """
    ciphertext = self._to_bytes(ciphertext)

    if not newCipherObj:
        return unpad( self.__eCipher.decrypt(
            ciphertext
        ), AES.block_size)
    else:
        return unpad( newCipherObj.decrypt(
            ciphertext
        ), AES.block_size)

def _decrypt_without_padding(self, ciphertext, newCipherObj=None):
    """
    decrypt_raw implements a variation of decrypt
    that does not utilize unpadding, for the express
    purpose of dechaining ciphertexts correctly
    when decrypting files.
    """
    ciphertext = self._to_bytes(ciphertext)

    if not newCipherObj:
        return self.__eCipher.decrypt( ciphertext )
    else:
        return newCipherObj.decrypt( ciphertext )
```
# **Encrypted Binary File Format**

The method stamp will implement our custom file format preamble if you will. We want the first part of our encrypted binary to hold attribution, version information, and encryption scheme so we can instruct our program how to decrypt on the fly. This is where we make use of our class variable padChr. Each piece of information we be padded to 16-bytes in width and centered for a clean look in a hex editor.

```python
def _stamp(self, fileHandle):
    # [64-bytes] Write Stamp
    fill = lambda b: b.center(16, type(self).padChr)
    for stamp in [b"UMBRA", b'1', b"CogitoErgoCode", b"AES"]:
        if len(stamp) > 16:
            raise ValueError("Overflow!")
        fileHandle.write(fill( stamp ))
```
When it comes time to unpack the information formatted into the beginning of the encrypted binary, we skip the program name, extract the version and test to see if it meets our current decryption protocol. We then skip attribution with a fileHandle.seek(16, 1) which means skip ahead 16 bytes from current position (1). We then extract the encryption scheme and test to see if this is indeed an AES encrypted file. You can of course modify this further if you wish but this isn't really so imperative.

```python
def _stamp_unpack(self, fileHandle):
    # [16][16-bytes] Skip program name <0-15>
    fileHandle.seek(16) 

    # [32][16-bytes] Extract version
    version = fileHandle.read(16).replace( type(self).padChr, b'' )
    # Test for correct version
    if int(version) != 1:
        raise ValueError("Incorrect Version!")
    
    # [48][16-bytes] Skip attribution from current position
    fileHandle.seek(16, 1) # dec.seek(48)

    # [64][16-bytes] Extract encryption scheme stored within file
    encryption = fileHandle.read(16).replace( type(self).padChr, b'' ).decode()
    if encryption != "AES":
        raise ValueError("Incorrect Encryption Scheme!")
```
# **Decryption Scheme**

This next part is vital in understanding how this program works. When designing file encryption we need a way to store the internal encryption key and iv along side the the internally encrypted ciphertext as a convenience. Of course we cannot just store them in plaintext or else you might as well not encrypt anything at all as any interested party could use them to decrypt the ciphertext. This is where the need for our external instance variables come into play. `We need two separate cipher objects`, an internal cipher object to handle the encryption of our files contents and an external cipher object that will handle the encryption of our internal key and iv. You may be wondering why specifically the internal key and iv, the answer is because we can recreate the cipher object to decrypt using only those two things.

```python
def _scheme(self, fileHandle, iv, key):
    """
    This is the decryption scheme to allow an 
    encrypted document to securely carry it's 
    own decryption components
    
    Encrypt-the-mac internal iv & key with 
    external cipher object.

    [eIV] [eCiphertext(iIV+iKey)] [eHMAC(eCiphertext)]
    """
    # [16-bytes] Write External IV
    # enc.write(self.__eCipher.iv)
    fileHandle.write(self.__eIV)

    # [48-bytes] Write External Encrypted (Internal IV + Internal Key)
    # encipheredInternals = self._encrypt_without_padding(iCipher.iv+iKey)
    encipheredInternals = self._encrypt_without_padding(iv+key)
    fileHandle.write(encipheredInternals)

    # [32-bytes] Write External Key HMAC of ^encipheredInternals
    hashedInternals = self.__eHMAC.update(encipheredInternals).digest()
    fileHandle.write(hashedInternals)
```

Reversing and unpacking the decryption scheme implementation carries with it a few additional steps. Once the external initialization vector is extracted we can recreate the original password by thrusting the externally supplied key and the extracted external iv (which acts as the salt), through the same Key-Derivation Function we used to strengthen and stretch our original plaintext password key.

Once the password is successfully recreated from the key and iv, we can now check the HMAC of the encrypted internal key and iv. To do this we extract the next 48 bytes of data after the external key position, this is our externally enciphered internal key and iv which was used to encrypt the file itself. After this we extract our HMAC tag housed within the next 32 bytes of data.

Finally we test the integrity of the externally enciphered internal key & iv by passing it into the HMAC function as the message and verifying the 32 byte tag against the encrypted data. The result will determine the continuation of our program flow. If ValueError is raised the data is either corrupt or compromised.

```python
def _scheme_unpack(self, inFilePath, fileHandle):
    # [80][16-bytes] Extract external IV stored within file
    eIV = fileHandle.read(16)

    """
    With the extracted external IV, and the provided key
    we can recreate the external password with the scrypt KDF method
    """
    ePassword = self._key_derivation_scrypt(self.__eKey, eIV)

    # [128][48-bytes] Extract externally Encrypted Internal IV & Key
    encipheredInternals = fileHandle.read(48)
    
    # [160][32-bytes] Extract externally Hashed encipheredInternals
    hashedInternals     = fileHandle.read(32)

    """
    Recalculate & verify external HMAC of encipheredInternals
    """
    eHMAC   = HMAC.new( ePassword, encipheredInternals, digestmod=SHA256 )
    try:
        eHMAC.verify( hashedInternals )
    except ValueError:
        print("Compromised!")

```

At this point in the program flow, if the encrypted data verified successfully, we can proceed to the recreation of the external cipher object used to encrypt the internal key and iv. We need this external cipher object first so we can unlock the internal mechanisms responsible for the file encryption and thus future decryption of the file data.

Once the external cipher object is recreated with the password and external iv, we can decrypt the externally enciphered internal key and iv into the decipheredInternals variable. The first 16-bytes of this variable will hold the decrypted internal iv, and the last 32 bytes will house the decrypted 32-byte key.

We can then recreate the internal cipher object with this externally decrypted internal key and iv. This will be used to decrypt our encrypted binary.

```python
    """
    Decrypt Main Internal IV & Key within encipheredInternals
    """
    eCipher             = AES.new(ePassword, AES.MODE_CBC, eIV)
    decipheredInternals = self._decrypt_without_padding(encipheredInternals, eCipher)
    iIV                 = decipheredInternals[:16] # 16 Byte IV
    iKey                = decipheredInternals[16:] # 32 Byte Key (May also be 24, 16)

    """ 
    Recreate Internal Cipher Object & HMAC
    """
    iCipher = AES.new(iKey, AES.MODE_CBC, iIV)
    iHMAC   = HMAC.new(iKey, digestmod=SHA256)

    return iCipher, iHMAC
```

# **File Encryption**

Finally we reach the actual file encryption method. Essentially we are going to go through the file buffer size by buffer size until all of our plain text from the inFilePath has been converted to ciphertext, updated HMAC, and written to the outFilePath encrypted binary. The method is the same as our previous hash checking and file copying digressions with an encryption twist. We will be keeping track of the last blocks need for padding with the lastBlockPadded variable, this variable will show non-zero if the size of the last block was not a multiple of AES blocksize. Its main purpose is to aid in decryption of the last block, to allow us to know if we need to apply the unpad function.

```python
@file_checks
def encrypt_file(self, inFilePath, outFilePath, bufSize=2**16):
    iKey    = get_random_bytes( AES.key_size[-1] )
    iCipher = AES.new ( iKey, AES.MODE_CBC     )
    iHMAC   = HMAC.new( iKey, digestmod=SHA256 )
    # iCipher.iv

    try:
        with open( inFilePath , "rb" ) as dec, \
             open( outFilePath, "wb" ) as enc:

            # [64-bytes] Write Stamp
            self._stamp(enc)

            # [96-bytes] Write Decryption Scheme Into File
            self._scheme(enc, iCipher.iv, iKey)

            """
            Internal Encryption of Plaintext
            
            [iCiphertext(FILE)] [lastBlockPadded] [iHMAC(iCiphertext)]
            """

            # Iterate over Plaintext Bytes Representation
            # Encrypt Plaintext (Multiple of AES Blocksize)
            while True:
                buffer    = dec.read(bufSize)
                bytesRead = len(buffer)

                # Exit loop on EOF
                if not bytesRead:
                    break
                
                # Upon decryption, if non-zero, unpad
                lastBlockPadded = bytes([ bytesRead % AES.block_size ])

                # Retrieve ciphertext
                cipherText = self._encrypt(bytesRead, buffer, iCipher)

                # Update Internal Key HMAC (Ciphertext)
                iHMAC.update(cipherText)

                # Write Internal Encrypted Data
                enc.write(cipherText)

            # [ 1-byte ] Write Incongruence
            enc.write(lastBlockPadded)

            # [32-bytes] Write Internal Key HMAC of Ciphertext
            enc.write(iHMAC.digest())

    except:
        raise IOError("File Encryption Failed!")
```

# **File Decryption**

Imagine we have a `96-byte ciphertext ending at index 95` stored quaintly within our encrypted binary which has a total `file size of 129-bytes`. We know that after the 95th index we will find our lastBlockPadded boolean, then our 32-byte HMAC tag. We `set the buffer size to 32-bytes` and iterate through the encrypted binary. How do we know when to stop? How do we know when we are eating into the wrong portions of data?

The gist of the decryption method will rely on the following logic. Before reading the data in, we measure said data to ensure we are not eating into the last block. We can achieve this by calculating ciphertext offsets. 

```python
# Calculate CipherText offsets
fileSize    = os.path.getsize(inFilePath)
cipherBegin = enc.tell()
cipherEnd   = fileSize  - ((1<<5)+1)
cipherSize  = cipherEnd - cipherBegin
```
During iteration there will be three conditions we can come across when reading in the encrypted binary. The first and most encountered will be the condition such that the current position is less than the cipherEnd even after the bufSize is consumed, in which case we simply read buffer size. 

The second condition being the moment that the first condition is no longer true, which will force our program to play it safe by consuming the bare minimum buffer size equivalent to AES blocksize, the smallest multiple of itself. This is done so we do not over extend into the last block which we have set aside for special processing in the else clause.

In all conditions we do not indiscriminately read buffer size, but instead we must measure its outcome beforehand to prevent encroaching into the territory of the last block, padding boolean, and HMAC tag.

```python
while True:
    # Up to deficient buffer
    if f.tell() < cipherEnd - bufSize:
        cipherTextBuffer = f.read(bufSize)

    # Deficient buffer, read data 16 bytes at a time
    # Up to last block
    elif f.tell() < cipherEnd - AES.block_size:
        cipherTextBuffer = f.read(AES.block_size)

    # last block
    else:
        # handle last 16-bytes
        # handle padding boolean
        # handle HMAC tag
```
# Visualizing Decryption

The following is not a data structure used in the program or any program for that matter, but a visualization or visual aid to help understand what's happening as we iterate over the encrypted binary. Each byte of data is represented by square brackets containing its index within the imaginary file. We start by consuming the first 32 bytes of data according to our buffer size, this would be byte positions 0 - 31 when you take into account the offset.

This would have been executed under condition `f.tell() < cipherEnd - bufSize` because 0 is less than the cipherEnd (96 total bytes) less the bufSize. This would look something like f.tell(0) < cipherEnd(96) - bufSize(32) or 0 < 64 which is True. The result is a read on bufSize in full.

```python
# A: f.tell(0); f.read(32)
[  0], [  1], [  2], [  3], [  4], [  5], [  6], [  7], 
[  8], [  9], [ 10], [ 11], [ 12], [ 13], [ 14], [ 15], 
[ 16], [ 17], [ 18], [ 19], [ 20], [ 21], [ 22], [ 23], 
[ 24], [ 25], [ 26], [ 27], [ 28], [ 29], [ 30], [ 31], 
```

This brings us to position 32 and the beginning of our next 32-byte buffer (32 - 63). if f.tell(32) < cipherEnd(96) - bufSize(32). the condition once again evaluates as True since 32 < 64 True. Once again we allow the program to read another 32-bytes.

```python
# f.tell(32); f.read(32), 
[ 32], [ 33], [ 34], [ 35], [ 36], [ 37], [ 38], [ 39], 
[ 40], [ 41], [ 42], [ 43], [ 44], [ 45], [ 46], [ 47], 
[ 48], [ 49], [ 50], [ 51], [ 52], [ 53], [ 54], [ 55], 
[ 56], [ 57], [ 58], [ 59], [ 60], [ 61], [ 62], [ 63], 
```
The position is now standing at index 64 and we know that if f.tell(64) < cipherEnd(96) - bufSize(32) or 64 < 64 is False, so what happens next is the control flow tests the elif f.tell(64) < cipherEnd(96) - AES.block_size(16) or 64 < 80 which is True and we read AES blocksize (16-bytes) instead of bufSize (32-bytes).

```python
# f.tell(64); f.read(16)
[ 64], [ 65], [ 66], [ 67], [ 68], [ 69], [ 70], [ 71], 
[ 72], [ 73], [ 74], [ 75], [ 76], [ 77], [ 78], [ 79],
```

At position 80 we test if f.tell(80) < cipherEnd(96) - bufSize(32) or 80 < 64 which is False, then elif f.tell(80) < cipherEnd(96) - AES.block_size(16) or 80 < 80 which is also False. We find ourselves in the else clause of the last block to be processed. This last 16-byte block represents the last block of the ciphertext and the block which we must test for padding.
```python
# Last 128-bit (16-byte) Block of ciphertext  
[ 80], [ 81], [ 82], [ 83], [ 84], [ 85], [ 86], [ 87], 
[ 88], [ 89], [ 90], [ 91], [ 92], [ 93], [ 94], [ 95],
```
We then f.read(1) within the same else clause to extract the lastBlockPadded Boolean, this will help us decide to unpad or not in the decryption routine.
```python
# LastBlockPadded Boolean
[ 96],
```
Finally the 32-byte Hash-Based Message Authentication Code Tag is extracted within the same else clause on the same iteration as the last 17 bytes before we break out of the infinite loop.
```python
# Hashed-based Message Authentication Code
[ 97], [ 98], [ 99], [100], [101], [102], [103], [104], 
[105], [106], [107], [108], [109], [110], [111], [112], 
[113], [114], [115], [116], [117], [118], [119], [120], 
[121], [122], [123], [124], [125], [126], [127], [128]
```

# **File Decryption Method**

```python
@file_checks
def decrypt_file(self, inFilePath, outFilePath, bufSize=2**16):

    try:
        with open( inFilePath , "rb" ) as enc, \
             open( outFilePath, "wb" ) as dec:

            # [64-bytes] Stamp Handling
            self._stamp_unpack(enc)

            # [160][96-bytes] External Decryption Scheme Handling
            iCipher, iHMAC = self._scheme_unpack(inFilePath, enc)

            # Calculate CipherText offsets
            fileSize    = os.path.getsize(inFilePath)
            cipherBegin = enc.tell()
            cipherEnd   = fileSize  - ((1<<5)+1)
            cipherSize  = cipherEnd - cipherBegin

            if cipherSize % AES.block_size != 0:
                raise ValueError("Ciphertext Corrupt!")
            
            while True:
                # Up to deficient buffer
                if enc.tell() < cipherEnd - bufSize:
                    cipherTextBuffer = enc.read(bufSize)

                # Deficient buffer, read data 16 bytes at a time
                # Up to last block
                elif enc.tell() < cipherEnd - AES.block_size:
                    cipherTextBuffer = enc.read(AES.block_size)

                # last block
                else:
                    # Extract Last Block, handle empty file on else
                    if enc.tell() != cipherEnd:
                        cipherTextBuffer = enc.read(AES.block_size)
                    else:
                        cipherTextBuffer = b''
                    iHMAC.update(cipherTextBuffer)
                    
                    # Extract Incongruence
                    lastBlockPadded = int.from_bytes( enc.read(1), "big" )

                    # Decrypt Last Block in context to Incongruence
                    if not lastBlockPadded:
                        plainText = self._decrypt_without_padding(cipherTextBuffer, iCipher)
                    else:
                        plainText = self._decrypt_with_padding(cipherTextBuffer, iCipher)

                    # Write Last Block
                    dec.write(plainText)
                    
                    # Extract Internally Hashed CipherText HMAC
                    internalHMAC = enc.read(32)

                    # Verify Internal iHMAC with Extracted Internal HMAC
                    try:
                        iHMAC.verify(internalHMAC) # Raises ValueError if MAC Bad
                    except ValueError:
                        print("Compromised!")

                    break

                iHMAC.update(cipherTextBuffer)

                plainText = self._decrypt_without_padding(cipherTextBuffer, iCipher)
                dec.write(plainText)

    except:
        raise IOError("File Decryption Failed!")
```