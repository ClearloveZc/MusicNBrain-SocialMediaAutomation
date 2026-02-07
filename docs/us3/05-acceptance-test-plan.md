# US3 Acceptance Test Plan

Owner: Zhenchao  
Version: v1.0  
Date: 2026-02-07

## 1. Test Scope

Validate US3 MVP against acceptance criteria AC-1 to AC-4.

## 2. Test Data

Use one reference campaign:

1. Title: Spring Student Recital
2. Date/Time: 2026-03-15 19:00
3. Venue: Zoom + studio hall
4. CTA: registration link

## 3. Test Cases

| TC ID | AC | Scenario | Steps | Expected Result |
| --- | --- | --- | --- | --- |
| TC-01 | AC-1 | Generate flyer and captions | Create campaign and click `Generate Content` | Flyer output and 3 platform captions are created and editable. |
| TC-02 | AC-2 | Auto timeline scheduling | Open scheduling page after content generation | Default jobs generated for T-7d, T-3d, T-1d. |
| TC-03 | AC-2 | Manual schedule override | Modify one scheduled datetime and save | Queue reflects updated datetime. |
| TC-04 | AC-3 | Multi-platform publish execution | Trigger due jobs for TikTok, XHS, IG | Three jobs run with independent states and logs. |
| TC-05 | AC-4 | Platform format adaptation | Inspect final payload before publish | Payload matches platform template mapping rules. |
| TC-06 | AC-4 | Length overflow fallback | Submit intentionally long caption | System truncates/warns per validation rule and logs adjustment. |
| TC-07 | Ops | Retry failed publish | Force one adapter failure and click retry | Job state changes `failed -> queued -> running` and logs retry count. |

## 4. Pass Criteria

US3 MVP is accepted when:

1. TC-01 to TC-05 pass fully.
2. At least one negative-path case (TC-06 or TC-07) passes.
3. No silent failures (every failed job has non-empty `error_code` and `error_message`).

## 5. Demo Script (5-7 Minutes)

1. Create campaign from sample concert data.
2. Generate content and quickly edit one caption.
3. Confirm schedule.
4. Show three platform jobs and execute one publish cycle.
5. Show one simulated failure and retry.
6. End with success/failure summary panel.

## 6. Evidence to Attach

1. Screenshot of generated content editor.
2. Screenshot of schedule table.
3. Screenshot of publish status with three platform rows.
4. Screenshot of one failure log and successful retry.
