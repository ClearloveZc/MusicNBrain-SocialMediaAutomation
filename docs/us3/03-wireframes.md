# US3 Low-Fidelity Wireframes

Owner: Zhenchao  
Version: v1.0  
Date: 2026-02-07

These wireframes define the minimum teacher-facing flow for US3 MVP.

## Screen A - Campaign Setup

```text
+------------------------------------------------------------------+
| Create Promotion Campaign                                        |
+------------------------------------------------------------------+
| Concert Title          [____________________________________]    |
| Concert Date/Time      [___________]  Venue/Link [___________]   |
| Student Highlights     [____________________________________]    |
| CTA Link               [____________________________________]    |
|                                                                  |
| [Generate Content]                                               |
+------------------------------------------------------------------+
```

Primary action: `Generate Content`  
Validation: title + datetime + venue/link are required.

## Screen B - Content Review and Edit

```text
+------------------------------------------------------------------+
| Generated Content                                                 |
+------------------------------------------------------------------+
| Flyer Headline                                                   |
| [Editable text area..........................................]    |
|                                                                  |
| Caption - TikTok                                                 |
| [Editable text area..........................................]    |
| Caption - Xiaohongshu                                            |
| [Editable text area..........................................]    |
| Caption - Instagram                                              |
| [Editable text area..........................................]    |
|                                                                  |
| [Regenerate]   [Save Draft]   [Next: Schedule]                  |
+------------------------------------------------------------------+
```

Primary action: `Next: Schedule`  
Safety: manual edit checkpoint before queueing any job.

## Screen C - Schedule Planner

```text
+------------------------------------------------------------------+
| Schedule Posts                                                    |
+------------------------------------------------------------------+
| Suggested Plan (Auto):                                           |
|  - T-7 days  [datetime]  Platforms [TT] [XHS] [IG]              |
|  - T-3 days  [datetime]  Platforms [TT] [XHS] [IG]              |
|  - T-1 day   [datetime]  Platforms [TT] [XHS] [IG]              |
|                                                                  |
| Teacher can edit each datetime and platform selection.           |
|                                                                  |
| [Back]   [Save Draft]   [Confirm and Queue Jobs]                |
+------------------------------------------------------------------+
```

Primary action: `Confirm and Queue Jobs`

## Screen D - Publish Status

```text
+------------------------------------------------------------------+
| Campaign Publish Status                                           |
+------------------------------------------------------------------+
| Job ID     Platform   Time                 State      Action     |
| job-101    TikTok     2026-02-10 19:00     success    View       |
| job-102    XHS        2026-02-10 19:00     failed     Retry      |
| job-103    IG         2026-02-10 19:00     queued     --         |
|                                                                  |
| Error Detail (selected failed job):                              |
| [token expired - reconnect account and retry]                    |
|                                                                  |
| [Retry Failed Jobs]                                              |
+------------------------------------------------------------------+
```

Primary action: `Retry Failed Jobs`

## Interaction Notes

1. Campaign stays in `draft` until schedule is confirmed.
2. All generated content remains editable at any point before queueing.
3. Retry action must keep the same content payload unless user explicitly updates it.
