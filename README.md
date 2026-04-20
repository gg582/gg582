# Hi, I'm Lee Yunjin (@gg582)

System-level developer focused on Linux, networking, and containerized infrastructure.  
Experienced in building low-level systems, reproducible environments, and performance-oriented tooling using C and Go.

Currently working on legacy Java environments (OpenJDK 8) as part of my internship, while maintaining strong interest in kernel-level optimization and infrastructure design.

*3-month internship at Metabuild Co. (March 3 - June 2)*

## Skills

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
| **Basics** | Legacy Env. | OpenJDK 8, PostgreSQL 9.6 |
| **Intermediate** | JDK Migration | Legacy JDK to Latest (1.6, 1.8, 21) |
| **Hard** | Advanced System | Apache Tika, Server Management, Design Pattern |
| ***Actually Learned*** | Basics, Hard(95%), Intermediate(50%) | Server Installation & Setup, Legacy Programming, Design Pattern, Apache Tika |

```diff
! Experience: Developed across multiple JDK versions (1.6–1.8–21) and adapted to legacy environments.
+ Strength: Explicit control over system behavior and compatibility with legacy stacks.
- Limitation: Increased verbosity and deeper code structure due to legacy conventions.
! Insight: Working with legacy systems requires balancing maintainability, compatibility, and modernization.
```

```bash
~ $ #################>== [90% Done]
```

---

# History
- 2021-2022 Daegu Univ. **MoNet**
- 2022-2023 Daegu Univ. RESL
- 2023-2025 Prepared for Graduation work (IncuSpeed)
- 2025 Industrial Engineer Certificate, Hana Social Venture University
- 2026.03.03-2026.06.02 Metabuild Co. Internship
- 2026-06~        (?)

## Focus
- Linux systems & networking
  - Kernel-level Tweak
- Automation / IaC (Ansible, Helm, Kubernetes)
- Go services (daemon, CLI, tooling, Web Development)
- C Programming
  - Legacy Refactoring
  - System Optimization
  - C/C++ Lightweight Web Back-end


```c
/*
 * Tiered execution flow designed for zero-latency branch prediction.
 * Pure C logic utilizing IEEE 754 NaN-space for pointer tagging.
 */
#define BIGINT_TAG_MASK 0xFFF8000000000000ULL
#define EXPONENT_MASK   0x7FF0000000000000ULL

uint64_t next_step(uint64_t n) {
    // First, check if it is `intxx_t`
    if (!(n & 0xC000000000000000ULL)) {
        // this is int, return n << 1; same as return (n * 2)
        return n << 1;
    }

    // Check if it is big integer.
    // XOR is great for quickly comparing mask bits
    if (((n ^ BIGINT_TAG_MASK) & BIGINT_TAG_MASK) == 0) {
        return bigint_mul2(n);
    }

    // 'double *= 2' by incrementing the exponent bits
    // Keeps data within General Purpose Registers, avoiding FPU stalls.
    uint64_t exp_inc = n + (1ULL << 52);
    if ((exp_inc & EXPONENT_MASK) != EXPONENT_MASK) {
        return exp_inc;
    }

    // Safely promote the result to big int type and return. 
    return promote_to_bigint_and_mul2(n);
}
```

## Key Projects

```diff
- Please See Carefully and analyze these two points:
+ Strength: What was done, and what is creative?
! Limitation: What is a limitation? And what can be enhanced further?
```

