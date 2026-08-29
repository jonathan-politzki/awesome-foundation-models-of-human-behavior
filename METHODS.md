# Methods

How foundation models of human behavior get built. The models themselves are in the [README](README.md).

## Transferable & ID-Free Recommendation

The recsys line that matters most here: does a user/item representation transfer across domains and platforms? A curated deep-dive lives at [Recommendation Systems without Explicit ID Features](https://github.com/westlake-repl/Recommendation-Systems-without-Explicit-ID-Features-A-Literature-Review) (Westlake).

- [PeterRec](https://arxiv.org/abs/2001.04253) · Tencent, SIGIR 2020. The first explicit claim that self-supervised pretraining on behavior sequences yields **universal user representations**, evaluated by user-profile prediction on held-out tasks, the probing protocol, invented here, and released with the ColdRec datasets. Adapters ("model patches") over a dilated-CNN backbone, i.e. the first universal user model was built without attention.
- [Conure](https://arxiv.org/abs/2009.13724) · SIGIR 2021. "One Person, One Model, One World": the first *lifelong/continual* user representation, handling forgetting by iterative weight pruning rather than adapters; nine tasks, one model, offline only.
- [CAT-ART](https://arxiv.org/abs/2211.11964) · Tencent + Alberta, WSDM 2023. Contrastive autoencoder learns a **global** user embedding across five domains while attention transfers **domain-specific** embeddings between them; a multi-target formulation where all participating domains improve at once.
- [Mind the Gap: Bridging Behavioral Silos with LLMs](https://arxiv.org/abs/2606.06779) · DoorDash, RecSys 2025 workshop. Hierarchical RAG turns restaurant orders and search queries into taxonomic features that personalize a *different* vertical (grocery) with no shared items; the LLM-as-interlingua argument, deployed.
- [UniSRec](https://arxiv.org/abs/2206.05941) · KDD 2022. Item text replaces IDs; contrastive multi-domain pretraining transfers cross-domain and cross-platform, the citable moment the field named the retraining problem and chose a foundation-model-shaped answer.
- [VQ-Rec](https://arxiv.org/abs/2210.12316) · WWW 2023. Text → discrete codes → representation; its item codes are semantic IDs by an independent route, converging with TIGER's RQ-VAE tokens.
- [Recformer ("Text Is All You Need")](https://arxiv.org/abs/2305.13731) · KDD 2023. Items as flattened attribute sentences, no IDs anywhere; strongest in cold start.
- [MoRec](https://arxiv.org/abs/2303.13835) · SIGIR 2023. The systematic ID-vs-modality showdown: modality-based items beat ID embeddings in cold start and match them hot, but only trained end-to-end; frozen-feature pipelines lose badly.
- [MISSRec](https://arxiv.org/abs/2308.11175) · ACM MM 2023. Multi-modal interest-aware sequence pretraining and transfer.
- [NineRec](https://arxiv.org/abs/2309.07705) · 2023. The transfer benchmark suite (2M-user pretraining + nine downstream scenarios incl. cross-platform), confirming zero-shot cross-platform transfer from pure modality signal.

## Tokenization & Semantic IDs

Turning items and events into a bounded vocabulary a model can generate over. The design choice that separates this literature from language modeling: text tokenizers compress by *frequency*, semantic IDs compress by *similarity*, which is why the compression scheme doubles as a generalization scheme.

- [Recommender Systems with Generative Retrieval (TIGER)](https://arxiv.org/abs/2305.05065) · Google DeepMind, NeurIPS 2023. Origin of Semantic IDs: RQ-VAE-quantized content embeddings turn items into token tuples, making next-item recommendation literal next-token generation.
- [Better Generalization with Semantic IDs](https://arxiv.org/abs/2306.08121) · Google/YouTube, RecSys 2024. Semantic IDs replace raw video IDs in YouTube production ranking, improving generalization to fresh content.

## Scaling Laws for Behavior

- [HSTU scaling result](https://arxiv.org/abs/2402.17152) · Meta, ICML 2024. Model quality follows a power law in training compute across three orders of magnitude "up to GPT-3/LLaMa-2 scale", the first industrial demonstration that behavioral logs scale like text.
- [Scaling Laws for Behavioral Foundation Models over User Event Sequences](https://research.unboxai.com/scaling-laws-for-behavioral-foundation-models.pdf) · Unbox AI 2026. The Chinchilla-style calibration: ~600 runs across 10^15–10^19 FLOPs on real retail events; compute-optimal event embedders are small (~2% of parameters), the optimal data/model ratio drifts from 344 toward the text ratio with compute, and the evaluation metric is itself part of the scaling law.
- [Wukong](https://arxiv.org/abs/2403.02545) · Meta, ICML 2024. Scaling law for large-scale recommendation via stacked factorization machines.
- [Kunlun](https://arxiv.org/abs/2602.10016) · Meta 2026. Scaling laws for massive-scale recommendation through unified architecture design.
- [LLaTTE](https://arxiv.org/abs/2601.20083) · Meta 2026. Scaling laws for **multi-stage** sequence modeling in ads recommendation: an offline model over long histories produces cached embeddings, an online ranker combines them with real-time signals. The companion [engineering post](https://engineering.fb.com/2026/08/05/ml-applications/from-user-sequences-to-scaling-laws-a-multi-stage-architecture-for-metas-ads-ranking/) reports log-linear gains in compute and the finding that **"sequence diversity beats sequence homogeneity"**, a balanced mix of action types yields "richer behavioral representations of users" than homogeneous sequences of high-signal actions.
- [Scaling Law of Large Sequential Recommendation Models](https://arxiv.org/pdf/2311.11351) · RecSys 2024. Power-law loss curves in model/data size on pure interaction sequences, with scaled models disproportionately better on hard long-tail predictions.
- [Scaling Sequential Recommendation Models with Transformers](https://arxiv.org/abs/2412.07585) · 2024. The second clean academic scaling study; honest about behavioral data being scarcer and sparser than text, so data is often the binding constraint.
- [Towards Generalizable and Efficient Large-Scale Generative Recommenders](https://arxiv.org/abs/2605.23312) · Netflix, RecSys 2026. Scales a production generative recommender 2M→1B parameters and finds scaling is heterogeneous across downstream tasks, some plateau, some keep improving.
- [CoMET scaling study](https://arxiv.org/abs/2508.12104) · Microsoft/Epic 2025. The largest event-sequence scaling law: 118M patients, clean power laws in compute/tokens/parameters.
- [Towards a Densing Law for User Representation Learning at Billion-Scale Capacity](https://arxiv.org/abs/2608.23392) · Ant Group/Alipay 2026. A scaling law for the tokenizer itself: minimum sufficient tokenization capacity grows log-linearly with behavioral data size, validated at billion-user scale.
- [Embedding collapse when scaling recommenders](https://arxiv.org/abs/2310.04400) · 2023. The failure mode behind "recsys didn't scale before generative reformulation."
- [Emergent Abilities of Large Language Models](https://arxiv.org/abs/2206.07682) · TMLR 2022. Frames the expectation that qualitatively new behavioral-modeling capabilities appear discontinuously with scale, and that small-scale pilots may falsely refute the paradigm.
- [Are Emergent Abilities a Mirage?](https://arxiv.org/abs/2304.15004) · NeurIPS 2023. Most claimed emergence is an artifact of discontinuous metrics; behavioral emergence claims should be made on continuous metrics first.
- [Small Foundation Models of Human Cognition and Behaviour](https://arxiv.org/abs/2608.05224) · 2026. On Psych-101, 0.6B–1B models match a 70B in-distribution while OOD generalization shows a steep scaling gradient, scale buys generalization, not in-distribution fit.

## Federated & Cross-Silo

- [Halo / Origin / Aquila](https://halo.wfanet.org/) · WFA, ISBA, ANA, 2019–present. The advertising industry's cross-media measurement program, with Meta, Google, Amazon, Snap and TikTok participating: 250k+ lines of open-source code including a **Virtual ID** schematic and private reach-and-frequency processing, so publishers compute deduplicated cross-company reach without exchanging identities. The most serious attempt at cross-organizational person coordination on record, and after six years the achievable shared person-fact is still a *count*, not a representation.
- [PFCR: Prompt-enhanced Federated Content Representation Learning](https://arxiv.org/abs/2401.14678) · WWW 2024. Cross-domain federated recommendation with no overlapped-user requirement: content-grounded item representations dissolve the shared-ID blocker.
- [TransFR](https://arxiv.org/abs/2402.01124) · 2024. Frozen-PLM text encodings as universal content representations, freeing federated recommendation from shared ID tables.
- [FedKD](https://arxiv.org/abs/2108.13323) · Nature Communications 2022. Federated mutual distillation, evaluated on news recommendation.
- [The Future of LLM Pre-training is Federated (Photon)](https://arxiv.org/abs/2405.10853) · Flower Labs/Cambridge, MLSys 2025. First system for federated end-to-end LLM pretraining (1.3B and 7B from scratch across organizations), the current ceiling of the paradigm; federated *behavioral*-FM pretraining remains an empty rung.
- [Navigating the Future of Federated Recommendation Systems with Foundation Models](https://arxiv.org/abs/2406.00004) · 2024. Position survey of the FL×FM×recsys intersection: where the FM helps the federated system, and the standing privacy/non-IID challenges.
- [Ten Challenging Problems in Federated Foundation Models](https://arxiv.org/abs/2502.12176) · TKDE 2025. The field's own problem map, notably omitting cross-client vocabulary/schema alignment, the interchange problem behavioral silos actually face.
- [FILM: Recovering Private Text in Federated Learning](https://arxiv.org/abs/2205.08514) · Princeton, NeurIPS 2022. Verbatim training text recovered from federated gradients, a standing caution that federation alone is not anonymity.

## Objectives, Representations & Theory

- [Representation Learning: A Review and New Perspectives](https://arxiv.org/abs/1206.5538) · Bengio et al., TPAMI 2013. The theoretical root: learning as disentangling the underlying factors of variation, "understand a person = recover the latent factors behind their behavior," stated a decade early.
- [Emergent World Representations (Othello-GPT)](https://arxiv.org/abs/2210.13382) · ICLR 2023. A GPT trained only to predict moves develops an internal, causally manipulable model of board state, the existence proof that predictive objectives induce probe-decodable world models.
- [Othello-GPT Has a Linear Emergent World Representation](https://arxiv.org/abs/2309.00941) · BlackboxNLP 2023. The representation is linear and steerable once probed in the frame the objective incentivizes, a lesson for probing behavioral models.
- [Language Models Represent Space and Time](https://arxiv.org/abs/2310.02207) · ICLR 2024. Linear, unified representations of geography and history crystallize from text prediction alone, real-world latent structure as a byproduct of prediction.
- [The Platonic Representation Hypothesis](https://arxiv.org/abs/2405.07987) · ICML 2024. Representations of scaled models trained on different data and objectives converge toward a shared statistical model of reality, with implications for aligning behavioral and language person-representations.
- [Sparse Autoencoders Find Highly Interpretable Features](https://openreview.net/forum?id=F76bwRSLeK) · ICLR 2024. Dictionary learning decomposes model activations into sparse, near-monosemantic features, the tool for asking whether a learned representation contains recoverable human factors.
- [Language Modeling Is Compression](https://arxiv.org/abs/2309.10668) · DeepMind, ICLR 2024. Next-token predictors are lossless compressors; compressing many people's logs pressures a model to discover shared generative structure, goals, routines, constraints.
- [Evaluating LLMs in Theory of Mind Tasks](https://www.pnas.org/doi/10.1073/pnas.2405460121) · Kosinski, PNAS 2024. False-belief performance emerged across GPT generations without ToM training, agent models induced from prediction over traces of agents.
- [LLMs Fail on Trivial Alterations to Theory-of-Mind Tasks](https://arxiv.org/abs/2302.08399) · Ullman 2023. The standard rebuttal: small perturbations collapse performance, mandating adversarial evaluation of any claimed intent understanding.
- [Algorithms for Inverse Reinforcement Learning](https://ai.stanford.edu/~ang/papers/icml00-irl.pdf) · Ng & Russell, ICML 2000. The founding statement of "infer the human from behavior" and its central obstacle: preferences are underdetermined by observed behavior.
- [Causal Confusion in Imitation Learning](https://arxiv.org/abs/1905.11979) · NeurIPS 2019. Behavior-cloned predictors latch onto spurious correlates; resolving the true causal model requires interventions logs alone do not provide.
- [Shaking the Foundations: Delusions in Sequence Models for Interaction and Control](https://arxiv.org/abs/2110.10819) · DeepMind 2021. Sequence models trained on logged agent data confuse observation with intervention; the fix is giving action tokens intervention semantics.
- [Passive Learning of Active Causal Strategies](https://arxiv.org/abs/2305.16183) · NeurIPS 2023. The optimistic counterpoint: passive training on demonstrations containing experimentation can teach generalizable causal strategies.
- [Understanding Internal Representations of Recommendation Models with Sparse Autoencoders (RecSAE)](https://dl.acm.org/doi/10.1145/3795529) · ACM TOIS 2025. Othello-style probing ported to user models: interpretable intents and interest clusters extracted from sequential recommenders.
