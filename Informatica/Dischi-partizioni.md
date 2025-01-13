# Dischi e Partizioni

## Dischi

### Tipi di Dischi
- **HDD (Hard Disk Drive)**: Utilizza piatti magnetici rotanti per memorizzare i dati. È più lento rispetto agli SSD ma offre una maggiore capacità di archiviazione a un costo inferiore.
- **SSD (Solid State Drive)**: Utilizza memoria flash per memorizzare i dati. È molto più veloce rispetto agli HDD ma generalmente più costoso per gigabyte.
- **NVMe (Non-Volatile Memory Express)**: Un'interfaccia di comunicazione per SSD che offre velocità di trasferimento dati molto elevate rispetto agli SSD tradizionali.

### Struttura di un Disco
- **Settori**: La più piccola unità di memorizzazione su un disco. Generalmente di 512 byte o 4096 byte (4K).
- **Tracce**: Cerchi concentrici sui piatti del disco.
- **Cilindri**: Insieme di tracce allineate verticalmente attraverso i piatti.
- **Cluster**: Gruppo di settori che il file system gestisce come un'unica unità.

## Partizioni

### Tipi di Partizioni
- **Partizione Primaria**: Può contenere un sistema operativo e può essere avviabile. Un disco può avere fino a quattro partizioni primarie.
- **Partizione Estesa**: Utilizzata per superare il limite delle quattro partizioni primarie. Può contenere un numero illimitato di partizioni logiche.
- **Partizione Logica**: Partizioni all'interno di una partizione estesa.

### Tabelle delle Partizioni
- **MBR (Master Boot Record)**: Utilizza una tabella delle partizioni di 32 bit. Supporta dischi fino a 2 TB e un massimo di quattro partizioni primarie.
- **GPT (GUID Partition Table)**: Utilizza una tabella delle partizioni di 64 bit. Supporta dischi di dimensioni molto maggiori e un numero quasi illimitato di partizioni.

### File System
- **NTFS (New Technology File System)**: Utilizzato principalmente nei sistemi operativi Windows. Supporta grandi dimensioni di file e dischi, e offre funzionalità avanzate come la compressione dei file e la crittografia.
- **FAT32 (File Allocation Table 32)**: Un file system più vecchio compatibile con molti sistemi operativi, ma con limitazioni sulla dimensione dei file (fino a 4 GB) e delle partizioni (fino a 8 TB).
- **exFAT (Extended File Allocation Table)**: Progettato per superare le limitazioni di FAT32, mantenendo la compatibilità con molti sistemi operativi.
- **EXT4 (Fourth Extended File System)**: Utilizzato principalmente nei sistemi operativi Linux. Supporta grandi dimensioni di file e dischi, e offre funzionalità avanzate come il journaling.

### Comandi Utili
- **fdisk**: Utilizzato per manipolare la tabella delle partizioni MBR.
- **gdisk**: Utilizzato per manipolare la tabella delle partizioni GPT.
- **mkfs**: Utilizzato per creare un file system su una partizione.
- **mount**: Utilizzato per montare un file system.
- **umount**: Utilizzato per smontare un file system.

### Gestione delle Partizioni
- **Creazione**: Le partizioni possono essere create utilizzando strumenti come `fdisk`, `gdisk` o `parted`.
- **Ridimensionamento**: Le partizioni possono essere ridimensionate utilizzando strumenti come `gparted` o `resize2fs`.
- **Formattazione**: Le partizioni devono essere formattate con un file system prima di poter essere utilizzate. Questo può essere fatto utilizzando il comando `mkfs`.

### Backup e Ripristino
- **Backup**: È importante eseguire regolarmente il backup dei dati per prevenire la perdita di dati. Strumenti come `rsync`, `tar` e `dd` possono essere utilizzati per creare backup.
- **Ripristino**: In caso di perdita di dati, i backup possono essere ripristinati utilizzando gli stessi strumenti utilizzati per creare i backup.

Questi appunti coprono i concetti fondamentali sui dischi e le partizioni a livello informatico. Puoi approfondire ciascun argomento per ottenere una comprensione più dettagliata.
