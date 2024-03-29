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
