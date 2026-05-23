# 19. Yanlış Rol — Kubernetes RBAC

**Kategori:** Cloud / Kubernetes / Forensics
**Konu:** Kubernetes'te bir ServiceAccount, manifest'te tanımlı yetkilerin ötesinde kaynak erişimi yapıyorsa bu yalnızca audit log'da yakalanır.

## Çözüm

### Dosyalar

```bash
unzip files\(19\).zip
cd files
ls -la
```

Dizinde Kubernetes manifest'leri ve audit kaydı vardı:

```
serviceaccount.yaml
role.yaml
rolebinding.yaml
audit.log
flag_vault.bin
```

### ServiceAccount

`serviceaccount.yaml`:

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: rapor-servis
  namespace: mavi-ortam
```

Kubernetes'te tam kullanıcı adı formatı:

```
system:serviceaccount:mavi-ortam:rapor-servis
```

### Role

`role.yaml` sadece pod okuma yetkisi veriyordu:

```yaml
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "list"]
```

`secrets` kaynağına dair yetki yoktu. Normal şartlarda bu hesabın secret okuması beklenmezdi.

### RoleBinding

Bu Role `rapor-servis` hesabına bağlanmıştı:

```yaml
subjects:
- kind: ServiceAccount
  name: rapor-servis
  namespace: mavi-ortam
```

### Audit Log

```bash
cat audit.log | jq .
```

Kritik kayıt:

```json
{
  "verb": "get",
  "user": "system:serviceaccount:mavi-ortam:rapor-servis",
  "objectRef": {
    "resource": "secrets",
    "name": "db-token",
    "namespace": "mavi-ortam"
  }
}
```

Yani hesap, manifest'te olmayan bir yetkiyi gerçekte kullanmıştı: `get secrets/db-token`.

### Vault Anahtarı

Format mantığı: `<service_account>_<namespace>_<secret_name>`

```
rapor_servis_mavi_ortam_db_token
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

## Flag

```
ISUCTF{J4756Y-WPBS2E-UP7Q2B}
```
