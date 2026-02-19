

# Initial setup:


## Docker:

1. Create a docker network for the matrix applications.

```
sudo docker network create --driver=bridge --subnet=10.10.10.0/24 --gateway=10.10.10.1 matrix_net
```

via [#1](https://github.com/AmirDez/matrix-on-premise)

## Creating the admin user:

1. Uncomment this line in the docker-compose.yml:

```
#CONTINUWUITY_ADMIN_EXECUTE: '["users create_user admin"]'
```

2. Run `docker compose up`

The admin user will be created and its password will be printed in the console.
Save it.

3. Re-comment the line you uncommented in step 1. Continuwuity will crash otherwise.

# Deploy

```
sudo docker-compose up -d
```

# Undeploy

```
sudo docker-compose down
```

# (Optional) DDClient

If you require your IP to be updated regularly, you can use ddclient.

```
pamac install ddclient
```

The config for a default install of ddclient can be found at `/etc/ddclient/`. Edit it with the values suggested by your domain register and enable the service with the below commands:

```
systemctl enable ddclient.service
systemctl start ddclient.service
```
