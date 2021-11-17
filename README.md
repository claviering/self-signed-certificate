# 使用 openssl 自签签名

修改 `root.conf` 生成根域名证书

修改 `server.conf` 生成服务器证书

直接用根证书签发域名证书

`openssl x509 -req -in server.csr -CA root.crt -CAkey root.key -CAcreateserial -out server.crt -days 3650 -sha384 -extfile v3.ext`

系统导入根证书

# using openssl self-signed certificate

change `root.conf` to make youself root certificate

change `server.conf` to make youself server certificate

only signed using root certificate

`openssl x509 -req -in server.csr -CA root.crt -CAkey root.key -CAcreateserial -out server.crt -days 3650 -sha384 -extfile v3.ext`

system inport root certificate

## Usage

`$ ./make.sh`

## Warning

Requirements for trusted certificates in iOS 13 and macOS 10.15

Learn about new security requirements for TLS server certificates in iOS 13 and macOS 10.15.

All TLS server certificates must comply with these new security requirements in iOS 13 and macOS 10.15:

- TLS server certificates and issuing CAs using RSA keys must use key sizes greater than or equal to 2048 bits. Certificates using RSA key sizes smaller than 2048 bits are no longer trusted for TLS.
- TLS server certificates and issuing CAs must use a hash algorithm from the SHA-2 family in the signature algorithm. SHA-1 signed certificates are no longer trusted for TLS.
- TLS server certificates must present the DNS name of the server in the Subject Alternative Name extension of the certificate. DNS names in the CommonName of a certificate are no longer trusted.
Additionally, all TLS server certificates issued after July 1, 2019 (as indicated in the NotBefore field of the certificate) must follow these guidelines:

- TLS server certificates must contain an ExtendedKeyUsage (EKU) extension containing the id-kp-serverAuth OID.
- TLS server certificates must have a validity period of 825 days or fewer (as expressed in the NotBefore and NotAfter fields of the certificate).
Connections to TLS servers violating these new requirements will fail and may cause network failures, apps to fail, and websites to not load in Safari in iOS 13 and macOS 10.15.

Published Date: November 03, 2019

https://support.apple.com/en-us/HT210176

## 注意

iOS 13 和 macOS 10.15 中的可信证书应满足的要求

了解 iOS 13 和 macOS 10.15 中的 TLS 服务器证书应满足的新安全要求。

在 iOS 13 和 macOS 10.15 中，所有 TLS 服务器证书都必须符合这些新的安全要求：

- 使用 RSA 密钥的 TLS 服务器证书和签发证书的 CA 必须使用长度大于或等于 2048 位的密钥。TLS 不再信任所用 RSA 密钥长度小于 2048 位的证书。
- TLS 服务器证书和签发证书的 CA 必须在签名算法中使用 SHA-2 系列中的哈希算法。TLS 不再信任 SHA-1 签名的证书。
- TLS 服务器证书必须在证书的“使用者备用名称”扩展中显示服务器的 DNS 名称。证书的 CommonName 中的 DNS 名称不再受信任。
此外，所有在 2019 年 7 月 1 日后签发的 TLS 服务器证书（如证书的 NotBefore 字段中所示）必须遵循以下准则：

- TLS 服务器证书必须包含一个内含 id-kp-serverAuth OID 的 ExtendedKeyUsage (EKU) 扩展。
- TLS 服务器证书的有效期必须为 825 天或更短（如证书的 NotBefore 和 NotAfter 字段中所示）。
违反上述新要求的 TLS 服务器连接将失败，并可能导致网络出现故障、应用无法运行，以及在 iOS 13 和 macOS 10.15 的 Safari 浏览器中无法载入网站。

发布日期： 2019 年 06 月 28 日

https://support.apple.com/zh-cn/HT210176

