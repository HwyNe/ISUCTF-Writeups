# 25. Sessiz Frekans

**Kategori:** Steganografi / Ses Analizi
**Konu:** Ses dosyasındaki gizli bilgi zaman/frekans düzleminde (spektrogram) saklı olabilir; kulakla değil görsel analizle çözülür.

## Çözüm

`kayit.wav` normal dinlendiğinde anlamsız sinyaller içeriyordu. Soru metni zaman/frekans düzlemini işaret ediyordu.

Ses dosyası spektrogram aracıyla incelendi (Audacity, sox, Sonic Visualiser vb.). Spektrogramda gizli iz görüldü.

`recorder_metadata.json` içinde cihaz ID'si vardı:

```
device_id: REC-42
```

Spektrogram ipucu "spektrogram izi" olarak yorumlanarak solution key oluşturuldu:

```
REC42_spektrogram_izi
```

`flag_vault.bin` bu anahtarla çözüldü.

## Flag

`flag_vault.bin` çözülerek elde edildi.
