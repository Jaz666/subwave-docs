# Smarter track selection

Choosing the next record is a two-part job. First, the station needs to find
music that is genuinely eligible: it must fit the show, respect your library
rules, avoid unwanted repeats, and make sense after what is playing now. Then
someone needs to make an editorial choice from those valid options.

SUB/WAVE now makes that division clearer. It builds a **Track Shortlist** from
your station's eligible music, then gives the DJ the final choice. The result
is a better balance of safety, variety and taste: the station keeps its rules,
while the DJ still chooses the record.

## Why the picker changed

The earlier **Agentic Picker** asked the DJ model to do the whole job in one
conversation: decide where to search, make one or more library searches,
inspect the results, and choose the next track. It was flexible and capable of
following a promising line of discovery, which remains a valuable quality in a
music station.

Its trade-off was that every additional search kept the model in the loop. Tool
definitions, search results and previous turns accumulated while the model was
still trying to discover music. More discovery could mean a better field of
choices, but it could also mean a longer wait and a much larger prompt before
the DJ made its final decision.

Track Shortlisting moves the repeatable discovery work into native controller
code—normally running on the controller's CPU. It uses the same station rules
and library sources to build the eligible field, then makes one final model
call for the DJ's editorial choice. The aim is not to remove judgement from the
DJ; it is to spend the model's attention on the judgement only it can make.

## Early local benchmark results

<img width="941" height="1672" alt="First Benchmarks" src="https://github.com/user-attachments/assets/f1ae5b20-77cd-49af-a817-074c5ebac822" />

On a locally hosted SUB/WAVE station using a modest GPU and a Meta Llama 3.1
8B Q5_K_M model, the first live samples showed a substantial improvement:

| Discovery passes | Agentic Picker | Native Shortlist | Result |
| --- | ---: | ---: | --- |
| 3 | 27.0 s · 24.3k tokens | 15.4 s · 6.5k tokens | 43% faster · 73% fewer tokens |
| 4 | 47.0 s · 31.9k tokens | 14.3 s · 9.4k tokens | 70% faster · 70% fewer tokens |
| 5 | 92.3 s · 37.2k tokens | 19.4 s · 11.5k tokens | 79% faster · 69% fewer tokens |

Across those runs, the native path used about **70% fewer tokens** on average.
It also made wider discovery practical without repeatedly waiting for the model
between searches.

These are early local benchmarks, not a universal performance promise. Actual
times depend on your library, the number of shortlist passes, model, hardware,
context-window settings, and whether your model runs locally or in the cloud.

## What the live comparisons show

Paired three-pass comparisons showed that the shortlist can keep the useful
range of discovery: contextual sources such as a show's mood or playlist,
continuity with the track on air, and an exploratory source such as deep cuts
or a wider library draw. In those tests, both paths completed without needing
the Backup selection.

They did not always choose the same record—and they should not be expected to.
Several eligible records can make sense after the same track. The important
test is that the shortlist preserves valid, varied options and leaves the DJ
with a genuine editorial decision, rather than mechanically reproducing one
previous tool trail.

## What listeners will notice

Listeners should hear a station that feels more intentional without becoming
predictable. The DJ is choosing from real possibilities that already fit the
moment, rather than trying to search the whole library and make an on-air
decision in one step.

That means the next track can preserve continuity when a show needs to hold a
thread, make a change when variety matters, or take a well-timed step into less
familiar territory. The shortlist is not an automatic queue and it is not a
playlist in disguise. It is a working selection of records the DJ may choose
between.

## How a Track Shortlist works

By default, SUB/WAVE takes three passes through the library:

1. **Context** starts with the active show, a playlist or musical journey, and
   its relevant musical brief.
2. **Continuity** looks for a useful relationship to the track on air, helping
   the next record feel like it belongs in the same broadcast.
3. **Exploration** makes room for a less obvious option, such as a deep cut,
   recent addition, favourite, or wider library discovery.

