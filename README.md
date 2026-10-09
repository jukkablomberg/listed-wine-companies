# Listed wine companies — the BoomCellar register

Every stock-market-listed wine company [BoomCellar](https://boomcellar.com/data?utm_source=github&utm_medium=dataset&utm_campaign=bc-register-github) has found, with a permanent ID, its identifiers, its index status, and — for those that have left the market — how and when they left, with the evidence. This repository mirrors the files BoomCellar serves; the canonical, live register is at https://boomcellar.com/data?utm_source=github&utm_medium=dataset&utm_campaign=bc-register-github (refreshed every 30 minutes).

## Edition 2026-10-09

Mirrored 2026-10-09 from the Frictionless package `boomcellar-datasets` **version 1.21**, byte-identical to the served files. This copy is not refreshed automatically — for current rows use the live files. Each new edition is a tagged release.

- `data/companies.csv` — **86 companies, 48 columns:** 22 Indexed (13 countries) · 6 Eligible, awaiting reconstitution · 18 Tracked, not indexed · 8 Excluded · 32 Delisted. Every one of the 54 companies still listed carries an ISIN; 46 of 86 carry a GLEIF LEI.
- `data/delisted.csv` — **33 exits, 17 columns**, 1996-03-13 → 2026-09-22 (3 rows without a confirmed date): 11 taken private · 9 squeezed out · 4 merged away · 4 insolvency · 3 left voluntarily · 1 wound down · 1 delisting approved (scheduled). Each row carries an evidence tier: 19 exchange, regulator or company filing · 8 court record or listing database · 6 press only (treat with caution).
- `data/datapackage.json` — the column dictionary, byte-identical to https://boomcellar.com/data/datapackage.json (it also describes the other files BoomCellar serves, which are not mirrored here).

Join on `bc_id`, never on names: IDs are permanent and never reused ([ID table](https://boomcellar.com/api/ids.json)).

## How a row is decided

- **Decision rule:** a company enters the index family only if selling wine is at least half its revenue, read from its own segment or product reporting (`wine_revenue_share_pct`, `wine_share_basis`, `wine_share_source_url`); everything else is tracked, excluded with a reason (`status_detail`), or recorded as an exit. Full rules: [methodology](https://boomcellar.com/methodology?utm_source=github&utm_medium=dataset&utm_campaign=bc-register-github).
- **Traceability:** share counts cite the filing and the note/page they were read from (`shares_source_url`, `shares_source_locator`); identifiers say where they came from (`isin_source`, `lei_basis`, `identifier_note`); exits cite their primary source (`primary_source_url`, `source_urls`).
- **Limits:** prices are delayed closes for index constituents only, and raw daily price history is not redistributed. A blank means not found or not reported — `identifier_note` and `wine_share_basis` say which. Exits graded "press only" are unconfirmed by a filing. The register is a work in progress: candidates are added as they are verified, and they join the index only at a dated reconstitution.

## Terms and citation

Free to use, including commercially, with attribution to BoomCellar (https://boomcellar.com).

> BoomCellar (2026). Listed wine companies — register, edition 2026-10-09 (data package v1.21). https://boomcellar.com/data

`CITATION.cff` in this repository gives GitHub's "Cite this repository" button the same citation. Also on [Hugging Face](https://huggingface.co/datasets/jukkab/listed-wine-companies) (edition 2026-10-01). The methodology is archived at [doi:10.5281/zenodo.23092835](https://doi.org/10.5281/zenodo.23092835) and the September *Wine Stocks Monthly Brief* at [doi:10.5281/zenodo.23049339](https://doi.org/10.5281/zenodo.23049339).

*Mirrored to GitHub by an AI agent on BoomCellar's behalf. Information, not investment advice.*
