# PulseRoute

**AI-powered emergency response corridor**

> Concept demo. All patient, signal and hospital-capacity data is simulated. Not for real emergencies.

---

## The problem

In one emergency, three systems work separately:

1. **Traffic** – congestion and uncoordinated signals slow the ambulance.
2. **Hospital** – the receiving team doesn't see patient vitals until the ambulance arrives.
3. **Public** – drivers don't know where to move, and bystanders aren't confident with first aid.

## Our solution

PulseRoute connects the journey from dispatch to hospital handover in one flow:

| Part | What it does |
|---|---|
| **Smart corridor** | Picks the best hospital with an AI score, plans the route, and clears signals ahead (green wave). |
| **Live patient sync** | Streams ECG, heart rate, SpO₂ and blood pressure to the hospital, only with patient consent. |
| **Equipment prep** | The crew requests tools and machines (defibrillator, cath lab, ICU bed, CT, MRI, blood units, etc.) so the hospital prepares before arrival. |
| **Citizen guidance** | Nearby drivers get proximity alerts such as "move left and slow down", plus a CPR guide with a rhythm trainer. |

---

## Features

### Route tab
- Live Google Map of Ludhiana. Tap or drag to set the accident point.
- Choose the emergency type: road accident, cardiac event, stroke, or other critical.
- Request medical equipment. Recommended items are pre-selected for each emergency type.
- Hospital preference: any, government, or private.
- **AI route evaluation** ranks hospitals by a weighted score:
  - travel time (52%)
  - match with the emergency type (18%)
  - hospital capacity (15%)
  - equipment match (15%)
- Dispatch the ambulance and watch it move with signals turning green ahead of it.
- Live stats: elapsed time, signals cleared, drivers alerted.
- PulseRoute on/off switch to compare against a normal run.
- **Human override** lets a dispatcher stop AI priority at any time.
- Traffic overlay and full-screen map (press `F`).

### Hospital tab
- Real-time ECG waveform with heart rate, SpO₂ and blood pressure.
- Patient consent toggle. When it is off, no medical data is shared.
- Advance equipment request list.
- Preparation checklist and run timeline that fill in as the ambulance gets closer.

### Citizens tab
- Alert card that changes with the ambulance distance: En Route, Approaching, Passing, Passed.
- Emergency contacts (108, 101, etc.).
- CPR quick guide with a rhythm trainer at 100, 110 or 120 bpm.

### General
- Landing screen with a launch button.
- Light and dark mode, following the device setting.
- Responsive layout, keyboard-friendly, and reduced-motion support.

---

## Tech stack

- **HTML, CSS, JavaScript** – a single file, no frameworks, no build step
- **Google Maps JavaScript API** – map, markers, traffic layer
- **Google Directions API** – ambulance route
- **Canvas API** – real-time ECG waveform
- **Inter** and **JetBrains Mono** via Google Fonts

---

## Run it locally

1. Download or clone this repository.
2. Open `hmmm.html` in a browser, or serve it with VS Code Live Server or `python -m http.server`.
3. Press **Launch Demo**.

### Google Maps API key (required for the map)

1. In Google Cloud Console, create an API key.
2. Enable **Maps JavaScript API** and **Directions API**, and turn on billing (Google has a free monthly credit).
3. Replace the key at the bottom of `hmmm.html`:

```html
<script async
  src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&loading=async&callback=initMap">
</script>
```

4. **Restrict the key** to your domain (HTTP referrers) and to those two APIs only.

> Do not publish an unrestricted key in a public repository.

If the map fails to load, the app shows a friendly "Map unavailable" message.

---

## How to demo it (about 2 minutes)

1. Press **Launch Demo**.
2. Set the accident point, pick **Cardiac Event**, and keep the recommended equipment.
3. Press **Find Hospitals**, then look at the AI ranking and press **Dispatch** on the top pick.
4. Watch signals turn green and drivers get alerted.
5. Open the **Hospital** tab for live vitals, the equipment list and the checklist.
6. Open the **Citizens** tab for the proximity alert and the CPR trainer.
7. Run it again with PulseRoute **Off**, and compare the timings.
8. Show the **Human Override** button.

---

## What is real and what is simulated

| Real | Simulated |
|---|---|
| Google Maps and Directions routing | Patient vitals and ECG |
| Hospital names and locations in Ludhiana
