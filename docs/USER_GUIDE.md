# 🎮 User Guide

## Controls

| Action | Result |
|--------|--------|
| Joystick **left / right** | Switch mode (wraps around: 1 → 2 → 3 → 4 → 1) |
| Joystick **up / down** | Move through the list or pages |
| **Short press** | Select / go back / toggle |
| **Long press** (hold 1 second) | Rescan, in any mode |

A title banner shows for a moment when you change mode, for example `Mode 2 of 4`.

---

## Mode 1: WiFi Scanner

**List screen** (strongest network at the top, `>` marks your choice):

```
>HomeWiFi   -42
 CafeGuest  -67
```
The number is **RSSI** in dBm. Closer to 0 = stronger signal.

**Press** to lock on a network. Then use **down / up** to flip through 3 pages:

| Page | Shows |
|------|-------|
| 1. Info | Network name + **encryption type** (WPA2-PSK, WPA3-PSK, Open...) |
| 2. MAC | The access point's MAC address (BSSID) |
| 3. Live | Signal bars + RSSI + trend arrow (↑ getting stronger, ↓ weaker, = steady). Updates every 1.5 seconds. Shows `Signal lost...` if the network disappears. |

**Press again** to go back to the list.

### Signal cheat sheet

| RSSI | Quality |
|------|---------|
| -30 to -50 dBm | Excellent |
| -50 to -67 dBm | Good |
| -67 to -80 dBm | Weak |
| below -80 dBm | Very weak |

---

## Mode 2: Security Audit

Up / down to browse. Each network gets a grade based on its encryption:

| Grade | Encryption types |
|-------|------------------|
| **GOOD** | WPA3, WPA2/WPA3, WPA2-Enterprise |
| **OK** | WPA2, WAPI |
| **WEAK** `!!` | WPA, WPA/WPA2 mixed |
| **BAD** `!!!` | Open (no password), WEP |

**Press** to see a summary (how many networks are GOOD / OK / WEAK / BAD). Press again to return.

---

## Mode 3: Channels

Up / down picks channel 1 to 13. The screen shows how many networks use it, a small bar graph, and the **Best** channel (1, 6, or 11) with the fewest neighbors. Handy for tuning your own router.

---

## Mode 4: Rogue AP Check

Looks for networks that share the **same name**. Real twins are normal for mesh and extenders, but can also be an **evil twin** (a fake copy of a real network).

| Level | Meaning |
|-------|---------|
| `i` **MULTI-AP** | Same name, same maker, same security. Usually normal. |
| `!!` **SUSPECT** | Same name, **different hardware maker**. Worth a look. |
| `!!!` **DANGER** | Same name, **different encryption**. Very suspicious. |

- Up / down browses the alerts. DANGER entries **blink**.
- **Press** to open detail cards for each access point (security, channel, RSSI, then MAC). Up / down flips the cards. Press again to go back.
- After every scan, if a DANGER twin exists, the LCD **flashes a warning in any mode**.
- `No twins found` means everything looks normal.

> This is a smart guess, not proof. Always check the details before worrying.
