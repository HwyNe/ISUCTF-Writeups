# 74. Zamansal Graf

**Kategori:** Threat Intelligence / Temporal Graph
**Konu:** Saldırı grafında kenarların aktif olduğu zaman damgaları artan sırada olmalı; geriye düşen yollar geçersiz.

## Çözüm

Arşivdeki dosyalar:

```
attack_graph.json
alerts.jsonl
scoring_rules.json
flag_vault.bin
```

### Olası yollar

```
U -> A -> B -> KASA
U -> C -> KASA
```

### Kenarların aktif zamanları

```
U > A      t=1
A > B      t=2
B > KASA   t=3

U > C      t=2
C > KASA   t=1
```

### Skor kuralı

`scoring_rules.json`:

```
timestamps must be nondecreasing
```

### Değerlendirme

- `U → A → B → KASA`: zamanlar `1 → 2 → 3` artıyor → **geçerli**
- `U → C → KASA`: zamanlar `2 → 1` geriye düşüyor → **geçersiz**

Marker:

```
temporal_path_H7D3
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{C94Y3E-V45D5J-TGG3TD}
```
