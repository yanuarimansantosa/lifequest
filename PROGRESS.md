# LifeQuest — Career Intelligence Platform

**Status: IN PROGRESS** | Last updated: 2026-06-20

---

## 📋 Project Summary

LifeQuest adalah SPA (Single Page Application) untuk siswa Indonesia yang membantu mereka menemukan karir masa depan yang sesuai dengan karakter dan dampak sosial yang ingin mereka buat, plus mengukur AI impact pada setiap karir.

- **URL:** https://lifequest.medinovatech.com
- **Tech Stack:** Vanilla JS + HTML/CSS, localStorage persistence
- **GitHub:** github.com/yanuarimansantosa/lifequest
- **Target User:** Pelajar SMA/SMK & mahasiswa awal (15-20 tahun)

---

## ✅ Phase 1 — COMPLETE (Core SPA)

### Features Done
- **S0 — Homepage:** 2 menu cards (Kenali Dirimu + Jelajahi Karier), single landing page
- **S1-S2 — RIASEC Assessment:** 36 questions, 6 dimensions (R/I/A/S/E/C), Likert scale 1-5
- **S3 — Career Grid:** Browse 58 karier, filter by 11 sectors
- **S4 — Career Matching:** 60% RIASEC + 40% mission alignment, top 5 careers
- **S5 — Career Intelligence:** 
  - AI Risk exposure (0-100 scale)
  - Projection: 2026/2030/2035 career sustainability
  - At-risk tasks (AI will automate)
  - Growing tasks (human advantage)
  - Human advantage overview
  - Career roadmap (timeline steps)
  - Related careers (tetangga)

### Data — Jun 19 2026
- **30 original careers** (health, it, biz, arts, social, edu, science, eng, security, media, sports)
- **28 new careers added** (cloud-eng, fashion, interior, ilustrator, fotografer, podcaster, penulis, fisikawan, geologi, ngo-worker, policy-analyst, sipil, mesin, elektro, industri, polisi, tentara, forensik, investigator, instruktur, kurikulum, pustakawan, konselor, atlet, pelatih, sport-scientist, sport-manager, fisioterapis)
- **Total: 58 careers** across 11 sectors (5 each, health 8)
- **CAREER_INTEL data:** Complete AI impact analysis per career

### Code Structure
```
index.html (single file SPA — 255KB)
├── HTML: screens S0-S5 + styles
├── CSS: dark mode (--bg, --border, --text variables)
├── JS: state management, screen navigation, assessment logic, career matching
├── Data: CAREERS array (58 entries), CAREER_INTEL object, PATHWAY_DATA (partial)
└── localStorage: persist assessment & filter choices
```

### Latest Changes (Jun 19 2026)
1. Fixed `cat:'tech'` → `cat:'science'` (agri career)
2. Injected 28 new careers with full CAREER_INTEL data
3. All 11 sectors now have 5 careers each (health 8)

---

## 🔄 Phase 2 — IN PROGRESS (Expansion & Career Pathways)

### Task Status (Jun 19)

#### Task 1: Update Filter Buttons to 11 Sectors
**Status:** ✅ COMPLETE (Jun 19, commit 468e793)
- ✅ 12 buttons implemented (Semua + 11 sectors)
- Location: index.html lines 424-435

