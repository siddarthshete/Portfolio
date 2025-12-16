# Complete Contact Form Setup Guide

Your contact form is now properly implemented with EmailJS integration. Follow these steps to get it working:

## 🚀 Quick Setup (5 minutes)

### Step 1: Create EmailJS Account
1. Go to [emailjs.com](https://www.emailjs.com/)
2. Sign up for a free account
3. Verify your email address

### Step 2: Add Email Service
1. In your EmailJS dashboard, go to **Email Services**
2. Click **Add New Service**
3. Choose **Gmail** (or your preferred email provider)
4. Follow the setup instructions
5. **Copy your Service ID** (e.g., `service_abc123`)

### Step 3: Create Email Template
1. Go to **Email Templates** in your dashboard
2. Click **Create New Template**
3. Use this template content:

```
Subject: Portfolio Contact: {{subject}}

New message from your portfolio website:

Name: {{name}}
Email: {{email}}
Subject: {{subject}}

Message:
{{message}}

---
This message was sent from your portfolio contact form.
```

4. **Copy your Template ID** (e.g., `template_xyz789`)

### Step 4: Get Your Public Key
1. Go to **Account** → **General**
2. **Copy your Public Key** (e.g., `user_abc123def456`)

### Step 5: Update Your Code
Open `index.html` and replace these three placeholders:

```javascript
// Line 512: Replace YOUR_PUBLIC_KEY
emailjs.init("YOUR_PUBLIC_KEY"); // Replace with your EmailJS public key

// Line 548: Replace YOUR_SERVICE_ID and YOUR_TEMPLATE_ID
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', formData)
```

**Example with real values:**
```javascript
emailjs.init("user_abc123def456");
emailjs.send('service_abc123', 'template_xyz789', formData)
```

### Step 6: Test Your Form
1. Open your portfolio in a web browser
2. Scroll to the Contact section
3. Fill out the form and submit
4. Check your email for the message

## ✅ What's Already Working

Your contact form now includes:

- ✅ **Form Validation**: All fields are required
- ✅ **Loading States**: Button shows "Sending..." with spinner
- ✅ **Success/Error Messages**: Clear feedback to users
- ✅ **Form Reset**: Form clears after successful submission
- ✅ **Error Handling**: Graceful fallback if EmailJS fails
- ✅ **Responsive Design**: Works on all devices

## 🔧 Alternative Options

If you prefer not to use EmailJS, you have these alternatives:

### Option A: Formspree (Easiest Alternative)
1. Go to [formspree.io](https://formspree.io/)
2. Create a free account
3. Create a new form
4. Replace the form in `index.html` with the code from `formspree-alternative.html`
5. Update the form action URL

### Option B: Custom Backend (Most Control)
1. Use the Node.js backend in the `backend/` folder
2. Follow the instructions in `CONTACT_FORM_SETUP.md`
3. Replace the form handling code with the code from `custom-backend-contact.html`

## 🐛 Troubleshooting

### Form Not Sending
- Check browser console for errors (F12 → Console)
- Verify your EmailJS credentials are correct
- Make sure your email service is properly configured

### "Failed to send message" Error
- Check your EmailJS dashboard for error logs
- Verify your template variables match: `{{name}}`, `{{email}}`, `{{subject}}`, `{{message}}`
- Ensure your email service is active

### No Email Received
- Check spam/junk folder
- Verify the "to" email address in your template
- Check EmailJS dashboard for delivery status

## 📧 Email Template Variables

Make sure your EmailJS template uses these exact variable names:
- `{{name}}` - Sender's name
- `{{email}}` - Sender's email
- `{{subject}}` - Message subject
- `{{message}}` - Message content

## 🎨 Customization

### Change Success/Error Messages
Edit the messages in the JavaScript code around line 550-554:

```javascript
showMessage('Message sent successfully! I\'ll get back to you soon.', 'success');
showMessage('Failed to send message. Please try again or contact me directly at siddarthshete@gmail.com', 'error');
```

### Change Email Recipient
In your EmailJS template, set the "To" field to your email address.

### Add More Form Fields
1. Add the HTML input in the form
2. Add the field to the `formData` object in JavaScript
3. Add the variable to your EmailJS template

## 🚀 Going Live

Once you've tested locally:

1. **Deploy your portfolio** to any hosting service (Netlify, Vercel, GitHub Pages, etc.)
2. **Update CORS settings** in EmailJS if needed
3. **Test the live form** to ensure it works in production

## 📞 Support

If you need help:
1. Check the EmailJS documentation: [emailjs.com/docs](https://www.emailjs.com/docs)
2. Check browser console for error messages
3. Verify all credentials are correct

Your contact form is now ready to receive messages! 🎉



