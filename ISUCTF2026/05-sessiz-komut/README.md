# 05. Sessiz Komut

**Kategori:** Forensics / Windows Log Analizi
**Konu:** Security, PowerShell, Sysmon ve DNS olaylarını birleştirerek tek bir saldırı zinciri çıkarmak.

## Çözüm

Arşivdeki dört log kaynağı birlikte tarandı:

```
Security_4624_4688.jsonl
PowerShell_Operational.evtx.json
Sysmon.jsonl
dns_client.log
```

Normal yönetim aktiviteleri arasında olay zincirinin sürekli tekrar eden marker'ı bulundu:

```
WIN17_decoded_ps_dnslabel
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{6AMDEH-YN2RVS-CD9KYV}
```
