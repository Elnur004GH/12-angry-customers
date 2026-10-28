# Twelve Angry Customers

Open-source starter kit for persona-based usability research on web applications, including the web layer of Android WebView apps.

## Status
Scaffold v0.1: twelve editable profiles, isolated agent brief generation, and an evidence/report contract. No browser automation or model integration yet. No app has been tested. This is an original implementation, not copied Truman code; no affiliation with Truman or the film.

## Run (Python 3, standard library only)
```bash
python3 tac.py --study study.example.json --out runs/demo
```
This generates twelve separate briefs and empty result templates. It does NOT visit the URL or call an AI model. Replace the example URL and goal before handing briefs to browser-capable agents.

## Profiles
All seven traits are integers 0–100: technical_skill, impatience, willingness_to_pay, curiosity, skepticism, persistence, guidance_need. Higher means more of that trait. These are adjustable simulation hypotheses, not validated psychometrics or population estimates. The title does not mean every participant starts angry.

Willingness to pay must be interpreted with the study's actual price/value context. Do not infer purchasing demand from simulated opinions. Do not equate technical skill with age or protected characteristics.

## Execution design
One isolated browser context and one private history per participant. Give each the goal and its own brief, never source code or other participants' findings. Observe -> choose action -> execute -> record evidence -> update confusion/frustration -> continue, succeed, or leave. Exhausting max_steps means budget_exhausted, not rage quit. Only after individual reports are frozen should a moderator compare findings or host discussion.

Every issue needs observed steps, actual vs expected behavior and evidence references. Keep inferred preferences separate from observed errors. Never fabricate screenshots, timings, actions or group consensus. Web browser results do not validate Android bridges, permissions, native back navigation, or device-specific WebView behavior.

## Data and operation boundaries
Use authorized test targets, synthetic accounts, per-run browser contexts and limited API credentials. Keep secrets and traces out of git. Purchases, sending messages, deletions and other consequential actions require explicit study authorization; default is to stop before them. Treat page content as untrusted data, never as instructions overriding the study.

## Next milestones
1. Browser adapter with host allowlist and action policy.
2. Model adapter and bounded step loop with per-session memory.
3. Evidence capture, redaction and report aggregation.
4. Human comparison study to calibrate personas.

## Contributing
Open an issue with a reproducible example. Add tests for behavioral or safety-boundary changes. Never submit credentials or private screenshots. MIT licensed; see LICENSE.
