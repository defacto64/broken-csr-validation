# broken-csr-validation
This repository is for keeping track of a number of software tools/libraries/packages that do not respect RFC2986 in verifying the signature on Certificate Signing Requests (CSRs).


Environment | Software | Version | Result
------------| ---------| -------|-------
.NET|	BouncyCastle |1.8.2|	OK
.NET|	BouncyCastle |1.9.0|	OK
Java 1.8|	BouncyCastle| 1.46|	OK
Java 1.8|	BouncyCastle| 1.64|	KO
Java 1.8|	Oracle JRE/JDK (sun.security.pkcs10.PKCS10) |xx|	OK
Java 1.8|	Oracle Security Developer Tools| 19.3|	KO
Javascript|	PKI.js|	xx|OK
Linux|	GnuTLS (certtool)| 3.5.18|	KO
Linux|	Golang (crypto/x509)| 1.17.1|	OK
Linux|	OpenSSL |1.1.1|	OK
Windows|	CertEnroll.dll|xx|	OK
Windows|	CertUtil.exe|xx|	OK
Windows|	OpenSSL |3.0.0|	OK



