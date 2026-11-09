# Google Flow Production Guide: Project 01 (Liminal Roblox Weirdcore)

Welcome to the production repository for **Project 01: Liminal Roblox Weirdcore**. This project is optimized specifically for **Google Flow** using **Nano Banana (Image Mode)** and **Veo (Video Mode)** to produce high-retention vertical YouTube Shorts, TikToks, and Instagram Reels (9:16 portrait).

---

## 1. The Core 2-Step Workflow (Per Shot)

Veo naturally redraws environments, props, and textures if given only text prompts. To guarantee **zero visual drift** across shots, execute each shot in two distinct steps:

```
[Step 1: Nano Banana]                     [Step 2: Veo]
Generate Frame Image (Still)   --->   Animate Frame Image (10s Clip)
- Attach Character Ref                - Set Frame Image as First Frame
- Attach Location Plate Ref           - Add Camera Motion + Action
- Lock Lighting & Composition         - Insert Narrator Line + Ambient Sound
```

1. **Step 1: FRAME IMAGE (Nano Banana)**
   - In Google Flow, set the model dropdown to **Nano Banana** (Image Mode).
   - Set aspect ratio to **9:16 (Vertical Portrait)** in the Flow dropdown.
   - Attach your saved Character library asset and the relevant Location Plate.
   - Paste the `FRAME IMAGE` prompt from the shot file. Generate until you approve the composition.

2. **Step 2: VIDEO (Veo)**
   - Switch the model dropdown to **Veo** (Video Mode).
   - Set the approved still image from Step 1 as the **first frame** / initial image input.
   - Ensure the aspect ratio remains **9:16**.
   - Paste the `VIDEO` prompt from the shot file.
   - Generate your 10-second clip.

3. **Step 3: Stacking & Trimming**
   - Save your generated raw clips as `Shot_01.mp4`, `Shot_02.mp4`...
   - Import clips into your video editor (CapCut, Premiere Pro, DaVinci Resolve).
   - Trim each clip to match the spoken voice-over narration line (~6–8 seconds per shot).
   - The ending of Shot 08 connects seamlessly back into Shot 01 for infinite loop retention!

---

## 2. Switching Modes in Google Flow

> [!IMPORTANT]
> The mode toggle is a **model dropdown** located right near the prompt input box (switching between **Nano Banana** and **Veo**), *not* a button on the generated image itself.
> - If images keep generating when you want video, switch the dropdown to **Veo**.
> - If video fails to load starting frames, make sure the model is on **Veo** and the frame image is attached to the prompt.

---

## 3. Style Block (Master Visual Anchor)

Every single prompt in this project incorporates the locked style block:

```text
Low-poly Roblox-style 3D game render, blocky characters and blocky environment, simple flat plastic textures, like a Roblox game world. Eerie empty liminal space, uncanny, something feels wrong. Flat overexposed fluorescent lighting, faint haze, muted desaturated colours. Dreamcore weirdcore mood. Deliberately simple blocky geometry, not realistic.
```

---

## 4. Voice Builder Setup (Configure Once in Flow)

Before generating video with dialogue, configure the **Liminal Narrator** voice in Google Flow's Voice Builder:

| Field | Setting / Value |
| :--- | :--- |
| **Voice Name** | `Liminal Narrator` |
| **Sample Dialogue** | `If you ever load into an empty server with zero ambient noise, do not touch your keyboard.` |
| **Customize Performance** | `Calm, low, hushed whisper tone with faint distant room reverb. Slow deliberate pacing, eerie, cold, steady delivery without dramatic shouting.` |

> [!TIP]
> Keep the sample dialogue short (≤ 120 characters) to prevent voice preview errors in Google Flow.

---

## 5. Anti-Drift Consistency Rules

1. **Location Plates:** Before generating characters in an environment, generate an empty plate (`PLATE_YELLOW_CORRIDOR` or `PLATE_VENDING_ALCOVE`) containing **zero characters**. Re-attach this plate into every shot occurring in that space with the anchor: *"Match the attached location plate '<NAME>' exactly."*
2. **Costume & Rig Anchor:** The Wanderer avatar must always have the exact same color scheme: bright yellow block head and arms, royal blue box torso, bright green box legs, and a minimal neutral smiley face.
3. **Dialogue Mode:** This project uses **pure off-screen voice-over narration**. Characters on screen **never** move their mouths or lips. This eliminates AI lip-sync artifacts and preserves the classic low-poly toy/game feel.
4. **No Filler Repeats:** Every Veo prompt includes: *"Speak the whole line ONCE only, then stop — do NOT repeat any word or phrase."*
5. **No Text / Watermarks:** Every prompt specifies: *"No subtitles, no captions, no written words anywhere on screen."* (Subtitles should be added in post-production with high-contrast animated text for maximal retention).
