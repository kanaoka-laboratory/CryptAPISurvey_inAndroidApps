Survey of cryptographic APIs in Android
====
日本語版READMEは[こちら](/README-jp.md)

Usable security research targeting software developers is becoming more and more active.
Among them, research focusing on how developers use cryptography has been attracting attention. 
These studies focused on specific cryptographic techniques (e.g., algorithms, IVs, and block cipher modes of operation of symmetric key cryptography) to explore their appropriate use. 

The main use of cryptography in software is through the use of cryptographic libraries, but it is not yet known which cryptographic libraries are used and how they are used in actual software.

In this page, we introduce the results of our survey, and the data and tools related to the survey.

## AndroZoo

Androzoo is a service that collects android applications and provides them.
As of September 1, 2021, it is reported to hold 16,370,174 APK files.
In this study, we use the data from Androzoo to analyze the applications.

See [AndroZoo](/androzoo/) for details.

## Tools

In this study, we convert APK files of Android applications to Smali files and statically analyze the contents of the Smali files.
For the conversion to Smali files, we used [apktool](https://ibotpeaches.github.io/Apktool/).

## Programs

The program used for the analysis in this study will be available (Sep 1, 2021).

## Crypt API List

This is a list of third-party cryptographic libraries that are frequently used in Android applications, as revealed by the analysis in this study.
The libraries provided by Android and Java (java.security, javax.crypto, androidx.security.crypto) are not included here.

As a result of our analysis and research, cryptographic libraries can be divided into three categories

- **Cryptographic libraries**: libraries that are developed and provided for the purpose of providing cryptographic technology.
- **Cryptographic function-providing libraries**: libraries that contain classes and methods for cryptographic functions to support the original purpose
- **Proprietary libraries**: libraries developed for in-house applications

### Cryptographic libraries

|Library Name| Package Name| Description | URL |
----|----|----|----
| Spongy Castle | org.spongycastle | The Android platform uses a cut-down version of BouncyCastle (without some features) for the JCE cryptographic provider, so you can't use all the features of BouncyCastle. A stock library of BouncyCastle with small changes to make it work on Android. | https://rtyley.github.io/spongycastle/ |
| Bouncy Castle | org.bouncycastle | The Android platform has adopted it as an encryption provider without some of its functions. For some reason, some apps seem to be calling BouncyCastle directly. | https://www.bouncycastle.org/ |
| SQL Cipher | net.sqlcipher | An open source SQL encryption library, also available for Android. | https://www.zetetic.net/sqlcipher/sqlcipher-for-android/ |
| JOSE: Javascript Object Signing and Encryption | com.nimbusds.jose | TOSE is a standard for encrypting and digitally signing JSON data. There are libraries available for its data representation and purposes. | https://connect2id.com/products/nimbus-jose-jwt |
| Conceal | com.facebook.crypto.cipher | Facebook's cryptography library But it's not maintained anymore (supposedly). | https://github.com/facebookarchive/conceal |
| Conscrypt | org.conscrypt | One of the Java Security Providers. It is developed by Google. | https://github.com/google/conscrypt | 


### Cryptographic function-providing libraries
|Library Name| Package Name| Description | URL |
----|----|----|----
|Amazon AWS S3 Client|com.amazonaws.services |Client library for AWS S3, with several Crypto-related classes.|https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/index.html?com/amazonaws/services/s3/AmazonS3Client.html|
|okhttp|okhttp|HTTP library, where cryptography is used by TLS-related classes.
Many applications have been found to include okhttp in their own application packages.|https://square.github.io/okhttp/|
|AWS Key Management Service (AWS KMS)|com.amazonaws.services.kms|A library for AWS key management. Allows key management and encryption.|https://docs.aws.amazon.com/AWSJavaSDK/latest/javadoc/index.html?com/amazonaws/services/kms/package-summary.html|
|ExoPlayer|com.google.android.exoplayer2|Third-party audio and video libraries for Android. It has cryptography-related classes.|https://developer.android.com/guide/topics/media/exoplayer|
|Apache HTTP Client|org.apache.http.auth, org.apache.hc.client5.http.auth|Apache's HTTP client library, with NTRM-related methods for invoking cryptography.|https://hc.apache.org/|
|greenDAO|org.greenrobot.greendao.database|Implementation of an object-oriented DB. Encryption features are provided.|https://github.com/greenrobot/greenDAO|
|Visual Studio App Center|com.microsoft.appcenter.utils.crypto|A library that supports the creation of apps for Android, iOS, macOS, Windows, etc. There are cryptography-related packages.|https://github.com/microsoft/appcenter-sdk-android|
|Signal|org.thoughtcrime.securesms|The database-related part of Signal provides functions related to SQL encryption.|https://github.com/signalapp/Signal-Android|
|Realm|io.realm|Database used for mobile systems, with Android library. The database (Realm file) can be encrypted.|https://realm.io/
|Zip4j|net.lingala.zip4j.crypto|Library for ZIP. There is an encryption part.|https://github.com/srikanth-lingala/zip4j
|Java MP4 Parser|org.mp4parse, com.mp4parser|MP4 library for Java. Includes methods for encryption and decryption.|https://github.com/sannies/mp4parser|
|kObjects|org.kobjects.crypt|A collection of libraries for embedded and mobile Java, including the Crypt package in Utilities.|https://kobjects.org/|
|Apache Common Codes|org.apache.commons.codec.digest|Common Encoders/Decoders, such as Base64 and Hex libraries. There is a library of message digests (hash functions).|https://commons.apache.org/proper/commons-codec/|
|Igexin|com.igexin.push.util|Android's library for ads. But news in 2017 that spyware has been embedded in it.||
|iText|com.itextpdf.text.pdf|A library for working with PDF. Multi-functional PDF engine. Includes classes for PDF encryption.|https://itextpdf.com/|

### Proprietary libraries


## Data

## Tips

## Result

## Publication

Akira Kanaoka, Mamoru Abe, "***A Large-Scale Survey of Cryptographic Library Usage in Android Applications***", Computer Security Symposium 2021, 2021 (to appear) (published in Japanese)

## Contact

Akira Kanaoka (Toho University)
akira.kanaoka@is.sci.toho-u.ac.jp

## Acknowledgement
This work was supported by JSPS KAKENHI Grant Number JP19K11972, JP19H04111, and JP19H04101.