# Ciphertext

---

Ciphertext is encrypted text transformed from plaintext using an encryption algorithm. Ciphertext can't be read until it has been converted into  plaintext (decrypted) with a key. The decryption cipher is an algorithm that transforms the ciphertext back into plaintext. The term cipher is sometimes used as a synonym for ciphertext. However, it refers to the method of encryption rather than the result.

**Types of ciphers**
There are various types of ciphers, including:

+ Substitution ciphers. Replace bits, characters, or character blocks in plaintext with alternate bits, characters or character blocks to produce ciphertext. A substitution cipher may be monoalphabetic or polyalphabetic:
  - A single alphabet is used to encrypt the entire plaintext message. For example, if the letter A is enciphered as the letter K, this will be the same for the entire message.
  - A more complex substitution using a mixed alphabet to encrypt each bit, character or character block of a plaintext message. For instance, the letter A may be encoded as the letter K for part of the message, but later it might be encoded as the letter W.
  
+ Transposition ciphers. Unlike substitution ciphers that replace letters with other letters, transposition ciphers keep the letters the same, but rearrange their order according to a specific algorithm. For instance, in a simple columnar transposition cipher, a message might be read horizontally but would be written vertically to produce the ciphertext.

+ Polygraphic ciphers. Substituting one letter for another letter, a polygraphic cipher performs substitutions with two or more groups of letters. This masks the frequency distribution of letters, making frequency analysis attacks much more difficult.

+ Permutation ciphers. In this cipher, the positions held by plaintext are shifted to a regular system so that the ciphertext constitutes a permutation of the plaintext.

+ Private-key cryptography. In this cipher, the sender and receiver must have a pre-shared key. The shared key is kept secret from all other parties and is used for encryption, as well as decryption. This cryptography is also known as "symmetric key algorithm."

+ Public-key cryptography. In this cipher, two different keys -- public key and private key -- are used for encryption and decryption. The sender uses the public key to perform the encryption, but the private key is kept secret from the receiver. This is also known as "asymmetric key algorithm."

**Uses of ciphertext**

Symmetric ciphers, which are typically used to secure online communications, are incorporated into many different network protocols to be used to encrypt exchanges. For example, Transport Layer Security uses ciphers to encrypt application layer data.

Virtual private networks connecting remote workers or remote branches into corporate networks use protocols with symmetric ciphers to protect data communications. Symmetric ciphers protect data privacy in most Wi-Fi networks, online banking, e-commerce services and mobile telephony.

Other protocols, including secure shell, OpenPGP and Secure/Multipurpose Internet Mail Extensions use asymmetric cryptography to encrypt and authenticate endpoints but also to securely exchange the symmetric keys to encrypt session data. For performance reasons, protocols often rely on ciphers to encrypt session data.

**Ciphertext attacks**

The known ciphertext attack, or ciphertext-only attack (COA), is an attack method used in cryptanalysis when the attacker has access to a specific set of ciphertext. However, in this method, the attacker doesn't have access to the corresponding cleartext, i.e., data that is transmitted or stored unencrypted. The COA succeeds when the corresponding plaintext can be determined from a given set of ciphertext. Sometimes, the key that's used to encrypt the ciphertext can be determined from this attack.

In a chosen ciphertext attack (CCA), the attacker can make the victim (who knows the secret key) decrypt any ciphertext and send back the result. By analyzing the chosen ciphertext and the corresponding plaintext they receive, the attacker tries to guess the secret key the victim used. The goal of the CCA is to gain information that diminishes the security of the encryption scheme.

Related-key attack is any form of cryptanalysis where the attacker can observe the operation of a cipher under several different keys whose values the attacker doesn't know initially. However, there is some mathematical relationship connecting the keys that the attacker does know.

**Ciphertext example**

One of the earliest and simplest ciphers is the Caesar cipher, which uses a symmetric key algorithm. The key acts as a shared secret between two (or more) parties that can be used to send secret information no one can read without a copy of the key.

The Caesar cipher is a substitution cipher in which each letter in the plaintext is "shifted" a certain number of places down the alphabet. For example, with a shift of 1, A would be B, B would be replaced by C, etc. The method is named after Julius Caesar, who is said to have used it to communicate with his generals.

Here is an example of the encryption and decryption steps involved with the Caesar cipher. The text to be encrypted is "defend the east wall of the castle," with a shift (key) of 1.

+ Plaintext: defend the east wall of the castle
+ Ciphertext: efgfoe uif fbtu xbmm pg uif dbtumf 


> **https://www.techtarget.com/whatis/definition/ciphertext**
