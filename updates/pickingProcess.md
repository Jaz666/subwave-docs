# Agentic Picker vs Shortlist Picker

## Key Differences

# Agentic Picker vs Shortlist Picker — differences

This table lists differences in method, including the Shortlist alternative.
Shared behaviour is omitted. Conditional capabilities depend on the active show,
available library services and configured model/provider.

| Area | Agentic Picker | Shortlist Picker's alternative |
|---|---|---|
| Choosing discovery tools | The model selects tools and their arguments; controller code executes them. | Controller code chooses and executes a bounded source plan. The model receives candidates without executable discovery tools. |
| Discovery spread | Prompt guidance encourages the model to use several complementary sources. | Code rotates sources across show context, continuity and variety, within the configured number of passes. |
| Targeted searches | The model constructs queries during discovery from the brief and session context. | An optional tool-free preparation call extracts up to three queries from explicit brief requests. Code validates supporting quotations and caches the result for the airing, including an empty result. |
| Refining discovery after results | Can inspect results and change searches when the provider permits further discovery rounds. | No equivalent adaptive query rewriting within a pick. Code runs the planned passes and bounded recovery sources; prepared queries remain fixed until the brief or airing changes. |
| Thin discovery results | Tool results describe misses; the model may try another source if it has discovery rounds remaining. | Code automatically adds available starred/random recovery sources when fewer than four balanced candidates remain. Shared fallback handles a still-unusable result. |
| Conversation continuity | Reads the wider session window, including earlier events and DJ turns. | Receives up to three short, already-aired editorial remarks. Routine announcements, private picking reasons and raw listener messages are excluded. |
| Set history and current situation | Reads the set's arc and contextual information through session messages and picking-event guidance. | Receives explicit compact recent-play, predecessor, time/weather/festival and listener-favourite information, where available. |
| Playlist and journey discovery priority | The model is instructed to lead with the relevant playlist, prepared catalogue or journey tool. Shared restrictions enforce eligibility. | Code gives directed sources priority and reserves a pass for a soft playlist when appropriate. The choosing model receives corresponding preference guidance. |
| Exploration picks | The model is nudged to call deepCuts and consider a fitting discovery. | Code prioritises deepCuts in the discovery plan and gives the choosing model a brief exploration cue. Runs and journeys retain precedence. |
| Artist balance across candidates | Uses shared source-level caps and final artist-variety guards. | Also caps the merged candidate list at three tracks per artist, with strict-playlist and prepared-episode exemptions. |
| Tempo/key ordering | The model judges compatibility from the supplied facts; the Agentic route adds no whole-list compatibility sort. | Code softly orders the merged list by measured transition fit before the model chooses, using the mix-run target when available. |
| Repeatedly offered but unchosen tracks | Has airplay history and ordinary variety guidance, without the Shortlist offer penalty. | Applies a decaying preference penalty to repeated offers. This changes ordering, not eligibility. |
| Initial choosing task | Discovery and the preliminary choice happen inside the model's agent run. | Normally one structured choosing call over the completed candidate list. Optional search preparation, Leanings review and corrective calls are separate. |
| Selection-reason wording | Returns a short reason, subsequently checked and associated with the verified chosen track. | Returns a musical clause; the controller adds the verified title/artist and substitutes neutral wording if the clause is unsuitable. |
| Intro-length guidance | Receives known measured intro length among the candidate facts. | Now receives the same measurement, with explicit guidance to consider speaking space softly when a link is planned. Musical flow retains priority. |
| Failed corrective choice | Shared ID repair and constrained re-picking apply; a failed Agentic corrective call returns no replacement. | Uses the same repair and constrained re-picking, but can choose the highest-ranked eligible corrective candidate in code if its model fails. |
| Choosing-model failure | After recovery attempts fail, the route falls back to the shared pool. | Can immediately choose the highest-ranked shortlist track in code, with a neutral reason and no transition effect. The failure still counts toward the shared circuit breaker. |
| Discovery deadline | One deadline covers the agent run and its internal recovery attempts. | Uses bounded pass counts and individual service/model request timeouts; it has no equivalent overall agent-run deadline. |
| Discovery diagnostics | Records the model's actual discovery-tool calls and responses. | Records controller source runs, arguments, status, returned/accepted counts and timings alongside the choosing-model record. |

