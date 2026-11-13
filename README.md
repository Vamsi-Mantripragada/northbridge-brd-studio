# BRD Studio (BRD Assistant)

A tool that helps a Business Analyst turn a change request into a checked, signed-off Business Requirements Document.

**The AI drafts. Code enforces the checks. People decide.** Requirements follow IEEE 29148 principles and EARS wording.

Status, 12 November 2026: Key facts use the standard checklist (12 core checks + 3 banking extras), with gap questions answered on the same tab; one requirement per business rule (CR-201 retest: 10 requirements, all 8 expected rules covered, versus 4 before); fairer quote check; colour dots on every list; "All done" notes; one document per BRD. Not yet tested on the new build: sections, checker, sign-off, change flows. How it works: `docs/How_BRD_Studio_Works.pdf`. Next changes: `docs/feedback_for_next_build.md`.

Earlier status, checkpoint 11 November 2026: all 9 tabs are built: Document (hides personal data), Key points, Questions, Glossary, Requirements, BRD sections, Check (Gemini), Sign-off (Word and Jira files) and Full picture with history. Tested by hand on BRD-102 up to the Sign-off checklist and the Word and Jira files. Sign-off is recorded by the BA once the approver has signed off (for example, by email); the approver signing in comes with hosting. Word and Jira files are saved to My Drive > northbridge_brd > exports, because Colab download links do not open. Above every tab the app shows the problem the BRD solves and a "How it all links" table (change request line to requirements to sections), so the user never loses the main change request; the same table is in the Word file. Sign-off lists every open item, and clicking one opens it on its tab. Password is off for testing. Fake data only.

## What is here

| Folder | Contents |
|---|---|
| `code/` | The 21 database tables, the sample and trace test, and the Gradio screens |
| `tests/` | AI tests and their marking |
| `docs/` | UX design, data model, traced example, ER diagram, clickable prototype |
| `samples/` | Fake documents used in the tests |
| `old/` | Earlier checker code, kept for reference |
| `checkpoints/` | Dated copies of working screen code |

## How to run

Everything runs in Google Colab, one file per cell.

1. In Colab Secrets, add `GROQ_API_KEY`, `GEMINI_API_KEY` and `BRD_DEMO_PASSWORD` (a made-up password), with Notebook access on.
2. Run `code/01_create_tables.py`.
3. Run `code/02_sample_and_trace_test.py`.
4. Run any file in `tests/`.
5. Run `code/app_screens.py` for the screens. Sign in as `admin`.

**Never put API keys, passwords or real customer data in any file.**

## Test results, 10 November 2026

| Test | Result |
|---|---|
| Find checklist items, new document with a trick line | 8 of 8 |
| Write requirements with sources | 10 of 10 |
| Gemini checker with planted mistakes | 5 of 5 |
| Write a section and link paragraphs | 8 of 8, after a fix |
| 21 tables store and trace | 8 of 8 |
| AI output saved to tables and traced | 10 of 10 |

These are small fake examples. The real screens were tested by hand on one small fake document (BRD-102), from upload to the Sign-off checklist and the Word and Jira files. Long documents and the full flow are still to be tested. The AI can word requirements differently on each run, so a person must read every run.

Keep this repository private.
