# Gilroy Urbanist - Project Plan

## Project Vision
A hyperlocal community platform for Old Town Gilroy that serves as a one-stop shop for:
- Discovering local businesses, churches, nonprofits, recreation, food, and entertainment
- Finding events happening tonight, this week, this weekend, and this month
- Engaging with urbanism-focused content and advocacy
- Building community through interactive features and events

## Core Values
- Pro-urbanism focus
- Community engagement
- Support local businesses
- Walkability and livability advocacy

---

## Phase 1: MVP (Minimum Viable Product)

### Core Features

#### 1. Interactive Map
- **Technology:** Leaflet.js with custom raster overlay
- **Features:**
  - Clickable locations (businesses, landmarks, etc.)
  - Pop-up information cards for each location
  - Categories/filters (food, entertainment, services, etc.)
  - Mobile-responsive design
- **Data:** Store locations in Supabase database

#### 2. Event Calendar/Bulletin Board
- **Views:**
  - "What's Happening Tonight"
  - "This Week"
  - "This Weekend"
  - "This Month"
- **Features:**
  - Event cards with date, time, location, description
  - Filter by category (music, food, family-friendly, etc.)
  - Link events to map locations
- **Data:** Events stored in Supabase

#### 3. Business/Location Directory
- **Information per location:**
  - Name, category, description
  - Address, hours, contact info
  - Photos
  - Links to website/social media
  - Map coordinates
- **Features:**
  - Search functionality
  - Filter by category
  - Click from list to highlight on map

#### 4. Blog/Articles
- **Features:**
  - Full articles expanding on social media posts
  - Urbanism advocacy content
  - Community stories
  - Photo galleries
- **Implementation:** Markdown files or Supabase database
- **Future:** Link to social media posts

#### 5. Basic Admin Panel
- **Features:**
  - Add/edit/delete locations
  - Add/edit/delete events
  - Publish blog posts
  - Upload images
- **Access:** Password-protected via Supabase Auth

---

## Recommended Tech Stack

### Frontend
- **Framework:** React 18+
- **Build Tool:** Vite (fast, modern)
- **Styling:** Tailwind CSS (rapid development, mobile-first)
- **Map:** Leaflet.js
- **Routing:** React Router
- **State Management:** React Context API (Zustand if needed later)

### Backend/Database
- **Database:** Supabase
  - PostgreSQL database
  - Built-in authentication
  - Real-time subscriptions (for live event updates)
  - File storage for images
  - Row Level Security (RLS) for admin protection

### Hosting
- **Site:** GitHub Pages (free) or Netlify (free tier)
- **Database:** Supabase free tier
  - 500MB database
  - 50k monthly active users
  - 2GB file storage
  - Unlimited API requests

### Development Tools
- **Version Control:** Git + GitHub
- **Code Editor:** Any (VS Code recommended)
- **Package Manager:** npm or pnpm

---

## Database Schema (Supabase)

### Tables

#### `locations`
```sql
- id (uuid, primary key)
- name (text)
- category (text) -- food, entertainment, services, etc.
- description (text)
- address (text)
- lat (decimal)
- lng (decimal)
- hours (jsonb) -- {monday: "9am-5pm", ...}
- contact_phone (text)
- contact_email (text)
- website (text)
- social_media (jsonb) -- {facebook: "...", instagram: "..."}
- images (text[]) -- array of image URLs
- featured (boolean) -- for sponsors
- created_at (timestamp)
- updated_at (timestamp)
```

#### `events`
```sql
- id (uuid, primary key)
- title (text)
- description (text)
- start_datetime (timestamp)
- end_datetime (timestamp)
- location_id (uuid, foreign key -> locations)
- category (text)
- image_url (text)
- external_link (text)
- featured (boolean)
- created_at (timestamp)
- updated_at (timestamp)
```

