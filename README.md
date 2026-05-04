# New Collar Labs Website

Clean Astro landing page for New Collar Labs.

## Local run

```bash
npm install
npm run dev
```

Open:

```bash
http://localhost:4321
```

## Current CTA flow

### Header
- **Book a free consultation** opens the dedicated booking section.
- After the online booking page URL is added, it opens the online booking page in a new tab.

### Hero form
- **Get free AI starter kit** collects lead details, reveals the Google Doc guide link, and opens a prefilled email draft to `newcollarlabs@gmail.com`.

> Important: Static websites cannot silently send email without a backend or email service. This version intentionally avoids Google Apps Script and uses a `mailto:` email draft instead. The visitor still needs to click Send in their email app.

### Offerings CTA
- **Book a free consultation** opens the online booking experience.
- **Get free AI starter kit** jumps to the Get Started form.

## Add the online booking page link

1. Create an online booking page for **Free 15-Min AI Consultation**.
2. Copy the public booking page URL.
3. Open `src/data/site.ts`.
4. Paste the URL here:

```ts
bookingPageUrl: 'https://calendar.app.google/1GdpHgKmZozjCx6K8',
```

Until that URL is added, the booking CTA scrolls to the booking section and shows a reminder to connect the booking link.

## Free guide link

The guide link is configured in `src/data/site.ts`:

```ts
googleDriveGuideUrl: 'https://docs.google.com/document/d/1ZE2CeFuwQJhMFjzLtgqnWqMSsnJ1wEuCpd2j31GE-L4/edit?usp=drive_link',
```

## Email subject format

The form opens a prefilled email draft with this subject format:

```text
New Collar Labs Website Inquiry - Customer Name
```

The email body includes:
- Customer name
- Email
- Business type
- Phone number
- CTA source
- Notes / what they need help with
- Guide link shared, when applicable

## Latest page flow
- Fixed desktop header with two CTAs: Book a free consult and Free AI starter kit.
- Full-width hero brief.
- Combined Co-Founder + Free Consultation section.
- Offerings + Free AI Starter Kit form section.
- Workflow section with both booking and starter kit CTAs.
- Sticky back-to-top arrow.

## Form behavior
The Free AI Starter Kit form opens a prefilled email draft to `newcollarlabs@gmail.com` and reveals the Google Doc starter kit link. This avoids Google Apps Script for the current static-site version.

## Online booking
Create an online booking page, then paste the public booking URL into `src/data/site.ts`:

```ts
bookingPageUrl: 'YOUR_PUBLIC_BOOKING_PAGE_URL'
```
