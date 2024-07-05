> 📜 This software is intended to be used for media files you own the rights for. The author of the repository
> is not responsible for any misuse of this software.

# Ansible Homeserver

👇 Ansible script to setup a configurable homeserver instance including features like media management, document storage, dns add blocker and much more 🔥

> 🚧 This project and it's documentation is still in development. Use at your own risk.

- https://www.authelia.com/reference/guides/generating-secure-values/#generating-a-random-alphanumeric-string

## Mount drive

```bash
# Identify the new disk on the system
sudo parted -l | grep Error

# Chose partition standard
sudo parted /dev/sda mklabel gpt

# Create new partition
sudo parted -a opt /dev/sda mkpart primary ext4 0% 100%

# Create filesystem for partition
sudo mkfs.ext4 -L datapartition /dev/sda1

# Create filesystem mount point
sudo mkdir -p /mnt/data

# Mounting on boot
sudo nano /etc/fstab
$ LABEL=datapartition /mnt/data ext4 defaults 0 2

# Remount the drives
sudo systemctl daemon-reload
sudo mount -a
```

```
sudo mount -t cifs -o vers=2.0,username=devtobias,password=Uj9caErAnXBta2o //Homeserver/data /mnt/nas/
```

https://phoenixnap.com/kb/ubuntu-samba
https://www.digitalocean.com/community/tutorials/how-to-partition-and-format-storage-devices-in-linux

## Manual steps (Backups)

### Uptime Kuma

Database can just be imported, since no users are managed within:

- kuma.db

### Radarr

Database can just be imported, since no users are managed within, just basic credentials via Authelia:

- radarr.db
- config.xml

# ⚖ License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for more details.
