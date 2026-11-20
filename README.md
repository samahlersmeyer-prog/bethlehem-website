# Bethlehem Lutheran Church website

Static website for Bethlehem Lutheran Church (LCMS), 3705 S. Anthony Blvd., Fort Wayne, IN.

- `index.html` is the whole site (home, Church Life, News and Our Story pages).
- `images/` holds the photos.
- `404.html` forwards old bethlehemlcms.org page addresses to the matching section.
- The This Sunday box, order of service, calendars and new bulletins come from the worship planner feed
  (`bethlehem-worship.web.app/public/this-sunday.json`), refreshed nightly. If it is down, the calendars fall back to the weekly schedule.
- `LAUNCH.md` has the steps for pointing bethlehemlcms.org here.

Hosted with GitHub Pages. Every change pushed to `main` goes live within a minute or two.
