---
marp: true
theme: graph_paper
footer: ACIT 2620 Principles of Enterprise Networking
author: Yves Rene Shema
---

<style scoped>
  h1, h2, p, footer {
    color: white
  }

  div.banner {
    padding: 1em;
    background: rgb(0, 0, 0, .6);
  }
</style>

![bg](../img/networking.jpg)

<div class="banner">

# ACIT 2620

## Principles of Enterprise Networking

By: Yves Rene Shema

</div>

---

## Domain Name System (DNS)

- allow users to locate services by DNS name rather than having to remember IP addresses
- hierarchical name system
- distributed database
  - each domain responsible for maintaining its own DNS servers (nowadays most domain registrars provide DNS services for their customers)
- allow changing server's IP address without requiring users to know about it.

---

## Top Level Domains (TLDs)

- assigned by ICANN
- 7 original gTLD: **.com**, **.net**, **.org**, **.int**, **.edu**, **.mil**, **.gov**
- country-code domains: **.us**, **.ca**, **.it**, ...
- new generic TLDS (gTLD): **.biz**, **.info**, ...
  - anyone can apply for for a subdomain

---

## Stakeholders

* **registrant**: takes ownership of a domain by claiming the domain through a registrar
* **registrar**: leasing domain names (on yearly basis) and inserting the names in global DNS (delegation). 
  * Create NS record for the domain in the TLD of the new name with the relevant registry operator

---

## Stakeholders

* **registry**: databases of DNS names under TLDs. Each registry is operated by a different organization (e.g. **.com** is operated by VeriSign)
* **ICANN**: oversees all the above. Also oversees the internet root zone ('.') (a..m.**root-servers.net**). 
  * Grants accreditation to registrars (the latter pay fees to ICANN which go towards the operation of ICANN itself)
  
---

## Zones

- independently managed subtree of the DNS tree
- has own root DNS that is the suffix of every DNS name in the zone.
- though multiple levels are possible, many zones tend to define only one additional level and create subzones for deeper levels
- each zone has its own authoritative nameservers charged with maintaining zone records
  - must have at least 2 nameservers for  redundancy

---

- a single nameserver can manage multiple unrelated zones (e.g. domain registrars)
- root zone (root of the DNS tree, represented by DNS name that is the empty string) is managed by root nameservers
  - contain only NS records for the immediate subzones or TLDs (**.com**, **.net**, ...)
  - 13 root nameservers widely distributed
  - **a.root-servers.net** to **m.root-servers.net** (each corresponding to a cluster of servers)

---

## Registration

- registrant choose a domain name and creates zone for it
- claim domain with a registrar
  - registrar inserts domain in global DNS through delegation
- domain added to TLD registry
- registrant create records under the zone

---

## DNS records

- generically called Resource Records (RR)
  - **A**: maps domain name to IPv4 addresses
  - **AAAA**: maps domain name to IPv6 addresses
  - **NS**: name servers for sub zones

---

- **CNAME**: canonical name or alias. 
  - Allows multiple domain names to point to the same physical machine, thus requiring only a single A record.
- **PTR**: reverse DNS 
- **MX**: Mail eXchange 
  - maps domain name to a mail server that accepts email on behalf of the domain. 
  - Thus, one domain name is able to represent both a web server (with a different IP address) and an email server.
- **TXT**: arbitrary text strings
  - often used for verification (e.g. SPF: Sender Policy Framework which protects agains spam)

---

## Nameserver

- answers queries for names defined under a zone
- authoritative
- each zone has one or more associated nameservers

---

## DNS resolver a.k.a recursive nameserver

- often provided by service providers (your ISP or your company)
- recursively forwards DNS queries to nameservers on the user's behalf
- caches queries for quick subsequent retrieval

---

## Stub resolver

- runs on the client
- forwards DNS queries to DNS resolvers configured for the client
- also caches queries for quick retrieval

---

## creating sub-domain zone AWS

- delegation: creating a separate hosted zone for a subdomain
  - create a hosted zone with the same name as the subdomain (type: public hosted zone)
  - using the name servers provided for the new hosted zone, create NS record in parent zone
    - the name of the NS record must be the same as the name of the subdomain
  - create records in subdomain hosted zone