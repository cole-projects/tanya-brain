---
title: "Admin Links"
type: resource
---

# Admin Links

## Usage CSV Download
Download the full session cost log (all clients, all sessions, cost in USD).

Run this in Terminal — saves the file to your Desktop:

```bash
curl -H "Authorization: Bearer cjDEPh3u5QrHuGlo4KPK7cd9_ZClA20t" \
  https://worker-production-32fb.up.railway.app/admin/usage-csv \
  -o ~/Desktop/tanya_usage.csv
```

Then open `tanya_usage.csv` on your Desktop in Numbers or Excel.

Columns: `log_id, timestamp, phone_hash, user, model, input_tokens, output_tokens, cache_read_input_tokens, cache_creation_input_tokens, approx_usd`
