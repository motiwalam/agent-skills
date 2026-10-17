---
name: writing
description: |
  Universal writing rules for every piece of text you produce: chat replies,
  docs, READMEs, code comments, log and error strings, commit messages, and PR
  descriptions. Plain words, short sentences, no AI tells, ASCII only, and
  comments only where the code cannot speak for itself. Must always apply.
---

# Writing

Apply these rules to all text you write or edit. Each section below adds
targeted rules for one kind of text. The general rules still apply there.

Write for a tired reader who is not a native English speaker. Each sentence
must survive one read.

## General rules

### Say the thing

- State the point directly. Skip contrast framing such as "not just X, but Y"
  or "X, not Y" when the reader never mentioned Y.
- Say what a thing does, with the mechanism or a number. "A column rename fails
  the build" beats "types that follow your schema". If a sentence could appear
  unchanged in another project's docs, it says nothing about this one. Cut it.
- Be specific. Name the source, the file, the count, the time. Delete vague
  attributions such as "experts believe" or "some argue".
- Give plans and facts in place of generic conclusions. Avoid saying things like
  "the future looks bright".
- If you made an assumption, say so. When a choice has trade-offs, lay them out
  and let the reader decide. Do not present a guess as a fact.

### Keep it short and simple

- Prefer simplicity in structure and in words.
- One idea per sentence. If the reader must backtrack to parse a sentence,
  split it.
- Sentence limits: 20 words for instructions, 25 words for explanations.
  Identifiers, commands, and numbers with units count as one word.
- Paragraphs: one topic, six sentences at most.
- Keep articles and "that". Short sentences with complete grammar beat
  telegraph style. "Make sure that the file exists before you run the
  command" beats "Ensure file exists before running."
- Break noun chains longer than three words with prepositions. "The timeout
  value for the connection pool" beats "the connection pool timeout
  configuration value".

### Instructions versus explanations

- Instructions use the imperative: "Run the migration."
- One instruction per sentence.
- Put the condition first, with a comma: "If the build fails, read the log."
  Readers and models drop trailing conditions.
- Explanations use simple present or simple past. Do not mix imperatives into
  them.
- For requirements, write "must". For possibility or permission, write "can".
  Avoid "should", "may", "might", and "could". A model reads "should" as
  optional.

### Active voice and strong verbs

- Name the actor. "The compiler validates queries" beats "queries are
  validated". Passive is fine only when the actor is unknown or irrelevant.
- Use a verb for an action. "Compress the file" beats "perform compression of
  the file".
- Cut adverbs, or pick a stronger verb. "Significantly improves" becomes the
  measured delta.
- Avoid present perfect in reports. "The deploy at 14:00 removed the cache
  warmup" beats "we have identified an issue".

### One term per concept

Pick one word for each concept and use it everywhere in the document. Common
rotations to collapse:

- check / verify / confirm / validate / ensure
- config / configuration / settings / options
- run / execute / invoke / launch
- error / issue / problem / failure

### Plain words

| Write this | In place of |
|---|---|
| use | leverage, utilize |
| to | in order to |
| before | prior to |
| because | due to the fact that |
| if | in the event that |
| help | facilitate |
| many | numerous, plethora, myriad |
| you can | enables you to, allows you to |
| is, has | serves as, stands as, boasts, features |
| by default | out of the box |
| internally | under the hood |
| for example, that is | e.g., i.e. |
| (name the items) | etc. |
| (say what it does) | gracefully handles, is designed to, aims to |
| (delete) | it is worth noting that, it is important to, simply, just, easily, seamlessly, robust, powerful, comprehensive |

Replace abstract metaphor nouns with the concrete word: substrate -> base,
wedge in -> add, vector -> way, surface -> API, north star -> goal,
gold-plating -> more than the job needs, endgame -> last phase.

### Do not compress ideas into compound words

Do not compress concepts, behaviors, or clarifying descriptors into compound
nouns or compound adjectives. Write them out in natural language.