#### `blog_posts`
```sql
- id (uuid, primary key)
- title (text)
- slug (text, unique)
- content (text) -- markdown
- excerpt (text)
- author (text)
- featured_image (text)
- published (boolean)
- published_at (timestamp)
- created_at (timestamp)
- updated_at (timestamp)
```

---

## Development Roadmap

### Week 1-2: Project Setup & Foundation
- [ ] Initialize React + Vite project
- [ ] Set up Tailwind CSS
- [ ] Set up Supabase project
- [ ] Create database schema
- [ ] Set up GitHub repository (already done!)
- [ ] Create basic routing structure
- [ ] Design color scheme and basic UI components

### Week 3-4: Interactive Map
- [ ] Integrate Leaflet.js
- [ ] Add custom map raster overlay
- [ ] Create location markers from database
- [ ] Build location popup cards
- [ ] Add category filtering
- [ ] Make mobile-responsive

### Week 5-6: Event Calendar
- [ ] Create event data model
- [ ] Build event card components
- [ ] Implement time-based filtering (tonight, week, weekend, month)
- [ ] Add category filtering
- [ ] Link events to map locations

### Week 7-8: Business Directory
- [ ] Create directory list view
- [ ] Build detailed location pages
- [ ] Implement search functionality
- [ ] Add category navigation
- [ ] Connect directory to map (click to highlight)

### Week 9-10: Blog System
- [ ] Set up markdown rendering
- [ ] Create blog post list page
- [ ] Build individual post pages
- [ ] Add image galleries
- [ ] Create blog post admin interface

### Week 11-12: Admin Panel
- [ ] Set up Supabase authentication
- [ ] Create admin login page
- [ ] Build location management interface
- [ ] Build event management interface
- [ ] Build blog post editor
- [ ] Add image upload functionality

### Week 13-14: Polish & Launch
- [ ] Mobile optimization
- [ ] Performance optimization
- [ ] SEO optimization (meta tags, sitemap)
- [ ] Cross-browser testing
- [ ] Content population
- [ ] Deploy to production
- [ ] Set up custom domain (if desired)

---

## Phase 2: Growth Features (Future)

### Community Engagement
- [ ] User comments (with moderation)
- [ ] User-submitted events (with approval)
- [ ] Photo submissions
- [ ] Event RSVPs
- [ ] Newsletter signup

### Business Features
- [ ] Sponsor/featured placement system
- [ ] Business dashboards (edit their own info)
- [ ] Analytics for businesses
- [ ] Advertisement management

### Membership Program
- [ ] Downtown membership card system
- [ ] Payment processing (Stripe)
- [ ] Member discounts tracking
- [ ] Digital membership cards
- [ ] Partner business portal

### Advanced Events
- [ ] Passport-style event system
- [ ] Scavenger hunt functionality
- [ ] Check-in system (QR codes)
- [ ] Leaderboards
- [ ] Prize tracking

### Content & Media
- [ ] Social media integration (auto-post)
- [ ] Photo galleries
- [ ] Video content
- [ ] Podcast integration
- [ ] Historical photo archives

### Physical Media
- [ ] Print-ready export of content
- [ ] Quarterly/annual publication layout
- [ ] QR codes linking to digital content
- [ ] Printed map versions

### Technical Enhancements
- [ ] Progressive Web App (PWA) - works offline
- [ ] Native mobile apps (iOS/Android)
- [ ] Push notifications
- [ ] Geolocation features
- [ ] Walking/biking route maps

---

## Phase 3: Full Platform (When Revenue Justifies)

### Migration to Full Stack
- Move from Supabase to dedicated backend
- Implement advanced payment processing
- Add email automation
- CRM for business partners
- Advanced analytics and reporting

### Estimated Costs: $20-50/month

---

## Cost Breakdown

### Phase 1 (Current)
- **Hosting:** $0/month (GitHub Pages)
- **Database:** $0/month (Supabase free tier)
- **Domain:** $10-15/year (optional)
- **Total:** $0-15/year

