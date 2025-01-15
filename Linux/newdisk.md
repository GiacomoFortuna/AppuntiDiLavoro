# Configurazione di un nuovo disco in Linux

```bash
# 1. Individuare il nuovo disco
lsblk
fdisk -l

# 2. Creare una tabella delle partizioni (opzionale, se il disco è nuovo)
parted /dev/sdX
mklabel gpt
quit

# 3. Creare una nuova partizione
fdisk /dev/sdX
# Dentro fdisk:
# - Premere 'n' per creare una nuova partizione
# - Specificare il tipo (default: primaria)
# - Selezionare i settori (default: intero spazio)
# - Premere 'w' per salvare e uscire

# 4. Verificare la nuova partizione
lsblk

# 5. Creare un Physical Volume (PV) per LVM
pvcreate /dev/sdX1

# 6. Creare un Volume Group (VG)
vgcreate Nome_VG /dev/sdX1

# 7. Creare un Logical Volume (LV)
lvcreate -L 10G -n Nome_LV Nome_VG
# Oppure, per usare tutto lo spazio:
lvcreate -l 100%FREE -n Nome_LV Nome_VG

# 8. Formattare il Logical Volume
mkfs.ext4 /dev/Nome_VG/Nome_LV
# (O usare un altro filesystem, es.: xfs, ext3)

# 9. Montare il Logical Volume
mkdir /mnt/Nome_Mount
mount /dev/Nome_VG/Nome_LV /mnt/Nome_Mount

# 10. Aggiungere al file /etc/fstab per il montaggio automatico
echo '/dev/Nome_VG/Nome_LV /mnt/Nome_Mount ext4 defaults 0 0' >> /etc/fstab

# 11. Verificare
df -h
lsblk

