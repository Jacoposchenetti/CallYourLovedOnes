# CallYourLovedOnces - Task List

## Legenda Priorità
- 🔴 P0 (Critico) - Funzionalità essenziali
- 🟡 P1 (Alto) - Funzionalità importanti  
- 🔵 P2 (Medio) - Miglioramenti
- ⚪ P3 (Basso) - Nice-to-have

---

## FASE 1: SETUP E CONFIGURAZIONE INIZIALE

### 🔴 1.1 Setup Progetto Android
- [ ] Creazione nuovo progetto Android in Android Studio
  - [ ] Configurare nome pacchetto: `com.callyourlovedones`
  - [ ] Impostare API minima 24, target API 34
  - [ ] Selezionare Empty Activity template
- [ ] Configurazione build.gradle (Module: app)
  - [ ] Aggiungere dipendenze Room
  - [ ] Aggiungere dipendenze Material Design
  - [ ] Aggiungere dipendenze Lifecycle
  - [ ] Aggiungere dipendenze WorkManager
  - [ ] Aggiungere dipendenze Navigation Component
- [ ] Configurazione build.gradle (Project)
  - [ ] Aggiungere plugin Kotlin
  - [ ] Aggiungere plugin Navigation SafeArgs
- [ ] Setup directory structure secondo architettura MVVM
  - [ ] Creare package `data`
  - [ ] Creare package `ui`
  - [ ] Creare package `utils`
  - [ ] Creare package `services`

### 🔴 1.2 Gestione Permessi
- [ ] Aggiungere permessi nel AndroidManifest.xml
  - [ ] `READ_CALL_LOG`
  - [ ] `READ_CONTACTS`
  - [ ] `POST_NOTIFICATIONS`
  - [ ] `SCHEDULE_EXACT_ALARM`
  - [ ] `WAKE_LOCK`
- [ ] Creare PermissionManager.kt
  - [ ] Implementare richiesta permesso READ_CALL_LOG
  - [ ] Implementare richiesta permesso READ_CONTACTS
  - [ ] Implementare richiesta permesso POST_NOTIFICATIONS
  - [ ] Gestire casi di permesso negato
  - [ ] Implementare controllo permessi runtime

### 🔴 1.3 Setup Database Room
- [ ] Creare entità database
  - [ ] Contact.kt (id, name, phoneNumber, lastCallDate, reminderInterval, isActive)
  - [ ] CallRecord.kt (id, contactId, callDate, callType, duration)
  - [ ] ReminderSettings.kt (id, contactId, reminderType, intervalDays, nextReminderDate)
- [ ] Creare DAO interfaces
  - [ ] ContactDao.kt (insert, update, delete, getAll, getById, getActiveContacts)
  - [ ] CallRecordDao.kt (insert, getCallsForContact, getLastCallForContact)
  - [ ] ReminderSettingsDao.kt (insert, update, getSettingsForContact)
- [ ] Creare CallDatabase.kt
  - [ ] Configurare Room database
  - [ ] Implementare migrations
  - [ ] Creare database instance singleton

---

## FASE 2: CORE FUNCTIONALITY

### 🔴 2.1 Lettura Call Log
- [ ] Creare CallLogReader.kt
  - [ ] Implementare lettura call log Android
  - [ ] Filtrare solo chiamate in uscita e in entrata
  - [ ] Mappare dati call log a CallRecord entity
  - [ ] Gestire eccezioni e permessi mancanti
- [ ] Creare CallLogAnalyzer.kt
  - [ ] Implementare analisi ultima chiamata per contatto
  - [ ] Calcolare giorni dall'ultima chiamata
  - [ ] Identificare contatti che necessitano promemoria
  - [ ] Implementare logica di soglia temporale

### 🔴 2.2 Gestione Contatti
- [ ] Creare ContactManager.kt
  - [ ] Lettura contatti da rubrica Android
  - [ ] Matching contatti con call log
  - [ ] Sincronizzazione contatti con database locale
