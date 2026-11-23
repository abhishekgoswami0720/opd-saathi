# OPD Saathi: Problem Brief (T2P3)

Build for Bharat hackathon · Track 2: Healthcare and Well-being · Patient Navigation for Public Hospitals
Last updated: 23 Nov 2026 (team additions in section 6)

## 1. The problem, in one scene

*The scene below is made up but realistic. The details come from the sources in section 3.*

A son takes an overnight train from a village in Bihar to bring his mother to a big government hospital in Delhi. Registration goes fine: he gets a slip with a token number. **The trouble starts right after that.** He doesn't know which building or floor the department is in, so he asks a guard, then a nurse. At the doctor's room, he can't tell when his number will be called. He steps away for water and the number goes by. Then the doctor orders a blood test, and he starts over. He carries a keypad phone and can't read English signs well. By evening, half the job is done, and they come back tomorrow.

**Problem statement:** In India's big government hospitals, a first-time patient gets a token in minutes but then gets lost. Nobody tells them where to go next or when their turn is coming. So they miss turns and lose whole days.

## 2. Who exactly we build for

**Primary user:** the family member (attendant) who brings a first-time, out-of-state patient to the OPD of a large central government hospital in Delhi (AIIMS, Safdarjung, RML). They usually carry a basic or keypad phone and read little English.

| Role | Who |
|---|---|
| Uses it | The attendant, sometimes the patient |
| Benefits | The patient and front-line staff |
| Approves and pays | The hospital (Medical Superintendent, IT cell) |

**Top difficulties (assumptions to test):**

1. They don't know where the next stop is. In one study, 69.6% of first-time OPD visitors needed a person to guide them ([IJCMPH, 2026](https://www.ijcmph.com/index.php/ijcmph/article/view/15904)).
2. They don't know when their turn will come.
3. They don't know what happens next (reports, pharmacy).

## 3. How big, how often, how costly

| Metric | Figure | Source or calculation |
|---|---|---|
| OPD patients a day, AIIMS Delhi | 14,000–15,000 | [Free Press Journal, 2026](https://www.freepressjournal.in/india/15000-patients-1000-surgeries-5-year-waits-the-complex-world-of-aiims-delhi) |
| OPD registrations a day: Safdarjung, RML, LHMC | 9,110; 6,000; 3,151 | [Lok Sabha answer](https://eparlib.nic.in/bitstream/123456789/669582/1/23510.pdf) (year not shown; may be old) |
| AIIMS patients from outside Delhi | 59% | 1,68,061 ÷ 2,84,468, Jan 2024, via [The Quint](https://www.thequint.com/my-report/photos-surviving-on-langars-living-in-tent-life-of-patients-outside-aiims) |
| First-time visitors who needed a person to guide them | 69.6% (n = 336) | [IJCMPH, 2026](https://www.ijcmph.com/index.php/ijcmph/article/view/15904) |
| OPD patients reachable by phone | 69% | Safdarjung Medicine Screening OPD, 13,161 ÷ 18,959, 2024 ([Mera Aspataal](https://vmmc-sjh.mohfw.gov.in/sites/default/files/2024.pdf)) |
| Keypad-phone users in India | ~250–300 million | [TelecomTalk, 2025](https://telecomtalk.info/?p=1002728) |
| Time per OPD visit | ~2 h for ~3 min with the doctor | Studies cited in [arXiv, 2026](https://arxiv.org/pdf/2604.00215) |
| Registration wait fixed by ABHA Scan & Share | 30–40 min → 5–10 min | [MoHFW, 2024](https://www.mohfw.gov.in/press-info/7908) |
| Cost of one extra day (patient + attendant) | ₹1,420 lost wages | 2 × ₹710/day, Delhi unskilled minimum wage ([Zimyo](https://www.zimyo.com/guides/minimum-wages/delhi/)) |
| Staff time spent giving directions, AIIMS (estimate) | ~104 staff-hours/day | 15,000 × 30% first-time (assumption) × 69.6% × 2 questions (assumption) × 1 min (assumption) ÷ 60 |
| Our SMS cost | ~₹0.90 a visit | 5 SMS × ₹0.18 ([Exotel](https://exotel.com/?p=1809)) |

No savings demonstrated yet.

## 4. Closest alternatives

| Alternative | Does well | Where our user still struggles |
|---|---|---|
| Asking staff, help desks, signage | Free, human, any language | Desks are crowded; nobody can tell you *when* your turn is |
| [AIIMS Disha](https://www.tribuneindia.com/news/delhi/aiims-launches-disha-navigation-app-to-assist-patients-visitors/amp) (Sep 2025) | Beacon-based indoor directions, offline, multilingual voice, kiosks | Smartphone app; launch reports cover finding places, not token status or the next step; one hospital |
| [ABHA Scan & Share](https://www.mohfw.gov.in/press-info/7908) | Fast registration | Stops at the registration slip |

**USP:** For the attendant of a first-time OPD patient at a big government hospital, OPD Saathi gets them to each next stop at the right time. It sends the next room and a "your turn is near" alert by SMS and voice call in their language, on any phone, with no app. So they don't miss turns or lose an extra day.

## 5. Riskiest assumption

That OPD room staff will press "Call next" every time. **Test:** shadow one OPD room for about 3 hours with a paper "NEXT" tick card. If staff tick at least 8 of 10 calls unprompted, the assumption holds.

## 6. Team additions (23 Nov 2026)

| Module | Already exists | Our angle | Hackathon tier |
|---|---|---|---|
| Multilingual voice assistant: booking → appointment tracking | Online OPD booking via [ORS / eHospital](https://vmmc-sjh.mohfw.gov.in/online-registration-ors-opd) (smartphone or web) | Booking by missed call / IVR in local languages on a keypad phone, using the same voice channel as the turn alerts | Build |
| Patient & queue management | Token displays in OPD rooms | One-tap staff screen that moves the journey forward and triggers messages | Build (core) |
| ASHA referral link (team's "centralized data repo") | 10.4 lakh+ ASHAs ([govt factsheet via NewKerala, 2026](https://www.newkerala.com/news/a/over-1040-lakh-ashas-1058-lakh-anganwadi-workers-427.htm)); ABDM consent-based record exchange | ASHA pre-books and refers; we keep journey data only, and clinical records stay with ABHA / ABDM consent | Mockup → Phase 2 |
| Ayushman-card hospitals | [PM-JAY hospital finder](https://www.business-standard.com/health/ayushman-bharat-hospitals-how-to-find-free-treatment-in-your-area-125042300210_1.html) | SMS of nearby empanelled hospitals at the moment of referral, with the Ayushman desk's location | Mockup → Phase 2 |

**Caveats:**
- PM-JAY generally does not cover outpatient consultations ([Bajaj Finserv summary](https://www.bajajfinserv.in/ayushman-card-hospital-list)), so the Ayushman feature is for admission and surgery referrals, not OPD visits.
- DPDP Rules were notified in Nov 2025, with consent-manager registration in phase II, due Nov 2026 ([Chambers, 2026](https://chambers.com/practice-guides/guides/digital-healthcare-2026/india/trends-and-developments)). OPD Saathi stores no medical records.
