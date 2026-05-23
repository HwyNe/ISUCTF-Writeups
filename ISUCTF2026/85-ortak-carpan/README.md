# 85. Ortak Çarpan (RSA Shared Prime)

**Kategori:** Kriptografi / RSA
**Konu:** İki farklı RSA modülü ortak bir asal çarpan paylaşıyorsa `gcd(n1, n2)` o asal çarpanı verir; her iki anahtar da çözülebilir.

## Çözüm

Arşivdeki kayıtlar RSA zayıf anahtar üretimi senaryosunu gösteriyordu. Farklı kullanıcılara ait açık anahtar modülleri karşılaştırıldı.

### Saldırı mantığı

```
gcd(n1, n2) = p   (ortak asal)
q1 = n1 / p
q2 = n2 / p
phi(n) = (p - 1) * (q - 1)
d = e^-1 mod phi(n)
```

Modüller pairwise GCD ile tarandığında ortak çarpan paylaşan bir çift bulundu.

Marker:

```
rsa_shared_prime_724
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{FZW8J3-U9CZNV-6E24ES}
```
