# 20. Kırık Başlık

**Kategori:** Forensics / File Carving
**Konu:** Dosya imzası (magic bytes) bozulduğunda görsel açılmaz ama içerik genelde sağlam kalır; header onarılınca dosya kurtarılır.

## Çözüm

Arşivdeki görsel dosya doğrudan açılmıyordu. PNG'nin doğru başlangıç imzası:

```
89 50 4E 47 0D 0A 1A 0A
```

Dosyanın ilk 8 byte'ı bu imzayla onarıldığında görsel tekrar açılabilir hale geldi.

Ancak flag doğrudan görselden gelmedi — `hash_kayitlari.csv` içinde olay token'ı vardı:

```
IMG221_header_onarildi
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

## Flag

```
ISUCTF{B52T2Q-MC7GBK-T6EK7Y}
```
