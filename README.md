# Hi, I'm Lee Yunjin (@gg582)

I am interested in Unix/Linux system management, automation scripting, container orchestration, and Go-based development.
Currently learning Java(OpenJDK 8) to follow up with my internship.
Many of my current projects are just for fun; so it does not match with my internship track.

*I'm doing a 3-month internship from Metabuild Co.(March 3 - June 2)*

## Skills

- Go
- Cloud Computing
- Linux
- FreeBSD
- C/C++
- RIOT OS
- ContikiOS
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
! It was a hard time struggling with Java 1.6-1.8.
+ Pros: Code is explicit.
- Cons: Code lines are too verbose. Search Engine automatically filters old Java lectures.
! Conclusion: It is inevitable to work with legacies, but be aware of being a legacy itself.
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
+ Pros: What was done, and what is creative?
! Cons: What is a limitation? And what can be enhanced further?
```

### Internship Projects
- Legacy System for Java 1.8 to Latest Spring Boot 4.x Application
- Origin: "Java 1.8, Spring+MyBatis+Legacy PostgreSQL" Keywords given from Internship progress
- Stack: Java, Maven, Spring Boot, MyBatis, Apache Tika, PostgreSQL, BountyCastle, JPA
- Pros: Explicit Code, Small LOC per each source file
- Cons: Verbose Code, Verbose & Deep Source Tree, Fragmented Service Requirements per each repository
- [Spring Boot Link](https://github.com/gg582/file-mime-checker)
- [Legacy Spring+MyBatis Link](https://github.com/gg582/spring-development-practice)
- [Legacy Java+Legacy BountyCastle](https://github.com/gg582/encrymania)

*Personally, I don't think that the organization should stick to Java 1.6-1.8 in any purposes in 2026. That's the problem of economics, not a technology.*

### RIOTOSMiniCarImplementation
- A vehicle that drives according to rules while avoiding obstacles
- Origin: **RIOTOS Experiments from Daegu Univ. RESL**
- Stack: C, RTOS
- Pros: Cool GPIO Peripherals Management from RIOTOS, **Driving pattern inspired by entomology(especially ants)**
- Cons: A car moves dumber than actual ants
- [Link](https://github.com/gg582/RIOTOSMiniCarImplementation)
### Raspberry Pi Raspbot
- A device driver, and a test application suites for Yahboom 4WD for RPi 4B
- Origin: **Discarded IoT experiments from MoNet**
- Stack: C, Linux Device Driver
- Pros: Simplified IOCTL wrapper for I2C Chip interaction, Comprehensive Pin Interrupt handler for Ultrasonic sensor
- Cons: No direct access/No low-level CPU-bound machine learning model for Raspi Cam
- [Link](https://github.com/gg582/raspberry_pi_raspbot)

### LibTTAK
- Consistent, Predictable, and Safe Memory Model for Pure C
- Origin: Local prototype for huge legacy style software's RSS footprint enhancement(Such as SSH-Chatter)
- Stack: C
- Pros: Predictable RSS consumption, Deterministic GC cycle
- Cons: Verbose Memory Manager calls, An isolated ecosystem
- [Link](https://github.com/religiya-serdtsa/libttak)

### Nanox
- Minimalistic, Modern Interpertation of UEmacs/PK
- Origin: Personal Interest about Remote Server Environment
- Stack: C, Legacy C Refactoring(GOD Architecture), ncursesw(UI Modernization)
- Pros: Eye-candy Emacs fork, Ultra-lightweight
- Cons: Dirty, legacy-style terminal cursor management
- [Link](https://github.com/gg582/nanox)

### DevOpsPlayground
- Reproducible Kubernetes cluster/service tooling (Helm/Ansible/Shell)
- Origin: Cloud Experiment & Management from **Daegu Univ. MoNet**
- Stack: Kubernetes, Helm, Ansible, Shell
- Pros: Reproducible Environment
- Cons: No proper directions about ACME Service Port Forwarding, No proper directions about setting up domains to Public IPs
- [Link](https://github.com/gg582/devopsplayground)

### IncuSpeed
- Incus container manager (Python GUI + Go secure daemon)
- Origin: *Discarded prototype* from **Daegu Univ. MoNet**
- Stack: Python(End-User Application in KivyMD), Go(Back-end, Incus Abstraction Layer), Incus, Bash(Installer)
- Pros: Reproducible Clean Incus Image
- Cons: Many of Incus features can be reproduced by Docker Compose(except Init-level virtualization), LXC is still prominent
- [Module](https://github.com/gg582/linux_virt_unit)
- [Application](https://github.com/gg582/incuspeed)

### RemoteCarFromMonet
- Kubernetes-integrated remote car control system (C motor driver + Go-based deployment)
- Origin: **Daegu Univ. MoNet**
- Stack: C, Go, Shell, Kubernetes
- Pros: Idea Sketch, Network Research, Brain Storming Result
- Cons: No Internal Proposals could be copied outside of a lab
- [Link](https://github.com/gg582/remotecarfrommonet)

### Linux-Mountain
- Linux kernel/networking tweaks for more predictable latency (BBR / ECMP / NAPI experiments)
- Origin: **Kernel Experiment**
- Pros: High Compatibility with Standard Linux Kernel
- Cons: Unpredictable patterns when connected to multi-node clusters with a standard kernel
- Stack: C, Linux kernel
- [Link](https://github.com/gg582/linux-mountain)

### SSH-Chatter
- TUI-based BBS/chat server over SSH/TELNET
- Origin: **SSH-Chat, Discord, KakaoTalk**
- Stack: C, Linux
- Pros: Looks cool and 90's retro vive
- Cons: This is not cool in 2020s
- [Link](https://github.com/gosuda/ssh-chatter)

### AvianRaptorNet
- Tiny image classifier inspired by avian tectofugal/thalamofugal visual pathways
- Origin: Machine Learning Lecture from Daegu Univ.(Professor Lee Miran), *Ornithology*
- Stack: PyTorch, Python
- Pros: Ultra-lightweight
- Cons: Low Proofs
- [Link](https://github.com/gg582/avianraptornet)

---

### Margo(for fun)
- Custom, Cute, Moe. A Brand-new C dialect
- Origin: **Just for fun**
- Stack: C, Margo(its own)
- Pros: Strong Matrix Functions, Clean Grammar
- Cons: A grammar is too isolated
- [Link](https://github.com/religiya-serdtsa/margo)

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
