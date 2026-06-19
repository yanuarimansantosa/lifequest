# LifeQuest — Career Intelligence Platform

**Status: IN PROGRESS** | Last updated: 2026-06-19

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

### Pending Tasks (Jun 19)

#### Task 1: Update Filter Buttons to 11 Sectors
**Status:** PENDING | Est. 15 min
- Current: 4 static buttons (Semua, Kesehatan, Teknologi, Bisnis)
- Target: 12 buttons (all, health, it, biz, arts, media, science, edu, social, eng, security, sports)
- Location: index.html lines 424-427

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
- [ ] Update filter buttons (15 min)
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
