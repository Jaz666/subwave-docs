# Giving your DJ Musical Leanings

**Musical Leanings** give a DJ private editorial judgment without asking a speaking persona to run the station. They provide a short description of the kinds of _eligible_ records a presenter tends to favor when there is a genuine close call.

They are deliberately separate from a DJ's **Soul**. A Soul tells Subwave how a presenter sounds and relates to listeners on air. Musical Leanings help the DJ choose between several records that already satisfy the current show rules, rotation, safety protections, and library guards.

## Why Separate Soul and Musical Leanings?
Our investigation into model behavior established a clear principle: putting music preferences inside a DJ's Soul shapes how they talk, but does not reliably guide what they play.

Vanilla track pickers receive the DJ’s Soul as part of their presentation prompt. While those musical words are visible to the model, calibrated testing showed that writing music tastes into the Soul produced no measurable, reliable selection effect above ordinary sampling variation. It can also confuse the model's presentation voice or cause the DJ to constantly talk about specific bands out of context.

**Musical Leanings** fixes this by introducing an explicit, bounded preference field. It acts strictly as a tiebreaker when two or more tracks fit the current show criteria equally well. It guides music discovery quietly behind the scenes without spilling into on-air monologues or overriding station safeguards.

## Meet Bob

Bob is a familiar example: a warm, knowledgeable guitar-music DJ built using the kind of rich prose new Subwave users often receive from general-purpose AI writing tools.

<img width="25%" height="25%" alt="bob" src="https://github.com/user-attachments/assets/77c6b3b7-141f-437d-a8cf-b756fcce25a1" />

Here is Bob's original, all-in-one draft:

>Bob is a lifelong music obsessive with an encyclopaedic knowledge of rock, indie and alternative music. Growing up on the great guitar bands of the 70s, 80s and 90s, he particularly loves classic rock, alternative rock, indie, Britpop, post-punk and progressive rock. His favourites include Pink Floyd, Led Zeppelin, Dire Straits, R.E.M., The Cure, The Smiths, Radiohead, Oasis, Blur and The Stone Roses. Bob loves melodic guitar music, prominent basslines, acoustic guitars, interesting production and songs with strong musicianship. He prefers deeper album tracks and overlooked gems rather than obvious hits, and enjoys discovering newer artists influenced by the music he grew up with. He dislikes manufactured pop, repetitive dance music and novelty records, and avoids overly commercial chart music. Warm, knowledgeable and enthusiastic, Bob loves sharing his musical discoveries with listeners and explaining what makes a great record special.

To make Bob work reliably in Subwave, we separate his voice, his **show territory**, and his **musical tiebreakers**.

# Where Bob's First Draft Belongs
A long list of band names inside a Soul or description is not a reliable selection strategy. If a named artist isn't in your library, isn't surfaced by discovery sources, or is ruled out by recency guards, prose names won't force them onto the air.

To get the best result, place each part of Bob's draft into its proper setting:

|Part of Bob's Draft|Best Home in Subwave|Why|
|---|---|---|
|“Warm, knowledgeable and enthusiastic... loves explaining what makes a record special.”|**DJ Soul**|Shapes how Bob speaks, reacts, and presents on air.|
|Classic rock, alternative, indie, Britpop, and post-punk|**Show Settings**|Establishes the programme's broad musical territory and genre filters.|
|“Dislikes manufactured pop and commercial chart music”|*Show Filters & Rules**|Hard boundary rules that belong in show guards, not soft close-call preferences.|
|Deeper album cuts, overlooked gems, melodic guitars, and dynamic builds|**Musical Leanings**|Private tiebreaker criteria used to pick a winner between eligible tracks.|
|Specific favourite artists (R.E.M., Radiohead, Pink Floyd, etc.)|**Show Playlists**|Defines an actual pool of library candidates rather than relying on prose.|
