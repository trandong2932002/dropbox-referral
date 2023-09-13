# DROPBOX REFERRAL

## Setup DigitalOcean

### [Install doctl and Login](https://docs.digitalocean.com/reference/doctl/how-to/install/)

### [Create your SSH keys](https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/to-team/)

## Create Image

### Preconfig

#### Get available images (*image-id*)

```shell
doctl compute image list-distribution
```

I use ubuntu 20.04

#### Get available regions (*region-slug*)

```shell
doctl compute region list
```

Select a region is suitable for your requirements

#### Get available droplet sizes (*size-slug*)

```shell
doctl compute size list
```

1vCPU and 1GB Ram is enough

#### Get availble ssh keys (*ssh_key-id*)

```shell
doctl compute ssh-key list
```

Select your ssh key to connect

### Create droplet and Configure

```powershell
doctl compute droplet create `
  --image <image-id> `
  --region <region-slug> `
  --size <size-slug> `
  --ssh-keys <ssh_key-id> `
  --wait `
  <droplet_name>
```

```shell
doctl compute droplet create \
  --image <image-id> \
  --region <region-slug> \
  --size <size-slug> \
  --ssh-keys <ssh_key-id> \
  <droplet_name>
```

#### Get droplet information (*ipv4*, *droplet-id*)

```shell
doctl compute droplet list
```

Get Public IPv4 of your droplet

#### Connect to droplet

```shell
ssh root@<ipv4>
```

#### [Install Squid as proxy server](https://www.digitalocean.com/community/tutorials/how-to-set-up-squid-proxy-on-ubuntu-20-04)

#### [Install dropbox](https://www.dropbox.com/install-linux)

### Create snapshot

#### Shutdown your droplet

```shell
doctl compute droplet-action shutdown <droplet-id>
```

#### Take a snapshot

```shell
doctl compute droplet-action snapshot --snapshot-name <snapshot_name> <droplet-id>
```

#### Remove droplet

```shell
doctl compute droplet delete <droplet-id>
```

## Create Droplet to get Dropbox referral

> Do this multiple time

### Get snapshots (*snapshot-id*)

```shell
doctl compute snapshot list
```

Select dropbox snapshot you just created

### Create droplet

```powershell
doctl compute droplet create `
  --image <snapshot-id> `
  --region <region-slug> `
  --size <size-slug> `
  --ssh-keys <ssh_key-id> `
  <droplet_name>
```

```shell
doctl compute droplet create \
  --image <snapshot-id> \
  --region <region-slug> \
  --size <size-slug> \
  --ssh-keys <ssh_key-id> \
  <droplet_name>
```

### Get referral

#### Sent an invitation

#### Using proxy to get referral and create dropbox account

#### Connect to droplet and login to Dropbox app