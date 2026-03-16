# Quick Start Guide - Gilroy Urbanist

## To Resume Work

### 1. Start Local Server
```bash
cd /home/lando/projects/gilroy-urbanist
python3 -m http.server 8000
```
Then visit: http://localhost:8000/map-demo.html

### 2. Check Current Status
- Read: `.claude/session-summary.md` for last session recap
- Read: `.claude/project-plan.md` for full roadmap

### 3. View Files
```bash
ls -la /home/lando/projects/gilroy-urbanist
```

---

## Current Project State

**Repository:** https://github.com/jelloshooter848/gilroy_urbanist

**Working Demo:** `map-demo.html` (121 interactive areas)

**SVG Map:** `map.svg` (75% complete)

**Next Priority:** Finish SVG map, then set up React + Supabase

---

## Useful Commands

### Git
```bash
git status
git add .
git commit -m "Your message"
git push origin main
```

### View Map in Inkscape
```bash
inkscape /home/lando/projects/REFERENCE/Oldtown\ Gilroy\ Map.svg
```

### Check Background Processes
```bash
ps aux | grep python
kill <process_id>  # to stop server
```

---

## File Locations

- **Project:** `/home/lando/projects/gilroy-urbanist/`
- **Reference Files:** `/home/lando/projects/REFERENCE/`
- **SVG Map:** `map.svg` (in project) or `REFERENCE/Oldtown Gilroy Map.svg` (source)

---

## Remember

✅ Always ask before committing/pushing to Git
✅ Server must be running to view map-demo.html (CORS issue)
✅ SVG labels are read from `inkscape:label` attributes
✅ 121 shapes total, auto-detecting location types

---

**Last Updated:** March 15, 2026
