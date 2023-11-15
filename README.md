# Il progetto
Il progetto analizza un dataset contente dati inerenti a diversi campioni d'acqua. Il dataset è composto da 9 features (parametri misurati nei campioni d'acqua) ed una label binaria che indica se il campione è potabile o meno:

- pH of 1. water (0 to 14).
- Hardness: Capacity of water to precipitate soap in mg/L.
- Solids: Total dissolved solids in ppm.
- Chloramines: Amount of Chloramines in ppm.
- Sulfate: Amount of Sulfates dissolved in mg/L.
- Conductivity: Electrical conductivity of water in μS/cm.
- Organic_carbon: Amount of organic carbon in ppm.
- Trihalomethanes: Amount of Trihalomethanes in μg/L.
- Turbidity: Measure of light emiting property of water in NTU.
- Potability: Indicates if water is safe for human consumption.
  Potable -1 and Not potable -0

Lo scopo del progetto è di prevedere in base ai parametri misurati se il campione d'acqua è potabile o meno.
Per fare ciò sono stati addestrati diversi modelli di classificazione, sono stati messi a confronto i risultati ed è stato selezionato il più efficace sui dati in questione. 
Il modello che ha ottenuto le prestazioni migliori è stato Random Forest Classifier.

## Struttura
- Preparazione
- Exploratory data analysis
  - Analisi Esplorativa
    - Documentazione dati
    - Conclusioni analisi esplorativa:
  - Fasi di lavoro
  - plit set
  - Base line model
  - Bilanciamento Dataset
  - Valori mancanti
  - Outliers
    - Analisi univariata
    - Analisi multivariata
  - Standardizzazione
  - Correlazioni
  - Selezione features
- Metrica di valutazione
- Definizione modelli
  - Strada 1 (tutte le features)
    - Spot check
    - Tuning parametri
  - Strada 2 (con 4 features)
    - Spot check
    - Tuning parametri
- Addestramento finale
- Conclusioni

## Risultati
I risultati mostrano che il modello RFC_final_1 addestrato su tutte le features ha ottenuto un risultato leggermente migliore rispetto al modello addestrato solamente sulle quattro features più rilevanti (RFC_final_2).

RFC_final_1 ha ottenuto un punteggio sul test set di accuracy pari a 0.636 e precision pari a 0.57.

Si notà inoltre che entrambi i modelli hanno ottenuto un punteggio significativamente inferiore nel test set piuttosto che durante l'addestramento. Questo probabilmente indica che, nonostante la cross validation e all'utilizzo della OSER (One Standard Error Rule), i modelli si sono adattati eccessivamente ai dati di train non riuscendo a generalizzare su nuovi dati: OVERFITTING.

Le previsioni ottenute mostrano un notevole sbilanciamento verso la classe 0. Ciò indica che il modello tende a predire con maggiore probabilità che l'acqua non sia potabile. Questa caratteristica è vantaggiosa per il dataset in questione poiché, dato il maggior numero di falsi negativi rispetto ai falsi positivi, è meno probabile che il modello identifichi erroneamente come potabile un campione d'acqua che in realtà non lo è. Questo è essenziale per garantire la sicurezza della salute. Tuttavia, la precisione rimane relativamente bassa, pari al 0.57, indicando che c'è una probabilità del 43% che un campione classificato come potabile non lo sia effettivamente.

Ipotizzo che la causa della bassa performance del modello sia causata principalmente dalla natura dei dati: dalla bassa correlazione tra le features ed il target, dalla bassa dimensionalità e dal rumore.

