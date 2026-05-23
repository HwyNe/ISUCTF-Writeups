# 37. E-posta Zinciri

**Kategori:** Forensics / Email
**Konu:** Forward edilmiş bir e-posta zincirinde her katmanda header alanları ve ek dosyalar birlikte değerlendirildiğinde gizli marker ortaya çıkıyor.

## Çözüm

E-posta zinciri sırayla açıldı. Her bir forward katmanında authentication header'ları incelendi:

```
Authentication-Results:
X-Original-To:
Received:
DKIM-Signature:
ARC-Authentication-Results:
```

Mail zincirinin belirli bir katmanında authentication header ile o katmandaki attachment dosya adı arasında bir ilişki vardı — bu ilişki marker değerini ortaya çıkardı.

Bulunan marker `flag_vault.bin` için solution key olarak kullanıldı.

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{WU8YC2-GJPMJA-UBRUBT}
```
