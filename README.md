# 안녕하세요, 이윤진(@gg582)입니다

Linux, 네트워킹, 컨테이너 기반 인프라를 중심으로 작업하는 시스템 레벨 개발자입니다.  
C와 Go를 활용하여 로우레벨 시스템, 재현 가능한 환경, 성능 중심 도구를 개발해왔습니다.

현재 인턴십을 통해 레거시 Java 환경(OpenJDK 8)을 다루고 있으며, 커널 레벨 최적화와 인프라 설계에 지속적인 관심을 가지고 있습니다.

*메타빌드 인턴십 (2026.03.03 - 2026.06.02)*

## 주요 프로젝트

- **IncuSpeed** — 재현 가능한 컨테이너 환경 관리 도구 (Python + Go + Incus)  
  → 실제 배포 및 테스트 환경을 구성하고 운영한 경험

- **Linux-Mountain** — Linux 커널 및 네트워크 지연 최적화 (BBR, ECMP, NAPI)  
  → 커널 및 네트워크 레벨에서의 성능 분석 및 튜닝 경험

- **DevOpsPlayground** — Kubernetes 클러스터 및 서비스 구성 자동화 (Helm, Ansible)  
  → IaC 기반 인프라 구축 및 자동화 경험

## 기술 스택

- Go
- Cloud Computing
- Linux
- FreeBSD
- C/C++
- RIOT OS
- Software Optimization
- Java

## 인턴십 수행 내용

| 난이도 | 주요 내용 | 기술 스택 |
| :--- | :--- | :--- |
| **기초** | 레거시 환경 분석 | OpenJDK 8, PostgreSQL 9.6 |
| **중급** | JDK 마이그레이션 | JDK 1.6, 1.8 → 21 |
| **고급** | 시스템 분석 및 설계 | Apache Tika, 서버 관리, 디자인 패턴 |
| **실제 수행** | 기초, 고급(95%), 중급(50%) | 서버 구축, 레거시 코드 분석, 디자인 패턴 적용, Apache Tika |

```diff
! 경험: JDK 1.6 ~ 1.8 ~ 21 환경 전반에서 개발 및 레거시 시스템 대응 경험
+ 강점: 시스템 동작을 명시적으로 제어하고 레거시 환경과의 높은 호환성 확보
- 한계: 레거시 코드 특성상 구조가 깊고 코드가 장황해지는 경향
! 인사이트: 레거시 시스템 개선은 유지보수성, 호환성, 현대화 사이의 균형이 핵심
````

```bash
~ $ #################>== [90% Done]
```

---

# 이력

* 2021-2022 대구대학교 **MoNet**
* 2022-2023 대구대학교 RESL
* 2023-2025 졸업 프로젝트 준비 (IncuSpeed)
* 2025 정보처리기사 취득 (하나 소셜벤처 대학)
* 2026.03.03 - 2026.06.02 메타빌드 인턴십
* 2026-06 ~ (진행 예정)

## 관심 분야

* Linux 시스템 및 네트워크

  * 커널 레벨 튜닝
* 자동화 / IaC (Ansible, Helm, Kubernetes)
* Go 기반 서비스 (데몬, CLI, 웹)
* C 프로그래밍

  * 레거시 리팩토링
  * 시스템 최적화
  * 경량 웹 백엔드

```c
/*
 * 분기 예측 지연을 최소화하기 위한 계층형 실행 흐름
 * IEEE 754 NaN 영역을 활용한 포인터 태깅 기반 순수 C 로직
 */
#define BIGINT_TAG_MASK 0xFFF8000000000000ULL
#define EXPONENT_MASK   0x7FF0000000000000ULL

