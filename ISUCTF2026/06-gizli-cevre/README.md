# 06. Gizli Çevre

**Kategori:** Forensics / Sistem Analizi
**Konu:** Uygulama ayarları config dosyası yerine environment variable'dan okunduğunda hassas bilgi `env_dump`'ta kalır.

## Çözüm

Arşivden çıkan dosyalar:

```
process_info.txt
env_dump.txt
```

`process_info.txt` uygulamanın normalde `/opt/webapp/config/base.cfg` kullandığını ama hassas ayarların env üzerinden geldiğini söylüyordu.

`env_dump.txt` içinde kritik satırlar:

```
CONFIG_SOURCE=env+file
CONFIG_OVERRIDE=true
INTERNAL_AUDIT_REF=ENV-TRACE-501
```

Olay değeri: `ENV-TRACE-501`.

## Flag

```
ISUCTF{ENV-TRACE-501}
```
