# Documentazione dei File Bash
Questa documentazione descrive le tipologie, le funzionalità e l'uso dei file bash utilizzati per la configurazione e il deploy del nostro applicativo.

---

## Tipologie di File Bash

### 1️⃣ **Bash per la Configurazione di NGINX**

**Cosa fa?**
- Collega il **reverse proxy NGINX** al **server Uvicorn** su cui gira l'applicativo.

**Perché è importante?**
- Consente agli endpoint dell'applicativo di essere raggiungibili tramite il **reverse proxy**, che:
  - Gestisce il traffico interno ed esterno (takers).
  - È accessibile sia da **Amazon Web Services (AWS)** che da client esterni.

---

### 2️⃣ **Bash per l'Installazione dell'Applicativo sulla VM**

- **Modalità**:
  - **Inserimento (primo deploy)**: Configura l'applicativo da zero.
  - **Aggiornamento (update)**: Aggiorna l'applicativo esistente.

**Cosa fa?**
1. **Operazioni comuni a primo deploy e update**:
   - **Rimozione della cartella esistente**: Elimina la directory dell'applicativo se già presente.
   - **Clonazione del repository**: Esegue un `git clone` della repository GitHub per ottenere la versione più recente dell’applicativo.
   - **Modifica delle variabili di ambiente**: Configura l'ambiente in base al file `config_env` specifico per l'ambiente (ad esempio `stg`, `prod`).
   - **Avvio del server Uvicorn**: Avvia il server che esegue l'applicativo.

2. **Operazioni esclusive del primo deploy**:
   - **Creazione del virtual environment Python**: Crea un ambiente isolato per le dipendenze.
   - **Installazione delle dipendenze**: Installa i moduli Python richiesti.
   - **Aggiornamento del sistema operativo**: Esegue aggiornamenti di sistema.
   - **Installazione di software aggiuntivo**: Configura software necessari, come **MySQL**.
  
---

## Esecuzione dei File Bash

### **Primo Avvio (Deploy Iniziale)**
Esegui il comando seguente:
```bash
./deploy_staging.sh --env="stg" --DBPassword="Rootroot24%" --Secret="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" --ip="10.4.124.21" --update=true
```

### **Aggiornamento (Update)**
Esegui il comando seguente:
```bash
./deploy_staging.sh --env="stg" --DBPassword="Rootroot24%" --Secret="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" --ip="10.4.124.20" --update=false
```


