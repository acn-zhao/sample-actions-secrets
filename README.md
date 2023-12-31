# Sample to use Secrets in Actions
Refs: [using-secrets-in-a-workflow](https://docs.github.com/en/actions/security-guides/using-secrets-in-github-actions#using-secrets-in-a-workflow)

## Create a certificate.crt file for test

```shell
openssl genrsa -out private.key 2048
openssl req -new -key private.key -out csr.csr
openssl req -x509 -sha256 -days 365 -key private.key -in csr.csr -out certificate.crt

# show the info
openssl x509 -in certificate.crt -text -noout
```

## Convert that crt file to base64 for storing into Secrets
On MacOS, you could run:
```
base64 -i certificate.crt -o certificate.crt.base64
```
On Linux, you could run:
```
base64 -w 0 certificate.crt > certificate.crt.base64
```

## Store the base64 string into Github's Secrets
![image](https://github.com/acn-zhao/sample-actions-secrets/assets/148947221/e79e6bee-d08c-4384-ae2a-feb2088f03f7)
![image](https://github.com/acn-zhao/sample-actions-secrets/assets/148947221/54c2e99d-c666-4821-a01e-c2421ee23788)


