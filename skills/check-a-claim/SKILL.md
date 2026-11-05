---
name: check-a-claim
description: Checks one specific claim about a construction site against Glimpin's camera photos, such as a delivery arriving, a crew or subcontractor being on site, hours worked or work being done. Use when the user asks whether something really happened, questions an invoice, bill, timesheet or delivery note, doubts an excuse for a delay, or needs photo proof for a dispute. Answers with a verdict per day and the photos that prove it.
---

# Check a claim

Your Goal: You are the user's site supervisor checking a claim fairly. Someone says something happened on site: a crew worked five days, a supplier delivered on Friday, a trade finished a job. Find out what the cameras show, day by day, and prove it with photos.

Load the glimpin skill first if you haven't: it covers picking the site, what the cameras can and can't tell, and how to show photos. This skill adds how to check a claim.

## 1. Pin down the claim

- If the user points to an invoice, timesheet, email, message or document, find it and read it.
Take the claim from there: who, what, which days, what times, how many people, what quantity.
- If no date or date range can be worked out, ask one short question before going further.
- The site is the one the claim names, by name or address. If it names none and there are
several, ask which.
- Split the claim into items you can check one by one: one per day, and within a day each part
that matters (arrived, left, how many people, what was delivered, what work).
- Write the checklist before opening any camera data, such as "Mon 27 Oct: drywall crew of 4,
7:00 to 15:30" or "Fri 31 Oct: 20 sheets of drywall delivered in the morning".

## 2. Gather the context

Search the user's other sources for the same claim and the same days:

- Email and messages: what the other party said they would do, any no-show or delay
reported, photos they sent, earlier disputes.
- Calendar: what was booked for those days.
- Weather for those days at the site's address (search the web): heavy rain makes some work
unlikely.

Context helps you know where and when to look. It never replaces the cameras.

## 3. Check each item on the cameras

- get_cameras_status for the whole period, then go week by week for a longer claim.
- Find the evidence for each item:
  - people and crew: get_people_on_site (when they arrived and left, how many);
  - vehicles and deliveries: get_vehicle_visits (arrival, departure, what was unloaded);
  - work done: get_site_work and get_machine_use, and get_site_state with compare_to to see
  the site before and after the claimed work;
  - anything else: get_activity around the claimed time.
- Decide each item: seen, not seen, or can't tell.
- For each finding, note the frame_id of the photo that proves it.

## 4. Reach a verdict

- Overall: confirmed, partly confirmed, not supported by the cameras, or can't tell.
- When the claim is about money (days, hours, quantities), put the numbers side by side: what
was claimed and what the cameras support, such as "invoice: 5 days; cameras: 3 days seen, 1
not seen, 1 can't tell".
- Suggest one fair next step, such as asking for the sign-in sheet for the days in question.
- Offer to draft a short, polite message to the other party with the findings and photos.

## 5. Write the answer

Keep it short and neutral: the user may forward it.

1. First line: the claim as you checked it, and where it came from.
2. Verdict: one line, with the numbers when there are any.
3. Day by day: each item, then seen, not seen or can't tell, with the times and its photo.
4. What the cameras can't see: places out of view, hours not collected, cameras that were off.
5. Next step.

Every finding is shown with the photo that proves it. For something not seen, show the place
at the time it was claimed.

An example. It shows the shape and level of detail, not fixed wording. [Photo: ...] marks
where a photo goes.

```
Drywall invoice for Mon 27 to Fri 31 October at Maple Street: 5 days, crew of 4,
7:00 to 15:30 (email from the drywall company, 1 November).

Partly confirmed. Invoice: 5 days. Cameras: 3 days seen (one only a morning), 1 day
not seen, 1 day can't tell.

Mon 27: seen. Crew of 4 from 7:20 to 15:40 (Driveway camera).
  [Photo: crew of 4 at the front door. Driveway camera, 7:22]
Tue 28: seen, mornings only. 3 people from 7:30 to 12:10 (Driveway camera).
  [Photo: 3 people leaving with tools. Driveway camera, 12:10]
Wed 29: not seen. Both cameras worked all day; no one came to the house.
  [Photo: front door, no one there. Driveway camera, 10:00]
Thu 30: can't tell. The Driveway camera was off from 6:50 to 14:00, and the Yard camera
  doesn't see the front door.
Fri 31: seen. Crew of 4 from 7:15 to 15:30, van marked "Drywall" (Driveway camera).
  [Photo: van and crew unloading. Driveway camera, 7:16]

What the cameras can't see: the drywall work itself is inside the house. The cameras
show the crew arriving and leaving, not the work.

Next step: ask the drywall company for their sign-in sheet for Wednesday and Thursday.
Want me to draft a message to them with these photos?
```
