# ☁️ AWS FCAJ Daily Learning
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Hugo](https://img.shields.io/badge/Hugo-FF4088?style=flat-square&logo=hugo&logoColor=white)
![Markdown](https://img.shields.io/badge/Markdown-000000?style=flat-square&logo=markdown&logoColor=white)

A **personal learning journal** documenting my AWS journey as a new member of the **FCAJ (FCJ AWS Community)**.  
Built as a **Hugo static site** to serve as a structured workshop-style reference for the Vietnamese AWS community.
> *"I hope it can contribute something to the Vietnamese AWS community and inspire everyone to keep learning."*

---

## ✨ What This Repository Contains

### 🗓️ Weekly Learning Journals
- Daily notes documenting new experiences, challenges, and discoveries at the FCAJ office
- Honest reflections from a first-day intern perspective (50+ people in the office, no team yet, AWS account issues — the real deal)

### 📖 New Terms & Concepts
- **General AWS Terms**: DC, AZ, Region, Edge Locations, CloudFront, WAF, Route 53, Serverless, AWS Budget
- **AWS Virtual Private Cloud (VPC)**: In-depth notes on VPC, Subnets, Route Tables, ENI, EIP, Internet Gateway, NAT Gateway, Security Groups, NACLs, VPC Flow Logs, VPC Peering, Transit Gateway, VPN, Direct Connect, and Elastic Load Balancing (ALB, NLB, CLB, GLB)

### ✅ To-Do Lists
- Action items tracked per week (join a team, fix AWS account, complete first lab, etc.)

### 🏆 Achievements
- Milestone tracking for every week — from setting up Hugo to completing first workshops

---

## 🧱 Content Structure

```bash
FCAJ_DAILY_LEARNING/
├── content/
│   ├── _index.md                        # Homepage: AWS Learning Journey
│   └── Week1-NewJourney/
│       ├── _index.md                    # First day at FCAJ office
│       ├── 1-NewTerm/
│       │   ├── Module1-GeneralTerm/     # AWS core terminology
│       │   └── Module2-VirtualPrivateCloud/  # In-depth VPC notes
│       ├── 2-ToDoList/                  # Weekly action items
│       └── 3-Achievements/             # Weekly milestones
├── themes/                             # Hugo theme (hugo-theme-learn)
├── static/                             # Static assets
└── config.toml                         # Hugo site configuration (EN + VI)
```

## 🛠 Tech Stack
| Category | Technologies |
|:--|:--|
| Site Generator | Hugo (hugo-theme-learn) |
| Content Format | Markdown |
| Languages | English & Tiếng Việt (i18n) |
| Hosting | AWS / Static Site |
| Diagrams | Draw.io |

---

## 📌 Topics Covered

### Week 1 — New Journey
- **General AWS Terms**: Data Centers, Availability Zones, Regions, Edge Locations (POP), CloudFront CDN, WAF, Route 53, Serverless, AWS Budget
- **Amazon VPC**: Virtual Networks, Subnets, Route Tables, Elastic Network Interfaces, Elastic IPs
- **VPC Connectivity**: Internet Gateway, NAT Gateway, VPC Endpoints (Interface & Gateway), VPC Peering, Transit Gateway
- **Hybrid Networking**: VPN Site-to-Site, VPN Client-to-Site, AWS Direct Connect
- **Security**: Security Groups (Stateful), Network ACLs (Stateless), VPC Flow Logs
- **Load Balancing**: ALB (Layer 7), NLB (Layer 4), CLB (Layer 4 & 7), GLB (Layer 3 / GENEVE)

## 🧪 Upcoming Topics
- Amazon EC2 & Auto Scaling
- Amazon S3 & Storage Services
- IAM (Identity and Access Management)
- Amazon RDS & Database Services
- AWS Lambda & Serverless Architecture
- CloudWatch, CloudTrail & Monitoring
- AWS Well-Architected Framework

---

## ▶️ Run the Site Locally

```bash
# Install Hugo (if not already installed)
brew install hugo   # macOS
sudo apt install hugo  # Ubuntu/Debian

# Clone and run
git clone https://github.com/apase95/AWS-FCAJ-DAILY-LEARNING.git
cd AWS-FCAJ-DAILY-LEARNING/FCAJ_DAILY_LEARNING

# Initialize submodule (Hugo theme)
git submodule update --init --recursive

# Start dev server
hugo server -D
```

Open `http://localhost:1313` in your browser.
<img width="1917" height="1003" alt="image" src="https://github.com/user-attachments/assets/b1208dea-ae29-4217-a710-099b2d82cc63" />

---

## 📬 Contact
- Email: hodtduy.work@gmail.com
- LinkedIn: [hodangthaiduy](https://www.linkedin.com/in/duy-ho-dang-thai-a33159383/)
- AWS Study Group: [FCAJ AWS Community](https://www.facebook.com/groups/awsstudygroupfcj/)

---
### Thanks for visiting this learning journal!
Happy cloud computing ☁️💻
