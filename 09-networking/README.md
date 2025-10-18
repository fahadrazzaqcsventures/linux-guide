# Linux Networking Commands (Simplified)

Networking in Linux is all about checking connections, managing interfaces, and transferring data between systems.  
Here are some **essential commands** you’ll use to test and troubleshoot network connectivity.

## 1. `ping` — Test Network Connectivity

Sends packets to a remote host to check if it’s reachable.

```bash
ping google.com
```

**What it does:**

- Verifies if the system can reach the target host.  
- Measures response time (latency).  

**Tip:**

Use `Ctrl + C` to stop the ping.  
You can also limit the count:

```bash
ping -c 4 google.com
```

---

## 🌐 2. `ifconfig` — Show Network Interface Info *(deprecated)*

Displays IP addresses, MAC addresses, and network status.

```bash
ifconfig
```

**Note:**

`ifconfig` is old and may not be installed by default.  
Modern systems use the `ip` command instead.

## 3. `ip a` — Show IP Addresses and Interfaces

Displays all network interfaces and their assigned IPs.

```bash
ip a
```

**Common uses:**

- Check which interface (like `eth0` or `wlan0`) is active.  
- View assigned IP addresses.  

**Tip:**  
To view only active interfaces:

```bash
ip -brief address show up
```

## 4. `netstat -tulnp` — List Network Connections

Shows all open network sockets, including TCP and UDP ports.

```bash
netstat -tulnp
```

**Options Explained:**

- `t` – TCP connections  
- `u` – UDP connections  
- `l` – Listening ports  
- `n` – Show numeric addresses instead of names  
- `p` – Show process IDs and names  

**Modern Alternative:**

`ss -tulnp` (faster and more detailed)

## 5. `curl` — Fetch Web Content

Retrieves data or web pages from a URL.

```bash
curl https://example.com
```

**What it does:**

- Displays webpage content in the terminal.  
- Useful for testing APIs or downloading small files.  

**Examples:**

```bash
curl -I https://google.com   # Show only HTTP headers
curl -O https://example.com/file.zip   # Save file with same name
```

## 6. `wget` — Download Files from the Internet

Downloads files directly from a URL.

```bash
wget https://example.com/file.zip
```

**Features:**

- Can resume interrupted downloads.  
- Saves files to the current directory.  

**Examples:**

```bash
wget -c https://example.com/file.zip   # Continue a stopped download
wget -r https://example.com            # Download an entire website recursively
```

## Quick Reference Table

| **Command** | **Purpose** | **Example** |
|--------------|-------------|-------------|
| `ping` | Test network connectivity | `ping -c 4 google.com` |
| `ifconfig` | Show network interface info (deprecated) | `ifconfig eth0` |
| `ip a` | Display IP addresses | `ip a` |
| `netstat -tulnp` | View active connections and ports | `netstat -tulnp` |
| `curl` | Fetch a web page or API response | `curl -I https://google.com` |
| `wget` | Download files from the web | `wget https://example.com/file.zip` |

## Summary

> Linux networking tools help you **check connectivity**, **inspect interfaces**, and **download data** directly from the terminal.  
> Remember: `ip` and `ss` are modern replacements for older commands like `ifconfig` and `netstat`.
