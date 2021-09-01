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
The libraries provided by Android and Java (java.security, javax.crypto, andro) are not included here.

As a result of our analysis and research, cryptographic libraries can be divided into three categories

- Cryptographic libraries: libraries that are developed and provided for the purpose of providing cryptographic technology.
- Cryptographic function-providing libraries: libraries that contain classes and methods for cryptographic functions to support the original purpose
- Proprietary libraries: libraries developed for in-house applications

### Cryptographic libraries

### Cryptographic function-providing libraries

### Proprietary libraries


## Data

## Tips

## Result

## Publication

Akira Kanaoka, Mamoru Abe, "*A Large-Scale Survey of Cryptographic Library Usage in Android Applications*", Computer Security Symposium 2021, 2021 (to appear) (published in Japanese)