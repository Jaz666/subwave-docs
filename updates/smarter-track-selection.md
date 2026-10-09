# Choosing how SUB/WAVE selects music

## TLDR - The Headline Difference - GPU vs CPU

- The **Agentic Picker** runs both Track Discovery and the Final Picking Decision entirely in either your local GPU, or on a Cloud LLM. This requires a model with at least 12 Billion Parameters, capable of Tool Calls to run reliably.
- The Shortlist Picker runs the Track Discovery on your CPU (typically faster than on a GPU) and then hands the Final Decision over to either your local GPU or Cloud LLM. This reduces the requirements of a large Parameter Model, and needs no Tool functionality. A model as small as 3 Billion Parameters is capable of running the Shortlist Picker, but we'd recommend a little higher than that for AI DJ Roleplaying.

--------

SUB/WAVE has two ways to find the next track. With **Agentic Tools**, the DJ's
language model explores your library through discovery tools and chooses a
record. With **Track Shortlist**, the Controller explores first and gives the
model a small set of suitable records to choose from.

Both routes keep the DJ involved in the final choice. The difference is who
does the searching. You can choose a route in **Settings → Music Selection**
once the update containing Track Shortlist is installed.

| | Agentic Tools | Track Shortlist |
| --- | --- | --- |
| Who explores the library? | The DJ model decides which discovery tools to call and can follow up on their results. | The Controller plans and runs a few suitable discovery sources. |
| What does the model choose from? | Tracks returned during its tool-led exploration. | A bounded list of eligible tracks assembled before the model is called. |
| What does your model need? | Reliable tool calling and enough context for tool descriptions, results and the ongoing conversation. | Enough context to compare the shortlist; ordinary track selection does not ask the model to call discovery tools. |
| Main controls | Discovery rounds and an agent deadline. | One to five shortlist passes. |

## Agentic Tools: the model leads discovery

The DJ model considers the show and the track currently playing, decides where
to look, calls library discovery tools and gathers their results. It may use
different tools or follow a promising lead from one search to another. From
the tracks it found, it proposes an initial choice; a final review can still
keep or change that choice before the record goes on air.

Because the model stays involved throughout discovery, each additional round
can add tool results to its context and take more time. This route is a good
fit when your cloud or local model handles tool calls reliably, has sufficient
context and you value model-led exploration.

In **Music Selection**, **Discovery rounds per pick** limits how many searches
the agent may make. The **Agent deadline** limits how long an Agentic pick may
run before the station uses its safe fallback. If you change either setting,
listen to several picks before deciding whether it improves your station.

### The Maze Analogy

