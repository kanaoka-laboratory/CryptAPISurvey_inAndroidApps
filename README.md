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
|Amazon AWS S3 Client|com.amazonaws.services |||
|okhttp|okhttp|||
|AWS Key Management Service (AWS KMS)|com.amazonaws.services.kms|||
|ExoPlayer|com.google.android.exoplayer2|||
|Apache HTTP Client|org.apache.http.auth, org.apache.hc.client5.http.auth|||
|greenDAO|org.greenrobot.greendao.database|||
|Visual Studio App Center|com.microsoft.appcenter.utils.crypto|||
|Signal|org.thoughtcrime.securesms|||
|Realm|io.realm|||
|Zip4j|net.lingala.zip4j.crypto|||
|Java MP4 Parser|org.mp4parse, com.mp4parser|||
|kObjects|org.kobjects.crypt|||
|Apache Common Codes|org.apache.commons.codec.digest|||
|Igexin|com.igexin.push.util|||
|iText|com.itextpdf.text.pdf|||

### Proprietary libraries


## Data

## Tips

## Result

## Publication

Akira Kanaoka, Mamoru Abe, "***A Large-Scale Survey of Cryptographic Library Usage in Android Applications***", Computer Security Symposium 2021, 2021 (to appear) (published in Japanese)

## Contact

Akira Kanaoka (Toho University)
akira.kanaoka@is.sci.toho-u.ac.jp
