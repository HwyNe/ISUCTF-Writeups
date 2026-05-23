# 23. Cron'un Notu

**Kategori:** Forensics / Linux Artifact
**Konu:** Cron, bash history, auth.log ve syslog gibi birden fazla Linux artifact'i aynı marker'ı taşıdığında bu değer olay anahtarı olarak kullanılır.

## Çözüm

Arşiv açıldıktan sonra dosyalar listelendi:

```bash
find . -type f
```

Dikkat çeken dosyalar:

```
etc/crontab
home/analyst/.bash_history
var/log/auth.log
var/log/syslog
flag_vault.bin
```

Tüm artifact'lerde ortak değer arandı:

```bash
grep -RIn "Marker\|marker\|CASE" .
```

Aynı değer dört dosyada da geçiyordu. Ortak marker:

```
sess_clean_env441_033120
```

`flag_vault.bin` içindeki şema:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

Solution key olarak marker kullanıldı.

## Flag

```
ISUCTF{AN63X4-FLDJ4J-EWULWF}
```
