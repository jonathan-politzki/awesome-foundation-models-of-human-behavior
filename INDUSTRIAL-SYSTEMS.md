# Industrial systems: who built what, and what kind of thing it is

The [README](README.md) holds the pretrained **person-models**. This file holds the industrial systems around them, and the distinction is the point: **most production systems are not foundation models, they are systems that serve, transfer, tokenize for, or replicate one.** Sorting them by which is which is more informative than listing them by company.

Individually many of these are replications. Collectively they are the field's strongest evidence for convergence: between 2022 and 2026 essentially every consumer platform independently arrived at the same design, tokenize behavior and pretrain one large transformer on the logs, without coordinating.

## The taxonomy

| Type | What it is | Systems here |
|---|---|---|
| **Serving architecture** | how one large offline model reaches many latency-bound production models | ExFM, the multi-stage ads stack |
| **Transfer mechanism** | what actually moves from the foundation model to the serving model, and how much survives | LoopFM, LFM4Ads |
| **Tokenization deployment** | semantic IDs rolled out in a production stack (the method itself is in [METHODS.md](METHODS.md)) | YouTube, Spotify, Snapchat |
| **Platform replication** | another company's own build of the generative-recommender recipe | Netflix GenRec, LUM, MTGR, HLLM, JD GenRec, ARGUS, PinFM, TransAct V2, GPR, RecGPT-V2 |
| **Production ranker** | a deployed feed ranker, inspectable or documented end to end | the X algorithm |
| **Domain instance** | the recipe in a specific behavioral vertical | MCM (retail), JourneyFormer (travel), BehaveGPT (academic) |

## Serving architectures and transfer mechanisms

How a trillion-parameter offline model reaches a model that must answer in milliseconds. This is where the interesting engineering is, and where the field's own measurements of *how much a representation carries* come from.

- [ExFM: External Large Foundation Model](https://arxiv.org/abs/2502.17494) · Meta, WWW 2025 (industrial, oral). The architecture paper behind GEM, which has none: one trillion-parameter FM taught offline serves many compact vertical models as students via external distillation, amortizing its cost across the fleet. The clearest public statement of the *economic* case for a behavioral foundation model.
- [LoopFM](https://arxiv.org/abs/2605.29280) · Meta 2026. Scalar distillation's "transfer ratio" **deteriorates as the teacher scales**, because one number cannot carry what a large model knows; passing intermediate embeddings as a user-keyed temporal sequence roughly doubles it (+0.5%, then +1.03% and +1.22% conversions in production). The strongest industrial evidence that the representation, not the prediction, is the deliverable.
- [LFM4Ads](https://arxiv.org/abs/2508.14948) · Tencent 2025. The fullest public account of FM→downstream transfer mechanics: user, item, and cross representations transferred at three levels into ads models for +2.45% platform-wide GMV.
- [The X algorithm (xai-org/x-algorithm)](https://github.com/xai-org/x-algorithm) · X/xAI 2026. The production For You ranker in public source: Phoenix, a transformer over tokenized sequences of viewer actions predicting 18+ action probabilities, replacing the 2023 snapshot's feature-era stack; the only top-tier feed whose feature-to-foundation transition is inspectable in code at both endpoints.

## Tokenization deployments

- [Semantic IDs for Generative Search and Recommendation at Spotify](https://research.atspotify.com/2025/9/semantic-ids-for-generative-search-and-recommendation) · Spotify 2025. Recommendation as instruction-following over semantic-ID vocabularies, with one SID space jointly trained for search and recommendation (deployment paper: [GLIDE](https://arxiv.org/abs/2603.17540)).
- [Semantic IDs for Recommender Systems at Snapchat](https://arxiv.org/abs/2604.03949) · Snap 2026. Practitioner account of rolling out semantic-ID tokenization across a recommender stack, replication evidence that "tokenize items, generate behavior" is infrastructure.

## Platform replications of the generative-recommender recipe

- [Netflix GenRec](https://arxiv.org/abs/2608.10257) · Netflix 2026. LLM-backbone ranker over verbalized user histories, served prefill-only; the paradigm claim: "from feature engineering to context engineering, from bespoke architectures to shared foundation backbones."
- [TransAct V2](https://arxiv.org/abs/2506.02267) · Pinterest 2025. Lifelong user action-sequence modeling with a next-action loss; companion [OmniSage](https://arxiv.org/abs/2504.17811) learns universal multi-entity representations driving ~2.5% sitewide gains.
- [ARGUS](https://arxiv.org/abs/2507.15994) · Yandex 2025. Autoregressive pretraining over year-long user histories (including negative feedback), scaled 3.2M→1B parameters with consistent gains at every step.
- [Large User Model (LUM)](https://arxiv.org/abs/2502.08309) · Alibaba, WSDM 2026. Explicitly named a "Large User Model": power-law improvements up to 7B parameters and +2.9% CTR in Taobao sponsored search.
- [MTGR](https://arxiv.org/abs/2505.18654) · Meituan, CIKM 2025. HSTU adapted while retaining DLRM cross features; confirms the generative recipe replicates at another billion-user platform.
- [HLLM](https://arxiv.org/abs/2409.12740) · ByteDance 2024. Item-LLM stacked under a User-LLM at up to 7B+7B parameters; ByteDance's [Douyin system](https://arxiv.org/abs/2511.06077) pushes behavior sequences to 10K events at billion-user scale.
- [JD.com GenRec](https://arxiv.org/abs/2604.14878) · JD, SIGIR 2026. Decoder-only generative retrieval with GRPO preference alignment over hybrid rewards; +9.5% clicks / +8.7% transactions online.
- [PinFM](https://arxiv.org/abs/2507.12704) · Pinterest 2025. Billion-scale user-sequence foundation model, cited by both Netflix and Tencent as a peer system.
- [GPR](https://arxiv.org/abs/2511.10138) · Tencent 2025. One-model generative paradigm for ads recommendation.
- [RecGPT-V2](https://arxiv.org/abs/2512.14503) · Alibaba/Taobao 2025. LLMs deployed across interest mining, retrieval, and explanation, shifting from log-fitting to intent-centric recommendation; a partial counterpoint arguing pure log-fitting amplifies filter bubbles.

## The paradigm in specific behavioral domains

- [BehaveGPT](https://arxiv.org/abs/2505.17631) · 2025. Academic counterpart: transformer pretraining over large user-behavior datasets with a DRO-based objective, evaluated on next-behavior prediction and cross-domain adaptation.
- [MCM: A Multi-task Pre-trained Customer Model](https://www.amazon.science/publications/mcm-a-multi-task-pre-trained-customer-model-for-personalization) · Amazon, RecSys 2023. A shared customer model pretrained over shopping behavior and reused across personalization tasks.
- [JourneyFormer](https://arxiv.org/abs/2606.19108) · Airbnb, KDD 2026. Encodes the multi-week guest search-to-booking journey as a transformer sequence, the paradigm in a low-frequency, high-stakes behavioral domain.