- [ ] Creare ContactRepository.kt
  - [ ] Implementare CRUD operations per contatti
  - [ ] Implementare logica business per contatti preferiti
  - [ ] Gestire aggiornamenti contatti

### 🔴 2.3 Sistema di Notifiche
- [ ] Creare NotificationHelper.kt
  - [ ] Configurare notification channels
  - [ ] Implementare creazione notifiche promemoria
  - [ ] Gestire azioni notifica (chiama ora, ricorda dopo)
  - [ ] Implementare notifiche persistenti
- [ ] Creare ReminderScheduler.kt
  - [ ] Utilizzare WorkManager per scheduling
  - [ ] Implementare logica calcolo prossimo promemoria
  - [ ] Gestire cancellazione/modifica promemoria

---

## FASE 3: USER INTERFACE

### 🟡 3.1 MainActivity e Navigation
- [ ] Setup MainActivity.kt
  - [ ] Implementare richiesta permessi all'avvio
  - [ ] Setup Navigation Component
  - [ ] Configurare bottom navigation o drawer
- [ ] Creare navigation graph
  - [ ] Definire destinazioni principali
  - [ ] Configurare transizioni tra fragment

### 🟡 3.2 Dashboard Fragment
- [ ] Creare DashboardFragment.kt
  - [ ] Mostrare statistiche generali
  - [ ] Lista contatti con giorni dall'ultima chiamata
  - [ ] Implementare FAB per aggiungere contatto
- [ ] Creare DashboardViewModel.kt
  - [ ] Implementare LiveData per statistiche
  - [ ] Gestire aggiornamenti in tempo reale
- [ ] Design layout dashboard
  - [ ] Creare fragment_dashboard.xml
  - [ ] Implementare RecyclerView per contatti
  - [ ] Aggiungere card per statistiche

### 🟡 3.3 Contacts Management Fragment
- [ ] Creare ContactsFragment.kt
  - [ ] Lista completa contatti monitorati
  - [ ] Funzionalità add/edit/delete contatto
  - [ ] Configurazione intervalli promemoria personalizzati
- [ ] Creare ContactDetailFragment.kt
  - [ ] Dettagli contatto e storico chiamate
  - [ ] Configurazioni promemoria specifiche
  - [ ] Statistiche contatto individuale
- [ ] Design layouts contatti
  - [ ] fragment_contacts.xml
  - [ ] fragment_contact_detail.xml
  - [ ] item_contact.xml per RecyclerView

### 🟡 3.4 Settings Fragment  
- [ ] Creare SettingsFragment.kt
  - [ ] Preferenze globali app
  - [ ] Configurazioni notifiche
  - [ ] Modalità non disturbare
- [ ] Implementare SharedPreferences
  - [ ] Salvare impostazioni utente
  - [ ] Implementare default values
- [ ] Design settings layout
  - [ ] Utilizzare PreferenceScreen
  - [ ] Organizzare impostazioni per categoria

---

## FASE 4: SERVIZI E BACKGROUND PROCESSING

### 🔴 4.1 Background Service
- [ ] Creare CallMonitoringService.kt
  - [ ] Monitoraggio periodico call log
  - [ ] Aggiornamento database contatti
  - [ ] Triggering notifiche promemoria
- [ ] Implementare WorkManager Workers
  - [ ] CallLogSyncWorker per sincronizzazione
  - [ ] ReminderWorker per controllo promemoria
  - [ ] Configurare periodicità appropriate

### 🟡 4.2 Gestione Stati App
- [ ] Implementare foreground service per monitoraggio continuo
- [ ] Gestire comportamento app in background
- [ ] Ottimizzare battery usage
- [ ] Implementare logica doze mode compatibility

---

## FASE 5: TESTING E DEBUGGING

