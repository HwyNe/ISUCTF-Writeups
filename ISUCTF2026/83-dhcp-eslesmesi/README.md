# 83. DHCP Eşleşmesi

**Kategori:** Forensics / DHCP Log
**Konu:** Cihaz adı → MAC → IP eşleşmesi DHCP log'undan çıkarılır.

## Çözüm

ZIP içinden `dhcp.log` ve `device_list.txt` çıktı.

`device_list.txt` içindeki hedef cihaz:

```
workstation-sec-09
```

`dhcp.log` içinde bu cihaz adı arandı:

```bash
grep "workstation-sec-09" dhcp.log
```

Kayıtta cihazın MAC adresi ve aldığı IP:

```
B3:C1:D2:E4:F5:A6   10.30.14.82   workstation-sec-09
```

Cihazın DHCP üzerinden aldığı adres:

```
10.30.14.82
```

## Flag

```
ISUCTF{10.30.14.82}
```
