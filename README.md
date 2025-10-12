#  Analisi Semantica e Valutazione Automatica degli Errori di Pronuncia in Thai

## Descrizione

Questo progetto propone una pipeline metodologica per l’**analisi semantica** e la **valutazione automatica degli errori di pronuncia** nella lingua Thai.
L'obiettivo non è solo stimare la correttezza fonetica, ma anche misurare l’**impatto comunicativo** degli errori, offrendo un approccio integrato **fonetico-semantico** a supporto dell’apprendimento della pronuncia in lingue tonali.

La pipeline utilizza il corpus **LOTUS**, manipolato per generare audio contenenti errori tipici degli apprendenti.
I dati sono stati impiegati per il *fine-tuning* del modello di riconoscimento vocale **`wav2vec2-large-xlsr-53-th`**, adattato a trascrivere fedelmente le pronunce errate senza correzione automatica.
Le trascrizioni vengono poi analizzate con il modello semantico **`paraphrase-multilingual-MiniLM-L12-v2`**, per misurare la **similarità semantica** tra frase di riferimento e frase pronunciata.

I risultati mostrano che l’aumento della frequenza e della gravità degli errori riduce proporzionalmente la similarità semantica, confermando l’efficacia dell’approccio.

## Caratteristiche principali

* Trascrizione automatica di pronunce corrette ed errate in Thai
* Misurazione della similarità semantica tra frase target e frase pronunciata
* Valutazione fonetico-semantica per feedback didattico mirato
* Supporto all’apprendimento della pronuncia in contesti di lingua tonale

## Installazione

Clona il repository:

```bash
git clone https://github.com/DamianaBuono/Pipeline-per-l-analisi-semantica-e-la-valutazione-degli-errori-di-pronuncia-nella-lingua-Thai.git
cd Pipeline-per-l-analisi-semantica-e-la-valutazione-degli-errori-di-pronuncia-nella-lingua-Thai

```

Installa le dipendenze principali (Python 3.8+ richiesto):

```bash
pip install torch transformers sentence-transformers numpy pandas
```

## Uso

Esempio di utilizzo della pipeline:

```python
from pipeline import PronunciationEvaluator

# Caricamento modelli
evaluator = PronunciationEvaluator(
    model_audio="wav2vec2-large-xlsr-53-th",
    model_semantic="paraphrase-multilingual-MiniLM-L12-v2"
)

# Valutazione di un file audio
score = evaluator.evaluate("audio_learner.wav", "frase_di_riferimento")
print(f"Similarità semantica: {score}")
```

## Risultati

La similarità semantica diminuisce proporzionalmente all’aumento degli errori di pronuncia.
La pipeline fornisce **feedback dettagliati**, utili per migliorare l’apprendimento della pronuncia Thai.

## Tecnologie

* **Linguaggio:** Python 3.8+
* **Modelli:** `wav2vec2-large-xlsr-53-th`, `paraphrase-multilingual-MiniLM-L12-v2`
* **Librerie:** `torch`, `transformers`, `sentence-transformers`, `numpy`, `pandas`

## Riferimenti

* **Corpus:** LOTUS
* **Modello ASR:** wav2vec2-large-xlsr-53-th – *Facebook AI*
* **Modello semantico:** paraphrase-multilingual-MiniLM-L12-v2 – *Sentence-BERT*
