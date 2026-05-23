# 82. Kullanıcı Zincirleri (Multi-Page Caesar Chain)

**Kategori:** Web / Caesar Cipher
**Konu:** Üç sayfalık zincirleme bulmaca; her sayfa Caesar +2 ile şifreli ipucu veriyor.

## Çözüm

### Adım 1 — profile.html

Kullanıcı `gh0st_84x`, bio ipucu veriyor:

```
"Follow the numbers, not the names."
```

Footer'da:

```
uid: 0x54
```

Hex → decimal: `84`.

Dosya hem `notes.txt`'e hem `gallery.html`'e link veriyor.

### Adım 2 — notes.txt

Dosya Caesar +2 ile şifreli. `-2` kaydırınca:

```
success with forensics
cracked the hash -- sha256 matches
final verification: gallery.html -- img id is img_znee
status: complete
```

Hedef: `gallery.html` içinde `img_znee` (encode edilmiş hali: `img_bpgg`).

### Adım 3 — gallery.html

Aktif (highlight'lı) kart `img_bpgg`. İçinde:

```
WUGT-EJCKP-84
```

Caesar `-2` uygulanınca:

```
USER-CHAIN-84
```

## Flag

```
ISUCTF{USER-CHAIN-84}
```
