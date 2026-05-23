# 62. Yanlış Protokol

**Kategori:** Forensics / PCAP / Cleartext Protocols
**Konu:** FTP gibi güvensiz protokollerde kimlik bilgileri düz metin geçer.

## Çözüm

PCAP dosyası incelendiğinde güvenli olmayan protokol olarak FTP trafiği görüldü.

`strings` ile hızlı kontrol:

```bash
strings internal_transfer.pcapng | grep -Ei "ftp|USER|PASS|220|331"
```

Dikkat çeken kayıtlar:

```
220 Welcome to the DLP Test FTP Server
USER admin
331 Please specify the password.
PASS CLEARTEXT_LOGIN_FOUND
530 Login incorrect.
```

FTP şifreleri şifrelenmeden geçtiği için `PASS` komutundaki parola değeri doğrudan flag'i veriyordu:

```
CLEARTEXT_LOGIN_FOUND
```

## Flag

```
ISUCTF{CLEARTEXT_LOGIN_FOUND}
```
