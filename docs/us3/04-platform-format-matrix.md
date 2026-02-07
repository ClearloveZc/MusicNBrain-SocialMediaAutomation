# US3 Platform Format Matrix

Owner: Zhenchao  
Version: v1.0  
Date: 2026-02-07

This matrix defines MVP formatting behavior before each publish adapter call.

## 1. Channel Rules

| Platform | Media Focus | Caption Style | Hashtag Strategy | CTA Placement | Notes |
| --- | --- | --- | --- | --- | --- |
| TikTok | Short vertical video, optional cover image | Short hook + one value statement + CTA | 3-5 tags, trend-aware | End of caption | Reuse existing uploader baseline and add template layer. |
| Xiaohongshu | Lifestyle note style, image or short video | Narrative tone, practical details | 3-8 tags, intent-based | Mid or end of text | Keep stronger context details in copy. |
| Instagram | Reel-first for reach, optional feed fallback | Brand-consistent concise caption | 3-8 tags, brand + topic mix | End of caption | Support both Reel and feed caption variants. |

## 2. Payload Template (Normalized)

All generated content is normalized into:

```json
{
  "headline": "string",
  "body": "string",
  "caption": "string",
  "hashtags": ["string"],
  "cta_text": "string",
  "cta_url": "string"
}
```

Platform adapters map normalized payload to channel-specific publish payload.

## 3. Validation Rules

| Rule ID | Rule |
| --- | --- |
| VR-1 | Caption cannot be empty. |
| VR-2 | At least one hashtag must exist after template expansion. |
| VR-3 | Media asset must be attached before job can move to `queued`. |
| VR-4 | If platform-specific hard limit is exceeded, truncate with warning and store original. |
| VR-5 | All outgoing payloads include campaign id for traceability. |

## 4. Style Profiles

| Profile | Tone | Example Use |
| --- | --- | --- |
| `teacher_invite` | Warm and inviting | General audience invitation |
| `student_highlight` | Celebratory and specific | Spotlight post for performers |
| `last_call` | Urgent and concise | Reminder at T-1 day |

## 5. Scheduling Presets

| Preset | Timepoint | Goal |
| --- | --- | --- |
| `early_awareness` | T-7 days | Build initial awareness |
| `engagement_push` | T-3 days | Increase intent and RSVPs |
| `final_reminder` | T-1 day | Maximize attendance conversion |

## 6. Open Validation Items

These items must be confirmed during adapter integration:

1. Final per-platform character limit and media constraints in live environment.
2. Whether each platform supports direct scheduling through current integration path.
3. Error taxonomy mapping from platform response to internal `error_code`.
