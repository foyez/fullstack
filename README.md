# Full-stack

- Full stack developer - who can develop on **client (HTML, CSS, Javascript, React, etc.)**, **server (Node, Golang, PHP, etc.)** and **Database (SQL (MySql, Postgres), NoSql (MongoDB), etc.)** software

## Command Line

- **cd** - change directory
- **ls** - list directory contents
- **pwd** - print working directory
- **mkdir** - make directory
- **rmdir** - remove directory

- **cat** - show file contents
- **man** - command manual
- **less** - show file contents by page
- **rm** - remove file
- **echo** - repeat input
- **cp** - copy files and directories
- **mv** - move (rename) files

#### Shells - allow to run command lines

Example: bash, zsh, fish, etc.

```bash
> echo $0 # show current shell
```

#### Terminal - runs shell applications

Example: iTerm2, hyper, Powershell, etc.

```
SHELL --> TERMINAL --> KERNEL
```

Kernel is the core of the operating system. It talks to the actual machine layer.

## How does the internet work?

- **Internet (International Network)** - A system of globally interconnected devices
- **Intranet (Internal Restricted Access Network)** - Private internet, e.g., vpn
- **VPN (Virtual Private Network)** - a intranet, which is just a private internet of different servers talking to each other (e.g. LAN), but it's inaccessible from the outside.
- **LAN (Local Area Network)** - confined to one building or site. It's smaller than a WAN. Often a LAN is a private network to an organization or business.
- **WAN (Wide Area Network)** - extends over a large area. A WAN is created by connecting lots of other LANs together.
- **IP (Internet Protocol)** - a set of rules. For example, how to accept (read, write or send back) a well form data
- **IP Address** - A label assigned to an internet connected device

```
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

```
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

## VIM (Vi Improved)

> Vim is a programmer's text editor.

#### VIM modes

- insert mode: text editing (`i`)
- command mode: primary mode (`ESC`)
- last line mode: searching, saving, exiting (`:`)

#### Commands

- Open/Create a file using vim: `vi test.txt`
- Quit vim without saving changes: `:q!`
- Quit vim with saving changes: `:wq`

- [Vi Commands Cheat Sheet](https://linuxmoz.com/vi-commands-cheat-sheet/)
- [Vim Copy, cut and paste](https://vim.fandom.com/wiki/Copy,_cut_and_paste)
