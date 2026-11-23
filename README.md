# OPD Saathi

**Next-step and turn alerts for OPD patients in India's big public hospitals, by SMS and voice call on any phone. No app needed.**

Built for the *Build for Bharat* hackathon, Track 2 (Healthcare), Problem 3: *Patient Navigation for Public Hospitals*.

> Status: **planning**. No code yet. See [`docs/problem-brief.md`](docs/problem-brief.md) for the full brief.

## The problem

In big government hospitals, a first-time patient gets a token in minutes, then gets lost. Nobody tells them where to go next or when their turn is coming. They miss turns and lose whole days.

- AIIMS Delhi sees about 14,000–15,000 OPD patients a day, and most come from outside Delhi.
- In one study, 69.6% of first-time OPD visitors needed a person to show them the way.
- Many patients carry a keypad phone, so smartphone apps can't reach them.

## Who it's for

The family member (attendant) who brings a first-time, out-of-state patient to a large government hospital OPD. They usually carry a basic or keypad phone and don't read English well.

## What it does (planned MVP)

| # | Feature | What it does |
|---|---------|--------------|
| 1 | Journey start at registration | Staff enter phone, language and department. The patient gets an SMS with building, floor, room and a color line to follow. |
| 2 | One-tap staff screen | "Call next token" and "Add next stop" (lab, X-ray, pharmacy) for each OPD room. |
| 3 | Turn-near alert | SMS plus an automatic voice call in Hindi or Bhojpuri when 3 tokens are left, and again at every new stop. |

**Out of scope:** indoor maps and turn-by-turn directions. AIIMS Disha already does that on smartphones.

## How it differs from AIIMS Disha

Disha answers *"where is the lab?"* on a smartphone. OPD Saathi answers *"what do I do next, and when?"* on any phone.

## Roadmap

- [ ] Data model: patient journey, stops, room queues
- [ ] Registration screen (staff)
- [ ] Room screen: call next / add next stop (staff)
- [ ] SMS sending (Hindi first)
- [ ] Voice call alert, with a simulated fallback for the demo
- [ ] Demo seed data for one real hospital layout
- [ ] Demo video

## Riskiest assumption

That OPD room staff will press "Call next" every time. We'll test this at a real OPD before building too far.
