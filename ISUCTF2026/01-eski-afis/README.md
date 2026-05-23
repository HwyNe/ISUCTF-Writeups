# 01. Eski Afiş

**Kategori:** OSINT / Görsel Analiz
**Konu:** İki afiş versiyonu arasında fark; kaldırılan bilgi eski sürümde kalmış.

## Çözüm

İki afiş yan yana karşılaştırıldı. Çoğu bilgi aynıydı ama eski versiyondaki siyah kutuda güncel sürümde olmayan satırlar bulundu:

```
Internal Ref: POSTER-OLD-63
Draft v0.3 - Not for public distribution
```

`POSTER-OLD-63` değeri doğrudan flag'in çekirdeğiydi.

## Flag

```
ISUCTF{POSTER-OLD-63}
```
