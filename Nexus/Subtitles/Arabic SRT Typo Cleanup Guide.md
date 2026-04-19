# Arabic SRT Typo Cleanup Guide

This guide is for cleaning Arabic `.srt` subtitle files with an AI agent.

It focuses on:

- glued words
- missing or wrong hamza
- wrong spacing
- duplicated words
- broken punctuation
- malformed Arabic word forms
- common OCR / subtitle typing mistakes
- subtitle-safe editing rules


## Goal

The goal is not just to fix a few examples.

The goal is to make the AI agent:

1. scan the entire subtitle file
2. check every subtitle block
3. detect repeated typo patterns across the whole file
4. fix the file directly
5. re-scan after each pass
6. continue until no obvious typos remain


## Core Rules

When cleaning Arabic subtitle files, the agent should follow these rules:

1. Preserve subtitle timing and numbering.
2. Edit only subtitle text lines.
3. Do not change meaning unless the original line is clearly broken.
4. Fix spelling, glued words, hamza, punctuation, and spacing.
5. Prefer natural standard Arabic spelling.
6. Keep lines subtitle-friendly and readable.
7. Re-scan the whole file after every editing pass.
8. Do not stop after fixing only user-provided examples.


## What To Check

The AI should scan the whole document for all of the following:

### 1. Glued Words

Two or more words incorrectly stuck together.

Examples:

- `هذه هيالقد سئمت من كل هذا الهروب`
  -> `هذه هي لقد سئمت من كل هذا الهروب`

- `لديكم الحقبألتزام الصمت`
  -> `لديكم الحق بالتزام الصمت`

- `بدون مشروباتبدون مشروبات`
  -> `بدون مشروبات بدون مشروبات`

- `يافتى`
  -> `يا فتى`

- `كيفلهذه`
  -> `كيف لهذه`

- `آلينالفرامل`
  -> `آلين، الفرامل`

- `جينكابتن`
  -> `جين، كابتن`

- `ياصديقي`
  -> `يا صديقي`

- `مازلت`
  -> `ما زلت`

- `يارجل`
  -> `يا رجل`


### 2. Repeated Word Fragments

The same word or phrase accidentally duplicated.

Examples:

- `استمعوااستمعوا`
  -> `استمعوا استمعوا`

- `لقد افسدوا القصةلقد افسدوا القصة`
  -> `لقد أفسدوا القصة لقد أفسدوا القصة`

- `هل سمعتنيهل سمعتني`
  -> `هل سمعتني هل سمعتني`

- `هذههذه`
  -> `هذه هذه`


### 3. Wrong Hamza

Fix missing or wrong hamza at the beginning, middle, or end of words.

Examples:

- `اخبرني`
  -> `أخبرني`

- `اعتقد`
  -> `أعتقد`

- `اريد`
  -> `أريد`

- `اعظم`
  -> `أعظم`

- `اصبح`
  -> `أصبح`

- `اتى`
  -> `أتى`

- `احدى`
  -> `إحدى`

- `الى`
  -> `إلى`

- `اذن`
  -> `إذن`

- `او`
  -> `أو`

- `اولاً`
  -> `أولًا`

- `اشياء`
  -> `أشياء`

- `الأشاعة`
  -> `الإشاعة`

- `الموافقه`
  -> `الموافقة`

- `مسؤليتي`
  -> `مسؤوليتي`

- `المسؤل`
  -> `المسؤول`

- `المسؤلين`
  -> `المسؤولين`

- `الأجراءت`
  -> `الإجراءات`


### 4. Wrong Final Form

Common bad endings:

- `مليئه`
  -> `مليئة`

- `ممتلئه`
  -> `ممتلئة`

- `رائعه`
  -> `رائعة`

- `شيقه`
  -> `شيقة`

- `واضحه`
  -> `واضحة`

- `معقده`
  -> `معقدة`

- `ميته`
  -> `ميتة`

- `مروعه`
  -> `مروعة`

- `قرقعه`
  -> `قرقعة`

- `حاجه`
  -> `حاجة`


### 5. Broken Spaces Around `و`

Arabic conjunction `و` should usually attach to the following word.

Examples:

- `القانون و الفوضى`
  -> `القانون والفوضى`

- `دانسون و هايسميث`
  -> `دانسون وهايسميث`

- `النار و يقودون`
  -> `النار ويقودون`

- `و كل`
  -> `وكل`

- `و الأمور`
  -> `والأمور`

But do not blindly break correct structures.
Always check context.


### 6. Missing Spaces After Names Or Vocatives

Examples:

- `يافتى`
  -> `يا فتى`

- `يافتيان`
  -> `يا فتيان`

- `يارجل`
  -> `يا رجل`

- `آلينالفرامل`
  -> `آلين، الفرامل`


### 7. OCR / Typing Corruption

Examples:

- `بهدؤ`
  -> `بهدوء`

- `بأجتهدا`
  -> `باجتهاد`

- `كيفلهذه`
  -> `كيف لهذه`

- `النيجريون`
  -> `النيجيريون`

- `الشياشنيون`
  -> `الشيشانيون`

- `البرازيلة`
  -> `البرازيلية`

- `المرآه`
  -> `المرآة`

- `القواده`
  -> `القوادة`

- `الأنتظار`
  -> `الانتظار`

- `الاعمال`
  -> `الأعمال`

- `الامن`
  -> `الأمن`

- `الاسبوع`
  -> `الأسبوع`


### 8. Broken Punctuation

Examples:

- `يا فتى ، لقد اضررت سيارتي`
  -> `يا فتى، لقد أضررت سيارتي`

