# Homepage Copy — Aloha Critter Club

Paste-ready copy for the homepage donation block. Finalized 2026-04-22 based on FY2025 financial data (see `CLAUDE.md` for the underlying numbers).

For the Astro/Netlify rebuild: this block lives above the Venmo QR on the homepage. Implement as a self-contained component (e.g. `src/components/DonationAsk.astro`) so it can be reused later on a dedicated Donate page.

---

## Framed donation ask — Option A (chosen)

**Placement:** Homepage, above the Venmo QR code.

**Headline (H2):**

> Fuel a Hawaii kid's love for animals.

**Body paragraph:**

> In 2025, Aloha Critter Club served 70 students across 5 Hawaii Island schools — teaching them to care for animals and each other. It costs us about **$86 a year** to serve one student, and every dollar goes into their hands.

**Giving tiers (bulleted list):**

- **$25** — a student's club supplies for a semester
- **$75** — one student's field trip to Magical Creatures
- **$250** — a full semester of supplies for an entire school
- **$500** — a teacher stipend for a full club cycle

**Call-to-action line (below tiers, above QR):**

> Scan to give via Venmo. We're a 501(c)(3); your donation is tax-deductible and you'll receive an automatic receipt.

**QR image alt text:**

> Venmo QR code to donate to Aloha Critter Club (handle: @alohacritterclub)

---

## Implementation notes for Astro

```astro
---
// src/components/DonationAsk.astro
const tiers = [
  { amount: '$25',  impact: "a student's club supplies for a semester" },
  { amount: '$75',  impact: "one student's field trip to Magical Creatures" },
  { amount: '$250', impact: 'a full semester of supplies for an entire school' },
  { amount: '$500', impact: 'a teacher stipend for a full club cycle' },
];
---
<section class="donation-ask">
  <h2>Fuel a Hawaii kid's love for animals.</h2>
  <p>In 2025, Aloha Critter Club served 70 students across 5 Hawaii Island
     schools — teaching them to care for animals and each other. It costs us
     about <strong>$86 a year</strong> to serve one student, and every dollar
     goes into their hands.</p>
  <ul>
    {tiers.map(t => (
      <li><strong>{t.amount}</strong> — {t.impact}</li>
    ))}
  </ul>
  <p>Scan to give via Venmo. We're a 501(c)(3); your donation is
     tax-deductible and you'll receive an automatic receipt.</p>
  <img src="/images/venmo-qr.png"
       alt="Venmo QR code to donate to Aloha Critter Club (handle: @alohacritterclub)" />
</section>
```

---

## Desktop-clickable Donate button (header)

Still pending copy decision. Candidates (short — header buttons should be 1–2 words):

- **Donate** (classic, clear)
- **Give via Venmo** (sets expectation about payment method)
- **Support Our Kids** (mission-forward)

Recommendation: **Donate** for the button label, linking to `https://venmo.com/u/alohacritterclub` (or the Venmo Charity Profile URL). When clicked on mobile this deep-links to the Venmo app; on desktop it opens the web profile. This solves the "no desktop-clickable donate" gap from the original problem statement.

---

## Rejected alternatives (kept for reference)

### Option B — Short & punchy

> **70 kids. 5 Hawaii schools. One after-school club teaching them to care for animals — and each other.**
>
> For **$86** you fund a full year of club for one student. Scan to donate via Venmo — 501(c)(3), automatic tax receipt.

### Option C — Story-forward

> **"I didn't know I could love an animal this much."**
> That's what a third grader at Pahoa Elementary told us after her first semester in Aloha Critter Club. In 2025 we reached 70 kids across 5 Hawaii schools for about $86 each. Your gift keeps the clubs running — and opens the door for the next kid.
>
> **$25** covers a student's supplies for a semester. **$500** stipends a teacher for a full club cycle. Scan to give via Venmo — 501(c)(3), tax-deductible.
>
> *(Swap the quote for a real one — with permission — before publishing.)*

Option C becomes viable if/when a real student quote is available with photo/permission. Consider revisiting for a dedicated Donate or Impact page on the new site.
