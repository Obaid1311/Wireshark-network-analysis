Network Traffic Analysis using Wireshark(SOC Analyst Project)

Overview:

This project focuses on analyzing network traffic using Wireshark to identify protocols, inspect packet-level data, and evaluate potential security risks from a SOC analyst perspective. The analysis includes DNS queries, HTTP communication, and TCP session behavior.

Tools Used:

- Wireshark (Network Protocol Analyzer)

Network Details:

- Internal IP Address: 10.148.70.224
- External IP Addresses Observed:
  - 184.84.221.x (Content Delivery Network servers)
  - 142.250.x.x (Google infrastructure)

Analysis Performed:

1. DNS Traffic Analysis:

- Observed DNS queries for:
  - www.youtube.com
  - googlevideo.com
- Identified CNAME records and multiple IP resolutions indicating CDN usage and load balancing.

2. HTTP Traffic Analysis:

- Captured HTTP GET requests for file/stream data.
- Observed response:
  - HTTP/1.1 206 Partial Content (indicates streaming or partial download)

Security Observation:
HTTP traffic is unencrypted and can be intercepted by attackers.

3. TCP Analysis:

- Observed TCP flags:
  - ACK
  - PSH, ACK
- Verified normal TCP session establishment and data transfer behavior.

4. Packet Inspection:

- Packet size observed around ~1500 bytes (standard MTU).
- TCP stream reassembly confirms large data transfer across multiple packets.

Security Findings:

Finding| Severity| Description
Unencrypted HTTP Traffic| Medium| Data transmission is not secure
External Connections| Low| Normal CDN and Google communication
No Malicious Domains| Low| Legitimate DNS queries observed
Normal TCP Behavior| Informational| No anomalies detected

Recommendations:

- Use HTTPS instead of HTTP for secure communication
- Implement IDS/IPS for network monitoring
- Enable DNS logging and monitoring
- Use threat intelligence tools for domain validation

Screenshots:

DNS Analysis:

"DNS" (screenshots/dns.png)

Overview:

"Overview" (screenshots/overview.png)

TCP Analysis:

"TCP" (screenshots/tcp.png)

HTTP Analysis:

"HTTP" (screenshots/http.png)

Project Structure:

wireshark-network-analysis/
│
├── README.md
├── pcap/
│   └── capture.pcapng
├── screenshots/
│   ├── dns.png
│   ├── overview.png
│   ├── tcp.png
│   └── http.png
├── report/
│   └── soc_analysis_report.pdf
└── notes/
└── analysis.txt

Skills Demonstrated:

- Network Traffic Analysis
- Packet Inspection
- Protocol Analysis (DNS, HTTP, TCP)
- SOC Analyst Investigation Techniques
- Cybersecurity Fundamentals

Conclusion:

The captured traffic represents normal user activity such as web browsing, video streaming, and DNS resolution. No suspicious or malicious behavior was identified during the analysis.
