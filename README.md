# Automated Aspect Discovery in E-Commerce Reviews

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Jupyter Notebook](https://img.shields.io/badge/Tools-Jupyter_Notebook-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## Abstract

This project examines automated aspect discovery in e-commerce customer reviews by comparing traditional statistical topic models with modern transformer-based and graph-based approaches. The objective is to identify which techniques most effectively capture coherent and interpretable product aspects from noisy, user-generated text, thereby supporting downstream tasks such as aspect-based sentiment analysis and data-driven product improvement.

---

## Project Overview

Customer reviews on e-commerce platforms contain rich information about product performance, user satisfaction, and recurring issues, yet they are challenging to summarize manually at scale. This project implements an end-to-end NLP pipeline that:

- Cleans and preprocesses raw review text.
- Trains multiple topic modeling algorithms on the same corpus.
- Evaluates and contrasts their ability to uncover meaningful product aspects and themes.

The repository is organized to facilitate reproducibility, inspection of intermediate results, and reuse in academic work, data analytics portfolios, or further methodological research.[web:4][web:6]

---

## Research Objectives

- **Data preparation**: Develop a robust preprocessing pipeline for review text, including normalization, tokenization, lemmatization, stopword handling, and domain-specific filtering.
- **Model implementation**: Implement and configure four topic modeling approaches:
  - Latent Dirichlet Allocation (LDA)
  - Latent Semantic Analysis (LSA)
  - BERTopic (transformer-based topic modeling)
  - Graph-Based Topic Modelling (e.g., co-occurrence or similarity graph with community detection)
- **Evaluation and comparison**:
  - Quantitatively assess topic coherence and diversity.
  - Qualitatively assess interpretability and semantic consistency of discovered aspects.
  - Analyze the strengths and limitations of each approach for e-commerce review analysis.

---

## Methodology

### Data Preprocessing

Review text is processed through a standardized sequence of steps:

- Text normalization (lowercasing, punctuation removal, handling of emojis and special characters).
- Tokenization and lemmatization using established NLP libraries.
- Stopword removal and optional n-gram extraction for multi-word aspects (e.g., “battery life”, “delivery time”).
- Construction of Bag-of-Words, TF–IDF matrices, and dense embeddings where required for specific models.

### Topic Modeling Techniques

- **LDA**: A probabilistic generative model applied to Bag-of-Words representations to obtain baseline topics over word distributions.
- **LSA**: A matrix factorization approach (typically via truncated SVD) on TF–IDF representations to uncover latent semantic dimensions in the corpus.
- **BERTopic**: A transformer-based method that combines document embeddings, clustering, and class-based TF–IDF to produce semantically rich topics.
- **Graph-Based Topic Modelling**: A graph construction over terms (based on co-occurrence or similarity) followed by community detection or clustering to derive topics as dense subgraphs.

### Evaluation Strategy

- Use standard topic coherence metrics (e.g., \(C_v\), \(U_{Mass}\)) to compare models quantitatively.
- Manually inspect top-ranked terms and representative documents for a subset of topics to assess interpretability.
- Generate visualizations such as topic distance maps, word clouds, and distribution plots to support analysis and reporting.

---

## Dataset

The project assumes access to a corpus of e-commerce product reviews collected from online marketplaces. Reviews are anonymized and stored under the `data/` directory with clear separation between raw and processed datasets:

- `data/raw/`: Original review text and optional metadata (e.g., rating, product category).
- `data/processed/`: Cleaned and preprocessed versions used directly in modeling experiments.

Any data usage and sharing must comply with platform policies and institutional guidelines. For academic submission, additional documentation (e.g., `data/README.md`) should detail data provenance, anonymization procedures, licenses, and ethical considerations.[web:6]

---

## Repository Structure

```text
├── data/
│   ├── raw/               # Original e-commerce review datasets (if shareable)
│   └── processed/         # Cleaned and preprocessed review datasets used for modeling
├── notebooks/             # Jupyter notebooks for preprocessing, modeling, and evaluation
│   ├── 01_data_preprocessing.ipynb
│   ├── 02_lda_lsa_modeling.ipynb
│   ├── 03_bertopic_modeling.ipynb
│   ├── 04_graph_topic_modeling.ipynb
│   └── 05_evaluation_visualization.ipynb
├── visualizations/        # Charts, graphs, and HTML visualizations (e.g., topic distance maps)
│   ├── coherence_scores.png
│   ├── topic_wordclouds/
│   └── ber_topic_map.html
├── src/                   # Optional: reusable Python modules
│   ├── data_utils.py
│   ├── modeling_utils.py
│   └── evaluation_utils.py
├── requirements.txt       # Python dependencies required to run the project
└── README.md              # Project documentation
```

This structure follows common best practices for machine learning and data science projects, emphasizing reproducibility and clarity.[web:11][web:15]

---

## Getting Started

### Prerequisites

- Python **3.8+**
- `pip` or `conda` for dependency management
- Jupyter Notebook or JupyterLab
- (Recommended) a virtual environment tool such as `venv` or `conda`

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/<your-username>/<your-repo-name>.git
   cd <your-repo-name>
   ```

2. Create and activate a virtual environment:

   ```bash
   python -m venv .venv
   source .venv/bin/activate      # On Windows: .venv\Scripts\activate
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

### Running the Analysis

1. Launch Jupyter:

   ```bash
   jupyter notebook
   ```

2. Execute the notebooks in the following order:

   1. `01_data_preprocessing.ipynb`
   2. `02_lda_lsa_modeling.ipynb`
   3. `03_bertopic_modeling.ipynb`
   4. `04_graph_topic_modeling.ipynb`
   5. `05_evaluation_visualization.ipynb`

3. Generated figures and HTML files will be written to the `visualizations/` directory for inclusion in reports or presentations.

---

## Experiments and Results

The experimental design focuses on understanding how each topic modeling approach behaves on the same review corpus:

- **Hyperparameter exploration**: Varying the number of topics and relevant model-specific parameters to study their impact on coherence and interpretability.
- **Quantitative evaluation**: Reporting average coherence scores and other relevant metrics for each model.
- **Qualitative assessment**: Presenting selected topics (e.g., delivery experience, product durability, pricing) and discussing their semantic clarity and usefulness.
- **Visual analysis**: Including topic distance plots, term-frequency visualizations, and word clouds for key topics.

These outputs are intended to be directly referenced in academic project reports, theses, and technical presentations.[web:12][web:14]

---

## Applications

The findings of this project can be applied in several contexts:

- **Product management**: Prioritizing improvements by identifying frequently mentioned aspects and recurring complaints.
- **Customer experience and operations**: Monitoring themes related to logistics, packaging, and service quality at scale.
- **Business intelligence**: Integrating discovered aspects into dashboards and aligning them with rating distributions, returns, or sales performance.
- **Teaching and research**: Providing an example of an end-to-end topic modeling study on real-world text data, suitable for coursework and methodological demonstrations.

---

## Limitations and Future Work

- Topic quality is sensitive to preprocessing decisions, the choice of hyperparameters, and the characteristics of the review corpus.
- Transformer-based methods (e.g., BERTopic) impose higher computational requirements compared with LDA and LSA.
- Graph-based models depend on the definition of term similarity and graph construction strategy, which may vary across domains.

Potential extensions include:

- Incorporating aspect-based sentiment analysis using topics as aspect candidates.
- Comparing review themes across platforms, product categories, or time periods.
- Developing interactive tools (e.g., dashboards or web applications) for exploring topics in real time.

---

## Academic Use and Citation

If this repository is used in academic work (course projects, dissertations, or publications), the following generic BibTeX entry can be adapted:

```bibtex
@misc{aspect_discovery_ecommerce,
  author       = {Your Name},
  title        = {Automated Aspect Discovery in E-Commerce Reviews},
  year         = {2026},
  howpublished = {\url{https://github.com/<your-username>/<your-repo-name>}},
  note         = {Accessed: YYYY-MM-DD}
}
```

For formal submissions, you may also reference related methodological literature on topic modeling and transformer-based NLP, and include this repository in the reproducibility or supplementary materials section.[web:4][web:18]

---

## Contributing

While the primary focus of this repository is academic experimentation, contributions that improve code structure, add alternative topic modeling techniques, or enhance evaluation and visualization are welcome.

- Fork the repository.
- Create a feature branch: `git checkout -b feature/<feature-name>`.
- Commit changes with clear and descriptive messages.
- Open a pull request explaining the motivation and design of the changes.

---

## Contact

**Author**: *Felcia Sairah Siji*
**Email**: sijifelcia7@gmail.com  
**Affiliation**: MSc Data Analytics, Technological University of the Shannon: Midlands, Athlone, Ireland.