![A capable DJ model explores the maze of discovery methods; a smaller model can find the same maze overwhelming.](https://raw.githubusercontent.com/Jaz666/subwave-docs/main/assets/illustrations/agentic-tools-maze.webp)

Think of each discovery tool as a signposted path through a maze. A capable
cloud or local model can keep its bearings, try promising routes and return
to the exit with a list of suitable tracks and a preliminary favourite. A
smaller model may lose its place, revisit the same paths until the Agentic pick
times out, or explore just one path before returning with a thin list. The
final record is chosen from the tracks found, with an optional Leanings review
before it goes on air. These are possible behaviours, not rules based solely
on model size; what matters is how reliably your model handles a multi-step
tool conversation.

## Track Shortlist: the Controller explores, then the model chooses

The Controller makes a short discovery plan for the current pick. Depending on
the show and the music on air, it can draw from sources concerned with show
context, musical continuity and wider library discovery. It does not run every
discovery tool on every pick, and it does not follow one fixed sequence. Strict
playlists and sonic journeys keep discovery focused on their direction.

The Controller applies the station's eligibility rules and gathers the tracks
those sources contribute. The DJ model then makes its initial editorial choice
from that shortlist. It cannot name a track outside the list as a valid
shortlist pick. Final safeguards may still refine that initial choice.

Track Shortlist is a good starting point for smaller or local models, models
that struggle with tool calling, or stations that want less model work during
each pick. It can also reduce cloud token use. It does **not** make library
searches free: the Controller still has to run them, and actual pick times
depend on your library, model and hardware.

### Back to the Maze

![The Controller follows selected discovery routes and brings eligible tracks to the DJ, who chooses from the shortlist.](https://raw.githubusercontent.com/Jaz666/subwave-docs/main/assets/illustrations/track-shortlist-maze.webp)

In the same maze, Track Shortlist sends the Controller along a small, planned
set of useful routes. It brings the eligible finds back to the exit, where the
DJ model compares them and chooses a track. The model still exercises musical
judgement, but it does not have to navigate the maze itself.

### Choosing the number of passes

Set **Track Shortlist passes** from **1 to 5** in **Music Selection**. Each pass
asks one suitable discovery source for candidates. The Controller balances
the available source types for the current situation; a pass is not permanently
assigned to “mood”, “similar tracks” or any other one method.

**Three passes is the default and a sensible place to start.** Fewer passes
usually make a narrower, quicker shortlist. More passes can offer the DJ a
wider choice, but may also mean more library work and more candidates for the
model to compare. Five is the widest setting, not an automatic quality
upgrade. Try changing one step at a time and judge the resulting picks as well
as their timing.

Additional passes do not add an LLM discovery loop. The model makes its
initial choice after the shortlist has been built; a separate final review or
a corrective re-pick can require further model calls.

## What both routes have in common

Your show and station rules still apply: playlist restrictions, show filters,
exclusions, repeat protection, artist and album spacing, and other selection
safeguards are not switched off by changing picker. Neither route is a way to
force an ineligible record into the queue.

**Musical Leanings** can inform a final review with either picker, without
overriding eligibility or show rules. See the separate
[Giving your DJ Musical Leanings](https://github.com/Jaz666/subwave-docs/blob/main/field-guide/giving-your-dj-musical-leanings.md)
guide for how they work and how to write them.

Listener-request matching and Segments & Skills have their **own** Direct or
Agentic settings. Changing the music picker does not change those settings.
If a primary pick cannot be completed, SUB/WAVE can use its Backup selection
path to keep music moving.

## Which should you choose?

- Choose **Agentic Tools** if you have a capable model with dependable tool
  calling and want the DJ to direct its own search through the library.
- Choose **Track Shortlist** if your model is smaller, has a tighter context
  window, struggles with tool loops, or you prefer a more bounded discovery
  process with fewer model-led steps.
- If you are unsure, start with **Track Shortlist at three passes** and listen
  to several picks. Try Agentic Tools with the same show if your model handles
  tools well and you want to compare its exploration.

The **Booth** shows private selection reasons and discovery information; the
**Stats** screen shows observed LLM context use and separate suggested
`num_ctx` values for the two picker routes when enough successful calls have
been recorded. These observations can help you tune a local model, but they
are not guarantees for every future pick.

Existing stations using Agentic Tools remain on that route unless you change
it. Stations that previously selected **Candidate Pool** move to Track
Shortlist, its supported successor. You can switch between the two routes in
**Music Selection** as your setup changes.

## Common questions

### Does Track Shortlist make the DJ's choice for it?

No. The Controller finds and filters candidates; the DJ model chooses the
record from the resulting shortlist, subject to the station's final checks.

### Does Track Shortlist mean my model no longer needs tool support?

Not for ordinary shortlist track selection. Other features may still use
tools, depending on how you have configured them. Check your request-matching
and Segments & Skills settings before changing models.

### Will listeners hear why a track was chosen?

No. Discovery sources and private selection reasons are operator information.
The DJ still introduces music naturally on air.

## Related reading

- [Building a great show](https://github.com/Jaz666/subwave-docs/blob/main/field-guide/building-a-great-show.md)
- [Frequently asked questions](https://github.com/Jaz666/subwave-docs/blob/main/faqs/README.md)
- [Official SUB/WAVE documentation](https://github.com/perminder-klair/subwave/tree/develop/docs)
