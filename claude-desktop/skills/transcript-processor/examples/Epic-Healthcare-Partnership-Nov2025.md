# Epic Healthcare Partnership
**Date:** 2025-11-25
**Category:** SADP / Healthcare
**Attendees:** Katie John, Tim Knox, Brian (healthcare group), Vix, Josh, Shane, Alec, David, others

---

## Overview

Epic Software is in Jamf's top 10 SADP priorities. Epic is the premier electronic medical record (EMR) system in the US (#2 globally). This meeting established strategy for deepening the Epic partnership over 18-24 months.

---

## Relationship Status

### Current State
- **Tier**: "Nursery tier of the orchard" (baby tier)
- **Annual paid membership** for iPad/Mac solution contacts
- **Monthly meetings** with iOS app developers assigned to Jamf
- "We can be partners with them, but they won't be partners with us"
- Epic will not sign NDAs
- Very customer-driven partnership model

### Key Insight
Epic won't look at Jamf twice unless customers are "banging down their door" asking for partnership.

### Potential Leverage
Francisco Partners has deeper ties with Epic - John and Henry asked for lay of the land to feed back to FP.

---

## Four-Pronged Strategy (18-24 months)

1. **Develop more with Epic platform** - Tim Knox is expert here
2. **Customer advocacy** - Get customers approaching Epic for partnership
3. **Build to Epic's standards** - Align with how they build/support
4. **Microsoft healthcare relationships** - Slow build, could help with Epic introductions

---

## Technical Integration Details

### Healthcare Listener (HL7)

**Current state:**
- Agnostic, works with industry standard HL7
- Can only do simple actions: wipe device, change extension attribute
- Missing: Transfer and Admit commands

**Low Hanging Fruit #1: Transfer Command**
- When transfer command comes in → update room field on device
- "Customers have been asking since the beginning"
- Simple endpoint update
- This is how Epic beats Jamf: "Rip out Jamf healthcare listener, use our tool, it does transfer"

**Low Hanging Fruit #2: Admit Command**
- Nurse hands device to patient on arrival
- Accept admit command → update room field
- Enable downstream healthcare listener actions

**Quote from Tim:** "Put me in a room with Alec, we can probably solve this in a couple hours. It's only taken us 8 years to ask for it."

### Patient-Facing vs Clinical-Facing

| Type | Seat Count | Dollar Value |
|------|------------|--------------|
| Patient-facing | Lower | Less direct value |
| Clinical-facing | Higher | More dollars |

**Land and expand strategy**: Win with healthcare listener (patents), then expand to clinical.

### Clinical Apps (Rover, Haiku, Kanto)
- Deploy these apps on mobile devices
- Less complaints about deployment than healthcare listener
- Opportunity: Better integrations into Epic apps

---

## Impossible Dreams

### Epic Compliance Reporting
- Report device compliance against Epic/Rover security standards
- Epic gives discounts if standards met
- **Status**: Unknown if possible, may need one endpoint from Pro
- Could get 90-98% there with existing benchmarks

### Badge Tap Authentication
- Clinicians tap badge → authenticate into Rover
- **Status**: IA Tiger team + Web team actively investigating
- Hardware complexity: iPads need badge scanners (no NFC), breadbox carts
- May be 2027+ project
- "We lose a crap load of business from this - everyone eats our lunch"

**How it would work:**
1. Badge scanner reads badge
2. IDP (Entra/Okta) creates access token
3. Token authenticates into Epic apps
4. Missing piece: Identity automation federating to create auth token

**Vault vs Vaulte confusion:**
- Vault (the case company): Badge tap that writes one value to EA (restructuring)
- Vaulte: Clinical solution meeting Dec 2 about logout

---

## HIPAA Approach

**Critical positioning:**
- "We are NOT HIPAA compliant"
- "We will NEVER be HIPAA compliant"
- "We are compliant by default because we do not retain that data"

**Why:** If Jamf starts touching patient information → BAA requirements, legal exposure

**Quote from Tim:** "I feel very strongly and made sure everybody at Jamf understands this"

---

## Hyperspace (Mac)

- Different from mobile badge tap
- Mac computers on wheels replacing Dell COWs
- Very expensive replacement for same Epic access
- "Shiny new toy but does it really work yet?"
- Badge still used, not phone
- "The juice ain't worth the squeeze" - focus on mobile fleet

---

## Action Items

| Owner | Action |
|-------|--------|
| Josh's team | Build transfer/admit POC |
| Tim + Vix | Business impact documentation |
| Tim + Vix | Bring Travis Cinor to healthcare community call |
| Katie | Work with Travis to get on roadmap |
| Katie | Keep minutes in SADP repository |
| Josh | Create Epic Slack channel |
| Tim | Find badge scanner + cart for IA team testing |
| IA Tiger team | Continue badge tap investigation |

---

## Organizational Notes

- Travis Cinor (Product) is more involved, attended JNUC roundtable
- Product team has built things "nobody asked for" - healthcare team frustrated
- Strategy: Speak with one voice, bring year's asks at beginning of year

---

## People Reference

| Person | Role | Focus |
|--------|------|-------|
| Tim Knox | Senior CE - Industry Solutions | Healthcare expert, 8+ years |
| Katie John | Partner Manager | Epic coordination |
| Brian | Healthcare group | Partner relationship |
| Vix | Healthcare | Customer advocacy |
| Travis Cinor | Product | Healthcare roadmap |
| Alec | Engineering | Technical implementation |
| Larry | ? | Badge scanner contacts |
