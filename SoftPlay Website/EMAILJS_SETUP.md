# EmailJS Setup Guide

This guide will help you configure EmailJS to enable contact form functionality on your website.

## Step 1: Create an EmailJS Account

1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Sign up for a free account (allows 200 emails per month)
3. Verify your email address

## Step 2: Add Email Service

1. Log in to your EmailJS dashboard
2. Go to **Email Services** in the sidebar
3. Click **Add New Service**
4. Choose your email provider (Gmail, Outlook, etc.)
5. Follow the setup instructions for your provider
6. Note your **Service ID** (you'll need this later)

## Step 3: Create Email Template

1. Go to **Email Templates** in the sidebar
2. Click **Create New Template**
3. Use the following template structure:

**Subject:**
```
Ново съобщение от {{from_name}}
```

**Content:**
```
Име: {{from_name}}
Имейл: {{from_email}}
Телефон: {{from_phone}}
Услуга: {{service}}
Съобщение:
{{message}}

---
Това съобщение е изпратено от контактната форма на Soft Play Solutions.
```

4. Set **To Email** to: `softplay1987@gmail.com`
5. Set **From Name** to: `{{from_name}}`
6. Set **Reply To** to: `{{reply_to}}`
7. Click **Save**
8. Note your **Template ID** (you'll need this later)

## Step 4: Get Your Public Key

1. Go to **Account** → **General** in the sidebar
2. Find your **Public Key** in the API Keys section
3. Copy the Public Key

## Step 5: Update script.js

Open `script.js` and replace the following placeholders:

1. **Line 41:** Replace `"YOUR_PUBLIC_KEY"` with your actual EmailJS Public Key
2. **Line 95:** Replace `'YOUR_SERVICE_ID'` with your Service ID from Step 2
3. **Line 95:** Replace `'YOUR_TEMPLATE_ID'` with your Template ID from Step 3

Example:
```javascript
emailjs.init("abc123xyz789");  // Your Public Key

// ...

emailjs.send('service_abc123', 'template_xyz789', templateParams)
```

## Step 6: Test the Form

1. Open your website in a browser
2. Navigate to the contact page
3. Fill out the contact form
4. Submit the form
5. Check your email inbox for the test message

## Troubleshooting

### Form shows "EmailJS не е конфигуриран"
- Make sure you've replaced all three placeholders in `script.js`
- Check that your Public Key, Service ID, and Template ID are correct
- Verify that EmailJS library is loaded (check browser console)

### Emails not being sent
- Check browser console for error messages
- Verify your Email Service is connected and active
- Make sure your email template uses the correct variable names
- Check your EmailJS dashboard for usage limits

### Form validation errors
- Make sure all required fields are filled
- Check that email format is valid (contains @ and .)
- Verify phone number has at least 5 characters

## Support

If you encounter issues:
1. Check the browser console (F12) for error messages
2. Review EmailJS dashboard for service status
3. Contact EmailJS support: [https://www.emailjs.com/support/](https://www.emailjs.com/support/)

## Security Note

The Public Key is safe to expose in client-side code. However, for production use, consider:
- Setting up rate limiting
- Adding CAPTCHA to prevent spam
- Using EmailJS's built-in spam protection features

