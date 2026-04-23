# Donor Thank-You & Tax Acknowledgment — Aloha Critter Club

IRS-compliant donor acknowledgment email. Finalized 2026-04-22 with EIN from IRS Letter 947 (2021-05-08).

Use this as a **Gmail template** for manual send after each Venmo donation (recommended path — see "Sending logic" below).

---

## Email template

**Subject:**

```
Thank you for supporting Aloha Critter Club — your tax receipt inside
```

**Body:**

```
Aloha [Donor First Name],

Thank you for your gift to Aloha Critter Club. Because of you, 70 kids
across 5 Hawaii Island schools get to spend their after-school hours
learning to care for animals — and each other. Your generosity keeps
that going.

Please keep this email for your tax records:

  Organization:              Aloha Critter Club
  Tax-exempt status:         501(c)(3) public charity, IRC 170(b)(1)(A)(vi)
  EIN:                       86-1496578
  Effective date of exemption: January 13, 2021
  Donor:                     [Donor Name]
  Donation amount:           $[Amount]
  Donation date:             [Date]
  Payment method:            Venmo (@alohacritterclub)

No goods or services were provided in exchange for this contribution.
Your donation is tax-deductible to the extent allowed by U.S. law.

This email serves as your official written acknowledgment from Aloha
Critter Club under IRS guidelines for charitable contributions
(IRS Publication 1771).

If you have questions — or want to hear more about what the kids are up
to this semester — just reply. I read every message.

With gratitude,

Kristin Spear
Founder & Board President
Aloha Critter Club
P.O. Box 1281, Kea'au, HI 96749
alohacritterclub@gmail.com | alohacritterclub.org
Instagram: @alohacritterclub
```

### Fields to personalize before each send
- `[Donor First Name]` (greeting)
- `[Donor Name]` (receipt line)
- `[Amount]` (receipt line)
- `[Date]` (receipt line — date of the Venmo transaction)

---

## Sending logic

### Recommended: Gmail template (manual, 2 min per gift)

1. Gmail → Settings (gear) → **See all settings** → **Advanced** tab
2. Enable **Templates** → Save Changes
3. Compose a new email → paste body above → click ⋮ → **Templates → Save draft as template → Save as new template** (name it "ACC donor receipt")
4. When a Venmo donation comes in, open a fresh email to the donor → Templates → "ACC donor receipt" → personalize the four fields → send

At FY2025 donation volume (3 gifts/year), total time: ~6 minutes annually. Do not over-engineer.

### Future automation (only if volume exceeds ~20 gifts/year)

Candidate path: Zapier → trigger on Venmo email notification in Gmail → parse amount/name → send from Gmail template. Requires ~1–2 hours setup and ongoing reliability monitoring. Skip until needed.

Alternative: add a parallel Donorbox or Givebutter widget for recurring gifts (Venmo Charity doesn't support monthly recurring). Those platforms send their own branded auto-receipts. Cost: ~1.5–2.9% per gift. Revisit if/when recurring gifts become a real ask.

---

## IRS compliance notes

**Why the specific language matters:**

- **"No goods or services were provided"** — required by IRS for any single gift of $250+. Including it on every receipt is safe and recommended.
- **EIN prominence** — donors' accountants will ask; including it upfront prevents a follow-up.
- **"Publication 1771" reference** — signals procedural correctness to donors who know what to look for.

**Edge cases not covered by this template** (handle individually, consult IRS Pub 1771):

- Non-cash gifts (goods, services, equipment donations)
- Quid-pro-quo donations (e.g., fundraiser ticket that includes a meal) — requires stating the fair-market value of the benefit
- Gifts over $5,000 (may require donor's Form 8283 signature from ACC)
- In-kind stock/securities donations

**Not legal or tax advice.** When in doubt, reference IRS Publication 1771 or consult a nonprofit accountant.

---

## On the new Netlify site

This template stays email-only — do not publish on the public site. However, the Donate page (if created) should include a short line like:

> All donations receive an automatic Venmo receipt and a personal tax acknowledgment from our Founder within 7 days. For your records, our EIN is 86-1496578.

That sets donor expectations without exposing the full template.
