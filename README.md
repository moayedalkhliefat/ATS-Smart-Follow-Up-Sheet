# ATS Smart Follow-Up Sheet

A modern, responsive Applicant Tracking System (ATS) and Candidate Follow-Up Sheet designed to help recruiters and job seekers track applications, interview stages, notes, statuses, and resume documents with **100% free online cloud storage**.

---

## 🌐 Recommended Free Cloud Stack Architecture

To fulfill your requirements for **Free Online Storage**, **Reliability**, **Multi-Device Access**, and **Ease of Use for Beginners**, we recommend the following industry-standard, 100% free stack:

```
[ GitHub / Netlify / Vercel ]  --->  [ Supabase (PostgreSQL Database + File Storage) ]
    (Free Website Hosting)                     (Free Cloud Database & Resumes)
```

### Breakdown of Responsibilities:

1. **Website Hosting — GitHub Pages, Netlify, or Vercel**
   - **What it does:** Hosts your HTML, CSS, and JavaScript website files online so you can access your ATS from any browser or device via a public URL (e.g., `https://your-app.netlify.app`).
   - **Cost:** **100% Free** (Unlimited static site hosting, custom domains, SSL/HTTPS certificates, global CDN).

2. **Database & Data Storage — Supabase (PostgreSQL)**
   - **What it does:** Stores your candidate records, application statuses, interview notes, dates, and metadata securely in the cloud. Any changes made on your phone, tablet, or work laptop sync instantly across all devices.
   - **Cost:** **100% Free** (Generous free tier with relational SQL database).

3. **File Storage — Supabase Storage**
   - **What it does:** Stores uploaded candidate files, such as resumes, CVs, cover letters, and portfolios (PDFs, DOCX, images).
   - **Cost:** **100% Free** (1 GB included on the free tier).

---

## 📋 Answering Your 10 Questions About Supabase (Free Database & File Storage)

### 1. Does the service have a free plan?
**Yes.** Supabase offers a robust **Free Tier** designed for hobbyists, prototypes, and small projects.

### 2. Can I use the free plan for this project without paying?
**Yes, absolutely.** The ATS Smart Follow-Up Sheet easily fits within the limits of the Supabase Free Tier. You will never be billed unless you explicitly upgrade to a paid plan.

### 3. What is included in the free plan?
- 2 Free Supabase Projects (databases).
- Full PostgreSQL database with relational tables, Row Level Security (RLS), and real-time capabilities.
- REST and GraphQL-style APIs generated automatically.
- Authentication (Email/Password, Social logins, etc.).
- File Storage buckets for documents/resumes.
- Client SDKs for JavaScript/HTML (`@supabase/supabase-js`).

### 4. What is the storage limit?
- **Database Storage:** Up to **500 MB** of relational database storage (which can hold tens of thousands of candidate records and notes).
- **File Storage:** Up to **1 GB** of file storage for resumes, PDFs, and documents.

### 5. What are the database/data limits?
- 500 MB relational database storage.
- Unlimited tables, rows (subject to total storage size), and queries.

### 6. What are the limits on users, requests, bandwidth, or file uploads?
- **Auth Users:** Up to 50,000 monthly active users.
- **Bandwidth / Data Transfer:** 2 GB per month.
- **API Requests:** Unlimited (subject to fair use / rate limits against abuse).
- **File Uploads:** Max file size per upload is typically up to 50MB (with 1 GB total bucket capacity).

### 7. Is a credit card required?
**No.** Supabase **does not require a credit card** to create a free account or start a free project. You cannot accidentally incur charges because billing is not tied to your free project unless you manually enter payment details to upgrade to a Pro plan.

### 8. What happens if I reach the free limit?
- If your project exceeds the free tier limits or remains inactive for 90 days without API traffic, Supabase may pause the project.
- You will receive notification emails well in advance. 
- Because no credit card is on file, **your card will never be automatically charged**. You can reactivate or export your data at any time.

### 9. Will my data remain safe if I stay within the free limits?
**Yes.** Supabase runs on enterprise-grade cloud infrastructure (AWS) with data encryption in transit (HTTPS/SSL) and at rest, automated daily backups, and Row Level Security (RLS) policies to protect your candidate data.

### 10. Is it easy for a beginner to manage?
**Yes.** Supabase provides a visual spreadsheet-like Table Editor where you can view, add, edit, and delete candidate records directly in your browser without writing complex SQL, alongside a simple JavaScript CDN library (`<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>`) that connects directly to your HTML application.

---

## 🚀 How to Set Up Your Free Cloud Database (5 Minutes)

1. Go to [Supabase](https://supabase.com) and create a free account (no credit card required).
2. Create a **New Project** (choose any name, password, and region).
3. Once your project is ready, go to **SQL Editor** and run the following SQL query to create your candidates table:

```sql
create table candidates (
  id uuid default gen_random_uuid() primary key,
  name text not null,
  role text not null,
  email text,
  phone text,
  status text default 'Applied',
  notes text,
  resume_url text,
  created_at timestamp with time zone default timezone('utc'::text, now()) not null
);

-- Enable Row Level Security (or disable for open personal usage)
alter table candidates enable row level security;

-- Create policy for public access (for personal/team single-user use without complex auth)
create policy "Allow public access to candidates"
  on candidates for all
  using (true)
  with check (true);
```

4. Go to **Project Settings > API** to copy your:
   - **Project URL** (`https://xyzcompany.supabase.co`)
   - **Anon/Public API Key** (`eyJhbGciOi...`)
5. Open `index.html` in your ATS application, click **Settings / Cloud Sync**, and paste your Supabase URL and Key to instantly sync your ATS across all your devices!

---

## 💻 Quick Local Testing
Open `index.html` directly in any web browser, or run a local static server:
```bash
python3 -m http.server 8080
```
