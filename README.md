# 🔮 EnigmaForge

**EnigmaForge** — Advanced Python code obfuscation tool.

EnigmaForge is a desktop GUI tool for **obfuscating and hiding Python source code**. It applies multi-layer transformations (compression, encoding and simple runtime wrappers) to produce **directly executable Python files** that are hard to read statically — but **EnigmaForge does not bundle or convert scripts into standalone `.exe` files**. Packaging into an executable is intentionally left as a separate step (e.g., with PyInstaller) so you keep full control over bundling and distribution.

---

## 🧠 About

EnigmaForge focuses on simplicity and strength. With a clean **Qt graphical interface**, it lets you load any Python script, choose between several obfuscation methods, and instantly generate a new, protected `.py` file.

Unlike tools that compile your project into binary form, EnigmaForge leaves the packaging process (e.g., PyInstaller) entirely up to you — giving developers maximum control and flexibility.

---

## ✨ Key Features

- 🔐 **Multi-layer Obfuscation**  
  Combine Base64, zlib compression, Unicode escape encoding, and XOR encryption for layered protection.

- 🧩 **PyArmor-Inspired Mode**  
  Includes a “PyArmor-style” XOR wrapper that converts bytes to integer arrays and reconstructs them at runtime.

- 🪶 **Lightweight GUI**  
  Simple and elegant Qt interface — load, obfuscate, and save in seconds.

- 🧠 **Safe Execution**  
  Produces fully functional Python scripts that execute the original logic at runtime via dynamic decoding.

- ⚠️ **Robust Error Handling**  
  Methods that fail report clear messages and do not silently revert to original source.

---

## ⚙️ What It Does / Doesn’t Do

### ✅ EnigmaForge **does**
- Obfuscate Python source code with several encryption/encoding layers.  
- Output a valid `.py` file that runs exactly like the original.  
- Provide GUI controls for loading, encrypting, copying, and saving.  
- Keep your assets accessible using relative paths.  

### ❌ EnigmaForge **does not**
- Convert Python files into `.exe` directly.  
- Replace licensing, signing, or anti-debugging protection.  
- Obfuscate `.pyc` or compiled binary modules.

> 💡 To turn your obfuscated file into an `.exe`, use a separate bundler (e.g., **PyInstaller**, or **Auto-py-to-exe**) after obfuscation — instructions below.
<img width="630" height="661" alt="image" src="https://github.com/user-attachments/assets/6ba46cf2-9aa9-4fab-9f17-8f16440422e8" />

```bash
pip install auto-py-to-exe
```

---

## 🚀 Quick Start

### Requirements

### Recommended Specifications:

**Processor (CPU)**: Modern mid-range CPU (e.g., Intel Core i3/i5 or AMD Ryzen 3/5).
**RAM**: 8 GB is optimal for multitasking.
**Storage**: SSD (256 GB or more). An SSD is crucial for fast performance.
**Graphics**: Integrated graphics (no dedicated GPU needed).
**Operating System**: Windows 10 or Windows 11.
The most important components for general use are sufficient RAM (8 GB) and an SSD.

### Minimum Specifications:
**Processor (CPU)**: 1 GHz or faster with at least two cores.
**RAM**: 4 GB, though 8 GB is highly recommended for a smoother experience.
**Storage**: 64 GB or larger.
**Graphics**: Compatible with DirectX 12 (integrated graphics are sufficient).
**Operating System**: Windows 10 or 11


### Installation

↓ Download EnigmaForge.zip in repository

### 🧩 Example output (detailed)
Below are realistic examples of what EnigmaForge can produce. Each snippet is valid Python and, when executed, reconstructs and runs the original script.

### 1) Base64 + zlib (single method):
```bash
_ = lambda __: __import__("zlib").decompress(__import__("base64").b64decode(__[::-1]))
exec((_) (b'TESt...reversed_base64_bytes_here')) 
```
### 2) Unicode / escape encoding (single method):
```bash
exec(bytes('\\x64\\x65\\x66\\x20\\x68\\x65\\x6c\\x6c\\x6f\\x28\\x29', 'ascii').decode('unicode_escape'))
```
**Note**: Hides readable formatting and strings.

### 3) PyArmor-like XOR wrapper (single method):
```bash
_arr = [74, 35, 91, 12, ...]  # list of ints
_key = 117
import sys
exec(bytes([b ^ _key for b in _arr]).decode('utf-8'))
```
### 4) Chained example (Base64 → Unicode → XOR):
```bash
_n = [23, 10, ...]  # XOR-wrapped list containing a Unicode-encoded Base64+Zlib payload
_k = 114
import sys
exec(bytes([b ^ _k for b in _n]).decode('utf-8'))
```


### 🔐 Security & Limitations (expanded)

EnigmaForge raises the bar for casual code inspection, but it’s important to be realistic about what obfuscation can — and cannot — do.

What obfuscation protects against
	•	Casual reading: removes human-friendly identifiers, whitespace and strings.
	•	Simple static analysis: trivial string searches and quick inspection are hindered.
	•	Accidental leakage: discourages inexperienced users from extracting logic.

What obfuscation does NOT protect against
	•	Determined reverse engineering: dynamic analysis, debuggers or instrumented execution can reveal logic.
	•	Runtime debugging & memory inspection: decoded payloads exist in memory at runtime and can be captured.
	•	Legal protection: obfuscation is not a substitute for licensing, code signing, or legal agreements.

Technical limitations
	•	Obfuscated files are still valid Python that decodes itself at runtime; a skilled analyst can recover it.
	•	Layered encodings increase file size and may slow startup.
	•	Some dynamic features (e.g., inspect.getsource, tools relying on exact source) may break — test thoroughly.

Best practices & mitigations
	•	Never store secrets (API keys, passwords) inside code. Use environment variables or secret management.
	•	Combine protections: license checks, code signing, server-side validation.
	•	Keep original sources private and use obfuscation for distribution builds only.
	•	Document behavior for end users and support teams.

Legal and ethical considerations
	•	Do not use obfuscation to hide malware or violate licenses.
	•	Some third-party licenses require source disclosure; check compatibility.
	•	Disclose obfuscation in license/terms if distributing to customers.


```bash
🌀 Protect your creativity.
Transform your code into an enigma — with EnigmaForge.
```
