# 61. Şüpheli Web Trafiği

**Kategori:** Forensics / PCAP / HTTP
**Konu:** Trafik kaydında normal istekler arasında sıra dışı bir HTTP isteği.

## Çözüm

Trafik kaydı HTTP istekleri açısından incelendi. Normal ağ trafiği arasında `example.com` adresine yapılan sıra dışı bir `curl` isteği görüldü:

```http
GET /?flag=NETWORK_TRACE HTTP/1.1
```

URL parametresindeki `flag` değeri olayla ilişkili değeri veriyordu:

```
NETWORK_TRACE
```

## Flag

```
ISUCTF{NETWORK_TRACE}
```
