# 69. Gece Vardiyası

**Kategori:** Forensics / Linux Log Korelasyon
**Konu:** Birden fazla Linux log dosyasından tek bir saldırı zinciri (SSH başarılı giriş → sudo arşivleme → HTTP indirme) çıkarılır.

## Çözüm

Arşivde Linux logları incelendi:

```
/var/log/auth.log
/var/log/sudo.log
/var/log/nginx/access.log
/home/melis/.bash_history
flag_vault.bin
```

### Zincir

`auth.log` içinde başarısız SSH denemelerinden sonra başarılı giriş:

```
Accepted password for melis from 10.44.18.23 ... session=SESS-4819
```

Aynı kullanıcı sudo ile arşivleme yapmıştı:

```
tar -czf /tmp/ogrenci_notlari.tgz /srv/paylasim/notlar
```

nginx `access.log` içinde aynı IP'den arşiv indirme:

```
GET /download/ogrenci_notlari.tgz HTTP/1.1" 200
```

### Solution Key

Zincirden üç parça birleştirildi:

```
melis_SESS4819_ogrenci_notlari
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{DZRSMX-TVSSJU-5V2P5A}
```
