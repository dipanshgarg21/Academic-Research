# Academic Research Portfolio: IoT Privacy, Mental Health, and Biomedical Imaging

This repository consolidates three in-depth research assets spanning accelerated biomedical image processing, culturally grounded digital mental health, and IoT privacy assurance. Each paper is preserved in PDF form for the original pagination and in companion plaintext extracts to support quick reference inside this repo. Use the summaries below to understand scope, compare findings, and decide how to apply the work in your own projects.

## Repository map

| File | Domain | Highlights |
| --- | --- | --- |
| `Advancing Healthcare Through Accelerated Biomedical Image Processing` | Biomedical imaging & AI | Outlines a physics-informed reconstruction pipeline that begins with undersampled k-space measurements, enforces Fourier-domain data consistency, and optimizes a multi-term loss blending pixel fidelity, super-resolution, and MS-SSIM similarity terms. |
| `Mental Health App Report for Indian Students` | Digital mental health | Documents the “Sahayata” concept: a B2B2C mental health app for NEET/JEE aspirants that responds to alarming suicide statistics with a tiered blend of self-help, anonymous peer support, and vetted clinicians, all tuned to exam-cycle stressors. |
| `Smart Speakers Privacy Breach` | IoT privacy & governance | Investigates how Amazon Alexa, Google Assistant, and Apple Siri routed private recordings to thousands of human reviewers because of wake-word failures and weak consent, then prescribes technical and policy mitigations for future voice-first systems.|

---

## 1. Accelerated Biomedical Image Processing

### Research focus
The imaging manuscript formalizes the data pathway from raw, mask-sampled k-space (`y = M^ x_k_out`) through a zero-filled inverse Fourier reconstruction (`x_ZF = F^{-1}(y)`) toward a refined output (`x_rec`) that honors the acquired lines while hallucinating the missing ones. The notation emphasizes explicit data-consistency terms (`F^{-1}` operators and `M` sampling masks) to keep the learned solution anchored to the scanner physics.

### Methodological insights
* **Composite optimization target.** The objective `L_total = L_recon + L_SR + L_MS-SSIM` demonstrates how fidelity losses, perceptual quality (via MS-SSIM), and optional super-resolution branches can be trained jointly to recover clinically faithful images from sparse measurements.
* **Zero-filled baselines as supervision.** By defining `x_ZF = F^{-1}(y)` and reusing it inside the loss, the approach penalizes deviations from both the measurement-consistent reconstruction and the high-resolution ground truth, which is a common strategy for turbo-charging iterative MRI or CT solvers with deep learning priors.

### Practical takeaways
* When adapting the method to a new modality, keep separate data-consistency and perceptual terms so that rare structures (e.g., lesions) are preserved even as textures are sharpened.
* Track each loss component during training; the original formulation exposes them individually, which makes it easier to diagnose whether artifacts stem from under-fitting the reconstruction term or over-emphasizing MS-SSIM.

---

## 2. “Sahayata” – Mental health infrastructure for Indian exam aspirants

### Why this matters
The NCRB recorded 13,892 student suicides in 2023, a 64.9% rise over the past decade, and one in five adolescents report rarely feeling calm, motivated, or excited. The crisis peaks around NEET/JEE milestones, producing predictable windows of heightened self-harm risk that current generic wellness apps fail to address.

### Solution blueprint
* **Tiered care model.** Sahayata’s foundation is a three-tier experience: Tier 1 provides universally accessible CBT, mindfulness, and positive-psychology modules; Tier 2 offers moderated, anonymous peer forums; Tier 3 unlocks paid sessions with vetted adolescent specialists. This progression lowers stigma by letting users self-select the depth of engagement.
* **Exam-cycle awareness.** Dedicated modules target the long preparation haul, the pre-exam sprint, and the post-result aftermath with tailored guidance on burnout prevention, performance anxiety, and coping with disappointment, mirroring the calendar-driven spikes in distress.
* **Feature system.** Onboarding diagnostics feed a personalized dashboard (“The Daily Dose”), crisis handling lives under “The Pressure Valve” (with Tele-MANAS escalation), the “Study Zone” embeds Pomodoro timers and focus soundscapes, and “The Common Room” plus the parent portal keep communities and caregivers informed.
* **Distribution strategy.** A B2B2C go-to-market plan aligns with coaching centers and schools so that support is embedded where aspirants spend most of their time, solving the reach problem while capturing outcome data for continuous improvement.

### Implementation cues
* Instrument analytics per tier to verify that students progress from self-help to human care when needed, mirroring the measurable pathway envisioned in the report.
* Localize all media (guided meditations, parental explainers, etc.) in multiple Indian languages to keep the trust gains documented in the content strategy section.

---

## 3. Smart speaker privacy breach analysis

### What happened
Investigations uncovered that Amazon, Google, and Apple routed both deliberate and accidental recordings to large pools of human reviewers to improve speech models, despite consumer expectations that “always listening” devices would rely solely on automation. False wake-word activations, opaque consent wording, and expansive storage pipelines meant sensitive domestic and business conversations were routinely exposed without users’ knowledge.

### Research contributions
* **Ecosystem framing.** The report synthesizes market penetration data (>80% awareness), usability challenges unique to conversational interfaces, and user personification behaviors (“para-friends”) to explain why trust was high even as privacy literacy lagged.
* **Technical anatomy.** Detailed coverage of the cloud workflow, wake-word filters, ASR, NLU, response generators, and QA dashboards, shows exactly where human reviewers entered the loop and why their access rights became the weakest link.
* **Policy & design levers.** Literature cited in the report calls for layered privacy filters (e.g., wake-word plus “sensitive word banks”), fine-grained data retention controls, and transparency resets so that consumers can calibrate consent to actual risk.

### Applying the lessons
* Treat human-in-the-loop QA as sensitive data processing that demands explicit opt-in, audit trails, and, ideally, on-device redaction before samples leave the home network.
* Incorporate specialized voice usability testing (e.g., Voice Usability Scale) alongside threat modeling so that delightful experiences do not mask latent surveillance vectors.

---

## Cross-domain themes and next steps

1. **Human-centered safeguards.** Whether you are reconstructing MRI volumes, triaging adolescent distress, or tuning wake words, the artifacts show that data fidelity and psychological safety are inseparable. Loss functions, care tiers, and consent flows should be audited just as rigorously as your models.
2. **Explainability for trust.** All three studies document user trust gaps that patients need to know how physics priors constrain AI, students need culturally resonant guidance, and households need clarity about who hears their recordings. Align your documentation, product copy, and outreach with those expectations.
3. **Operational analytics.** Capture per-module metrics (loss curves, mental-health outcomes, privacy incident reports) so that stakeholders can prove compliance and effectiveness over time.
