# 09. Ortak Modül

**Kategori:** Kriptografi / RSA Common Modulus Attack
**Konu:** Aynı mesaj iki farklı açık üs `e1`, `e2` ile ama aynı modül `n` kullanılarak şifrelenmişse, iki ciphertext'ten orijinal mesaj kurtarılabilir.

## Çözüm

Saldırının teorisi:

```
c1 = m^e1 mod n
c2 = m^e2 mod n
```

`gcd(e1, e2) = 1` ise extended Euclidean ile `a*e1 + b*e2 = 1` katsayıları bulunur. Sonra:

```
m = (c1^a * c2^b) mod n
```

Arşivdeki parametre ve log dosyalarında olay marker'ı bulundu:

```
RSA901_ortak_modul_tehlikelidir
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{ZGBUPS-4SW52C-VVHH8A}
```
