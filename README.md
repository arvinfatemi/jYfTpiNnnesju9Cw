# Potential Talents – Candidate Ranking

This mini-project demonstrates how to rank semi-sourced human-resources candidates using lightweight natural language techniques. The deliverable is a single polished notebook (`Potential Talents.ipynb`) that recruiters or hiring stakeholders can skim to understand the approach.

## Project overview
- Frame the business problem: score candidates against HR-focused keywords and support re-ranking once a reviewer stars a preferred profile.
- Compare two complementary ranking strategies: TF-IDF for a transparent lexical baseline and MPNet sentence embeddings for semantic matching.
- Simulate a feedback loop by reusing the embedding space to re-rank candidates after a “star” event.
- Summarize opportunities for filtering, evaluation, and UI handoff.

## Dataset
- Source: Google Sheet shared in the challenge prompt – [`117X6i53dKiO7w6kuA1g1TpdTlv1173h_dPlJt5cNNMU`](https://docs.google.com/spreadsheets/d/117X6i53dKiO7w6kuA1g1TpdTlv1173h_dPlJt5cNNMU/edit?usp=sharing).
- Columns: `id`, `job_title`, `location`, `connection`. A `fit` score exists in the sheet but is dropped to mimic a cold-start setting.
- Access: the notebook downloads the latest CSV export directly so no raw data ships with the repo.

## Repository layout
- `Potential Talents.ipynb` – main analysis and ranking walkthrough.
- `description.txt` – original problem statement for quick reference.

## How to run the notebook
1. Create a virtual environment (optional but recommended): `python3 -m venv .venv && source .venv/bin/activate`.
2. Install dependencies: `pip install pandas scikit-learn sentence-transformers`.
3. Launch Jupyter (Lab or Notebook) from the repo root and open `Potential Talents.ipynb`.
4. Run the cells sequentially; the notebook reads directly from Google Sheets, so an internet connection is required.

## Results & next steps
- TF-IDF surfaces literal “Aspiring Human Resources” titles immediately and serves as an interpretable baseline.
- MPNet embeddings reward semantically similar titles (e.g., “HR specialist” vs “talent acquisition partner”) and therefore reduce manual triage time.
- Re-ranking a starred candidate is as simple as reusing the embedding space, hinting at a low-effort feedback loop for recruiters.
- Suggested follow-ups: log ranking metrics such as precision@k, add filters (location/connection cutoffs), and wrap the workflow in a lightweight UI so sourcers do not need to touch code.
