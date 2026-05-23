# 72. Etiket Boşluğu (Kubernetes Admission Gap)

**Kategori:** Cloud / Kubernetes / OPA
**Konu:** Admission policy etiket varlığını şart koşmadan değer kontrolü yapıyor; etiketi olmayan namespace'te kontrol "yok sayılıyor", deny çalışmıyor.

## Çözüm

Arşivdeki dosyalar:

```
policy/admission.rego
manifests/namespaces.yaml
manifests/pods.yaml
audit/admission_audit.jsonl
flag_vault.bin
```

Admission policy şu kontrolü yapıyordu:

```rego
input.namespace.labels.secure != "true"
input.request.hostPath
```

Yani `secure=true` etiketi olmayan namespace içinde hostPath kullanımı deny olmalıydı.

### Boşluk

`namespaces.yaml` içinde `gray` namespace etiketsizdi:

```yaml
gray:
  labels: {}
```

`pods.yaml` içinde `collector` pod'u `gray` namespace'inde hostPath kullanıyordu:

```yaml
namespace: gray
hostPath: /var/log
```

Beklenen sonuç: deny. Ama audit kaydında istek **allow** olmuştu:

```
missing label path not evaluated
marker: admission_gap_Q3L9
```

Etiket hiç olmadığı için Rego sorgusu evaluate edilmeden geçmiş — klasik admission gap.

Olay marker'ı:

```
admission_gap_Q3L9
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{KBGLCB-N82RHC-4J67NY}
```
