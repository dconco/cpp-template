# 🚀 C++ Template Project

<div align="center">

![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![CMake](https://img.shields.io/badge/CMake-064F8C?style=for-the-badge&logo=cmake&logoColor=white)
![Ninja](https://img.shields.io/badge/Ninja-1F2937?style=for-the-badge&logo=ninja&logoColor=white)

_A modern, blazing-fast C++ template project with CMake and Ninja build system_

[📋 Features](#-features) • [🛠️ Setup](#-setup) • [🔧 Building](#-building) • [⚡ Quick Commands](#-quick-commands)

</div>

---

## ✨ Features

-  🏗️ **Modern CMake** configuration
-  ⚡ **Ninja build system** for lightning-fast builds
-  🐛 **Debug & Release** configurations
-  👀 **Auto-rebuild** on file changes
-  🔄 **Multi-core** compilation support
-  📦 **Ready-to-use** project structure

## 🛠️ Setup

### Prerequisites

| Tool              | Ubuntu/Debian                      | macOS                    | Windows                                                          |
| ----------------- | ---------------------------------- | ------------------------ | ---------------------------------------------------------------- |
| **Build Tools**   | `sudo apt install build-essential` | `xcode-select --install` | Visual Studio                                                    |
| **CMake**         | `sudo apt install cmake`           | `brew install cmake`     | [cmake.org](https://cmake.org)                                   |
| **Ninja**         | `sudo apt install ninja-build`     | `brew install ninja`     | [GitHub Releases](https://github.com/ninja-build/ninja/releases) |
| **File Watching** | `sudo apt install inotify-tools`   | Built-in                 | Built-in                                                         |

### Quick Install (Ubuntu/Debian)

```bash
sudo apt update && sudo apt install -y build-essential cmake ninja-build inotify-tools
```

## 🔧 Building

### 📁 Initial Setup

```bash
# Clone your project
git clone https://github.com/dconco/cpp-template.git
cd cpp-template

# Create build directory
mkdir build && cd build
```

### 🏃‍♂️ Build Commands

<details>
<summary><strong>🎯 First Time Build</strong></summary>

```bash
cmake -G Ninja .. && ninja -j$(nproc) && ./app
```

**What this does:**

-  🔧 Configures project with Ninja generator
-  🏗️ Builds using all CPU cores
-  ▶️ Runs your application

_Use this for initial setup or when CMakeLists.txt changes_

</details>

<details>
<summary><strong>⚡ Quick Rebuild</strong></summary>

```bash
ninja -j$(nproc) && ./app
```

**What this does:**

-  🔄 Rebuilds only changed files
-  ▶️ Runs your application

_Fastest option for regular development_

</details>

<details>
<summary><strong>🐛 Debug Build</strong></summary>

```bash
cmake -G Ninja -DCMAKE_BUILD_TYPE=Debug .. && ninja -j$(nproc) && ./app
```

**What this does:**

-  🐛 Enables debug symbols
-  🚫 Disables optimizations
-  🔍 Perfect for debugging with GDB/IDE

</details>

<details>
<summary><strong>🚀 Release Build</strong></summary>

```bash
cmake -G Ninja -DCMAKE_BUILD_TYPE=Release .. && ninja -j$(nproc) && ./app
```

**What this does:**

-  ⚡ Full optimizations enabled
-  📦 Smaller executable size
-  🏎️ Maximum performance

</details>

<details>
<summary><strong>🧹 Clean Build</strong></summary>

```bash
ninja clean && ninja -j$(nproc) && ./app
```

**What this does:**

-  🗑️ Removes all build artifacts
-  🔄 Forces complete rebuild
-  🩹 Fixes corrupted build cache

</details>

<details>
<summary><strong>👀 Watch Mode</strong></summary>

```bash
while inotifywait -e modify,move,create,delete ../src/; do ninja -j$(nproc) && ./app; done
```

**What this does:**

-  👁️ Monitors `src/` directory
-  🔄 Auto-rebuilds on file changes
-  🏃‍♂️ Automatically runs your app

_Perfect for rapid development cycles_

</details>

## ⚡ Quick Commands

Want to make your life easier? Add these aliases to your `~/.bashrc` or `~/.zshrc`:

```bash
# 🛠️ C++ Development Aliases
alias cpp-start="cmake -G Ninja .. && ninja -j\$(nproc) && ./app"
alias cpp-serve="ninja -j\$(nproc) && ./app"
alias cpp-debug="cmake -G Ninja -DCMAKE_BUILD_TYPE=Debug .. && ninja -j\$(nproc) && ./app"
alias cpp-release="cmake -G Ninja -DCMAKE_BUILD_TYPE=Release .. && ninja -j\$(nproc) && ./app"
alias cpp-clean="ninja clean && ninja -j\$(nproc) && ./app"
alias cpp-watch="while inotifywait -e modify,move,create,delete ../src/; do ninja -j\$(nproc) && ./app; done"
```

**Reload your shell:**

```bash
source ~/.bashrc  # or ~/.zshrc
```

**Now you can use:**

-  `cpp-start` → 🎯 Initial build and run
-  `cpp-serve` → ⚡ Quick rebuild and run
-  `cpp-debug` → 🐛 Debug build and run
-  `cpp-release` → 🚀 Optimized build and run
-  `cpp-clean` → 🧹 Clean rebuild and run
-  `cpp-watch` → 👀 Auto-rebuild on changes

## 🎯 Customizing Your Executable

If your executable isn't named `app`, replace `./app` with your actual name:

**Find your executable name in CMakeLists.txt:**

```cmake
add_executable(my-awesome-app src/main.cpp)  # Your exe is "my-awesome-app"
```

**Then use:**

```bash
ninja -j$(nproc) && ./my-awesome-app
```

## 🚨 Troubleshooting

<details>
<summary><strong>❌ "ninja: command not found"</strong></summary>

**Solution:** Install ninja for your platform

```bash
# Ubuntu/Debian
sudo apt install ninja-build

# macOS
brew install ninja
```

</details>

<details>
<summary><strong>❌ "Permission denied: ./app"</strong></summary>

**Solution:**

-  ✅ Ensure build completed successfully
-  ✅ Check executable exists in build directory
-  ✅ Try: `ls -la app` to verify permissions

</details>

<details>
<summary><strong>❌ CMake configuration fails</strong></summary>

**Solution:**

-  ✅ Verify `CMakeLists.txt` exists in project root
-  ✅ Check all dependencies are installed
-  ✅ Try deleting build folder and recreating

</details>

<details>
<summary><strong>❌ File watching doesn't work</strong></summary>

**Solution:**

-  ✅ Install `inotify-tools` (Linux)
-  ✅ Ensure `../src/` path exists from build directory
-  ✅ Check file permissions on src directory

</details>

## 🤝 Contributing

1. 🍴 Fork the repository
2. 🌿 Create a feature branch (`git checkout -b amazing-feature`)
3. ✏️ Make your changes
4. 🧪 Test with both debug and release builds
5. 📤 Submit a pull request

---

<div align="center">

**Made with ❤️ and lots of ☕**

_Happy Coding! 🚀_

</div>