### Internship Projects
- Legacy System for Java 1.8 to Latest Spring Boot 4.x Application
- Origin: "Java 1.8, Spring+MyBatis+Legacy PostgreSQL" Keywords given from Internship progress
- Stack: Java, Maven, Spring Boot, MyBatis, Apache Tika, PostgreSQL, BountyCastle, JPA
- Strength: Explicit Code, Small LOC per each source file
- Limitation: Verbose Code, Verbose & Deep Source Tree, Fragmented Service Requirements per each repository
- [Spring Boot Link](https://github.com/gg582/file-mime-checker)
- [Legacy Spring+MyBatis Link](https://github.com/gg582/spring-development-practice)
- [Legacy Java+Legacy BountyCastle](https://github.com/gg582/encrymania)

*Working with legacy Java environments (1.6–1.8) provided practical experience in handling real-world constraints such as compatibility and long-term maintenance.*

*Refactoring legacy architectures requires structural analysis of code paths, data flow, and system behavior, followed by targeted improvements based on observable and measurable characteristics.*

### Part 1. Infrastructure & Edge Computing

---

### DevOpsPlayground
- Reproducible Kubernetes cluster/service tooling (Helm/Ansible/Shell)
- Origin: Cloud Experiment & Management from **Daegu Univ. MoNet**
- Stack: Kubernetes, Helm, Ansible, Shell
- Strength: Reproducible Environment
- Limitation: No proper directions about ACME Service Port Forwarding, No proper directions about setting up domains to Public IPs
- [Link](https://github.com/gg582/devopsplayground)

### IncuSpeed
- Incus container manager (Python GUI + Go secure daemon)
- Origin: *Discarded prototype* from **Daegu Univ. MoNet**
- Stack: Python(End-User Application in KivyMD), Go(Back-end, Incus Abstraction Layer), Incus, Bash(Installer)
- Strength: Reproducible Clean Incus Image
- Limitation: Many of Incus features can be reproduced by Docker Compose(except Init-level virtualization), LXC is still prominent
- [Module](https://github.com/gg582/linux_virt_unit)
- [Application](https://github.com/gg582/incuspeed)

### RemoteCarFromMonet
- Strength: Integration of physical device control with Kubernetes-based deployment and networking experiments
- Origin: **Daegu Univ. MoNet**
- Stack: C, Go, Shell, Kubernetes
- Strength: Idea Sketch, Network Research, Brain Storming Result
- Limitation: No Internal Proposals could be copied outside of a lab
- [Link](https://github.com/gg582/remotecarfrommonet)

### Part 2. System Optimization

---

### LibTTAK
- Consistent, Predictable, and Safe Memory Model for Pure C
- Stack: C
- Strength: Predictable RSS consumption and deterministic GC behavior
- Origin: Local prototype for huge legacy style software's RSS footprint enhancement(Such as SSH-Chatter)
- Limitation: Verbose Memory Manager calls, An isolated ecosystem
- [Link](https://github.com/religiya-serdtsa/libttak)

### Linux-Mountain
- Linux kernel/networking tweaks for more predictable latency (BBR / ECMP / NAPI experiments)
- Origin: **Kernel Experiment**
- Strength: High Compatibility with Standard Linux Kernel
- Limitation: Unpredictable patterns when connected to multi-node clusters with a standard kernel
- Stack: C, Linux kernel
- [Link](https://github.com/gg582/linux-mountain)

### RIOTOSMiniCarImplementation
- A vehicle that drives according to rules while avoiding obstacles
- Origin: **RIOTOS Experiments from Daegu Univ. RESL**
- Stack: C, RTOS
- Strength: Cool GPIO Peripherals Management from RIOTOS, **Driving pattern inspired by entomology(especially ants)**
- Limitation: A car moves dumber than actual ants
- [Link](https://github.com/gg582/RIOTOSMiniCarImplementation)

### Raspberry Pi Raspbot
- A device driver, and a test application suites for Yahboom 4WD for RPi 4B
- Origin: **Discarded IoT experiments from MoNet**
- Stack: C, Linux Device Driver
- Strength: Simplified IOCTL wrapper for I2C Chip interaction, Comprehensive Pin Interrupt handler for Ultrasonic sensor
- Limitation: No direct access/No low-level CPU-bound machine learning model for Raspi Cam
- [Link](https://github.com/gg582/raspberry_pi_raspbot)

---

```diff
+ From here on, the software development is based on personal interest and beliefs. Although not practical, these are like 'well-crafted clockwork' pieces into which a lot of technical effort has been put, so please view them with affection.
```

### SSH-Chatter
- TUI-based BBS/chat server over SSH/TELNET
- Origin: **SSH-Chat, Discord, KakaoTalk**
- Stack: C, Linux
- Strength: Looks cool and 90's retro vive
- Limitation: This is not cool in 2020s
- [Link](https://github.com/gosuda/ssh-chatter)

### AvianRaptorNet
- Tiny image classifier inspired by avian tectofugal/thalamofugal visual pathways
- Origin: Machine Learning Lecture from Daegu Univ.(Professor Lee Miran), *Ornithology*
- Stack: PyTorch, Python
- Strength: Ultra-lightweight
- Limitation: Low Proofs
- [Link](https://github.com/gg582/avianraptornet)


### Margo(for fun)
- Custom, Cute, Moe. A Brand-new C dialect
- Origin: **Just for fun**
- Stack: C, Margo(its own)
- Strength: Strong Matrix Functions, Clean Grammar
- Limitation: A grammar is too isolated
- [Link](https://github.com/religiya-serdtsa/margo)


### ChoiCrypt
- An AES-256 variant featuring a shuffle inspired by Choi Seok-jeong's Hexagonal Tortoise problem
- Origin: Cryptography lecture from Daegu Univ.(Professor Choi Yong-ho)
- Stack: C
- Strength: It is very difficult for an attacker to predict if it involves shuffling beyond the S-Box or cryptographic tuning.
- Limitation: This is a custom encryption which is quite heavy. It is only for an experiment, after all
- [Link](https://github.com/gg582/choicrypt)

### CWIST
- Easy Web Development Suite for Pure C
- Origin: **Why can't we invent Flask for C**
- Stack: C
- Strength: Simple Calls, Easy API, Fast MVP reproduction. AI-friendly and predictable naming convention
- Limitation: No Implementation for HTTP/2, Implicit code lines
- [Link](http://github.com/religiya-serdtsa/cwist)

### Baboship
- Easy EMS Parcel Shipping Prediction
- Origin: **My Soviet 11-jewels Alarm Clock from Ukraine is not arriving**
- Stack: C, CWIST(its own), WASM
- Strength: 100% AI-driven MVP
- Limitation: No prediction supported for sea parcel service
- [Link](https://github.com/gg582/baboship)
- [Website](https://gg582.github.io/baboship)

### Ceversi
- Super-lightweight Reversi/Othello VS Website with Virtual Betting Room
- Origin: **ReactJS-like look and feel with SSR, all in C**
- Stack: C, CWIST(its own), SQLite
- Strength: 100% AI-driven MVP
- Limitation: The site is boring
- [Link](https://github.com/gg582/ceversi)
- [Website](https://ceversi.korokorok.com)

### Nanox
- Minimalistic, Modern Interpertation of UEmacs/PK
- Origin: Personal Interest about Remote Server Environment
- Stack: C, Legacy C Refactoring(GOD Architecture), ncursesw(UI Modernization)
- Strength: Eye-candy Emacs fork, Ultra-lightweight
- Limitation: Dirty, legacy-style terminal cursor management
- [Link](https://github.com/gg582/nanox)

---

## Activities & Credentials
### Research Assistant / Projects
- Research Assistant in national R&D projects (**ETRI: 2**, NRF: 4)

![Researches](./certs.png)

### Awards
![Awards](./award.png)
![Award2](./IT공학대전학생작품경진대회상.png)

### Certifications
- Industrial Engineer (Information Processing) — passed (Republic of Korea)

![IndustrialEngineer](./industrial_engineer.png)

### Training
![edu](./하나금융창업교육.png)

---

## Stats (Optional)
[![GitHub Streak](http://github-readme-streak-stats.herokuapp.com?user=gg582&theme=dark)](https://git.io/streak-stats)
[![Top Langs](https://github-readme-stats-rouge-rho-81.vercel.app/api/top-langs/?username=gg582&layout=compact&theme=dark&exclude_repo=BaekjoonProblemSolvingCollections,linux-grate-10percent-overclock-test,RIOTOSMiniCarImplementation,CSharp-Arkanoid-based-Project,tk9.0,nanox_rust,simple-html-examples)](https://github.com/anuraghazra/github-readme-stats)
[Grade](https://github-readme-stats.vercel.app/api?username=gg582&show_icons=true)
![Total Lines of Code](https://github.com/gg582/allcloc/blob/main/public/banner.svg)
[![Solved.ac Profile](http://mazassumnida.wtf/api/v2/generate_badge?boj=yoonjin67)](https://solved.ac/yoonjin67/)

---

## Contact
- gg582@proton.me
- gzblues61@daum.net
