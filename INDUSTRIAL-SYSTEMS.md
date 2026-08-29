# Industrial behavioral foundation models: the per-company ledger

The [README](README.md) keeps the systems that established a distinct claim. This file holds the rest: each major platform's own build of the same recipe, plus the domain-specific instances. Individually these are replications. Collectively they are the strongest evidence the field has for convergence, which is why they are kept rather than dropped: between 2022 and 2026, essentially every consumer platform independently arrived at the same design, tokenize behavior and pretrain one large transformer on the logs, without coordinating.

Read this file when you want to know *how widely* the paradigm replicated. Read the README when you want to know *what it established*.

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

## Semantic-ID deployments beyond the originating paper

- [Semantic IDs for Generative Search and Recommendation at Spotify](https://research.atspotify.com/2025/9/semantic-ids-for-generative-search-and-recommendation) · Spotify 2025. Recommendation as instruction-following over semantic-ID vocabularies, with one SID space jointly trained for search and recommendation (deployment paper: [GLIDE](https://arxiv.org/abs/2603.17540)).
- [Semantic IDs for Recommender Systems at Snapchat](https://arxiv.org/abs/2604.03949) · Snap 2026. Practitioner account of rolling out semantic-ID tokenization across a recommender stack, replication evidence that "tokenize items, generate behavior" is infrastructure.

## The paradigm in specific behavioral domains

- [BehaveGPT](https://arxiv.org/abs/2505.17631) · 2025. Academic counterpart: transformer pretraining over large user-behavior datasets with a DRO-based objective, evaluated on next-behavior prediction and cross-domain adaptation.
- [MCM: A Multi-task Pre-trained Customer Model](https://www.amazon.science/publications/mcm-a-multi-task-pre-trained-customer-model-for-personalization) · Amazon, RecSys 2023. A shared customer model pretrained over shopping behavior and reused across personalization tasks.
- [JourneyFormer](https://arxiv.org/abs/2606.19108) · Airbnb, KDD 2026. Encodes the multi-week guest search-to-booking journey as a transformer sequence, the paradigm in a low-frequency, high-stakes behavioral domain.
