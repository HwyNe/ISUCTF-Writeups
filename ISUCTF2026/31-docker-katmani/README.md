# 31. Docker Katmanı

**Kategori:** Forensics / Container
**Konu:** Docker image layer'ları snapshot mantığıyla çalışır; bir önceki layer'da bulunan dosya sonraki layer'da `.wh.` whiteout dosyasıyla "silinmiş" gibi görünür ama hâlâ alt katmanda mevcuttur.

## Çözüm

`ctf_image.tar` açıldı:

```bash
tar -xf ctf_image.tar
```

`manifest.json` ile layer sırası incelendi. Her layer dosyası tek tek listelendi.

Güncel layer'da:

```
.wh..internal_config
```

Bu bir **whiteout** dosyasıydı — önceki layer'da bulunan `.internal_config` dosyasının silindiğine işaret ediyordu. Ama dosya hâlâ alt layer'da duruyordu.

Eski layer'da:

```
opt/app/.internal_config
```

İçerik:

```
LAYER_TRACE_ID=LAYER-TRACE-884
```

## Flag

```
ISUCTF{LAYER-TRACE-884}
```
