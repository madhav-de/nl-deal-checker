---
name: nl-deal-checker
description: Check whether a Dutch online deal is real before buying - the actual shop price vs comparison sites, marketplace sellers, contract vs outright cost, open-box grades, inflated "was" prices and cashback rules. Use when the user weighs a purchase at a Dutch shop or provider (Coolblue, bol, MediaMarkt, Amazon.nl, Odido, KPN, Vodafone, etc.) or asks "is this a good deal?".
license: MIT
metadata:
  version: "1.0.0"
  author: madhav-de
---

# nl-deal-checker

Verify a Dutch deal before the user buys. The goal is one honest number: what this will really cost, from whom, with what risk.

Most bad deals in the Netherlands are not scams. They are real listings that look cheaper than they are: a comparison-site price no shop actually charges, a marketplace seller behind a big shop's name, a phone discount that only exists with a 2-year plan, or an open-box unit with a scratched screen.

## When to use

- The user shares a price, link or screenshot and asks whether to buy.
- The user compares shops, or a subscription offer against buying outright.
- The user is looking at open-box / second-chance (tweedekans) / refurbished items.
- The user mentions cashback, Black Friday, or a "was" price.

## Workflow

Run every check that applies. Skip the ones that don't, and say which you skipped.

### 1. Find the real shop price

- A price on a comparison site (Tweakers Pricewatch, Kieskeurig, Knibble, Beslist, PriceSpy, TVOutlet's comparison pages) is a pointer, not an offer. Open the shop's own product page and confirm the price there.
- Match the exact model code. Variants (for example OLED65B6E vs OLED65B68LA, or EU vs foreign-market versions) can differ in price, panel, features and warranty.
- Note the date you saw each price. Black Friday prices move daily.
- Say clearly when a price is from Belgium or Germany. It is useful as a benchmark (and for asking a Dutch shop to match), not as an NL price.

### 2. Check who actually sells it

- bol: read "Verkoop door". bol itself or a partner seller? Partner sellers have their own return rules and delivery times.
- Amazon.nl: "Verzonden door / Verkocht door" - Amazon or a third party?
- MediaMarkt: some listings are sold and shipped by third parties ("Verkoop en verzending door ...").
- For unknown shops: check for Thuiswinkel Waarborg membership, a KvK number and recent reviews.

### 3. Work out the real cost of contract deals

Phone-plus-plan offers show a discounted device price that only applies with a subscription. Always compute:

```
contract total = upfront + (device credit per month x months) + (plan per month x months)
outright total = phone price at a shop + (SIM-only per month x months)
```

- Compare over the same period (usually 24 months).
- Break-even: device discount / months = how much more per month the bundled plan may cost before buying outright wins.
- Existing customers: renewal ("verlengen") offers can differ from the new-customer shop price. Also suggest asking for a loyalty discount on SIM-only.
- Device credit (toestelkrediet) above the legal threshold is registered credit (BKR). Mention it if the user may apply for a mortgage soon.
- Note the lock-in: a renewal restarts a fixed term.

### 4. Decode open-box and second-chance listings

- Read the condition text in full ("Staat van dit product"), not only the grade label. A label can refer to the packaging while the text describes the device.
- Hard no for screens: "krassen" (scratches), "deuk" (dent), "barst" (crack), "pixel" defects, or "beschadigd scherm" on a TV, monitor, laptop or phone. Screen damage is permanent and visible.
- Compare the open-box price against the current new price at the same shop. Savings under about 10% rarely justify a used unit.
- Check what the channel gives you: warranty length, return window, and whether accessories (remote, stand, cables) are included.
- Open-box purchases usually do not qualify for manufacturer cashback or bundled promotions. Include that in the comparison.
- For OLED TVs, ask the user to test for burn-in and dead pixels within the return window (full-screen solid colours).

### 5. Check "was" prices and price history

- A struck-through price is often a list price (adviesprijs) that nobody charged. Do not report "X% off" based on it.
- Ask the user to check the price history on Tweakers Pricewatch (or PriceSpy) for the exact model, or check it yourself if you can load it.
- Under Dutch/EU rules a shop's announced discount must refer to its lowest price in the previous 30 days. A shop showing "Laagste prijs in 30 dagen" or "Meest toegepaste prijs" gives you a better anchor than the struck-through price.

### 6. Check cashback and promo rules

- Which exact models qualify? Cashback often covers only some sizes or series (for example a 65" model but not the 55").
- Deadlines: purchase window, registration deadline, proof-of-purchase deadline.
- Exclusions: open-box, refurbished, marketplace sellers, and sometimes certain shops.
- Report the effective price after cashback, and the price you pay upfront.

### 7. Know the user's rights

- Online purchases in the EU have a 14-day withdrawal right (herroepingsrecht) for most products; some shops give 30 days. Check who pays return shipping.
- The statutory warranty (conformiteit) means a product must work as long as can reasonably be expected, often longer than the shop's stated 2 years for expensive items.

## Output format

Lead with the verdict. Keep it scannable.

```
Verdict: BUY / WAIT / SKIP - one line why.

Real cost: €X at <shop> (seller: <who>), seen <date>.

| Check | Result |
|---|---|
| Shop price confirmed | ... |
| Seller | ... |
| Contract vs outright | ... (if relevant) |
| Condition (open box) | ... (if relevant) |
| Price history / "was" price | ... |
| Cashback | ... |

Better option: <cheaper or safer alternative, if any>.
Next step: <one concrete action, e.g. "check 'Verkoop door' on the bol page">.
```

## Rules

- Never present a comparison-site price as the price the user will pay.
- Never call a contract deal cheaper without doing the total-cost math.
- Say what you could not verify (blocked pages, missing price history) instead of guessing.
- Give prices in EUR including VAT, with the shop name and the date seen.
- Do not give financial or legal advice beyond these checks. Point to the shop's terms or ConsuWijzer (consuwijzer.nl) for disputes.

## Dutch glossary

| Dutch | Meaning |
|---|---|
| Adviesprijs | Manufacturer's list price |
| Tweedekans | Second-chance / open-box item |
| Onbeschadigd | Undamaged |
| Lichte gebruikssporen | Light signs of use |
| Zichtbaar beschadigd | Visibly damaged |
| Staat van dit product | Condition of this product |
| Verkoop door | Sold by |
| Toestelkorting | Device discount (with a subscription) |
| Toestelkrediet | Device credit (paying the phone in monthly instalments) |
| Verlengen | Renew a contract |
| Herroepingsrecht | Right of withdrawal |
| Uitverkocht / Niet leverbaar | Sold out / not available |