The DJ sees the resulting eligible shortlist and makes the editorial call. It
can choose only from that list, so the rules that made a record eligible remain
in force through the final decision.

## Your station rules still come first

Track Shortlisting changes how SUB/WAVE finds candidates; it does not loosen
your music policy. Existing show filters, strict playlist rules, exclusions,
recency and no-repeat protection, artist variety, and other station guards
continue to apply before the DJ selects a record.

In practical terms, a DJ cannot use a promising-sounding shortlist to bypass a
strict show, revive an excluded track, or ignore rotation simply because it
likes the idea. Editorial judgement begins only after the station has
established a safe musical field.

## Choose the breadth of the search

<!-- Screenshot placeholder: Settings → DJ behaviour → Track selection, showing
the Track Shortlist passes control at its default of 3. -->

In **Settings → DJ behaviour → Track selection**, set **Track Shortlist
passes** from one to five:

- **1 pass** uses Context only for the narrowest, most tightly focused choice.
- **2 passes** add Continuity.
- **3 passes** are the default: Context, Continuity, then Exploration.
- **4 and 5 passes** repeat Context and then Continuity, widening the field the
  DJ considers.

More passes give the DJ a broader set of eligible options. They can be useful
for a large, varied library or a show where discovery is part of the point.
Fewer passes make the decision more tightly anchored to the show and current
track. Start with three; adjust only when you can hear a clear reason to make
the field narrower or broader.

Each additional pass adds roughly up to one second to building the shortlist.
The larger effect may be the final DJ decision: more passes mean more tracks
for the model to compare, so its selection can take longer. How much longer
depends on your chosen model and its local or cloud setup. Consider the wider
choice alongside the response time that feels right for your station.

## Give a DJ a musical instinct

<img width="499" height="174" alt="image" src="https://github.com/user-attachments/assets/b0991cbb-65cb-4eb3-bb50-8bd0f024791b" />

**Musical Leanings** let you describe the kinds of choices a presenter tends
to favour—for example, overlooked album tracks, gentle changes in energy, or
unexpected connections across eras. They are separate from a DJ's Soul.

That separation matters. A Soul describes how a DJ speaks and relates to the
listener; Musical Leanings describe a small amount of private musical taste.
When several shortlisted records would all work, that taste can help settle a
close call.

Musical Leanings are a soft tie-breaker, not a new rule set. They do not make
an ineligible track eligible, override show settings or rotation, or appear in
the DJ's on-air speech. A guest's Leanings can influence a close decision too,
but remain lighter than the host's.

For practical patterns and a worked example, see [Giving your DJ Musical
Leanings](../field-guide/giving-your-dj-musical-leanings.md).

## What happens when a shortlist cannot be used

Music keeps moving. If SUB/WAVE cannot complete a shortlist selection, it uses
its established **Backup selection** path rather than leaving the station
waiting for a decision. This is automatic; Track Shortlisting is the normal
way the station finds music, not a mode you need to switch between.

## Frequently asked questions

### Does a shortlist take choice away from the DJ?

No. It separates eligibility from editorial judgement. The station prepares a
field of music that already meets its requirements; the DJ decides which of
those valid records is right for this moment.

### Does it make the station more restrictive?

No. It retains the safeguards you already set. The Exploration pass is there
to preserve discovery within those safeguards, rather than treating familiar
choices as the only safe ones.

### Should I use five passes for the best results?

Not necessarily. Five passes mean a broader choice, not automatically a better
one. Three is the balanced default. Use more only when your library, show, and
model setup have room for a wider final choice; use fewer when you want a more
focused field.

### Will listeners hear why a record was shortlisted?

No. Discovery sources and private selection reasoning belong in the Booth, not
in a DJ link. The DJ's on-air job is still to present the record naturally.

## Related reading

- [Building a great show](../field-guide/building-a-great-show.md)
- [Frequently asked questions](../faqs/README.md)
- [Official SUB/WAVE documentation](https://github.com/perminder-klair/subwave/tree/develop/docs)
