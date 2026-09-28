# Reddit methodology: evaluating ArthurHeitmann/arctic_shift

Evaluation of **[ArthurHeitmann/arctic_shift](https://github.com/ArthurHeitmann/arctic_shift)** as a path for Rzk-related Reddit search from this research box (2026-09-28, Asia/Singapore). Complements the discourse summary in [08-community-and-discourse.md](08-community-and-discourse.md).

**Verdict (short).** Arctic Shift is a **usable lightweight search path** via its HTTP API and web UIs. **Full monthly / multi-year dumps are not practical** on this box (multi-terabyte torrents; single recent comment months are already tens of GB compressed). Scoped API queries for `rzk` / `rzk-lang` in relevant subreddits returned **no hits**; one **real** comment mentioning *simplicial type theory* (adjacent math, pre-Rzk assistant) was recovered. No fabricated Reddit posts were added.

---

## What arctic_shift is

From the project README (clone tip, research time):

> Making Reddit data accessible to researchers, moderators and everyone else. Interact with the data through large dumps, an API or web interface.

Three interaction modes:

| Mode | Entry | Suitable for Rzk keyword search? |
|------|-------|----------------------------------|
| **Compressed dumps** (`.zst` / legacy `.zst_blocks`) | [download_links.md](https://github.com/ArthurHeitmann/arctic_shift/blob/main/download_links.md); [GitHub Releases](https://github.com/ArthurHeitmann/arctic_shift/releases); Academic Torrents | **No** for this box — see sizes below |
| **HTTP API** | Base `https://arctic-shift.photon-reddit.com` — docs in repo `api/README.md` | **Yes** — primary path used here |
| **Web UIs** | [Search](https://arctic-shift.photon-reddit.com/search); [download-tool](https://arctic-shift.photon-reddit.com/download-tool) (users / smaller subreddits) | **Yes** (manual); both returned HTTP 200 from the box |

Helper scripts (`scripts/processFiles.py`) stream `.zst` / `.jsonl` without full unpack (requires Python ≥ 3.10 + `zstandard`). Data provenance notes: [file_content_explanations.md](https://github.com/ArthurHeitmann/arctic_shift/blob/main/file_content_explanations.md) — official Reddit API collection; private/quarantined subs omitted; 2023-11+ dual retrieval / `_meta` merge.

---

## Dump sizes (why full dumps are impractical here)

Verified from Academic Torrents / magnet metadata linked by arctic_shift `download_links.md`:

| Archive | Approx. size | Source note |
|---------|--------------|-------------|
| Reddit submissions+comments **2005-06 → 2024-12** | **~3.12 TB** compressed | Academic Torrents `contentSize` / page “Download 3.12TB” (`ba051999…`) |
| Aggregate **2005-06 → 2025-12** magnet | **~3.80 TB** (`xl=3804096351995`) | Magnet in `download_links.md` |
| Individual recent **comment** months (e.g. 2024-06…12) | **~32–36 GB** each (`.zst`) | Same torrent listing |

Monthly dumps continue into **2026** on Academic Torrents (links listed through 2026-08 in upstream `download_links.md` at research time). The README explicitly recommends working on compressed files and using dumps for “massive” workloads; the API README says the same for heavy users.

**Box conclusion:** downloading even one recent comment month, let alone the multi-year corpus, is out of scope for these notes. We did **not** torrent dumps.

---

## Lightweight API: how to query

Base URL: `https://arctic-shift.photon-reddit.com`

Useful endpoints (paraphrased from `api/README.md`):

- `GET /api/posts/search` — filters: `author`, `subreddit`, `after`/`before`, `title` / `selftext` / `query` (keyword), `limit`, `sort`
- `GET /api/comments/search` — + `body`, `link_id`, `parent_id`
- `GET /api/posts/ids` / `/api/comments/ids` — ID lookup (good for verifying known threads)

**Important constraint (*verified* by live 400 responses):** keyword parameters `query` / `title` / `selftext` / `body` require an accompanying **`author` or `subreddit`** (global full-text without a scope is rejected). Active subs can time out; rate limits return HTTP 429 / “Too many requests” / “Timeout” under burst traffic. Prefer low `limit`, narrow `after`/`before`, and backoff.

No API key is documented; the service asks for considerate use and points heavy users at monthly dumps.

---

## Minimal real queries attempted (2026-09-28 SGT)

| Query | Result |
|-------|--------|
| `posts/search?query=rzk` (no subreddit) | **400** — `'query' requires one of: author, subreddit` |
| `posts/search?subreddit=dependent_types\|homotopytypetheory\|types\|math&title=rzk` | **`{"data":[]}`** |
| `comments/search?subreddit=dependent_types\|homotopytypetheory&body=rzk` | **`{"data":[]}`** |
| `posts/ids?ids=6dnmpg,9g6rtz,7pkwbh,42j8vu,e9pgbw,s8wp2b` | **Hit** — metadata matches prior Google-indexed rows (see below) |
| `comments/search?subreddit=types&body=simplicial&limit=5` | **Hit** — comment `dsi58ir` under `t3_7pkwbh` naming *simplicial type theory* and *cubical type theory* |

Further bursts (`haskell` body=`rzk`, `math` body=`"simplicial type theory"`, etc.) hit rate limits / timeouts; **not** treated as positive or negative evidence beyond the successful empty/non-empty responses above.

### ID-verified adjacent posts (arctic_shift)

Timestamps converted to Asia/Singapore:

| ID | Subreddit | Title (API) | created (SGT) | score | comments |
|----|-----------|-------------|----------------|-------|----------|
| `6dnmpg` | dependent_types | A Type Theory for Synthetic ∞-Categories | 2017-05-27 21:15 SGT | 9 | 2 |
| `9g6rtz` | math | The synthetic theory of ∞-categories vs … [slides] | 2018-09-16 09:23 SGT | 28 | 3 |
| `7pkwbh` | types | Homotopy type theory from computational perspective? | 2018-01-11 10:26 SGT | 13 | 7 |
| `42j8vu` | dependent_types | Towards a Directed Homotopy Type Theory… (Nuyts) | 2016-01-25 10:50 SGT | 8 | 12 |
| `e9pgbw` | agda | Cubical Agda: A Dependently Typed Programming Language… | 2019-12-13 00:02 SGT | 15 | 3 |
| `s8wp2b` | homotopytypetheory | Anders CCHM/HTS Theorem Prover | 2022-01-21 08:03 SGT | 4 | 0 |

### Real comment hit (simplicial TT, not Rzk)

- **Comment id:** `dsi58ir`  
- **Link:** `t3_7pkwbh` (r/types)  
- **created:** 2018-01-11 11:55 SGT  
- **score:** 2  
- **Body gist (*paraphrase*):** points at “simplicial type theory and cubical type theory” and recent cubical computational models — **not** a mention of the Rzk assistant or `rzk-lang`.

---

## Usability verdict for Rzk research

1. **Do use** arctic_shift **API / search UI / download-tool** for scoped keyword checks when Reddit.com itself is blocked — this is the right lightweight path.
2. **Do not** plan on ingesting full arctic_shift torrents for a niche assistant like Rzk without dedicated storage and seeding time (multi-TB).
3. **Finding unchanged:** no arctic_shift-backed evidence of Reddit threads primarily about Rzk / `rzk-lang` / sHoTT as of this pass; adjacent RSTT / HoTT discourse exists and can be ID-verified.
4. **Rate limits** are real — document empty results carefully; do not invent “no discussion” from a 429.

---

## Sources for this note

- https://github.com/ArthurHeitmann/arctic_shift (README, `api/README.md`, `download_links.md`, `file_content_explanations.md`) — cloned 2026-09-28  
- Live API base https://arctic-shift.photon-reddit.com  
- Academic Torrents listing for `ba051999301b109eab37d16f027b3f49ade2de13` (size metadata)
