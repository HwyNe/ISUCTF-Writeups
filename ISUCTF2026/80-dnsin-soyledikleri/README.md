# 80. DNS'in Söyledikleri

**Kategori:** Forensics / PCAP / DNS Tunneling
**Konu:** Firewall özetinde yüksek DNS hacmi üreten istemci kritik; uzun subdomain'ler sıra numarasıyla parçalanmış Base32 veri.

## Çözüm

Firewall özetinde dikkat çeken istemci:

```
10.44.18.23 → 10.44.0.53:53 udp count=184
```

PCAP içinde bu istemcinin sıra numaralı uzun DNS sorguları:

```
001.mnqxgzj5irhfgl.tunnel.lab.ctf
002.jwgiydw5dpnnsw.tunnel.lab.ctf
003.4plenzzv65dvnz.tunnel.lab.ctf
004.swyx3tnfzgc43j.tunnel.lab.ctf
```

Parçalar sıra numarasına göre birleştirildi:

```
MNQXGZJ5IRHFGLJWGIYDW5DPNNSW4PLENZZV65DVNZSWYX3TNFZGC43J
```

Base32 decode:

```
case=DNS-620;token=dns_tunel_sirasi
```

Vault için normalize edilen solution key:

```
DNS620_dns_tunel_sirasi
```

## Flag

```
ISUCTF{E9PZSX-6WWZE9-8WS2MS}
```
