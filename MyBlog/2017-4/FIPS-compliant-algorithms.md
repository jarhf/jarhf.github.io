C# 程序遇到如下异常的解决办法
```
Exception has been thrown by the target of an invocation. ---> System.InvalidOperationException: This implementation is not part of the Windows Platform FIPS validated cryptographic algorithms
```

>最简单就是不用Md5，改用SHA1算法

# regedit

```
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\FipsAlgorithmPolicy]
"Enabled"=dword:00000000

```

# secpol.msc


```
Security Settings -> Local Policies -> Security Options -> 
System Cryptography:Use FIPS compliant algorithms for  encryption,hashing,signing    
Disable

```
>
System cryptography: Use FIPS 140 compliant cryptographic algorithms, including encryption, hashing and signing algorithms

For the Schannel Security Service Provider (SSP), this security setting disables the weaker Secure Sockets Layer (SSL) 
protocols and supports only the Transport Layer Security (TLS) protocols as a client and as a server (if applicable). 
If this setting is enabled, Transport Layer Security/Secure Sockets Layer (TLS/SSL) Security Provider uses only the FIPS
140 approved cryptographic algorithms: 3DES and AES for encryption, RSA or ECC public key cryptography for the TLS key
exchange and authentication, and only the Secure Hashing Algorithm (SHA1, SHA256, SHA384, and SHA512) for the TLS hashing
requirements.

For Encrypting File System Service (EFS), it supports the Triple Data Encryption Standard (DES) and Advanced Encryption 
Standard (AES) encryption algorithms for encrypting file data supported by the NTFS file system. By default, EFS uses the
Advanced Encryption Standard (AES) algorithm with a 256-bit key in the Windows Server 2003 and Windows Vista family and 
DESX algorithm in Windows XP for encrypting file data. For information about EFS, see Encrypting File System.

For Remote Desktop Services, it supports only the Triple DES encryption algorithm for encrypting Remote Desktop Services
network communication. 

 Note: Remote Desktop Services was called Terminal Services in previous versions of Windows Server.

For BitLocker, this policy needs to be enabled before any encryption key is generated. Recovery passwords created when 
this policy is enabled are incompatible with BitLocker on Windows 8, Windows Server 2012, and earlier operating systems.
If this policy is applied to computers running operating systems prior to Windows 8.1 and Windows Server 2012 R2, 
BitLocker will prevent the creation or use of recovery passwords; recovery keys should be used for those computers instead.

Default: Disabled.

Note: The Federal Information Processing Standard (FIPS) 140 is a security implementation designed for certifying 
cryptographic software. FIPS 140 validated software is required by the U.S. Government and requested by other prominent 
institutions.


>http://blog.aggregatedintelligence.com/2007/10/fips-validated-cryptographic-algorithms.html


# FIPS compliant Algorithms:

## Hash algorithms

*   HMACSHA1
*   MACTripleDES
*   SHA1CryptoServiceProvider

## Symmetric algorithms(use the same key for encryption and decryption)

*   DESCryptoServiceProvider
*   TripleDESCryptoServiceProvider

## Asymmetric algorithms(use a public key for encryption and a private key for decryption)

*   DSACryptoServiceProvider
*   RSACryptoServiceProvider

# Algorithms that are not FIPS compliant

*   HMACMD5
*   HMACRIPEMD160
*   HMACSHA256
*   HMACSHA384
*   HMACSHA512
*   MD5CryptoServiceProvider
*   RC2CryptoServiceProvider
*   RijndaelManaged
*   RIPEMD160Managed
*   SHA1Managed
