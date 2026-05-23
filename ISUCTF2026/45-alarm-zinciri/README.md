# 45. Alarm Zinciri

**Kategori:** SIEM / Korelasyon
**Konu:** Aynı olay farklı log kaynaklarında farklı alanlarda taşınıyor; üçü birleştirilince zincir tamamlanıyor.

## Çözüm

Üç farklı log kaynağı incelendi:

- `alerts.json` içinde `EVT-20501` event id bulundu
- `firewall.log` aynı `event_ref` değerini gösterdi
- `endpoint.log` aynı `chain_id` değerini doğruladı

Üç kaynaktan tek bir olay zinciri çıkarıldı:

```
ALERT-CHAIN-205
```

## Flag

```
ISUCTF{ALERT-CHAIN-205}
```