### Phase 2 (Growing)
- **Hosting:** $0/month (still free tier)
- **Database:** $0-25/month (may outgrow free tier)
- **Payment Processing:** 2.9% + $0.30 per transaction (Stripe)
- **Total:** $0-25/month + transaction fees

### Phase 3 (Scaled)
- **Hosting:** $10-20/month
- **Database:** $20-30/month
- **Email Service:** $10-15/month
- **Total:** $40-65/month

---

## Success Metrics

### Phase 1 Goals (First 3 Months)
- 500+ monthly visitors
- 50+ locations mapped
- 20+ events posted
- 5+ blog posts published
- 3+ regular returning users

### Phase 2 Goals (6-12 Months)
- 2,000+ monthly visitors
- 100+ locations mapped
- 50+ events per month
- 10+ blog posts per month
- 5+ business sponsors
- 50+ membership cards sold

---

## Progress Log

### Session 1 (2026-03-15)

#### ✅ Completed
1. ✅ Initialize Git repository
2. ✅ Create project plan document
3. ✅ Set up GitHub repository (gilroy_urbanist)
4. ✅ Configure SSH authentication for GitHub
5. ✅ Create basic placeholder index.html
6. ✅ Create interactive map demo (map-demo.html)
7. ✅ Import SVG map (75% complete, 121 shapes)
8. ✅ Implement clickable SVG shapes with hover effects
9. ✅ Read and display Inkscape labels (street names, building names)
10. ✅ Auto-detect location types (streets, buildings, parking, green spaces)
11. ✅ Set up local development server (Python HTTP server on port 8000)

#### 📝 Current State
- **Repository:** https://github.com/jelloshooter848/gilroy_urbanist
- **Local Server:** http://localhost:8000/map-demo.html
- **SVG Map:** 121 interactive areas with proper labels
- **Files Created:**
  - `.claude/project-plan.md` - Project documentation
  - `index.html` - Simple placeholder page
  - `map-demo.html` - Interactive map demo
  - `map.svg` - Old Town Gilroy map (75% complete)

#### 🎯 Key Decisions Made
- **Tech Stack:** React + Vite, Supabase, Leaflet.js (or pure SVG), Tailwind CSS
- **Map Approach:** Using custom SVG map with Inkscape labels
- **Hosting:** GitHub Pages (free tier)
- **Phase 1 Focus:** Interactive map + Event calendar (both simple versions)

## Next Steps

### Immediate (Next Session)
1. 🔲 Finish SVG map (remaining 25%)
2. 🔲 Set up React + Vite project structure
3. 🔲 Set up Supabase account and database
4. 🔲 Create database schema (locations, events, blog_posts tables)
5. 🔲 Integrate SVG map into React app

### Week 1-2 Tasks (Updated)
- [x] Initialize project and repository
- [x] Create interactive map proof-of-concept
- [ ] Set up React + Vite project
- [ ] Set up Tailwind CSS
- [ ] Set up Supabase project
- [ ] Create database schema
- [ ] Design color scheme and basic UI components
- [ ] Create basic routing structure

---

## Notes & Ideas

### Design Inspiration
- Urban planning blogs
- Local news sites
- Event platforms like Eventbrite
- Community boards like Nextdoor
- Modern, clean, mobile-first

### Color Scheme Ideas
- Earth tones (browns, greens) - connection to agriculture/garlic
- Urban modern (blues, grays) - professional, clean
- Vibrant (reds, yellows) - energetic, community-focused

### Features to Consider
- Walking time estimates between locations
- Bike-friendly route highlighting
- Public transit integration
- Parking information
- Accessibility information
- Pet-friendly locations

### Partnerships
- Chamber of Commerce
- Downtown Business Association
- Local government
- Tourism board
- Historical society

---

## Contact & Collaboration

This is a living document. Update as the project evolves!

Last Updated: 2026-03-15
