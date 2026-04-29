```markdown
# Hi, I'm Lee Yunjin (@gg582)

[Korean README](https://github.com/gg582/gg582/blob/main/README.md)

System-level developer focused on Linux, networking, and containerized infrastructure.  
Experienced in building low-level systems, reproducible environments, and performance-oriented tooling using C and Go.

Currently handling legacy Java environments (OpenJDK 8) and Document OCR DB analysis as part of my internship, while maintaining a strong interest in kernel-level optimization and infrastructure design.

*3-month internship at Metabuild Co. (March 3 – June 2, 2026)*

## Highlight

- **IncuSpeed** — Reproducible container environment manager (Python + Go + Incus)  
  → Practical experience in building and managing deployable test environments.
- **Linux-Mountain** — Linux kernel and networking tuning for predictable latency (BBR, ECMP, NAPI)  
  → Hands-on experience with performance optimization at the kernel and network layers.
- **DevOpsPlayground** — Reproducible Kubernetes cluster and service setup (Helm, Ansible)  
  → Infrastructure-as-Code (IaC) based cluster provisioning and automation experience.

## Skills

- **Languages:** Go, C/C++, Java
- **Systems:** Linux, FreeBSD, RIOT OS (RTOS)
- **Infrastructure:** Cloud Computing, Kubernetes, Ansible, Helm
- **Specialization:** Software Optimization, Legacy Refactoring

## Internship Track

| Difficulty | Focus Area | Tech Stack |
| :--- | :--- | :--- |
| **Basics** | Legacy Env. | OpenJDK 8, PostgreSQL 9.6 |
| **Intermediate** | JDK Migration | Legacy JDK → Modern JDK (1.6, 1.8, 21), Legacy Visual Basic → Go (via Claude Code) |
| **Advanced** | Advanced Systems | Apache Tika, Server Management, Design Patterns, PostgreSQL OCR Filtering |
| ***Actual Progress*** | Basics, Advanced (95%), Intermediate (50%) | Server Setup, Legacy Programming, Design Patterns, Apache Tika, SQL Authoring |

```diff
! Experience: Developed across multiple JDK versions (1.6–1.8–21) and adapted to legacy environments.
+ Strength: Explicit control over system behavior and ensuring compatibility with legacy stacks.
- Limitation: Increased verbosity and deeper code structures due to legacy conventions.
! Insight: Working with legacy systems requires a balance between maintainability, compatibility, and modernization.
```

```bash
~ $ #################>== [90% Done]
```

---

# History

* 2021-2022 Daegu Univ. **MoNet** (Research Assistant)
* 2022-2023 Daegu Univ. **RESL** (Research Assistant)
* 2023-2025 Graduation Project Development (IncuSpeed)
* 2025 Industrial Engineer Information Processing, Hana Social Venture University
* 2026.03.03 - 2026.06.02 Metabuild Co. Internship
* 2026.06 - (?)

## Focus

* **Linux Systems & Networking**
    * Kernel-level tuning
* **Automation / IaC** (Ansible, Helm, Kubernetes)
* **Go Services** (Daemons, CLI, Tooling, Web Development)
* **C Programming**
    * Legacy Refactoring & System Optimization
    * Lightweight C/C++ Web Backends

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
        // If integer, return n << 1 (same as n * 2)
        return n << 1;
    }

    // Check if it is a Big Integer
    if (((n ^ BIGINT_TAG_MASK) & BIGINT_TAG_MASK) == 0) {
        return bigint_mul2(n);
    }

    // Perform 'double *= 2' by incrementing exponent bits
    // Keeps data within General Purpose Registers to avoid FPU stalls
    uint64_t exp_inc = n + (1ULL << 52);
    if ((exp_inc & EXPONENT_MASK) != EXPONENT_MASK) {
        return exp_inc;
    }

    // Safely promote to big int and return
    return promote_to_bigint_and_mul2(n);
}
```

## Key Projects

### Internship Projects

* **Modernizing Legacy Java 1.8 to Spring Boot 4.x Architecture**
    * **Background:** Transitioning from "Java 1.8, Spring+MyBatis+Legacy PostgreSQL" stack.
    * **Stack:** Java, Maven, Spring Boot, MyBatis, Apache Tika, PostgreSQL, BouncyCastle, JPA.
    * **Strength:** Explicit code logic, modularized source files with small LOC.
    * **Insight:** Refactoring legacy architectures requires structural analysis of data flow and system behavior, followed by targeted improvements.
    * [Spring Boot Link](https://github.com/gg582/file-mime-checker) | [Legacy Spring+MyBatis](https://github.com/gg582/spring-development-practice) | [Legacy Java+BouncyCastle](https://github.com/gg582/encrymania)

---

### Part 1. Infrastructure & Edge Computing

#### DevOpsPlayground
* Reproducible Kubernetes cluster/service tooling (Helm/Ansible/Shell)
* **Origin:** Cloud experiments at **Daegu Univ. MoNet**.
* [Link](https://github.com/gg582/devopsplayground)

#### IncuSpeed
* Incus container manager (Python GUI + Go secure daemon)
* **Stack:** Python (KivyMD), Go (Incus abstraction), Bash.
* [Application](https://github.com/gg582/incuspeed)

#### RemoteCarFromMonet
* K8s-integrated remote car control combining physical device drivers and distributed deployment.
* **Stack:** C, Go, Kubernetes.

---

### Part 2. System Optimization

#### LibTTAK
* Consistent and safe memory model for Pure C.
* **Feature:** Predictable RSS consumption and deterministic GC behavior.
* [Link](https://github.com/religiya-serdtsa/libttak)

#### Linux-Mountain
* Kernel/networking tweaks for predictable latency (BBR / ECMP / NAPI).
* [Link](https://github.com/gg582/linux-mountain)

#### RIOTOSMiniCarImplementation
* Rule-based autonomous vehicle inspired by **entomology (ants)**.
* **Stack:** C, RIOT OS (RTOS).
* [Link](https://github.com/gg582/RIOTOSMiniCarImplementation)

---

### Experimental & Creative Systems

#### SSH-Chatter
* TUI-based BBS/chat server over SSH (Port 22) and TELNET (Port 2323).
* **Vibe:** 90's Retro aesthetics in C.
* [Web Terminal](https://retro-chatroom.rly.best/) | [Link](https://github.com/gosuda/ssh-chatter)

#### Margo (for fun)
* A custom, "cute" C-dialect transpiler.
* **Strength:** Powerful matrix functions and clean grammar.
* [Link](https://github.com/religiya-serdtsa/margo)

#### Nanox
* Modern interpretation of UEmacs/PK using `ncursesw` for UI modernization.
* **Focus:** Lightweight remote server editing environment.
* [Link](https://github.com/gg582/nanox)

#### ChoiCrypt
* AES-256 variant featuring shuffles inspired by **Choi Seok-jeong's Magic Squares (Ji-Su-Gui-Mun-Do)**.
* [Link](https://github.com/gg582/choicrypt)

---

## Contact
* [gg582@proton.me](mailto:gg582@proton.me)
* [gzblues61@daum.net](mailto:gzblues61@daum.net)
```
