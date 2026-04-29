# Hi, I'm Lee Yunjin (@gg582)

[Korean README](https://github.com/gg582/gg582/blob/main/README.md)

I am a system-level developer focusing on Linux, networking, and container-based infrastructure.
I have experience in building low-level systems, reproducible environments, and performance-oriented tools using C and Go.

Currently, as part of my internship, I am dealing with legacy Java environments (OpenJDK 8) and document OCR DB analysis, while also maintaining a steady interest in kernel-level optimization and infrastructure design.

*Performing a 3-month internship at Metabuild (March 3 - June 2)*

## Key Projects

- **IncuSpeed** — Reproducible container environment manager (Python + Go + Incus)
  → Practical experience in building and managing actual deployable test environments

- **Linux-Mountain** — Linux kernel and network tuning for predictable latency (BBR, ECMP, NAPI)
  → Hands-on experience in directly optimizing performance at the kernel and network layers

- **DevOpsPlayground** — Reproducible Kubernetes cluster and service configuration (Helm, Ansible)
  → Experience in IaC-based cluster provisioning and automation

## Tech Stack

- Go
- Cloud Computing
- Linux
- FreeBSD
- C/C++
- RIOT OS
- Software Optimization
- Java

## Internship Track

| Difficulty | Focus Area | Tech Stack |
| :--- | :--- | :--- |
| **Basic** | Legacy Environment | OpenJDK 8, PostgreSQL 9.6 |
| **Intermediate** | JDK Migration | Legacy JDK → Latest JDK (1.6, 1.8, 21), Legacy Visual Basic → Go (Using company-provided Claude Code) |
| **Advanced** | Advanced System | Apache Tika, Server Management, Design Patterns, OCR Data Filtering & Integrity Verification in PostgreSQL |
| ***Actually Learned*** | Basic, Advanced (95%), Intermediate (50%) | Server Installation & Deployment, Legacy Programming, Design Patterns, Apache Tika, SQL Writing |

```diff
! Experience: Experience adapting to legacy environments by developing across various JDK versions (1.6–1.8–21)
+ Strength: Can explicitly control system behavior and ensure compatibility with legacy stacks
- Limitation: Code tends to become verbose and structures grow deep due to legacy conventions
! Insight: Handling legacy systems requires a balance between maintainability, compatibility, and modernization
```

```bash
~ $ #################>== [90% Done]
```

---

# History

* 2021-2022 Daegu University **MoNet**
* 2022-2023 Daegu University **RESL**
* 2023-2025 Graduation Project Preparation (IncuSpeed)
* 2025 Industrial Engineer Information Processing, Hana Social Venture University
* 2026.03.03-2026.06.02 Metabuild Internship
* 2026-06~ (?)

## Areas of Interest

* Linux Systems & Networking
  * Kernel-level tuning
* Automation / IaC (Ansible, Helm, Kubernetes)
* Go Services (Daemon, CLI, Tools, Web Development)
* C Programming
  * Legacy Refactoring
  * System Optimization
  * C/C++ Lightweight Web Backend

```c
/*
 * Hierarchical execution flow designed to minimize branch prediction latency
 * Pure C logic utilizing IEEE 754 NaN space for pointer tagging
 */
#define BIGINT_TAG_MASK 0xFFF8000000000000ULL
#define EXPONENT_MASK   0x7FF0000000000000ULL

uint64_t next_step(uint64_t n) {
    // First, check if it is `intxx_t`
    if (!(n & 0xC000000000000000ULL)) {
        // If it is an integer, return n << 1, which is identical to (n * 2)
        return n << 1;
    }

    // Check if it is a Big Integer
    // XOR is advantageous for quickly comparing mask bits
    if (((n ^ BIGINT_TAG_MASK) & BIGINT_TAG_MASK) == 0) {
        return bigint_mul2(n);
    }

    // Perform 'double *= 2' by increasing exponent bits
    // Keeps data inside General Purpose Registers to avoid FPU stalls
    uint64_t exp_inc = n + (1ULL << 52);
    if ((exp_inc & EXPONENT_MASK) != EXPONENT_MASK) {
        return exp_inc;
    }

    // Safely promote the result to big int type and return
    return promote_to_bigint_and_mul2(n);
}
```

## Key Projects

### Internship Project

* Learning Java 1.8-based legacy system, Modern Spring Boot 4.x application structure
* Background: Started based on keywords "Java 1.8, Spring+MyBatis+Legacy PostgreSQL" during the internship
* Tech Stack: Java, Maven, Spring Boot, MyBatis, Apache Tika, PostgreSQL, BouncyCastle, JPA
* Strength (Pros): Explicit code, small LOC per each source file
* Limitation (Cons): Verbose code, deep and complex source tree, fragmented service requirements per repository
* [Spring Boot Link](https://github.com/gg582/file-mime-checker)
* [Legacy Spring+MyBatis Link](https://github.com/gg582/spring-development-practice)
* [Legacy Java+Legacy BouncyCastle](https://github.com/gg582/encrymania)

*Handling legacy Java environments (1.6–1.8) allowed me to actually experience realistic constraints such as compatibility and long-term maintenance.*

*Refactoring legacy architecture requires a structural analysis of code paths, data flows, and system behavior first, followed by targeted improvements based on observable and measurable characteristics.*

*Verbose and loosely organized code increases cognitive load and decreases maintainability, making structural refactoring essential for long-term system evolution.*

* Microsoft Excel Format with VBA(*.xlsm) to Go+Javascript-based Web-App
* Background: Started work based on given sheets
* Tech Stack: Legacy Migration
* Strength (Pros): Golang-based lightweight Web Server
* Limitation (Cons): The app is for educational purpose.

### Part 1. Infrastructure & Edge Computing

---

### DevOpsPlayground

* Reproducible Kubernetes cluster/service toolset (Helm/Ansible/Shell)
* Background: Experience in cloud experimentation and management conducted at **Daegu University MoNet**
* Tech Stack: Kubernetes, Helm, Ansible, Shell
* Strength (Pros): Reproducible environment
* Limitation (Cons): Lack of proper guidance on ACME service port forwarding, lack of setup guide for connecting domains to public IPs
* [Link](https://github.com/gg582/devopsplayground)

### IncuSpeed

* Incus container manager (Python GUI + Go secure daemon)
* Background: *Discarded prototype* that was conducted at **Daegu University MoNet**
* Tech Stack: Python (Final user application in KivyMD), Go (Backend, Incus abstraction layer), Incus, Bash (Installer)
* Strength (Pros): Reproducible clean Incus image environment
* Limitation (Cons): Many Incus features can be reproduced with Docker Compose (excluding init-level virtualization), LXC family still has an entry barrier
* [Module](https://github.com/gg582/linux_virt_unit)
* [Application](https://github.com/gg582/incuspeed)

### RemoteCarFromMonet

* Kubernetes-based remote vehicle control system combining physical device drivers and distributed deployment
* Background: **Daegu University MoNet**
* Tech Stack: C, Go, Shell, Kubernetes
* Strength (Pros): Integration of physical device control with Kubernetes-based deployment and networking experiments
* Limitation (Cons): Internal proposals could not be taken outside the laboratory, and the cognitively friendly controller dashboard (by @alisherfw) based on Javascript was excluded due to the loss of the GitLab server

### Part 2. System Optimization

---

### LibTTAK

* Consistent, predictable, and safe memory model for pure C
* Tech Stack: C
* Strength (Pros): Predictable RSS usage and deterministic GC behavior
* Background: Local prototype for improving the RSS footprint of large legacy-style software like SSH-Chatter
* Limitation (Cons): Verbose memory manager calls, isolated ecosystem
* [Link](https://github.com/religiya-serdtsa/libttak)

### Linux-Mountain

* Linux kernel/network tuning for more predictable latency (BBR / ECMP / NAPI experiments)
* Background: **Kernel Experiment**
* Strength (Pros): High compatibility with the standard Linux kernel
* Limitation (Cons): Unpredictable patterns may occur when connected to multi-node clusters with the standard kernel
* Tech Stack: C, Linux kernel
* [Link](https://github.com/gg582/linux-mountain)

### RIOTOSMiniCarImplementation

* A vehicle that avoids obstacles while driving according to rules
* Background: RIOT OS experiment conducted at **Daegu University RESL**
* Tech Stack: C, RTOS
* Strength (Pros): RIOT OS-based GPIO peripheral management, driving patterns inspired by **entomology (especially ants)**
* Limitation (Cons): Rule-based navigation without adaptive or learning functions
* [Link](https://github.com/gg582/RIOTOSMiniCarImplementation)

### Raspberry Pi Raspbot

* Device drivers and test application suite for Yahboom 4WD for Raspberry Pi 4B
* Background: *Discarded IoT experiments* conducted at **MoNet**
* Tech Stack: C, Linux Device Driver
* Strength (Pros): Simplified IOCTL wrapper for I2C chip interaction, comprehensive pin interrupt handler for ultrasonic sensors
* Limitation (Cons): Absence of direct access / failure to implement low-level CPU-bound machine learning models for the Raspberry Pi camera
* [Link](https://github.com/gg582/raspberry_pi_raspbot)

---

```diff
+ The following projects focus on experimental system design, low-level control, and custom runtime behavior beyond general production constraints.
```

### SSH-Chatter

* TUI-based BBS/chat server operating over SSH/TELNET
* Background: **SSH-Chat, Discord, KakaoTalk**
* Tech Stack: C, Linux
* Strength (Pros): Cool 90s retro vibes
* Limitation (Cons): Limited applicability in modern distributed communication environments
* [Link](https://github.com/gosuda/ssh-chatter)
* Telnet port 2323, SSH port 22
* [Web Terminal (May be down)](https://retro-chatroom.gosunuts.xyz/)

### AvianRaptorNet

* Ultra-small image classifier inspired by the tectofugal/thalamofugal visual pathways of birds
* Background: Daegu University Machine Learning class (Professor Lee Miran), *Ornithology*
* Tech Stack: PyTorch, Python
* Strength (Pros): Ultra-lightweight
* Limitation (Cons): Experimental verification and benchmarking are limited
* [Link](https://github.com/gg582/avianraptornet)

### Margo (for fun)

* A custom, cute, and moe new C dialect
* Background: **Just for fun**
* Tech Stack: C, Margo (Own language)
* Strength (Pros): Powerful matrix functions, clean syntax
* Limitation (Cons): Grammar ecosystem is too isolated
* [Link](https://github.com/religiya-serdtsa/margo)

### ChoiCrypt

* AES-256 variant including a shuffle inspired by Choi Seok-jeong's Hexagonal Tortoise Problem (Ji-Su-Gui-Mun-Do)
* Background: Daegu University Cryptography class (Professor Choi Yong-ho)
* Tech Stack: C
* Strength (Pros): Extremely difficult for an attacker to predict when it involves shuffles or cryptographic tuning beyond the S-Box
* Limitation (Cons): Heavy custom encryption method and is strictly for experimental use
* [Link](https://github.com/gg582/choicrypt)

### CWIST

* Easy web development suite for pure C
* Background: **Why can't we make Flask for C?**
* Tech Stack: C
* Strength (Pros): Simple calls, easy API, fast MVP reproduction, AI-friendly and predictable naming
* Limitation (Cons): HTTP/2 not implemented, presence of implicit code lines
* [Link](http://github.com/religiya-serdtsa/cwist)

### Baboship

* Easy EMS international mail delivery prediction
* Background: **Because my Soviet 11-jewel alarm clock coming from Ukraine did not arrive**
* Tech Stack: C, CWIST (Own), WASM
* Strength (Pros): 100% AI-based MVP
* Limitation (Cons): Does not support sea mail delivery prediction
* [Link](https://github.com/gg582/baboship)
* [Website](https://gg582.github.io/baboship)

### Ceversi

* Ultra-lightweight Reversi/Othello match website including a virtual betting room
* Background: **Implementing a ReactJS-like look and feel entirely with C via SSR**
* Tech Stack: C, CWIST (Own), SQLite
* Strength (Pros): 100% AI-based MVP
* Limitation (Cons): Game features and attraction are not sufficient to retain users
* [Link](https://github.com/gg582/ceversi)
* [Website](https://ceversi.korokorok.com)

### Nanox

* A minimalistic editor modernizing UEmacs/PK
* Background: Personal interest in remote server environments
* Tech Stack: C, Legacy C Refactoring (GOD Architecture), ncursesw (UI Modernization)
* Strength (Pros): Good-looking Emacs fork, ultra-lightweight
* Limitation (Cons): Messy legacy-style terminal cursor management
* [Link](https://github.com/gg582/nanox)

---

## Activities & Qualifications

### Research Participation / Projects

* Participation as a Research Assistant in national R&D projects (**ETRI: 2 cases**, NRF: 4 cases)

![Researches](./certs.png)

### Awards

![Awards](./award.png)
![Award2](./IT공학대전학생작품경진대회상.png)

### Certification

* Passed Industrial Engineer Information Processing (Republic of Korea)

![IndustrialEngineer](./industrial_engineer.png)

### Education

![edu](./하나금융창업교육.png)

---

## Statistics

[![GitHub Streak](http://github-readme-streak-stats.herokuapp.com?user=gg582&theme=dark)](https://git.io/streak-stats)
[![Top Langs](https://github-readme-stats-rouge-rho-81.vercel.app/api/top-langs/?username=gg582&layout=compact&theme=dark&exclude_repo=BaekjoonProblemSolvingCollections,linux-grate-10percent-overclock-test,RIOTOSMiniCarImplementation,CSharp-Arkanoid-based-Project,tk9.0,nanox_rust,simple-html-examples)](https://github.com/anuraghazra/github-readme-stats)
![Grade](https://github-readme-stats.vercel.app/api?username=gg582&show_icons=true)
![Total Lines of Code](https://github.com/gg582/allcloc/blob/main/public/banner.svg)
![Gold II capture before Baekjoon service termination](https://github.com/gg582/gg582/blob/main/%EB%B0%B1%EC%A4%80%EA%B8%B0%EB%A1%9D%EC%84%B1%EC%BA%A1%EC%B3%902026.png?raw=true)

---

## Contact

* [gg582@proton.me](mailto:gg582@proton.me)
* [gzblues61@daum.net](mailto:gzblues61@daum.net)
