# Network-Design-Lab5
Layer 7 WAF Defense Against PHP-to-Shell Exploits

A lab assignment demonstrating how to design, deploy, and verify a Layer 7 Web
Application Firewall (WAF) using **ModSecurity**, **NGINX**, and
**Containerlab**. Custom ModSecurity rules protect a vulnerable PHP backend
against php2shell remote code execution (RCE) vectors.

---

## Table of Contents

1. [Overview & Objectives](#overview--objectives)
2. [Prerequisites](#prerequisites)
3. [Network Topology & IP Allocation](#network-topology--ip-allocation)
4. [Repository Structure](#repository-structure)
5. [Building the Custom Images](#building-the-custom-images)
6. [Deploying the Lab](#deploying-the-lab)
7. [Custom ModSecurity Rules](#custom-modsecurity-rules)
8. [Validation & Testing](#validation--testing)
9. [Troubleshooting](#troubleshooting)
10. [Cleanup](#cleanup)
11. [Marking Rubric](#marking-rubric)

---

## Overview & Objectives

The objective of this lab is to design, deploy, and verify a Layer 7 WAF using
ModSecurity, NGINX, and Containerlab. An isolated switched network topology
(`sw0`) connects an attacker node, a WAF proxy, and a backend vulnerable PHP
application (`php:8.2.34-apache`). The primary task is writing custom
ModSecurity rules that block php2shell RCE vectors while allowing legitimate
traffic through.

**Learning outcomes:**

- Build container images for Containerlab-compatible nodes
- Construct a switched L2 topology with static IP addressing
- Reverse-proxy traffic through ModSecurity/NGINX
- Author custom ModSecurity rules targeting argument names, values, and headers
- Validate WAF behavior against expected HTTP status codes

---

## Prerequisites

| Requirement | Version / Notes |
|-------------|-----------------|
| Docker Engine | 24.x or newer |
| Containerlab | 0.5x or newer |
| Linux host | Kernel module `bridge` loaded; `iproute2` available |
| Disk space | ~2 GB for base images |

Verify your environment:

```bash
docker --version
containerlab version
