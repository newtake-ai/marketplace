---
name: newtake-use
description: "Use whenever the user wants to generate images, videos, or audio, test or compare models (\"run a demo with these models\", \"compare model A and B\"), read or edit canvas nodes, manage scripts, storyboards, timelines, characters, voices, or assets, or export media in Newtake — even when no specialized workflow skill is named. Routes general creation and model evaluation directly to Newtake MCP tools and delegates specialized productions (director treatment, Blender white-model previs to live action, music-driven product ad) to dedicated Newtake skills."
---

# Newtake General Creation & Model Routing Entry

Use this skill whenever the user wants to generate images, videos, or audio, compare or benchmark models, read or edit canvas nodes, manage scripts/storyboards/timelines/characters/voices/assets, or export finished media through the connected Newtake MCP server.

## 1. Establish Runtime & Follow Server Instructions

- Treat the connected Newtake MCP server's `initialize` `instructions` (workflow digest) and live tool schemas as the authoritative source of truth for routes, model contracts, and evidence boundaries.
- Before operating on a canvas, call `doctor` to verify identity and readiness, then call `target_project` to bind the exact target project (reuse the user-specified project, list existing projects via `list_projects` / `project_list`, or create one via `create_project` when requested).
- Opening the browser canvas is on-demand (only when the user asks to view the canvas or a tool returns `makeVisible=true`), not a mandatory prerequisite for ordinary media generation or model evaluation.

## 2. General Image, Video, Audio Generation & Model Evaluation

When the user asks to "run a demo with these models", "compare two models on the same prompt/reference", or generate images/videos/audio from text or references, execute directly with Newtake MCP tools without forcing a specialized multi-stage production workflow:

1. **Model Discovery & Live Contract**:
   - Call `search_models` to find candidate models (e.g., Seedance, Kling, Hailuo, Veo, Sora, Wan, Seedream, Flux, Midjourney, Minimax), or `recommend_video_models` when video model recommendations are needed.
   - Call `get_model` to inspect the selected model's live schema / `inputContract`. Pass the exact model identifier in `model`, and populate `params` strictly from the declared creative parameters.
   - Prioritize user-specified settings first, then task-motivated choices; omit unspecified optional parameters so Web defaults apply rather than arbitrarily maxing out resolution, duration, or output count (new image runs default to `count=1`).
2. **Multi-Model Comparison & Demos**:
   - When the user asks to test or compare multiple models on the same prompt or reference image/video, run `search_models` and `get_model` for each candidate model, then create or submit separate generation tasks on the target canvas (each with its own stable `idempotency_key`), preserving clear node labels and reference edges for side-by-side comparison.
3. **Choose the Right Execution Entry Point**:
   - **Prompt-only durable task submission (no canvas reference nodes)**: Use `generation_submit` with `request={model, prompt, params}`.
   - **Video generation & reference-backed canvas generation (image/video/audio reference nodes, start/end frames, extension, video editing)**: Follow the deployment's execution admission (`doctor.executionAdmission` and `instructions`), using `generate_video` or `create_node` / `update_node` with reference edges (`left` / `leftEnsure` / `leftAdd` or `referenceImageNodes` / `referenceVideoNodes` / `referenceAudioNodes`) and `{{Node <nodeId>}}` prompt placeholders.
   - If inline canvas execution is disabled in the current deployment (`run` only accepts `false`), prepare the reference-connected node on the canvas with `run=false` and ask the user to trigger the run in the browser canvas — never strip reference inputs to silently fall back to text-only generation.
4. **Uploading Local Reference Media**:
   - To attach local user files to the canvas as references, follow `upload_ticket` → direct byte upload to the signed URL → `upload_complete` → `upload_media`. Never treat local file paths or temporary chat attachments as existing canvas resources.
5. **Waiting, Recovery & Output Verification**:
   - When `generate_video` runs a live generation, wait for the tool call to finish rather than polling `task_status` in parallel or issuing duplicate submissions.
   - If a submission state is unknown or interrupted, recover with the original `task_id` or `idempotency_key` via `task_status` before retrying.
   - Verify completed outputs with `read_node` / `inspect_media`.

## 3. Canvas Orchestration, Scripts, Timelines & Export

- **Canvas Nodes & Groups**: Use `read_project`, `get_project_snapshot`, `read_node`, `create_node`, `update_node`, `delete_node`, and `manage_group` to inspect and arrange nodes, edges, and groups.
- **Scripts, Storyboards & Timelines**: Use `create_script_v2` / `read_script_v2` / `edit_script_v2` / `read_timeline` / `apply_timeline_edit` for storyboard scripts and timeline editing, and `edit_audio` when exposed for standalone audio cutting/mixing.
- **Export & Delivery**: Use `export_readiness` / `export_video` / `export_status` / `task_status` to render and verify finished timelines or videos.

## 4. Delegate Specialized Production Workflows

When the user's request matches one of the specialized workflows below, hand off to and follow that dedicated skill rather than simplifying its production contract here:

- **Turn canvas work into a 16:9 paginated director treatment (`index.html` + assets + ZIP)**: Use `newtake-to-treatment`.
- **Narrative script + scene references → Newtake dual-angle scene views & 3-view character sheets → Blender 3D white-model camera previs → Seedance 2.5 live-action video**: Use `newtake-blender-live-action`.
- **Zen Piano soundtrack performance recording → 20-second horizontal cross-section one-take product ad**: Use `music-driven-product-ad`.
