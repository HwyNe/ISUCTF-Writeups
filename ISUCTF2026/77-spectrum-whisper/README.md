# 77. Spectrum Whisper

**Kategori:** Steganografi / Ses + Morse
**Konu:** Spektrogramda belirli frekans bandında kısa/uzun sinyaller → Morse kod.

## Çözüm

Ses dosyasında normal konuşma yoktu. Spektrogramda belirli frekans bandında kısa/uzun sinyaller görüldü — Morse pattern'i.

Sinyaller Morse olarak okundu:

```
-- --- .-. ... . ..--.- .. -. ..--.- ... .--. . -.-. - .-. ..- --
```

Morse decode:

```
MORSE_IN_SPECTRUM
```

(`..--..` = `_` underscore)

## Flag

```
ISUCTF{MORSE_IN_SPECTRUM}
```
