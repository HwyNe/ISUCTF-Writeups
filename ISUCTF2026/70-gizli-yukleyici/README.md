# 70. Gizli Yükleyici (LD_PRELOAD Rootkit)

**Kategori:** Forensics / Linux Rootkit
**Konu:** `/etc/ld.so.preload` ile her sürece bir shared library zorla yüklenir; bu kütüphane komut çıktılarını manipüle edebilir.

## Çözüm

Arşivde dosya sistemi artifactleri incelendi.

`/etc/ld.so.preload` dosyası dikkat çekti:

```
/usr/local/lib/libfilter.so
```

Bu dosya Linux dinamik yükleyicisinin her çalıştırılan programa belirtilen shared library'yi preload etmesini sağlar — yaygın bir rootkit/persistence tekniği.

`proc_maps_snapshot.txt` içinde aynı kütüphanenin belleğe yüklendiği doğrulandı:

```
/usr/local/lib/libfilter.so
```

syslog içinde asıl marker bulundu:

```
loader: /usr/local/lib/libfilter.so marker=ldpreload_N6D4
```

`libfilter.so.hex` içinde de aynı değer görülebiliyordu:

```
ldpreload_N6D4
```

Solution key:

```
ldpreload_N6D4
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{BBPC3X-5EMEES-396BJS}
```
