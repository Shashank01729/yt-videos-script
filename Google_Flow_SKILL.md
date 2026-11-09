---
name: google-flow
description: Produce AI videos in Google Flow (Veo + Nano Banana). Use when the user is making a video/short/film/reel in Google Flow — writing per-shot image+video prompts, locking character & background consistency across separately generated clips, setting up Flow voices (incl. non-English accents), fixing common Veo failures (lip-sync, repeated words, policy blocks, drifting backgrounds), and structuring the project into per-shot files. Covers portrait Shorts/Reels and the liminal/Roblox weirdcore genre.
---

# Google Flow video production

Google Flow = Google's AI filmmaking tool. Two models matter:
- **Nano Banana (image)** 🍌 — makes stills. Default is often "2 images per prompt."
- **Veo (video)** 🎬 — makes clips (10 seconds each, with audio).

The user generates **one clip at a time** and approves each before the next. Deliver prompts copy-paste ready, and walk them shot by shot ("next").

## The golden workflow: FRAME IMAGE → VIDEO (per shot)
Veo redraws rooms/props/clothes slightly on every run. To stop drift, every shot is two steps:
1. **FRAME IMAGE** — in image mode (Nano Banana), generate a still. Attach: character refs + a location/reference image. This locks composition, faces, clothes, room.
2. **VIDEO** — in Veo mode, set that still as the **first frame** ("START FROM THE ATTACHED FRAME IMAGE, then animate it"), paste the motion + dialogue + sound. 10s.
3. Name clips `Shot_01`, `Shot_02`… trim each to its narration, stack in order in an editor.

## Switching modes (users get stuck here)
The mode is a **model dropdown** near the prompt box, not a button on the image. If images keep generating when they want video, the model is still on **Nano Banana** — change it to **Veo**. Image prompts → Nano Banana; video prompts → Veo.

## Aspect ratio
Set it in BOTH places: the prompt text ("vertical 9:16 portrait format") AND Flow's aspect-ratio dropdown. The dropdown is the real switch. Shorts/Reels/TikTok = **9:16 portrait**. Keep the whole film one orientation.

## Consistency (the #1 problem)
- **Characters:** build each in Flow's character builder and save to Library. Reuse the saved character in every shot so face/clothes never change. Builder fields:
  - **Portrait prompt** (head & shoulders) + **Full-body prompt** (full figure).
  - **Character info (optional):** a plain description locking appearance; end with "look must stay identical in every shot."
- **Locations:** make one **location plate** = an EMPTY still of the room/place (no people), save under a name like `PLATE_HEALING_WING`. Attach it to every shot there, with: "Match the attached location plate exactly: same room, furniture, props in the same places, same colours; only the framing changes."
- **Clothing:** write the exact outfit into every prompt (per-shot costume anchor). Don't rely on memory.
- **Positions / 180° rule:** keep each character on a fixed side across shots (e.g. A always LEFT, B always RIGHT) so cuts don't flip them.

