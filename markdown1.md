# Documentazione dei File Bash
Questa documentazione descrive le funzionalità e l'uso dei file bash utilizzati per la configurazione e il deploy del nostro applicativo.

---

## Tipologie di File Bash

### 1️⃣ **Bash per la Configurazione di NGINX**

**Cosa fa?**
- Collega il **reverse proxy NGINX** al **server Uvicorn** su cui gira l'applicativo.

**Perché è importante?**
- Consente agli endpoint dell'applicativo di essere raggiungibili tramite il **reverse proxy**, che:
  - Gestisce il traffico interno ed esterno (takers).
  - È accessibile sia da **Amazon Web Services (AWS)** che dall’esterno.

---

### 2️⃣ **Bash per l'Installazione dell'Applicativo sulla VM**

**Funzionalità principali**:
1. **Primo Deploy**:
   - Configura l'ambiente virtuale Python e installa le dipendenze richieste.
   - Aggiorna il sistema operativo.
   - Installa software necessari, come **MySQL**.

2. **Aggiornamento o Inserimento**:
   - Rimuove (se presente) la cartella contenente l'applicativo.
   - Clona il repository GitHub dell'applicativo.
   - Modifica le variabili di ambiente in base al file `config_env`.
   - Avvia il server **Uvicorn** per eseguire l'applicativo.

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


