# 21. Tarayıcı Hatırlıyor

**Kategori:** Forensics / Browser Artifacts
**Konu:** Dosya sistemden silinse bile tarayıcı artifact'leri (History, Cookies, Network Predictor) olayın izini korur.

## Çözüm

Kullanıcı bir belge indirdiğini ama daha sonra dosyanın silindiğini söylüyordu. Dosya sistemi temizdi, bu yüzden analiz tarayıcı kayıtlarına yönlendirildi.

Arşivdeki Chrome artifact'leri:

```
Chrome/History            (SQLite)
Chrome/Cookies
Chrome/Network Action Predictor
user_timeline.csv
```

Chrome `History` SQLite DB'si açıldığında silinen belgenin olay kaydı bulundu. Aynı iz Cookies, Network Action Predictor ve `user_timeline.csv` içinde de tekrar ediyordu.

Tüm artifact'lerde ortak token:

```
nihai_not_482_a91f482_100811
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

## Flag

```
ISUCTF{VCHNU7-V8J5FK-3Q6RVX}
```
