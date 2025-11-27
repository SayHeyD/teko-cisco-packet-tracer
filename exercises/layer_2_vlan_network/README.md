# Layer 2 VLAN Network

> [!TIP]
> [Switch Configuration Documentation](../../sw/2690.md)

## Table of Contents

* [About](#about)
  * [Credentials](#credentials)
  * [Exercise](#exercise)

## About

The assigment should be a practical example about networks with layer 2 only VLANs.
It also shows that even on a simple network like this, different VLANs for different WLAN
networks are possible, even if only one access point is used.

| Network Name | Network CIDR    | VLAN ID |
|--------------|-----------------|---------|
| Management   | 192.168.1.0/24  | `1`     |
| Internal     | 192.168.10.0/24 | `10`    |
| Guest        | 192.168.99.0/24 | `99`    |

We use VLAN ID `1` for the management network, because it is the default VLAN ID for 
Cisco Network devices.

> [!TIP]
> The available VLAN IDs on most network devices are 1 - 4094

### Credentials

If required the password for all devices always is: `1234`

### Exercise

[Packet tracer file download](./layer_2_vlan_network.pkt)

```
                    PC02 (192.168.10.120/24)
                         |
                         | SSID: Intern → VLAN 10
                         | SSID: Guest → VLAN 99
                         |
                      +-----+
                      | AP  |  (Access Point)
                      +-----+
                         |
                         | Trunk Port
                         | VLANs: 1(U), 10(T), 99(T)
                         |
    ┌────────────────────┼────────────────────┐
    │                    │                    │
    │                 SW2                     │
    │         ┌────┬────┬────┬────┐           │
    │         │ P1 │ P2 │ P3 │... │           │
    │         └────┴────┴─┬──┴────┘           │
    └───────────────────┬─┘───────────────────┘
                        │
                        │ Trunk Port 3
                        │ MGMT, Client, Guest
                        │ VLANs: 1(U), 10(T), 99(T)
                        │
    ┌───────────────────┼────────────────────┐
    │                   │                    │
    │                 SW1                    │
    │         ┌────┬────┬────┬────┐          │
    │         │ P1 │ P2 │ P3 │... │          │
    │         └─┬──┴────┴────┴────┘          │
    └──────────┼─────────────────────────────┘
               │
               │ Access Port 1
               │ VLAN 10 (Untagged)
               │
           ┌───┴───┐
           │ PC01  │
           └───────┘
      192.168.10.100/24

```

What this graph doesn't show is that to make this setup work, we additionally need a 
WLAN Controller. This is because the available WLAN Access Points in Cisco Packet Tracer
do not support Standalone VLAN configuration, with different WLAN SSIDs.

Also note that the Trunk to the WLAN Controller and the WLAN Access Point must have
the VLANs 1, 10, 99 in tagged mode for the setup to work correctly.

The WlAN Controller also needs to have a DHCP Server setup, because the WLAN Access Point
doesn't allow for a static IPv4 connection.
