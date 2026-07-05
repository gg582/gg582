# Open Source Developer - @gg582

Linux 시스템 프로그래밍, 고성능 네트워크 터널링, TUI(Text User Interface) 및 미니멀 도구 개발에 집중하고 있는 오픈소스 메인테이너 및 기여자입니다. **Cubrid** 및 **Gosuda** 오픈소스 커뮤니티의 일원으로 활동하고 있습니다.

---

## 🏛️ Organizations & Commits

### [Cubrid](https://github.com/CUBRID) (Member)
- 엔터프라이즈급 오픈소스 RDBMS 생태계에 참여하며 오픈소스 데이터베이스 기술과 다중 클라이언트 결합 환경 분석.

### [Gosuda](https://github.com/gosuda) (Member / Co-maintainer)
- 터미널 환경의 경량 인프라, 암호학, 고성능 네트워크 중계기 등을 공동 유지보수 및 릴리즈.

---

## 🛠️ Main Open Source Projects

### 📡 [Portal](https://github.com/gosuda/portal-tunnel) (Gosuda)
**Self-Hostable Relay Tunnel for Localhost**
- **소개**: 포트 포워딩, 방화벽 규칙 설정 없이 로컬 호스트 서비스를 외부(에이전트 웹 등)에 노출시켜주는 신뢰가 필요 없는(Trustless) 고성능 중계 터널 엔진.
- **핵심 기술**:
  - **E2E Tenant TLS & ECH**: 중계 서버가 원시 데이터를 복호화할 수 없도록 사용자 엔드포인트에서 직접 TLS를 종단하며, ECH(Encrypted Client Hello)를 적용해 SNI 노출 방지.
  - **MITM 감지**: TLS keying material(Exporter)을 양단에서 비교하여 중간자 공격 및 중계기 측 복호화 시도를 무력화하는 자가 검증 프로브 내장.
  - **Multi-Hop Relay**: 3개 이상의 릴레이 노드를 체이닝하여 노드당 송수신자 정보를 은닉하는 익명 라우팅 구조 구현.
  - **x402 Sui USDC Payment**: API 호출 시 Sui 블록체인을 통한 USDC 결제를 요구할 수 있는 게이트웨이 제공.
- **사용법**:
  ```bash
  # 1. 설치 (macOS / Linux)
  curl -fsSL https://github.com/gosuda/portal-tunnel/releases/latest/download/install.sh | bash
  
  # 2. 로컬 포트 외부 공개 (기본 임의 public 도메인 제공)
  portal expose 3000
  
  # 3. 커스텀 릴레이 서버 지정 노출
  portal expose 3000 --name myapp --relays https://portal.example.com --discovery=false
  
  # 4. 멀티홉(익명 라우팅) 활성화
  portal expose 3000 --multi-hop-depth 3
  ```

### 🌐 [CWIST](https://github.com/religiya-serdtsa/cwist) (Maintainer)
**Pure C Web Development Suite (Flask alternative for C)**
- **소개**: "C언어용 Flask"를 목표로 구축된 직관적이고 가벼운 C 전용 웹 개발 스위트. BoringSSL, OpenSSL, lsquic 등을 기반으로 다중 프로토콜을 안전하고 제어 가능하게 제공합니다.
- **핵심 기술**:
  - **HTTP/3 & WebTransport 지원**: lsquic 라이브러리를 바인딩하여 QUIC 및 양방향/단방향 스트림을 다루는 고성능 서버 사이드 WebTransport 세션 탑재.
  - **Post-Quantum TLS**: `cwist_app_use_pqc_layer(app, true)`를 호출해 하이브리드 X25519MLKEM768을 강제하고 레거시 TLS를 배제하는 간결한 보안 설정 지원.
  - **Zero-copy Reactor**: io_uring / epoll / kqueue 기반의 C100K 리액터 및 lock-free 큐 구성.
- **사용법**:
  ```c
  #include <cwist/app.h>

  static void hello(cwist_http_request *req, cwist_http_response *res) {
      (void)req;
      cwist_sstring_assign(res->body, "Hello from CWIST!");
  }

  int main(void) {
      cwist_app *app = cwist_app_create();
      cwist_app_use_db(app, ":memory:");
      cwist_app_use_pqc_layer(app, true);
      cwist_app_get(app, "/", hello);
      cwist_app_listen(app, 8080);
      cwist_app_destroy(app);
      return 0;
  }
  ```

