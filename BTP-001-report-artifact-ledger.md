# BTP-001 Report Artifact Ledger

Scope: identity and integrity of the three artifacts tied to the KCN BTP-001 Bootstrap & Benchmark Report. This ledger does not record the sign-off decision, signature verification, or ratification. Those are tracked in the sign-off document.

Repository: Evank253/kcn-btp001-report
Pinned commit: af8ccdf298aa256230f8ce1138f2a8ac56d72220

Labels: MEASURED = computed by Claude in its sandbox on 2026-10-17. REPORTED = stated by another party; not observed by Claude.

## Artifact 1: HTML report

Path: KCN_BTP001_Benchmark_Report.html
Size: 7,776 bytes
SHA-256: ea1b74d9ebebbd39dc256d094cf997472da15e7cb908773dd265584c649deb75
Git blob: ab84e51d92d2a8379d4b8bdf534227b0a4778423

- MEASURED 2026-10-17T15:23:56Z: raw.githubusercontent.com at the pinned commit returned HTTP 200, 7,776 bytes, the SHA-256 above.
- MEASURED: `git cat-file -p ab84e51d` gives the same bytes and digest. The pinned commit's tree entry for the path is that blob.
- REPORTED: GitHub connector retrieval (ChatGPT) gave 7,776 bytes and the same digest.

Discrepancies, retained:
- `0ff2f177…` is not this file. It is the SHA-256 of the file with all 3 `&amp;` replaced by `&` (7,764 bytes, full digest 0ff2f17792a2203ff4efebc7bb8c452268b0f90176fabcad208ded8b9a49e3d6). MEASURED.
- `1f91f65a…` appears in the pinned commit's message as the HTML SHA-256. UNREPRODUCED. It is not the SHA-256 of any of the 5 blobs in the repository's history. It matched none of about 15 simple transforms (newline, CRLF, BOM, dash and entity variants). That test was not exhaustive.
- The HTML header reads "Commit: a6e3445". The file is committed in af8ccdf. By the af8ccdf commit message, a6e3445 wrote broken placeholder content.
- Branch fork, MEASURED 2026-10-17: `main` is at a6e3445b0097bd3ec4c7c36bdfe0255e44d67dac and still serves the placeholders (HTML 57 bytes, PDF-slot file 56 bytes). `Python-3` is at af8ccdf298aa256230f8ce1138f2a8ac56d72220 and holds the files recorded in this ledger; a fresh clone checks it out. A branch URL on `main` therefore returns different bytes. Cite commit or blob SHAs, not branch URLs.

## Artifact 2: PDF-generation note (text, not a PDF)

Path: KCN_BTP001_Benchmark_Report.pdf (at the pinned commit)
Size: 618 bytes
SHA-256: 88267f4e926dde1dec5190ea6cb11a028b350a61f3bc496b0dd30dc10424f89f
Git blob: c6bc2c8ac211aa720fcf4274066b0bd1a8c3a14d

- MEASURED: ASCII text, begins "PDF GENERATION NOTE", no `%PDF` header. It describes a WeasyPrint command and a browser print-to-PDF route.
- The file sits at a `.pdf` path although it is text. The rendered PDF (Artifact 3) is committed at a different path so the two do not collide. Cite the pinned commit and blob above, not the branch tip.

## Artifact 3: Rendered PDF

Path: KCN_BTP001_Benchmark_Report-rendered.pdf
Size: 27,433 bytes
SHA-256: d56bd7a376ba34f102e2070ec1a8f13b54e2102fe51207a43c09dab68b03622f
Git blob: a806f286a77b42eb03da6b8b61837413eadcb9f1
Format: PDF 1.7, 4 pages, A4, fonts embedded

- MEASURED: generated 2026-10-17 (about 15:36 UTC) in Claude's sandbox with WeasyPrint 70.0, from the bytes of Artifact 1 (digest verified before rendering). `HTML(filename=…).write_pdf(…)` was used, not the note's `file:` one-liner.
- NOT REPRODUCIBLE: a second run gave 27,432 bytes and a different digest. The digest identifies only this exact file.
- Preservation location: Evank253/kcn-btp001-report, at the path above, committed together with this ledger. The commit SHA is not recorded here because a commit cannot contain its own SHA; it goes in a follow-up entry.
- Retrieval of the committed copy: NOT_MEASURED until a raw-URL fetch at that commit is recorded and its size, SHA-256 and blob SHA are compared to the values above.
- MEASURED text comparison against Artifact 1: 776 words vs 763; word-sequence similarity 0.98; key figures (149, 0.895, AAA-plus, 0.98, 737, 17,964, 0.018, FED-010, PROPOSED, NOT_MEASURED) occur equally often in both. Of 19 differing spans, 15 were inspected (whitespace, one hyphenation break, bullet glyphs). 4 were not inspected.
- Renders in Liberation Serif, not the declared Georgia.
- REPORTED: another assistant confirmed the same size and digest from the transferred file.

## Rules

1. Each artifact keeps its own size, digest and provenance. Digests are not interchangeable.
2. A digest match shows byte identity with the compared bytes. It does not show authorship, authorization, or that the reported benchmark results are correct.
3. The report's content is frozen as of af8ccdf and still reads PROPOSED and NOT_MEASURED for BTP-001. Editing the HTML changes its digest. Any update should be a new commit with a new record, and this entry should be kept.
4. Discrepancies stay recorded until reproduced or explained.
