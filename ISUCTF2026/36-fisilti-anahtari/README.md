# 36. Fısıltı Anahtarı

**Kategori:** Kriptografi / Known-Plaintext XOR
**Konu:** Vardiya notunda iki şifreli akış var; birinde bilinen başlık (known plaintext) kullanılarak anahtar çıkarılıyor, aynı anahtarla diğer akış çözülüyor.

## Çözüm

Vardiya notunda iki akış vardı:

```
akis_01
akis_02
```

İlk akışın başlangıcında sabit bir başlık biliniyordu (known plaintext). Bu başlık şifreli akışla XOR'landığında anahtar düştü:

```
key = akis_01[0:n] XOR known_plaintext[0:n]
```

Çıkan anahtar:

```
mavi-kilit
```

Aynı anahtar `akis_02` ile XOR'lanınca gizli belirteç ortaya çıktı.

Solution key:

```
4421_fisilti_ayni_anahtari_sevmez
```

`flag_vault.bin` bu anahtarla çözüldü.

## Flag

`flag_vault.bin` çözülerek elde edildi.
