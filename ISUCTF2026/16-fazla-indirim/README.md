# 16. Fazla İndirim

**Kategori:** Web / Logic Flaw
**Konu:** Alışveriş uygulamasında kupon stacking mantığı, sepet ve oturum birlikte değerlendirilmediğinde beklenmedik sipariş koşulu tetiklenebiliyor.

## Çözüm

İlk analizde sadece kupon stacking mantığı tespit edildi — ancak token tek başına flag için yeterli değildi.

Veritabanında kritik sipariş kaydı bulundu:

```
id:    ORD-771
token: coupon_stack_precision
```

Doğru solution key, sipariş id ve token'ın normalize edilmiş birleşimiydi:

```
ORD771_coupon_stack_precision
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

## Flag

```
ISUCTF{R3WAJQ-C8GRRG-YHEB9R}
```
