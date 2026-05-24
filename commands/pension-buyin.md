---
name: pension-buyin
description: >
  Guide someone through offsetting a Swiss severance payment above the AVIG Art. 11a RAV
  threshold by making a voluntary Pensionskasse buy-in (Einkauf). Use this skill whenever
  the user mentions: severance above the RAV cap, RAV delay due to severance, Art. 11a
  threshold, pension buy-in to protect RAV benefits, Einkauf Pensionskasse for
  unemployment, severance too high for RAV, AVIG-Praxis ALE B122, or any question about
  offsetting a high Swiss severance. Also trigger if the user says their severance is
  above CHF 148,200 or asks how to avoid a RAV waiting period.
---

# RAV Severance Offset via Pension Buy-In (Einkauf)

This skill guides through the process of making a voluntary Pensionskasse buy-in to bring
a Swiss severance payment below the AVIG Art. 11a threshold, eliminating or reducing the
RAV benefit delay.

At each step where an email needs to be sent, **proactively offer to draft it** — ask the
user for the missing details (name, employer, pension fund contact, dates), draft the
email in formal German, show an English translation for review, and wait for approval
before sending.

---

## ⚠️ Not legal, tax, or financial advice — verify current figures

This guide summarises Swiss rules (AVIG Art. 11a, AVIG-Praxis ALE B122) to help the user
act — it is **not** legal, tax, or financial advice. The thresholds and rates below were
correct under the AVIG-Praxis ALE in effect at writing (2026) and **change over time**:
the Art. 11a cap is indexed to the maximum insured salary, and Quellensteuer rates vary by
canton and year.

Before the user acts on any number:
- **Confirm the current Art. 11a threshold and B122 maximum** against the live AVIG-Praxis
  ALE or with the user's Arbeitslosenkasse — don't present the figures here as
  guaranteed-current.
- **Frame buy-in and withdrawal-timing as options with tradeoffs, not guaranteed wins.**
  The value depends on the user's marginal tax rate, relocation plans, and the 3-year
  lock-in. For large amounts, recommend they confirm with their pension fund and a tax
  adviser.

---

## Bilingual display

This plugin's users aren't all native German speakers, but every job-room.ch label is in German (or French/Italian in non-German cantons). Whenever you surface a German term to the user — form labels, status badges, document types, button names — include an English translation in parentheses on first mention in the current reply (e.g. `Arbeitsbemühungen (work efforts)`, `Übermittlung (submission)`). After the first mention in a reply, the German alone is fine.

This rule applies to user-facing chat only. Do **not** translate text typed into job-room.ch form fields (those need German), the body of German emails drafted for the user (translation happens as a separate preview step), or legal article references like `Art. 11a AVIG`.

---


## Background: The Legal Basis

**AVIG Art. 11a** sets a threshold of **CHF 148,200** (12 × the maximum insured monthly
salary of CHF 12,350). If a severance exceeds this, the excess delays the start of RAV
daily allowances (Taggelder) day-for-day.

**AVIG-Praxis ALE Section B122** allows voluntary pension contributions (Einkauf) made
for the purpose of closing pension gaps to be deducted from the severance before
calculating the threshold — up to a maximum of **CHF 90,720**.

**Result:** A buy-in of at least the excess amount brings the effective severance down to
CHF 148,200, eliminating the delay entirely.

---

## Step 1 — Calculate the Excess

```
Excess = Gross severance − CHF 148,200
```

This is the **minimum buy-in** needed to eliminate the RAV delay.

Estimated RAV delay without action (days) ≈ Excess ÷ CHF 411 (daily insured earnings =
CHF 12,350 ÷ 30). At ~CHF 280/day in Taggelder, each day of delay costs roughly CHF 280.

---

## Step 2 — Request an Einkaufsberechnung from the Pension Fund

The user must contact their Pensionskasse and request an **Einkaufsberechnung** (buy-in
capacity calculation). This document confirms the maximum amount they are allowed to
contribute and includes all payment details for the transfer.

