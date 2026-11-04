SAFEROUTE AI — PHONE-FRIENDLY LIVE DATABASE STARTER

WHAT THIS BUNDLE DOES
- One shared Supabase database for reports from multiple phones/users.
- Real-time insert/update/delete subscription for the safety report list.
- Leaflet/OpenStreetMap view with coloured markers when a report has GPS coordinates.
- Browser notification while the website is open and permission is granted.
- Road hazard form, GPS button, report list, counts, video preview.

IMPORTANT LIMITATIONS
- The HTML is a frontend template. It will NOT share data until you create/configure Supabase and run setup.sql.
- This starter provides foreground browser notifications only. True push notifications while the page is closed require HTTPS hosting, a service worker, a push subscription and a secure server-side push sender (for example a Supabase Edge Function + Web Push/VAPID). Do not put a service-role key or VAPID private key in the HTML.
- A local file opened as file:// is not a suitable production host for push notifications. Host the files on an HTTPS site (for example a static hosting service) for reliable browser APIs.
- The public demo policies allow anonymous users to read and submit reports. That is easy for a hackathon demo but is NOT safe for a public launch without authentication, rate limits and moderation. There is no public update/delete policy.
- Risk colours are selected by the reporter; they are not validated AI predictions. Video is preview-only; no AI model is connected.

SETUP USING A PHONE
1. Open supabase.com in Chrome and create a free project. Keep the project password private.
2. Open the project's SQL Editor, create a new query, paste all of setup.sql, and run it.
3. In Project Settings / API (or Connect), copy the Project URL and anon/public key. Never copy the service_role/secret key.
4. Host index.html over HTTPS. A local HTML editor's preview may not support realtime/notifications reliably. Keep index.html as the main site file.
5. Open the hosted site, paste Project URL and anon/public key, then tap “Connect live database”. Allow notifications using “Enable alerts”.
6. Test from two phones/browser sessions: submit a report on one and confirm the other updates. Add coordinates or tap “Use my location” to see a map marker.

BACKGROUND PUSH NOTIFICATIONS
This bundle deliberately does not pretend background push is already working. For closed-tab alerts, deploy a service worker on the same HTTPS origin and a server-side push sender. The sender must keep the VAPID private key secret and trigger pushes when a new database row is inserted. Use an Edge Function/database webhook or another trusted backend; do not expose private keys in index.html. Browser/Android notification support varies by browser and permission settings.