Avoid: "The top-of-handler cache-hit early return is skip-as-success, not an
error path; the after-retry return is what lets the request succeed."

Write: "The handler returns early when the cache already has the value; this
counts as a success. Otherwise, the request succeeds when it reaches the
return after the retry loop."

### AI tells to remove

- Puffery: "pivotal", "testament to", "evolving landscape", "indelible mark".
- AI vocabulary: additionally, crucial, delve, enhance, fostering, garner,
  interplay, intricate, showcase, tapestry, underscore, vibrant.
- Superficial "-ing" tails: ", highlighting...", ", ensuring...",
  ", showcasing...". Delete them or make a new sentence with a real subject.
- Forced groups of three. Use the natural count.
- Synonym cycling to avoid repeating a word. Repeat the word.
- Hedge stacks: "could potentially possibly" becomes "can", or state what is
  known and say "unknown" for the rest.
- Chatbot phrases: "Great question!", "Certainly!", "I hope this helps!",
  "Let me know if...". Respond directly.
- Formatting tells: em dashes, colons used as mid-sentence connectors, bold on
  every term, "**Label:** label restated" bullets, Title Case Headings,
  decorative emojis. Use sentence case headings. Separate thoughts with a
  period or a comma.

### Voice

Sterile text is as obvious as slop. When the format allows it, have an opinion,
vary sentence length, and use "I" where it fits. Technical docs, comments, and
commit messages stay neutral and factual.

### Leave these exactly as they are

Code, inline code, identifiers, commands, flags, file paths, config keys,
quoted error messages and log lines, and product names.

## ASCII only

Use only ASCII characters in everything you write: prose, comments, log and
error strings, commit messages, and PR descriptions. Replace common non-ASCII
characters as follows:

| Character | Write instead |
|---|---|
| em dash (U+2014), en dash (U+2013) | a period or comma in prose, a hyphen `-` in code text |
| right arrow (U+2192) | `->` |
| left arrow (U+2190) | `<-` |
| double arrow (U+21D2, U+2194) | `=>`, `<->` |
| curly quotes (U+2018, U+2019, U+201C, U+201D) | straight quotes `'` and `"` |
| ellipsis (U+2026) | `...` |
| multiplication sign (U+00D7) | `x` or `*` |
| plus-minus (U+00B1) | `+/-` |
| degree sign (U+00B0) | `deg`, or the unit name such as `degC` |
| micro sign (U+00B5), Greek mu (U+03BC) | `u`, as in `us` or `uA` |
| less/greater or equal (U+2264, U+2265) | `<=`, `>=` |
| check mark, cross, emoji | words such as "done", "failed", "yes", "no" |
| non-breaking space (U+00A0) | a normal space |

Exception: use a non-ASCII character when the user explicitly asks for it.
Examples are user-facing copy that needs a specific glyph, localized strings,
or a test that exercises Unicode handling. Keep the exception to that text
only. Everything around it stays ASCII.

These rules cover text you write. When you edit a file, leave non-ASCII text
that was already there, such as degree or micro signs in existing comments,
unless the user asks you to clean it up.

## Code comments

- Write a comment only when the code is not readable by itself, or the context
  is truly non-obvious: a subtle invariant, an external constraint, a dangerous
  footgun, or the reason for an unusual choice.
- When unsure whether a comment is needed, leave it out. A missing comment is
  easy to add later. A comment that restates the code is noise.
- Match the local commenting standard. If similar sections in the file or repo
  follow a convention, follow it over any rule here.
- Keep comments concise. Use enough punctuation to be clear, and no more.
- Do not write comments that go stale after merge: "we added X for the Y
  migration", "new in this PR", "changed from Z".
- Do not restate the field, function, or variable name.
- Reference an issue number only when there is a specific story behind the
  code, such as an edge case or a surprising workaround. Never add one by
  default.

Delete:

```go
// increment i
i++
```

Keep:

