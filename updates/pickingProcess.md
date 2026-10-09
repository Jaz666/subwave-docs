# Agentic Picker vs Shortlist Picker

Updated 9 October 2026. This comparison includes the morning's local changes,
including targeted-search grounding, compact conversation guidance and
intro-length support, as intended for PR #1687.

Prepared against local feature commit `0f40c67f`; the integrated station is at
`c448291a`.

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
