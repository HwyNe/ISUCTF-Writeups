# 15. Sessiz Kanal — DNS Exfiltration

**Kategori:** Forensics / PCAP / Threat Hunting
**Konu:** DNS Tunneling tekniği; veri subdomain'e parçalanarak encode edilip zararsız görünen domainlere sorgu atılır. Firewall'dan geçer, IDS tespitini zorlaştırır.

## Çözüm

PCAP'taki 425 paketten 24'ü DNS sorgusuydu. Normal mDNS, Spotify ve Epic Games sorguları arasına 5 anormal sorgu gizlenmişti:

```
part1-ISUC.localhost.
part2-TF26.localhost.
part3-DNS.localhost.
part4-TUNNEL.localhost.
part5-TRACE.localhost.
```

Klasik DNS Tunneling pattern'i:

- Subdomain olarak veri parçalanıp encode ediliyor
- `*.localhost` gibi zararsız görünen domainlere sorgu atılıyor
- Her sorgu gerçek DNS çözümlemesi gerektirmiyor — firewall geçişli
- Normal trafiğin içine dağıtılmış — anomaly tespitini zorlaştırıyor

Subdomain parçaları sıra numarasına göre birleştirildi:

```
ISUC + TF26 + DNS + TUNNEL + TRACE
```

## Flag

```
ISUCTF{DNS_TUNNEL_TRACE}
```
