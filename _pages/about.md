---
permalink: /
title: ""
excerpt: ""
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

{% if site.google_scholar_stats_use_cdn %}
{% assign gsDataBaseUrl = "https://cdn.jsdelivr.net/gh/" | append: site.repository | append: "@" %}
{% else %}
{% assign gsDataBaseUrl = "https://raw.githubusercontent.com/" | append: site.repository | append: "/" %}
{% endif %}
{% assign url = gsDataBaseUrl | append: "google-scholar-stats/gs_data_shieldsio.json" %}

<span class='anchor' id='about-me'></span>

Hi there! My name is Yaowen Ye (叶耀文). I am an AIDD specialist on the **AI-Driven Drug Discovery (AIDD) Team** at **PharmaBlock Sciences, Inc.** (Nanjing), where I work with Dr. Jun Lu on the autoimmune pipeline. I received my M.Sc. in Bioinformatics from **Nanjing Tech University** in 2025, where I worked with Prof. Dengming Ming on machine learning and computational biology for aging intervention — *AI for GeroScience*.

My research sits between **AI-driven drug discovery** and **geroscience**. I build knowledge graphs and multimodal deep learning models to surface novel targets and safer intervention strategies. I care a lot about the step that usually gets skipped: whether a computational result survives contact with a real pipeline — which is why I like validating predictions against clinical evidence rather than against a leaderboard.

Most recently I have been trying to understand **inflammaging** from the direction of autoimmune disease. My working hypothesis is that the mechanisms are less separable than the two literatures make them look, and that immune-cell-resolved representations are a good way to test that.

Outside the lab, I also enjoy digging into classical algorithms and AI-driven models for Texas Hold'em, I still follow game-theoretic solvers and, lately, LLM-based poker agents— imperfect information is a fun place to think. If we share interests, feel free to email me!

# 🔥 News
- *2026.04*: &nbsp;📄 The **immuneKG** preprint is now on bioRxiv, with code released on GitHub.
- *2025.09*: &nbsp;🚀 Joined the **AIDD Team at PharmaBlock Sciences** (Nanjing), working on the autoimmune pipeline.
- *2025.05*: &nbsp;📄 **SenolyticSynergy** preprint posted on bioRxiv; published in *International Journal of Molecular Sciences*.
- *2025.04*: &nbsp;🎉 Selected as **student representative** at **CASC 2025**, presenting a poster and speaking at both the Chinese and English sessions.

# 📝 Publications

<div class='paper-box'><div class='paper-box-image'><div><div class="badge">bioRxiv 2026</div><img src='images/immunekg.jpg' alt="immuneKG" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

