---
name: application
description: Tailor a CV and write a cover letter for a specific job advert, ATS-safe and grounded only in what the applicant has actually done. Use whenever a job description, job link or role title is pasted in, whenever the user says "apply", "tailor my CV", "write a cover letter", "should I go for this", or asks to line their experience up against a role. Also use when reviewing or rewriting existing application documents.
---

# Application

Tailor to the advert, mirror its language, never invent. Everything on the page must be traceable to something the applicant actually did.

## Where this works best

Any chat window with file creation, since the output is two documents. Better in an environment that can read the user's existing CV from disk (Claude Code, Cowork, or a chat with file upload) so the tailoring works from the real document rather than a retyped summary. Set up the personal facts file below once and every application after that takes one paste of the advert.

## Setup

Before first use, ask the user for the material this skill runs on, and store it wherever the environment persists things (a `cv/` directory in the repo, a project file, memory):

- Their current CV or full work history, with real titles, dates and numbers.
- **Fixed descriptions**: any fact that must always be worded the same way. Exact job titles as they should appear, which markets or regions a piece of work actually covered, the correct name for a former employer.
- **Never-say list**: anything that must not appear. Ventures they do not want on a cover letter, a skill they have dabbled in but never shipped with, a former company they do not want named, a project under NDA.
- Logistics: notice period or availability, work authorisation, location and remote preference.

Get these wrong and the documents are worse than useless, so confirm them with the user rather than inferring. Re-read them on every run.

## Cover letter rules

- Never name a gap, a missing credential, a weakness, or anything short of the advert's ask.
- Never write a sentence that hands the employer a reason to filter the applicant out. No "although I lack", no "while my background is not in", no "I would need to get up to speed on".
- If the advert asks for something they genuinely do not have, raise it with the user directly in chat, after the draft. Never in the document.
- Lead with the closest match to the advert's top requirement, not with a career summary.
- Three or four short paragraphs. No "I am writing to apply for". No "I was excited to see".
- Concrete over adjectival. "20+ registries across four markets" beats "extensive experience".
- No em dashes.

## Method

1. Read the advert properly. Pull out its top five requirements in the employer's own words, and note which are hard requirements versus nice to have.
2. Map each to specific evidence from their history. Where there is no evidence, leave it out. Do not stretch, do not upgrade a title, do not widen the scope of a piece of work beyond what actually happened.
3. Mirror the advert's vocabulary in the CV. If they say "stakeholder management" do not write "partner alignment". ATS parsers match literally.
4. Reorder and rewrite the CV bullets so the strongest matches sit highest in each role. Rewriting is fine, adding responsibilities they did not have is not.
5. Write the cover letter to the top two requirements only. A letter that covers everything covers nothing.
6. Output as .docx unless told otherwise. Single column, standard headings (Experience, Education, Skills), no tables, no text boxes, no graphics, nothing load-bearing in headers or footers. ATS parsers drop all of it.
7. After delivering, tell the user in chat what the advert asked for that the documents could not evidence, and how big a problem it looks. That conversation belongs in chat, never in the application.

## Output

Two files, named `CV_<Company>_<Role>.docx` and `CoverLetter_<Company>_<Role>.docx`. Then a short chat note covering the gaps, anything in the advert worth asking about at interview, and an honest read on fit. Direct, no cheerleading.
