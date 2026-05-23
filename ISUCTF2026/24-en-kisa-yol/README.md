# 24. En Kısa Yol — Güvenlik Grafı

**Kategori:** Threat Intelligence / Graf Analizi
**Konu:** Güvenlik grafı üzerinde en kısa saldırı yolu için aktif uyarılar ve varlık envanteri birlikte işlenmeli.

## Çözüm

Arşiv açıldı:

```bash
unzip Files\(6\).zip
cd artifacts
find . -type f
```

Önemli dosyalar:

```
alerts.jsonl
asset_inventory.csv
attack_graph.json
flag_vault.bin
```

Soru ipucu yalnızca grafı değil aktif uyarıları da işaret ediyordu. Üçü birlikte değerlendirildi:

```bash
cat attack_graph.json
cat alerts.jsonl
cat asset_inventory.csv
```

Graf üzerinde en olası ilerleme yolu:

```
U1 → G1 → S1 → KASA
```

Solution key:

```
path_U1_G1_S1_KASA
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{VX3E2Z-KWL4EP-QGD995}
```