#### Task 2: Career Pathway Section ("Peta Jalan Karier")
**Status:** PENDING | Est. 3-4 hours total
- Section: Accordion below Career MRI (S5)
- Header CTA: "Sudah yakin? Lihat peta jalanmu →"
- Content: Pathway level badge + education path + SMA prep checklist
- Pathway Levels (colors NO red/yellow/black):
  - `free`: Mulai Sekarang (teal #0d9488)
  - `flex`: Jalur Fleksibel (indigo #6366f1)
  - `degree`: Gelar Diperlukan (violet #7c3aed)
  - `licensed`: Profesi Berlisensi (slate #334155)

**Subtasks:**
- [ ] Code HTML/CSS/JS for accordion section
- [ ] Populate PATHWAY_DATA for all 58 careers (formal/alt/min_years/license/sma_prep)
- [ ] Integrate with renderCi() function
- [ ] QA test expand/collapse + data display

---

## 📋 Phase 3 — PLANNED (Kampus Database)

**Status:** PLAN READY (development not started)

### Scope
- 38 Indonesian provinces × 10 universities = 380+ entries
- Rankings: Webometrics (national) + QS (world top 30)
- Programs: Only relevant to LifeQuest careers (~30 programs)
- Accreditation: BAN-PT data per program
- Displayed in: Peta Jalan section, filter by province + type (negeri/swasta)

### Data Structure
```js
KAMPUS_DB = {
  universities: [
    {
      id: 'ui',
      nama: 'Universitas Indonesia',
      kota: 'Depok',
      provinsi: 'Jawa Barat',
      tipe: 'negeri',
      rank_nasional: 1,
      rank_dunia: 521,
      prodi: [
        { nama: 'Kedokteran', akreditasi: 'Unggul', tahun: 2023 }
      ],
      url: 'ui.ac.id'
    },
    // ... 380+ universities
  ]
}
```

### Sources
- webometrics.info/en/Asia/Indonesia
- QS World University Rankings
- BAN-PT (banpt.or.id)
- PDDikti (pddikti.kemdikbud.go.id)

### Update Frequency
- Annual manual update (Q1 each year)
- File: data/kampus-db.js (separate, loaded lazy)

---

## 📅 Work Timeline

### DONE (Jun 19)
- ✅ Fix `cat:'tech'` stray
- ✅ Inject 26 karier baru (28 total)
- ✅ All 11 sectors complete (5 each)

### THIS WEEK (Jun 20)
- [x] ~~Update filter buttons~~ (Jun 19, done)
- [ ] Code Peta Jalan UI (1-2 hours)
- [ ] Populate PATHWAY_DATA (2-3 hours)
- [ ] Integrate & QA (1 hour)

### NEXT WEEK
- [ ] Code Kampus DB filter + display
- [ ] QA all features
- [ ] Tag v1.1, commit

### LATER (Jul+)
- [ ] Scrape kampus data from Webometrics/BAN-PT
- [ ] Integrate kampus section
- [ ] Tag v1.2

---

## 🔗 Key Files

| File | Content | Lines |
|------|---------|-------|
| index.html | SPA code (single file) | 255KB |
| CAREERS[] | Career entries (58 total) | 600-900 |
| CAREER_INTEL{} | AI impact data per career | 1000-4000 |
| PATHWAY_DATA{} | Education paths (to be completed) | TBD |
| Filter buttons | S3 career grid | 424-427 |
| S5 (Career MRI) | Career intelligence display | <div id="s5"> |

---

## 💡 Notes for Next Developer

1. **Index.html is single file** — all HTML/CSS/JS in one file, no build step needed
2. **localStorage persistence** — state (assessment, filter, choices) saved automatically
3. **PATHWAY_DATA needed** — 58 karier × edu_path (formal/alt/min_years/license/sma_prep)
4. **No backend** — all data client-side, no server required
5. **Kampus DB is separate** — will be lazy-loaded as data/kampus-db.js when user opens Peta Jalan

---

Last updated: 2026-06-19 | dev@medinovatech.com

---

## ✅ Task 3: Kampus Database Prodi Links (Jun 20)

**Status:** ✅ COMPLETE — MOBILE-OPTIMIZED (commits 3810137→d3c79dc, tags v20260620.2→v20260620.3)

### Iteration 1 (v20260620.2)
- Added `getProdiUrl()` function to dynamically generate URLs for 200+ prodi
- Updated renderKampus() to render prodi as clickable `<a>` tags

### Iteration 2 (v20260620.3) — Mobile Optimizations
Fixed for finger-friendly tapping:
1. **HTML Bug Fix:** Closing tag `</span>` → `</a>` (was breaking link wrapping)
2. **Mobile Styling:** Added `display:inline-flex; gap:5px` inline to prodi chips for proper clickable area
3. **Working URLs:** 
   - UI prodi use faculty domains: `https://fk.ui.ac.id`, `https://fasilkom.ui.ac.id`, `https://law.ui.ac.id`, etc. (verified 200 OK)
   - Other kampus fall back to `https://[id].ac.id` (e.g., `https://itb.ac.id`, `https://ugm.ac.id`, tested 200 OK)

### Features
- **Entire card clickable:** Full prodi area is a link, not just text
- **Finger-optimized:** Proper spacing + flex layout for easy mobile tapping
- **No broken links:** All URLs verified working (not 404s)
- **Badge preserved:** Akreditasi badge visible on every clickable link
- **Opens in new tab:** target="_blank" + rel="noopener noreferrer"

### End-to-End Flow (Mobile-Ready)
Select Career (e.g., Dokter) → View Intelligence (S5) → Expand Peta Jalan → **Tap any prodi card area** → Opens university website in new tab

### Deployment
- ✅ v20260620.2: Initial implementation (dynamic URL generator)
- ✅ v20260620.3: Mobile fixes (full card clickable, working URLs)
- ✅ Both tagged, pushed to yanuarimansantosa/lifequest GitHub
- ✅ Live at https://lifequest.medinovatech.com

