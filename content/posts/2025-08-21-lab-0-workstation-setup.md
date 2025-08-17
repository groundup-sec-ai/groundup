---
title: "Lab 0: Workstation + Juice Shop"
date: 2025-08-21
description: "Setting up a baseline environment: OWASP Juice Shop for web security practice and Jupyter for AI experiments."
tags: ["cybersecurity", "ai", "beginner", "groundup"]
---

# Lab 0: Workstation + Juice Shop

{{< img src="/screenshots/2025-08-18_kickoff_01.png" alt="GroundUp Kickoff" width="816" >}}

## Goal
Create a baseline environment that will be used throughout this series.  
We’re setting up two foundations:  

- **OWASP Juice Shop** – a deliberately vulnerable web application, giving us a safe playground for web security labs.  
- **Jupyter Notebooks** – an interactive Python environment we’ll later use for AI experiments, automation, and documenting results.  

Even if we don’t need Jupyter immediately, installing it now ensures we’re ready when the time comes.

---

## A note for Windows users
All labs are written using **macOS/Linux commands**.  
If you’re on Windows, you can follow along using [WSL2](https://learn.microsoft.com/en-us/windows/wsl/) or by adapting commands for PowerShell/Docker Desktop. The workflow and concepts are the same.

---

## Prerequisites
- Admin rights on your machine  
- ~5 GB free disk space  
- Installed: Git, Python 3.11+, Docker, VS Code (optional)

---

## Steps (macOS/Linux)

```bash
# Verify versions
git --version
python3 --version
docker --version

# Create project folder
mkdir -p ~/groundup && cd ~/groundup
git init

# Set up Python virtual environment
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip jupyter

# Run OWASP Juice Shop in Docker
docker pull bkimminich/juice-shop
docker run -d --name juice -p 3000:3000 bkimminich/juice-shop

# Verify it’s running
curl -I http://localhost:3000
```
{{< img src="/screenshots/2025-08-21-lab-0-workstation-setup_01.png" alt="GroundUp Docker Juice Shop curl" width="802" >}}
This is the curl command showing the response headers from Juice Shop

{{< img src="/screenshots/2025-08-21-lab-0-workstation-setup_02.png" alt="GroundUp Docker Juice Shop browser" width="1094" >}}
---

## Verify it worked
- Open [http://localhost:3000](http://localhost:3000) in your browser → you should see the Juice Shop homepage.  
- Run `docker ps` → you should see a container named `juice` with status `Up`.  
- Run `jupyter --version` → confirms Jupyter installed successfully.

{{< img src="/screenshots/2025-08-21-lab-0-workstation-setup_03.png" alt="GroundUp Docker PS" width="802" >}}
{{< img src="/screenshots/2025-08-21-lab-0-workstation-setup_04.png" alt="GroundUp Jupyter version" width="802" >}}
---

## Clean up
If you want to stop and remove the Juice Shop container:  

```bash
docker stop juice && docker rm juice
```

---

## Takeaways
- Running Juice Shop locally provides a safe, reproducible playground for web security practice.  
- Jupyter will be our workspace for AI experiments later in the series.  
- With these two tools set up, we have a solid foundation for all future labs.  
