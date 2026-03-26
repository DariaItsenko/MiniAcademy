# 📧 Parent Email Reports Setup

## Overview
The app now supports sending weekly progress reports to parents via email using the Resend email service.

## Features Added
✅ Parent email configuration in Account Page
✅ Manual "Send Report Now" button
✅ Beautiful HTML email template with:
- Overall performance grade (12-point scale)
- Stars earned by subject (Math, English, Ukrainian)
- Engagement metrics (streak, points)
- Achievements & badges
- Personalized teacher's notes
- Study recommendations

## Setup Instructions

### 1. Get a Resend API Key
1. Go to https://resend.com
2. Sign up for a free account
3. Navigate to API Keys section
4. Create a new API key
5. Copy the API key (starts with `re_`)

### 2. Add API Key to Your App
1. The app will prompt you to add your `RESEND_API_KEY`
2. Paste your API key when prompted
3. The key is stored securely as an environment variable

### 3. Configure Parent Email
1. Log in as a student
2. Go to Account Page (click username in top-right)
3. Scroll to "Parent Progress Reports" section
4. Enter parent's email address
5. Click "💾 Save"

### 4. Send Reports
**Manual:** Click "📤 Send Report Now" button in Account Page

**Automatic (Future Enhancement):** 
Set up a scheduled job to call the `/send-report` endpoint weekly

## Email Template Preview
The email includes:
- 📊 Weekly Progress Report header
- 📈 Overall performance grade
- ⭐ Stars by subject breakdown
- 🔥 Streak and engagement metrics
- 🏆 Achievements & badges earned
- 💡 Personalized teacher's notes with recommendations

## API Endpoint
**POST** `/make-server-51051136/send-report`

**Body:**
```json
{
  "username": "student_name",
  "parentEmail": "parent@example.com",
  "progress": { /* user progress object */ },
  "points": 250,
  "streak": 7,
  "grade": 3,
  "badges": [ /* badges array */ ]
}
```

## Important Notes
- **Free Tier:** Resend offers 100 emails/day for free
- **From Address:** Currently uses `onboarding@resend.dev` (Resend's test address)
- **Custom Domain:** For production, you should verify your own domain in Resend
- **Testing:** Use your own email to test the report format

## Troubleshooting
- If email fails to send, check that `RESEND_API_KEY` is set correctly
- Verify the parent email is a valid email format
- Check browser console for error messages
- Verify your Resend account is active and within rate limits

## Future Enhancements
- [ ] Scheduled weekly automatic reports
- [ ] Email language selection (English/Ukrainian)
- [ ] Custom email templates per grade level
- [ ] Report history tracking
- [ ] Multiple parent emails
