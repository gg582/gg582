# Open Source Developer - @gg582

I am an open-source maintainer and contributor focusing on Linux system programming, high-performance network tunneling, Text User Interface (TUI), and minimalist tool development. I am active as a member of the **Cubrid** and **Gosuda** open-source communities.

---

## 🏛️ Organizations & Commits

### [Cubrid](https://github.com/CUBRID) (Member)
- Participate in the enterprise-grade open-source RDBMS ecosystem, analyzing open-source database technologies and multi-client integration environments.

### [Gosuda](https://github.com/gosuda) (Member / Co-maintainer)
- Co-maintain and release lightweight terminal infrastructure, cryptography, and high-performance network relays.

---

## 🛠️ Main Open Source Projects

### 📡 [Portal](https://github.com/gosuda/portal-tunnel) (Gosuda-Tunnel)
**Self-Hostable Relay Tunnel for Localhost**
- **Introduction**: A trustless, high-performance relay tunnel engine that exposes localhost services to the public (e.g., agent web) without port forwarding or configuring firewall rules.
- **Key Technologies**:
  - **E2E Tenant TLS & ECH**: Terminates TLS directly at the user endpoint so the relay server cannot decrypt the raw data, and applies ECH (Encrypted Client Hello) to prevent SNI exposure.
  - **MITM Detection**: Includes a self-verifying probe that compares TLS keying material (Exporter) on both ends to defeat man-in-the-middle attacks and relay-side decryption attempts.
  - **Multi-Hop Relay**: Implements an anonymous routing structure that chains three or more relay nodes to hide sender and receiver information per node.
  - **x402 Sui USDC Payment**: Provides a gateway that can require USDC payment via the Sui blockchain when making API calls.
- **Usage**:
  ```bash
  # 1. Install (macOS / Linux)
  curl -fsSL https://github.com/gosuda/portal-tunnel/releases/latest/download/install.sh | bash
  
  # 2. Expose local port to the public (provides a random public domain by default)
  portal expose 3000
  
  # 3. Expose via a custom relay server
  portal expose 3000 --name myapp --relays https://portal.example.com --discovery=false
  
  # 4. Enable multi-hop (anonymous routing)
  portal expose 3000 --multi-hop-depth 3
  ```

### 🌐 [CWIST](https://github.com/religiya-serdtsa/cwist) (Maintainer)
**Pure C Web Development Suite (Flask alternative for C)**
- **Introduction**: An intuitive, lightweight web development suite for pure C, aiming to be a "Flask for C". It provides multi-protocol support securely and manageably based on BoringSSL, OpenSSL, lsquic, etc.
- **Key Technologies**:
  - **HTTP/3 & WebTransport Support**: Binds the lsquic library to implement a high-performance server-side WebTransport session handling QUIC and bidirectional/unidirectional streams.
  - **Post-Quantum TLS**: Supports clean security configurations that force hybrid X25519MLKEM768 and exclude legacy TLS by calling `cwist_app_use_pqc_layer(app, true)`.
  - **Zero-copy Reactor**: Configures C100K reactor and lock-free queues based on io_uring / epoll / kqueue.
- **Usage**:
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
- **Introduction**: A deterministic memory control framework and concurrency runtime created to prevent common limitations of long-running C applications (e.g., heap fragmentation, allocator contention across threads).
- **Key Technologies**:
  - **Generational Arena**: An arena system that overcomes heap fragmentation and cleans up large allocation blocks at once using Generation boundaries.
  - **Epoch Reclamation (EBR)**: A thread-safe, lock-free memory reclamation layer without global pauses.
  - **Concurrency Model**: Implements task thread pools and async primitives like Future / Promise.

### 💬 [SSH-Chatter](https://github.com/gosuda/ssh-chatter) (Gosuda)
**Modern C-Based SSH Chat Server & BBS Terminal**
- **Introduction**: A modern C-based SSH/Telnet BBS chat server ported and extended from Go's `ssh-chat` to C. It offers a 90s retro-style view while internally incorporating a modern security and extension framework.
- **Key Technologies**:
  - **BBS and various TUI commands**: Internally implements modular structures such as a BBS (/bbs command supporting sorting and search), RSS reader (/rss), and ASCII art canvas (/asciiart).
  - **AI Moderation & Security**: An automated toxic content filtering pipeline utilizing the Gemini API and local Ollama backends.
  - **Networking & Morse Relay**: Provides amateur HAM radio integration based on the Binkp protocol specification.
  - **Memory Optimization**: Employs an internal custom Epoch GC (`sshc_epoch_reclaim`) and memory management techniques.
- **Usage**:
  ```bash
  # 1. Build (runs make in a POSIX environment)
  make
  
  # 2. Run (starts the daemon with port, host key path, etc.)
  ./ssh-chatter -a 0.0.0.0 -p 2222 -k ./host_keys
  
  # 3. Connect via SSH
  ssh nickname@your-ip -p 2222
  ```

### 📝 [Nanox](https://github.com/gg582/nanox) (Maintainer)
**UEmacs/PK Modernization & Minimalist Terminal Text Editor**
- **Introduction**: An ultra-lightweight terminal editor refactored and optimized for modern remote environments, based on the classic text editor MicroEmacs (UEmacs).
- **Key Technologies**:
  - **Legacy C Refactoring**: Modularizes and restructures the spaghetti-like legacy codebase (God Architecture).
  - **ncursesw Modernization**: Improves unicode (UTF-8) support and multiple view management tailored for modern terminal environments.
  - **Enhanced Security**: Introduces safety measures for running shell commands within the editor via configuration variables `$confirmshell` and `$makebackup`.

### 🔌 [Gozik](https://github.com/gosuda/gozik) (Gosuda)
**FFMPEG-Based Minimalist GTK Audio / CD Player**
- **Introduction**: A minimalist audio playback daemon and client that supports playing local music files as well as audio streams via streaming plugins.
- **Key Technologies**:
  - **gRPC Architecture**: Isolates the lightweight Go backend daemon responsible for playback from the UI layer.
  - **Streaming Extensibility**: Supports extension plugins (such as `gozik-yt-music`) to fetch external sources like YouTube Music.

---

## 📬 Contact
- **Email**: gg582@proton.me
- **GitHub**: [@gg582](https://github.com/gg582)
