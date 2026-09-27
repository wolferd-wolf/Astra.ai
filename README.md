# Aura — Edge LLM Studio

<p align="center">
  <img src="preview.png" alt="Aura Studio Banner" width="100%" style="border-radius: 12px; margin-bottom: 16px;" onerror="this.style.display='none'" />
</p>

<p align="center">
  <strong>Private, on-device AI workspace running sub-1B models directly inside your browser.</strong><br>
  Zero server latency • Zero cloud telemetry • Powered by WebGPU & Transformers.js v3
</p>

<p align="center">
  <a href="https://github.com"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square" alt="License"></a>
  <img src="https://img.shields.io/badge/Execution-Client--Side%20WebGPU%20%2F%20WASM-emerald?style=flat-square" alt="WebGPU Ready">
  <img src="https://img.shields.io/badge/Zero%20Config-Single%20File-orange?style=flat-square" alt="Single File">
  <img src="https://img.shields.io/badge/PRs-Welcome-brightgreen?style=flat-square" alt="PRs Welcome">
</p>

---

## Highlights

- **100% Client-Side Privacy**: All weights and tokens reside exclusively in your browser tab. No prompts or files are ever transmitted to a remote server.
- **Hardware Acceleration**: Automatic WebGPU adapter probing for sub-second token delivery on modern GPUs, with graceful fallback to multi-threaded CPU WASM.
- **Editorial Anti-Slop Interface**: Warm typography (`Newsreader` serif, `Plus Jakarta Sans`, and `JetBrains Mono`) inspired by Claude.ai, with no neon gradients or visual clutter.
- **Micro-Animations (React Bits inspired)**:
  - **Point Square Matrix**: 9-dot pulsing loader and micro-cursor that tracks token generation.
  - **ShinyText**: Shimmer sweep across headlines.
  - **BlurText & DecryptedText**: Smooth text reveal and model selection scrambles.
  - **ClickSpark**: Interactive physics particle burst on primary actions.
- **Local Tooling**: In-memory file and code inspections (`.js`, `.ts`, `.py`, `.json`, etc.), Web Speech API voice dictation, full parameter tuning (Temperature, Max Tokens, System Persona), session search, and Markdown exports.
- **Persistent Cache**: 4-bit ONNX weights are cached via the browser's `CacheStorage` / `IndexedDB`, meaning subsequent loads require **0 KB of network data**.

---

## Supported Models

Aura runs quantized sub-1B parameter models tailored for edge execution:

| Model | Parameters | Quantization | Download Size | Best For |
| :--- | :--- | :--- | :--- | :--- |
| **SmolLM2-135M-Instruct** | 135M | Q4 ONNX | ~90 MB | Instant startup, ultra-light mobile devices, rapid code reasoning |
| **SmolLM2-360M-Instruct** | 360M | Q4 ONNX | ~230 MB | Multi-turn conversational depth and instruction following |
| **Qwen2.5-0.5B-Instruct** | 490M | Q4 ONNX | ~350 MB | Multi-lingual tasks, syntax generation, and complex structured reasoning |

---

## Quick Start

### 1. Run Locally (No Installation Required)

Because Aura is a self-contained single-page application, you do not need Node.js, Docker, or Python to test it:

```bash
# Clone the repository
git clone https://github.com/<your-username>/aura-studio.git
cd aura-studio

# Open index.html directly in any modern browser
open index.html        # macOS
xdg-open index.html   # Linux
start index.html      # Windows
```

*Tip: For testing on local network devices, you can serve the directory using Python:*
```bash
python3 -m http.server 8080
```

---

### 2. Deploy to GitHub Pages in 60 Seconds

1. Go to your repository on **GitHub**.
2. Navigate to **Settings** $\rightarrow$ **Pages** (under the "Code and automation" section).
3. Under **Build and deployment**:
   - **Source**: `Deploy from a branch`
   - **Branch**: `main` (or `master`)
   - **Folder**: `/ (root)`
4. Click **Save**.
5. Your studio will be live in 1–2 minutes at:
   ```text
   https://<your-username>.github.io/<your-repo-name>/
   ```

> **Note on HTTPS:** GitHub Pages serves content over HTTPS by default, which is a mandatory browser security requirement for accessing `navigator.gpu` (WebGPU) and `window.SpeechRecognition`.

---

## Browser Support Matrix

| Platform / Browser | WebGPU Acceleration | WASM CPU Fallback | Voice Dictation |
| :--- | :---: | :---: | :---: |
| **Chrome / Chromium (v113+)** | Full (FP16 / INT4) | Supported | Supported |
| **Edge (v113+)** | Full (FP16 / INT4) | Supported | Supported |
| **Brave** | Supported | Supported | Supported |
| **Safari (v18+)** | Partial / Flags | Supported | Supported |
| **Firefox Nightly** | Flag required | Supported | Partial |
| **Android Chrome** | Supported on newer devices | Supported | Supported |
| **iOS Safari** | WASM fallback | Supported | Supported |

---

## Repository Structure

```text
├── index.html            # Complete, self-contained single-file application
├── manifest.json         # PWA manifest for Add-to-Home-Screen on mobile/desktop
├── .nojekyll             # Bypasses Jekyll build processing on GitHub Pages
├── preview.png           # (Optional) Social sharing banner for OpenGraph cards
├── LICENSE               # Open-source license (MIT)
└── README.md             # Project documentation and guides
```

---

## Contributing

Contributions are welcome! If you would like to contribute:
1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/model-quant-options`).
3. Commit your changes (`git commit -m 'feat: add support for INT8 quantization'`).
4. Push to the branch (`git push origin feature/model-quant-options`).
5. Open a Pull Request.

---

## License

Distributed under the **MIT License**. See `LICENSE` for more information.
