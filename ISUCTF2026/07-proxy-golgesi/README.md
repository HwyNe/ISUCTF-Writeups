# 07. Proxy Gölgesi

**Kategori:** Forensics / Ağ Analizi
**Konu:** Proxy loglarında normal trafik arasına gizlenmiş tek şüpheli istek.

## Çözüm

`proxy_access.log` içinde 5000 satıra yakın istek vardı. Domain ve URL pattern'leri tarandığında sıra dışı bir istek dikkat çekti:

```
https://internal-report.ctf.local/retrieve?ref=PROXY-HIT-322&token=a3f9c12e
```

`ref` parametresi doğrudan olay değerini taşıyordu:

```
PROXY-HIT-322
```

## Flag

```
ISUCTF{PROXY-HIT-322}
```
