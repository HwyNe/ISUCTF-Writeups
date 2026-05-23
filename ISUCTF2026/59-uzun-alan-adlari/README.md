# 59. Uzun Alan Adları

**Kategori:** Forensics / DNS Exfiltration
**Konu:** DNS sorgularında uzun subdomain'ler hex/base encoded veri taşıyor; seq numarasına göre birleştirildiğinde gizli payload çıkar.

## Çözüm

DNS sorguları incelendi. Normal trafik arasında seq numaralı uzun domain'ler bulundu:

```
seq01.<chunk>.tunnel.lab
seq02.<chunk>.tunnel.lab
...
```

`chunk` değerleri hex olarak çözüldü ve parçalar sırayla birleştirildi:

```
LONG-DNS-930
```

## Flag

```
ISUCTF{LONG-DNS-930}
```
