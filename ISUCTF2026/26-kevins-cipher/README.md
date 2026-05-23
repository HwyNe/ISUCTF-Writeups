# 26. Kevin's Cipher

**Kategori:** Tersine Mühendislik
**Konu:** Binary'de kullanıcı girdisi sabit bir XOR anahtarıyla işleniyor; aynı anahtar binary içindeki şifreli diziye uygulanınca flag çıkar.

## Çözüm

1. Binary incelendi (`strings`, `objdump`, decompiler).
2. Programın kullanıcıdan lisans anahtarı aldığı ve girdinin `0x41` ile XOR'landığı görüldü.
3. Binary içinde şifreli byte dizisi bulundu.
4. Aynı `0x41` anahtarıyla diziye XOR uygulandı.

```python
data = bytes([0x27, 0x2d, 0x20, 0x26, 0x3a, ...])  # binary'den çıkarılan dizi
print(bytes([b ^ 0x41 for b in data]).decode())
```

Çıkan flag isim referansı veriyordu (Kevin Mitnick).

## Flag

```
flag{kevin_mitnick}
```
