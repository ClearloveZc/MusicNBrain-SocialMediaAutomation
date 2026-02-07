# US3 Product Requirements

Owner: Zhenchao  
Version: v1.0  
Date: 2026-02-07

## 1. Problem Statement

Music teachers spend too much time preparing social posts for concert promotion.  
US3 delivers a minimum workflow where a teacher can create campaign-ready promotional content and publish it on the required platforms with minimal manual work.

## 2. User Story

As a music teacher, I want the system to automatically generate promotional content and post to social media, so that I can attract more audience without spending time on manual marketing work.

## 3. US3 MVP Definition

US3 MVP is complete when a teacher can run one campaign from input to published posts across the required channels with visible status and retry support.

## 4. Scope

## In Scope (MVP)

1. Concert input form (title, date, location, student highlights, registration link).
2. AI content generation for flyer text and caption variants.
3. Post scheduling based on concert timeline.
4. Publishing adapters for Xiaohongshu, TikTok, Instagram.
5. Platform-specific formatting rules for content output.
6. Publish status page with success/failure logs and manual retry.

## Out of Scope (MVP)

1. Paid ads and budget optimization.
2. Multi-language translation pipeline.
3. Audience analytics dashboard.
4. Auto-reply to comments and direct messages.

## 5. Functional Requirements

| ID | Requirement | Priority |
| --- | --- | --- |
| FR-1 | Teacher can create a promotion campaign from concert details. | P0 |
| FR-2 | System generates at least 1 flyer concept and 3 caption variants. | P0 |
| FR-3 | Teacher can edit generated copy before scheduling. | P0 |
| FR-4 | System proposes default posting timeline (T-7d, T-3d, T-1d). | P0 |
| FR-5 | Teacher can confirm or modify schedule times per platform. | P0 |
| FR-6 | System publishes to Xiaohongshu, TikTok, Instagram through channel adapters. | P0 |
| FR-7 | System applies channel formatting templates before publish. | P0 |
| FR-8 | System records publish job status (`queued`, `running`, `success`, `failed`). | P0 |
| FR-9 | Teacher can retry failed jobs from status page. | P1 |
| FR-10 | System stores campaign artifacts for later reuse. | P1 |

## 6. Non-Functional Requirements

| ID | Requirement |
| --- | --- |
| NFR-1 | End-to-end campaign publish setup should be under 5 minutes for first run. |
| NFR-2 | Publish scheduler executes jobs within +/- 2 minutes from target time. |
| NFR-3 | Failed publish events must include actionable error reasons in logs. |
| NFR-4 | No plaintext secrets in source code or logs. |

## 7. Acceptance Criteria (Meeting Alignment)

| AC ID | Acceptance Criterion | Verification Method |
| --- | --- | --- |
| AC-1 | AI generates flyer based on concert details. | Create campaign with sample concert; verify flyer output exists and is editable. |
| AC-2 | System schedules posts according to concert timeline. | Verify auto-generated schedule and job queue timestamps. |
| AC-3 | Supports Xiaohongshu, TikTok, Instagram. | Execute one publish job per platform and observe status transitions. |
| AC-4 | Content matches platform-specific formats. | Validate output against platform template matrix. |

## 8. User Flows Covered by MVP

1. Teacher creates campaign.
2. System generates content.
3. Teacher reviews and edits.
4. Teacher confirms schedule.
5. System executes queued publishing jobs.
6. Teacher checks status and retries failures.

## 9. Success Metrics

1. 90 percent of campaigns can be configured in one pass without developer help.
2. 85 percent first-attempt publish success rate across all channels.
3. 100 percent of failed jobs show clear error category and retry action.

## 10. Risks and Mitigation

| Risk | Impact | Mitigation |
| --- | --- | --- |
| Platform UI/API changes | Publish failures | Adapter abstraction per platform and fast selector/config updates. |
| Rate limits | Delayed posting | Queue backoff and controlled retry windows. |
| AI content quality variance | Low-quality promo copy | Human review checkpoint before scheduling. |
| Credential expiration | Runtime failures | Preflight credential check and token freshness warning. |

## 11. Delivery Plan (Week-Level)

1. Week 1: Product and design artifacts finalization.
2. Week 2: TikTok adapter hardening and generic channel adapter interface.
3. Week 3: Xiaohongshu and Instagram adapter baseline + format templates.
4. Week 4: Integration test, demo script, and handoff notes.
