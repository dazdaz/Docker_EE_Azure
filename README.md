Instructions on howto deploy Docker Enterprise Edition onto Azure

## 1. Deploy Docker Enterprise Edition 17.06.2.
The Docker store points back to the Azure marketplace, so use either link.

https://azuremarketplace.microsoft.com/en-us/marketplace/apps/docker.dockerdatacenter?tab=Overview
https://store.docker.com/editions/enterprise/docker-ee-azure

Deployment Documentation here :
https://docs.docker.com/docker-for-azure/

Best practices on deploying Docker EE :
https://success.docker.com/article/Docker_Reference_Architecture-_Docker_EE_Best_Practices_and_Design_Considerations


## 2. Create the SP
```
docker run -ti docker4x/create-sp-azure dockerspdemo

Your access credentials ==================================================
AD ServicePrincipal App ID:       071aaaaa-333-4444-a079-888888888888
AD ServicePrincipal App Secret:   1234567890qnRn8888888888aaa
AD ServicePrincipal Tenant ID:    721223342424-4444-5555-2d7cd011daaa
```

## 3. Copy in your SSH public key into the web ui - This is just an example, and not a live key.
```
ubuntu1704:~$ cat .ssh/id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAmLmwkzQDjEOW1Rj3TP5NldVDqUODVH9xuYrkeaSkxtdP
J8D9Hz+XAWnGAXdaIkCVOw2YEfHKWSo6befgNxiS+AKS+S+wM/bJpc4qOLe5ozFjZPNRHcw5O8WkgP5g
/wg2BOvxBqSKpsSzvi4rYVRLtl7TLVMyajhELiJ9GqT8f25gr3jFmtuQQIkRES1aC4oL2tHsn529POfP
1lPhh5tb2FbqEpm9L3779ljjkSX7mD4zza3zUckkuAIb5R7KSOrvPnJaEU903hrI0tx5omGyDy+h/2D1
h0aqHanPcU9Ml91ZpMKdpa0+FeVgs2M3LHYTNnvZ76ScV2VtUQwm3YEvjw== alex@whoever.org

Docker Username:
ddcadmin
admin123
P@ssword1234


https://store.docker.com/editions/enterprise/docker-ee-trial

Trial subscription is Valid for 1 month - "not valid"

Keys look like this :
{"key_id":"88888888-0Aq5xVFmPYb6tswdtmGvtI30dC1111111111","private_key":"888888888hM7b8chBiAbPenOEM1IYxxgzD4Nos48MkYu",\
"authorization":"ewogICAicGF5bG9hZCI6ICJleUpsZUhCcGNtRjBhVzl1SWpvaU1qQXhPQzB3TWkweE1WUXdNam8xTWpveE1Gb2lMQ0owYjJ0bGJpSTZ\
JbXN4YlVWbmIxQnVjMVI0VlcwelQxZGFXWFphUVdWbGJVOURNR1F3YkZZNVVEUnVNbEZwT1RWWlpqZzlJaXdpYldGNFJXNW5hVzVsY3lJNk1UQXNJbk5qWVc1\
dWFXNW5SVzVoWW14bFpDSTZkSEoxWlN3aWJHbGpaVzV6WlZSNWNHVWlPaUpQYm14cGJtVWlMQ0owYVdWeUlqb2lWSEpwWVd3aWZRIiwKICAgInNpZ25hdHVyZ\
XMiOiBbCiAgICAgIHsKICAgICAgICAgImhlYWRlciI6IHsKICAgICAgICAgICAgImp3ayI6IHsKICAgICAgICAgICAgICAgImUiOiAiQVFBQiIsCiAgICAgICA\
gICAgICAgICJrZXlJRCI6ICJKN0xEOjY3VlI6TDVIWjpVN0JBOjJPNEc6NEFMMzpPRjJOOkpIR0I6RUZUSDo1Q1ZROk1GRU86QUVJVCIsCiAgICAgICAgICAgIC\
AgICJraWQiOiAiSjdMRDo2N1ZSOkw1SFo6VTdCQToyTzRHOjRBTDM6T0YyTjpKSEdCOkVGVEg6NUNWUTpNRkVPOkFFSVQiLAogICAgICAgICAgICAgICAia3R5I\
jogIlJTQSIsCiAgICAgICAgICAgICAgICJuIjogInlkSXktbFU3bzdQY2VZLTQtcy1DUTVPRWdDeUY4Q3hJY1FJV3VLODRwSWlaY2lZNjczMHlDWW53TFNLVGx3\
LVU2VUNfUVJlV1Jpb01OTkU1RHM1VFlFWGJHRzZvbG0ycWRXYkJ3Y0NnLTJVVUhfT2NCOVd1UDZnUlBIcE1GTXN4RHpXd3ZheThKVXVIZ1lVTFVwbTFJdi1tcTd\
scDVuUV9SeHJUMEtaUkFRVFlMRU1FZkd3bTNoTU9fZ2VMUFMtaGdLUHRJSGxrZzZfV2NveFRHb0tQNzlkX3dhSFl4R05sN1doU25laUJTeGJwYlFBS2syMWxnNz\
k4WGI3dlp5RUFURE1yUlI5TWVFNkFkajVISnBZM0NveVJBUENtYUtHUkNLNHVvWlNvSXUwaEZWbEtVUHliYncwMDBHTy13YTJLTjhVd2dJSW0waTVJMXVXOUdrcT\
R6akJ5NXpoZ3F1VVhiRzliV1BBT1lycTVRYTgxRHhHY0JsSnlIWUFwLUREUEU5VEdnNHpZbVhqSm54WnFIRWR1R3FkZXZaOFhNSTB1a2ZrR0lJMTR3VU9pTUlJSX\
JYbEVjQmZfNDZJOGdRV0R6eHljWmVfSkdYLUxBdWF5WHJ5clVGZWhWTlVkWlVsOXdYTmFKQi1rYUNxejVRd2FSOTNzR3ctUVNmdEQwTnZMZTdDeU9ILUU2dmc2U3R\
fTmVUdmd2OFluaENpWElsWjhIT2ZJd05lN3RFRl9VY3o1T2JQeWttM3R5bHJOVWp0MFZ5QW10dGFjVkkyaUdpaGNVUHJtazRsVklaN1ZEX0xTVy1pN3lvU3VydHBzU\
FhjZTJwS0RJbzMwbEpHaE9fM0tVbWwyU1VaQ3F6SjF5RW1LcHlzSDVIRFc5Y3NJRkNBM2RlQWpmWlV2TjdVIgogICAgICAgICAgICB9LAogICAgICAgICAgICAiYW\
xnIjogIlJTMjU2IgogICAgICAgICB9LAogICAgICAgICAic2lnbmF0dXJlIjogInlZOFk3OVVFVS05TDdwVy1xamZ1dzhva1BPemk5c0c2cmlzcmpTcWREaTdjMlZB\
N1FFckw4SVU3d01FTmw2dEFVV1JsNkpPVGFXMnZPNks1ZzJFX3pEZTQ0dlhMVWphelg4RHRBNkkzZmQ4QUJOaWxRRTVWM0lEcC0tTGRjUnhyMEdvZnphMFB2dm80Z2\
daOTdKc29zMmZ5T3d6OEhkRmFCSVQ4eGpsUC1tSmZFdk5zcEVrbUM1WkNhYldlZ3RWYUZaN1pTU3gxdGNTdGtocDhhZWFEUzY2ZVF2WkNhNTlBLU5MbVN1YmpMYjkwc\
EdmZDBBNUNfMmxvX25YTXFYMGxPUXNCMEQ0MW9kdGhvYk1mY3BHLVF4UVU1a1JuYW01SnFBVVlNRkZIUkc2NkdHY005VnpTY2xWbHF4Mi14bmZweS1PMTBoY0RwcFNL\
M2w2eDM1clpsV25xMU9Kekc1NkFKYWJiUmd4V2RrMU5vbklIbTQxWG0zeGZ0YndMZURFdzAtSGNfb0prdm1zV2VIRERHbnY4aTNGRXhxTjFOd21zUzZQWXY2RGZMYllj\
Q25ZRW9CZ1lQazZzNFhXMXdGRGVjb1piallBb3dDY0d0SU4ycml1b1RCNG5VTXgySWJwcTE3SHhaakJmUE1OLUpZTkxHeXkwTWlpTmFSYkJtbmxXUndIZ2kzbTJ1d0c5\
MkN5UkhmZno2SGRBemRaQWZxQ2xWQkxJQzZjd05nWVJQaG04blVXVFBRQ1N5dDJYdnlFMEV4QXhNWllXaWFhVkZKUzhqcnREVHZieTcxYWNiUEl0dTBYaGRUa2tpVE1p\
NHJMeTEtSDE0NXRNajY5YnhTci1VSGowNFZNU3RjMjJKRHZTYk5PWTV1Q2VqNDliVnVRa292VUFLZUQyY0E0IiwKICAgICAgICAgInByb3RlY3RlZCI6ICJleUptYjNK\
dFlYUk1aVzVuZEdnaU9qRTJPQ3dpWm05eWJXRjBWR0ZwYkNJNkltWlJJaXdpZEdsdFpTSTZJakl3TVRndE1ERXRNVEJVTURJNk5USTZNakphSW4wIgogICAgICB9CiAg\
123456=="}
```

