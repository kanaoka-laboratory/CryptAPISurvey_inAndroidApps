Androidアプリケーションにおける暗号ライブラリ利用状況の調査
====
English version of README is [here](/README.md)

開発者を対象にしたユーザブルセキュリティ研究が活発になっており、その中でも開発者が暗号技術をどのように利用しているかに焦点を当てた研究が注目されている。これらの研究では特定の暗号技術（例：共通鍵暗号のアルゴリズム、IV、暗号利用モード）に焦点を当ててその適切利用についての調査や対処が行われていた。

ソフトウェアにおける暗号技術の利用は暗号ライブラリを利用することが主となっているが、暗号ライブラリが実際のソフトウェアにおいてどのライブラリがどれほど利用されどう利用されているかはまだわかっていない。

金岡研究室では、Androidアプリケーションにおいて暗号技術がどう利用されているかの大規模調査をしている。
このページではその調査の結果や、調査に関するデータやツールを紹介する。

## AndroZoo
AndrozooはAndroidアプリケーションを収集しそれを提供しているサービスである。
2021年9月1日現在、16,370,174のAPKファイルを収集しているとされている。
本研究では、Androzooで収集されたデータを用いてアプリケーションの分析を行った。

詳細に関しての詳細は[Androzoo](/androzoo/)を参照。

## 利用ツール
本研究では、AndroidアプリケーションのAPKファイルをSmaliファイルに変換し、Smaliファイルの内容を静的解析している。
Smaliファイルへの変換は、[apktool](https://ibotpeaches.github.io/Apktool/)を利用した。

## 作成したプログラム、スクリプト

本研究で解析に利用したプログラムやスクリプトを後日公開します（2021年9月1日）。

## 暗号APIリスト
本研究の解析により明らかになったAndroidアプリケーションで利用される頻度の高いサードパーティ製暗号ライブラリ群を示す。
なお、AndroidやJavaにより提供されるライブラリ（java.security, javax.crypto, androidx.security.crypto) はここに含まれていない。

我々の解析と調査の結果、暗号ライブラリは以下の3つに分類できる。
- **暗号ライブラリ**：暗号技術を提供する目的で開発され提供されているライブラリ
- **暗号機能提供ライブラリ**：本来の提供機能をサポートする目的で暗号機能のクラスやメソッドを含んでいるライブラリ
- **独自ライブラリ**：自社用アプリケーション用に開発されたライブラリ


### 暗号ライブラリ

|Library Name| Package Name| Description | URL |
----|----|----|----
| Spongy Castle | org.spongycastle | The Android platform uses a cut-down version of BouncyCastle (without some features) for the JCE cryptographic provider, so you can't use all the features of BouncyCastle. A stock library of BouncyCastle with small changes to make it work on Android. | https://rtyley.github.io/spongycastle/ |
| Bouncy Castle | org.bouncycastle | The Android platform has adopted it as an encryption provider without some of its functions. For some reason, some apps seem to be calling BouncyCastle directly. | https://www.bouncycastle.org/ |
| SQL Cipher | net.sqlcipher | An open source SQL encryption library, also available for Android. | https://www.zetetic.net/sqlcipher/sqlcipher-for-android/ |
| JOSE: Javascript Object Signing and Encryption | com.nimbusds.jose | TOSE is a standard for encrypting and digitally signing JSON data. There are libraries available for its data representation and purposes. | https://connect2id.com/products/nimbus-jose-jwt |
| Conceal | com.facebook.crypto.cipher | Facebook's cryptography library But it's not maintained anymore (supposedly). | https://github.com/facebookarchive/conceal |
| Conscrypt | org.conscrypt | One of the Java Security Providers. It is developed by Google. | https://github.com/google/conscrypt | 


### 暗号機能提供ライブラリ
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

### 独自ライブラリ
|Library Name| Package Name| Description | URL |
----|----|----|----
| &lt;unknown&gt; | net.idt.um.android.api.com.config |  Details unknown. Doesn't come up directly in the search. Applications called net.idt.um.android.bossrevapp comes up. Possibly a library made by a development company. ||
| Tencent Open Platform | com.tencent.utils, com.tencent.open.utils |It may be a framework for Tencent's development support. There seems to be an implementation of the encryption part, but we couldn't find it even after much searching. Rather than being completely open, it may be something you can get by applying.||
| Tencent Cloud: Tencent Push Notification Service | com.tencent.android.tpush.encrypt | There is an API for implementing message push as Tencent's SDK, but there's no information on the specifics. ||
| Alipay wireless SDK | com.alipay.sdk.encrypt | Alipay's SDK, but it doesn't seem to be available to the public. There is a decompiled version on Github. https://github.com/XClouded/alipay ||
| &lt;unknown&gt; | com.baidu.location | Baidu's location library? Encryption seems to be one of the methods there. | |Cutie Garden| com.cutie.merge.garden | Android application (game). The method has decrypt ||

## データ
本研究に関連するデータを掲載する。
データ掲載はスペースの問題で論文に記載できなかったものを掲載することと、解析結果の再現性を担保することを目的としている。

詳細は[Data](/data/) を参照。

## Tips

*TBD*

## 結果
本研究での解析結果の詳細を掲載する。
データ掲載はスペースの問題で論文に記載できなかったものを掲載することを目的としている。

詳細は[Result](/result/) を参照。


## Publication

金岡 晃、阿部 衛：Androidアプリケーションにおける暗号ライブラリ利用状況の大規模調査、コンピュータセキュリティシンポジウム2021（CSS2021）、2021 (発表予定) 

## Contact

金岡 晃（東邦大学）
akira.kanaoka@is.sci.toho-u.ac.jp

## Acknowledgement
本研究の一部はJSPS科研費 JP19K11972、JP19H04111、JP19H04101の助成を受けたものです。