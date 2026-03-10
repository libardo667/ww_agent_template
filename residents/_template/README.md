# residents/_template/ — New Resident Template

Copy this entire directory to create a new resident:

```bash
cp -r residents/_template residents/your_character_name
```

Then edit the three identity files:

1. `identity/SOUL.md` — Who this person is (disposition, habits, personality)
2. `identity/IDENTITY.md` — Name, vibe, emoji
3. `identity/tuning.json` — Loop timing and personality parameters

The runtime directories (memory/, letters/) are created automatically by the
daemon on first run. You don't need to populate them.

## Directory Structure

```
{name}/
├── identity/
│   ├── SOUL.md           ← Edit this: personality kernel
│   ├── IDENTITY.md       ← Edit this: name and metadata
│   └── tuning.json       ← Edit this: loop timing parameters
├── memory/
│   ├── working.json      ← Auto-created: rolling event buffer
│   ├── provisional/      ← Auto-created: fast loop scratchpad
│   │   └── archived/     ← Auto-created: processed impressions
│   └── long_term/        ← Auto-created: curated memories
├── letters/
│   ├── drafts/           ← Slow loop stages drafts here
│   │   └── sent/         ← Mail loop moves sent drafts here
│   ├── inbox/            ← Incoming letters land here
│   │   └── read/         ← Mail loop archives read letters here
│   ├── letter_5.md       ← Penpal letters (every 5 turns)
│   └── letter_10.md
├── decisions/
│   └── decision_N.json   ← Slow loop decision log
├── turns/
│   └── turn_N.json       ← API response archive
├── session_id.txt        ← Auto-created on first bootstrap
└── world_id.txt          ← Set by daemon from server
```

## Character Design Tips

**The fast loop makes them reactive.** Low cooldown + low act_threshold =
someone who reacts to everything. High cooldown + high threshold = someone
who rarely notices what's happening around them.

**The slow loop makes them thoughtful (or not).** Low impression_threshold =
someone who reflects on every small thing. High threshold = someone who
only reflects when a lot has happened. Short fallback = frequent unprompted
reflection. Long fallback = only thinks when forced to.

**The mail loop makes them social (or not).** Enabled with low send_delay =
someone who writes back immediately. High discard_threshold = someone who
almost sends things but decides not to. Disabled entirely = a recluse who
never writes.

**SOUL.md makes them who they are.** Everything else is just timing. A
character with identical tuning but a different SOUL.md is a completely
different person. And a character with identical SOUL.md in a different
world is recognizably the same person. That's the test.