1 manager node
2 x Linux UCP worker
1 x Windows UCP worker

Windows admin password : P@ssword1234


## 4. Goto Docker Resource Group / Deployment / Check Status

## 5.Deploy a container into Swarm

Wait 5 minutes after deployment has completed before you can login to UCP and DTR.

Login to UCP Manager, DTR Replica and UCP Workers.
Access UCP Manager, DTR Replica and UCP Workers through the dockerswarm-externalLoadBalancer-public-ip

Must be HTTPS
UCP Manager / ddcadmin admin123
https://ucplb-g1234567890dw.southeastasia.cloudapp.azure.com
https://ucplb-5555555555555.southeastasia.cloudapp.azure.com

Must be HTTPS
DTR Manager / ddcadmin P@ssword1234
https://dtrlb-g1234567890dw.southeastasia.cloudapp.azure.com
https://dtrlb-5555555555555.southeastasia.cloudapp.azure.com

How to configure public IP on DTR replica

Goto UCP / Stack / New Stack
Mode / Containers

Copy and paste the config below.



## Additional Tasks
*Download UCP Bundle
```
source env.sh


version: '3.2'

services:
  app:
    image: yongshin/docker-node-app:latest
    deploy:
      replicas: 3
      labels:
        com.docker.ucp.mesh.http: "external_route=http://nodeapp.david.dtcntr.net,internal_port=4000"
    environment:
      - "MONGODB_SERVICE_SERVICE_HOST=nodeapp_db"
    ports:
      - 4000
    networks:
      - ucp-hrm
      - nodeapp-network

  db:
    image: clusterhq/mongodb
    deploy:
      replicas: 1
    networks:
      - nodeapp-network
    ports:
     - 27017:27017
    volumes:
     - db:/data/db

volumes:
  db:
    driver: local

networks:
  nodeapp-network:
    driver: overlay
  ucp-hrm:
    external: true


version: '3.2'

services:
  app:
    image: pengbai/docker-supermario:latest
    deploy:
      replicas: 1
    ports:
      - 8080:8080
```

## Running a container in Docker Swarm
```
docker service create -p 80:80 --replicas 1 --name myfirstapp torosent/myfirstapp
docker service inspect --pretty myfirstapp
docker service scale myfirstapp=5
docker service ps myfirstapp
docker service rm myfirstapp
```

# SSH into a Swarm cluster
```
ssh azureuser@myswarmclu-swarmworkshop-1234eamgmt.ukwest.cloudapp.azure.com -A -p 2200
```

## Random Notes
https://docs.docker.com/compose/compose-file/#compose-and-docker-compatibility-matrix
Docker 17.06 does'nt supported encrypted overlay
Docker EE supported for Linux works on 
LCOW
Download UCP bundle, configured per user - allows you to manage the swarm and deploy to the swarm
source env.sh


Compose file version 3 reference
https://docs.docker.com/compose/compose-file/
https://docs.docker.com/docker-for-azure/deploy/

