# Data-Management-project \
## Il caso GameStop. 
### Presa dati di Reddit 
Eseguire il file: redditAPI.ipynb fornendo i seguenti parametri: \
• after & before = periodo temporale di interesse; \
• query = parola chiave perestrarre le submission; \
• sub = in quale subreddit bisogna andare a cercare\
Si osservi che per ogni richiesta API vengono scaricate un massimo di 100 submission.\

Eseguire il file:
Data_Cleaning.ipynb \
Questo permette di eseguire una pulizia dei dati in modo da renderli integrabili e tali da poter 
effettuare la Sentiment Analysis.\
Eseguire il file:
Sentiment.ipynb \
Permette di poter effettuare la Sentiment Analysis arricchendo il dataset. 
### Presa dati finanziari
Eseguire il file:
scriptyFinance.ipynb
fornendo i seguenti parametri: \
• Ticker; \
• Start; \
• End; \
• Interval \
Si osservi che i dati a 1 minuto sono disponibili solo per i precedenti 7 giorni da quando si lancia lo 
script. \
### Velocità
Creare un topic “reddit” da terminale attraverso il comando:
kafka-topics.bat --create --topic reddit --bootstrap-server localhost:9092 \
Aprire in due terminali contemporaneamente: \
• Producer.ipynb \
• Consumer.ipynb \
Questo effettua una rilevazione di 100 submission per volta, che poi vengono trasformate in 
formato JSON, caricate sul broker attraverso il servizio kafka. \
Il Consumer consuma i dati che da JSON vengono inseriti in un dataframe Pandas. \
### Integrazione dei dati
Creare un topic “gmereddit” da terminale attraverso il comando:
kafka-topics.bat --create --topic gmereddit --bootstrap-server localhost:9092 \
Per eseguire l'integrazione tra i dati di Reddit e i dati finanziari bisogna eseguire:
Merge.ipynb
Fornendo i parametri: \
• reddit: submission effettuate sul subreddit (dataframe); \
• gme: dati finanziari (dataframe); \
• u: utente mongo; \ 
• p : password utente \
• port: porta in cui è attivo l'utente \
Questo script integra i due dataset e carica tutto su mongo.
