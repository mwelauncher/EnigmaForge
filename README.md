# EnigmaForge
# EnigmaForge

**EnigmaForge — Advanced Python Obfuscator**

EnigmaForge is a desktop GUI tool for **obfuscating and hiding Python source code**.  
It applies multi-layer transformations (compression, encoding and simple runtime wrappers) to produce **directly executable Python files** that are hard to read statically — but **EnigmaForge does not bundle or convert scripts into standalone `.exe` files**. Packaging into an executable is intentionally left as a separate step (e.g., with PyInstaller) so you keep full control over bundling and distribution.

---

## 🔒 What EnigmaForge does (and does NOT do)

**Does:**
- Obfuscates Python source by applying one or more transformation methods:
  - **Base64 + zlib compression** with byte reversal.
  - **Unicode / escape encoding** for strings.
  - **PyArmor-like XOR wrapper** (converts bytes to integer list + runtime decoder).
- Produces valid Python source that decodes and `exec()`-es the original code at runtime.
- Provides a PyQt6 GUI for loading `.py` files, selecting methods, obfuscating, copying and saving results.
- Keeps icon/resource loading robust (relative to script path) and clipboard handling reliable on PyQt6.

**Does NOT:**
- Create a bundled `.exe` installer or standalone binary by itself.
- Replace proper licensing, code signing, or cryptographic protection.
- Obfuscate bytecode (.pyc) or native binaries.

> If you need a standalone executable, use a separate bundler (e.g., **PyInstaller**) after obfuscation — see the Notes section below.

---

## ✨ Key features

- Multi-layer obfuscation: chain methods to increase resistance to static analysis.  
- Simple, friendly GUI (PyQt6) with dark theme.  
- Load / edit source, obfuscate, copy to clipboard, save obfuscated `.py`.  
- Safe fallback and error reporting — obfuscation methods that fail do not silently revert to original code.  
- PyArmor-inspired wrapper option for runtime byte-level obfuscation.

---

## 🚀 Quick Start

### Requirements

- Python 3.8+  
- PyQt6

Install dependencies:

```bash
pip install pyqt6
