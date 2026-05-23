# 65. Yetki Zinciri (AWS IAM Chain)

**Kategori:** Cloud / AWS IAM / CloudTrail
**Konu:** Tek tek IAM politikaları normal görünür ama rol zinciri (PassRole → AssumeRole) takip edildiğinde kritik kasaya erişim çıkar.

## Çözüm

Zincir analiz edildi:

```
analyst       → iam:PassRole          → ReportRole
ReportRole    → sts:AssumeRole        → VaultReadRole
VaultReadRole → secrets:GetSecretValue → vault-main
```

CloudTrail içinde gürültü kayıtları arasında kritik olay:

```
event:  GetSecretValue
user:   VaultReadRole
secret: vault-main
marker: iam_chain_M8V2
```

Doğru solution key:

```
iam_chain_M8V2
```

`flag_vault.bin` bu anahtarla çözüldü.

## Flag

```
ISUCTF{YT43ZE-GQYWRW-QWLDXG}
```
