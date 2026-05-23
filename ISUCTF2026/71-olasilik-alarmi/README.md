# 71. Olasılık Alarmı

**Kategori:** SIEM / Bayes Korelasyon
**Konu:** Tek tek alarmlar gürültü; aynı asset üzerinde kısa süre içinde farklı türde alarmların birlikte gelmesi kritik.

## Çözüm

SIEM kayıtlarında tek alarmlar gürültüydü. Asıl kritik olan aynı asset üzerinde kısa zaman aralığında şu alarm türlerinin birlikte görülmesiydi:

```
recon
auth_fail
exec
exfil
```

Kritik asset:

```
SRV-88
```

`alerts.jsonl` içinde bu asset için olaylar ardışık geliyordu:

```
SRV-88 recon       ts=5000
SRV-88 auth_fail   ts=5001
SRV-88 exec        ts=5002
SRV-88 exfil       ts=5003
```

`weights.json` içinde bu korelasyonun marker'ı verilmişti:

```
bayes_alert_V5W8
```

Solution key olarak kullanıldı.

## Flag

```
ISUCTF{P8P3MH-5S45DR-5ZF83B}
```
