# 52. Git Gölgesi

**Kategori:** Forensics / Git History
**Konu:** Git repo'sundan silinen hassas içerik commit geçmişinde kalır.

## Çözüm

ZIP içinde bir git reposu vardı.

```bash
cd repo
git log --all --oneline
```

Şüpheli commit mesajı görüldü:

```
Refactor: remove hardcoded internal references from config
```

`git show` ile commit incelendi:

```bash
git show <commit-hash>
```

`src/config.py`'dan silinmiş satırlar:

```python
INTERNAL_REF = "GIT-HIST-310"
AUDIT_TOKEN  = "audit-a3f9c12e"
```

`AUDIT_TOKEN` flag'i veriyordu.

## Flag

```
ISUCTF{audit-a3f9c12e}
```
