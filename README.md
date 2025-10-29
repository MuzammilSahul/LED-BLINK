# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
 <img width="1476" height="1198" alt="Screenshot 2025-10-28 183744" src="https://github.com/user-attachments/assets/5bcb35f4-0978-42a3-8da3-5498a919f78a" />


2. Click **File → New STM32 Project**.
<img width="1371" height="1161" alt="Screenshot 2025-10-28 183149" src="https://github.com/user-attachments/assets/7debc132-61cb-4470-9ebb-58399783cb3f" />
<img width="1499" height="1199" alt="Screenshot 2025-10-28 183916" src="https://github.com/user-attachments/assets/2f57acb4-4dc0-4770-8f32-11577d676bad" />


3. Select the **target microcontroller** or board and click **Next**.
<img width="1788" height="1131" alt="Screenshot 2025-10-28 184510" src="https://github.com/user-attachments/assets/1518db80-ebf6-452c-ad5d-e259cd292153" />
<img width="1501" height="1148" alt="Screenshot 2025-10-28 203823" src="https://github.com/user-attachments/assets/78c65d5b-9dee-4b68-804a-7246f091a4a7" />




4. Name the project.
  <img width="1199" height="1125" alt="Screenshot 2025-10-28 184612" src="https://github.com/user-attachments/assets/1c2b733d-445c-42c1-8f00-204a88482610" />


5. The corresponding `.ioc` file will be generated automatically.
<img width="1513" height="1046" alt="Screenshot 2025-10-28 222649" src="https://github.com/user-attachments/assets/c8f6645a-de34-4b7e-9e25-072d7263dbd9" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/acc4f1c4-5e33-431b-8a76-3b102016baa6" />
<img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/b7abcd80-797d-451f-a7c3-23f303822423" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  <img width="1409" height="947" alt="Screenshot 2025-10-29 121805" src="https://github.com/user-attachments/assets/aba3aa3f-4b95-4389-b599-8795cd5f088d" />

 
8. Edit the generated main program as required.
  <img width="1312" height="1197" alt="Screenshot 2025-10-29 103759" src="https://github.com/user-attachments/assets/0afcc04f-9882-4bf8-8052-d9873fa66b9e" />


9. Click **Project → Build All**.
  <img width="1920" height="1200" alt="Screenshot 2025-10-29 104135" src="https://github.com/user-attachments/assets/bd9eddc6-0ec7-47be-aefd-76ffd15ae7e8" />


10. Link the **HEX file** using the post-build process.
    <img width="1917" height="1195" alt="Screenshot 2025-10-29 104110" src="https://github.com/user-attachments/assets/2fe3b55e-705a-456f-a18d-a1178f258d24" />


11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1918" height="1151" alt="Screenshot 2025-10-29 104314" src="https://github.com/user-attachments/assets/085b2aed-8773-47ed-93a1-1351a8e8c591" />


12. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
![WhatsApp Image 2025-10-29 at 10 45 34_e3a54c19](https://github.com/user-attachments/assets/787bb5cc-e2e7-4806-95a4-9d70a8866f30)

CASE 2: LED OFF
![WhatsApp Image 2025-10-29 at 10 45 34_2f8c45fc](https://github.com/user-attachments/assets/3f4b6b14-c110-4f83-977b-4d318ff0394d)

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
