# 86. Arşiv Unutmaz (Multi-Source OSINT)

**Kategori:** OSINT / Multi-Archive
**Konu:** Güncel sayfalar temizlenmiş olsa da web arşivi, git geçmişi ve sosyal profil dökümlerinde eski iz kalır.

## Çözüm

Arşivde:

```
web_archive/
repo_export/
social_export/
mail_archive/
flag_vault.bin
```

### Güncel web

```
web_archive/2024-02-01/index.html  → güncel sayfa temiz
```

### Eski web

```
web_archive/2023-09-12/index.html
token seed: kuzey_lamba
```

### Git geçmişi

```
repo_export/.git/COMMIT_222_config.env
```

İçinde:

```
PROJECT_CODE=LMB21
TOKEN_SEED=kuzey_lamba
```

### Sosyal profil

```
arda.kuzey
```

### Solution Key

Parçalar normalize edildi:

```
arda_kuzey_lmb21_kuzey_lamba
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{UESY85-6FT5DY-M5Y6WG}
```
