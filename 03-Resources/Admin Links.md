---
title: "Admin Links"
type: resource
---

# Admin Links

## Usage CSV Download
Download the full session cost log (all clients, all sessions, cost in USD).

```
https://worker-production-32fb.up.railway.app/admin/usage-csv?key=cjDEPh3u5QrHuGlo4KPK7cd9_ZClA20t
```

Paste into browser → downloads as `tanya_usage.csv` → open in Numbers or Excel.

Columns: `log_id, timestamp, phone_hash, user, model, input_tokens, output_tokens, cache_read_input_tokens, cache_creation_input_tokens, approx_usd`
