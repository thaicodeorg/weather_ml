---
type: source
created: {{date}}
tags: []
status: seed
source_type: pdf
origin:
author:
published:
retrieved: {{date}}
immutable: true
---

# {{title}}

<!-- Verbatim content only. Never edit the material below this line. -->

<!--
Sources/ is the vault's immutability boundary. A source note records what a
document said, unaltered, so that every claim built on it can be traced back.
Corrections, disagreements and summaries do not belong here; they belong in a
literature note or a permanent note that cites this one.

  · `source_type` is one of pdf, url, youtube, report. It decides how the body
    below is captured, not what the document is about.
  · `origin` is where the content came from: a URL, or the vault-relative path
    of the file. Never a wiki-link to a note.
  · `author` is who published it. If the clipper recorded a channel, that is the
    author; if it recorded nothing, leave the field empty rather than guessing.
  · `published` is when it was published, not when you clipped it. Leave empty
    if only a retrieval date is known.
  · `retrieved` is when this copy was captured.
  · `immutable: true` is not optional. The validator rejects a source note that
    disclaims it.

Worked example, from the Hugging Face paper page already clipped in Sources/URL/:

    ---
    type: source
    created: 2026-09-26
    tags: []
    status: seed
    source_type: url
    origin: https://huggingface.co/papers/2412.15832
    author: ECMWF
    published: 2024-12-21
    retrieved: 2026-09-26
    immutable: true
    ---

    # AIFS-CRPS paper page

    <the clipped page, byte for byte, exactly as it was captured>
-->
