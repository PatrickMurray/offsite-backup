# Offsite Backup

Author: Patrick Murray

The objective of this repository is to setup an encrypred
[Resilio Sync](https://www.resilio.com/) replication node with system
monitoring tolling. Such replication nodes may be deployed off-site to increase
availability for targetted datasets.

## Stack

*Hardware:*

1. Raspberry Pi 4 Model B, 8GB 
2. Samsung Evo Select MicroSD Card, 32 GB
3. Seagate Backup Plus Hub, 8TB

*Software:*

1. Raspberry Pi OS Lite
2. [Ansible](https://www.ansible.com/)
3. [Resilio Sync on Linux](https://help.resilio.com/hc/en-us/articles/206178924-Installing-Sync-package-on-Linux)
4. [Grafana Cloud](https://grafana.com/products/cloud/)


## Replication Node Setup

### Boot Medium Imaging

Navigate to the [Raspberry Pi OS website](https://www.raspberrypi.com/software/operating-systems/)
and select "Raspberry Pi OS Lite" - a ZIP archive should begin downloading.
Next, extract the ZIP archive using [`unzip(1)`](https://linux.die.net/man/1/unzip)
and burn the image file (`.img`) to the boot medium using [`dd(1)`](https://linux.die.net/man/1/dd).
For example:

```bash
unzip Downloads/2022-01-28-raspios-bullseye-armhf-lite.zip
root $ dd if= 2022-01-28-raspios-bullseye-armhf-lite.img of=/dev/sda
```

*Note:* The boot medium path (i.e. `/dev/sda`) may be determined using
[`lsblk(8)`](https://linux.die.net/man/8/lsblk).



TODO - Below documentation.



### Image Configuration

#### Enable SSH Service

Mount micro SD

```
root $ mkdir /mnt/pi
root $ mount BOOT_PARITION /mnt/pi
```



## Initial Host Configuration


### Change Default Credentials

Boot up the Raspberry Pi

Username: `pi`
Password: `raspberry`

Change password with `passwd`

Copy SSH public key

```bash
ssh-copy-id pi@192.168.0.81
```


### Ansible Configuration Management

```bash
ansible-playbook --ask-vault-pass main.yml
```



