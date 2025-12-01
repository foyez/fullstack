# Full-stack

- Full stack developer - who can develop on **client (HTML, CSS, Javascript, React, etc.)**, **server (Node, Golang, PHP, etc.)** and **Database (SQL (MySql, Postgres), NoSql (MongoDB), etc.)** software

## Command Line

<details>
<summary>View contents</summary>

- **cd** - change directory
- **ls** - list directory contents
- **pwd** - print working directory
- **mkdir** - make directory

```bash
> mkdir test foo # make two directories called test and foo
> mkdir -p ~/test # make a test directory if it doesn't exists
```

- **rmdir** - remove directory

- **cat** - show file contents

```bash
> cat info.txt
> cat ~/.config
```

- **man** - command manual
- **less** - show file contents by page
- **rm** - remove file
- **echo** - repeat input
- **cp** - copy files and directories (c.g. `cp file.txt folder`)
- **mv** - move (rename) files (e.g. `mv file1.txt file2.txt folder`)
- **grep** - searches text and strings in a given file or searches the given file for lines containing a match to the given strings or words

```bash
> grep 'word' filename

> fgrep 'word-to-search' file.txt

> grep 'word' file1 file2 file3

> grep 'string1 string2'  filename

> cat otherfile | grep 'something'

> command | grep 'something' # ls | grep README.md

> command option1 | grep 'data'

> grep --color 'data' fileName

> grep [-options] pattern filename

> fgrep [-options] words file
```

### Shells - allow to run command lines

Example: bash, zsh, fish, etc.

```bash
> echo $0 # show current shell
```

### Terminal - runs shell applications

Example: iTerm2, hyper, Powershell, etc.

```txt
SHELL --> TERMINAL --> KERNEL
```

Kernel is the core of the operating system. It talks to the actual machine layer.

</details>

## How does the internet work?

<details>
<summary>View contents</summary>

- **Internet (International Network)** - A system of globally interconnected devices
- **Intranet (Internal Restricted Access Network)** - Private internet, e.g., vpn
- **VPN (Virtual Private Network)** - a intranet, which is just a private internet of different servers talking to each other (e.g. LAN), but it's inaccessible from the outside.
- **LAN (Local Area Network)** - confined to one building or site. It's smaller than a WAN. Often a LAN is a private network to an organization or business.
- **WAN (Wide Area Network)** - extends over a large area. A WAN is created by connecting lots of other LANs together.
- **IP (Internet Protocol)** - a set of rules. For example, how to accept (read, write or send back) a well form data
- **IP Address** - A label assigned to an internet connected device

```txt
IPv4 - 8.8.8.8 (4.3 billion addresses 4.3 * 10^9)
IPv6 - 2001:4860:4860:8888 (340 undecillion addresses 3.4 * 10^38)
```

- **TCP (Transmission Control Protocol)** - connection-oriented protocol, guarantee delivery of data, possible to retransmit lost packets. Used by HTTPS, HTTP, SMTP, POP, FTP, etc
- **UDP (User Datagram Protocol)** - connection-less protocol, can't guarantee delivery of data, not possible to retransmit lost packets. Used by video conferencing, streaming, DNS, VoIP, etc