### 🔵 5.1 Unit Testing
- [ ] Test CallLogAnalyzer
  - [ ] Test calcolo giorni dall'ultima chiamata
  - [ ] Test identificazione contatti da contattare
- [ ] Test ContactRepository
  - [ ] Test CRUD operations
  - [ ] Test data validation
- [ ] Test ReminderScheduler
  - [ ] Test scheduling logic
  - [ ] Test cancellation logic

### 🔵 5.2 Integration Testing
- [ ] Test lettura call log reale
- [ ] Test creazione notifiche
- [ ] Test persistenza database
- [ ] Test permissions handling

### 🔵 5.3 UI Testing
- [ ] Test navigation flow
- [ ] Test add/edit contact flows
- [ ] Test settings persistence
- [ ] Test responsive design

---

## FASE 6: OTTIMIZZAZIONI E POLISH

### 🔵 6.1 Performance Optimization
- [ ] Ottimizzare query database
  - [ ] Aggiungere indici appropriati
  - [ ] Ottimizzare query complesse
- [ ] Implementare caching intelligente
  - [ ] Cache call log data
  - [ ] Cache contact information
- [ ] Ottimizzare UI performance
  - [ ] Implementare lazy loading
  - [ ] Ottimizzare RecyclerView

### 🔵 6.2 UX Improvements
- [ ] Implementare loading states
- [ ] Aggiungere empty states
- [ ] Implementare error handling UI
- [ ] Aggiungere confirmation dialogs
- [ ] Implementare undo functionality

### ⚪ 6.3 Advanced Features
- [ ] Backup e restore configurazioni
  - [ ] Export settings to file
  - [ ] Import settings from file
- [ ] Integrazione calendario
  - [ ] Riconoscimento eventi speciali
  - [ ] Promemoria per compleanni
- [ ] Statistiche avanzate
  - [ ] Grafici andamento chiamate
  - [ ] Report mensili/settimanali
- [ ] Widget per home screen
  - [ ] Widget contatti da chiamare
  - [ ] Quick call widget

---

## FASE 7: FINALIZZAZIONE E RILASCIO

### 🟡 7.1 App Icon e Branding
- [ ] Creare app icon
  - [ ] Versioni multiple risoluzioni
  - [ ] Adaptive icon per Android 8+
- [ ] Definire color scheme consistente
- [ ] Implementare splash screen

### 🟡 7.2 Play Store Preparation
- [ ] Creare screenshots app
- [ ] Scrivere descrizione Play Store
- [ ] Configurare app signing
- [ ] Generare APK/AAB per rilascio
- [ ] Test su dispositivi multipli

### 🔵 7.3 Documentation
- [ ] README.md completo
- [ ] Documentazione API interna
- [ ] User guide/help section in app
- [ ] Privacy policy

---

## CHECKLIST FINALE PRE-RILASCIO

### Funzionalità Core ✅
- [ ] App legge correttamente call log
- [ ] Notifiche promemoria funzionano
- [ ] Gestione contatti completa
- [ ] Settings persistono correttamente
- [ ] Background processing funziona

### Test Dispositivi 📱
- [ ] Test su Android 7.0 (API 24)
- [ ] Test su Android 14 (API 34)
- [ ] Test su diversi produttori (Samsung, Xiaomi, etc.)
- [ ] Test con permessi negati
- [ ] Test modalità risparmio energetico

### Performance 🚀
- [ ] Avvio app < 2 secondi
- [ ] Scrolling smooth in tutte le liste
- [ ] Nessun memory leak
- [ ] Battery usage ottimizzato

### Compatibilità 🔧
- [ ] Supporto dark/light theme
- [ ] Supporto diverse lingue (almeno EN/IT)
- [ ] Responsive design per tablet
- [ ] Accessibility features

---

**NOTA**: Vidima ogni checkbox con [x] quando il task è completato. Aggiungi note o commenti sotto ogni sezione se necessario.