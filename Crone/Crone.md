# Documentazione su `cron` in Linux

## Introduzione
`cron` è un sistema di pianificazione dei processi su Unix-like OS. Permette di eseguire comandi o script automaticamente a intervalli specifici, utilizzando il daemon `cron`. 

Il file di configurazione principale di `cron` è il **crontab**, dove si definiscono le attività pianificate.

---

## Sintassi di `crontab`
La sintassi base di una riga in un file crontab è:

```
* * * * * comando
- - - - -
| | | | |
| | | | +---- Giorno della settimana (0 - 7) (Domenica = 0 o 7)
| | | +------ Mese (1 - 12)
| | +-------- Giorno del mese (1 - 31)
| +---------- Ora (0 - 23)
+------------ Minuto (0 - 59)
```

### Campi speciali
- **`*`**: Qualsiasi valore.
- **`,`**: Separatore per valori multipli (es: `1,15`).
- **`-`**: Intervallo di valori (es: `1-5`).
- **`/`**: Incrementi (es: `*/10` significa ogni 10 unità).

### Esempi
| Programmazione        | Significato                                      |
|-----------------------|-------------------------------------------------|
| `0 5 * * *`          | Esegui alle 5:00 di ogni giorno                 |
| `*/15 8-18 * * 1-5`  | Ogni 15 minuti dalle 8:00 alle 18:00 (lun-ven)  |
| `0 0 1 * *`          | A mezzanotte del primo giorno di ogni mese      |
| `30 22 * * 0`        | Alle 22:30 di ogni domenica                     |

---

## Comandi principali

### Modifica del crontab
Per modificare il crontab dell'utente corrente:
```bash
crontab -e
```

### Visualizza il crontab
Per vedere le attività pianificate per l'utente corrente:
```bash
crontab -l
```

### Rimuovi il crontab
Per eliminare tutte le attività pianificate:
```bash
crontab -r
```

---

## File di sistema di `cron`

### `/etc/crontab`
File globale che permette di pianificare attività per tutti gli utenti.
Sintassi:
```
Minuto Ora Giorno Mese Giorno_settimana Utente Comando
```

Esempio:
```bash
0 2 * * * root /usr/bin/apt update
```

### `/etc/cron.*`
Cartelle predefinite per attività ricorrenti:
- **`/etc/cron.hourly`**: Script eseguiti ogni ora.
- **`/etc/cron.daily`**: Script eseguiti una volta al giorno.
- **`/etc/cron.weekly`**: Script eseguiti una volta alla settimana.
- **`/etc/cron.monthly`**: Script eseguiti una volta al mese.

---

## Log di `cron`
I log delle attività pianificate si trovano solitamente in:
```bash
/var/log/syslog  # Ubuntu e Debian
/var/log/cron    # CentOS e RedHat
```
Per visualizzare i log:
```bash
tail -f /var/log/syslog | grep cron
```

---

## Variabili di ambiente in `crontab`
- **`SHELL`**: Specifica la shell utilizzata (default: `/bin/sh`).
- **`PATH`**: Percorso di ricerca per i comandi.
- **`MAILTO`**: Indirizzo email per notifiche (lasciare vuoto per disabilitare).

Esempio:
```bash
SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=utente@example.com

0 7 * * * /path/to/script.sh
```

---

## Debug e consigli utili
- Assicurarsi che il servizio `cron` sia attivo:
  ```bash
  sudo systemctl status cron
  ```
- Testare manualmente i comandi pianificati per verificare che funzionino.
- Usare percorsi assoluti per file e script.
- Controllare eventuali errori nei log.

---

## Risorse aggiuntive
- Manuale di `crontab`:
  ```bash
  man 5 crontab
  ```
- Manuale di `cron`:
  ```bash
  man cron
  ```

---



