# broken-csr-validation
This repository is for keeping track of a number of software tools/libraries/packages that do not respect RFC2986 in verifying the signature on Certificate Signing Requests (CSRs).

In the following table, a Result "OK" means that the software gives the correct result (such as "Failed", "Invalid" or the likes) on verifying a _wrong_ signature. Examples of CSRs carrying a wrong signature can be found in the "data" folder.


Environment | Software | Version | Result
------------| ---------| -------|-------
.NET|	BouncyCastle |1.8.2|	KO
.NET|	BouncyCastle |1.9.0|	KO
Java 1.8|	BouncyCastle| 1.46|	KO
Java 1.8|	BouncyCastle| 1.64|	**OK**
Java 1.8|	Oracle JRE/JDK (sun.security.pkcs10.PKCS10) |xx|	KO
Java 1.8|	Oracle Security Developer Tools| 19.3|	**OK**
Javascript|	PKI.js|	xx|KO
Linux|	GnuTLS (certtool)| 3.5.18|	**OK**
Linux|	Golang (crypto/x509)| 1.17.1|	KO
Linux|	OpenSSL |1.1.1|	KO
Windows|	CertEnroll.dll|xx|	KO
Windows|	CertUtil.exe|xx|	KO
Windows|	OpenSSL |3.0.0|	KO



