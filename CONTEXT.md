# Context

Material that surrounds the field without being a model or a method: how adjacent communities describe the same object, what the societal stakes are, and the neighbouring techniques that keep getting mistaken for it. The models are in the [README](README.md).

## Surveys of Adjacent Fields

- [Foundation Models for Recommender Systems: A Survey and New Perspectives](https://arxiv.org/abs/2402.11143) · 2024. The declared foil: FMs *for* recommendation, organized by the feature-based → generative → agentic arc; expanded 2025 successor [here](https://arxiv.org/abs/2504.16420).
- [Recommendation with Generative Models](https://arxiv.org/abs/2409.15173) · Deldjoo, He, McAuley et al. 2024. Book-length consolidation of generative recommendation, organized by backbone modality (ID-driven / LLM-based / multimodal), with dedicated risk and evaluation treatment.
- The 2023 LLM4Rec survey wave: [Liu et al.](https://arxiv.org/abs/2302.03735) (pretrain/prompt strategies), [Wu et al.](https://arxiv.org/abs/2305.19860) (discriminative vs. generative), [Lin et al.](https://arxiv.org/abs/2306.05817) (where × how to adapt in the pipeline), [Fan et al.](https://arxiv.org/abs/2307.02046) (pretrain/fine-tune/prompt), [Li et al.](https://arxiv.org/abs/2309.01157) (single-stage generative recommendation). All FMs-for-the-task; none takes the person-model as its object.
- [A Survey on User Behavior Modeling in Recommender Systems](https://arxiv.org/abs/2302.11087) · IJCAI 2023. The incumbent field's self-description ("UBM"): conventional / long-sequence / multi-type / side-info behavior modeling, with industrial practice notes.
- [Multimodal Pretraining, Adaptation, and Generation for Recommendation](https://arxiv.org/abs/2404.00621) · KDD 2024. Lifecycle-stage cut over content modalities, the record of recommendation escaping ID-locked vocabularies from the content side.
- [User Simulation in the Era of Generative AI](https://arxiv.org/abs/2501.04410) · Balog & Zhai 2025. The conceptual map of user simulation's three roles: user modeling, synthetic training data, and evaluation instrument.
- [User Modeling in the Era of Large Language Models](https://arxiv.org/abs/2312.11518) · Tan & Jiang 2023. The bidirectional framing (LLMs for user modeling / user modeling for LLMs); the closest thing the assistant thread has to a dedicated survey.
- [Advances in Temporal Point Processes: Bayesian, Neural, and LLM Approaches](https://arxiv.org/abs/2501.14291) · 2025. The principled framework for modeling *when* the next event happens, complementary to the transformer's *what*.
- [A Survey of Context Engineering for LLMs](https://arxiv.org/abs/2507.13334) · 2025. The discipline-founding survey of the interface layer through which person-context reaches a model.
- [Memory in the Age of AI Agents](https://arxiv.org/abs/2512.13564) · 2025. Taxonomy of memory forms (token-level / parametric / latent), the three competing answers to "where does the representation of the person live."
- [From Persona to Personalization: Role-Playing Language Agents](https://arxiv.org/abs/2404.18231) · 2024. Covers the persona-construction and role-play corner of person simulation.

## Privacy, Manipulation & Society

- [Private traits and attributes are predictable from digital footprints](https://www.pnas.org/doi/10.1073/pnas.1218772110) · Kosinski et al., PNAS 2013. Facebook Likes predict personality, orientation, and political views, the landmark demonstration that behavioral traces expose the latent person, and the field's foundational privacy warning.
- [Deep Learning with Differential Privacy](https://arxiv.org/abs/1607.00133) · CCS 2016. DP-SGD, the workhorse for training with formal privacy guarantees.
- [Learning Differentially Private Recurrent Language Models](https://arxiv.org/abs/1710.06963) · ICLR 2018. User-level DP for sequence models, the right privacy unit when one person contributes thousands of correlated events; the utility cost shrinks as the user population grows.
- [Membership Inference Attacks Against Recommender Systems](https://arxiv.org/abs/2109.08045) · CCS 2021. Practical user-level membership inference from ranked outputs alone: the better a model compresses individual histories, the more it leaks who was in training ([2025 survey](https://arxiv.org/abs/2509.11080)).
- [Reliable and Responsible Foundation Models](https://arxiv.org/abs/2602.08145) · 2026. Trust dimensions (bias, privacy, hallucination, drift) for the foundation-model era.

## Extras

Adjacent work that is load-bearing context but not itself a foundation model of human behavior.

### Prompted simulation & silicon sampling

No trained person-model; a frontier LLM's priors, steered by prompts or retrieved context, play the person. This is the null hypothesis the trained models above compete against.

- [Generative Agents: Interactive Simulacra of Human Behavior](https://arxiv.org/abs/2304.03442) · Stanford/Google, UIST 2023. The "Smallville" paper: 25 LLM agents with memory, reflection, and planning produce believable emergent social behavior, the archetype of the prompted-LLM route.
- [Generative Agent Simulations of 1,000 People](https://arxiv.org/abs/2411.10109) · Stanford 2024. Agents built from two-hour interviews with 1,052 real Americans reproduce each person's survey answers at 85% of their own test-retest reliability, the template for ceiling-normalized evaluation.
- [Homo Silicus](https://arxiv.org/abs/2301.07543) · Horton, NBER 2023. The economics-side founding paper of prompted human simulation: re-run classic behavioral-economics experiments on LLM subjects and validate against published human results (successor: [General Social Agents](https://arxiv.org/abs/2508.17407)).
- [Turing Experiments](https://arxiv.org/abs/2208.10264) · Microsoft Research, ICML 2023. Defines psychology-experiment replication as a task (ultimatum game, Milgram, wisdom of crowds) and discovers hyper-accuracy distortion: aligned models answer too correctly to be human.
- [Predicting results of social science experiments using LLMs](https://docsend.com/view/ity6yf2dansesqn6) · Stanford 2024. GPT-4-simulated responses predict treatment effects of 70 preregistered US survey experiments at r = 0.85, exceeding human expert forecasters ([demo](https://treatmenteffect.app)).
- [Out of One, Many (silicon sampling)](https://arxiv.org/abs/2209.06899) · Political Analysis 2023. The founding silicon-sampling paper: GPT-3 conditioned on demographic backstories reproduces subgroup response distributions with high "algorithmic fidelity."
- [Questioning the Survey Responses of Large Language Models](https://arxiv.org/pdf/2306.07951) · 2023–2025. Shows LLM survey responses are dominated by ordering/labeling artifacts, the prompted route measures the model's priors about groups, not people.
- [Whose Opinions Do Language Models Reflect?](https://arxiv.org/abs/2303.17548) · ICML 2023. RLHF'd models collapse onto the opinions of a narrow demographic slice, with persona steering only partially recovering population coverage.
- [Large Population Models (AgentTorch)](https://arxiv.org/abs/2409.10568) · MIT Media Lab, AAMAS 2024. Millions of agents driven by prompted LLM archetypes reproduce aggregate population dynamics without training any behavioral model, the strongest case that population-level tasks may not need learned weights.
- [CitySim: Large-Scale LLM-Driven Urban Agent Simulation](https://arxiv.org/abs/2506.21805) · Woven by Toyota 2025. Up to 1M persona-driven LLM agents in a graph model of Tokyo; aggregate time-use and commute patterns match national survey data, but on individual well-being prediction it loses to a gradient-boosting baseline (F1 0.36 vs 0.45), the population-vs-individual boundary in one paper.
- [Scaling Synthetic Data Creation with 1,000,000,000 Personas (Persona Hub)](https://arxiv.org/abs/2406.20094) · Tencent 2024. A billion LLM-imagined personas for synthetic data diversity, the instructive foil: persona diversity is cheap; fidelity to real individuals is the hard part.

### Simulation as training signal

Run the expensive person-prior offline, distill into a cheap servable model. Wins concentrate in cold-start and sparse regimes; the student inherits the simulator's priors and distortions.

- [LLMRec: Large Language Models with Graph Augmentation for Recommendation](https://arxiv.org/abs/2311.00423) · WSDM 2024. The LLM samples plausible user-item interaction edges and profiles; a graph CF model trains on the densified graph.
- [SUBER: An RL Environment with Simulated Human Behavior for Recommender Systems](https://arxiv.org/abs/2406.01631) · 2024. An RL recommender trained against LLM-simulated users generating rewards from persona and history ([code](https://github.com/SUBER-Team/SUBER); sibling: [Lusifer](https://arxiv.org/abs/2405.13362)).

### Memory & context interface

Where the person-representation lives when it is tokens rather than weights.

- [Democratizing LLMs via Personalized Parameter-Efficient Fine-tuning](https://arxiv.org/abs/2402.04401) · 2024. Per-user PEFT as a personalization mechanism, the natural per-person baseline for weight-based user modeling.
- [MemGPT](https://arxiv.org/abs/2310.08560) · UC Berkeley 2023. The OS metaphor for agent memory: the LLM pages information between context and external storage, the design that seeded the agent-memory field.
- [Mem0](https://arxiv.org/abs/2504.19413) · 2025. Production-focused successor: extracts, consolidates, and retrieves salient user memories across sessions at a fraction of full-context cost.
- [Agentic Context Engineering (ACE)](https://arxiv.org/abs/2510.04618) · 2025. Contexts as evolving curated playbooks, the token-level person-store made self-improving.

### Industry writeups (secondhand sources)

- [Training GEM at LLM scale](https://engineering.fb.com/2026/08/03/ml-applications/training-gem-at-llm-scale-meta-ads-recommendation-foundation-model/) · Meta 2026. GEM is **not** initialized from an LLM: a hybrid architecture with trillions of sparse and billions of dense parameters, trained from scratch on ad content and engagement. "LLM-scale" means infrastructure, and the counterpoint worth quoting: "AI infrastructure optimized for LLM training does not directly transfer, requiring significant innovation," because "today's data center GPUs and their software stacks are mostly optimized for LLM workloads, whereas recommendation workloads have a fundamentally different profile."
- [Sequence learning for personalized ads recommendation](https://engineering.fb.com/2024/11/19/data-infrastructure/sequence-learning-personalized-ads-recommendations/) · Meta 2024. Event-Based Features "replace traditional human-engineered sparse features as primary model inputs," and **dense tokenization** puts sparse features and behavioral events into one sequence so attention discovers feature crosses that were previously hand-built. Note the terminology: Meta's "token" is a dense vector attention reads, not a discrete code a model generates.
- [Stripe's payments foundation model](https://deepakness.com/raw/stripe-transfer-based-model/) · Stripe 2025. Trained on tens of billions of transactions; general-purpose transaction vectors sharply improve card-testing fraud detection (landscape overview [here](https://dwaynegefferie.substack.com/p/transaction-foundation-models), covering Plaid's ~12,000-institution model, Mastercard, and Nubank).
