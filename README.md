# Sensor Detectives — GitHub Pages files

## Files
- `index.html` — student team activity, mystery sensor investigation, engineering mission, and Google Form submission.
- `teacher.html` — instructor dashboard that reads the published Google Sheets response CSV.

## Google Form connection
The student page submits one JSON record into the existing Google Form field:
- Form endpoint: `https://docs.google.com/forms/d/e/1FAIpQLSd7flk9dbfjnUNjjnjWI7JADqkSc6CYWt6BgmGeGka3S2cGXQ/formResponse`
- Field name: `entry.940517399`

The Google Form currently has a single `result` question. The complete team submission is serialized as JSON into that field. This avoids needing to add many new questions to the form.

## Publish the response sheet
1. Open the Google Sheet connected to the form.
2. Choose **File → Share → Publish to web**.
3. Select the form responses worksheet (usually `Form Responses 1`).
4. Choose **Comma-separated values (.csv)** and publish.
5. Copy the published CSV URL.
6. Open `teacher.html` after deployment and paste the published CSV URL into the field, then click **Load submissions**.

The sheet must be published to the web for the static teacher dashboard to read it. Do not publish any sheet containing private information beyond what you are comfortable making public. If you need a private teacher-only dashboard, use an authenticated backend or Apps Script instead.

## Deploy to the existing repository
1. Download the ZIP and extract it.
2. Replace the repository's existing `index.html` and `teacher.html` with these files.
3. Commit and push to the branch used by GitHub Pages (commonly `main`).
4. Wait for GitHub Pages to redeploy.

Student link: `https://esraamagedd.github.io/mystery-box/`
Teacher link: `https://esraamagedd.github.io/mystery-box/teacher.html`

## Notes
- The game has five fixed investigation cases: LDR, ultrasonic distance, rain, temperature, and PIR motion.
- Score is a formative activity score, not a secure exam grade. Since the activity is a static website, students can modify browser-side data.
- The form submission is sent to Google Forms in a hidden iframe. Google Forms does not provide a reliable browser success response, so the student page reports that the submission was sent but the instructor should verify it appears in the response sheet.
