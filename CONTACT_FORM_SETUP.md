# Contact Form Setup Guide - Tanzania Traditional Dances Festival 2025

## 📧 **Where Contact Form Messages Go**

Currently, the contact form shows a demo message. Here are the **real implementation options** for where messages can actually be sent:

---

## 🚀 **Option 1: Email Service (Recommended)**

### **A. EmailJS (Free & Easy)**
```javascript
// Add this to your HTML head
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>

// Replace the form submission with:
emailjs.init("YOUR_USER_ID");
emailjs.send("YOUR_SERVICE_ID", "YOUR_TEMPLATE_ID", {
    from_name: data.firstName + " " + data.lastName,
    from_email: data.email,
    subject: data.subject,
    message: data.message,
    phone: data.phone
});
```

**Destinations:**
- 📧 **Primary Email:** info@ttdf2025.co.tz
- 📧 **Backup Email:** admin@csrg.co.tz
- 📧 **Technical Support:** tech@ttdf2025.co.tz

---

## 🌐 **Option 2: Backend Server**

### **A. PHP Backend**
Create `contact-handler.php`:
```php
<?php
if ($_POST) {
    $to = "info@ttdf2025.co.tz";
    $subject = "TTDF 2025 Contact Form: " . $_POST['subject'];
    $message = "Name: " . $_POST['firstName'] . " " . $_POST['lastName'] . "\n";
    $message .= "Email: " . $_POST['email'] . "\n";
    $message .= "Phone: " . $_POST['phone'] . "\n";
    $message .= "Message: " . $_POST['message'];
    
    mail($to, $subject, $message);
    echo "success";
}
?>
```

### **B. Node.js Backend**
```javascript
const express = require('express');
const nodemailer = require('nodemailer');

app.post('/contact', async (req, res) => {
    const transporter = nodemailer.createTransporter({
        service: 'gmail',
        auth: {
            user: 'info@ttdf2025.co.tz',
            pass: 'your-app-password'
        }
    });
    
    await transporter.sendMail({
        from: req.body.email,
        to: 'info@ttdf2025.co.tz',
        subject: `TTDF 2025 Contact: ${req.body.subject}`,
        text: req.body.message
    });
    
    res.json({ success: true });
});
```

---

## 📱 **Option 3: Form Services**

### **A. Formspree (Free)**
```html
<form action="https://formspree.io/f/info@ttdf2025.co.tz" method="POST">
    <!-- Your form fields -->
</form>
```

### **B. Netlify Forms**
```html
<form name="contact" netlify>
    <!-- Your form fields -->
</form>
```

### **C. Google Forms**
- Create a Google Form
- Embed it in your website
- Responses go to Google Sheets

---

## 💬 **Option 4: CRM Integration**

### **A. HubSpot**
```javascript
// Add HubSpot tracking code
// Form submissions automatically create contacts
```

### **B. Salesforce**
```javascript
// Use Salesforce Web-to-Lead
// Form submissions create leads in Salesforce
```

### **C. Mailchimp**
```javascript
// Add subscribers to Mailchimp list
// Send automated follow-up emails
```

---

## 📊 **Option 5: Database Storage**

### **A. MongoDB**
```javascript
// Store messages in MongoDB
const message = new Message({
    firstName: data.firstName,
    lastName: data.lastName,
    email: data.email,
    subject: data.subject,
    message: data.message,
    timestamp: new Date()
});
await message.save();
```

### **B. MySQL/PostgreSQL**
```sql
INSERT INTO contact_messages 
(first_name, last_name, email, subject, message, created_at)
VALUES (?, ?, ?, ?, ?, NOW());
```

---

## 🔧 **Implementation Steps**

### **Step 1: Choose Your Method**
1. **For Quick Setup:** Use EmailJS or Formspree
2. **For Full Control:** Set up backend server
3. **For Business:** Use CRM integration

### **Step 2: Update Contact Information**
Replace placeholder emails with real ones:
- **Primary:** info@ttdf2025.co.tz
- **Technical:** tech@ttdf2025.co.tz
- **General:** admin@csrg.co.tz

### **Step 3: Add Spam Protection**
```javascript
// Add reCAPTCHA
<script src="https://www.google.com/recaptcha/api.js"></script>
<div class="g-recaptcha" data-sitekey="YOUR_SITE_KEY"></div>
```

### **Step 4: Add Auto-Response**
```javascript
// Send confirmation email to user
const userEmail = {
    to: data.email,
    subject: "Thank you for contacting TTDF 2025",
    message: "We received your message and will respond within 24-48 hours."
};
```

---

## 📋 **Current Contact Information**

### **CSRG Office**
- **Address:** Centre for Sports Research and Governance Limited, Dar es Salaam, Tanzania
- **Email:** info@ttdf2025.co.tz
- **Phone:** +255 22 123 4567
- **Mobile:** +255 712 345 678

### **Festival Venue**
- **Venue:** Jakaya Kikwete Convention Centre
- **Location:** Dodoma, Tanzania
- **Dates:** 04th - 05th September 2025

---

## 🎯 **Recommended Setup**

For the Tanzania Traditional Dances Festival 2025, I recommend:

1. **Primary:** EmailJS for immediate setup
2. **Backup:** Formspree for reliability
3. **Storage:** Simple database for message history
4. **Notifications:** SMS alerts for urgent inquiries

This ensures messages reach the right people quickly and reliably!

---

## 📞 **Emergency Contact**

For urgent festival-related matters:
- **Hotline:** +255 712 345 678
- **WhatsApp:** +255 712 345 678
- **Emergency Email:** urgent@ttdf2025.co.tz

---

*This guide ensures all contact form submissions reach the appropriate CSRG team members for the Tanzania Traditional Dances Festival 2025.*
