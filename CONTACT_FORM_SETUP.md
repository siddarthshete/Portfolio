# Contact Form Backend Setup Guide

I've implemented three different options for connecting your contact form to a backend. Choose the one that best fits your needs:

## Option 1: EmailJS (Recommended - Easiest)

**Pros:** No backend required, easy setup, free tier available
**Cons:** Limited customization, requires EmailJS account

### Setup Steps:

1. **Sign up for EmailJS:**
   - Go to [emailjs.com](https://www.emailjs.com/)
   - Create a free account

2. **Configure Email Service:**
   - Add your email service (Gmail, Outlook, etc.)
   - Get your Service ID

3. **Create Email Template:**
   - Create a new email template
   - Use variables: {{name}}, {{email}}, {{subject}}, {{message}}
   - Get your Template ID

4. **Update the Code:**
   Replace these placeholders in `index.html`:
   ```javascript
   emailjs.init("YOUR_PUBLIC_KEY"); // Your EmailJS public key
   emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', formData)
   ```

5. **Test the Form:**
   - Open your portfolio
   - Fill out and submit the contact form
   - Check your email for the message

## Option 2: Formspree (Also Easy)

**Pros:** No backend required, simple setup, good free tier
**Cons:** Limited customization, requires Formspree account

### Setup Steps:

1. **Sign up for Formspree:**
   - Go to [formspree.io](https://formspree.io/)
   - Create a free account

2. **Create a Form:**
   - Create a new form
   - Get your form endpoint URL

3. **Update the Code:**
   Replace the form action in `formspree-alternative.html`:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```

4. **Test the Form:**
   - Submit a test message
   - Check your email

## Option 3: Custom Node.js Backend (Most Control)

**Pros:** Full control, customizable, can add features like spam protection
**Cons:** Requires hosting, more complex setup

### Setup Steps:

1. **Install Dependencies:**
   ```bash
   cd backend
   npm install
   ```

2. **Configure Environment Variables:**
   - Copy `env.example` to `.env`
   - Add your email credentials:
   ```
   EMAIL_USER=your-email@gmail.com
   EMAIL_PASS=your-app-password
   PORT=3000
   ```

3. **For Gmail Users:**
   - Enable 2-factor authentication
   - Generate an App Password
   - Use the App Password in EMAIL_PASS

4. **Start the Server:**
   ```bash
   npm start
   # or for development
   npm run dev
   ```

5. **Update Frontend (if using custom backend):**
   - Use the code from `custom-backend-contact.html`
   - Update the fetch URL if your backend is hosted elsewhere

6. **Deploy the Backend:**
   - Deploy to platforms like Heroku, Railway, or Vercel
   - Update the frontend fetch URL to your deployed backend URL

## Security Considerations

### For EmailJS/Formspree:
- These services handle security for you
- No additional security measures needed

### For Custom Backend:
- Add rate limiting to prevent spam
- Add CAPTCHA verification
- Validate and sanitize input
- Use HTTPS in production

## Example Rate Limiting (Custom Backend)

Add this to your `server.js`:

```javascript
const rateLimit = require('express-rate-limit');

const limiter = rateLimit({
    windowMs: 15 * 60 * 1000, // 15 minutes
    max: 5, // limit each IP to 5 requests per windowMs
    message: 'Too many contact form submissions from this IP'
});

app.use('/api/contact', limiter);
```

## Testing Your Setup

1. **Test Form Submission:**
   - Fill out all fields
   - Submit the form
   - Check for success/error messages

2. **Test Email Delivery:**
   - Check your email inbox
   - Verify all form data is included

3. **Test Error Handling:**
   - Try submitting with missing fields
   - Test network errors (disconnect internet)

## Troubleshooting

### EmailJS Issues:
- Check your Service ID and Template ID
- Verify your EmailJS account is active
- Check browser console for errors

### Formspree Issues:
- Verify your form endpoint URL
- Check Formspree dashboard for submissions
- Ensure form fields match template

### Custom Backend Issues:
- Check server logs for errors
- Verify email credentials
- Test CORS settings
- Check environment variables

## Recommended Choice

For a portfolio website, I recommend **EmailJS** because:
- No backend hosting required
- Easy to set up and maintain
- Reliable and secure
- Good free tier for personal use
- Professional email delivery

The implementation is already in your `index.html` file. Just follow the EmailJS setup steps above to get it working! 