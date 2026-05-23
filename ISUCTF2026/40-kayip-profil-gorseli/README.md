# 40. Kayıp Profil Görseli

**Kategori:** Forensics / EXIF Metadata
**Konu:** Görselin kendisi değil, EXIF metadata içindeki bağlantı önemli.

## Çözüm

Arşivdeki profil görselinin EXIF metadata alanları incelendi:

```bash
exiftool profil.jpg
```

Metadata içinde kritik alan:

```
linked_file: img_909.jpg
```

Bu referans başka bir dosyaya işaret ediyordu. `gallery/img_909.jpg` dosyasına bakıldığında flag doğrudan içinde bulundu.

## Flag

```
ISUCTF{PROFILE-META-909}
```
