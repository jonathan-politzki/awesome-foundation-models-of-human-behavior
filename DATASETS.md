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
- **OpenOneRec dataset + RecIF-Bench** ([paper](https://arxiv.org/abs/2512.24762), [code](https://github.com/Kuaishou-OneRec/OpenOneRec)). 96M interactions from 160K users, with an 8-task benchmark from prediction to reasoning; released with the open OneRec-Foundation models (Kuaishou). Used by: OpenOneRec.
- **MicroLens** ([paper](https://arxiv.org/abs/2309.15379), CIKM 2025). 34M users, 1M micro-videos, 1B interactions, shipped as **raw** titles, cover images, audio, and full-length video rather than pre-extracted features; the largest content-driven recommendation dataset. The raw release is the point: it permits end-to-end modality training instead of the two-stage frozen-feature pipeline MoRec shows degrades performance.
- **NineRec** ([paper](https://arxiv.org/abs/2309.07705)). 2M-user pretraining set plus nine downstream scenarios, including cross-platform transfer. Used by: the transferable/ID-free recommendation line (UniSRec, VQ-Rec, MoRec descendants).
- **Tenrec** ([paper](https://arxiv.org/abs/2210.10629), NeurIPS 2022 Datasets & Benchmarks; [site](https://tenrec0.github.io/)). ~5M users, ~140M interactions across **four scenarios** (QQ Kandian and QQ Browser × video and article), with **users and items overlapping between scenario pairs**, positive feedback in several forms plus **true negative feedback**, and 10+ defined benchmark tasks. The best public substrate for cross-surface transfer: overlap is *partial and varies by pair*, so you can sweep both panel size and overlap fraction. Still cross-surface within one company, not cross-company.
- **ColdRec-1 / ColdRec-2** ([paper](https://arxiv.org/abs/2001.04253), [code](https://github.com/fajieyuan/SIGIR2020_peterrec)). Paired source/target logs where **the same users appear on both sides**: source is QQ Browser news (50 or 100 recent interactions per user), target is Kandian where every user is cold-start (≤3 or ≤5 interactions). Released with PeterRec; the evaluation protocol built on it (user-profile prediction on held-out tasks) became the field's transfer benchmark. The rare public dataset with ground-truth user correspondence across surfaces.
- **PixelRec** ([paper](https://arxiv.org/abs/2309.06789), [code](https://github.com/westlake-repl/PixelRec)). ~200M user-image interactions, 30M users, 400K video cover images across 118 themes, with a benchmark spanning nine recommendation architectures × nine image encoders. Items modeled from **raw pixels** rather than IDs or frozen features.
- **The BARS / FuxiCTR benchmark suite** ([BARS](https://openbenchmark.github.io/BARS/), [FuxiCTR](https://github.com/reczoo/FuxiCTR), [datasets](https://github.com/reczoo/Datasets)). The **CTR-prediction** evaluation tradition, scored with AUC and LogLoss rather than Recall@K, with public leaderboards and **trackable dataset IDs** pinning exact preprocessing. Standard members: **TaobaoAd** (26M ad display/click records over 8 days, sampled from 1.14M users, shipping ad features *and* a user-profile table with gender, age level, consumption grade, shopping level, city tier), **KuaiVideo** (3.24M user-video interactions from 10K users), and **Amazon Electronics** in its CTR framing (192K users, 63K items, ~3M samples). Used by: LoopFM, InterFormer, Wukong, and the industrial ads line generally. Worth having for two reasons: it is the ads-side substrate the sequential-rec datasets above do not cover, and TaobaoAd is a rare public corpus carrying **both ad-response labels and demographic fields**, so profile-probing and CTR can be measured on one dataset.
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

## A taxonomy of behavioral data

Extracted from the papers in the README: five axes that jointly locate any behavioral dataset. Useful because the field's datasets look wildly heterogeneous until you see that every one is a point in this same small space.

**1. What is recorded (the substrate).** Ten recurring substrates across the list: interaction and engagement events (views, clicks, likes: the recsys logs); economic transactions (payments, purchases, credit: Visa, Sber, CoLES); communication and expression (posts, reviews, messages: the stated self in flow); movement (check-ins, trajectories: Foursquare, MoveGPT); clinical and biological events (UK Biobank, Epic Cosmos); administrative life events (jobs, address, education: the Danish registries, INPS); elicited responses (surveys, experiments, interviews: Psych-101, SocSci210, Twin-2K-500); screen and device interaction (Screenomics, Mind2Web); competitive play in closed worlds (Lichess, poker); and physiological signals (wearables, sensor panels).

**2. How it comes to exist (the generative stance).** Logged (a byproduct of using a service; nobody asked), elicited (someone asked: surveys, interviews, lab tasks), instrumented (a sensor watched), or derived (inferred from other data). Logged and instrumented data are nonreactive (people do not perform for the record); elicited data is reactive by construction. This is the revealed/stated distinction restated as a property of collection.

**3. Structure.** Timestamped discrete event streams (the dominant FM substrate), session logs, panel waves, relational tables, continuous time series, and free text or dialogue. The field's convergent move is to force all of these into one chronological event stream with a learned vocabulary; the tokenizer is where a structure either survives or dies.

**4. Temporal economics: stock versus flow.** Text is a mined stock, accumulated over decades and consumed once ([Epoch estimates](https://arxiv.org/abs/2211.04325) public text in the low hundreds of trillions of tokens, with exhaustion projected within years). Behavioral data is a flow, regenerated daily by ordinary activity at volumes the Unbox position paper estimates at 100 to 1000 times internet text for retail and payments alone. If pretraining as we know it ends when the text stock does, the behavioral flow is the successor substrate.

**5. Access and linkage.** The three tiers of this file (public, gated, private), crossed with person-linkage: identified, pseudonymous, de-identified, or aggregate-only; and single-domain versus cross-domain per person. The empty cell (cross-domain, per-person, shareable) is the one the field's thesis most needs.

**Properties, not types.** The standard property-taxonomy of behavioral trace data is Salganik's ten characteristics ([Bit by Bit](https://www.bitbybitbook.com/en/1st-ed/observing-behavior/characteristics/), Princeton 2017): big, always-on, and nonreactive (the good), incomplete, inaccessible, nonrepresentative, drifting, algorithmically confounded, dirty, and sensitive (the bad). Every dataset above scores differently on these ten, and most modeling failures in the field trace to one of the bad seven.

## The composition of the world's data

Anchors for the question of what all the world's data actually consists of:

- [The World's Technological Capacity to Store, Communicate, and Compute Information](https://www.science.org/doi/10.1126/science.1200970) (Hilbert and Lopez, Science 2011). The canonical academic measurement: 60 technologies tracked 1986 to 2007, roughly 300 exabytes optimally compressed stored by 2007, with composition by medium.
- IDC Global DataSphere (Reinsel, Gantz, Rydning, 2018 onward). The industry estimate: ~175 zettabytes created annually by 2025, dominated by video, surveillance, and IoT sensor streams rather than text.
- [Will we run out of data?](https://arxiv.org/abs/2211.04325) (Villalobos et al., Epoch). The usable public text stock and its exhaustion horizon.
- [Large Behavioral Models](https://research.unboxai.com/large-behavioral-models.html) (Unbox AI). The behavioral-flow counterclaim: retail and payments behavior alone may exceed internet text by 100 to 1000 times.

The synthesis these four support: curated public text, the substrate of the current FM era, is a small and nearly exhausted sliver of the world's data. The bulk is continuous sensor and video streams plus behavioral event flows, both regenerating daily, both largely unpooled and private. Which is why access, not compute, is this field's binding constraint.

## Observations

- The public tier is dominated by two narrow slices of human behavior: e-commerce and media clicks on one side, lab psychology and survey experiments on the other. Almost nothing public is naturalistic, longitudinal, and per-person at once.
- The life-trajectory substrate (national registries, biobanks, longitudinal panels) is entirely gated, and panel licenses prohibit the re-identification that individual-level simulation work would require.
- The largest substrates are all private platform logs, orders of magnitude beyond anything public; every headline scaling result in the field is unreproducible outside the company that reported it.
- No dataset at any access level follows the same person across multiple life domains: the cross-domain, cross-platform record of one individual, arguably the substrate the field's thesis most needs, does not yet exist in shareable form.