uint64_t next_step(uint64_t n) {
    if (!(n & 0xC000000000000000ULL)) {
        return n << 1;
    }

    if (((n ^ BIGINT_TAG_MASK) & BIGINT_TAG_MASK) == 0) {
        return bigint_mul2(n);
    }

    uint64_t exp_inc = n + (1ULL << 52);
    if ((exp_inc & EXPONENT_MASK) != EXPONENT_MASK) {
        return exp_inc;
    }

    return promote_to_bigint_and_mul2(n);
}
```

## 주요 프로젝트 상세

### 인턴십 프로젝트

* Java 1.8 기반 레거시 시스템 → 최신 Spring Boot 4.x 구조로 전환

* 기반: Spring + MyBatis + Legacy PostgreSQL 환경

* 기술 스택: Java, Maven, Spring Boot, MyBatis, Apache Tika, PostgreSQL, BouncyCastle, JPA

* 강점:

  * 명시적인 코드 구조
  * 파일 단위로 분리된 작은 코드 크기

* 한계:

  * 장황한 코드 구조
  * 깊은 디렉토리 구조
  * 서비스 요구사항이 저장소 단위로 분산됨

레거시 Java 환경(1.6~1.8)을 다루며 호환성과 유지보수라는 현실적인 제약을 경험했습니다.
레거시 아키텍처 개선은 코드 경로, 데이터 흐름, 시스템 동작에 대한 구조적 분석을 기반으로 이루어져야 하며,
측정 가능한 지표를 기반으로 한 점진적 개선이 필수적입니다.

또한, 느슨한 구조와 과도한 코드 길이는 인지 비용을 증가시키고 유지보수를 어렵게 만들기 때문에
구조적 리팩토링은 장기적인 시스템 개선에 핵심 요소임을 확인했습니다.

---

### 1. 인프라 / 엣지 컴퓨팅

#### DevOpsPlayground

* Kubernetes 환경 자동 구성 도구 (Helm, Ansible, Shell)
* 강점: 재현 가능한 환경 구성
* 한계: ACME 포트 포워딩 및 도메인 설정 가이드 부족

#### IncuSpeed

* Incus 기반 컨테이너 관리 도구 (Python GUI + Go 데몬)
* 강점: 재현 가능한 컨테이너 이미지 환경
* 한계: 일부 기능은 Docker Compose로 대체 가능

#### RemoteCarFromMonet

* Kubernetes 기반 원격 차량 제어 시스템
* 강점: 물리 장치 제어 + 분산 시스템 통합
* 한계: 내부 자료 외부 공개 불가

---

### 2. 시스템 최적화

#### LibTTAK

* C 기반 메모리 모델
* 강점: 예측 가능한 RSS 및 결정적 GC
* 한계: 독립적인 생태계

#### Linux-Mountain

* 커널 및 네트워크 튜닝
* 강점: 표준 커널과 높은 호환성
* 한계: 멀티노드 환경에서 패턴 변동성 존재

#### RIOTOSMiniCarImplementation

* 규칙 기반 자율 주행 차량
* 강점: GPIO 제어 및 독창적 이동 방식
* 한계: 학습 기능 없음

#### Raspberry Pi Raspbot

* 라즈베리파이 디바이스 드라이버
* 강점: IOCTL 기반 인터페이스 단순화
* 한계: 고급 ML 기능 부재

---

```diff
+ 아래 프로젝트는 실험적 시스템 설계 및 저수준 제어에 초점을 둔 작업입니다.
```

#### SSH-Chatter

* SSH 기반 TUI 채팅 서버
* 강점: 레트로 스타일 인터페이스
* 한계: 현대 서비스 적용성 제한

#### AvianRaptorNet

* 초경량 이미지 분류 모델
* 한계: 검증 부족

#### Margo

* 자체 C 언어 확장
* 한계: 생태계 제한

#### ChoiCrypt

* AES 변형 암호 알고리즘
* 한계: 실험용

#### CWIST

* C 기반 웹 프레임워크
* 한계: HTTP/2 미지원

#### Baboship / Ceversi / Nanox

* 다양한 실험적 프로젝트 (웹, 게임, TUI 에디터)

---

## 활동 및 자격

### 연구 참여

* ETRI 2건, NRF 4건 참여

### 자격증

* 정보처리기사 취득

---

## 연락처

* [gg582@proton.me](mailto:gg582@proton.me)
* [gzblues61@daum.net](mailto:gzblues61@daum.net)

```
