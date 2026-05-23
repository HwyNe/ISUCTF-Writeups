# 32. Parçalı Paket

**Kategori:** Forensics / PCAP
**Konu:** PCAP içinde gürültü/decoy payload'lar arasında tek anlamlı stream.

## Çözüm

`traffic_mix.pcapng` içinde yüzlerce `noise-N` payload vardı. `session_index.csv` incelendiğinde anlamlı session işaret edildi.

Stream 42 reassemble edildiğinde gerçek payload:

```
CASE-028:stream42_reassembled_payload
```

`session_index.csv` aynı token'ı doğruluyordu.

Solution key:

```
stream42_reassembled_payload
```

`flag_vault.bin` çözüldü.

## Flag

```
ISUCTF{NM75ER-3U7XRC-V4Y78G}
```
