<img width="442" height="423" alt="image" src="https://github.com/user-attachments/assets/37a76b8a-4da6-4c2b-90bd-358ad6299457" />

Servitor  is a **fully automated pentesting recon framework** powered by **GitHub Actions** and **ProjectDiscovery tools**. Three chained pipelines handle **recon**, **adaptive scanning**, and **reporting**.
Automate the low hanging fruit am I right?
Far from finalised, many tuning, much improve, so optimize.



##  Features
- **Full Recon Chain** → Subfinder, DNSx, Naabu, HTTPx, Katana, Wayback
- **Adaptive Vulnerability Scanning** → Nuclei with curated templates + fuzzing
- **Self-Chained Workflows** → Recon → Scan → Report
- **Artifact Management** → Clean structured results after each stage
- **Optional Dashboards** → Hook into GitHub Pages for private reports
- **Extensible** → Add your own tools, templates, or exploit chains

##  Pipelines
| Pipeline | Purpose | Tools |
|----------|---------|-------|
| **1. Deep Recon** | Enumerates subs, resolves DNS, probes hosts, crawls endpoints | `subfinder`, `dnsx`, `naabu`, `httpx`, `katana`, `waybackurls` |
| **2. Adaptive Vulnerability Scanning** | Targets high-priority CVEs + fuzzes endpoints dynamically | `nuclei`, `ffuf`, `dalfox` |
| **3. Reporting** | Consolidates results into Markdown + JSON reports | Built-in |

##  Repository Layout

.
├── domains.txt # Targets (one per line)
├── .github/
│ └── workflows/
│ ├── 1_recon_pipeline.yaml
│ ├── 2_nuclei_scan_pipeline.yaml
│ ├── 3_reporting_pipeline.yaml
└── README.md


##  Quickstart
1. **Add targets** to `domains.txt`:

example.com
targetsite.io
corp.internal


2. **Push to trigger recon**:

git checkout -b recon
git add domains.txt
git commit -m "Launching recon "
git push origin recon

This fires he Recon pipline and stores recon artifacts.

3. **Run vulnerability scanning**:  
- Auto-triggers after recon, or  
- Trigger manually via the Actions tab.

4. **Collect results**:  
- `subdomains_raw.txt` → discovered subs  
- `live_hosts.txt` → resolvable hosts  
- `open_ports.txt` → scanned ports  
- `nuclei_high.json` → vuln findings  
- `REPORT.md` → consolidated report  

##  Tooling Stack
- **Subfinder** → subdomain discovery  
- **DNSx** → DNS resolution / filtering  
- **Naabu** → fast port scanning  
- **HTTPx** → host probing + tech detection  
- **Katana** → endpoint crawler  
- **WaybackURLs** → archive scraping  
- **Nuclei** → vuln scanning (templates)  
- **ffuf** → fuzzing  
- **Dalfox** → XSS/param hunting  

## Disclaimer
This framework is **for authorized security testing only**. You are responsible for what you point it at.  

## Wish List
- Shodan + Censys integration  
- Slack/Discord alert hooks  
- GitHub Pages dashboards  