[TCP vs UDP](https://www.lifesize.com/en/blog/tcp-vs-udp/)

- To check a site is up and running

```bash
> ping twitter.com # ping hits a server
```

- **DNS (Domain Name System)**<sup>[link](cloudflare.com/learning/dns/what-is-dns/)</sup>

The Domain Name System (DNS) is the phonebook of the Internet. Humans access information online through domain names, like nytimes.com or espn.com. Web browsers interact through Internet Protocol (IP) addresses. DNS translates domain names to IP addresses so browsers can load Internet resources.

Each device connected to the Internet has a unique IP address which other machines use to find the device. DNS servers eliminate the need for humans to memorize IP addresses such as 192.168.1.1 (in IPv4), or more complex newer alphanumeric IP addresses such as 2400:cb00:2048:1::c629:d7a2 (in IPv6).

```txt
domain: foyez.com
subdomain: blog.foyez.com
tld: com
```

- **Nameservers**: Map domains to IP addresses

- **Traceroute**

Traceroute is a network diagnostic tool used to track
in real-time the pathway taken by a packet on an IP network from source to destination, reporting the IP addresses of all the routers it pinged in between. Traceroute also records the time taken for each hop the packet makes during its route to the destination.

It helps diagnose network problems. Traceroute will tell you exactly where the hops break down if you can't connect.

```bash
> man traceroute # traceroute manual
> traceroute google.com # run traceroute
```

Ping and Traceroute both uses ICMP (Internet Control Message Protocol) requests.

- **Hop**: A hop is a computer networking term that refers to the number of routers that a packet (a portion of data) passes through from its source to its destination.

- **Packet**: Packet is a little bit of information you can transmit.

</details>

## Networking <sup>[ref](https://www.youtube.com/playlist?list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF)</sup>

<details>
<summary>View contents</summary>

## What an IP address *is*

* Like a phone number for devices on a network — lets devices talk.
* Every device that wants to talk on a network or the internet needs one (phone, watch, smart bulb, etc.).
* IP addresses come in **IPv4** format here: `A.B.C.D` (four octets, each 0–255).

---

## How devices get an IP

* **DHCP** (think: *Oprah of IPs*): the router automatically hands out IP addresses to devices on the network.
* You can also set static IPs manually (not covered in detail here).

---

## The three important values you’ll see on your device

* **IP Address** — the device’s address (e.g. `192.168.1.12`)
* **Subnet Mask / Netmask** — tells you which part of the IP is the *network* and which is the *host* (e.g. `255.255.255.0`)
* **Default Gateway** — the router that takes traffic off your local network (often `192.168.1.1`)

Commands:

* Windows: `ipconfig`
* Linux/macOS: `ifconfig` (or `ip addr` on modern Linux)
* Phone: Settings → Wi-Fi → network details

---

## Network vs Host portion (the core idea)

* Subnet mask determines which octets are **locked** (network) and which can **change** (host).
* **Hack:** If an octet in the subnet mask is `255`, the corresponding octet in the IP is fixed for the whole network.

  * Example: `255.255.255.0` ⇒ first three octets (`A.B.C`) are network, last (`D`) is host.
  * So `192.168.1.X` — the `192.168.1` is the network; `X` is the host number.

Analogy:

* Network portion = **street name** (e.g., Private Drive)
* Host portion = **house number** (e.g., `4`, `5`, `6`)
* If two devices share the same street (network), they can directly hand the packet to each other. If not, they call the **router** (default gateway / UPS).

---

## Reserved addresses in a network

For a typical `/24` (mask `255.255.255.0`), IPs run `X.X.X.0` → `X.X.X.255`:

* **Network address** = `.0` (first address) — *not assignable to hosts*
* **Broadcast address** = `.255` (last address) — *used to send to everyone*
* **Router / default gateway** commonly uses one host IP (e.g. `.1`) — typically taken

### Counting usable addresses (how many devices you can assign)

* Total addresses = `2^(number of host bits)`

  * For `/24` there are 8 host bits ⇒ `2^8 = 256` addresses
* Usually subtract 2 for network & broadcast:

  * Usable = `256 - 2 = 254`
* If the router uses one IP (commonly), that still counts as one of the usable addresses, leaving `253` *other* devices you can assign addresses to.

---

## Quick examples / cheats

* Subnet mask `255.255.255.0` = `/24` = 256 total addresses (`.0` → `.255`)

  * Network address: `192.168.1.0`
  * First usable often: `192.168.1.1` (commonly the router)
  * Last usable: `192.168.1.254`
  * Broadcast: `192.168.1.255`
* If mask were `255.255.255.128` = `/25`:

  * Host bits = 7 → `2^7 = 128` addresses per subnet (useable 126 normally)

---

## Mnemonics & small reminders

* **Oprah = DHCP** (gives out IPs: “You get an IP! You get an IP!”)
* **255 means locked** — that octet won’t change across that network.
* **Network = street; Host = house number** — if same street, hand it over; if not, call the router.
* **Always subtract 2** for network & broadcast when counting usable addresses; subtract any additional reserved IPs (like a router) only if you’re counting *free* remaining addresses.

---

# 📝 IP Address Classes & Mismanagement

## 🌐 Why We Ran Out of IPv4

* There are **4.3 billion IPv4 addresses** (`2^32 = 4,294,967,296`).
* In the early 1980s, this seemed like “more than enough.”
* Two big things were underestimated:

  1. **The growth of the internet** (huge).
  2. **Explosion of devices** needing IPs (IoT: watches, ovens, toilets, etc.).

Result → **Massive mismanagement of IP ranges**.

---

# 📦 IP Address Classes (Classful Networking)

IPv4 addresses are four numbers (0–255) separated by dots.

They were grouped into **classes A, B, C, D, E**.

```
Class A: 0.0.0.0 – 127.255.255.255
Class B: 128.0.0.0 – 191.255.255.255
Class C: 192.0.0.0 – 223.255.255.255
Class D: 224.0.0.0 – 239.255.255.255 (Multicast)
Class E: 240.0.0.0 – 255.255.255.255 (Experimental)
```

---

# 🎯 The Big Problems

## 1. **Giant Networks Given Away**

Class A networks have:

* **16,777,214 host addresses each**
* Only **126** usable networks in Class A.

Example companies with Class A blocks:

* GE (3.0.0.0)
* IBM (9.0.0.0)
* AT&T (12.0.0.0)
* Xerox (13.0.0.0)
* HP (15.0.0.0)

→ Far more IPs than they ever needed.

---

## 2. **Default Subnet Masks Made Networks Too Big**

### Class A

* Subnet mask: `255.0.0.0`
* Host capacity: **16.7 million**

### Class B

* Subnet mask: `255.255.0.0`
* Hosts per network: **65,534**

### Class C

* Subnet mask: `255.255.255.0`
* Hosts per network: **254**
* **Most efficient** of the classful group.

---

# 🧠 Subnetting Preview

Class A, B, C networks can be subdivided into smaller networks with new subnet masks.
Doing this is called **classless addressing** (CIDR).

Example:

* IBM’s 9.0.0.0/8 can be sliced into smaller subnets like:

  * `9.40.0.0/16`
  * `9.40.1.0/24` etc.

> Modern networks are almost always **classless**.

---

# ❗ Wasted / Reserved Address Space

## Class D

* Range: **224.0.0.0 – 239.255.255.255**
* Purpose: **Multicast**
* Not usable for hosts.

## Class E

* Range: **240.0.0.0 – 255.255.255.255**
* Purpose: **Experimental**
* Not usable in normal networks.

---

# 🔁 The Missing Range: 127.x.x.x

Ever notice Class A stops at 126 and Class B starts at 128?

Where is **127.x.x.x**?

→ **Reserved for loopback testing**
Anything from `127.0.0.1` to `127.255.255.255` points back to your own machine.

You only need **127.0.0.1**, but they reserved **the whole 16 million address block**.

Example test:

```
ping 127.0.0.1
```

or even

```
ping 127.151.151.8
```

Both loop back to you.

---

# 🩹 Why This Caused IPv4 Exhaustion

* Huge chunks reserved and unusable.
* Class A and B given away too generously.
* Networks were sized much larger than needed.
* Devices exploded in number.

→ IPv4 exhaustion.

---

# 🩼 The Fix

* **NAT** (first bandaid)
* **CIDR** (classless addressing)
* **Eventually IPv6**

---

# 📌 Key Takeaways to Memorize

* IPv4 has **4.3 billion addresses** → not enough.
* Classful addressing wasted huge amounts.
* Default subnet masks:

  * A → `255.0.0.0`
  * B → `255.255.0.0`
  * C → `255.255.255.0`
* Class D = multicast; Class E = experimental.
* `127.x.x.x` = loopback range (all 16M of them…).

---

# 📝 RFC 1918, Private IPs & NAT

## 🚨 1996 Crisis: The Internet Was “Running Out”

* IPv4 = **4.3 billion** addresses → seemed huge early on
* By the mid-90s → **exhaustion began**
* Not enough public IPs for every device
* **Solution:** RFC 1918 (Private IP addresses) + **NAT**

---

# 🛡️ RFC 1918 — The “Band-Aid” That Saved the Internet

## 🎯 What RFC 1918 Introduced

Created **Private IP ranges** that *cannot* be routed on the public internet:

### **Private IPv4 Blocks**

| Class | Private Range                 | Default Mask  |
| ----- | ----------------------------- | ------------- |
| A     | 10.0.0.0 – 10.255.255.255     | 255.0.0.0     |
| B     | 172.16.0.0 – 172.31.255.255   | 255.255.0.0   |
| C     | 192.168.0.0 – 192.168.255.255 | 255.255.255.0 |

### ✔ Why this helped

* These IPs **don’t need to be unique globally**
* Every home, business, data center can reuse the exact same ranges
* Allows **millions** of devices to exist without needing public addresses

**Most common home network:** `192.168.1.0/24`
(Routers love Class C.)

---

# 🧱 Public vs Private IPs — The Key Difference

### **Public IP**

* Globally unique
* Routable on the internet
* Needed for reaching external sites like google.com, networkchuck.coffee

### **Private IP**

* Only works inside your local network
* Not routable on the internet
* Given to your devices by your router (DHCP)

Your device right now: **private**
Your home’s internet connection: **one public IP**

---

# 🔀 NAT — Network Address Translation (The Magic)

NAT is the **second half of the Band-Aid**.

## 🌟 What NAT does

* Lets **hundreds** of private devices share **ONE public IP**
* Happens automatically on your router

Flow:

1. Your device (private IP) → wants google.com
2. Sends traffic to the router
3. **NAT translates** the private IP → public IP
4. Traffic goes out with the public IP
5. Response returns
6. NAT remembers which internal device requested it
7. Routes back to the correct device

### 📌 Result

To the outside world:
**All devices = one identity → the router’s public IP**

This is why “What is my IP?” in Google shows **one** IP for your entire home.

---

# 🏠 Example (NetworkChuck Style)

Your network:

* Toilet: `192.168.1.25`
* PC: `192.168.1.100`
* Phone: `192.168.1.204`
* Router’s public IP (from ISP): `11.5.4.28`

Every device → goes out to the internet as **11.5.4.28**

Your router = **Oprah**
“You get NAT! You get NAT! Everyone gets internet!”

---

# 🌐 Why NAT + Private IPs Saved the Internet

Without them:

* Every device (phones, TVs, smart toilets) would need a public IP
* We'd have run out decades ago
* Home networking would be impossible
* The modern internet wouldn’t exist

---

# ⚠️ But… We STILL Ran Out (IPv4 Exhaustion)

Even with NAT + private addressing:

* ISPs, carriers, businesses still needed more public IPs
* IPv4 = **2³²** addresses (not enough long-term)

So the world began adopting:

---

# 🟦 IPv6 — The Long-Term Solution

* 128-bit address space
* **2¹²⁸ possible IPs** (staggeringly huge)
* Every device can have a public address
* No NAT required in theory
* Mobile carriers commonly give phones **IPv6 public addresses** today

IPv4 still dominates → but IPv6 usage is rapidly growing.

---

# 🧭 Summary (TL;DR)

* **Public IPs** = globally unique, used on the internet
* **Private IPs (RFC 1918)** = reused everywhere, not routable
* **NAT** = lets entire networks share one public IP
* Private IPs + NAT literally **saved IPv4**
* But IPv6 is the real long-term fix

---

# 🧠 Quick Memory Hooks

* **Private = local only**
* **Public = internet-visible**
* **NAT = translator / mask / identity swapper**
* **RFC 1918 = the Band-Aid**
* **IPv6 = the future (2¹²⁸ addresses!)**

---

Below are **clean, organized, memory-friendly Markdown notes** summarizing the *actual concepts* from the video transcript you provided — **without the ads, filler, jokes, or distractions**.

These are optimized for:

* fast recall
* understanding subnetting foundations
* practicing binary ↔ decimal conversion
* remembering key rules

---

# 🧠 IP Addresses & Binary

## #️⃣ What an IP Address Really Is

* You normally see an IP like: `192.168.1.21` → **decimal format**
* Computers see it as **binary** → 32 bits like:
  `11000000.10101000.00000001.00010101`
* Think of binary as **“Matrix mode”** — computers only work with **1s (on)** and **0s (off)**

---

# 📦 Bits, Bytes & Octets

* **1 byte = 8 bits**
* **1 IP address = 32 bits = 4 bytes**
* Each part between dots = **1 octet = 8 bits**

```
192 . 168 .   1 .  21
↓      ↓      ↓      ↓
8b    8b     8b     8b   = 32 bits
```

---

# 🔌 Binary = ON / OFF

* `1` = ON
* `0` = OFF
* Computers literally treat binary like switches.

---

# 🧮 The Powers of Two Table (Your Decoder Ring)

This chart is EVERYTHING for subnetting & conversions.

### **Powers of Two for one octet**

| Bit Position | Value |
| ------------ | ----- |
| 1            | 128   |
| 2            | 64    |
| 3            | 32    |
| 4            | 16    |
| 5            | 8     |
| 6            | 4     |
| 7            | 2     |
| 8            | 1     |

Short version (left → right):
`128  64  32  16   8   4   2   1`

This is used for:
✔ Converting **binary → decimal**
✔ Converting **decimal → binary**

---

# 🔄 Converting Binary → Decimal

Example binary octet:
`11000000`

Steps:

1. Line up bits with the powers of two table
2. Keep the values where the bit = 1
3. Add them up

```
1 1 0 0 0 0 0 0
128+64 = 192
```

So `11000000` → **192**

---

## Another example

Binary: `10101000`

```
1 0 1 0 1 0 0 0
128 + 32 + 8 = 168
```

So `10101000` → **168**

---

# 🔄 Converting Decimal → Binary

Example: **172**

Process:

1. Compare 172 to the largest power of two ≤ it.
2. Subtract and continue.

```
172 ≥ 128 → 1   (172−128 = 44)
44  ≥ 64  → 0
44  ≥ 32  → 1   (44−32 = 12)
12  ≥ 16  → 0
12  ≥ 8   → 1   (12−8 = 4)
4   ≥ 4   → 1   (4−4 = 0)
0   ≥ 2   → 0
0   ≥ 1   → 0
```

Binary result:
`10101100`

---

## Another example: **16**

```
16 ≥ 128 → 0
16 ≥ 64  → 0
16 ≥ 32  → 0
16 ≥ 16  → 1 (16−16 = 0)
0 ≥ 8    → 0
0 ≥ 4    → 0
0 ≥ 2    → 0
0 ≥ 1    → 0
```

Binary:
`00010000`

---

# ⭐ Why This Matters: Subnetting

* Subnetting **requires** fast binary understanding
* CIDR notation (like `/24` → 24 bits are 1s) is literally binary
* Network/host boundaries depend on binary math
* This skill is **leg day** — impossible to skip and still “get” subnetting

---

# 🧩 Recap / Core Concepts

* IP addresses are **32 bits**
* Binary is the computer’s native language
* Each octet uses **powers of two**
* Converting back and forth is essential for:

  * Subnet masks
  * CIDR ranges
  * Network/host calculations
  * Address planning

---

# 🧠 Subnet Mask

*(Why 255 freezes the network portion, how binary reveals network + host bits, and how host count is calculated)*

---

# 🌐 1. What a Subnet Mask Actually *Does*

A subnet mask tells you:

* **Which part of the IP address is the network portion**
* **Which part is the host portion**
* **How big the network is**
* **How many IP addresses are available**
* It does this using **binary patterns of 1s (network bits) and 0s (host bits)**

Every IP address *must* have a subnet mask.

---

# #️⃣ 2. Why 255 Means “Frozen / Cannot Change”

Subnet masks are numbers like:

```
255.255.255.0
```

### Why does **255** mean “this octet cannot change”?

Because **255 in binary = 11111111**
All bits are **1** → those are **network bits** → fixed, unchangeable.

### Why does **0** mean “this octet *can* change”?

Because **0 in binary = 00000000**
All bits are **0** → host bits → available to number individual hosts.

---

# 🔢 3. Converting Subnet Mask to Binary

Example: `255` → binary
Subtract powers of two:

* 255 − 128 → 127
* 127 − 64 → 63
* 63 − 32 → 31
* 31 − 16 → 15
* 15 − 8 → 7
* 7 − 4 → 3
* 3 − 2 → 1
* 1 − 1 → 0

Result:
`11111111`

So the subnet mask:

```
255.255.255.0
```

Binary:

```
11111111.11111111.11111111.00000000
```

---

# 🧩 4. What the 1s and 0s *Mean*

Binary subnet mask:

* **1s = Network bits**
  → identify *which network* the IP belongs to
  → network portion cannot change

* **0s = Host bits**
  → identify *individual devices*
  → host portion can change

Example:

```
11111111.11111111.11111111.00000000
Network | Network | Network | Host
```

Means:

* First 3 octets = *network* (won’t change)
* Last octet = *hosts* (can vary)

---

# 🧮 5. Counting Hosts Using Binary

Host count depends on how many **0s** are in the binary subnet mask.

### Formula:

```
Hosts = 2^(number of host bits) - 2
```

Subtract 2 for:

* Network address
* Broadcast address

---

# 📌 Example: 255.255.255.0 (a /24)

Binary:
`11111111.11111111.11111111.00000000`

Zeros = 8 → host bits = 8

```
2^8 = 256
256 - 2 = 254 usable hosts
```

This matches what we know: **/24 → 254 hosts**

---

# 🔧 6. Increasing Hosts by “Stealing” Bits

If you need more than 254 hosts (e.g., you want 500), you must:

✔ Add more **zeros** (host bits)
✔ Remove some **ones** (network bits)

Example change:

Original (binary):

```
11111111.11111111.11111111.00000000
```

Change last network bit to 0:

```
11111111.11111111.11111110.00000000
```

Zeros = now **9** (instead of 8)

```
2^9 = 512 addresses
512 - 2 = 510 usable hosts
```

---

# 🔄 7. Converting the Modified Subnet Mask Back to Decimal

Binary for the third octet:

`11111110`

Add its powers of two:

```
128 + 64 + 32 + 16 + 8 + 4 + 2 = 254
```

So the new mask becomes:

```
255.255.254.0
```

This subnet mask supports:

* **510 usable hosts**
* **512 total addresses**

You just performed *real subnetting*.

---

# 🔐 8. Rule of Subnet Masks: **They Are Always Contiguous**

Subnet mask binary must always be:

* All 1s in a row
* Followed by all 0s in a row
* Never mixed

Valid:

```
11111111 11111111 11110000 00000000
```

Invalid:

```
11111111 11110111 00000000 00000000
      wrong →      ↑ hole inside the 1s
```

This ensures masks are readable and compatible with routing.

---

# 🧠 9. What We Learned (Short Flash Summary)

* `255` = `11111111` → all network bits
* `0`   = `00000000` → all host bits
* Host count = `2^(# of zeros) - 2`
* More zeros = more hosts
* More ones = more networks
* Changing the subnet mask **is** subnetting
* Subnet masks must be contiguous

---


# 🧠 Subnetting a Network

### “Breaking One Network into Four Using Subnetting”

---

# 🌐 1. Why We Subnet

Your home network has one big subnet — insecure + messy.
Goal: **split it into 4 isolated networks** (IoT, Wireless, DMZ, Users).

Instead of using multiple routers, VLANs, or lazy default network additions,
**we subnet the existing network into smaller networks**.

Subnetting lets you:

* Increase security
* Segment devices by purpose
* Control broadcast domains
* Organize your network properly

---

# 🧩 2. The Subnet Mask Tells You *Everything*

Subnet mask in decimal → boring
Subnet mask in **binary** → *reveals the truth*

Example mask (from video):

```
255.255.255.0
```

Binary:

```
11111111.11111111.11111111.00000000
```

Meaning:

* **1s = Network bits** (fixed)
* **0s = Host bits** (variable)

Hosts come from the **zeros**.

---

# 🔥 3. Mission: Turn 1 Network → 4 Networks

To create more networks, we need **more network bits**.

How do we get more network bits?
👉 We **steal (borrow) host bits**

> “When you need more networks, you need more bits.”

---

# 🔢 4. Use the NoraTwo Chart (2ⁿ) to Determine Bit Borrowing

Goal: create **4 networks**.

Use powers of 2:

```
1 → 2 → 4 → 8 → 16 → …
```

* To get at least **4 networks**, we need `2^2 = 4`.
* So we must steal **2 host bits**.

**Borrowed bits = number of bits required to reach desired network count**

Examples:

* Need **4 networks** → 2 bits
* Need **17 networks** → next power of 2 is 32 → 5 bits

---

# 🖤 5. Modify the Mask (Flip Bits to the “Dark Side”)

Original mask:

```
11111111.11111111.11111111.00000000
```

Borrow 2 bits → flip first 2 host bits to 1:

```
11111111.11111111.11111111.11000000
```

Now the mask is:

### **Binary mask**

```
11111111.11111111.11111111.11000000
```

### **Decimal mask**

Add the first two powers in last octet:
`128 + 64 = 192`

So new subnet mask:

```
255.255.255.192
```

### **CIDR notation**

Count network bits:

```
8 + 8 + 8 + 2 = 26 bits
```

New mask = **/26**

---

# 🚀 6. /26 Means Four Networks

/24 → /26 steals **2 bits**, giving:

* 2² = **4 subnets**
* Host bits left = 6
* Hosts → `2^6 = 64 total`, minus 2 →
  ➡️ **62 usable hosts per subnet**

---

# 📏 7. Finding the Increment

Increment = value of the **last network bit**.

Last network bit value (in the borrowed range) = **64**.

Thus each network increases by **64**.

---

# 📦 8. Build the Four Networks

Network 1:

```
192.168.1.0     – 192.168.1.63
```

Network 2:

```
192.168.1.64    – 192.168.1.127
```

Network 3:

```
192.168.1.128   – 192.168.1.191
```

Network 4:

```
192.168.1.192   – 192.168.1.255
```

All have mask:

```
255.255.255.192  (/26)
62 usable hosts each
```

---

# 🔍 9. Host Count Formula (Review)

Count host bits:
`6`

Formula:

```
Hosts = 2^(host bits) – 2
Hosts = 2^6 – 2 = 62 usable
```

---

# 🧠 10. The Four-Step Universal Subnetting Method

Works for ANY address class (A/B/C):

### **1. Convert the subnet mask to binary.**

Find network bits & host bits.

### **2. Determine number of required networks.**

Use powers of 2 to find needed borrowed bits.

### **3. Borrow bits → modify mask → convert back to decimal.**

### **4. Use increment to build subnets.**

This ALWAYS works.

---

# 📚 EXTRA MATERIALS

(added per your request)

---

# 📘 CIDR Quick Reference Chart (/8 → /32)

### **CIDR to Subnet Mask Table**

| CIDR | Subnet Mask     | Host Bits | Usable Hosts       |
| ---- | --------------- | --------- | ------------------ |
| /8   | 255.0.0.0       | 24        | 16,777,214         |
| /9   | 255.128.0.0     | 23        | 8,388,606          |
| /10  | 255.192.0.0     | 22        | 4,194,302          |
| /11  | 255.224.0.0     | 21        | 2,097,150          |
| /12  | 255.240.0.0     | 20        | 1,048,574          |
| /13  | 255.248.0.0     | 19        | 524,286            |
| /14  | 255.252.0.0     | 18        | 262,142            |
| /15  | 255.254.0.0     | 17        | 131,070            |
| /16  | 255.255.0.0     | 16        | 65,534             |
| /17  | 255.255.128.0   | 15        | 32,766             |
| /18  | 255.255.192.0   | 14        | 16,382             |
| /19  | 255.255.224.0   | 13        | 8,190              |
| /20  | 255.255.240.0   | 12        | 4,094              |
| /21  | 255.255.248.0   | 11        | 2,046              |
| /22  | 255.255.252.0   | 10        | 1,022              |
| /23  | 255.255.254.0   | 9         | 510                |
| /24  | 255.255.255.0   | 8         | 254                |
| /25  | 255.255.255.128 | 7         | 126                |
| /26  | 255.255.255.192 | 6         | 62                 |
| /27  | 255.255.255.224 | 5         | 30                 |
| /28  | 255.255.255.240 | 4         | 14                 |
| /29  | 255.255.255.248 | 3         | 6                  |
| /30  | 255.255.255.252 | 2         | 2                  |
| /31  | 255.255.255.254 | 1         | 0 (special cases)  |
| /32  | 255.255.255.255 | 0         | 1 host (single IP) |

Here’s an updated version of your table with an added column for IP Range and another for the Increment (size of each subnet):

| CIDR | Subnet Mask     | Host Bits | Usable Hosts      | IP Range                  | Increment (Size) |
| ---- | --------------- | --------- | ----------------- | ------------------------- | ---------------- |
| /8   | 255.0.0.0       | 24        | 16,777,214        | 0.0.0.0 - 255.255.255.255 | 16,777,216       |
| /9   | 255.128.0.0     | 23        | 8,388,606         | 0.0.0.0 - 127.255.255.255 | 8,388,608        |
| /10  | 255.192.0.0     | 22        | 4,194,302         | 0.0.0.0 - 63.255.255.255  | 4,194,304        |
| /11  | 255.224.0.0     | 21        | 2,097,150         | 0.0.0.0 - 31.255.255.255  | 2,097,152        |
| /12  | 255.240.0.0     | 20        | 1,048,574         | 0.0.0.0 - 15.255.255.255  | 1,048,576        |
| /13  | 255.248.0.0     | 19        | 524,286           | 0.0.0.0 - 7.255.255.255   | 524,288          |
| /14  | 255.252.0.0     | 18        | 262,142           | 0.0.0.0 - 3.255.255.255   | 262,144          |
| /15  | 255.254.0.0     | 17        | 131,070           | 0.0.0.0 - 1.255.255.255   | 131,072          |
| /16  | 255.255.0.0     | 16        | 65,534            | 0.0.0.0 - 0.255.255.255   | 65,536           |
| /17  | 255.255.128.0   | 15        | 32,766            | 0.0.0.0 - 0.127.255.255   | 32,768           |
| /18  | 255.255.192.0   | 14        | 16,382            | 0.0.0.0 - 0.63.255.255    | 16,384           |
| /19  | 255.255.224.0   | 13        | 8,190             | 0.0.0.0 - 0.31.255.255    | 8,192            |
| /20  | 255.255.240.0   | 12        | 4,094             | 0.0.0.0 - 0.15.255.255    | 4,096            |
| /21  | 255.255.248.0   | 11        | 2,046             | 0.0.0.0 - 0.7.255.255     | 2,048            |
| /22  | 255.255.252.0   | 10        | 1,022             | 0.0.0.0 - 0.3.255.255     | 1,024            |
| /23  | 255.255.254.0   | 9         | 510               | 0.0.0.0 - 0.1.255.255     | 512              |
| /24  | 255.255.255.0   | 8         | 254               | 0.0.0.0 - 0.0.255.255     | 256              |
| /25  | 255.255.255.128 | 7         | 126               | 0.0.0.0 - 0.0.127.255     | 128              |
| /26  | 255.255.255.192 | 6         | 62                | 0.0.0.0 - 0.0.63.255      | 64               |
| /27  | 255.255.255.224 | 5         | 30                | 0.0.0.0 - 0.0.31.255      | 32               |
| /28  | 255.255.255.240 | 4         | 14                | 0.0.0.0 - 0.0.15.255      | 16               |
| /29  | 255.255.255.248 | 3         | 6                 | 0.0.0.0 - 0.0.7.255       | 8                |
| /30  | 255.255.255.252 | 2         | 2                 | 0.0.0.0 - 0.0.3.255       | 4                |
| /31  | 255.255.255.254 | 1         | 0 (special cases) | 0.0.0.0 - 0.0.1.255       | 2                |
| /32  | 255.255.255.255 | 0         | 1 host            | Single IP (no range)      | 1                |

* **Increment** represents how many IP addresses are in each subnet.
* **IP Range** shows the range of addresses available within the subnet.

---

# 🔍 Visual: Network Bits vs Host Bits

Example: /26

```
11111111.11111111.11111111.11000000
|------- Network (26 bits) -------|-- Hosts (6 bits) --|
```

General rule:

```
[Network Bits = 1s][Host Bits = 0s]
```

Easy memory trick:

* **More 1s = more networks, fewer hosts**
* **More 0s = fewer networks, more hosts**

---

# 🔧 Visual: Borrowing Host Bits

Start (/24):

```
11111111.11111111.11111111.00000000
```

Borrow 2 bits:

```
11111111.11111111.11111111.11000000
```

Hosts shrunk from 256 → 64.

---

# 📐 Quick Increment Table

For the last octet:

| New Mask | Binary | Increment |
| -------- | ------ | --------- |
| /25      | 128    | 128       |
| /26      | 192    | 64        |
| /27      | 224    | 32        |
| /28      | 240    | 16        |
| /29      | 248    | 8         |
| /30      | 252    | 4         |
| /31      | 254    | 2         |
| /32      | 255    | 1         |

---

# 👨‍🏫 Extra: How to Subnet *Any Network* in Under 30 Seconds

### 1. Identify original mask

### 2. Determine needed networks

### 3. Borrow bits (power of 2 rule)

### 4. Convert mask back to decimal

### 5. Increment = value of borrowed bit

### 6. Build ranges

Done.

---

# 🌟 How to get the Five-Network Homework from Chuck?

</details>

## VIM (Vi Improved)

<details>
<summary>View contents</summary>

> Vim is a programmer's text editor.

### VIM modes

- insert mode: text editing (`i`)
- command mode: primary mode (`ESC`)
- last line/command mode: searching, saving, exiting (`:`)
- visual mode: select texts (`v`)

### Command Mode

- This is the **default** mode
- Editing the text is not possible
- Navigate, Search, Delete, Undo etc.

### Insert Mode

- Allows to enter text

### Common Commands

- Open/Create a file using vim: `vi test.txt`
- Quit vim without saving changes: `:q!`
- Quit vim with saving changes: `:wq`
- `dd` - Delete a line
- `d10d` - Delete 10 lines
- `u` - Undo
- `CTRL + r` - Redo
- `$` - Jump to end of the line
- `A` - Jump to end of the line and switch to insert mode
- `0` - Jump to start of the line
- `I` - Jump to start of the line and switch to insert mode
- `10G` - Go to line 10

### Search Commands

- `/pattern` - Search for pattern
- `n` - Jump to next match
- `N` - Search in opposite direction

### Replace Commands

- `:%s/old/new` - Replace old with new throughout the file
- `:%s/old/new/g`
- `:6,10s/old/new/g`

```
% => run this command on all lines.
6,10 => run this command on line 6 and 10
g => match multiple occurences in the same line.
```

Resources

- [Vi Commands Cheat Sheet](https://linuxmoz.com/vi-commands-cheat-sheet/)
- [Vim Copy, cut and paste](https://vim.fandom.com/wiki/Copy,_cut_and_paste)

</details>

## Server

<details>
<summary>View contents</summary>

A server is a computer or system that provides resources, data, services, or programs to other computers, known as clients, over a network. In theory, whenever computers share resources with client machines they are considered servers. This means that a device could be both a server and a client at the same time.

Simple server with node.js

```js
const http = require("http");
const PORT = 8080;

http
  .createServer((req, res) => {
    res.write("Hello, World!");
    res.end();
  })
  .listen(PORT);

console.log(`Server started! Listening on port ${PORT}`);
```

> Generally ports below 1000 are reserved.

The internet runs over port 80 on HTTP server and port 443 on HTTPS server.

Usually 127.0.0.1 is a loopback command. That means instead of going out to the internet and hitting a server on port 8080, it hits the localhost running on port 8080.

### Data Centers

Servers generally live in a place called data centers. It's the collection of the stack of servers.

### The Cloud

Cloud computing is the on-demand availability of computer system resources, especially data storage (cloud storage) and computing power, without direct active management by the user. Large clouds often have functions distributed over multiple locations, each location being a data center.

### Elastic Computing or Cloud Elasticity

Elastic computing is the ability to quickly expand or decrease computer processing, memory and storage resources to meet changing demands without worrying about capacity planning and engineering for peak usage.

### VPS (Virtual Private Server)

A virtual private server (VPS) is a virtual machine sold as a service by an Internet hosting service.

</details>

## Operating Systems (OS)

<details>
<summary>View contents</summary>

An operating system (OS) is system software that manages computer hardware, software resources, and provides common services for computer programs. Operating systems are found on many devices that contain a computer – from cellular phones and video game consoles to web servers and supercomputers.

### Two main types of server operating systems

```txt
1. windows
2. unix ->
i. BSD -> freeBSD -> OSX/MacOS
ii. linux (ubuntu, debian, red hat)
iii. solaris
```

</details>

## SSH (Secure Shell or Secure Socket Shell)

<details>
<summary>View contents</summary>

- HTTP (Hypertext Transfer Protocol): It allows to send files over the internet like HTML, CSS and Javascript files between browsers and servers.
- FTP (File Transfer Protocol): It allows to send computer files from a server to a client on a computer network.
- HTTPS: It is similar to HTTP but it transfers encrypted files.
- IMAP: It allows to send e-mails.

Secure Shell is a cryptographic network protocol for operating network services securely over an unsecured network. Typical applications include remote command-line, login, and remote command execution, but any network service can be secured with SSH.

SSH provides a secure channel over an unsecured network by using a client–server architecture, connecting an SSH client application with an SSH server. The protocol specification distinguishes between two major versions, referred to as SSH-1 and SSH-2.

```txt
# Key pair

my computer    --------------->   server
(private key)  encrypted message  (public key)
(secrete)      <---------------
```

A **public key** that is copied to the SSH server(s). Anyone with a copy of the public key can encrypt data which can then only be read by the person who holds the corresponding **private key**. Once an SSH server receives a public key from a user and considers the key trustworthy.

Encryption Methods:

- Symmetrical Encryption
- Asymmetrical Encryption
- Hashing

Create a ssh key:

```bash
> cd ~/.ssh
> ssh-keygen # generate ssh key
```

### HTTPS vs SSH

SSH and HTTPS are both protocols for securely transmitting data over the internet, but they serve different purposes and operate at different levels of the networking stack.

SSH (Secure Shell) is a protocol for establishing a secure, encrypted connection between two computers. It is primarily used for remote access and command-line management of servers and other computing systems. SSH provides a secure channel over an unsecured network, such as the internet, allowing users to securely log in to remote systems, execute commands, and transfer files.

HTTPS (Hypertext Transfer Protocol Secure) is a protocol for securely transmitting data over the World Wide Web. It is used to encrypt data exchanged between a web server and a client, such as a web browser. HTTPS is designed to protect sensitive information, such as login credentials, credit card details, and other personal information, from being intercepted and viewed by unauthorized parties.

The main difference between SSH and HTTPS is their intended use and the type of data they protect. SSH is used for secure remote access to computing systems, while HTTPS is used for secure web browsing and transmitting sensitive data over the internet. Additionally, SSH operates at the transport layer of the networking stack, while HTTPS operates at the application layer.

Overall, both SSH and HTTPS are important protocols for securing data transmitted over the internet and protecting against unauthorized access and interception.

- [source](https://www.quora.com/What-is-the-difference-between-SSH-and-HTTPS)

### Connecting to the server

```bash
# username by default is root
# ssh {user}@{host}
# host -> IP Address or Domain Name
ssh root@SERVER_IP

# first time connecting to the server
ssh -i keyName root@SERVER_IP # ssh -i fsbc root@165.22.140.238

# Generate public/private rsa key pair
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
# Enter: /Users/{username}/.ssh/id_rsa_{keyName}

# Copy public key
pbcopy < ~/.ssh/id_rsa_github.pub
# To connect with server paste the public key, e.g. github

# Add identity
ssh-add ~/.ssh/id_rsa_github
```

</details>
