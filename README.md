### Custom Blue Team Network Monitoring Tool (Mini-IDS)

Ein leichtgewichtiges, Python-basiertes Intrusion Detection System (IDS) zur Live-Überwachung von Netzwerkschnittstellen, Erkennung von Denial-of-Service-Angriffen (DoS) und Identifikation unsicherer Protokolle durch Deep Packet Inspection (DPI). 

Dieses Projekt demonstriert Kernkompetenzen im Bereich des Blue Teaming, der Protokollanalyse (Layer 3/4) und der automatisierten Bedrohungserkennung im SOC-Kontext. 

### Features

* **Volumetrische DoS-Erkennung:** In-Memory-Tracking von Paketraten pro IP-Adresse innerhalb eines gleitenden Zeitfensters zur Identifikation von Traffic-Anomalien.
* **SYN-Flood-Detection:** Überwachung von TCP-Handshake-Flags zur Erkennung halboffener Verbindungsversuche (Anomalie-Erkennung auf Schicht 4).
* **Deep Packet Inspection (DPI):** Filterung von TCP-Payloads nach unverschlüsselten Klartext-Anmeldedaten (Credentials) zur Erkennung von Sicherheitsrisiken (z. B. HTTP-Logins, FTP, Telnet).
* **Ressourceneffizienz:** Verwendung von zustandslosen Sniffing-Methoden (store=False) zur Vermeidung von Speicherüberläufen (RAM) bei hohem Traffic-Aufkommen.

### Anwendung & Vorschau

Das IDS analysiert den Live-Verkehr im Promiscuous Mode. Bei Schwellenwert-Überschreitung werden strukturierte Alerts ausgegeben: 

text

======================================================================
      DANIEL RUL - CUSTOM BLUE TEAM NETWORK MONITORING TOOL      
======================================================================
[1] Aktive Netzwerkschnittstelle: Ethernet
[2] DoS-Schwellenwert: 150 Pakete / 2.0s
[*] Starte Packet Sniffing... Drücke STRG+C zum Beenden.
======================================================================

[ALERT] [DoS Traffic] Hohes Paketaufkommen von IP:
        -> 151 Pakete in den letzten 2.0 Sekunden!
--------------------------------------------------
[WARNING] [Insecure Protocol] Unverschlüsselte Daten von .... -> .....
          Inhalt (Auszug): user=admin pass=secret123
--------------------------------------------------

Verwende Code mit Vorsicht.

### Voraussetzungen & Installation

1. VS Code / Terminal als Administrator starten (erforderlich für den Zugriff auf Sockets im Promiscuous Mode).
2. Npcap (Windows) oder libpcap (Linux) installieren.
3. Abhängigkeiten installieren: 

bash

pip install scapy

Verwende Code mit Vorsicht.
4. Skript ausführen: 

bash

python soc_mini_ids.py

Verwende Code mit Vorsicht.
