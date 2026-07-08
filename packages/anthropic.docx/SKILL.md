# Word Documents (docx)

Use this skill whenever the user wants to create, read, or edit Word (.docx) documents.

## When to use
- Producing a report, memo, letter, or template as a .docx.
- Formatting: table of contents, headings, page numbers, letterhead.
- Extracting or reorganizing content from existing .docx files.
- Find-and-replace, tracked changes, comments, image insertion.

## How
Use the python-docx library (or docx tooling) to build the document programmatically. Preserve existing structure when editing; only change what the request requires. Return the path to the written .docx.

Do NOT use this for PDFs, spreadsheets, or Google Docs.
