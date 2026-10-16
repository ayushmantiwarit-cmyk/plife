# PLIFE – Animal Saviour 🐾

A single-page website that helps ordinary people in India look after an injured or lost wild animal or bird **until the forest department / rescuers arrive**.

Built for **Hacktoberfest 2026 – Best Open-Source AI Project** (WikiClub Tech, UIT Prayagraj).

## Problem Statement
When someone finds an injured animal or a baby bird, they often don't know what to do. Well-meaning mistakes (giving cow's milk, forcing water, keeping the animal as a pet, handling a dangerous animal) can kill the animal or hurt the person. They also don't know which forest department number to call.

## Solution
- **Rescue Guide:** do's and don'ts and animal-wise first aid (baby bird, injured bird, squirrel, deer, snake, monkey, heat stress).
- **Location-based Helpline:** the user chooses a state and district (or taps "use my location") and sees the matching forest department / rescue number with click-to-call.
- **Instant Care Guide:** the user describes the animal and its condition and gets a first-aid guide immediately (safety, shelter, food/water, what not to do, who to call). It works offline from a built-in rule set, with no API key.
- **Gemini AI Advisor (optional):** if a Gemini key is set in the file, Gemini adds a more detailed answer below the instant guide, in the selected language. The chosen location is passed to the AI.
- **Indian languages:** a language picker (dropdown + search box) covers the 22 scheduled languages plus English, Bhojpuri, Awadhi and Mizo. The page is translated with Google Translate, and Gemini replies in the chosen language.
- **Animal Info Search:** quick Wikipedia summary of an animal.

## Technologies Used
HTML, CSS, JavaScript (one file, no build step, no backend) · Google Gemini API · Google Translate widget · Wikipedia REST API · OpenStreetMap Nominatim (reverse geocoding)

## AI Model
- Default: `gemini-2.5-flash` (change `GEMINI_MODEL` at the top of the script in `index.html`)
- Gemini API terms: https://ai.google.dev/gemini-api/terms

> Gemini is accessed through Google's API and is **not** an open-weight model. If your challenge requires an open-weight model, replace the `fetch` call in `askAI()` with a local model (for example Ollama) and update this section with its exact name and license.

## AI Integration
`offlineAdvice()` in `index.html` classifies the animal (baby bird, bird, small mammal, large animal, reptile) and the situation (bleeding, heat, cold, fell from nest, entangled) and returns a guide instantly. If `GEMINI_API_KEY` is set, `askAI()` also sends the animal, age, location, condition and language to the Gemini API with a safety-focused system prompt (no medicines, no forced feeding, always call the forest department, never invent phone numbers) and shows the answer below the instant guide.

## Installation and Usage
1. Download `index.html`.
2. Open it in a browser (double-click). That's it.
3. Optional: get a free key at https://aistudio.google.com/apikey and put it in `GEMINI_API_KEY` at the top of the script to enable the Gemini advice.

> Security note: with no backend, a key in the file is visible to anyone who opens the page. Never commit a real key to a public repo. Restrict the key to your website in Google AI Studio, or put it behind a small server for public deployment.

## Helpline Data
Numbers come from official state forest department websites and news reports. States with no verified direct number show 112 and a search link instead. Numbers can change, so please verify and send a pull request to update the `HELPLINES` object in `index.html`.

## Limitations (honest list)
- The instant guide is rule-based and generic; Gemini advice can be wrong. Neither is a substitute for a vet or forest official.
- Helpline coverage is partial; not every state has a verified number, and numbers are state-level (not district-level).
- "Use my location" needs browser permission and internet, and works best on https or localhost.
- Translation is automatic (Google Translate) and needs internet; it may contain mistakes, and a few languages (for example Bodo or Kashmiri) may not be supported by it. Those show as "page translation unavailable" and stay in English; Gemini can still answer in them.
- No image recognition or user accounts yet.

## Credits
The base page layout/theme started from the author's earlier personal "Forest World" page (animal search + Wikipedia). The rescue guide, location helpline chooser and AI advisor were built for this event.

## License
MIT – see [LICENSE](LICENSE).

## Demo
_Add screenshots or a demo link here._
