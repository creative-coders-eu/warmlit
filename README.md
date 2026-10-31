# Warmlit website

The public website for Warmlit, a calm, private iPhone companion for GLP-1 pills and shots. It is
served by GitHub Pages from this repository, `creative-coders-eu/warmlit`, at
https://creative-coders-eu.github.io/warmlit/

The app's source and product documents live in a separate private repository. This repository holds
only the website.

| Path | Page | Used as |
|---|---|---|
| `/` | Landing page | Marketing URL |
| `/privacy/` | Privacy Policy | App Store Connect Privacy Policy URL, in-app link |
| `/consumer-health-data/` | Consumer Health Data Privacy Policy (Washington MHMDA, Nevada SB 370) | Footer link on every page, including the homepage |
| `/terms/` | Terms of Use (they add to Apple's Standard EULA, which governs the licence) | Terms of Use (EULA) link on the paywall and in the description |
| `/support/` | Support and FAQ | App Store Connect Support URL |
| `/disclaimer/` | Medical disclaimer | Linked from the Terms and the app |
| `/404.html` | Not-found page | Served by GitHub Pages for missing URLs |

## How it's built

- Plain HTML and one stylesheet, `assets/site.css`. There is no build step and no JavaScript.
- There are no cookies, analytics, trackers, external fonts or third-party requests. Each page has a
  Content-Security-Policy meta tag that only allows this site's own stylesheet and images, so nothing
  third-party can be added by accident.
- Light and dark mode follow `prefers-color-scheme`. Colour tokens are at the top of `site.css`; every
  text colour pair meets WCAG AA contrast.
- Links are relative, so the site works at any path. The exception is `404.html`: GitHub Pages serves it
  for missing URLs at any depth, so its links start with `/warmlit/`. Change them if the site moves to a
  custom domain.
- The header and footer are repeated in every page. When you change one, change all seven.
- `robots.txt` only takes effect on a custom domain, because crawlers read it from the domain root. You
  can submit `sitemap.xml` in Search Console instead.

## Preview

Run `python3 -m http.server 8000` in this folder and visit http://localhost:8000/. Opening the files
directly also works, but folder links such as `privacy/` then show a file listing instead of the page.

Before publishing, serve the folder, fetch every page and every internal link (no 404s, and every
`#anchor` points at an existing `id`), and check that the HTML is valid.

## What the pages promise (keep in line with the app)

The pages describe Warmlit 1.0 as the product decisions define it:

- **Free forever:** medications and schedules (daily, twice daily, weekly, every few days or chosen
  days), logging with edit and backfill, dose reminders, the pill-window timer with its Live Activity
  and Dynamic Island countdown, the injection-site map, the side-effect log, manual weight, protein and
  water, full history, CSV export and import, Face ID lock, one Home Screen widget, Siri, Shortcuts and
  Control Center actions, Apple Health sync for weight, protein and water, and the end-of-window alarm
  on iOS 26 or later.
- **Warmlit Pro** sells only Warmlit's own work: insights, the doctor report, the weekly recap, the
  other widgets (Lock Screen, interactive, StandBy), and alternate app icons and themes. Prices:
  $39.99/year with a 7-day free trial, $9.99/month, or $79.99 once. There is no launch discount. The
  AI-written recap needs iOS 26 or later and Apple Intelligence; other iPhones get a template recap.
- **Only what ships in 1.0.** Apple Health sync covers weight, protein and water only: Warmlit doesn't
  read medications from Apple Health or save symptoms or side effects to it.
- **United States only** at launch.

## Keep in sync

- **App Store badge.** The landing page shows a "Coming soon" note. At launch, replace it with Apple's
  official "Download on the App Store" badge, unmodified (don't recreate it in CSS), linked to the
  product page.
- **Prices.** The US prices and trial terms on the landing page and in the Terms must match App Store
  Connect.
- **Legal pages.** Version 1.0 of the Privacy Policy, the Consumer Health Data Privacy Policy and the
  Terms is the first published version, so their change logs start with it. Once the pages are live,
  any change updates the version (and the effective date when it moves) and adds a change-log entry;
  never describe features that aren't in the app there. Announce material changes in the app's
  release notes. Terms §19 lists the only reasons the Terms may change, and a change that reduces
  users' rights needs at least 30 days' notice in the release notes and on the page. Before personal
  data is used for a new purpose, tell the people it's about directly; for consumer health data, also
  ask for their consent.
- **Terms and EULA.** Apple's Standard EULA governs the licence, and App Store Connect uses it (no
  custom EULA). The Terms only add Warmlit's own commitments. Keep it that way: a custom EULA would
  need Apple's minimum terms, including a phone number, which this site doesn't show.
- **Prices and availability.** Warmlit is offered only on the US App Store, with prices in US dollars.
  If it opens in other countries, reword the price notes on the landing page and in Terms §6–7 first.
- **Consumer Health Data Privacy Policy.** Washington's Attorney General requires it to be a separate,
  distinct link on the homepage that contains only what the My Health My Data Act requires. Its sections
  on tracking across websites and on changes to the policy are there because Nevada's law (SB 370) also
  requires them. Keep it on its own page, keep the footer link on `index.html`, and don't fold it back
  into the Privacy Policy. The company's registration details stay in its footer, not in its text.
- **Beta and support.** The privacy pages describe how the TestFlight beta works: TestFlight collects
  crash reports and usage information automatically; Apple gets the name and email address of testers
  we invite by email; the tester list holds name, email and pill, shot or switcher; we ask for consent
  before using health details in feedback or emails. Update them if the beta or support process
  changes.
- **Contact is email only:** admin@ccoders.eu. Apart from the emergency numbers 911 and 112, the site
  shows no phone number.
- **Company details.** Polish company law (KSH art. 206 § 1) expects the company's name, registered
  office and address, registry court and KRS number, NIP and share capital on its websites. They are in
  the footer of every page, in the first and contact sections of the Privacy Policy and the Terms, and
  on the Support page.
  Address blocks use the name "Creative Coders sp. z o.o."; the App Store seller name, CREATIVE CODERS
  SP Z O O, appears only where the Privacy Policy and Terms explain it. The details were checked
  against the official Ministry of Justice KRS record
  (`https://api-krs.ms.gov.pl/api/krs/OdpisAktualny/0001271368?rejestr=P&format=json`) on 2026-10-28.
  The address keeps the register's spelling, with its diacritics: "ul. płk. Zoltána Baló 6/5" (house 6,
  unit 5), 02-793 Warszawa. The company was formed on the online template, so until its share capital
  is paid in, art. 206 § 1 pkt 4 requires the pages to add, next to the amount, that the required
  contributions to the share capital have not been paid in. Remove that note from every page as soon
  as the contributions are paid in; the amount stays. The register drops its own mention after the
  management board files its statement that the contributions were paid in (KSH art. 167 § 5, KRS Act
  art. 45 ust. 1b).
- **App behaviour.** The Privacy Policy and Support pages describe these app details: "Sync with Apple
  Health" (free; weight, protein and water only), Apple Health weight, protein and water in the doctor
  report, "Show medicine names" (off by default), "Write with on-device AI" (iOS 26 or later),
  automatic local copies (erased by "Delete all data"), the Settings › Your data labels, "Alarm when
  the window ends" under Settings › Pill window, the optional Apple Health deletion in "Delete all
  data", each medicine's Reminders switch, medicines added by a CSV import starting out paused, and the
  14-day reminder horizon with its "Keep your reminders coming" notice. Update the pages if any of them
  change.
- **Icons.** `favicon.svg`, `favicon.ico`, `apple-touch-icon.png` and `assets/warmlit-icon-512.png` are
  the web copies generated with the app icon. Replace them whenever the icon changes.
- **Medicine brand names** never appear on this site, including the page titles; the app shows them only
  in its medication picker.
- **No medical claims or dosing advice.** Warmlit is not a regulated medical device; keep that sentence
  in the footer and the disclaimer.
