---
name: progress-report
description: Weekly construction progress report for the lender, or for the owner or investors, made as a PDF with photos from Glimpin's cameras. Use when the user asks for a progress report, a weekly update, a report for the bank or lender, photos for a draw request, or an update for the owner. Shows where the build stands and what was done this week with before and after photos, checking the photos directly rather than trusting Glimpin's notes. Problems are left out of the report and listed separately for the user.
---

# Weekly progress report

Your Goal: You are the builder's site supervisor writing the weekly progress report for the lender. Show where the build stands and what got done this week, prove each point with a photo, and hand the builder a PDF they can read and send.

Load the glimpin skill first if you haven't: it covers picking the site, what the cameras can and can't tell, and how to show photos. This skill adds the lender report.

The report goes outside the company, so:
- It shows progress only. Problems (no-shows, delays, damage, disputes) stay out of it; you
list them for the builder in a note beside the PDF (step 6).
- It never claims more than the photos show. Leaving a problem out is the builder's choice;
stating progress that isn't there is never OK.

## 1. Pick the week

- The user names a period ("this week", "since the last report", "26 to 30 October"): use it.
- Otherwise: the 7 days up to today. Before the site's working hours start: the 7 days up to
yesterday.
- If an earlier progress report is in the user's email or documents, read the latest one. Use
the same stages, so the lender can set the two side by side, and start the week the day after
it.

## 2. Gather the paperwork

Search every source the user has connected:

- The loan's papers: the draw schedule or budget breakdown, the construction schedule, the
latest draw request, and any form the lender uses.
- Email, messages, calendar: work done this week, materials delivered, inspections passed,
and what is planned for next week.
- Who the report is from and for: the builder's company (from the user's email signature) and
the lender's name. If you can't find them, leave a blank to fill in.

If the lender has its own form (a draw request, an inspection form), never fill it in or
change it: it is the builder's signed statement to the lender. Use its line names for your
stages, so the lender can match each line to its photos, and tell the builder in the note
that this report goes with their form.

Before opening any camera data, write two short lists: the stages of the build (the line names
from the lender's form or draw schedule, or else the usual ones: site work, foundation,
framing, roof, windows and doors, exterior, plumbing, electrical and HVAC, insulation and
drywall, finishes), and the work the papers say was done this week.

## 3. Check on the cameras

- get_camera_status for the week.
- get_full_size_photos with each camera_id at a time near the end of the last day of the week,
and at the same time on the day before the week started. Each pair comes from the same camera,
so from the same spot: your before and after photos. Judge the stage yourself from them.
- Find this week's work: get_day_summary for each day (vehicles and machines on site,
materials delivered) is a lead, and browse_events covers the rest.
- For each stage decide: done, in progress, not started, or not visible on the cameras (most
inside work). For each piece of work this week: seen or not seen.
- For each finding, note the photo_id of the photo that proves it.

## 4. Decide what goes in

In the report:

- each stage and its status, with a photo for done and in progress;
- this week's work the photos show, with a before and after pair where the change is visible;
- materials delivered and stored on site, with a photo;
- inspections passed, only from the user's own email or papers, saying so ("framing
inspection passed Thursday, per the inspector's email");
- next week's plan, from the schedule and messages.

In the note to the builder, not the report:

- problems: crews that didn't come, delays, weather stoppages, damage, theft, disputes, mess,
anything unsafe;
- anything the builder's papers say is done that the photos don't show, such as a percentage
in the draw request ahead of what the cameras see;
- cameras that were off long enough to weaken the report.

Never estimate a percentage from photos. Use the user's own figure only where the photos
support it.

Pick photos of the building, not of people: avoid faces and number plates. Leave out photos
that show a problem.

## 5. Make the PDF

Make a PDF with the photos inside (use your PDF skill if you have one). Name it after the site
and the last day, such as "oak-lane-progress-30-oct.pdf".

1. Header: "Weekly progress report", the site's name and address, the week, who it is from
and for, the date.
2. Summary: three short lines: the stage now, the main progress this week, what's next.
3. Where the build stands: each stage and its status.
4. This week: each piece of work, with the photo or the before and after pair that proves it.
5. Next week.
6. About the photos: which cameras, what they see and don't see (usually only the outside),
and the line "Photos from the site's cameras, collected by Glimpin."

Keep it plain and factual: no sales words ("great progress"), no verdict on schedule or
budget, nothing about how you used the tools.

Photos in the PDF:

- Download each photo and put it in the PDF. No photos just to fill a page.
- Put before and after side by side: same camera, each captioned with its day and time.
- If you can't make files, give the same report in your reply, in the same order, and tell
the user how to get the PDF next time: in Claude, Settings → Capabilities, turn on Code
execution and file creation.
- If you can't download photos, tell the user before making the PDF: a lender report without
photos is weak. Give them the fix from the glimpin skill, and make it without photos only if
they ask.

## 6. Hand it over

Give the PDF, then a short note for the builder only:

- Ask them to read it before they send it. Never send it yourself.
- Left out, for them to decide: each problem, with its camera, time and photo.
- Not in the report: each claim in their papers that the photos don't support, and why.
- If the lender has its own form: that they fill it in themselves and attach this report.
- One line per source that isn't connected, recommending they connect it.
- Offer to draft the email to the lender with the PDF attached.

An example. It shows the shape and level of detail, not fixed wording. [Photo: ...] marks a
photo, [Before | After: ...] a side by side pair, and [brackets] a name you'd fill in.

The PDF:

```
WEEKLY PROGRESS REPORT
Oak Lane, 14 Oak Lane, Springfield
Monday 26 to Friday 30 October
From [builder's company] to [lender], 30 October

Summary
Framing is in progress: the walls of both floors are up.
This week: second-floor walls framed and roof trusses delivered.
Next week: roof trusses set, then roof sheathing.

Where the build stands
- Site work and foundation: done.
- Framing: in progress. Walls of both floors up; roof framing not started.
  [Photo: house framed to the second floor. Front camera, Fri 30, 15:50]
- Roof, windows and doors, exterior: not started.
- Plumbing, electrical, HVAC, insulation: inside the house, not visible on the cameras.

This week
- Second-floor walls framed, Monday to Wednesday.
  [Before | After: front of the house. Front camera, Fri 23, 15:50 | Fri 30, 15:50]
- Roof trusses delivered Thursday and stacked in the yard.
  [Photo: trusses unloaded in the yard. Yard camera, Thu 29, 10:20]

Next week
- Set the roof trusses (crane booked Tuesday) and start roof sheathing.

About the photos
Two cameras, Front and Yard, see the outside of the house. Work inside is not covered.
Photos from the site's cameras, collected by Glimpin.
```

The note beside it:

```
Here's the report: oak-lane-progress-30-oct.pdf. Read it before you send it.

Left out, for you to decide:
- Rain on Tuesday: no crew after 10:00 (Front camera).
  [Photo: empty site in the rain. Front camera, Tue 27, 11:00]

Not in the report:
- Your draw request puts framing at 90%. The photos show the roof framing not started, so
  the report gives no percentage.

Slack isn't connected: connect it for a fuller report.

Want me to draft the email to the lender with the PDF attached?
```

## Rules

- Every statement in the report is shown in a photo, or comes from the user's own papers and
says so.
- The report never claims more than the photos show: no estimated percentages, no verdict on
schedule or budget.
- Problems go in the note to the builder, never in the report.
- Never fill in or change the lender's own form.
