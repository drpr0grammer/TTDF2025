# EmailJS Setup Guide - TTDF 2025 Contact Form

## 🚀 **Quick Setup (5 Minutes)**

### **Step 1: Create EmailJS Account**
1. Go to [EmailJS.com](https://www.emailjs.com/)
2. Sign up for a free account
3. Verify your email address

### **Step 2: Add Email Service**
1. In EmailJS dashboard, go to "Email Services"
2. Click "Add New Service"
3. Choose "Gmail" or "Outlook"
4. Connect your email account (info@ttdf2025.co.tz)
5. Note down the **Service ID** (e.g., `service_abc123`)

### **Step 3: Create Email Template**
1. Go to "Email Templates"
2. Click "Create New Template"
3. Use this template:

```html
Subject: TTDF 2025 Contact Form: {{subject}}

Dear TTDF 2025 Team,

You have received a new contact form submission:

**Contact Information:**
- Name: {{from_name}}
- Email: {{from_email}}
- Phone: {{phone}}

**Inquiry Details:**
- Subject: {{subject}}
- Message: {{message}}
- Newsletter Subscription: {{newsletter}}

**Response Required:**
Please respond to {{from_email}} within 24-48 hours.

Best regards,
TTDF 2025 Website

---
This message was sent from the Tanzania Traditional Dances Festival 2025 contact form.
```

4. Note down the **Template ID** (e.g., `template_xyz789`)

### **Step 4: Get Public Key**
1. Go to "Account" → "API Keys"
2. Copy your **Public Key** (e.g., `user_def456`)

### **Step 5: Update Contact Form**
Replace the placeholders in `contact.html`:

```javascript
// Replace YOUR_PUBLIC_KEY
emailjs.init("user_def456");

// Replace YOUR_SERVICE_ID and YOUR_TEMPLATE_ID
emailjs.send('service_abc123', 'template_xyz789', templateParams)
```

---

## 📧 **Email Destinations**

### **Primary Recipients:**
- **Main Contact:** info@ttdf2025.co.tz
- **Backup Contact:** admin@csrg.co.tz
- **Technical Support:** tech@ttdf2025.co.tz

### **Auto-Response Setup:**
Create a second template for auto-responses:

```html
Subject: Thank you for contacting TTDF 2025

Dear {{from_name}},

Thank you for contacting the Tanzania Traditional Dances Festival 2025!

We have received your inquiry about: {{subject}}

**What happens next:**
- Our team will review your message within 24 hours
- You will receive a detailed response within 48 hours
- For urgent matters, please call: +255 22 123 4567

**Festival Details:**
- Event: Tanzania Traditional Dances Festival 2025
- Dates: 04th - 05th September 2025
- Venue: Jakaya Kikwete Convention Centre, Dodoma
- Organizer: Centre for Sports Research and Governance Limited (CSRG)

**Stay Connected:**
- Website: www.ttdf2025.co.tz
- Phone: +255 22 123 4567
- Mobile: +255 712 345 678

Best regards,
TTDF 2025 Team
Centre for Sports Research and Governance Limited

---
This is an automated response. Please do not reply to this email.
```

---

## 🔧 **Advanced Configuration**

### **Multiple Recipients:**
To send to multiple email addresses, modify the template:

```html
To: info@ttdf2025.co.tz, admin@csrg.co.tz, tech@ttdf2025.co.tz
```

### **Subject Line Customization:**
```html
Subject: TTDF 2025 Contact: {{subject}} - From {{from_name}}
```

### **Priority Filtering:**
Add priority tags based on subject:

```javascript
// Add priority to templateParams
const priority = data.subject === 'urgent' ? 'HIGH' : 'NORMAL';
templateParams.priority = priority;
```

---

## 📱 **Mobile Optimization**

### **SMS Notifications:**
Integrate with Twilio for SMS alerts:

```javascript
// Add to success callback
if (data.subject === 'urgent') {
    // Send SMS to +255 712 345 678
    console.log('Sending SMS notification for urgent inquiry');
}
```

---

## 🛡️ **Security & Spam Protection**

### **reCAPTCHA Integration:**
1. Add reCAPTCHA to the form
2. Verify before sending email
3. Block suspicious submissions

### **Rate Limiting:**
```javascript
// Prevent multiple submissions
let isSubmitting = false;

if (isSubmitting) {
    alert('Please wait, your message is being sent...');
    return;
}
isSubmitting = true;
```

---

## 📊 **Testing & Monitoring**

### **Test the Setup:**
1. Fill out the contact form
2. Submit with test data
3. Check email delivery
4. Verify auto-response

### **Monitor Performance:**
- EmailJS dashboard shows delivery status
- Check spam folders
- Monitor response times

---

## 🎯 **Recommended EmailJS Plan**

### **Free Plan (100 emails/month):**
- Perfect for testing and small events
- Basic templates
- Gmail/Outlook integration

### **Paid Plans:**
- **Starter ($15/month):** 1,000 emails
- **Business ($25/month):** 10,000 emails
- **Enterprise ($50/month):** 50,000 emails

For TTDF 2025, the **Starter plan** should be sufficient.

---

## 🚨 **Emergency Setup**

If EmailJS setup fails, use this backup method:

### **Formspree (Alternative):**
```html
<form action="https://formspree.io/f/info@ttdf2025.co.tz" method="POST">
    <!-- Same form fields -->
</form>
```

### **Direct Email Link:**
```html
<a href="mailto:info@ttdf2025.co.tz?subject=TTDF 2025 Inquiry&body=Hello, I would like to inquire about...">
    Send Email Directly
</a>
```

---

## 📞 **Support Contacts**

### **EmailJS Support:**
- Email: support@emailjs.com
- Documentation: docs.emailjs.com

### **TTDF 2025 Technical Team:**
- Email: tech@ttdf2025.co.tz
- Phone: +255 712 345 678

---

*This setup ensures all contact form submissions reach the TTDF 2025 team reliably and professionally.*
