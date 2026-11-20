# FileHub Upgraded

FileHub is a Firebase-powered secure file sharing platform with separate file and AI image prompt libraries.

## Included

- User panel with `/files` and `/prompts` sections
- Admin panel for files, AI prompts, users, notifications and site customization
- Welcome popup, scrolling notice and inline notice button
- Configurable header/footer ad and script slots
- Adsterra direct-link support
- Custom colors, branding and logo URL
- AI assistant with file-aware responses and admin instructions

## Run locally

This is a static HTML app. Serve the project directory with any static web server, for example:

```bash
python3 -m http.server 4173
```

Open `index.html` for the user panel and `FILEHUB.html` for the admin panel.

## HTML Template Library (new)

- Admin Panel → **HTML Templates**: create/edit/delete templates, add thumbnail, Markdown description, raw HTML source, ad unlock count, optional admin unlock code, and publish/draft status.
- User Panel → **HTML Templates**: view published templates, complete the configured Ad unlock steps or enter the admin code, then download a standalone `.html` file or copy its source.
- Template metadata is stored at `html_templates`; HTML source is stored separately at `html_template_sources`; per-user code unlocks are stored at `user_template_unlocks`.
- Template descriptions, welcome popup messages, scrolling notices, file descriptions and push notices render Markdown through Marked + DOMPurify.

### Important security note

The existing project is a client-side Firebase app. The Ad timer and admin-code UI are client-side gates, not tamper-proof proof-of-view. To enforce unlocks against users who directly call Firebase, configure Realtime Database Security Rules or a trusted server/Cloud Function so `html_template_sources` can only be read after a server-verified unlock. Never treat a client-side timer or a client-readable code hash as secure payment/ad verification.
