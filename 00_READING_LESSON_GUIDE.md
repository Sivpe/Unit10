# 📖 READING LESSON — FASHION STATEMENTS (p.106) · Teacher Guide
### Go Beyond 3 · Secondary 8 · Focus: UNDERSTAND PARAPHRASING · ~60 min

> **Note:** All classroom exercises below are **NEW**. The page's own exercises (Ex 1, 1b, 2b, 3, 4, and the
> "match a description to each person" task) are **not reused** — students already have the book. Instead we
> teach the same **reading text & paraphrasing skill** with fresh tasks in the worksheet.

---

## 🎞 THE FILES
| File | Use it for |
|------|-----------|
| `READING_LESSON_SLIDES.html` | Teach the lesson (project). 12 slides: title → objectives → warm-up → skill → HOW-TO → article → practice → word tools → matching → worksheet → wrap-up → answer key. |
| `READING_WORKSHEET_100.html` | Student's graded worksheet (share to phones). 100 pts, 30-min timer, teacher mode (password `8Cteacher`), answer review, Google Sheets send. |

---

## ⏱ SUGGESTED 60-MIN LESSON FLOW
1. **Warm-up (5 min)** — Slide 3. "Where did your clothes come from?" pair talk.
2. **Teach the skill (10 min)** — Slides 4–5. Define paraphrasing with the colour contrast, then the HOW-TO box tips.
3. **Read (10 min)** — Slide 6 + open the article in the worksheet (tap "SHOW the reading text"). Students read
   the 6 short texts (A–F) and identify the *"from → to"* main idea of each.
4. **Guided practice (10 min)** — Slides 7–9. Do the paraphrase example, the word-family/category tools, and the
   person-to-item matching (using keywords like *stand out / bracelets / slogans / comfortable*).
5. **Independent worksheet (25 min)** — Students open `READING_WORKSHEET_100.html`, enter name/class, START.
   Timer counts down; auto-submits at 0. They see their per-exercise points and review with answer keys.
6. **Wrap-up + exit ticket (5 min)** — Slide 11. Paraphrase: *"Fashion changes, but a good jacket never goes out of style."*
7. **Teacher collects** — results land in your Google Sheet via the worksheet's Apps Script POST (if you set the URL).

---

## 🔑 WORKSHEET ANSWER KEY (100 pts)

| Section | Pts | Answers |
|---------|-----|---------|
| 1 · Vocabulary choose | 12 | slogan · stand out · accessory · banned · sole · belt |
| 2 · Paraphrase | 16 | Q7 "comfy…all the time" · Q8 "stones and bones" · Q9 "so popular…casual wear" · Q10 "stopped students wearing pajamas to lessons" |
| 3 · True / False | 24 | T · T · F · T · F · F |
| 4 · Gap-fill | 16 | sleeping · statement · hold · help · plastic · hit · sailors · communicate |
| 5 · Comprehension | 20 | B · B · B · C · B |
| 6 · Category / word family | 12 | sneakers · bracelet · comfortable · fashionable |

**Section points:** 12 + 16 + 24 + 16 + 20 + 12 = **100** (exact).

**Matching-hint notes for the article:**
- **A pajamas** — Persian word, "baggy cotton pants", jacket + sleeping, school ban.
- **B sneakers** — basketball → comfortable everyday footwear → expensive fashion statement.
- **C belts** — carry weapons → tight leather belts (power) → hold jeans up / chic accessory.
- **D chopines** — protected from dirty streets, so high you needed help to walk → stylish-but-uncomfortable high shoes without heels.
- **E jewelry** — stones & bones → gold (show wealth) → plastic (cheap accessory).
- **F t-shirts** — sailors' underwear → American actors in movies → informal wear → communicate messages.

---

## ✅ SETTING THE GOOGLE SHEETS LINK (optional)
The worksheet posts to `GOOGLE_WEBAPP_URL` (blank by default). To collect results, follow the same steps as
`00_QUIZ_SETUP_GUIDE.md` (create a sheet → Apps Script `doPost` → deploy as Web App, access = **Anyone** →
paste the `/exec` URL into `READING_WORKSHEET_100.html`).

> ⚠️ If you point the worksheet to the SAME web app as the 100-point quiz, the two products append rows into the
> same `Responses` tab with **different columns**. Simplest fix: create a **second** sheet + Apps Script deployment
> for the reading worksheet so its results stay clean. The payload already includes `"READING-WORKSHEET"` in the
> `details` field so you can tell rows apart either way.
