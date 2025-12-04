# Link Aggregation

> [!TIP]
> [Router Configuration Documentation](../../sw/2690.md)
> [Previous exercise](../link_aggregation)

## Table of Contents

* [About](#about)
  * [Credentials](#credentials)
  * [Exercise](#exercise)

## About

This exercise builds on top of the [previous exercise](../link_aggregation).

| Network Name | Network CIDR    | VLAN ID |
|--------------|-----------------|---------|
| Management   | 192.168.1.0/24  | `1`     |
| Internal     | 192.168.10.0/24 | `10`    |
| Guest        | 192.168.99.0/24 | `99`    |

The goal of this exercise is to configure a router to have multiple VLANs configured on 
one physical network interface and have multiple devices inside the local networks 
to be able to communicate with each other. E.g. `192.168.1.100` can ping `192.168.99.10`.

### Credentials

* Enable Secret: `1234`
* Virtual Terminal Password: `12345`

Username: `root`
Password: `12345`

### Exercise

[Packet tracer file download](https://github.com/SayHeyD/teko-cisco-packet-tracer/raw/refs/heads/main/exercises/routing/routing.pkt)

* Add Router
* Configure VLANs
