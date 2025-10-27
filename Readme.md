Wireshark Network Capture and Analysis Report

 Objective

To perform live network packet capture using Wireshark in Kali Linux, identify different network protocols in use, and analyze their communication patterns.

---

 Procedure

1. **Installed Wireshark** using:

   ```bash
   sudo apt install wireshark
   ```
2. **Started capture** on the active interface (`eth0`) using:

   ```bash
   sudo wireshark
   ```
3. **Generated network traffic** by browsing websites and pinging servers.
4. **Stopped capture** after one minute and saved the file as `capture_kali.pcapng` in `/home/kali/`.
5. **Filtered and analyzed packets** using the following commands:

   ```bash
   tshark -r /home/kali/capture_kali.pcapng -z io,phs -q
   tshark -r /home/kali/capture_kali.pcapng -Y "tcp"
   tshark -r /home/kali/capture_kali.pcapng -Y "dns"
   tshark -r /home/kali/capture_kali.pcapng -Y "icmp"
   ```

---

 Observations

* **Total Packets Captured:** 119
* **Capture Duration:** ~1 minute
* **File Type:** `.pcapng` (Wireshark Capture File)
* **Protocols Detected:**

  * **TCP** – Reliable transport layer protocol (Port 443)
  * **DNS** – Domain Name System lookups (UDP Port 53)
  * **TLSv1.2** – Encrypted HTTPS traffic
  * **ICMPv6** – IPv6 network discovery and ping
  * **ARP & QUIC** – Link-layer resolution and modern encrypted transport

---

 Findings

* The system communicates over both **IPv4** and **IPv6**.
* **TLSv1.2** and **QUIC** indicate encrypted HTTPS sessions.
* **DNS** queries to Mozilla and Google servers confirm active browsing.
* No suspicious packets were observed — traffic represents normal web usage.

---

 Conclusion

The Wireshark capture successfully demonstrated packet-level analysis of real-time network communication. Multiple protocols were identified, including DNS, TCP, TLSv1.2, ICMPv6, and QUIC. The analysis confirmed typical web browsing activity and showed how secure connections are established through encryption layers.

