# YouTube: ranking, growth and use on client sites

Status: **researched 2026-10-17** from YouTube Help, the YouTube Official Blog, Google Search Central (video), Google Analytics Help, 総務省 usage surveys, 消費者庁 (ステマ), JASRAC and the YouTube Japan blog (`SOURCES.md`, section "YouTube"). Facts carry a source; practice is marked. SNS: `sns.md`. Law: `../legal/japan.md`.

## What YouTube optimises (fact)

- The system aims for **long-term viewer satisfaction**: it uses what people watch, skip, search, like, dislike and mark "not interested", watch time (absolute and relative) and post-watch surveys. It "doesn't push videos out"; each viewer's recommendations are pulled for them. It has no preferred video type or format.
- Search ranks by how well **title, description and video content** match the query, plus engagement for that query; it is not a list of the most-viewed videos.
- So there is no algorithm trick: earn the click honestly (title + thumbnail) and keep the viewer satisfied (content).

## Myths (what YouTube itself says)

| Myth | YouTube |
|---|---|
| Tags matter | tags play a "minimal role"; useful mainly for misspellings; tag lists in descriptions break the spam policy |
| Upload at the right time | publish time is not known to affect long-term performance (matters for live and premieres) |
| Post daily or weekly or the channel dies | view growth is not correlated with upload interval; breaks were not correlated with view changes |
| One weak video hurts the channel | no; declines come when viewers stop watching most videos |
| Sub4sub, buying views | policy violation (incentivisation spam); asking people to subscribe is fine |
| Clickbait is harmless | malicious clickbait breaks the spam and thumbnail policies; it also lowers watch time |

## Packaging

- **Title** (practice): the search phrase early, natural Japanese a person would type (「通信制高校 学費」), about 60 characters so phones do not cut it; never a keyword list.
- **Description:** the first 1–2 lines carry the point and the site link (they show before "more"), then chapters, links, up to 3 hashtags. More than 60 hashtags = all ignored (fact).
- **Chapters:** at least 3 timestamps, the first at 00:00, each at least 10 s (fact).
- **Thumbnail** (practice): 1280 × 720, a large face or object, up to 3–4 words of bold text readable on a phone. Misleading thumbnails are removed (fact).
- **A/B test** ("Test & compare titles and thumbnails"): up to 3 variants; the winner is chosen by **watch-time share**, not CTR; desktop Studio only; not for Shorts (fact).
- **CTR:** half of all channels and videos sit between **2 % and 10 %** impression CTR; judge it only with many impressions; high CTR with low watch time is a clickbait warning (fact).

## Holding the viewer

- **Intro retention** = share still watching after 30 seconds; if it is low, the opening does not match the title and thumbnail (fact). Open with the promise in the first seconds, no long logo intro (practice).
- Length should fit the content; relative watch time matters more for short videos, absolute for long ones (fact).
- **Shorts:** vertical, up to **3 minutes**; since 2025-03-31 every start counts as a Shorts view (fact). Practice: Shorts for reach (campus life, one tip), long videos for trust and enquiries (explanations, interviews, FAQ).
- Consistency that helps (practice): a recognisable series format and a pace the team can keep for 6–12 months; two good videos a month beat two a week abandoned after two months.

## Captions and languages

- Japanese automatic captions exist; YouTube says always review and edit them (fact). Upload a corrected caption file.
- **Translated titles and descriptions are searchable** in other languages (fact): for English markets add an English title, description and captions.
- **Auto-dubbing** is on by default for eligible channels; a dub cannot be edited, only unpublished; choose "publish manually" to review first (fact). Multi-language audio tracks can be uploaded (Advanced features).

## Policies for business channels (fact)

- **AI content:** realistic synthetic content (a real person made to say something, a fake real event, a realistic scene that never happened) must be disclosed; not needed for clear fantasy, filters, AI help with scripts or thumbnails. Disclosure does not reduce reach.
- **Paid promotion:** tick the paid-promotion box (it shows "Includes paid promotion"); creators and brands remain responsible for the law.
- **Made for kids:** a wrong setting limits recommendations and features. A school video for parents and teens is usually not "made for kids": decide per video.

## Japan

- Usage (総務省 令和7年度 survey, published 2026-06-26): YouTube **81.5 %** of all ages; 10代 95.0 %, 20代 96.3 %, 30代 94.0 %, 40代 91.6 %, 50代 84.9 %, 60代 72.6 %, 70代 48.5 %. Parents, B2B buyers and older patients are all there (fact for the figures).
- **ステマ規制:** a paid tie-up needs YouTube's paid-promotion box **and** 「PR」 or 「プロモーション」 in the title or first line of the description **and** a spoken mention. 消費者庁 names a notice shown too briefly in a video as unclear, so the YouTube label alone is not enough (practice built on the 消費者庁 guidebook). A company's own channel about its own services is not ステマ, but 景表法 claims rules still apply.
- **Clinics:** videos are advertising under 医療広告等ガイドライン: no patient testimonials, before/after only with treatment, cost, risks and side effects (`../legal/japan.md`).
- **Music:** JASRAC (and NexTone) have blanket deals with YouTube for compositions, **not for the master recordings** of commercial tracks; use the YouTube Audio Library or licensed stock music, never a CD or streaming track (fact for the deals; rule practice).
- **Students and patients on camera:** written consent from the guardian per use and platform, renewed each school year; "unlisted" is not private (practice).

## On the website

- **Embeds:** use the privacy-enhanced domain (`youtube-nocookie.com`) and a **facade** (a poster image with a play button that loads the player on click, e.g. lite-youtube) instead of a raw iframe, which loads about 0.5–1 MB of scripts; never an autoplaying embed in the hero (fact for nocookie; practice for the rest). Flatsome's `[ux_video]` prints a normal iframe; prefer its video button / lightbox element or a facade plugin.
- **Google video results:** a video is indexed only on a **watch page** where the video is the main content; a video inside a normal article or service page will not get a video result (fact, since 2023-12). For key videos make one page each: title, summary or transcript, `VideoObject` with the YouTube `embedUrl`, chapters in the YouTube description for key moments.
- **Linking:** website in the channel links and in every description; Organization `sameAs` with the channel URL; a 「動画で見る」 page with playlists that mirror the site's main pages (practice).
- **Measuring:** links from YouTube descriptions carry `utm_source=youtube&utm_medium=video&utm_campaign=<series>`; `medium=video` lands in GA4's **Organic Video** channel (fact for the channel rule). YouTube is external, so UTMs are correct here (the "no UTM between our own domains" rule does not apply).

## Monthly report (practice)

Impressions, CTR, intro retention (30 s), average view duration, returning viewers, traffic sources (browse, suggested, search, external, Shorts feed), subscribers gained; GA4 Organic Video sessions → key events; Search Console "Videos" search appearance and the video indexing report. Legal checks done (PR labels, clinic wording, music).
