# 44. Katmanlı Akış

**Kategori:** Forensics / PCAP
**Konu:** PCAP içinde HTTP cevabı chunked transfer + deflate sıkıştırma katmanlarıyla geliyor; iki katman birlikte soyulmadan içerik okunamıyor.

## Çözüm

Proxy loglarında sıradan görünen indirme isteği görüldü:

```
GET /download/report.cache
```

`stream_index.csv` dosyasından bu isteğin PCAP içindeki TCP stream numarası bulundu. İlgili stream çıkarıldığında HTTP cevabının iki katmanlı geldiği görüldü:

```
Transfer-Encoding: chunked
Content-Encoding:  deflate
```

### Çözüm

1. Önce chunk parçaları birleştirildi (chunked decoding)
2. Sonra `zlib.decompress()` ile deflate açıldı

Açılan içerikten anahtar bilgisi:

```
tcp_chunk_X9A2
```

`flag_vault.bin` şeması `xor-sha256-stream`'di. `salt + solution_key` SHA-256 ile işlenip keystream üretildi, ciphertext XOR ile çözüldü.

## Flag

```
ISUCTF{AL4D4Q-2NZ5SZ-MCUWXZ}
```