**Important cap for people who relocated to Switzerland from abroad:** If the employee has
been in Switzerland fewer than 5 years, the annual buy-in is capped at **20% of the
insured savings salary** — not the full theoretical gap. The pension fund confirms the
exact limit in the Einkaufsberechnung.

### Draft the email for this step

Offer to draft the email to the pension fund. Ask the user for:
- Their full name
- Their employer name and last day of employment
- The pension fund name and contact (if known; otherwise suggest they check their pension
  fund certificate or ask HR)

Then draft a formal German email. Template:

```
Sehr geehrte Damen und Herren,

ich bin Mitarbeiter/in von [Arbeitgeber] und werde per [Datum] aus dem Unternehmen
ausscheiden. Im Zusammenhang mit meiner Abfindung und den Bestimmungen von Art. 11a AVIG
möchte ich prüfen, ob und in welchem Umfang ein freiwilliger Einkauf in die
Pensionskasse möglich ist.

Ich bitte Sie um eine aktuelle Einkaufsberechnung sowie die entsprechenden
Zahlungsangaben.

Mit freundlichen Grüssen,
[Name]
```

Always show an English translation alongside the German draft. Wait for the user's
approval before sending.

---

## Step 3 — Decide the Buy-In Amount

Once the Einkaufsberechnung arrives, walk through the options with the user. Contributing
**more than the minimum** (up to the full maximum allowed) is often attractive because
every franc contributed:
- Is deductible from Swiss taxable income in the contribution year (when income is
  typically high due to severance)
- At Swiss marginal rates of ~30–35%, each CHF 10,000 contributed saves ~CHF 3,000–3,500
  in income tax (the rate depends on the user's actual taxable income and commune — treat
  this as a rough estimate, not a quote)

But it is **not automatic**: the extra amount is locked under the 3-year rule (see below)
and only pays off if the user's marginal rate and timeline make the deduction worth more
than the lost flexibility. Present it as a tradeoff to weigh with the user — and, for large
amounts, a tax adviser — not a default.

---

## Step 4 — Make the Transfer

Transfer from a **personal bank account in the user's name only** before the last day of
employment. The **Einkaufsberechnung document contains all payment details**: beneficiary
name, IBAN, bank, and the personal payment reference number. The reference is unique to
the individual — it must be included exactly as shown.

**Deadline:** The transfer must be credited to the pension fund before the last day of
employment (separation date, not garden leave start date if these differ).

---

## Step 5 — Obtain the Einzahlungsbestätigung

Once the transfer is credited, the pension fund automatically sends an
**Einzahlungsbestätigung** (payment confirmation) showing the amount contributed. No
special request is needed — this is a standard document issued automatically.

---

## Step 6 — Confirm with the Arbeitslosenkasse

Before or shortly after submitting the ALE-Antrag, the user should check with their
**Arbeitslosenkasse (ALK)** that the Einzahlungsbestätigung is sufficient. The standard
question to ask (by phone or their contact form) is:

> "Welches Dokument benötigen Sie von der Pensionskasse, damit der Einkaufsbetrag bei der
> Berechnung der Wartezeit nach Art. 11a AVIG berücksichtigt werden kann?"

In practice, the Einzahlungsbestätigung is all that is needed — but confirming in advance
avoids surprises. Common ALKs in Switzerland: Unia ALK, SYNA, KGAST, cantonal public
fund (KAST).

### Draft the email or contact form message for this step

If the user wants to contact the ALK in writing, offer to draft a short German message.
Ask for:
- Their name and postcode
- Their ALK (if known)
- Their last employer and separation date
- The approximate severance amount

Template:

