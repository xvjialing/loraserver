---
title: Gateway management
menu:
    main:
        parent: features
        weight: 2
description: Gateway statistics aggregation, location and channel-plan (re)configuration.
---

# Gateway management

LoRa Server has support for managing gateways. Gateways can be created either
by enabling *create on stats* (see [gateway configuration]({{<ref "/install/config.md">}}))
or by using the [api]({{<ref "/integrate/api.md">}}).

## Gateway location

The (last known) location of the gateway will be stored in the database. When
the gateway is equipped with a GPS, its location will be automatically updated
after every stats update in case it has changed. Else, it can be manually set
when creating or updating the gateway.

## Gateway statistics

LoRa Server exposes the gateway statistics on a pre-configured aggregation
intervals (see [Configuration]({{<ref "/install/config.md">}})).
By default these intervals are configured to: minute, hour, day and month.

The following data retention is being used:

* `MINUTE` - one hour
* `HOUR` - one day
* `DAY` - one month
* `MONTH` - one year

## Gateway re-configuration

If a [gateway-profile]({{<relref "gateway-profile.md">}}) is assigned
to the gateway, LoRa Server will push configuration updates to the gateway
to keep its channel-plan in sync with the configuration of the network.
This is triggered when LoRa Server receives gateway statistics (which also
contains the current configuration version of the gateway). If there is new
version of the configuration available, then it will be pushed by LoRa Server
to the gateway.

Note that this feature must also be configured in the
[LoRa Gateway Bridge configuration](/lora-gateway-bridge/install/config/).
