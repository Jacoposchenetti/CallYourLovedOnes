# CallYourLovedOnces - Piano di Progetto

## Panoramica del Progetto

CallYourLovedOnces è un'applicazione Android che analizza il registro chiamate del dispositivo per identificare quando è passato troppo tempo dall'ultima conversazione con i propri cari e invia promemoria per incoraggiare l'utente a ricontattarli.

## Funzionalità Principali

### Core Features
- **Analisi Registro Chiamate**: Accesso e analisi del call log di Android
- **Gestione Contatti Importanti**: Selezione e categorizzazione dei contatti da monitorare
- **Sistema di Notifiche**: Promemoria intelligenti basati su soglie temporali personalizzabili
- **Dashboard Statistiche**: Visualizzazione delle abitudini di comunicazione
- **Configurazione Flessibile**: Impostazioni personalizzate per ogni contatto

### Funzionalità Avanzate
- **Modalità Non Disturbare**: Rispetto degli orari di silenzio
- **Integrazione Calendario**: Considerazione di eventi speciali (compleanni, anniversari)
- **Backup e Sincronizzazione**: Salvataggio delle configurazioni
- **Analisi Comportamentale**: Suggerimenti basati sui pattern di comunicazione

## Stack Tecnologico

### Piattaforma e Linguaggio
- **Linguaggio**: Java/Kotlin per Android
- **IDE**: Android Studio
- **Target SDK**: API 34 (Android 14)
- **Minimum SDK**: API 24 (Android 7.0)

### Architettura
- **Pattern**: MVVM (Model-View-ViewModel)
- **Dependency Injection**: Hilt/Dagger
- **Navigation**: Android Navigation Component
- **Lifecycle**: Android Lifecycle Components

### Database e Storage
- **Database Locale**: Room (SQLite wrapper)
- **Shared Preferences**: Configurazioni utente
- **File Storage**: Backup e cache

### UI/UX
- **Design System**: Material Design 3
- **Layout**: Constraint Layout, RecyclerView
- **Animazioni**: Lottie (opzionale)
- **Temi**: Supporto Dark/Light mode

### Permessi Android Richiesti
- `READ_CALL_LOG`: Accesso al registro chiamate
- `READ_CONTACTS`: Lettura dei contatti
- `POST_NOTIFICATIONS`: Invio notifiche (API 33+)
- `SCHEDULE_EXACT_ALARM`: Promemoria precisi
- `WAKE_LOCK`: Mantenimento attività in background

### Librerie Principali
- **Room**: Database locale
- **WorkManager**: Operazioni in background
- **Retrofit**: API calls (per funzionalità future)
- **Gson**: Serializzazione JSON
- **Material Components**: UI
- **Lifecycle Extensions**: Gestione lifecycle

## Architettura del Progetto

```
app/
├── src/main/java/com/callyourlovedones/
│   ├── data/
│   │   ├── database/
│   │   │   ├── entities/
│   │   │   ├── dao/
│   │   │   └── CallDatabase.kt
│   │   ├── repositories/
│   │   └── models/
│   ├── ui/
│   │   ├── dashboard/
│   │   ├── contacts/
│   │   ├── settings/
│   │   └── notifications/
│   ├── utils/
│   │   ├── CallLogAnalyzer.kt
│   │   ├── NotificationHelper.kt
│   │   └── PermissionManager.kt
│   ├── services/
│   │   └── CallMonitoringService.kt
│   └── MainActivity.kt
├── src/main/res/
│   ├── layout/
│   ├── values/
│   ├── drawable/
│   └── menu/
└── build.gradle
```

## Flusso di Lavoro

### Setup Iniziale
1. Configurazione progetto Android
2. Implementazione richiesta permessi
3. Setup database Room
4. Creazione UI base

### Sviluppo Core
1. Implementazione lettura call log
2. Sistema di analisi delle chiamate
3. Gestione contatti preferiti
4. Sistema di notifiche

### Finalizzazione
1. Testing completo
2. Ottimizzazione performance
3. UI/UX polish
4. Preparazione per rilascio

## Istruzioni per la Gestione dei Task

### Come Utilizzare il File TASKS.md

1. **Completamento Task**: Quando completi un task, modifica il file TASKS.md cambiando `[ ]` in `[x]`
2. **Stato Avanzamento**: Ogni task principale ha subtask che devono essere completati in ordine
3. **Verifica Dipendenze**: Prima di iniziare un task, assicurati che tutti i prerequisiti siano completati
4. **Documentazione**: Per ogni task completato, aggiungi note o commenti se necessario
5. **Testing**: Testa sempre la funzionalità implementata prima di marcare il task come completato

### Esempio di Vidimazione

```markdown
- [x] ~~Setup progetto Android~~
  - [x] ~~Creazione nuovo progetto~~
  - [x] ~~Configurazione build.gradle~~
  - [x] ~~Setup dependencies~~
```

### Priorità dei Task

- **P0 (Critico)**: Funzionalità core essenziali
- **P1 (Alto)**: Funzionalità importanti per UX
- **P2 (Medio)**: Miglioramenti e ottimizzazioni
- **P3 (Basso)**: Funzionalità nice-to-have

## Note di Implementazione

### Considerazioni sulla Privacy
- Tutti i dati rimangono locali sul dispositivo
- Nessuna trasmissione di dati sensibili
- Implementare crittografia per dati sensibili

### Performance
- Utilizzare WorkManager per operazioni in background
- Implementare caching intelligente
- Ottimizzare query database

### Compatibilità
- Testare su diverse versioni Android
- Gestire correttamente le API deprecated
- Implementare fallback per dispositivi older

## Metriche di Successo

- **Funzionalità**: 100% dei core features implementati
- **Performance**: Avvio app < 2 secondi
- **Usabilità**: UI intuitiva con max 3 tap per funzionalità principali
- **Stabilità**: 0 crash durante testing base