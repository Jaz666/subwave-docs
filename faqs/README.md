# Frequently asked questions

Quick answers for the questions that come up while setting up and tuning a
SUB/WAVE station. For exact controls and setup steps, use the
[official SUB/WAVE documentation](https://github.com/perminder-klair/subwave/tree/develop/docs).

## DJ links and factual grounding

### Will factual grounding make my DJ sound robotic?

No. It gives the DJ a boundary for factual claims, not a script. It can still
react, be warm, make an observation or simply say less. The difference is that
it should not turn a plausible guess about an artist, record or moment into an
on-air fact. Read [Safer, more natural DJ links](../updates/grounded-dj.md).

### Why has the DJ stopped adding trivia it probably knows?

Because a fact that happens to be true is not always a fact that has been
supplied and verified for that link. Keeping music and programme claims within
the current context makes a station more trustworthy. A personal reaction is
still welcome; an invented release date or biography is not.

### Will every link become a fact-filled introduction?

No. Supplied facts and Sleeve Notes are optional material, not a checklist. A
short, natural link—or no extra commentary beyond what the task needs—can be
the better radio moment.

### What are Sleeve Notes? Do I need to write them myself?

Sleeve Notes are optional, bounded track-related material that can give a DJ
something useful to say. They may include supplied album, year or station
history context. You do not need to create them for every record, and they do
not require the DJ to use every detail. Read [Sleeve Notes: richer links between
records](../updates/sleeve-notes.md).

### Can Sleeve Notes replace a show brief or a DJ Soul?

No. Sleeve Notes concern this record and this link. A Soul shapes who the DJ
sounds like; a show brief explains the programme and listener moment.

## Smarter track selection

### What is a Track Shortlist?

It is a set of eligible candidate tracks assembled by SUB/WAVE before the DJ
makes the final editorial choice. The shortlist can draw from context,
continuity and exploration, while show rules, safety and variety rules still
apply. Read [Smarter track selection](../updates/smarter-track-selection.md).

### Does a shortlist take choice away from the DJ?

No. It moves the broad search for eligible music out of the DJ model, then asks
the DJ to make one considered choice from the resulting candidates. That gives
the DJ a clearer editorial decision rather than a long sequence of tool calls.

### Is a bigger shortlist always better?

Not necessarily. More passes give the DJ more candidates and can help
discovery, but each extra pass adds roughly up to a second to constructing the
shortlist. A larger final choice can also take longer for the DJ model to
consider, depending on your LLM setup. Start with the default and increase
only when the extra range is useful for that show.

### What happened to the Agentic Picker?

For ordinary track selection, the native shortlist now does the discovery work
and leaves one final choice to the DJ. The Agentic Picker remains in SUB/WAVE
for now because the shortlist does not yet cover the listener-request agent.

### Does this mean my AI model no longer needs to support tools?

That is the direction of travel for normal track selection, but it is not the
right time to change your LLM setup. Keep your existing tool-capable model
configuration while the listener-request path still uses the Agentic Picker.

### Will a listener hear why a record was shortlisted?

No. The private selection reason in the Booth Log explains the DJ's choice for
you; it is not on-air copy. The listener hears a natural link grounded in the
context for that moment.

### What are Musical Leanings?

They are a DJ's soft preferences for close calls in a shortlist: for example,
an overlooked album track over the familiar hit, or a gentle melodic choice for
a particular morning show. They do not override show filters, safety or variety
rules. Read [Giving your DJ Musical Leanings](../field-guide/giving-your-dj-musical-leanings.md).

### Should I name favourite artists in Musical Leanings?

Usually no. A list of artists sounds specific but does not reliably create the
selection behaviour people expect. Describe the musical qualities and the
tie-break you want instead. If certain artists truly must appear, use the
station's playlist and show settings to make that requirement explicit.

## Building a station voice

### What is the difference between a Soul and a show brief?

A **Soul** is casting: how this DJ notices music, talks to listeners and uses
restraint. A **show brief** is programming: what the show is for, who it meets,
how it should move and what makes that hour distinct. See [Writing a great DJ
Soul](../field-guide/writing-a-great-dj-soul.md) and [Writing a great DJ brief](../field-guide/writing-a-great-dj-brief.md).

### How much should I put in a Soul or show brief?

Enough to create useful choices, but not a biography, a playlist and a rulebook
all at once. A Soul needs a clear voice and point of attention; a brief needs a
listener moment, a programme promise and any meaningful boundaries. If it
cannot be summarised in a few plain sentences, divide the job between the
right settings instead of adding more prose.

### Why do all my DJs still sound similar?

First check whether their Souls actually give them different points of view,
not merely different lists of favourite artists. If the similarity is across
the whole station, also check whether a shared system prompt or house rule is
over-specifying the delivery.

### Should I write a custom system prompt straight away?

Usually no. Start with the built-in default and tune the DJ's Soul, show brief,
Musical Leanings and show settings first. Customise the shared prompt only for
a genuine station-wide behaviour you can hear and describe. Read [Customising
your system prompt and house rules](../field-guide/customising-your-system-prompt-and-house-rules.md).

### What are station house rules for?

House rules are the stable, universal constraints that apply to every spoken
output: for example, factual discipline, how presenters refer to listeners, or
whether performance cues are allowed. They are not the place to put one show's
music policy or one DJ's personality.

## Tuning and review

### How do I know what to change after a surprising pick or link?

Do not react to one moment. Read or listen to a short run in the Booth Log,
identify a repeatable pattern, then change the setting layer that owns it:
Soul for voice, brief for programme shape, Leanings for close calls, settings
and filters for musical territory, or shared rules for station-wide spoken
behaviour. Read [Learning from the Booth Log](../field-guide/learning-from-the-booth-log.md).

### Why does the private selection reason not sound like the link I heard?

They serve different audiences. The reason is private editorial context for
understanding a choice; the link is the DJ speaking to listeners. A concise
link is not missing anything simply because it does not explain the selection.

### How often should I retune a show?

Review after enough listening to see a pattern: a few comparable moments over
several days is more useful than a single transition. Make one small change,
then listen again before changing another layer.

## More help

- [Update pages](../updates/README.md) explain the recent changes.
- [Operator Field Guide](../field-guide/README.md) covers the longer-term
  craft of building and tuning a station.
- [Official SUB/WAVE documentation](https://github.com/perminder-klair/subwave/tree/develop/docs) covers exact product setup.
