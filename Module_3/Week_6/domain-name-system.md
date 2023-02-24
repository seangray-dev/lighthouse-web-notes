# DNS

DNS stands for Domain Name Sytem, which is a system used on the internet to translate domain names (such as www.example.com) into IP addresses (such as 192.0.2.1).

Every device connected to the internet has a unique IP address, which is used to identify and communicate with that device. However, remembering IP addresses for all websites would be impractical, so DNS was devleoped as a way to associate human-readable domain names with their corresponding IP addresses.

In the DNS system, there are several types of name servers that work together to resolve domain names into IP addresses:

1. Root Name Servers: These are the highest level of name servers in the DNS system. There are 13 root name servers located around the world, and they are responsible for maintaining information about top-level domains (TLDs) such as .com, .org, and .net.

2. TLD Name Servers: These name servers are responsible for maintaining information about a particular top-level domain (TLD). For example, the .com TLD name servers maintain information about all domain names that end in .com.

3. Authoritative Name Servers: These are the name servers that hold the actual information about a specific domain name. When a DNS resolver needs to resolve a domain name, it first contacts the authoritative name server for that domain to obtain the IP address associated with that domain name.

4. Recursive Name Servers: These are the name servers that most end-users interact with. They are responsible for receiving DNS queries from a client, resolving those queries by contacting other name servers as necessary, and returning the results to the client.

When a user enters a domain name into their web browser, the browser sends a DNS query to a recursive name server. The recursive name server then starts the process of resolving the domain name by contacting the root name servers to find the TLD name servers for the domain. The TLD name servers then direct the recursive name server to the authoritative name server for the domain, which finally provides the IP address associated with the domain name. The recursive name server then returns the IP address to the user's web browser, which can then use it to establish a connection to the web server hosting the requested website.

## Record Types

Although there are many available DNS Record Types, there is a small subset that cover most use cases.

- A: most common; map a hostnames to IP address (IPv4, 32-bit address)
- NS: Name Server that is responsible for a DNS zone
- MX: Mail Exchange record specifies where email gets sent to
- CNAME: Canonical Name, an alias for another hostname
- AAAA: similar to A, but uses IPv6, 128-bit address

## DNS Providers

For your reference, common cloud-based DNS providers include (but are not limited to):

- Amazon Route 53
- CloudFlare
- Verisign
- EasyDNS
- Azure DNS
