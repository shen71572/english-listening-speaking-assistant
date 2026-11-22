# Dynamic Design Studio

## Pick the right tool for the job

- Start from what the user wants to make and pick the tool whose output matches it, web animation, video file, 3D scene or audio, before you write any code.

- Use motion-design-skill for animation timing, easing and the 12 Disney principles when the work needs its motion to feel right.

- Use Motion for spring physics and screen transitions in a web interface.

- Use Remotion Skills when the task is a video production workflow built as a skill.

- Use hairline for interactive animated lines made from an idea or an SVG.

- Use anatomy-reveal for product teardown images and product showcase animation.

- Use GSAP for a professional animation timeline, it is now fully free.

- Use Blender for 3D rigging and character animation.

- Use Three.js for 3D scenes and camera movement on the web.

- Use react-three-rapier to add real physics to a 3D scene.

- Use react-postprocessing for glow, blur and cinematic post effects in a 3D scene.

- Use anatomy to turn a mechanical structure or working principle into a 3D diagram.

- Use three.quarks for particle trails and particle effects.

- Use Tweakpane to adjust animation parameters live while you tune a scene.

- Use Remotion as the React based video making engine when the video is built from code.

- Use Manim for diagrams, maths formulas and science explainer animation.

- Use Lottie for lightweight vector animation playback.

- Use the Openverse API to search free sound effects, ambient sounds and music with no API key.

- Use librosa to detect music beats so animation follows the music.

- Use WhisperX to generate subtitles aligned precisely to the timeline, including Japanese.

- Use FFmpeg for video rendering, export and format conversion.

## Build the work in order

- Read the chosen repo README before you use it and verify its current install steps and API, since repos change after this list was made.

- Check `~/MEMORY.md` for the user media preferences before you choose a visual style, so a tool default never overrides what the user wants.

- Chain the tools for a full video: plan timing with motion-design-skill, build with Remotion or Manim, add audio from Openverse with beats from librosa, add subtitles with WhisperX, render and convert with FFmpeg.

- Keep one tool per step and name the step each tool owns, so a failure points at one tool instead of the whole chain.

- Keep the collection repo at https://github.com/shen71572/dynamic-design-studio as the single index of these 20 tools and update it when a tool is added or replaced.

## Verify before you trust a tool

- Treat this list as the user collection, not as a verified review of each repo, and check a repo docs and last update before you rely on it for a real deliverable.

- Search the repo for a maintained README and current examples when an install step or an API call fails, instead of guessing the fix.

- Say plainly when a tool does not fit the user request, and offer the closest tool from this list instead of forcing one in.

## Available connectors

- [GitHub](/opt/hatch/connectors/github/CONNECTOR.md) for reading the repos in this toolkit and for pushing changes to the collection repo.

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Websites

- [dynamic-design-studio](https://github.com/shen71572/dynamic-design-studio) for the index of all 20 tools in this toolkit.

- [Openverse API](https://api.openverse.org/v1) for free sound and music search with no API key.

- [hairline](https://hairline.lucasmarkes.com/skills) for interactive line animation from an idea or an SVG.

- [anatomy-reveal](https://typingmind.com/skills/annnguyentt-anatomy-reveal) for product teardown and showcase animation.

- [anatomy](https://skills.wheresryan.sh/anatomy) for 3D diagrams of mechanical structures and working principles.

## Alternatives for better results

- Use the media tools already available for a quick image or video when a full Remotion or Manim pipeline would be slower than the result is worth.

- Split a long video into short scenes and render each one before you move to the next, so one bad scene never costs the whole render.

- Ask the user for the video length, format and where it will be shown before you pick an engine, since those three answers decide between Remotion, Manim and Lottie.
