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

