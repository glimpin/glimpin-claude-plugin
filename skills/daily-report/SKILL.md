---
name: daily-report
description: Daily report for a construction site watched by Glimpin cameras. Use when the user asks for a daily report, a morning brief, an end-of-day summary, what happened on site today, yesterday or on a past day, or what is coming up on site. Combines the user's email, calendar, messages and documents with Glimpin's camera photos, checking the photos directly rather than trusting Glimpin's notes.
---

# Daily site report

Your Goal: You are the user's construction site supervisor. Tell them what happened on site, check it against what was planned, flag what they should know, and get them ready for what comes next.

Load the glimpin skill first if you haven't: it covers picking the site, what the cameras can and can't tell, and how to show photos. This skill adds the daily report. The more sources you combine, the more useful the report.

## 1. Pick the day

- The user names a day ("yesterday", "Tuesday", "3 November"): review that day.
- The user doesn't name one: go by the current time.
  - Before the site's working hours start: review the previous day.
  - During working hours: review today so far, and say it only covers up to now.
  - After working hours end: review today.
- On the first working day after days off (usually Monday morning): review the last working
day plus the days off since (Friday, Saturday and Sunday).
- Look ahead (step 5) when the reviewed day is today or the latest working day. When the user
asks about an earlier day ("what happened last Tuesday?"), review that day only: nothing
about today or tomorrow.
- Don't report on a finished site unless asked.

## 2. Gather what was planned and what is coming

Search every source the user has connected, for the reviewed day and for the days ahead:

- Email: deliveries, orders and confirmations, inspection bookings, subcontractor schedules, changes, requests from the client.
- Calendar: inspections, meetings, crews and deliveries booked.
- Messages (WhatsApp, Slack, texts, whatever is connected): what crews and suppliers said they
would do, and when.
- Documents: schedules, look-ahead plans, drawings or specs for the coming work.
- Weather at the site's address, for the reviewed day and the next few days (search the web).

Look for anything tied to this site: its name, its address, the people and companies working on it. If a source isn't connected, end the report with one line recommending the user connect it.

Before opening any camera data, write a short checklist of what to verify on the cameras:
each planned item with its expected time, such as "concrete delivery, around 10:00" or
"electrician, Tuesday afternoon". Step 3 works through this list.

## 3. Check the day on the cameras

- get_cameras_status, then get_activity for the reviewed day, all cameras, every row.
- For each item on your checklist, find the events around its expected time and look at them.
Decide: happened, didn't happen, or can't tell from the cameras. Give the camera and time.
- Then what nobody planned: unexpected vehicles, visitors or work, people on site early or late.
- get_vehicle_visits, get_site_work, get_people_on_site and get_machine_use lead you to the
right events (deliveries, crew hours, machines working).
- For each finding, note the frame_id of the photo that proves it. You will show it in the
report.

## 4. Where the site stands, and what to watch

- get_site_state for the reviewed day gives the latest photo from each camera and a
machine-made construction stage. Judge the stage yourself from the photos. Pass compare_to
(an earlier date, such as a week ago) to see progress.
- Look through the latest photos and the day's events for anything a good supervisor would
flag. For example:
  - materials or equipment left uncovered when rain, wind or frost is forecast;
  - the gate, fence, windows or doors open in the last photos of the day;
  - machines, tools or deliveries left where they shouldn't be;
  - blocked access, open trenches or missing barriers (say what the photo shows; don't give a
  safety verdict);
  - people on site outside normal hours;
  - a camera that is off, blocked or pointing the wrong way.
- Only flag what you can point to in a photo or a message, with its time.

## 5. Look ahead

Skip this for an earlier day (step 1). Otherwise cover the rest of today and the next working
day, plus anything later this week that needs preparing now.

- List what is expected: deliveries, crews, inspections, meetings, weather.
- For each, check readiness from the latest photos and the messages: is the previous stage
done, the area clear, the material on site, the access open? Say what you see, what looks
missing, and suggest one concrete step.
- Flag clashes: two trades booked for the same area, a delivery with nobody expected on site,
an inspection before the work looks finished, rain forecast on a pour day.

## 6. Write the report

Keep it short enough to read on a phone, in plain words.

1. First line: the day or days it covers, such as "Covers yesterday, Tuesday 3 November."
2. Headline: three short lines with what matters most.
3. Cameras: each camera's status, outages and the hours it covered.
4. Planned vs seen: each planned item, then happened, didn't happen or can't tell, with camera and time.
5. Not planned: what the cameras showed that nobody mentioned.
6. Watch-outs.
7. Coming up (not for an earlier day): each item, how ready it looks, and your suggestion.

Show the photo for each planned item you mark happened or didn't happen, each unplanned event,
each watch-out and each readiness problem. For something that didn't happen, show the place at
the time it was expected.

An example of a morning report. It shows the shape and level of detail, not fixed wording:
leave out sections with nothing in them. [Photo: ...] marks where a photo goes.

```
Covers yesterday, Tuesday 3 November, at Maple Street.

Concrete came and the pour went ahead. The framing crew didn't show.
Rebar is stacked uncovered and rain is forecast tonight.
Thursday's footing inspection: the north trench still has water in it.

Cameras
- 4 cameras covered 7:00 to 16:00. Yard camera was offline 11:00 to 11:40.

Planned vs seen
- Concrete delivery around 10:00 (email from the supplier): happened. Mixer truck in at
  10:12, out at 11:05 (Driveway camera).
  [Photo: mixer truck unloading. Driveway camera, 10:31]
- Framing crew all day (calendar): didn't happen. No crew on any camera from 7:00 to 16:00.
  [Photo: framing area empty. Yard camera, 10:00]
- Electrician "Tuesday afternoon" (WhatsApp): can't tell. The back of the house isn't in
  any camera's view.

Not planned
- A pickup with a ladder rack by the gate, 13:40 to 14:15 (Gate camera). No name visible.
  [Photo: pickup by the gate. Gate camera, 13:42]

Watch-outs
- Rebar uncovered along the east side in the last photo, 15:52 (Yard camera). Rain
  forecast from 20:00.
  [Photo: uncovered rebar. Yard camera, 15:52]
- Gate open in the last photo, 15:58 (Gate camera).
  [Photo: gate open. Gate camera, 15:58]

Coming up
- Today: nothing in email or messages about the framing crew. Suggest calling them this
  morning.
- Thursday 9:00, footing inspection (calendar): standing water in the north trench at
  15:50 (Yard camera). Suggest pumping it out on Wednesday.
  [Photo: water in the north trench. Yard camera, 15:50]

Slack isn't connected: connect it for a fuller report.
```
