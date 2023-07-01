# nocer

Nocer aims to automate the recon data collection for a given target. It will do this using existing open-source tools bound together by a simple data backend (SQLite) + some cherries on top of my own.

## TODOs
- [ ] Integrate `subfinder` for fast subdomain enumeration
- [ ] Integrate `rengine` to generate alterations based on the patterns followed by the names found by `subfinder`
- [ ] Gather DNS data on all the subdomains resulted above. For each subdomain we are interested in:
  - [ ] A/AAAA/CNAME record. If it doesn't exist, I'd like to differentiate between `NXDOMAIN`, which indicates an invalid name, and `NOERROR` which indicates there's no record for this name, but there are valid names below it in the zone tree.
  - [ ] MX/TXT/NS records
- [ ] For all the subdomains in the database that have an A/AAAA/CNAME record, scan for open ports:
  - [ ] Start with the top 100 ports defined by nmap
  - [ ] Design a solution for port scanning: all 65k ports on 100s(for now) of hosts. `zmap` seems to be the state of the art for larger scale single-port scanning. Can I write a `zmap` module to scan all the ports? Are there other solutions (maybe a typical port-scanner + `ziterate`)?
- [ ] Find web servers among the open ports. _Hash part of the response to compare it to future responses_.