- `هل سمعتني ؟`
  -> `هل سمعتني؟`

- `حسناً ، توقفوا`
  -> `حسنًا، توقفوا`

- `! استمعوا`
  -> `استمعوا!`


### 9. Broken Sentence Forms

Sometimes the typo is not just a word, but a malformed phrase.

Examples:

- `انه صوت انوثي`
  -> `إنه صوت أنثوي`

- `رأيت مجموعة محقيقين`
  -> `رأيت مجموعة محققين`

- `هل تثق بنا بهدؤ`
  -> `هل تثق بنا بهدوء`

- `أنا أتحدث عن الذين يعملون بأجتهدا`
  -> `أنا أتحدث عن الذين يعملون باجتهاد`


## Safe Editing Rules For SRT

The AI should keep these formatting rules:

- Do not change subtitle numbers.
- Do not change timestamps.
- Only edit text lines.
- Preserve line breaks where possible.
- If a sentence needs punctuation, add it without breaking subtitle structure.
- Avoid turning one subtitle into long literary Arabic if simple correction is enough.


## Recommended Workflow For The AI

The AI should use multiple passes.

### Pass 1: Obvious Known Patterns

Fix:

- glued words
- duplicated words
- obvious hamza mistakes
- punctuation spacing

### Pass 2: Word Form Review

Scan for:

- words ending in `ه` that should be `ة`
- broken hamza words
- malformed Arabic forms
- common OCR damage

### Pass 3: Contextual Review

Check suspicious lines in context:

- a name glued to another word
- a conjunction glued incorrectly
- a phrase that looks semantically broken

### Pass 4: Whole File Re-Scan

After edits, scan again for:

- leftover glued forms
- repeated typo families
- wrong `و` spacing
- remaining malformed words

The AI should repeat this until no obvious typo pattern remains.


## Prompt Template

Use this prompt for future Arabic subtitle files:

```text
You are cleaning an Arabic .srt subtitle file.

Your task is to scan the ENTIRE file and fix Arabic typos directly in the subtitle text.

Important rules:
1. Do not change subtitle numbering.
2. Do not change timestamps.
3. Edit only subtitle text lines.
4. Fix the whole file, not just examples.
5. Re-scan the file after each correction pass.
6. Continue until no obvious typo patterns remain.

You must check for all of the following:
- glued words
- duplicated words
- missing spaces
- wrong spaces around the conjunction و
- missing or wrong hamza
- wrong final forms like ه instead of ة
- malformed Arabic word forms
- OCR-like corruption
- punctuation spacing errors

Examples of the kinds of fixes you must look for across the whole file:

هذه هيالقد سئمت من كل هذا الهروب
-> هذه هي لقد سئمت من كل هذا الهروب

لديكم الحقبألتزام الصمت لكني اريد سماعكم تصرخون
-> لديكم الحق بالتزام الصمت، لكني أريد سماعكم تصرخون

بدون مشروباتبدون مشروبات
-> بدون مشروبات بدون مشروبات

يافتى ، لقد اضررت سيارتي
-> يا فتى، لقد أضررت سيارتي

رأيت مجموعة محقيقين
-> رأيت مجموعة محققين

انه صوت انوثي
-> إنه صوت أنثوي

القانون و الفوضى
-> القانون والفوضى

آلينالفرامل
-> آلين، الفرامل

بهدؤ
-> بهدوء

بأجتهدا
-> باجتهاد

كيفلهذه
-> كيف لهذه

مازلت
-> ما زلت

يارجل
-> يا رجل

Instructions:
- First scan the whole file for obvious repeated typo patterns.
- Then scan for glued words and malformed Arabic forms.
- Then scan for missing hamza and broken endings.
- Then scan for wrong spacing around و.
- Then re-scan everything again.
- Fix the file directly.
- Do not stop after fixing only a few examples.
- At the end, report what typo families you corrected.
```


## Stronger Prompt For Agentic Tools

If the AI can edit files and re-check them, use this version:

```text
Read the Arabic .srt file from start to finish and clean the entire subtitle text.

Work in repeated full-file passes:

Pass 1:
- fix glued words
- fix duplicated words
- fix missing spaces
- fix punctuation spacing

Pass 2:
- fix wrong hamza
- fix broken Arabic endings
- fix malformed word forms
- fix OCR-like corruption

Pass 3:
- scan specifically for wrong spacing with و
- convert forms like "و كلمة" into "وكلمة" where appropriate

Pass 4:
- scan again for leftover glued forms like:
  - يافتى
  - يافتيان
  - يارجل
  - مازلت
  - كيفلهذه
  - آلينالفرامل
  - هذههذه
  - استمعوااستمعوا
  - بهدؤ
  - بأجتهدا

Pass 5:
- re-read the entire file for isolated one-off typos missed by pattern search

Constraints:
- keep subtitle numbers unchanged
- keep timestamps unchanged
- edit only subtitle text
- preserve subtitle readability

Do not stop after one pass.
Do not assume the file is clean until you re-scan it and no obvious typo families remain.
```


## Practical Advice

For future subtitle files, the most reliable approach is:

1. Give the AI the `.srt` file directly.
2. Tell it to edit the file in place.
3. Tell it explicitly to use multiple full-file passes.
4. Tell it to focus on typo families, not just isolated examples.
5. After it says it finished, manually spot-check random subtitle numbers.


## Suggested Filename For Reuse

You can reuse this guide as:

- `arabic_srt_typo_cleanup_guide.md`

Or copy the prompt section into future requests.