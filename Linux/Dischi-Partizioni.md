# Dischi e Partizioni su Linux


In Linux, la gestione dei dischi e delle partizioni è un aspetto fondamentale dell'amministrazione del sistema. Questo documento fornisce una panoramica dettagliata su come funzionano i dischi e le partizioni in un ambiente Linux.

## Dischi
Un disco è un dispositivo di memorizzazione fisico che può contenere uno o più file system. I dischi possono essere di vari tipi, come HDD (Hard Disk Drive), SSD (Solid State Drive), e NVMe (Non-Volatile Memory Express).

### Identificazione dei Dischi
Per identificare i dischi presenti nel sistema, si può utilizzare il comando `lsblk`:
```bash
lsblk
```
Questo comando elenca tutti i dispositivi a blocchi, inclusi i dischi e le partizioni.

Un altro comando utile è `fdisk -l`, che elenca tutti i dischi e le loro partizioni:
```bash
sudo fdisk -l
```

## Partizioni
Una partizione è una divisione logica di un disco. Ogni partizione può contenere un file system diverso e può essere montata in punti diversi del file system di Linux.

### Creazione di Partizioni
Per creare una nuova partizione, si può utilizzare `fdisk` o `parted`. Ecco un esempio di utilizzo di `fdisk`:
```bash
sudo fdisk /dev/sdX
```
Dove `/dev/sdX` è il disco su cui si desidera creare la partizione. All'interno di `fdisk`, si possono utilizzare vari comandi per creare, eliminare e gestire le partizioni.

### Formattazione delle Partizioni
Dopo aver creato una partizione, è necessario formattarla con un file system. Ad esempio, per formattare una partizione con il file system ext4, si utilizza il comando `mkfs`:
```bash
sudo mkfs.ext4 /dev/sdX1
```
Dove `/dev/sdX1` è la partizione da formattare.

### Montaggio delle Partizioni
Per utilizzare una partizione, è necessario montarla in un punto del file system. Questo si fa con il comando `mount`:
```bash
sudo mount /dev/sdX1 /mnt
```
Dove `/dev/sdX1` è la partizione e `/mnt` è il punto di montaggio.

### Gestione delle Partizioni
Per visualizzare le partizioni montate, si può utilizzare il comando `df`:
```bash
df -h
```
Questo comando mostra l'utilizzo del disco in modo leggibile.

## Strumenti Avanzati
Esistono vari strumenti avanzati per la gestione dei dischi e delle partizioni su Linux, come `LVM` (Logical Volume Manager) e `RAID` (Redundant Array of Independent Disks).

### LVM
LVM permette di creare volumi logici che possono essere ridimensionati dinamicamente. Per utilizzare LVM, si devono installare i pacchetti necessari e seguire una serie di comandi per creare volumi fisici, gruppi di volumi e volumi logici.

### RAID
RAID è una tecnologia che permette di combinare più dischi in un array per migliorare la ridondanza e/o le prestazioni. Esistono vari livelli di RAID, come RAID 0, RAID 1, RAID 5, ecc.

## Conclusione
La gestione dei dischi e delle partizioni è un'abilità essenziale per qualsiasi amministratore di sistema Linux. Conoscere i comandi e gli strumenti giusti permette di gestire efficacemente lo spazio di archiviazione e garantire la stabilità e le prestazioni del sistema.
