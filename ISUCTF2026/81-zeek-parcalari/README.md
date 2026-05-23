# 81. Zeek Parçaları

**Kategori:** Forensics / Zeek Logs
**Konu:** Zeek üç ana log üretir (conn, dns, http); aynı `uid` üzerinden tek olay üç dosyada takip edilir.

## Çözüm

Arşivde Zeek formatında üç log vardı:

```
conn.log
dns.log
http.log
```

### http.log

Normal domain'ler arasında tek farklı kayıt:

```
host:         internal.ctf.local
uri:          /report?ref=ZEEK-LINK-714&session=a3f9c12e
user_agent:   python-requests/2.31.0
status_code:  200
```

### conn.log

Aynı `uid` üzerinden bağlantı kaydı:

```
uid:     CxR7mK9pQ2fL
src:     10.10.2.88
dst:     10.10.5.7:80
service: http
state:   SF
```

Olayla ilişkili referans, URI içindeki `ref` parametresiydi:

```
ZEEK-LINK-714
```

## Flag

```
ISUCTF{ZEEK-LINK-714}
```