The main capability without a direct Shortlist equivalent is **adaptive
discovery within a pick**: a model reading an unexpected result and deciding
to pursue a different query. Agentic can do this only when its provider's
discovery-round allowance permits it. Shortlist instead uses planned source
rotation, validated prepared queries and automatic recovery sources.

Both methods share the show restrictions, recency rules, Musical Leanings
review and replacement validation, artist/album guards, isolated link writer,
speech-budget checks and queue-admission checks. Both now expose measured intro
length to the choosing model.

## Discovery - Pick - Queue Timeline

**✓** means the step applies when its conditions are met. **—** means that
particular step is absent. Optional and recovery steps do not happen on every
pick. The table follows a typical automatic pick, with conditional branches
included alongside the main sequence.

| Step, from starting a pick to queueing | Agentic Picker | Shortlist Picker |
|---|:---:|:---:|
| **1. Start a pick cycle when another automatic track is needed; prevent overlapping picks** | ✓ | ✓ |
| 2. Estimate when the chosen track will play and resolve the appropriate show | ✓ | ✓ |
| 3. Maintain the DJ session and prepare programme/episode context and handoffs when required | ✓ | ✓ |
| 4. Check the daily model budget and shared failure circuit breaker | ✓ | ✓ |
| 5. Determine whether a spoken link is due and permitted | ✓ | ✓ |
| 6. Capture the intended preceding track, including a queued predecessor where applicable | ✓ | ✓ |
| 7. Advance any DJ-mode mix run or sonic journey | ✓ | ✓ |
| 8. Occasionally favour exploration through deep cuts, when the show permits it | ✓ | ✓ |
| 9. Resolve host and optional guest Musical Leanings for the later review | ✓ | ✓ |
| 10. Record the picking event in the DJ session | ✓ | ✓ |
| **11. Load library information and determine which discovery sources are available** | ✓ | ✓ |
| 12. Resolve the show's playlist pool and any excluded playlists | ✓ | ✓ |
| 13. Establish strict genre, era, mood, energy and vocal restrictions, where configured and supported | ✓ | ✓ |
| 14. Establish minimum and maximum track lengths | ✓ | ✓ |
| 15. Establish recent-track restrictions and the hard no-repeat window | ✓ | ✓ |
| 16. Resolve listener favourites, when enabled | ✓ | ✓ |
| 17. Supply the show brief and musical guidance to the picking model | ✓ | ✓ |
| **18. Optionally prepare targeted search queries through a separate model call with no discovery tools** | — | ✓ |
| 19. Check prepared queries against supporting quotations; reject invented subjects, presenter searches and exclusions | — | ✓ |
| 20. Cache prepared queries—including an empty result—for reuse during that airing | — | ✓ |
| 21. Have the controller choose a bounded, rotating discovery plan | — | ✓ |
| 22. Have the model choose discovery tools and their search arguments | ✓ | — |
| 23. Support targeted artist, title, genre, lyrical-theme and instrumentation searches, when available | ✓ | ✓ |
| 24. Support mood, energy, era, playlist, episode-catalogue and sonic-journey discovery | ✓ | ✓ |
| 25. Support similarity, deep cuts, favourites, recent additions and other variety sources | ✓ | ✓ |
| 26. Execute discovery functions in controller code and collect real library tracks | ✓ | ✓ |
| 27. Apply shared show restrictions, duration limits, exclusions, recency checks and candidate deduplication | ✓ | ✓ |
| 28. Apply freshness-biased ordering and source-level limits, including artist caps where appropriate | ✓ | ✓ |
| 29. Attach known track metadata, musical analysis, similarity evidence and airplay history | ✓ | ✓ |
| 30. Show measured intro length directly to the initial picking model, when known | ✓ | ✓ |
| 31. Let the model refine discovery after reading results, when its provider allows additional rounds | ✓ | — |
| 32. Automatically try bounded recovery sources when too few usable candidates are collected | — | ✓ |
| **33. Apply an additional artist cap across the complete merged candidate list, with playlist/episode exemptions** | — | ✓ |
| 34. Reduce the preference for tracks repeatedly offered but not selected | — | ✓ |
| 35. Order the complete candidate list by measured tempo/key compatibility, when available | — | ✓ |
| 36. Give the choosing model the wider DJ-session message history | ✓ | — |
| 37. Give the choosing model a compact recent-track summary and up to three short, already-aired conversation cues | — | ✓ |
| 38. Consider musical flow, show guidance, variety, listener favourites and relevant contextual cues | ✓ | ✓ |
| **39. Make a preliminary track choice without Musical Leanings influencing it** | ✓ | ✓ |
| 40. Return a track ID, musical selection reason and optional transition choice | ✓ | ✓ |
| 41. Check that the chosen ID belongs to the discovered candidates | ✓ | ✓ |
| 42. Repair an unambiguous near-miss in the returned track ID, if necessary | ✓ | ✓ |
| 43. Attempt a constrained corrective pick from existing candidates, if necessary | ✓ | ✓ |
| 44. Take the best-fitting eligible shortlist track in code if the Shortlist choosing model fails | — | ✓ |
| 45. Use the shared fallback pool if the selected route cannot provide an accepted pick | ✓ | ✓ |
| **46. Privately add available Last.fm tag evidence for the Musical Leanings assessment** | ✓ | ✓ |
| 47. Identify viable challengers and check whether Leanings offer a distinguishing advantage over the preliminary choice | ✓ | ✓ |
| 48. Run a separate, compact Musical Leanings model review only when there is a qualifying choice to settle | ✓ | ✓ |
| 49. Verify any proposed replacement against the allowed candidates, supported Leanings and musical-flow checks | ✓ | ✓ |
| 50. Keep the preliminary choice if the review fails or proposes an unsupported replacement | ✓ | ✓ |
| **51. Apply the shared artist-variety guard; correct or rescue the pick when required** | ✓ | ✓ |
| 52. Apply the shared album-cooldown guard when enabled | ✓ | ✓ |
| 53. Resolve the final selection reason against the actual final track | ✓ | ✓ |
| 54. Generate any spoken link through the separate listener-facing writer, with private picking context kept separate | ✓ | ✓ |
| 55. Clean and budget the link for the intro; check for echoed listener-request wording and stale speech ownership | ✓ | ✓ |
| 56. Respect DJ mode and operator transition-effect switches before attaching transition requests | ✓ | ✓ |
| **57. Build the queue item with verified track details, reason and any link, speaker, predecessor and timing information** | ✓ | ✓ |
| 58. Recheck the never-play blocklist at queue admission | ✓ | ✓ |
| 59. Recheck the automatic maximum track length at queue admission | ✓ | ✓ |
| 60. Reject a track already playing or already queued | ✓ | ✓ |
| 61. Add the accepted track to the upcoming queue, schedule persistence and start the shared sender | ✓ | ✓ |
| 62. Record the accepted selection and confirm Leanings usage only if its replacement survived the guards and reached the queue | ✓ | ✓ |

