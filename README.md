# SpringOne2018 PCF Demo

## APP Manifests

`Note`: The application source code can be found at the below repos.

- [pcf-articulate-code] (https://github.com/pivotal-education/pcf-articulate-code)
- [pcf-attendee-service-code] (https://github.com/pivotal-education/pcf-attendee-service-code)

## Demonstrate cf push

```
$ cf push -f manifest.yml

## Demonstrate Services

### Create service

```
$ cf create-service cf create-service cleardb spark attendee-db

### Bind service

```
$ cf bind-service attendee attendee-db

### Create user provided service instance

```
$ cf create-user-provided-service attendee-service -p uri
$ cf bind-service articulate attendee-service

## Demonstrate Blue-Green

```
$ cf map-route articulate-v2 cfapps.io -n articulate-sleepy-possum
$ cf unmap-route articulate cfapps.io -n articulate-sleepy-possum

## Demonstrate Metrics

http://metrics.run.pivotal.io/
