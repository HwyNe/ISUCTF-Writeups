# 53. Kim Okuyabilir?

**Kategori:** Linux / Permissions
**Konu:** Unix dosya izinleri kullanıcı/grup/diğer şeklinde ayrılır; kullanıcı bir gruba üye olduğunda o grubun erişim haklarını kazanır.

## Çözüm

`analyst` kullanıcısının üye olduğu gruplar:

```
analyst
soc-team
audit-ro
```

Hedef dosyanın izinleri:

```
-rw-r-----  root  audit-ro  PERM-READ-812.enc
```

Çözümleme:

```
owner (root): rw-
group (audit-ro): r--
other: ---
```

Group bit'inde okuma izni var ve grup `audit-ro`. `analyst` kullanıcısı bu gruba üye olduğu için dosyayı okuyabiliyor.

Olay değeri:

```
PERM-READ-812
```

## Flag

```
ISUCTF{PERM-READ-812}
```
