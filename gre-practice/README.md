# GRE Pair Practice — local demo

Entry point: homepage footer, after “Layout after Jon Barron.” → GRE Practice (`gre-practice/`).
The practice page reuses the homepage stylesheet, including its font, colors, and dark mode.

Run the homepage with any static server, for example:

```sh
python3 -m http.server 8765 --bind 127.0.0.1
```

Then open http://127.0.0.1:8765/gre-practice/.

## Bank

`bank.js` contains 88 unique pairs / 175 distinct words and phrases extracted from
`BB高新6选2词表 - 26年9月.pdf`.
Duplicate pairs were merged. Definitions and common meanings follow the supplied
word list; memory mnemonics and instructions in the PDF are not app instructions.
No source PDFs are copied into the website. Other vocabulary banks are listed but
disabled until they are imported. The mathematics list is not a pairing bank.

This is word-list recall practice, not a set of original GRE sentence-equivalence
questions. Random distractors exclude any other recorded pair among the six options;
this does not guarantee there are no semantic overlaps outside the supplied list.

## Flow and storage

Select two words → submit → paraphrase orally or in the optional text field →
reveal source definitions → self-rate recall → next question.
A wrong pairing or an “unfamiliar” recall rating adds the target pair to review.
It leaves review after a correct pairing and a “remembered” rating.
Rounds contain 5, 10, or 20 questions (fewer if the review pool is smaller).
Progress, current round, typed paraphrases, and review IDs are stored in localStorage
under `gre-pair-demo-v1`. No account, backend, AI grading, or cross-device sync.

Verified locally in Chrome: entry link, correct and wrong answers, resume after
reload, paraphrase persistence, completed round, review selection, 250 random
questions containing exactly one bank-defined pair, and 390px mobile layout.
