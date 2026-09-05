# Rule: Environment, Limits, and What Not to Work Around

Applies to every task. Short, and none of it is negotiable.

## Never circumvent a technical protection

If a file will not open with ordinary tools, **stop and report it**. Do not
route around the obstacle.

Specifically forbidden, whatever the reason and however small the immediate
goal:

- decrypting or removing DRM, owner passwords, or permissions encryption from
  any document;
- patching, monkey-patching, or replacing a library's cryptography layer;
- loading system crypto libraries directly to reimplement a cipher;
- stripping copy, print, or extraction restrictions;
- bypassing a licence check, paywall, or access control of any kind.

This holds even when the task is trivial, even when you are only reading
metadata, even when the file is the owner's own copy, and even when the
protection looks like a formality. The size of the goal does not license the
method. If verifying a title page requires defeating encryption, the correct
output is one sentence: *"`topbook.pdf` is encrypted and I could not read it
with standard tools — please confirm its title, or provide an unprotected
copy."*

The reference books carry copyright notices, and Morris carries an explicit
no-reproduction notice. Treat every one of them as a book you are allowed to
read and not allowed to break into.

Reading a scan by rasterising pages and running OCR is **not** circumvention —
that is ordinary reading of an unprotected file, and it is fine.

## Stay inside the workspace

Read and write only within the workspace directory. Everything you need is
here by design.

Specifically forbidden:

- reading or parsing agent, IDE, or system logs — `~/.gemini/`, any
  `transcript.jsonl` or `transcript_full.jsonl`, any `brain/` or session
  directory, crash dumps, telemetry;
- recovering your own prompt, context, or earlier instructions from any log,
  cache, or history file;
- writing outside the workspace, including to `/tmp`;
- reading the user's home directory, shell history, browser data, keychains,
  SSH keys, or credential stores.

**If you cannot see part of your instructions, say so and ask for them again.**
That is one sentence and it costs the user five seconds. Reconstructing a
prompt out of a session log is not resourcefulness — it is reaching into a
place you were not given, and those logs may hold material from other sessions
and other work that has nothing to do with this project.

The same applies to any obstacle: a truncated prompt, a missing file, an
ambiguous instruction, a tool that will not run. **Ask. Do not reconstruct, do
not infer from artefacts, do not route around.**

## Do not delete the user's files

Never `rm` anything you did not create in this session, and never `rm -rf` a
directory the user placed in the workspace — not to tidy up, not after
confirming it is a duplicate, not because it is obsolete. Say what you believe
is redundant and why, and let the user remove it.

Files you created yourself in `build/tmp/` are the exception; clean those up as
described below.

## Do not rewrite the record

Build reports in `build/reports/` record what a given build actually did. They
are the user's audit trail. If a later session changes a page, write that
change into the *new* session's report or append a dated note — never edit an
earlier report so that it describes work done afterwards. A report that has
been retroactively made accurate is no longer evidence of anything.

## Clean up what you extract

Page images, OCR intermediates, and converted text from the reference books are
working artefacts, not deliverables. Delete them from `build/tmp/` as soon as
you are done with them. Never leave extracted pages of a copyrighted book
sitting on disk, and never move one outside `build/tmp/`.

## Never duplicate the source material

Transcripts and reference books live in exactly one place:
`source/<course>/`. If they are somewhere else in the workspace, **move**
them, do not copy. Two copies of a 75MB library is not a tidy-up, it is a
second thing to keep in sync and a second thing to accidentally commit.

If the workspace root is not the repository root — if you find yourself adding
exclude entries for folders like `Downloads` or a duplicated kit directory —
stop and tell the owner the workspace is in the wrong place. Do not build
around it.

## When a tool is missing

If Jekyll, Ruby, a gem, or any other dependency is absent or the sandbox
refuses a write:

1. Say so plainly, with the verbatim error.
2. Give the one command the owner should run to fix it.
3. **Do not claim the step succeeded**, and do not substitute a different check
   for the one you were asked to perform.
4. Continue with whatever else you can do, and list what remains blocked.

A failed build reported honestly is a good outcome. A failed build reported as
"complete" is the worst outcome available.

## Never invent an identifier

Email addresses, URLs, dates, lecture numbers, author names, section numbers.
If you do not have it, leave the field empty, put a `TODO` in the build report,
and ask. An address derived from a GitHub username is a guess wearing a
disguise.

## Scope discipline

When a step turns out to be far harder than it should be, that is a signal to
check whether you have the right approach — not a licence to escalate. Fifteen
tool calls spent on a step that should have taken one is itself the error
message. Stop, report the obstacle, and ask.
