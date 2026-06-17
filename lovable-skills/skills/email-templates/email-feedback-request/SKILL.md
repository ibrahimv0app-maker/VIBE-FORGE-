---
name: email-feedback-request
description: Use when sending the Feedback request. Always uses responsive, accessible HTML email with: short survey, incentive. Plain-text fallback included.
---

# Email Template: Feedback request

Feedback request — short survey, incentive.

## Email Specs
- From: branded name + email
- Subject: 50-60 chars, action-oriented
- Preheader: 80-100 chars, complements subject
- Body: 200-500 words, scannable
- CTA: one primary, max one secondary
- Footer: unsubscribe, address, social

## Subject Line Patterns
- Direct: "Verify your email"
- Action: "Reset your password"
- Question: "Ready to upgrade?"
- Number: "3 new comments on your post"
- Personalization: "{first_name}, your trial ends in 2 days"
- Urgency: "Last day to claim your discount"

## HTML Structure
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{subject}</title>
</head>
<body style="margin:0;padding:0;background:#f4f4f5;">
  <!-- Preheader (hidden) -->
  <div style="display:none;max-height:0;overflow:hidden;">
    {preheader}
  </div>

  <!-- Container -->
  <table role="presentation" width="100%" cellpadding="0" cellspacing="0">
    <tr>
      <td align="center" style="padding:24px;">
        <table role="presentation" width="600" cellpadding="0" cellspacing="0"
               style="background:#ffffff;border-radius:8px;overflow:hidden;">

          <!-- Header / Logo -->
          <tr>
            <td style="padding:24px 24px 0;text-align:center;">
              <img src="logo.png" alt="Brand" width="120" style="display:inline-block;">
            </td>
          </tr>

          <!-- Body -->
          <tr>
            <td style="padding:32px 24px;font-family:Inter,Arial,sans-serif;font-size:16px;line-height:1.6;color:#0a0a0a;">
              <h1 style="margin:0 0 16px;font-size:24px;font-weight:600;">
                {headline}
              </h1>
              <p style="margin:0 0 16px;">
                {body paragraph 1}
              </p>
              <p style="margin:0 0 24px;">
                {body paragraph 2}
              </p>

              <!-- CTA Button -->
              <table role="presentation" width="100%" cellpadding="0" cellspacing="0">
                <tr>
                  <td align="center" style="padding:8px 0;">
                    <a href="{cta_url}" style="display:inline-block;padding:12px 24px;background:#3b82f6;color:#ffffff;text-decoration:none;border-radius:6px;font-weight:500;">
                      {cta_text}
                    </a>
                  </td>
                </tr>
              </table>
            </td>
          </tr>

          <!-- Footer -->
          <tr>
            <td style="padding:24px;border-top:1px solid #e4e4e7;font-family:Inter,Arial,sans-serif;font-size:14px;color:#71717a;text-align:center;">
              <p style="margin:0 0 8px;">
                <a href="{unsubscribe_url}" style="color:#71717a;">Unsubscribe</a>
                ·
                <a href="{preferences_url}" style="color:#71717a;">Email preferences</a>
              </p>
              <p style="margin:0;">
                {company_name} · {company_address}
              </p>
            </td>
          </tr>

        </table>
      </td>
    </tr>
  </table>
</body>
</html>
```

## Plain-Text Version
Always include a plain-text alternative. Most email clients render it if HTML fails.

## Responsive Design
- Single column on mobile (max-width: 600px)
- Font size ≥ 16px on mobile
- Buttons ≥ 44px tall (touch target)
- Padding ≥ 16px on mobile

## Accessibility
- `role="presentation"` on layout tables
- Alt text on images
- Sufficient color contrast (4.5:1)
- Don't rely on color alone
- Link text descriptive (not "click here")

## Testing
- Litmus / Email on Acid for client compatibility
- Test in Gmail, Outlook, Apple Mail, Yahoo
- Dark mode test
- Plain text fallback test
- Image-off test (does it still make sense?)

## Forbidden Patterns
- All-image emails (image blocking breaks them)
- Forms in email (don't work in most clients)
- JavaScript (doesn't run in email)
- External CSS (use inline styles)
- Web fonts (limited support, use system fonts)

## Output Format
1. Subject line + preheader
2. HTML email
3. Plain-text version
4. Sending code (e.g., Resend, SendGrid)

