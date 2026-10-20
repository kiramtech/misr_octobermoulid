# Misr Trip Coordinator

Passenger lists by Cairo arrival, Cairo departure and origin, with Cairo to Mazrah and Mazrah to Cairo bus numbers. The 30 passengers already booked are included.

## Setup (about 10 minutes)

### 1. Supabase (database)

1. Sign in at supabase.com and click New project. Any name and region will do.
2. Open SQL Editor, click New query, and paste the whole of `supabase-setup.sql`.
3. Find `CHANGE-ME` in section 2 and replace it with your admin PIN, keeping the quotes. Click Run.
4. Open Project Settings > API and copy two values: the Project URL and the anon public key.

### 2. Connect the app

Open `config.js` and paste the two values in place of `PASTE_PROJECT_URL_HERE` and `PASTE_ANON_PUBLIC_KEY_HERE`. This is the only file you edit.

### 3. GitHub Pages (hosting)

1. On github.com, click New repository, give it a name, and create it.
2. Click "uploading an existing file" and drag in `index.html`, `config.js`, `manifest.json` and the `icons` folder. Click Commit changes.
3. Go to Settings > Pages. Under Source choose "Deploy from a branch", then branch `main` and folder `/ (root)`, and click Save.
4. After about a minute the app is live at `https://<your-username>.github.io/<repo-name>/`.

## Using the app

- Arrivals in Cairo and Departures from Cairo tabs, each sorted by time and grouped by booking. The By origin tab groups everyone by where they start (Kerala, Dubai, Qatar and any origin added later). Mohammed Vallakkal and Muhammed Bishr Gosalakkal are always first, followed by the rest of their booking.
- Type a bus number next to a passenger, or use "Bus for all" to fill the whole booking.
- "Add a booking" at the bottom adds a new PNR to all three tabs. Pick or type where the booking travels from.
- On a phone, use Add to Home Screen to open it like an app with its own icon.
- To delete a booking, open Admin, enter the PIN, and use "Delete booking".

## Good to know

- Anyone with the link can add bookings and edit bus numbers, so share it only with the coordination team.
- The PIN is checked by the database, so it cannot be bypassed from the page.
- To change the PIN later, run this in the SQL Editor: `update public.app_settings set admin_pin = 'NEW-PIN' where id = 1;`
- To change who appears first, edit `TOP_OF_LIST` in `config.js`; to change the starred name or title, edit `STARRED`.
- Times are Cairo local times, as shown on the booking.
