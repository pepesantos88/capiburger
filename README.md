# CapyBürger — review before publishing

German–English study app for the Einbürgerungstest, featuring Capy and an extra Germany trivia game.

## Open locally

From this directory run `python3 -m http.server 8080`, then open `http://localhost:8080`.
The app has no runtime dependencies. Keep `index.html`, `app.js`, `styles.css`, `assets/` and `data/` together.
Alternatively, open `index.html` directly to inspect the static app before deploying.

## What works

- Five-question daily practice; each answer shows an explanation, and finishing the fifth saves the day's score and streak. Accuracy uses completed daily practices only.
- Home shows **Questions mastered** for the chosen state: one point per distinct official question answered correctly at least once in Daily, Free Study or Mock Exam. The total is 300 general + 10 for that state; a correct answer is counted immediately, even before finishing a session. Incorrect answers and Trivia do not count. Changing state switches the 10 local questions without erasing earlier progress. Settings has a small, confirmed **Reset question progress** button; it clears this counter for all states but keeps daily streaks, exam history, settings and trophies. Prior aggregate scores cannot reconstruct earlier per-question successes, so existing users start this new counter at zero.
- Unlimited topical study; bilingual questions and answer choices; shuffled answer placement and explanations.
- One-hour mock exam: 30 general questions plus 3 for the chosen federal state; results history and a 33/33 goal.
- A first-open name prompt and a name-aware greeting. Name, federal state, translations and humour (Classic or Spicy) can be changed in Settings.
- Home prioritises the daily five, then shows a rotating word or slang word, a phrase and an expandable cultural story. Free Study and Home share six illustrated topic filters.
- Trivia: 500 drafted questions in six categories. Quick Round asks one per category, ends on the first error, shows the next score target on a loss, and awards a trophy only at 6/6. Long Run rolls a random category each turn, starts with three lives, shows a three-step bonus meter, adds a life for every three consecutive correct answers (maximum five lives), and awards a trophy for all six slices before losing all lives. Trophies are in a collapsible menu.
- Daily reminder on Home until today's practice is completed. No closed-app phone notifications in this web version.
- 365 rotating cultural prompts and 365 rotating German words, including colloquial words.
- All 300 nationwide and 160 state questions have bilingual study cards. Nationwide questions 72 and 73 have updated options because the 2025 BAMF PDF gives outdated answers. As of **3 October 2026**, the app uses Friedrich Merz as chancellor and CDU/CSU plus AfD as the two largest Bundestag groups. Each adapted question is marked with its update date and explains what changed. Recheck time-sensitive facts before the real exam.
- The 43 image-based questions use 100 original, simplified SVG study illustrations. These are deliberately different from the BAMF images and photographs; review the original official PDF alongside this app to recognise the exact exam artwork. No image extracted from the PDF is included in this app folder.

## Review carried out on 3 October 2026

- All 460 answer positions were compared with an independent marked catalog. Four conflicting keys were checked against the actual German option text; the geographically/institutionally straightforward state items were reviewed separately. Another answer sheet aligned with 222 nationwide keys. BAMF's interactive answer service could not be used to verify **each** key individually, so this is a carefully checked study build rather than a certified BAMF answer key.
- Current Chancellor, Bundestag group sizes and Federal President were checked against their official websites. These answers may change again before the real exam; the app dates its two altered questions, numbers 72 and 73.
- All 500 Trivia entries passed format, uniqueness of options, category, difficulty and answer-position checks. A content review identified and fixed an inaccurate Paul Ehrlich description, an awkward Z3 date question and an overly obvious literature question; their linked culture cards were regenerated. A fully independent, source-by-source verification of all 500 original questions is **not complete**. The 365 culture cards reuse these answers, so treat both as editorial study content.
- 43 image-based questions include 100 SVG study illustrations. Twelve small choice images are embedded in the question data to make the browser upload fit GitHub's 100-file limit; 88 remain separate SVG files. All image assets were checked; the Capy images also passed file validation. These diagrams approximate the originals and should be compared with the official catalog before the actual test.
- Automated flow checks cover all 16 states, the five-question daily practice, unique question mastery, correct-only scoring, state switching, reset confirmation and persistence across a simulated reload, the exam timer and results, both Trivia modes, life bonuses and trophies. The QA script lives alongside the source folder in the authoring workspace; it is not required to run the static app.
- Real browser layout and interaction checks could not be completed in this workspace because there is no browser binary; an attempt to download Chromium was blocked by its download host. **Before your one Netlify deploy**, open this exact package locally on a phone or desktop browser and try each main screen. This local preview uses no Netlify deploy.

Source of the original German catalog: [Einbürgerungstestverordnung, Anlage 1](https://www.gesetze-im-internet.de/einbtestv/anlage_1.html). Official test details and changes should be checked at [BAMF](https://www.bamf.de/).

The progress is saved in the browser's local storage on that device and browser. It does not sync between devices.

The ZIP provided with this review contains **99 files**, with `index.html` and `netlify.toml` at its root. The Netlify file sets `publish = "."`, which overrides an older publish directory selected in the Netlify UI when the repository's base directory is its root. Extract the ZIP before inspecting, and upload the **contents** at the root of the existing GitHub repository in a single commit. Do not upload the ZIP itself or a folder containing those files. Make sure any old `netlify.toml` and the build base directory in Netlify do not point into an older nested app folder. Git-connected Netlify sites normally deploy on each pushed commit; no hosted deployment has been made during this review.
