# 🎮 ARKNOID STM32 - Dự Án Hệ Thống Nhúng Chuyên Nghiệp

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Language: C](https://img.shields.io/badge/Language-C-blue.svg)]()
[![Platform: STM32F401RE](https://img.shields.io/badge/Platform-STM32F401RE-green.svg)]()
[![Status: Active](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()

---

## 📋 Mục Lục

- [Giới Thiệu](#giới-thiệu)
- [Tính Năng](#tính-năng-game)
- [Cách Chơi](#cách-chơi)
- [Yêu Cầu Hệ Thống](#yêu-cầu-hệ-thống)
- [Cài Đặt & Thiết Lập](#cài-đặt--thiết-lập)
- [Kiến Trúc Dự Án](#kiến-trúc-dự-án)
- [Hướng Dẫn Sử Dụng](#hướng-dẫn-sử-dụng)
- [Các Tài Liệu](#các-tài-liệu)
- [Liên Hệ](#liên-hệ)

---

## 🎯 Giới Thiệu

**ARKNOID** là một dự án học tập hệ thống nhúng **toàn diện** được xây dựng trên **STM32F401RET6 Nucleo Board**. Dự án thực hiện game **Arkanoid** cổ điển với giao diện OLED, 5 nút bấm, LED, buzzer, và hệ thống FSM (Máy trạng thái hữu hạn).

**Đây không chỉ là một game - đây là hành trình học tập hoàn chỉnh về:**
- ✅ Embedded C Programming
- ✅ STM32 Microcontroller
- ✅ Giao tiếp Hardware (GPIO, SPI, Timer)
- ✅ Real-time Systems & FSM Design
- ✅ Game Physics & Collision Detection
- ✅ Professional Development Workflow (Git, GitHub, Documentation)

> **Vòng đời chương trình:** `MENU → GAME → GAME OVER/LEVEL CLEAR → MENU`

---

## 🎮 Tính Năng Game

### Gameplay Features
- ✅ **3 Difficulty Levels:** Easy (1) - Normal (2) - Hard (3)
- ✅ **Ball Physics:** Realistic movement with velocity & collision
- ✅ **Collision Detection:** AABB (Axis-Aligned Bounding Box)
- ✅ **Block Breaking:** Destroy blocks, score points
- ✅ **Score System:** Real-time score tracking
- ✅ **Game States:** Menu → Game → GameOver/LevelClear → Menu
- ✅ **Visual Feedback:** LED blinks (6x GameOver, 3x LevelClear)
- ✅ **Audio Feedback:** Buzzer beeps on button press

### Hardware Integration
- ✅ **128x128 OLED Display** (SPI communication)
- ✅ **5 Debounced Buttons** (Active LOW, 10kΩ pull-ups)
- ✅ **1 LED Output** (GPIO, 330Ω resistor)
- ✅ **1 Buzzer** (GPIO, 5V compatible)
- ✅ **Real-time Timer** (SysTick 1ms interrupts)

---

## 🎮 Cách Chơi

### Menu Navigation
```
1. Ấn SW5 (Button Down): Con trỏ di chuyển xuống danh sách tùy chọn
2. Ấn SW3 (Button Enter): Chọn mục hiện tại
   └─ Nếu ở "Level Select": Di chuyển đến chọn level
   └─ Nếu ở "START": Bắt đầu game

3. Ấn SW2/SW4 (Left/Right): Thay đổi level
   └─ SW2 (Left): Giảm level
   └─ SW4 (Right): Tăng level
```

### In-Game Controls
```
SW2 (Left):  Di chuyển thanh sang trái
SW4 (Right): Di chuyển thanh sang phải
SW3 (Enter): [Dành cho extended features]
```

### Game States
```
┌─────────────────────────────────────────┐
│          MENU STATE                     │
│  • Select Level (1, 2, or 3)           │
│  • Navigate with SW5 + SW2/SW4         │
│  • Confirm with SW3                    │
└────────────────────┬────────────────────┘
                     │ START game
                     ▼
        ┌────────────────────────┐
        │    GAME STATE          │
        │ • Ball in play         │
        │ • Break blocks         │
        │ • Control bar          │
        └────────────────────────┘
                     │
          ┌──────────┴──────────┐
          ▼                     ▼
    ┌──────────────┐     ┌──────────────┐
    │ GAME OVER    │     │ LEVEL CLEAR  │
    │ (6 LED      │     │ (3 LED       │
    │  blinks)    │     │  blinks)     │
    └──────┬───────┘     └──────┬───────┘
           │                    │
           └────────┬───────────┘
                    │ Return to MENU
                    ▼
            ┌──────────────────┐
            │   MENU STATE     │
            │ (again)          │
            └──────────────────┘
```

---

## 🔧 Yêu Cầu Hệ Thống

### Hardware
```
✓ STM32F401RET6 Nucleo Board
✓ 128x128 OLED Display (SPI interface)
✓ 5x Push buttons (SW1-SW5)
✓ 10kΩ resistors (for button pull-ups)
✓ 1x LED + 330Ω resistor
✓ 1x Buzzer (5V compatible)
✓ ST-Link USB programmer (on-board)
✓ USB cables (power + programming)
```

### Software - Required
```
□ C Compiler: arm-none-eabi-gcc (v10.3+)
□ Build Tool: GNU Make (v3.8+)
□ Version Control: Git (v2.20+)
□ GitHub Account: Free account
□ Terminal/PowerShell: Windows/Mac/Linux
```

### Software - Optional
```
□ IDE: STM32CubeIDE (Recommended)
□ Code Editor: VS Code + Cortex-Debug
□ Debugger: ST-Link Utility / OpenOCD
□ Serial Monitor: PuTTY, Tera Term, CubeIDE
```

---

## 📦 Cài Đặt & Thiết Lập

### 1️⃣ Clone Repository

```bash
git clone https://github.com/quangducbk2004-iot/arknoid-stm32-game.git
cd arknoid-stm32-game
```

### 2️⃣ Install Toolchain

#### Windows - Using STM32CubeIDE (Easy)
```
1. Download: https://www.st.com/en/development-tools/stm32cubeide.html
2. Run installer & follow wizard
3. Verify: CubeIDE opens successfully
```

#### Windows - Using Command Line
```bash
# Download arm-none-eabi-gcc (from ARM website)
# https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm

# Add to PATH: Control Panel → Environment Variables → Add gcc folder

# Verify:
arm-none-eabi-gcc --version
make --version
```

#### MacOS
```bash
brew install arm-none-eabi-gcc
brew install make
arm-none-eabi-gcc --version
```

#### Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install build-essential gcc-arm-none-eabi git
arm-none-eabi-gcc --version
make --version
```

### 3️⃣ Install ST-Link Drivers

```bash
# Windows: Download from
# https://www.st.com/en/development-tools/stsw-link009.html

# MacOS
brew install stlink

# Linux
sudo apt install stlink-tools openocd
```

### 4️⃣ Verify Installation

```bash
git --version          # Git version 2.x.x
make --version         # GNU Make version
arm-none-eabi-gcc --version  # ARM GCC
```

---


## 🏗️ Kiến Trúc Dự Án

### Cấu Trúc Thư Mục

```
arknoid-stm32-game/
│
├── Src/                          # Source code
│   ├── main.c                    # Entry point + FSM
│   ├── syscalls.c                # System calls
│   ├── sysmem.c                  # Memory management
│   │
│   ├── drivers/                  # Hardware drivers
│   │   ├── gpio.c                # GPIO configuration
│   │   └── timebase.c            # SysTick timer
│   │
│   ├── periph/                   # Peripherals
│   │   ├── button.c              # Button debounce
│   │   ├── led.c                 # LED control
│   │   └── buzzer.c              # Buzzer control
│   │
│   ├── game/                     # Game logic
│   │   ├── run_game.c            # Main game loop
│   │   ├── collision.c           # Physics & collision
│   │   ├── levels.c              # Level data
│   │   └── menu_ui.c             # Menu system
│   │
│   └── graphic/                  # Graphics
│       ├── display_init.c        # OLED initialization
│       └── render.c              # Drawing functions
│
├── Inc/                          # Header files
│   ├── boardconfig.h             # Pin definitions + constants
│   ├── drivers/
│   ├── periph/
│   ├── game/
│   │   └── entities.h            # Game data structures
│   └── graphic/
│
├── Debug/                        # Build output
│   ├── makefile
│   ├── objects.mk
│   └── arknoid.elf              # Compiled executable
│
├── Startup/                      # Startup code
│   └── startup_stm32f401retx.s
│
├── *.ld                          # Linker scripts
├── .gitignore                    # Git ignore patterns
└── README.md                     # This file
```

### GPIO Pin Mapping

| Pin # | Port | Function | Type | Use |
|:-----:|:----:|:--------:|:----:|:---:|
| 5 | PA4 | GPIO Input | Digital | SW3 (Enter) |
| 22 | PB5 | GPIO Input | Digital | SW1 (Up) |
| 20 | PB3 | GPIO Input | Digital | SW2 (Left) |
| 17 | PB0 | GPIO Input | Digital | SW4 (Right) |
| 21 | PB4 | GPIO Input | Digital | SW5 (Down) |
| 12 | PA11 | GPIO Output | Digital | LED |
| 42 | PC9 | GPIO Output | Digital | Buzzer |
| 27 | PA5 | SPI Clock | Digital | OLED CLK |
| 29 | PA7 | SPI MOSI | Digital | OLED MOSI |

### Software Architecture

```
┌─────────────────────────────────────────────┐
│            MAIN (main.c)                    │
│        FSM: MENU ↔ GAME ↔ GAMEOVER         │
└────────────┬────────────────────────────────┘
             │
    ┌────────┴────────────┐
    │                     │
 ┌──▼──────┐     ┌───────▼──────┐
 │  MENU   │     │  GAME LOOP   │
 │ • Cursor│     │ • Input      │
 │ • Levels│     │ • Physics    │
 └─────────┘     │ • Collision  │
                 │ • Render     │
                 │ • Timing     │
                 └──────────────┘
```

### Memory Layout

```
STM32F401RET6:
├─ Flash: 512 KB (Code + Constants)
├─ SRAM: 96 KB (Global vars, Stack, Heap)
└─ CCM: 192 KB (Fast access memory)
```

---

## 💻 Hướng Dẫn Sử Dụng

### Build Project

```bash
cd Debug
make clean
make all

# Expected output:
# Linking arknoid.elf
# Creating hex file arknoid.hex
# Size of arknoid.elf: XXX bytes
```

### Flash to Board

```bash
# Using st-flash:
st-flash write Debug/arknoid.elf 0x8000000

# Or using STM32CubeIDE:
# Right-click project → Run
```

### Play Game

1. Flash firmware to board
2. Press RESET on board
3. Use 5 buttons to play:
   - **SW5**: Navigate menu down
   - **SW3**: Select option
   - **SW2**: Move bar left / Decrease level
   - **SW4**: Move bar right / Increase level
   - **SW1**: (Reserved for future)

---

## 📚 Các Tài Liệu

Dự án bao gồm 13+ tài liệu học tập chi tiết:

### Phân Tích & Kiến Trúc
- 📄 **README_ANALYSIS.md** - Phân tích toàn diện
- 📄 **ARKNOID_ARCHITECTURE.md** - Sơ đồ hệ thống
- 📄 **ARKNOID_QUICK_REFERENCE.md** - Tham khảo nhanh

### Hướng Dẫn Thực Hành
- 📄 **ARKNOID_IMPLEMENTATION_GUIDE.md** - Từng bước
- 📄 **ARKNOID_DEVELOPER_GUIDE.md** - Phát triển tính năng
- 📄 **CIRCUIT_SCHEMATIC_ANALYSIS_GUIDE.md** - Phân tích mạch

### Học Nâng Cao
- 📄 **ADVANCED_C_AND_STM32_PERIPHERALS.md** - C & STM32 nâng cao
- 📄 **GITHUB_SETUP_GUIDE.md** - Thiết lập GitHub

### Lịch Trình
- 📄 **DETAILED_WEEKLY_ROADMAP.md** - Roadmap 6 tuần
- 📄 **WEEKLY_CHECKLIST.md** - Danh sách hàng tuần
- 📄 **TUAN1_HUONG_DAN_THUC_HANH.md** - Tuần 1 chi tiết

**Chọn Learning Path:**
```
Student Path (Mới):
  Week 1: README_ANALYSIS.md + QUICK_REFERENCE.md
  Week 2-3: ARCHITECTURE.md + IMPLEMENTATION_GUIDE.md
  Week 4-5: ADVANCED_C_AND_STM32.md
  Week 6+: DEVELOPER_GUIDE.md + Features

Developer Path (Kinh nghiệm):
  Day 1: QUICK_REFERENCE.md + IMPLEMENTATION_GUIDE.md
  Day 2-5: CIRCUIT_SCHEMATIC.md + Build & Test
  Day 6+: ADVANCED_C_AND_STM32.md + Features

Engineer Path (Nâng cao):
  Day 1: ARCHITECTURE.md + IMPLEMENTATION_GUIDE.md
  Day 2: CIRCUIT_SCHEMATIC.md  
  Day 3-5: ADVANCED_C_AND_STM32.md + Optimization
  Day 6+: Custom features & Portfolio
```

---

## 📊 Project Statistics

```
Lines of Code:
├─ C Code: ~2,500 lines
├─ Documentation: ~15,000 lines
└─ Config: ~500 lines

Learning Materials:
├─ Files: 13+ documents
├─ Words: 50,000+
├─ Examples: 100+
└─ Timeline: 6-10 weeks

Supported Platforms:
├─ Windows (7+)
├─ MacOS (10.14+)
└─ Linux (Ubuntu 18.04+)
```

---

## 🔗 External Links

### STM32 Resources
- [STM32F401 Datasheet](https://www.st.com/resource/en/datasheet/stm32f401re.pdf)
- [STM32 Reference Manual](https://www.st.com/resource/en/reference_manual/dm00096844.pdf)
- [STMicroelectronics](https://www.st.com)
- [ARM Cortex-M4](https://developer.arm.com)

### Tools & Development
- [GNU ARM Toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/)
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Learning Lab](https://lab.github.com)

---

## 🤝 Contributing

1. **Fork** the repository
2. Create **feature branch** (`git checkout -b feature/amazing-feature`)
3. **Commit** changes (`git commit -m 'Add amazing feature'`)
4. **Push** to branch (`git push origin feature/amazing-feature`)
5. Create **Pull Request**

### Code Guidelines
```
✓ Write clear, commented code
✓ Use snake_case for naming
✓ Test before submitting PR
✓ Document new functions
✓ Follow existing code style
```

---

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details

```
Copyright (c) 2024 Quang Duc Bui

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

---

## 📧 Contact & Support

- **GitHub:** [@quangducbk2004-iot](https://github.com/quangducbk2004-iot)
- **Issues:** [Report bugs](../../issues)
- **Discussions:** [Ask questions](../../discussions)

---

## ✨ Key Learning Outcomes

By completing this project, you will learn:

- ✅ Embedded C programming best practices
- ✅ STM32 microcontroller programming
- ✅ Real-time systems & interrupts
- ✅ Hardware interface (GPIO, SPI, Timer)
- ✅ Game physics & collision detection
- ✅ FSM design patterns
- ✅ Professional development workflow
- ✅ Git & GitHub version control
- ✅ Technical documentation writing
- ✅ Hardware circuit analysis

---

## 🎓 Learning Journey

```
Week 1: ✅ Setup & Understanding
Week 2: ✅ Build & Hardware
Week 3: ✅ Assembly & Testing
Week 4: ⏳ Advanced Learning
Week 5: ⏳ Practice & Exercises
Week 6: ⏳ Features & Optimization
       🎯 Professional Portfolio Ready!
```

---

**Last Updated:** April 15, 2026  
**Version:** 2.0  
**Author:** Quang Duc Dao
**Collaborators** Quang Minh To
**Status:** Active Development

---
