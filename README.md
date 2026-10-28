# Roblox Lightning VFX Reference Pack

Collected clips of chain lightning and full lightning movesets from Roblox VFX creators on X. Use these as visual references for Blender (or Roblox Studio) recreation.

## Source Posts
- Chain Lightning: https://x.com/slashskill_/status/2114063547156361599
- Dual Lightning Daggers Moveset: https://x.com/ZDoranto/status/1910072867477237916
- Lightning Skill (high quality): https://x.com/itz_venomec/status/2070954492523102252
- Lightning Strike Skill: https://x.com/eternalanthem_/status/2006174277385548029
- Stylized Lightning Beam: https://x.com/icedxmon1/status/2107181530837840122
- Procedural Lightning Module: https://x.com/aquifye_/status/2018412453479272739

## Local Zip Creator Script
Run this locally to download the clips and create a zip:

```python
import requests, zipfile, os
videos = {
    "slashskill_chain_lightning.mp4": "https://video.twimg.com/amplify_video/2114063386963025921/vid/avc1/900x900/2KCtSnYTipUJKti5.mp4",
    "ZDoranto_lightning_daggers_moveset.mp4": "https://video.twimg.com/amplify_video/1910072180622192640/vid/avc1/1280x720/q_wgCpJnrBolc_Gc.mp4",
    "itz_venomec_lightning_skill.mp4": "https://video.twimg.com/amplify_video/2070953639942750208/vid/avc1/2560x1440/_ClrySyx1jy79Emz.mp4",
    "eternal_lightning_strike.mp4": "https://video.twimg.com/amplify_video/2006173681374953473/vid/avc1/1280x720/jdJbmQvWdHQSLVg-.mp4",
    "icedxmon_stylized_beam.mp4": "https://video.twimg.com/amplify_video/2107181202683625472/vid/avc1/1280x720/ydD9cL7ZJK9EUaRQ.mp4",
    "aquifye_procedural_lightning.mp4": "https://video.twimg.com/amplify_video/2018412128689111040/vid/avc1/3840x2160/R30t6Flri-Uk-wdm.mp4",
}
os.makedirs("lightning_refs", exist_ok=True)
with zipfile.ZipFile("Roblox_Lightning_VFX_Reference_Pack.zip", "w") as zf:
    for name, url in videos.items():
        print(f"Downloading {name}...")
        r = requests.get(url, headers={"User-Agent": "Mozilla/5.0"})
        path = f"lightning_refs/{name}"
        open(path, "wb").write(r.content)
        zf.write(path, name)
print("Zip ready: Roblox_Lightning_VFX_Reference_Pack.zip")
```

## Multi-Agent Review + Blender Recreation Prompt
Paste this into Claude (with Blender MCP), Codex, or a multi-agent setup. Instruct it to spawn sub-agents (Gemini-style reviewers) as needed:

```
You are an expert VFX technical artist coordinating a multi-agent review.

Attached are reference videos of Roblox lightning effects (chain lightning + full movesets from creators like slashskill_, ZDoranto, itz_venomec, aquifye_, etc.).

Tasks:
1. Spawn specialized review agents (Gemini 4 Argon style or equivalent) to independently analyze the clips. Have them note: chaining logic, branching/fork density, impact effects (circles, debris, shockwaves), color/gradient usage, glow intensity, timing, particle density, animation sync, and performance considerations.
2. Aggregate the reviews. Draw inspiration for improved versions.
3. If useful, use ImageGen / Codex image tools to generate concept frames or reference stills of key moments (chain arcs, impact blooms, stylized beams).
4. Recreate a high-quality, reusable chain lightning system in Blender using Geometry Nodes. Support multiple targets, forks, core + glow layers, and adjustable parameters (length, thickness, color, branch chance, lifetime).
5. Prototype 2–3 additional moveset elements inspired by the references (ground strike with debris, vertical energy beam, multi-hit dash/projectile).
6. Export clear renders or node screenshots. Describe how each piece can be adapted to Roblox Studio (Beams, ParticleEmitters, Trails, or custom modules).
7. Prioritize stylized, performance-friendly looks suitable for real-time games.

Focus first on chain lightning, then the most impactful moveset pieces. Summarize key insights from the sub-agents.
```

---
Reference pack for lightning VFX study and recreation. Direct video links above can be used if the script needs updating.
