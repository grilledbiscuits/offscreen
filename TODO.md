# TODO

## Screenshot import: today's screen time

- [ ] Add screenshot import for iPhone Screen Time, Samsung Digital Wellbeing, and Google Pixel Digital Wellbeing. Extract the displayed total for today so far; this is a planned feature, not implemented functionality.

### Capture instructions

| Platform | Required screen | Extract |
| --- | --- | --- |
| iPhone | Settings → Screen Time → See All App & Website Activity → Day → today; select this iPhone under Devices | Overall daily duration, not Daily Average or an all-devices total |
| Samsung | Settings → Digital Wellbeing and parental controls → today's overview or screen-time detail | Overall daily duration, not a goal, remaining allowance, or individual app duration |
| Google Pixel | Settings → Digital Wellbeing and parental controls → main dashboard | Today's overall duration in the usage chart |

### Proposed extraction method

Use OCR retaining text positions, followed by platform-specific rules based on headings and layout. Avoid fixed pixel coordinates. Read the displayed overall total directly; never sum visible apps or estimate chart bars. Normalize explicit duration units to minutes (for example, `3 h 42 min` becomes `222`) and retain the source text for review.

Validate the dashboard type, daily period, date, device scope, readability, and plausibility against elapsed time. Reject Battery screens, weekly totals, averages, and ambiguous values. Use Africa/Johannesburg for the competition date; require clarification if the device's reporting day differs. If only “Today” is visible, require user confirmation that the screenshot was captured today. Upload time and image metadata do not prove freshness.

Show the extracted duration and highlight its source in the screenshot before confirmation. Store the date, total minutes, platform, upload timestamp, and whether date/device scope were user-confirmed. Missing or unreadable data must never become zero. Repeated uploads replace that day's observation rather than adding durations; flag decreases for review.

### Competition and privacy

Label entries “Today so far” with their submission time. Current-day rankings are provisional because users submit at different times. Upload time is not verified capture time. Share only the agreed aggregate figures with friends; decide image retention and deletion before implementation.

Screenshots cannot reliably prove ownership, freshness, or authenticity. Treat results as screenshot-reported usage, not verified usage. Native App Store acceptance remains unconfirmed; screenshot import is not an established policy workaround.

### Acceptance checks and open decision

Before release, test real screenshots from all three platforms across light/dark themes, display sizes, and supported language/version combinations. Include weekly views, daily averages, all-device iPhone reports, cropped/blurred images, missing dates, duplicate uploads, and midnight boundaries. Confirm that unsupported or uncertain inputs never silently produce a leaderboard score.

Open decision: require a retake for unclear screenshots, or permit a separately labelled manual entry. No choice has been approved yet.

### References

- [Apple Screen Time guide](https://support.apple.com/en-gb/guide/iphone/iphbfa595995/ios)
- [Samsung Digital Wellbeing guide](https://www.samsung.com/us/support/answer/ANS10001357/)
- [Google Digital Wellbeing guide](https://support.google.com/android/answer/9346420?hl=en)

Design recorded 2026-10-31. No extraction implementation or device validation performed.