```
Sehr geehrte Damen und Herren,

ich bin seit [Datum] bei Ihrer Kasse angemeldet. Meine Abfindung von [Arbeitgeber]
beläuft sich auf CHF [Betrag] und übersteigt den Grenzwert gemäss Art. 11a AVIG.

Ich beabsichtige, vor dem [Datum] einen freiwilligen Einkauf in meine Pensionskasse
([Name der PK]) vorzunehmen, um die Abfindung gemäss AVIG-Praxis ALE B122 unter den
Grenzwert zu senken.

Welches genaue Dokument benötigen Sie von der Pensionskasse, damit der Einkaufsbetrag
bei der Berechnung der Wartezeit nach Art. 11a AVIG berücksichtigt werden kann?

Mit freundlichen Grüssen,
[Name]
```

---

## The 3-Year Lock-In Rule

Any buy-in amount **cannot be withdrawn as a lump sum within 3 years** of the
contribution date. If withdrawn early:
- Switzerland **retroactively reverses the tax deduction** — the contributed amount is
  added back to taxable income in the year of contribution, cancelling the tax saving
- The reversal applies only to the tax deduction, not to the capital itself

**This affects everyone planning to leave Switzerland within 3 years.** Even with
reversal, early withdrawal can still be the right move depending on the destination
country's tax rates — see the section below.

---

## Tax Scenarios at Withdrawal

When the user eventually leaves the pension fund (leaves employer, leaves Switzerland, or
retires), the withdrawal is subject to Swiss **Quellensteuer** (withholding tax). The rate
depends on the canton of the pension foundation's domicile — rates vary from ~4.8% to
~8%+ depending on the canton. Inner Swiss cantons such as Schwyz and Appenzell
Innerrhoden typically have the lowest rates; check current rates at the time of transfer.

**Tip:** When leaving the employer during unemployment, you can transfer vested benefits
to a Freizügigkeitsstiftung (vested benefits foundation) in a low-tax canton to lock in a
lower Quellensteuer rate before leaving Switzerland. Compare current rates before
choosing.

| Scenario | Swiss tax | Destination country tax | Notes |
|---|---|---|---|
| Withdraw while still Swiss resident | ~5–8% (varies by canton) | None | Simple but foregoes timing flexibility |
| Withdraw before establishing residency abroad | ~4.8–5% (low-tax canton) | None | Good if no favourable foreign tax regime |
| Withdraw in a country with a tax treaty | ~4.8–5% | Varies | Check treaty terms — may further reduce Swiss tax |
| Withdraw as regular tax resident abroad | ~4.8–5% Swiss | Full foreign income tax | Avoid if possible |

**If leaving Switzerland within 3 years of the buy-in:** compare the cost of the
deduction reversal against the expected foreign tax rate. In most cases, withdrawing
before establishing foreign residency (in the transition window) is cheaper than paying
full foreign income tax on the balance later.

---

## Summary Checklist

- [ ] Calculate excess above CHF 148,200
- [ ] Draft and send email to pension fund requesting Einkaufsberechnung
- [ ] Receive Einkaufsberechnung — confirm buy-in capacity and payment details
- [ ] Decide buy-in amount (recommend full maximum)
- [ ] Transfer from personal account before last day of employment
- [ ] Receive Einzahlungsbestätigung automatically from pension fund
- [ ] Contact ALK to confirm they accept Einzahlungsbestätigung (optional but recommended)
- [ ] Forward Einzahlungsbestätigung to ALK
- [ ] Plan withdrawal timing based on destination country tax situation

---

## Key Facts at a Glance

| Item | Value |
|---|---|
| AVIG Art. 11a threshold | CHF 148,200 |
| Maximum buy-in deductible (AVIG-Praxis ALE B122) | CHF 90,720 |
| 20% cap (relocated from abroad, <5 years in CH) | 20% of insured savings salary |
| 3-year lock-in | Yes — tax deduction reversed if withdrawn earlier |
| Lowest Quellensteuer cantons | Schwyz, Appenzell Innerrhoden (~4.8–5%) |
| Document ALK needs | Einzahlungsbestätigung from pension fund |
