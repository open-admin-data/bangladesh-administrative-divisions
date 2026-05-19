# Methodology

## Data Sources

- **OCHA COD-AB Bangladesh** (CC BY-IGO) — Division, district, and upazila records with P-codes and centroid coordinates
- **techno-stupid/places-in-bangladesh** — Bengali (বাংলা) upazila names
- **gopalsdiary/fenimodel25** — Bengali district and upazila names with cross-reference
- **ekdak.com** — Bangladesh Post Office postal codes mapped to police stations/upazilas
- **msrumon/postal-codes gist** — District-level postal codes

## Processing

1. Administrative records from OCHA COD-AB XLSX gazetteer (divisions, districts, upazilas)
2. Bengali names merged from multiple community sources (100% coverage all levels)
3. Postal codes matched via ekdak.com API hierarchy + name fuzzy matching (100% coverage)
4. City Corporations excluded (12 entities — separate local government system, not admin hierarchy)
5. Multi-format export: JSON, NDJSON, CSV

## Accuracy

- Coordinates: 100% at all levels (from OCHA COD-AB centroids)
- Bengali names: 100% at all levels
- Postal codes: 100% at district and upazila levels
- Build script is idempotent: same input always produces same output