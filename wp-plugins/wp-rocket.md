# WP Rocket

Status: merged 2026-10-11. Unverified against the current version (pass 2).

WP Rocket owns page caching, lazy loading, CSS/JS optimisation and preloading. Theme lazy-load options stay off so they do not fight it.

## Routine

- After changing content, CSS or JS: clear the cache. If a change "does not show", clear the cache first and look again before changing anything else.
- Layout broken only after a CSS change: usually cached optimised CSS ("Remove Unused CSS"). Clearing regenerates it; it can take a few minutes.
- Clear only what changed on production. A full clear makes WP Rocket re-crawl the whole site, which loads the server; never clear in a loop or across many sites at once.

## A person decides

Every setting. Typical symptom → setting: "Delay JavaScript" breaking a slider or form; "Remove Unused CSS" hiding styles; preload settings. Describe the symptom and the likely setting.

## Facts

- Exclude one image from lazy load (the hero): class `skip-lazy`, or WP Rocket → Media exclusions.
- Logged-in users are not cached by default; forms and login-protected pages keep working.
- `wp rocket` WP-CLI commands exist only when the WP Rocket CLI add-on is installed; some sites do not have it.
- Do not add your own lazy-loading, minification or cache code; it conflicts.
