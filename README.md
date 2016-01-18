Description
===========
This is meant to be used as a general idea for sending events to elasticsearch using logstash confirguations for:
* TippingPoint IPS
* Bro NSM/IDS files (specifically conn, dns, dhcp, dpd, files, http, kerberos, notice, rdp, ssh, smtp, ssl, x509)
* Windows event logs (sent via nxlog) and also sysmon logs if it is installed
* Juniper SSL VPN logs (note may need to change username regex field a bit, but was extremely useful to visualize where users were logging in from geo map in kibana and also for tracking down users if they were compromised while VPN'ed in)
* Suricata IDS
* FireEye (not parsed but just sent)
* PaloAlto Traffic and Threat logs
* Add GeoIP to all source/destination IPs
* Add AS Name and AS Number to all source/destination IPs (this has been extremely useful for whitelisting/blacklisting/filtering)

Notes
=====
I would tailor this file to your environment and please note I never got around to normalizing all the time stamp fields.

Bro HTTP has additional client headers added such as "X-FLASH-VERSION" as "flash_version", "RANGE" as "content_range", "ACCEPT-LANGUAGE" as "accept_language", "X-REQUESTED-WITH" as "x_requested_with".

As I was a literally a one man security shop, for over a year, its a fairly rough looking file.. However security is not pretty and I had great success using this file to collect pretty much everything I needed for an opensource SIEM.

There are still shops out there with a lot more than 1 person that could not even tell you processes spawned on their servers (whether it is used as a DC or point of sales).

So this file was still a great victory for me despite how f'ed up it might be.