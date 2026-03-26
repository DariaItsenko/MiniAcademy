# 🚀 Quick Deployment Guide

## Fastest Way: Deploy to Vercel

### Step 1: Create Vercel Account
1. Go to https://vercel.com
2. Click "Sign Up"
3. Choose "Continue with GitHub"

### Step 2: Upload to GitHub
1. Create account at https://github.com
2. Create new repository
3. In terminal:
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/education-app.git
git push -u origin main
```

### Step 3: Deploy
1. Login to Vercel
2. Click "Add New..." → "Project"
3. Import your GitHub repository
4. Add environment variables:
   - `SUPABASE_URL`
   - `SUPABASE_ANON_KEY`
   - `SUPABASE_SERVICE_ROLE_KEY`
   - `RESEND_API_KEY`
5. Click "Deploy"

### ✅ Done!
Your site will be live at: `https://your-app.vercel.app`

---

## Alternative: Quick CLI Deploy

```bash
# Install Vercel CLI
npm install -g vercel

# Deploy
vercel

# Add environment variables
vercel env add SUPABASE_URL
vercel env add SUPABASE_ANON_KEY
vercel env add SUPABASE_SERVICE_ROLE_KEY
vercel env add RESEND_API_KEY

# Deploy to production
vercel --prod
```

---

## 📝 Pre-Deploy Checklist

- [ ] All environment variables added
- [ ] Supabase configured
- [ ] Email API key added
- [ ] Test build locally: `npm run build`
- [ ] All files committed to Git

---

## 🔄 Update Your Site

After any code changes:
```bash
git add .
git commit -m "Description of changes"
git push
```

Vercel will automatically deploy the update!

---

For detailed instructions in Ukrainian, see `DEPLOYMENT_GUIDE_UA.md`
