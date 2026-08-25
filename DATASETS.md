# Datasets behind foundation models of human behavior

These are the data substrates that the models in the [README](README.md) actually train and evaluate on, grouped by access level, with the papers that use each. Access is the field's binding constraint: the public tier is small and narrow, the richest longitudinal substrates sit behind applications, and the largest corpora are platform logs no outsider can touch. Scale claims are as reported in the cited papers.

## Public

- **MovieLens 25M**. Movie rating and interaction sequences with timestamps and text metadata; the standard sequential-recommendation substrate. Used by: RecFound-style unified recommendation FMs and the SASRec/BERT4Rec lineage of baselines.
- **Amazon Reviews 2023** (McAuley lab). Product interaction sequences with rich item text across dozens of categories. Used by: RecFound-style work, UniSRec-lineage transfer studies, HumanLLM (as one of its public trace sources).
- **Psych-101** ([paper](https://arxiv.org/abs/2410.20268)). Trial-by-trial choices from 60K+ participants, ~10M choices across 160 psychology experiments. Used by: Centaur, Small Foundation Models of Human Cognition and Behaviour.
- **SocSci210** ([data](https://huggingface.co/socratesft)). 2.9M individual responses from 400K participants across 210 open social-science experiments, with seen/unseen-study splits. Used by: Socrates.
- **choices13k**. ~13K risky-choice problems from large-scale decision experiments. Used by: Peterson et al. (Science 2021) theory discovery from prediction.
- **Twin-2K-500** ([data](https://huggingface.co/datasets/LLM-Digital-Twin/Twin-2K-500)). 2,058 US participants answering 500+ questions across four waves, with a held-out wave as per-person ground truth. Used by: digital-twin benchmarking.
- **OdysSim corpus** ([paper](https://arxiv.org/abs/2606.14199)). 21.4M interactions / 10B tokens aggregated from 62 behavioral datasets. Used by: OdysSim (OSim).
- **HUMANUAL** ([code](https://github.com/zou-group/humanlm)). Six public-data collections: 23K users, 227K responses (daily-life issues, political blogs, chat sessions). Used by: HumanLM.
- **Cognitive Genome** ([code](https://github.com/microsoft/AnthropomorphicIntelligence)). 5.5M public logs from 282K identified Reddit/Twitter/Blogger/Amazon users, distilled into 1.27M QA pairs. Used by: HumanLLM.
- **MicroLens** ([paper](https://arxiv.org/abs/2309.15379)). 30M users, 1B interactions, raw short-video content; the largest content-driven recommendation dataset, built for training large behavioral models.
- **NineRec** ([paper](https://arxiv.org/abs/2309.07705)). 2M-user pretraining set plus nine downstream scenarios, including cross-platform transfer. Used by: the transferable/ID-free recommendation line (UniSRec, VQ-Rec, MoRec descendants).
- **MIND**. Microsoft news-recommendation logs. Used by: FedKD.
- **Multimodal Banking Dataset** ([paper](https://arxiv.org/abs/2409.17587)). Large public benchmark of multimodal bank-client event sequences with downstream tasks; shared evaluation infrastructure for transaction-behavior models (Sber).
- **RelBench** ([site](https://relbench.stanford.edu/start)). 11 relational databases, ~66 temporal entity-level tasks including churn, LTV, and purchase prediction. Used by: Relational Deep Learning, KumoRFM.
- **Lichess open database**. Billions of timestamped chess games, the same identified player across years, finite move vocabulary, Elo ground truth. Used by: Maia, behavioral stylometry (McIlroy-Young et al.).
- **IRC Poker Database (U. Alberta) and PHH dataset (UofT CPRG)**. ~10M hands (1995-2001) with persistent pseudonymous players, plus 21.6M anonymized real-money hands; betting sequences as fully observed style signal.
- **Taobao UserBehavior / Tmall / Yoochoose / RetailRocket**. E-commerce clickstreams with view, cart, and purchase event types; standard multi-event-type substrates for sequential behavior modeling.
- **Steam / Last.fm / Spotify Million Playlist**. Play and purchase histories over long horizons; long per-user sequences with strong habit signal.
- **Foursquare / Gowalla check-ins**. Time-and-place mobility events; a recurring substrate for next-location prediction.
- **GSS (General Social Survey, NORC)**. US attitude and behavior survey since 1972; the 2006-2014 panel waves reinterview the same respondents, enabling test-retest-normalized evaluation. Used by: Generative Agent Simulations of 1,000 People (ground truth), the genagents agent bank.
- **Mind2Web-style computer-use sets** (Mind2Web, AgentNet, OS-Genesis). Screen-level human-computer interaction traces; the substrate bridging user modeling and computer-use agents.

## Gated / application-required

- **UK Biobank**. Long-horizon health timelines of UK participants. Used by: Delphi-2M (training; forecasting 1,000+ diseases ~20 years out).
- **Danish national registries** (Statistics Denmark). Health, education, job, income, and address events at day resolution for the whole population. Used by: life2vec (training), Delphi-2M (external validation on 1.9M Danes).
- **Italian social-security records (INPS)**. Administrative work and income trajectories. Used by: Life Sequence Transformer.
- **Epic Cosmos**. 118M patients, 115B medical events pooled across Epic health systems; research access through the Epic community. Used by: CoMET.
- **Longitudinal panels** (PSID, NLSY79/97, HRS, Add Health, MIDUS, German SOEP, UK birth cohorts). Decades-long trajectories of the same individuals: income, health, family, attitudes. Free with registration; licenses prohibit re-identification, so they support trajectory modeling but not named personas. Used by: LifeSentence-style panel work.
- **genagents interview tier** (Stanford, by application). The 1,000 two-hour interviews and individual ground-truth responses behind Generative Agent Simulations of 1,000 People; the demographic agent tier is public.
- **Screenomics screen logs** (IRB-restricted). 20 users, one month, 1.9M screenshots captioned into 360K actions. Used by: LongNAP.

## Private / proprietary

These are not obtainable, but they define the field's frontier; company, claimed scale, and reporting paper.

- **Meta action streams**. User action sequences across Meta surfaces; HSTU deployed at 1.5T parameters with +12.4% online gains; GEM trained on thousands of GPUs, +5% Instagram ad conversions. Papers: HSTU, GEM.
- **Netflix member histories**. Tokenized interaction histories of all members; production models scaled 2M to 1B parameters. Papers: Netflix Foundation Model, GenRec, Netflix scaling study.
- **Kuaishou logs**. Short-video interaction streams at 400M+ DAU. Paper: OneRec.
- **ByteDance / Douyin logs**. Behavior sequences up to 10K events per user at billion-user scale; 7B+7B item/user models. Papers: HLLM, Douyin system.
- **Alibaba / Taobao logs**. Commerce behavior at platform scale; power-law gains up to 7B parameters, +2.9% CTR in Taobao sponsored search. Papers: LUM, RecGPT-V2.
- **Ant Group / Alipay logs**. Billion-user payments and behavior data. Paper: Towards a Densing Law for User Representation Learning.
- **LinkedIn member histories**. Verbalized professional activity serving 30+ ranking tasks with one 150B model. Paper: 360Brew.
- **Pinterest action streams**. Lifelong user action sequences; billion-scale user-sequence FM, ~2.5% sitewide gains. Papers: PinnerFormer, TransAct V2, OmniSage, PinFM.
- **Yandex user histories**. Year-long histories including negative feedback; models scaled 3.2M to 1B parameters. Paper: ARGUS.
- **Tencent ads logs**. Billions of daily samples; FM representations transferred into ads models for +2.45% platform GMV. Papers: LFM4Ads, GPR.
- **Meituan logs**. Billion-user local-commerce platform traffic. Paper: MTGR.
- **Amazon shopping behavior and Airbnb guest journeys**. Shared customer model pretrained over shopping behavior (MCM); multi-week search-to-booking sequences (JourneyFormer).
- **Visa transaction network**. Consumer transactions plus payment-network signals; TransactionGPT reports +22.5% over the production model. Papers: TREASURE, TransactionGPT.
- **Stripe / Plaid / Mastercard / Nubank transactions**. Stripe trained on tens of billions of transactions; Plaid trains one model across ~12,000 institutions; Mastercard and Nubank run analogous builds. Source: industry writeups in the README.
- **Sber client streams**. Banking transactions, online interactions, and communications unified into one event stream, deployed at a major bank. Papers: CoLES, LATTE, Sber multimodal event FM.
- **Unbox AI retail corpus**. Anonymized retail events, ~10^8 unique actions and ~10^9 event tokens, used for ~600 scaling-law runs across 10^15-10^19 FLOPs. Paper: Scaling Laws for Behavioral Foundation Models.
- **Simile training data**. Grocery and delivery-app transactions plus AI-led voice interviews and surveys, fine-tuning a Qwen3.5-27B simulation model. Source: Building Confidence in Simile.
- **Markopolo AI clickstreams**. Sequences from 603 independent businesses (e-commerce, SaaS, streaming) behind the 709M-parameter edge model ATHENA.

## Observations

- The public tier is dominated by two narrow slices of human behavior: e-commerce and media clicks on one side, lab psychology and survey experiments on the other. Almost nothing public is naturalistic, longitudinal, and per-person at once.
- The life-trajectory substrate (national registries, biobanks, longitudinal panels) is entirely gated, and panel licenses prohibit the re-identification that individual-level simulation work would require.
- The largest substrates are all private platform logs, orders of magnitude beyond anything public; every headline scaling result in the field is unreproducible outside the company that reported it.
- No dataset at any access level follows the same person across multiple life domains: the cross-domain, cross-platform record of one individual, arguably the substrate the field's thesis most needs, does not yet exist in shareable form.
