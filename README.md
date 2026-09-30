# Royal Velocity Cabs

A single-page website for **Royal Velocity Cabs**, an intercity cab service based in Pune. Customers can get a fare, book a cab, browse tour packages and request corporate cabs. All bookings go to WhatsApp.

## Features

- **Fare calculator**: pick pickup and drop points (or type any custom address) and get a fare based on real road distance. Trip types: one way, round trip, airport transfer.
- **Vehicle classes**: Swift / Aura / Dzire (₹14/km), Maruti Ertiga (₹17/km), Innova Crysta (₹22/km).
- **Corporate cabs**: booked as required, on a fixed 300 KM per day plan. Customers choose the vehicle and number of days and get an estimate and a WhatsApp quote request.
- **Tour packages**: a scrolling row of Maharashtra tours with search, category filters and a **Popular** tag. Includes Shirdi, Ashtavinayak, Mahabaleshwar, Lonavala, Kolhapur, Nashik–Trimbakeshwar, Ajanta–Ellora and more.
- **WhatsApp booking**: booking form, tour buttons, corporate quotes and a floating button all open WhatsApp with the details filled in.
- **Navbar**: highlights the section currently in view.
- **Fleet and reviews**: vehicle detail popups and guest reviews.

## Tech stack

Plain HTML, CSS and JavaScript in one file. There is no build step.

- [Tailwind CSS](https://tailwindcss.com) via CDN
- [Lucide](https://lucide.dev) icons via CDN
- Google Fonts (Cinzel, Plus Jakarta Sans)
- [OpenStreetMap Nominatim](https://nominatim.org) (address lookup) and [OSRM](https://project-osrm.org) (road distance) for fares. No API key needed.

## Getting started

1. Put these files in the same folder:
   - `index.html` (the website)
   - `AuraCar.avif`
   - `ErtigaCar.avif`
   - `InnovaCrystaCar.webp`
2. Open `index.html` in a browser. An internet connection is needed for styles, icons, fonts and fare distances.

### Deploy free with GitHub Pages

Repository **Settings → Pages**, choose the `main` branch and the root folder, then save. The site goes live at `https://<your-username>.github.io/<repo-name>/`.

## How the fare works

Fare = billable distance × per-km rate of the chosen vehicle. Tolls are extra and paid at actuals.

- Fixed locations are converted to coordinates and the road distance is fetched from OSRM.
- Custom addresses are looked up with Nominatim. The customer sees the matched place so they can confirm it is right.
- Round trips double the distance.
- A minimum of 120 KM is billed per booking.
- If an address can't be found, the fare shows **To be confirmed** and the WhatsApp message says the fare will be confirmed. It never shows a made-up number.
- If routing is unavailable, an approximate distance (straight line × 1.3) is used and clearly marked as approximate.

## Customising

Everything is in `index.html`. Search for these names in the `<script>` section:

| What to change | Where |
| --- | --- |
| Per-km rates and vehicle details | `vehicleSpecs` |
| Minimum billed KM | `MIN_BILLABLE_KM` |
| Corporate KM per day | `CORP_KM_PER_DAY` |
| Add or edit a tour | `tours` list (one object per tour) |
| Which tours get the Popular tag | `POPULAR` list |
| Pickup and drop hubs and their coordinates | `HUBS` and the `<select>` options |
| Per-km rates used for tour estimates | `TOUR_RATES` |
| WhatsApp number | Find and replace `917498743461` (links) and `+91 74987 43461` (displayed) |

To add a tour, add one line to `tours`. It then appears in the row, in search and under its category filter automatically.

## Known limitations

- Prices for the newer tour packages are estimates (approx. km × per-km rate). Check them before publishing.
- Nominatim and OSRM are free public services with fair-use limits and no uptime guarantee. If bookings grow, switch to the Google Maps Distance Matrix API or a similar paid service.
- The navigation links are hidden on small screens. A mobile menu is not built yet.

## Contact

WhatsApp: +91 74987 43461

## License

© 2026 Royal Velocity Travels. All rights reserved.
