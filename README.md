# 🔐 Dynamic OTP-Driven Secure Access System

## 🛡️ Project Overview

This project implements a secure, time-limited access control system using One-Time Password (OTP) verification over GSM communication.
The system is built around the **LPC2148 ARM7 microcontroller** and sends OTPs to a registered mobile number.
Access is granted only after successful password and OTP verification.

---

## 🎯 Objective

To design and implement a microcontroller-based OTP authentication system that:

* Authenticates users using a stored password
* Generates and sends OTP via GSM module
* Verifies OTP within a defined time using RTC
* Grants or denies access based on OTP validity

---

## 🔧 Hardware Requirements

* LPC2148 ARM7 Microcontroller
* GSM Module (M660A or SIM800/SIM900 compatible)
* 16×2 LCD Display
* 4×4 Matrix Keypad
* Push Switch
* LED / Bulb / DC Motor with L293D Driver
* External EEPROM (AT24C256)

---

## 💻 Software Requirements

* Embedded C Programming
* Keil µVision IDE
* Flash Magic (for programming LPC2148)

---

## 🧩 Project Modules

Each peripheral is developed and tested individually before integration.

* **lcd.c / lcd.h** → LCD control functions
* **keypad.c / keypad.h** → Matrix keypad scanning
* **uart.c / uart.h** → UART communication with GSM module
* **delay.c / delay.h** → Timing utilities
* **i2c.c / i2c.h** → EEPROM communication
* **projectmain.c** → Main application logic integrating all modules

---

## 🧪 Testing Procedure

### ✔ LCD Test

Display characters, strings, and numbers.

### ✔ Keypad Test

Display pressed key on LCD.

### ✔ EEPROM Test

Test byte and page read/write operations.

### ✔ UART Test

Verify transmit/receive using interrupts.

### ✔ RTC Test

Display current date/time using LPC2148 RTC.

### ✔ GSM Module Test

**Manual AT command testing:**

```
AT
ATE0
AT+CMGF=1
AT+CMGS="MobileNumber"
```

**Automatic testing:**

* Use `gsm_init()` and `send_sms()` functions
* UART interrupt driven communication

---

## ⚙️ Final Execution Logic

1. Wait for password input via keypad
2. Verify password from EEPROM
3. If valid → Generate OTP and send via GSM
4. Start timer using RTC
5. Wait for OTP entry within allowed time
6. Grant or deny access accordingly
7. Allow password update via external interrupt

---

## 📦 How to Run

1. Compile project in Keil µVision
2. Flash firmware using Flash Magic
3. Connect GSM, LCD, Keypad, EEPROM, and driver circuit
4. Power ON the system
5. Follow instructions displayed on LCD

---

## 📎 Important Notes

* UART interrupt-driven communication is mandatory for GSM reliability
* Always validate GSM command responses before proceeding
* Password and OTP values are stored and read from EEPROM

---

## 👨‍💻 Author

**Mamidi Manikanta**

Embedded Systems Developer


