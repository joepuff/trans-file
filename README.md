LAN File Transfer V34 (Final Perfect Edition)
局域网互传 V34 [最终完美版]
English | 中文

<a name="english"></a>

🇬🇧 English Documentation
1. Introduction
LAN File Transfer V34 is a serverless, secure, and robust single-page web application designed for peer-to-peer file sharing within a local network (or across the internet via WebRTC). It focuses on transmission stability and security, featuring a "Stop-and-Wait" protocol to prevent packet loss and self-healing mechanisms.

2. Key Features
Serverless P2P: Uses PeerJS (WebRTC) for direct browser-to-browser connection. No intermediate server stores your files.

Robust Transmission Protocol:

Stop-and-Wait ARQ: Splits files into 100 parts and verifies every single part before moving to the next.

Auto-Healing: Automatically retries failed chunks (up to 5 times) to handle unstable network conditions.

Throttling: Built-in delay (THROTTLE_MS) to prevent overwhelming the data channel.

Military-Grade Security:

E2EE (End-to-End Encryption): Uses AES-GCM (256-bit) for payload encryption.

PBKDF2 Key Derivation: Derives 16 separate sub-keys from your 32-character secret to encrypt different file segments.

Secure Handshake: Verifies connection via SHA-256 hash of the key before allowing file transfer.

User Friendly:

Visual Grid: A 25x4 grid shows real-time status of every file chunk (Sending, Waiting, Done, Retry, Error).

QR Code Pairing: Generate and scan QR codes for instant connection between mobile and desktop.

Deep Linking: Support URL hash (#c=KEY) for one-click connection.

3. Technology Stack
Core: HTML5, Vanilla JavaScript.

Networking: WebRTC via PeerJS.

Cryptography: Native Web Crypto API (SubtleCrypto).

Utilities: qrcode.js (Generation), html5-qrcode (Scanning).

4. How to Use
Open the App: Open the index.html file in two different browsers/devices.

Pairing:

Device A: Click the 🎲 button to generate a random 32-character key, then click 🚀 Connect.

Device B: Enter the same key manually OR scan Device A's QR code (click 📱 on A, 📷 on B). Click 🚀 Connect.

Connection: Wait for the status to change to "✅ Secure Channel Established". The drop zone will activate.

Send File: Click the drop zone or drag a file to send.

Yellow blocks: Waiting for receiver confirmation.

Green blocks: Successfully transferred.

Orange/Red blocks: Retrying or failed.

5. Security Note
The application creates a direct tunnel. However, metadata (signaling) passes through the public PeerJS broker.

XSS Protection: The history log uses textContent and safe DOM creation methods to prevent Cross-Site Scripting attacks from malicious filenames.

<a name="chinese"></a>

🇨🇳 中文说明文档
1. 项目简介
局域网互传 V34 [最终完美版] 是一个无后端、高安全性的单页 Web 应用，专为局域网（或广域网）内的点对点文件传输设计。本项目针对 WebRTC 在大数据传输中容易丢包的问题进行了深度优化，实现了类似 TCP 的可靠传输机制。

2. 核心特性
无服务器 P2P：基于 PeerJS (WebRTC) 实现浏览器直连，文件不经过第三方服务器存储。

高可靠传输协议：

停等协议 (Stop-and-Wait)：将文件切分为 100 个分片，每发送一个分片必须收到接收端的 ACK 确认才发送下一个。

自动愈合 (Auto-Healing)：网络波动导致分片校验失败时，自动重试（最多 5 次）。

防拥塞：内置微秒级延时 (THROTTLE_MS)，防止数据通道过载导致的丢包。

军工级安全：

端到端加密 (E2EE)：所有数据载荷均使用 AES-GCM (256-bit) 加密。

动态密钥派生：使用 PBKDF2 算法从 32 位主密钥中派生出 16 组子密钥，轮询加密不同分片。

安全握手：连接建立时通过 SHA-256 哈希校验密钥一致性，杜绝错误连接。

可视化交互：

状态网格：25x4 的像素网格实时展示 100 个分片的传输状态（发送中、等待确认、完成、重试、失败）。

扫码连接：集成二维码生成与扫描功能，手机与电脑互传更便捷。

URL 传参：支持通过 URL Hash (#c=密钥) 分享链接，对方打开即连。

3. 技术栈
核心：HTML5, 原生 JavaScript (无框架依赖)。

网络：WebRTC (通过 PeerJS 库)。

加密：原生 Web Crypto API (SubtleCrypto)，性能极高。

工具库：qrcode.js (生成二维码), html5-qrcode (扫描二维码)。

4. 使用说明
启动：在两台设备（如手机和电脑）上打开 index.html。

配对：

设备 A：点击 🎲 生成 32 位随机密钥，然后点击 🚀 连接（作为 Host）。

设备 B：输入相同的密钥，或者点击 📷 扫描设备 A 的二维码（设备 A 需点击 📱 展示）。点击 🚀 连接。

连接：等待状态栏显示“✅ 安全通道已建立”，此时文件拖放区域会变亮激活。

传输：点击区域选择文件或拖入文件。

黄色块：正在等待接收端校验确认。

绿色块：传输并校验成功。

橙色/红色块：正在重试或传输失败。

5. 安全与优化细节
V34 更新：修复了文件名可能导致的 XSS 漏洞，现在的历史记录渲染采用安全的 DOM 节点创建方式。

信令服务器：使用 PeerJS 官方公共服务器进行握手（仅交换连接元数据，不传输文件内容）。

兼容性：支持 iOS Safari、Android Chrome 及所有现代桌面浏览器。

License / 许可证
MIT License. Free for personal and commercial use.
