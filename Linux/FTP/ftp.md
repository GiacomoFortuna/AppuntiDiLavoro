## Protocollo FTP

### Che cos'è il protocollo FTP

Il **File Transfer Protocol (FTP)** è un protocollo di rete standard utilizzato per trasferire file tra un client e un server all'interno di una rete basata su **TCP/IP**, come Internet o una rete locale (LAN). 

FTP può essere utilizzato per gestire i file presenti su un server, consentendo sia di modificarli che di trasferirli da e verso il server. È particolarmente utile nella gestione di siti web, dove i servizi di hosting mettono a disposizione un server FTP e forniscono all’utente le credenziali necessarie per connettersi.


FTP è stato sviluppato per la prima volta negli anni '70 e standardizzato come parte della famiglia di protocolli TCP/IP. È stato progettato per fornire un metodo semplice e affidabile per trasferire file, con funzionalità aggiuntive per la gestione dei file remoti.

---

#### **Requisiti per una connessione FTP**

Per stabilire una connessione FTP, è necessario conoscere e configurare i seguenti parametri:

- **Nome del server FTP:** Fornito dal provider di hosting, in genere è costituito dal nome del dominio preceduto da `ftp`, ad esempio: `ftp.dominio.com`.
- **Nome utente:** Generato durante la registrazione al servizio o creato manualmente dall’utente.
- **Password:** Necessaria per autenticarsi e accedere alle risorse del server.
- **Porta:** La porta predefinita per le connessioni FTP è la **21**.

![ftp](ftp.avif)


Con queste informazioni, è possibile accedere al server FTP per trasferire, scaricare o gestire file in modo semplice ed efficace.

---

### **Cosa si può fare con FTP?**

Come dicevamo il protocollo FTP ci permette di stabilire una connessione con il server e gestire i file.

Questo significa che con una connessione FTP si possono fare diverse operazioni sui file tra cui:

- Caricare i file dal nostro computer verso il server FTP;
- Scaricare i file dal server al nostro computer;
- Modificare i file sul server;
- Eliminare i file sul server;
- Modificare i permessi dei file.

---

#### **Funzionamento del protocollo FTP**

FTP opera seguendo un'architettura **client-server**, dove:
- Il **server FTP** mette a disposizione file e risorse.
- Il **client FTP** si connette al server per accedere o trasferire file.

Il protocollo utilizza due canali distinti per la comunicazione:
1. **Canale di Comando (Control Channel):**
   - Utilizza la porta **21** per impostazione predefinita.
   - Gestisce i comandi inviati dal client (es. richieste di connessione, autenticazione, navigazione directory) e le risposte del server.

2. **Canale Dati (Data Channel):**
   - È dedicato al trasferimento effettivo dei file.
   - La porta utilizzata dipende dalla modalità di connessione (attiva o passiva):
     - **Modalità Attiva:** Il server apre una connessione verso il client.
     - **Modalità Passiva:** Il client avvia la connessione verso il server, utile per superare firewall o NAT.

---

#### **Autenticazione**

L’autenticazione è un passaggio fondamentale per stabilire una connessione FTP e determinare i diritti di accesso ai file e alle risorse sul server. FTP supporta due modalità principali di autenticazione:

1. **Accesso autenticato (Username/Password):**
   - Il client fornisce un nome utente e una password al server.
   - Le credenziali vengono verificate dal server per concedere l'accesso alle risorse.
   - Questo tipo di autenticazione è comunemente usato in scenari aziendali o privati per proteggere file sensibili o limitare l'accesso ai soli utenti autorizzati.
   - **Limiti di sicurezza:**
     - FTP standard trasmette username e password in **chiaro** (plaintext), rendendoli vulnerabili a intercettazioni se il traffico non è cifrato.
     - Per aumentare la sicurezza, è consigliabile utilizzare **FTPS (FTP Secure)** o **SFTP**.

2. **Accesso anonimo:**
   - Non richiede credenziali specifiche. Di solito, l'utente inserisce "anonymous" come nome utente e una password generica o vuota.
   - È comunemente usato per rendere accessibili file pubblici, come repository software, archivi di documenti, o altri contenuti destinati alla condivisione libera.
   - **Limitazioni:**
     - Gli utenti anonimi hanno solitamente accesso limitato ai file sul server.
     - Le directory disponibili sono spesso in modalità **sola lettura** e isolate dal resto del file system del server.


---

#### **Modalità di Trasferimento**

FTP supporta diverse modalità di trasferimento dei file:
- **Binaria:** Per file non testuali (es. immagini, video, archivi, eseguibili), che vengono trasferiti senza alcuna modifica.
- **Testuale:** Per file di testo (es. `.txt`, `.csv`), che possono subire una conversione di fine riga per adattarsi al sistema operativo (es. Windows utilizza `\r\n`, mentre Unix utilizza `\n`).

---

#### **Sicurezza**

FTP standard non include crittografia, il che significa che:
- I dati, incluse credenziali di accesso e file, vengono trasmessi in chiaro.
- È vulnerabile ad attacchi di intercettazione come lo **sniffing**.

Per migliorare la sicurezza sono state introdotte varianti come:
- **FTPS (FTP Secure):** Utilizza il protocollo SSL/TLS per cifrare il traffico.
- **SFTP (SSH File Transfer Protocol):** Un protocollo separato che utilizza SSH per fornire trasferimenti sicuri.

FTP rimane tuttavia largamente utilizzato in molti scenari grazie alla sua semplicità e versatilità, soprattutto quando la sicurezza non è una priorità fondamentale (es. ambienti controllati o trasferimenti di dati non sensibili).

## WinSCP come Standard Aziendale per l'Utilizzo del Protocollo FTP

In azienda, utilizziamo **WinSCP** come client FTP standard per gestire in modo efficiente il trasferimento di file tra sistemi locali e server remoti. WinSCP offre un'interfaccia grafica intuitiva che semplifica l'interazione con il protocollo FTP, permettendo agli utenti di connettersi ai server aziendali con credenziali di autenticazione sicure (username e password) e di accedere rapidamente alle directory di lavoro.


#### **Funzionalità Specifiche Utilizzate**
- **Trasferimenti sicuri:** Sebbene l'FTP standard sia il protocollo principale, è raccomandato l'uso di FTPS o SFTP dove disponibile, per proteggere i dati sensibili.
- **Sincronizzazione e gestione file:** WinSCP consente di sincronizzare file tra sistemi locali e server remoti, una funzionalità fondamentale per mantenere aggiornati i repository aziendali.
- **Automazione:** Per attività ripetitive, gli script di WinSCP vengono utilizzati per automatizzare trasferimenti regolari, garantendo maggiore efficienza e riduzione degli errori manuali.

#### **Vantaggi Operativi**
WinSCP è stato scelto come standard aziendale per il suo supporto al protocollo FTP, la compatibilità con i requisiti di sicurezza e la facilità di utilizzo per utenti di diversi livelli di competenza tecnica. L'interfaccia a doppio pannello (file locali e remoti) e le funzionalità avanzate consentono una gestione centralizzata e affidabile dei trasferimenti di file, rendendo il processo rapido e conforme agli standard aziendali.
