# 90. Ters Kanal (Reverse-Time DTMF)

**Kategori:** Steganografi / Ses / DTMF
**Konu:** Stereo ses dosyasının sağ kanalı zaman ekseninde tersine çevrilmiş DTMF tonları taşıyor.

## Çözüm

Arşivden çıkan dosyalar:

```
recording.wav
channel_notes.json
flag_vault.bin
```

`channel_notes.json` ipuçları:

```
right_channel:  reverse before analysis
alphabet:       frequency modulo map
marker_hint:    dtmf_reverse_L4P6
```

Ses iki kanallı:

- **Sol kanal:** sadece gürültü/boş veri
- **Sağ kanal:** ters zamanlı kısa ton dizileri

### Çözüm

Sağ kanal ters çevrildi (`sox in.wav out.wav reverse` benzeri). Ton dizisi DTMF/frekans eşleşmesiyle marker'a dönüştü:

```
dtmf_reverse_L4P6
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{A3CQYE-NBQZ94-N6H2R8}
```