[immuneKG: An Immune-Cell-Aware Knowledge Graph Framework for Target Discovery in Immune-Mediated Diseases](https://www.biorxiv.org/content/10.64898/2026.04.30.721823v2)

**Yaowen Ye**, Ning Qu, Xiaoqi Liang, et al., Jun Lu

[**Code**](https://github.com/YaowenYe/immuneKG) \| [**bioRxiv**](https://www.biorxiv.org/content/10.64898/2026.04.30.721823v2)
- Introduces a new entity class (**immune_cell**) and four original directed relation types — contributing **9,105 novel triples** absent from all existing biomedical KG schemas.
- Reprograms disease nodes with three novel modal feature sets quantifying immune homeostatic imbalance: **autoantibody profiles, cytokine signatures, and HLA genotypes**.
- **407,000+ training triples across 7,287 entities and 32 relation types**; predicted targets validated by clinical enrichment against Cortellis Phase II+ evidence in IBD.
</div>
</div>

<div class='paper-box'><div class='paper-box-image'><div><div class="badge">review</div><img src='images/revise_senolytics.png' alt="revise_senolytics" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

Revisiting senolytics: an anti-aging drug safety perspective.[Being revised](https://www.sciencedirect.com/journal/ageing-research-reviews)
  
**Yaowen Ye**, et al., Dengming Ming

*Ageing Research Reviews* (JCR Q1, IF = 12.4), **under second round revision**. 
- A review arguing that the anti-aging field discusses efficacy far more loudly than safety, examining the evidence across mechanism of action, dosing cycles, and administration strategy, and making the case for a shift from lifespan maximization toward healthy aging.
</div>
</div>


<div class='paper-box'><div class='paper-box-image'><div><div class="badge">SenolyticCapsule</div><img src='images/senolyticcapsule.jpg' alt="SenolyticCapsule" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

Multi-head attention-based prediction of high-safety senolytic drug combinations

**Yaowen Ye**, et al., Dengming Ming

*Journal of Nanjing Tech University (Natural Science Edition)* — Chinese core journal \| [**Code**](https://github.com/Yeaee/SenolyticCapsule)
- A multi-drug prediction model centred on senolytic **cocktail therapy**, yielding **five high-safety senolytic capsules**.
- **Three parallel feature streams** — SMILES semantic embedding, substructure fingerprints, molecular descriptors — feed a multi-head attention model, trained on **1,512 positive and 681 negative** combination samples.
- 100 candidate capsules filtered by predicted toxicity down to five combinations free of adverse drug effects.
</div>
</div>

<div class='paper-box'><div class='paper-box-image'><div><div class="badge">IJMS 2025</div><img src='images/senolyticsynergy.jpg' alt="SenolyticSynergy" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

[SenolyticSynergy: An Attention-Based Network for Discovering Novel Senolytic Combinations via Human Aging Genomics](https://www.biorxiv.org/content/10.1101/2025.05.28.655258v1.full.pdf)

**Yaowen Ye**, et al., Dengming Ming

*International Journal of Molecular Sciences* (JCR Q1, IF = 5.6) \| [**Preprint**](https://www.biorxiv.org/content/10.1101/2025.05.28.655258v1.full.pdf)
- A **multimodal attention-based network** trained on known drug-combination data to discover novel senolytic combinations for the preventive treatment of age-induced disease.
- Integrates **human aging genomics** — age-related differential genes and pathways — to embed aging-specific biological priors into the model.
- Builds a high-confidence senolytic combination database, then predicts and validates combinations with elevated synergy scores.
</div>
</div>


# 🛠 Platforms

<div class='paper-box'><div class='paper-box-image'><div><div class="badge">ADMET</div><img src='images/admet_optimizer.jpg' alt="ADMET-Optimizer" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

**ADMET-Optimizer** — Matched-Pair Transformation Console for Lead Optimization

*Project lead, PharmaBlock AIDD Team*
- Input a lead molecule, generate analogs via **interpretable matched-molecular-pair transformation rules**, predict ADMET with switchable scorer backends, and rank the candidates.
- **21 ADMET endpoints, 165 transformation rules**; a pluggable scorer architecture unifies local chemprop models and the ADMETlab 3.0 API behind one interface.
- Retrospectively benchmarked on real medicinal-chemistry cases, including **terfenadine → fexofenadine** hERG mitigation (predicted hERG risk 0.995 → 0.738 at 0.80 structural similarity).
</div>
</div>

<div class='paper-box'><div class='paper-box-image'><div><div class="badge">PK</div><img src='images/pkextract.jpg' alt="PKExtract" width="100%"></div></div>
<div class='paper-box-text' markdown="1">

**PKExtract** — Automated Pharmacokinetics Extraction & Analytics Platform

*Project lead, PharmaBlock AIDD Team*
- An AI pipeline that ingests in-vivo PK study reports in batch, identifies the source, and extracts **concentration–time profiles and derived PK parameters** (C<sub>max</sub>, T<sub>max</sub>, T<sub>1/2</sub>, AUC, CL, V<sub>d</sub>, MRT, bioavailability) into analysis-ready structured data.
- A companion analytics module aggregates across studies — species, administration route, dosing and fasting status — with heat-mapped cross-tabulation.
- Runs fully **on-premises** to meet internal data-governance requirements.
</div>
</div>

# 📖 Educations
- *2022.09 - 2025.06*, **M.Sc. in Bioinformatics**, Nanjing Tech University. Advisor: Prof. Dengming Ming.
- *2018.09 - 2022.06*, **B.Eng. in Pharmaceutical Engineering**, Nanjing Tech University.

# 💬 Talks and Conferences
- *2025.04*, **CASC 2025** — China Aging Science Conference & International Conference on Aging Biology. Invited participant; poster presentation; selected as **student representative** and spoke at both the Chinese and English sessions.
- *2026.05*, AI Virtual Cell & Industrial Translation Salon.
- *2026.04*, Spring Drug Discovery Conference, Nanjing.
- *2025.11*, Conference on Artificial Intelligence in Pharmacy.

# 💻 Experience
- *2025.09 - Present*, **PharmaBlock Sciences, Inc.**, Nanjing — AIDD Team, autoimmune pipeline. Leading immuneKG, ADMET-Optimizer, and PKExtract.
- *2025.05 - 2025.08*, **Hengrui Medicine Co., Ltd.**, Shanghai — metabolic pipeline.

# 🎲 Elsewhere
Founder of **Turkey Studio** during my undergraduate years — registered the company and domain, and built and ran three servers, using the private one for deep learning training. Projects on that infrastructure included a greedy-algorithm search for heads-up Texas Hold'em, an OpenCV + PyGUI game automation loop, and an LSTM model for securities forecasting. The poker one stuck: I still follow game-theoretic solvers and, lately, LLM-based poker agents.