```go
// The vendor API rejects batches over 500, so we chunk here.
for _, batch := range chunk(items, 500) {
```

Keep, with an issue number, because the behavior is surprising:

```go
// Keep the stale value for one extra cycle. Removing it caused the
// flapping in #1234.
return cached
```

### Config and YAML comments

The same rules apply to YAML and other config. For multi-cluster or multi-env
values (Helm values, shared config namespaces, Argo overlays):

- Comment only deviations from the normal pattern: extra quota, a non-zero PVC
  or NodePort, test-only headroom, a temporary exception.
- Do not comment the default path ("operator only", "same as staging").
- If one env needs a long reason, put it only in that env's values file. Do not
  copy it to every sibling.
- If a field is zero or omitted because the global default already means zero,
  do not restate that in a comment.
- Before you add a comment, ask: would deleting it change what a reader must
  know? If not, delete it.

## Log and error strings

- ASCII only, concise, no exclamation marks, no apologies.
- Error messages state what happened, the cause if known, and the fix as an
  imperative.

Before: "Oops! Something went wrong while attempting to connect. Please ensure
your credentials are properly configured."
After: "Connection to the database failed. The server rejected the password
for user `app`. Set `DB_PASSWORD` and connect again."

## Commit messages

- Follow the repo's existing format first (scope prefix, conventional commits,
  and so on). Check `git log` before you write.
- Subject: imperative mood, about 50 characters, 72 at most, no trailing
  period. "Add retry to the uploader" beats "Added retries" or "Fixes".
- Leave a blank line between the subject and the body.
- Body: wrap at 72 columns. Explain why the change exists and what it changes
  at a high level. The diff already shows how.
- Use plain past or present facts in the body. No filler such as "This commit
  aims to".
- Reference an issue only if the repo convention or the story needs it.
- Keep one logical change per commit.

```
Chunk vendor uploads into batches of 500

The vendor API started rejecting requests over 500 items, which broke
nightly syncs for large accounts. Split the upload into fixed-size
batches and retry each batch on its own.
```

## PR descriptions

- Follow the repo's PR template if one exists.
- Lead with what the PR does and why, in one to three sentences. Delete "This
  PR aims to".
- Then list the changes a reviewer needs to know about. Skip what the diff
  makes obvious.
- Say how you tested it: the commands you ran and what they showed. If you did
  not test something, say so.
- Call out risks, limits, follow-ups, and anything the reviewer must decide.
- Link the related issue once, where the template or repo convention puts it.
- Keep the title in the imperative, like a commit subject.
- No decorative emojis, no marketing tone, ASCII only.

```markdown
Chunk vendor uploads into batches of 500

The vendor API now rejects requests over 500 items, which broke nightly
syncs for large accounts.

## Changes
- Split `Upload` into fixed-size batches with per-batch retry.
- Add `upload.batch_size` (default 500).

## Testing
- `go test ./uploader/...` passes, including a new 1,200-item test.
- Ran a sync against staging account 42 (3,100 items), no rejections.

## Risks
- Large syncs now make more requests. Rate limits are unchanged.
```

## Self-check before you deliver

1. Search the text you wrote for non-ASCII characters. Replace each one unless
   the user explicitly asked for it or it was already in the file.
2. Read the three longest sentences. Split any over 20 words (instructions)
   or 25 words (explanations).
3. In instructions, search for "should", "may", "might", "could", "has been",
   "have been", and ", ...ing". Fix each hit. Keep "might" or "could" where
   it reports real uncertainty, so a guess does not read as a fact.
4. In instructions, find each condition that trails its command. Move it to
   the start of the sentence. Leave "if" and "when" alone where they start a
   noun clause, as in "ask if the build passed" or "log when the job ran".
5. Check that each concept uses one term throughout.
6. For each comment you added, ask whether the code already says it. Delete
   the ones that do. Leave existing comments alone unless the user asked for
   a comment cleanup.
7. Ask: "What makes this obviously AI-generated?" Fix what you find.
