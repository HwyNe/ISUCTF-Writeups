# 57. Yerel Kütüphane (APK Native Library)

**Kategori:** Mobile / Android Reverse
**Konu:** Java/Smali tarafı sadece JNI çağrısı yapıyor; gerçek kontrol mantığı native `.so` kütüphanesinde.

## Çözüm

### 1. Java/Smali analizi

APK `jadx` ile dekompayl edildi. Java tarafında sadece şu çağrı vardı:

```java
nativeCheck(input);
```

Asıl mantık `lib/arm64-v8a/libgate.so` içindeydi.

### 2. Native library analizi

`libgate.so` Ghidra/`strings` ile incelendi:

```
xor-key: /mobile/native/v2
```

XOR anahtarı endpoint string'iydi.

### 3. HAR doğrulama

HAR kaydında aynı endpoint görüldü; native kodun ürettiği değerle uyumluydu.

### 4. Veritabanı

`app.db` `secrets` tablosunda blob alındı:

```sql
SELECT value FROM secrets WHERE key='gate_token';
```

### 5. XOR

Blob, endpoint string'i ile XOR'landığında marker çıktı:

```
apk_native_C8V5
```

`flag_vault.bin` bu anahtarla çözüldü.

## Flag

`flag_vault.bin` çözülerek elde edildi.
