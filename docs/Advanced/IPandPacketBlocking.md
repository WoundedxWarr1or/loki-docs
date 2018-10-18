# IP and Packet Blocking

Although the [Service Node](../ServiceNodes/SNOverview.md) network has no central points of failure, two significant censorship threats face the network; namely [harvesting attacks](https://geti2p.net/en/docs/how/threat-model#harvesting) and [deep packet inspection](http://tec.gov.in/pdf/Studypaper/White%20paper%20on%20DPI.pdf). Harvesting attacks would seek to gather the IP addresses of all operating Service Nodes on the network and use ISP level firewalls to block connections to those particular addresses. This type of censorship is regularly [performed on the Tor network in China](https://arxiv.org/abs/1204.0447). Deep packet inspection (DPI), aims to investigate the structuring of each individual packet that passes through a firewall, and selectively drop or block packets that appear to relate to a particular service. Again, DPI has been used extensively by state-level actors.

Much work has been done to design systems which evade DPI. Users can leverage types of pluggable transports which alter the signature of each packet aiming to appear as normal unblocked traffic. IP blocking is generally avoided by running domain fronting bridges which will encrypt traffic as HTTPS requests to unblocked services like Azure or Cloudflare. Once they reach the unblocked service, the bridge will forward the request to the desired location. In the case of domain fronting, it becomes difficult for a state level actor to prevent the flow of all traffic to popular bridges without causing significant disruption to the general usage of the internet.

[Governance](../About/Governance.md) mechanisms built into Loki can be used to operate domain fronting bridges so that users can access Loki services in countries where large-scale internet censorship policies are at play. Additionally, [OBFS4](https://github.com/Yawning/obfs4) pluggable transport support will be bundled with the Service Node release of the Loki wallet to help further protect against DPI.