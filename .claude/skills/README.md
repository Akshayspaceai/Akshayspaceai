# Motion skills

Third-party agent skills for motion graphics and launch videos, vendored after a
read-only security review on 2026-10-09. Each skill keeps its upstream LICENSE.
Nothing here was modified; to update, re-review the upstream diff before copying.

Stack: Claude writes HTML + GSAP, the skills set timing/camera/taste, HyperFrames
renders the MP4.

| Skill(s) | Source | Commit | License |
|---|---|---|---|
| hyperframes, hyperframes-core, hyperframes-animation, hyperframes-creative, hyperframes-cli, hyperframes-registry, motion-graphics, product-launch-video, media-use | [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes) `skills/` | `3aa68869f7d4` | Apache-2.0 |
| gsap-core, gsap-timeline, gsap-scrolltrigger, gsap-plugins, gsap-react, gsap-performance, gsap-utils, gsap-frameworks | [greensock/gsap-skills](https://github.com/greensock/gsap-skills) | `aed9cfd32777` | MIT |
| motion-design | [LottieFiles/motion-design-skill](https://github.com/LottieFiles/motion-design-skill) | `f9a8a041b851` | MIT |
| product-launch-motion | [AbubakrChan/product-launch-motion](https://github.com/AbubakrChan/product-launch-motion) | `951d6149d274` | MIT |
| motion-effects, reel-export, loop-cover | [charlie947/motion-graphics-skills](https://github.com/charlie947/motion-graphics-skills) | `4cd156acdad0` | MIT |

## Review notes

- **HeyGen telemetry.** `media-use` sends usage events to PostHog and, if you are
  signed in to HeyGen, links them to your HeyGen account email. `hyperframes-cli`
  tells the agent to post feedback to a public channel after renders. Both are
  skipped when `HYPERFRAMES_NO_TELEMETRY=1`, which `../settings.json` sets.
  (`hyperframes telemetry disable` does not cover `media-use`; use the env var.)
- **Runtime downloads.** The HyperFrames skills run `npx hyperframes@<pinned>` and
  may fetch extra workflow skills with `npx hyperframes skills update`.
- **Paid APIs are opt-in.** HeyGen TTS, Gemini and ElevenLabs are used only if you
  provide keys.
- `product-launch-motion` expects you to supply `vendor/gsap.min.js` (see its NOTICE).

## Reviewed but not vendored

- **remotion-dev/skills** — official and clean, but the repo has no license. If you
  switch to Remotion: `npx skills add remotion-dev/skills` (install
  `remotion-best-practices` alone, or the individual skills, not both).
- **t3knobox/klik-anim-skill-creation** — excellent Remotion craft rules (9/10), but
  no license, and it is Remotion-only.
- **whaleyxbt/claude-motion** — strong, but a project template, not portable skills.
  Clone it as a project if you want a Remotion setup.
- **cth9191/animate**, **Barty-Bart/motion-graphics** — safe, good, niche (their own
  canvas stack; talking-head B-roll).
- **howseen-ai/claude-motion-design** — tied to the author's machine, tells the agent
  to work around sandbox limits, scrapes YouTube and Unsplash.
- **iart-ai/motion-design-skills** — ads in every reference file, broken script paths,
  repeats LottieFiles.
- **199-biotechnologies/motion-dev-animations-skill** — pre-approves Bash and Write
  via `allowed-tools`, and points to resources that do not exist.
- **frankxai/awesome-motion-design-agent-skills** — thin checklists; `AGENTS.md`
  routes agents to the author's private system.
- **nateherkai/hyperframes-student-kit** — its HeyGen skills are outdated copies; the
  rest depend on the kit's folder layout.
- **haidrrrry/claude-remotion-skill**, **Sunwood-ai-labs/hyperframes-motion-reel-skill**
  — safe but thin or overlapping (motion-reel is Japanese-only).
