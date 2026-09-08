# 🎓 GOOGLE SHEETS + TEACHER SETUP GUIDE
### For `Q3_QUIZ_100.html` — Unit 10: Changing Fashions (100 pts · 30 mins)

This quiz automatically sends every student's answers and score to a **Google Sheet** of your choice.
It has **NEW** features:
- **Fresh vocabulary exercises** (Sections 1 & 3 are brand-new sentences — not copied from the textbook).
- **A clickable reading text box** (📖 "SHOW the reading text") so students can read the report on their phone before the reading questions.
- **Full answer review after submit:** students tap **"See my answers & the answer keys"** and see every question, their own answer, the correct answer (green), and a ✓/✗ for each exercise with the points earned.
- Password-protected **Teacher mode** with the complete answer key.

---

## STEP 1 — Create the Google Sheet that collects answers
1. Go to <https://sheets.new> → a new empty spreadsheet opens.
2. Name it, e.g. **"Unit 10 Fashion Quiz — Results"**. Keep this tab open.
3. Copy the **URL** — you don't need it yet, but it helps.

---

## STEP 2 — Add the Apps Script that writes answers to the sheet
1. In the sheet, click **Extensions ▸ Apps Script**. A script editor opens.
2. Delete everything in the editor, and **paste the code below**.
3. Click the **Save 💾** icon (top-left). Name it "QuizEndPoint".

```javascript
// ---------- GOOGLE APPS SCRIPT · Quiz endpoint ----------
function doPost(e) {
  try {
    var data = JSON.parse(e.postData.contents);
    var ss = SpreadsheetApp.getActiveSpreadsheet();
    var sheet = ss.getSheetByName('Responses') || ss.insertSheet('Responses');

    // Column headers (first row)
    var HEADERS = ['Timestamp','Name','Class','Score (%)','Points',
      'S1 Verbs','S2 Sort','S3 Gaps','S4 TrueFalse','S5 Ex4','S6 Compr','S7 Keywords',
      'Q1','Q2','Q3','Q4','Q5','Q6','Q7','Q8','Q9','Q10','Q11','Q12','Q13','Q14','Q15','Q16',
      'Q17','Q18','Q19','Q20','Q21','Q22','Q23','Q24','Q25','Q26','Q27','Q28','Q29','Q30','Details'];

    var headerRow = sheet.getRange(1,1,1,HEADERS.length).getValues()[0];
    if (headerRow[0] !== 'Timestamp') {           // first time only
      sheet.getRange(1,1,1,HEADERS.length).setValues([HEADERS]);
      sheet.getFrozenRows(1);
    }

    var row = [ new Date(), data.name, data.cls, data.percent, data.points ]
      .concat( data.sections || [], data.answers || [], [ data.details || '' ] );

    sheet.appendRow(row);
    return ContentService.createTextOutput('OK').setMimeType(ContentService.MimeType.TEXT);
  } catch (err) {
    return ContentService.createTextOutput('ERR: ' + err).setMimeType(ContentService.MimeType.TEXT);
  }
}
```

---

## STEP 3 — Deploy it as a Web App (this is what gives you the URL)
1. Click **Deploy ▸ New deployment**.
2. **⚙ Select type:** `Web app`.
3. Under **Execute as:** choose **Me (your email)**.
4. Under **Who has access:** choose **Anyone**  ⚠️ *This is essential* — so the students' phones can post without logging in.
5. Click **Deploy** → copy the **Web app URL** (it ends in `/exec`).
6. If Google asks you to **authorize**, click **Authorize** and allow access.

> 📌 Keep this `/exec` URL — it's your endpoint. You may update the script later and click
> **Deploy ▸ Manage deployments ▸ ✎ Edit ▸ New version** to re-deploy.

---

## STEP 4 — Put your URL into the quiz
1. Open **`Q3_QUIZ_100.html`** in any text editor (or Notepad / a code editor).
2. Search for: `const GOOGLE_WEBAPP_URL = "";`
3. Paste your `/exec` URL between the quotes.
4. Save. That's it — the quiz is now connected to your sheet.

---

## STEP 5 — Share it with the class
- Send **`Q3_QUIZ_100.html`** to the students (class Telegram/Zalo group, email, or a class website).
- They open it **in a phone browser** (Chrome/Safari). It needs internet only to send the score
  to your sheet — the quiz itself works offline.

> 💡 **Tip:** To make one neat link instead of a file, upload the HTML to a free host (e.g. GitHub Pages,
> Netlify Drop, or your school platform) and share that link. The phone just needs to load the page.

---

## 🔐 TEACHER MODE — password: `8Cteacher`
- Tap the small **🔒 Teacher** button in the top-right corner of the quiz.
- Enter the password **`8Cteacher`** → a green **“TEACHER MODE ON”** banner appears.
- Now:
  - **Reveal answers:** the correct option in every question gets highlighted **green**,
    and sorting shows the correct boxes.
  - **Teacher panel:** scroll to the bottom to see the **full answer key** for every question.
- Tap **🔓 Exit** to return to normal student view.

> Change the password: search for `const TEACHER_PASSWORD = "8Cteacher";` near the top of the file.

---

## 📊 What each student submits to the sheet
One row per submission:
- **Name · Class · Timestamp**
- **Score (%)** and **Points** out of 100
- **Per-section breakdown** (S1–S7)
- **Their exact answers** to all 30+ questions (Q1–Q30…)
- **Details** — a text summary (e.g. how many sort words they placed).

---

## ✅ RUNNING THE LESSON (suggested)
1. Students join, type **Name + Class**, tap **Start** (30:00 countdown begins).
2. Each exercise shows clear instructions in a blue box.
3. Top timer shows remaining time — it **auto-submits** when it hits 0.
4. Students tap **Finish & Submit** when done → they see their score & points; their row lands in your Sheet.
5. You watch results in Google Sheets live; if they take breaks, they can **Resume** later.

*Tip: set the timer to 25 minutes for a slightly tighter challenge, or adjust the total points per section by editing the `POINTS` values in the file.*

---

## ⚠️ Troubleshooting
| Problem | Fix |
|---|---|
| Row doesn't appear in the sheet | Make sure the Web App "Who has access = Anyone", and the `/exec` URL is pasted correctly. Re-deploy the script after edits. |
| "ERR:" in console / not posting | Check the sheet name — the script creates a sheet named **Responses**. |
| Quiz won't open on phones | Ensure they open the actual file/URL in a browser, not inside a messaging app's preview. |
| Want columns in a different order | Edit the `HEADERS` array in the Apps Script to match. |