### 💾 [LibTTAK](https://github.com/religiya-serdtsa/libttak) (Maintainer)
**Predictable & Safe Custom Memory Allocator & Concurrency Runtime for C**
- **소개**: 장시간 가동되는 C 애플리케이션의 고질적 한계(힙 파편화, 스레드 간 할당자 경합 등)를 방지하기 위해 생성된 결정론적 메모리 제어 프레임워크 및 동시성 런타임.
- **핵심 기술**:
  - **Generational Arena**: 힙 파편화를 극복하고 대규모 할당 단위를 생명주기(Generation) 경계로 일시에 정리하는 아레나 시스템.
  - **Epoch Reclamation (EBR)**: global pause가 발생하지 않는 스레드 안전 비차단(lock-free) 메모리 회수 레이어.
  - **동시성 모델**: 태스크 스레드 풀 및 Future / Promise 비동기 프리미티브 구현.

### 💬 [SSH-Chatter](https://github.com/gosuda/ssh-chatter) (Gosuda)
**Modern C-Based SSH Chat Server & BBS Terminal**
- **소개**: Go 언어의 `ssh-chat`을 C 언어로 포팅 및 확장한 모던 C 기반 SSH/Telnet BBS 채팅 서버. 90년대 레트로 감성의 뷰를 제공하면서 내부적으로는 현대적인 보안 및 확장 프레임워크를 갖추고 있습니다.
- **핵심 기술**:
  - **BBS 및 다양한 TUI 명령어**: 내부적으로 `/bbs` 명령을 통한 게시판(정렬 및 검색 지원), `/rss` 리더기, `/asciiart` 캔버스 등을 모듈식 구조로 구현.
  - **AI Moderation & Security**: Gemini API 및 로컬 Ollama 백엔드를 활용한 자동 유해물 필터링 파이프라인.
  - **네트워킹 & 모스 릴레이**: Binkp 프로토콜 사양 기반의 아마추어 햄 라디오 연동 기능 제공.
  - **메모리 최적화**: 내부 커스텀 Epoch GC(`sshc_epoch_reclaim`) 및 메모리 관리 기법 활용.
- **사용법**:
  ```bash
  # 1. 빌드 (POSIX 환경에서 make 구동)
  make
  
  # 2. 실행 (포트, 호스트 키 경로 등 설정하여 데몬 실행)
  ./ssh-chatter -a 0.0.0.0 -p 2222 -k ./host_keys
  
  # 3. 사용자 SSH 접속
  ssh nickname@your-ip -p 2222
  ```

### 📝 [Nanox](https://github.com/gg582/nanox) (Maintainer)
**UEmacs/PK Modernization & Minimalist Terminal Text Editor**
- **소개**: 고전 텍스트 에디터인 MicroEmacs(UEmacs)를 현대적 원격 환경에 맞추어 Refactoring 및 최적화한 초경량 터미널 에디터.
- **핵심 기술**:
  - **Legacy C Refactoring**: 스파게티 형태의 레거시 구조(God Architecture)를 모듈화 및 재구성.
  - **ncursesw 현대화**: 유니코드(UTF-8) 지원 및 현대식 터미널 환경에 맞는 다중 뷰 관리 개선.
  - **보안 기능 강화**: 설정 변수 `$confirmshell` 및 `$makebackup` 도입을 통한 에디터 내 쉘 명령어 실행 안전 장치 제공.

### 🔌 [Gozik](https://github.com/gosuda/gozik) (Gosuda)
**FFMPEG-Based Minimalist GTK Audio / CD Player**
- **소개**: 로컬 음악 파일 재생부터 스트리밍 플러그인을 통한 음원 재생까지 지원하는 미니멀리스트 오디오 재생 데몬 및 클라이언트.
- **핵심 기술**:
  - **gRPC 아키텍처**: 재생을 담당하는 경량 Go 백엔드 데몬과 UI 레이어를 격리.
  - **스트리밍 확장성**: YouTube Music 등 외부 소스를 가져오는 확장 플러그인(gozik-yt-music) 지원.

---

## 📬 Contact
- **Email**: gg582@proton.me
- **GitHub**: [@gg582](https://github.com/gg582)
