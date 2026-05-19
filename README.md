# Bangladesh Administrative Divisions / বাংলাদেশ

Open dataset of Bangladesh's administrative hierarchy — 8 divisions, 64 districts, and 495 upazilas. This repository provides structured, bilingual (Bengali + English) reference data with geographic coordinates and postal codes at every level. Designed for developers, researchers, government agencies, and AI agents.

Licensed under CC-BY-4.0. Browse the hierarchy through GitHub's folder navigation, download aggregate files in JSON/CSV/NDJSON, or integrate directly via raw URLs.

## Overview

| Item | Details |
|------|---------|
| Division | 8 |
| District | 64 |
| Upazila | 495 |
| Coordinates | ✅ Included (all levels) |
| Postal Codes | ✅ Included (upazila level) |
| Formats | JSON, NDJSON, CSV |
| License | CC-BY-4.0 |
| Last Updated | 2026-05-19 |

## Browse by Division

| # | Division | Districts | Upazilas | Link |
|---|----|----|----|------|
| 1 | বরিশাল (Barishal) | 6 | 42 | [Browse](divisions/barishal-bd10/) |
| 2 | চট্টগ্রাম (Chattogram) | 11 | 104 | [Browse](divisions/chattogram-bd20/) |
| 3 | ঢাকা (Dhaka) | 13 | 89 | [Browse](divisions/dhaka-bd30/) |
| 4 | খুলনা (Khulna) | 10 | 59 | [Browse](divisions/khulna-bd40/) |
| 5 | ময়মনসিংহ (Mymensingh) | 4 | 35 | [Browse](divisions/mymensingh-bd45/) |
| 6 | রাজশাহী (Rajshahi) | 8 | 67 | [Browse](divisions/rajshahi-bd50/) |
| 7 | রংপুর (Rangpur) | 8 | 58 | [Browse](divisions/rangpur-bd55/) |
| 8 | সিলেট (Sylhet) | 4 | 41 | [Browse](divisions/sylhet-bd60/) |

## Data Files

| File | Format | Description |
|------|--------|-------------|
| [all-division.json](data/all-division.json) | JSON | All 8 division records |
| [all-district.json](data/all-district.json) | JSON | All 64 district records |
| [all-upazila.json](data/all-upazila.json) | JSON | All 495 upazila records |
| [all-flat.json](data/all-flat.json) | JSON | Levels 1-2 flat array |
| [all-flat.ndjson](data/all-flat.ndjson) | NDJSON | Streaming format |
| [all-flat.csv](data/all-flat.csv) | CSV | Spreadsheet format |
| [hierarchy.json](data/hierarchy.json) | JSON | Nested tree |
| [schema.json](data/schema.json) | JSON Schema | Data schema |

## Quick Start

### Python

```python
import json

with open("data/all-division.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for r in data:
    print(f"{r['name']['local']} ({r['name']['en']}) — {r['children_count']['district']} districts")
```

### JavaScript

```javascript
import { readFileSync } from "fs";

const data = JSON.parse(readFileSync("data/all-division.json", "utf-8"));
console.log(`Total: ${data.length} divisions`);
```

## Schema

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier |
| `level` | integer | 1=division, 2=district, 3=upazila |
| `level_name` | object | Level label (local + English) |
| `name.local` | string | Name in local script |
| `name.en` | string | English name |
| `name.slug` | string | URL-safe slug |
| `parent` | object/null | Parent division reference |
| `ancestors` | array | Full ancestor chain |
| `children_count` | object | Count of children per level |
| `zip_codes` | array | Postal codes (where available) |
| `geo.lat` | string | Latitude (WGS84) |
| `geo.lon` | string | Longitude (WGS84) |

Full schema: [data/schema.json](data/schema.json)

## Hierarchy Browse

```
divisions/{division-slug}/
divisions/{division-slug}/{district-slug}/
```

Upazilas are listed inline in each district's README.

## AI Integration

- [llms.txt](docs/llms.txt) — Quick reference for AI agents
- [llms-full.txt](docs/llms-full.txt) — Summary with per-division links
- [Per-division data](docs/llms-full/) — Full data by division

## Citation

```
Bangladesh Administrative Divisions Dataset (CC-BY-4.0)
URL: https://github.com/open-admin-data/bangladesh-administrative-divisions
```

See [CITATION.cff](CITATION.cff) for machine-readable citation.

## License

- **Data**: [CC-BY-4.0](LICENSE)

## Related

- [ListBase](https://www.listbase.org) — Structured reference data for every country
- [open-admin-data](https://github.com/open-admin-data) — Open administrative data for ASEAN countries
- [thailand-administrative-divisions](https://github.com/open-admin-data/thailand-administrative-divisions) — Thailand dataset
