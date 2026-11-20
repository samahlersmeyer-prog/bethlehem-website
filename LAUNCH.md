# Launch checklist: moving bethlehemlcms.org to GitHub Pages

## Before the switch
- [ ] Ben signs off on the content (staff list, times, photos, family line, history and charter member list).
- [ ] Luke downloads every file from the old site's `editoruploads/files/` (BULLETINS and MESSENGER folders).
      Those links stop working when the domain moves. Put them in a `files/` folder in this repo and update the links,
      or put them in a shared Google Drive folder.
- [ ] Luke exports the current DNS records from IONOS (screenshot is fine). **Keep every MX, TXT (SPF/DKIM) and
      mail-related record exactly as it is, so church email keeps working.**
- [ ] Confirm Pastor Ben's email domain: the site lists `pastorben@bethlehemlcms.com`, but the site is `.org`.
- [ ] Merge the worship planner's website-feed pull request and paste its `firestore.rules` into the Firebase console,
      so the office can add bulletin links on final weekends.

## The switch (about 15 minutes, then up to a few hours for DNS)
1. In this repo: **Settings → Pages → Custom domain** → `www.bethlehemlcms.org` → Save.
   GitHub adds a `CNAME` file. (Don't add it earlier, or the github.io preview link starts redirecting to the old site.)
2. In IONOS DNS for `bethlehemlcms.org`, change only the website records:
   - `www` → **CNAME** `samahlersmeyer-prog.github.io`
   - `@` (bare domain) → **A** records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - Delete any other A/AAAA records on `@` and `www` that point at IONOS hosting.
   - Leave MX and TXT records alone.
3. Back in **Settings → Pages**, wait for the DNS check to pass, then turn on **Enforce HTTPS**.

## After the switch
- [ ] Open `bethlehemlcms.org`, `www.bethlehemlcms.org` and an old address (`/about/our-beliefs.cfm`), which should
      land on the matching section.
- [ ] Send a test email to the church addresses to confirm email still arrives.
- [ ] In the worship planner's Firebase project, add `www.bethlehemlcms.org` under Authentication → Authorized domains
      only if the planner is ever opened from that domain (not needed for the public feed).
- [ ] Cancel IONOS **website hosting** only after a week of the new site running. Keep the **domain** registration and
      email (or move them deliberately later).

## Weekly upkeep (no code)
- **This Sunday, order of service and calendar** update themselves every night from the worship planner.
  The order of service appears once Pastor Ben marks the weekend final.
- **Bulletin:** Akasha pastes the Canva public view link into the weekend's **Website** card in the planner.
  It shows up on the site the next morning.
- **The Messenger:** still a manual link in `index.html` (`#messenger`) for now.
