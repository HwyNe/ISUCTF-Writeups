# 38. Sessiz Ek

**Kategori:** Forensics / Polyglot
**Konu:** Yanlış isimlendirilmiş arşiv — PDF gibi görünen dosya aslında RAR.

## Çözüm

Dosya `.pdf` uzantılıydı ama PDF reader açamıyordu. Magic byte'lar kontrol edildi:

```bash
file ek.pdf
xxd ek.pdf | head
```

Çıktıda `Rar!\x1A\x07\x00` imzası görüldü — dosya aslında RAR arşiviydi.

Dosya `.rar` uzantısına çevrildi ve `unrar` ile açıldı:

```bash
mv ek.pdf ek.rar
unrar x ek.rar
```

İçinden çıkan dosyada flag doğrudan vardı.

## Flag

Arşivden okundu.
