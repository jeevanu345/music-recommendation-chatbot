# Music Recommendation Chatbot

A small Flask application that demonstrates a conversational interface for genre-based music suggestions and feedback storage.

## Recommendation method

The current recommender is a keyword-matching baseline. It looks for one of four genres—folk, country, rock, or pop—and randomly selects up to three songs from a small in-memory catalog. It does not currently use a trained machine-learning model, embeddings, collaborative filtering, or an external music catalog.

This baseline is useful for exercising the API and feedback workflow, but it should not be described as personalized AI until a model and evaluation method are implemented.

## Current components

- `app.py` — Flask API and persistence workflow
- `recommendation_model.py` — keyword-based recommendation baseline
- `requirements.txt` — Python dependencies
- `Readme.txt` — legacy documentation retained for comparison

## Run locally

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python app.py
```

## Evaluation needed

A future model should be evaluated with a versioned dataset and metrics appropriate to the task, such as precision at k, catalog coverage, diversity, and explicit user-feedback outcomes. Cold-start behavior and failure cases should also be documented.

## Limitations

- The catalog is tiny and synthetic.
- Matching is based on genre keywords.
- Random selection makes results non-deterministic.
- There is no documented automated test suite.
- Recommendation quality has not been benchmarked.
