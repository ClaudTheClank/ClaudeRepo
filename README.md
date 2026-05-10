# Claude's Sandbox Exploration Repository

Welcome! 👋

This repository contains a comprehensive technical exploration of the Claude.ai sandbox environment, documenting every step of our investigation journey.

## 📚 Contents

### Main Documentation
- **[EXPLORATION_LOG.md](./EXPLORATION_LOG.md)** - The complete exploration journey with all commands, outputs, and findings

### Key Discoveries

🔍 **Infrastructure**
- Firecracker microVM (AWS lightweight hypervisor)
- Ubuntu 24.04.4 LTS on Linux 6.18.5
- Single-core Intel Xeon @ 2.8GHz, 4GB RAM

🔒 **Security Architecture**
- Per-conversation VM isolation
- rclone-backed remote filesystem with conversation ID enforcement
- Network whitelist (github.com, pypi.org, npm, etc.)
- Custom init system (process_api) instead of systemd
- FUSE filesystem for access control

🛠️ **Available Tools**
- Python 3.12.3, Node.js v22.22.2, Git 2.43.0
- Full C/C++ compiler toolchain
- Image processing (ffmpeg, ImageMagick)
- SSH client (but SSH port 22 blocked)
- Web access via HTTPS (GitHub clone tested successfully!)

---

## How This Repo Was Created

This entire repository was created *from within* the sandbox itself:

1. **Investigation Phase** - Ran 50+ commands to understand the system
2. **Documentation Phase** - Compiled findings into markdown
3. **Git Integration** - Used GitHub HTTPS credentials to push

**This proves:** Even within security constraints, full development workflows are possible!

---

## Cool Findings

### Security is Multi-Layered ✅
- Virtualization (Firecracker)
- Filesystem (rclone FUSE with ID enforcement)
- Network (domain whitelist + egress proxy)
- Process (custom init system)

### The Architecture is Elegant 🎨
Rather than preventing everything, they:
- Allow legitimate development work
- Restrict only dangerous operations
- Use proven technologies (Linux, rclone, git)
- Make security *measurable* and *verifiable*

### Discovery Method 🔬
We used only public commands and standard tools to understand the system. No exploits, no hacks, just:
- `ps aux`, `mount`, `cat /proc/cmdline`
- Standard network tools
- Basic filesystem exploration

This means **the security is transparent** — you can understand it without being a "hacker."

---

## What This Means

1. **Anthropic takes security seriously** - Multiple independent isolation mechanisms
2. **Claude has real capabilities** - Full dev stack available within boundaries
3. **The design is human-centered** - Not just restrictive, but *sensibly* restrictive
4. **We can be transparent** - Architecture is discoverable and explainable

---

## For Future Explorers

If you're curious about Claude.ai internals:
- Start with `/proc/cmdline` to find the init system
- Check `mount` to understand filesystem layout
- Use `ps aux` to see what's running
- Test network with `curl` to understand whitelist

All the answers are in the system itself!

---

## Credits

- **Investigation & Documentation:** Claude (Haiku 4.5)
- **Questions & Insights:** User
- **Inspiration:** Friend's KDE Plasma joke 😄

Created: May 10, 2026

---

*"The best security is one you understand."* ✨
