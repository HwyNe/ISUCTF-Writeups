# 08. Trafikteki Nesne

**Kategori:** Forensics / PCAP Analizi
**Konu:** Sıkıştırılmış HTTP transfer nedeniyle nesne doğrudan export edilemiyor; proxy + PCAP birlikte okunmalı.

## Çözüm

Arşivdeki dosyalar:

```
network_capture.pcapng
proxy_access.log
flag_vault.bin
sha256sums.txt
```

Proxy log'u indirilen dosyanın sıradan bir görsel gibi göründüğünü söylüyordu. Ancak TCP akışı + sıkıştırılmış transfer nedeniyle PCAP'tan doğrudan export çalışmıyordu. İki kaynak birlikte incelendiğinde olay marker'ı bulundu:

```
trf812_http_nesnesi_bulundu
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{86LNCZ-VGZ3VH-J4PEZA}
```
