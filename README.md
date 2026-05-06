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

### Starter kit form
- **Get free AI starter kit** collects lead details and reveals the Google Doc guide link.
- If Google Form settings are configured in `src/data/site.ts`, the form submits to Google Forms in the background.
- If Google Form settings are blank, the site falls back to the older prefilled email draft behavior.

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

## Google Form lead capture

The starter kit form can save leads to a Google Form without opening an email app.

1. Create a Google Form with these fields:
   - Full name
   - Email
   - Business type
   - Source
2. Link the Google Form to a Google Sheet.
3. Open the form preview, inspect the form action URL, and copy the `formResponse` URL.
4. Find each field's `entry.xxxxx` ID.
5. Paste those values into `src/data/site.ts`:

```ts
googleForm: {
  actionUrl: 'https://docs.google.com/forms/d/e/YOUR_FORM_ID/formResponse',
  fields: {
    fullName: 'entry.111111111',
    email: 'entry.222222222',
    businessType: 'entry.333333333',
    source: 'entry.444444444',
  },
},
```

Once those values are filled in, submissions are saved in Google Forms/Sheets in the background and the AI Starter Kit link is shown on the page.

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
The Free AI Starter Kit form submits to Google Forms when the Google Form action URL and field IDs are configured in `src/data/site.ts`. If those values are blank, it opens a prefilled email draft to `newcollarlabs@gmail.com` as a fallback.

## Online booking
Create an online booking page, then paste the public booking URL into `src/data/site.ts`:

```ts
bookingPageUrl: 'YOUR_PUBLIC_BOOKING_PAGE_URL'
```
