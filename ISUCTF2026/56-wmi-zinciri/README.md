# 56. WMI Zinciri

**Kategori:** Forensics / Windows Persistence
**Konu:** WMI kalıcılık zinciri (Filter + Consumer + Binding) Windows'ta klasik persistence tekniğidir; PowerShell log ve DNS izleri zinciri tamamlar.

## Çözüm

Arşivdeki kayıtlar:

```
WMI_repository.json
Sysmon.jsonl
PowerShell_Operational.jsonl
dns_client.log
flag_vault.bin
```

`WMI_repository.json` içinde tipik WMI persistence zinciri görüldü:

```
Filter:   NightlyFilter
Consumer: CommandLineEventConsumer
Binding:  NightlyFilter -> CommandLineEventConsumer
```

`dns_client.log` zincire bağlı DNS izi gösteriyordu:

```
wmi-chain.sync.lab
```

Asıl marker `PowerShell_Operational.jsonl` içinde decode edilmiş halde bulundu:

```
decoded marker wmi_chain_T5R8
```

`flag_vault.bin` şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

Solution key:

```
wmi_chain_T5R8
```

## Flag

```
ISUCTF{CTD5C7-M2BWVU-FG5BDV}
```