## Dialogue — two modes, pick deliberately
- **On-camera speech (lip-sync):** the character's face is in frame and they talk. Write: "spoken out loud ON CAMERA with full lip-sync; mouth moves in sync with every word." Good when a character is actually speaking to someone.
- **Voice-over narration (no lips):** a narrator over the action. Write: "pure off-screen voice-over narration only. NO character on screen ever speaks or moves their mouth or lips at any point." Use for narrated stories. Name the narrator so the voice stays consistent, but still state they never move their lips on camera.
- **Wrong-voice fix:** if a character speaks in the wrong voice (e.g. a healer speaks the hero's line), add a VOICE RULE naming the ONLY speaker and mark on-screen non-speakers "(silent)".

## Veo failure fixes (recurring)
- **Repeated words / phrases** (short lines get padded): lengthen the line so it fills ~7–8s of a 10s clip, AND add "Speak the whole line ONCE only, then stop — do NOT repeat any word or phrase." Do NOT instruct pauses — pauses cause filler repeats.
- **Policy block ("might violate policies"):** remove exact ages and literal man/woman labels in character builds — describe features instead ("The subject features…"). Soften injury/violence: instead of "red burn / blood," use fantasy-safe "soft glowing scorch mark like a dying ember / magical sparkles." Keep it all-ages.
- **Hologram/ghost appears life-size:** add "small translucent hologram, hand-sized; the character is NOT physically in the room."
- **Object appears from a hand / wrong staging:** place props explicitly ("crystal rests on the side table, arm's length away, nobody touches it").
- **Background drifts between tabs:** use the location plate + "Match the attached location plate exactly."

## Voice setup (set once per character, reuse)
Flow voice builder has three fields:
- **Voice name** — e.g. `Liminal Narrator`, `Arin - Hindi Male`.
- **Sample dialogue** — ONE short line (keep it ≤ ~120 chars; long samples can fail preview).
- **Customize performance** — describe age, tone, pace, accent, emotion. Keep it concise; if "preview generation failed", shorten it and drop edgy words ("creepy"→"unsettling").
- **Non-English accent:** state it explicitly, e.g. "native Hindi speaker with a natural Indian accent, no English/foreign accent." For Hindi, write dialogue in Devanagari.
- **Fast/spooky etc.:** put pace & tone words in performance ("speaks fast with few pauses", "sharp, crisp tone", "faint distant reverb").

## Sound
Put a SOUND line in every VIDEO prompt (ambient only, usually "No background music" so the voice stays clear).

## Project structure (deliver as files)
```
<Project Name>/
  00_README_How_This_Works.md     # style block, voice, workflow
  02_Reference_Images/            # location plates (optional for shorts)
  Video_01_<slug>/ or Scene_01_<slug>/
    _Overview.md                  # story, shot list
    01_Character_<name>.md        # portrait + body + info prompts
    Shot_01.md ... Shot_NN.md     # each: FRAME IMAGE prompt + VIDEO prompt
```
Each shot file: attach list, the narration line, STEP 1 FRAME IMAGE prompt, STEP 2 VIDEO prompt, a checkbox line.

## Prompt skeletons
**FRAME IMAGE (image mode):**
```
<STYLE BLOCK>, vertical 9:16 portrait format.
MOOD & COLOR GRADE: <...>
LOCATION (keep this exact layout): <...>. Match the attached location plate '<NAME>' exactly.
LIGHT: <...>
CHARACTERS (use saved Flow character images so faces/clothes never change): <exact look + exact outfit>.
FRAMING: <shot size, lens>, compose for a tall 9:16 vertical frame.
THE MOMENT (a single frozen instant, held still): <one beat>.
This is ONE still image: no motion blur, no text. No subtitles, no captions, no written words anywhere.
```
**VIDEO (Veo mode):**
```
<STYLE BLOCK>, vertical 9:16 portrait format.
MOOD & COLOR GRADE: <...>
LOCATION (keep this exact layout): <...>. Match the attached location plate '<NAME>' exactly.
START FROM THE ATTACHED FRAME IMAGE as the first frame, then animate it.
CAMERA: <move>.
ACTION: <what moves>.
DIALOGUE (<on-camera lip-sync> OR <pure off-screen VO, no mouths move>): <voice desc>: "<line>". Speak ONCE only, do not repeat any word.
SOUND: <ambient>. No background music.
No subtitles, no captions, no written words anywhere on screen.
```

## Style blocks (reusable)
- **Photoreal live-action:** "Photorealistic cinematic film still from a live-action fantasy film, real actors, natural skin texture, shallow depth of field… Not animated, not a cartoon, not an illustration."
- **Roblox / liminal weirdcore:** "Low-poly Roblox-style 3D game render, blocky characters and blocky environment, simple flat plastic textures, like a Roblox game world. Eerie empty liminal space, uncanny, something feels wrong. Flat overexposed fluorescent lighting, faint haze, muted desaturated colours. Dreamcore weirdcore mood. Deliberately simple blocky geometry, not realistic." Sound: "deep low droning hum, muffled echoing reverb, faint fluorescent buzz, backrooms liminal ambience. No music."

## Shorts/Reels craft
60–120s, hook in first 2 seconds, pose a question that isn't answered to hold watch-time, loopable ending. Trim raw 10s clips down to the spoken line to control total runtime.

## Copyright / monetization (if asked)
Adapting someone's webtoon/comic/anime is infringement even WITH credit — credit ≠ license. Safe path: original stories (own names/characters/art), licensed content (written permission), or public-domain/CC-commercial. YouTube monetization also needs the Partner Program (1,000 subs + 4,000 watch hours, or 10M Shorts views / 12 mo).