Targeted searching is available to **both** methods. Shortlist's additional
preparation turns explicit brief requests into validated, reusable queries;
Agentic constructs its queries during discovery.

Both methods now expose known measured intro length to the choosing model.
Shortlist also receives brief guidance to treat intro space as a soft preference
when a link is planned, with musical flow retaining priority. Missing intro
measurements remain unknown. The shared speech-budget checks still determine
what can actually fit and air.

Once queued, both methods use the same speech-rendering and Liquidsoap delivery
pipeline.

Source files checked:

- `controller/src/broadcast/dj-agent.ts`
- `controller/src/broadcast/dj-agent/agents.ts`
- `controller/src/broadcast/dj-agent/shortlist-pick.ts`
- `controller/src/broadcast/dj-agent/leanings-pass.ts`
- `controller/src/broadcast/dj-agent/enqueue.ts`
- `controller/src/broadcast/shortlist-search-preparation.ts`
- `controller/src/music/shortlist.ts`
- `controller/src/music/shortlist-search.ts`
- `controller/src/music/shortlist-offers.ts`
- `controller/src/llm/internal/tools/picker/scope.ts`
- `controller/src/llm/internal/tools/picker/slim.ts`
- `controller/src/llm/instructions/picker.md`
- `controller/src/broadcast/queue.ts`
