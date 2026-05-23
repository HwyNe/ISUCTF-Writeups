# 39. Paket Günlüğü

**Kategori:** Forensics / PCAP
**Konu:** Ağ kaydında HTTP/TCP akışları arasında JSON payload'lar; normal trafik arasında olayla ilişkili tek JSON kaydı.

## Çözüm

PCAP veya log dosyası incelendiğinde HTTP ve TCP akışları içinde JSON payload'lar vardı.

Normal trafik arasında olayla ilişkili tek JSON kaydı şu yapıdaydı:

```json
{
  "ref": "<gizli_referans_değeri>"
}
```

`ref` alanındaki değer doğrudan flag veya vault anahtarı olarak kullanıldı.

## Flag

JSON `ref` alanından elde edildi.
