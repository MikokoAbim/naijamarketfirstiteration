# NaijaMarket

A small API that reads shopping messages written in Nigerian-style English (for example, "Add Garri from Aba Traders to my cart"). It finds what the user wants (the intent) and the product or store they mention (the entities).

- Built and tested on Windows.

## Before you start

- Install Python 3.10. Newer versions (3.12 and above) do not work with TensorFlow 2.13.
- Make sure these are in the project folder (the same folder as this README):
  - `tokenizer.pickle`
  - `label_encoder.pickle`
  - `intent_recognition_model/`
  - `model-best/`

## Set up

- Open a terminal in the project folder.
- Create a virtual environment:
  - `python -m venv naija_market_env`
- Turn it on:
  - Windows: `.\naija_market_env\Scripts\activate`
  - Mac/Linux: `source naija_market_env/bin/activate`
- Install everything the app needs:
  - `pip install -r requirements.txt`

## Run the app

- Go into the API folder:
  - `cd ApiFolder`
- Start the server:
  - `uvicorn main:app --reload`
- You must run this command from inside `ApiFolder`. The app finds its models using paths that start from there.
- Wait until you see "Application startup complete".

## Try it

- Open `http://127.0.0.1:8000/docs` in your browser.
- Pick an endpoint, click "Try it out", type a sentence, then click "Execute":
  - `/IR` returns the intent (what the user wants).
  - `/NER` returns the products and stores found in the sentence.
  - `/personal-assistant` uses both to answer a product search.
- Example sentence: `Can you help me find Local beans`

## Common problems

- "No module named NER" or "file not found":
  - You are in the wrong folder. Run `cd ApiFolder` first.
- Error when loading a model:
  - Your library versions are different. Run `pip install -r requirements.txt` again in a clean environment.
- Install fails on TensorFlow:
  - Check your Python version with `python --version`. It must be 3.10.

## Optional: run the notebooks

- Only needed if you want to retrain the models.
- Install extra packages:
  - `pip install pandas matplotlib mlflow tqdm jupyter`
- Notebooks:
  - `IntentRecognition.ipynb` trains the intent model.
  - `EntityRecognition.ipynb` trains the entity model.
  - `UseModels.ipynb` tests the saved models.
