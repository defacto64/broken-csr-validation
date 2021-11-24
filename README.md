# broken-csr-validation
This repository is for keeping track of a number of software tools/libraries/packages that do not _fully_ respect RFC2986 in verifying the signature on Certificate Signing Requests (CSRs) -- at least, this is my opinion. I may be wrong, but I am still waiting to see a sound counter-argument.

Most software capable of parsing CSRs do not check how a CSR is encoded (whether DER or BER): they just check that the signature was computed over the certificationRequestInfo element "AS IS" (as it appears in the CSR). This assumption is wrong, as a BER-encoded CSR (which is legitimate, although unfrequent) requires a more complex treatment. RFC2986, in fact, requires DER-encoding the certificationRequestInfo component prior to signing it, and consequently the _same processing should be done on verifying_ the signature by any software which offers a CSR verification function. In practice, some do and some don't, leading to interoperability problems.

In the following table, a Result "OK" means that the software gives what I consider the correct result (such as "Failed", "Invalid" or the likes) on verifying a _wrong_ signature, where wrong means cryptographically correct, but computed over the wrong data (as explained above).

Examples of CSRs carrying a wrong signature can be found in the "data" folder.
<br><br>

Environment | Software | Version | Result | Bug report
------------| ---------| -------|-------|------
.NET|	BouncyCastle C#|1.8.2|	KO
.NET|	BouncyCastle C#|1.9.0|	KO
Java |	BouncyCastle Java| 1.46|	KO
Java |	BouncyCastle Java| 1.64|	**OK**
Java |	Oracle JRE/JDK (sun.security.pkcs10.PKCS10) |1.8.0_311|	KO
Java |	OpenJDK (sun.security.pkcs10.PKCS10) |11.0.11|	KO
Java |	Oracle Security Developer Tools| 19.3|	**OK**
Javascript|	PKI.js|	...|KO
Javascript| forge| 0.7.0|KO
Linux|	GnuTLS (certtool)| 3.5.18|	**OK**
Linux|	Golang (crypto/x509)| 1.17.1|	KO|https://github.com/golang/go/issues/49519
Linux|	OpenSSL |1.1.1|	KO
Windows 10|	CertEnroll.dll|10.0.19041.746|	KO
Windows 10|	CertUtil.exe|10.0.19041.1|	KO
Windows 10|	OpenSSL |3.0.0|	KO |https://github.com/openssl/openssl/issues/17010
Windows 10|PKISolutions' PowerShell PKI Module|3.7|KO|https://github.com/PKISolutions/PSPKI/issues/162



