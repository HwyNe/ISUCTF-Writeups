# 42. Tekrar Eden İmza

**Kategori:** Kriptografi / DSA Nonce Reuse
**Konu:** DSA/ECDSA'da aynı nonce `k` ile iki imza üretilirse private key tamamen sızar.

## Çözüm

İki farklı imza kaydı incelendiğinde `r` değerinin aynı olduğu görüldü:

```
A: r = 5489, s = 7746, h = 7341
B: r = 5489, s = 8643, h = 2201
```

Aynı `r` → aynı nonce `k` → klasik DSA nonce reuse.

### Formüller

`k` ortak olduğu için:

```
s1 = k^-1 * (h1 + x*r) mod q
s2 = k^-1 * (h2 + x*r) mod q
```

`k` çözümü:

```
k = (h1 - h2) * (s1 - s2)^-1 mod q
```

`x` (private key) çözümü:

```
x = (s1 * k - h1) * r^-1 mod q
```

### Hesaplama

```
k           = 3137
private key = 4242
```

`verification_note.txt` dosyasında bu checksum'ın hangi marker'a karşılık geldiği yazılıydı:

```
dsa_reuse_4N7P
```

Bu marker solution key olarak kullanıldı.

## Flag

```
ISUCTF{Q22JMF-RTLRPV-HU7RE3}
```
