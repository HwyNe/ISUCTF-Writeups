# 30. Affine Cipher — A=0 Sistemi

**Kategori:** Kriptografi / Klasik Şifre
**Konu:** Affine cipher'da her harf `f(x) = (a*x + b) mod 26` ile dönüştürülür; çözmek için `a`'nın mod 26 tersini bulmak gerekir.

## Çözüm

A=0 sisteminde harfler sayıya çevrildi. Dönüşüm:

```
y = (a*x + b) mod 26
```

Parametreler:

```
a = 7
b = 3
```

`7`'nin mod 26 modular inverse'i `15` (çünkü `7 * 15 = 105 ≡ 1 mod 26`).

Çözme formülü:

```
x = 15 * (y - 3) mod 26
```

Her şifreli harfe uygulandığında plaintext çıktı:

```
AFFINE-MOD-91
```

## Flag

```
ISUCTF{AFFINE-MOD-91}
```
