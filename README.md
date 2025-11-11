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
  ![WhatsApp Image 2025-11-11 at 12 57 55_f1f98fe8](https://github.com/user-attachments/assets/c3efc36d-b723-456c-ac88-99ccfe28a3cc)

2. Click **File → New STM32 Project**.
<img width="1280" height="799" alt="image" src="https://github.com/user-attachments/assets/1e506e6d-fb11-4751-a936-2224a36a88d7" />
<img width="1280" height="799" alt="image" src="https://github.com/user-attachments/assets/3faae2c0-8b0f-4eb7-a823-238d0685f35e" />



3. Select the **target microcontroller** or board and click **Next**.
  <img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/ba614978-4cca-4606-8d20-55cfb3c8ce7c" />


4. Name the project.
   <img width="1280" height="799" alt="image" src="https://github.com/user-attachments/assets/3ebdbe01-2e42-4576-a19e-c472455e21f5" />

5. The corresponding `.ioc` file will be generated automatically.
  <img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/984ecb0f-78df-4024-af9e-e9f8821b073c" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  <img width="1280" height="796" alt="image" src="https://github.com/user-attachments/assets/878745e5-307e-4d5a-bd46-285b38fa7793" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1280" height="799" alt="image" src="https://github.com/user-attachments/assets/3d89d173-f2e3-467b-832d-3a653ffe07e4" />

 
8. Edit the generated main program as required.
  <img width="1280" height="791" alt="image" src="https://github.com/user-attachments/assets/1b2654c3-4121-48fe-a266-cdad2dedad99" />
  <img width="1280" height="799" alt="image" src="https://github.com/user-attachments/assets/fb1e6c7e-3cf7-4c0b-83a3-b0fbc4f94327" />



9. Click **Project → Build All**.
    
   <img width="616" height="387" alt="image" src="https://github.com/user-attachments/assets/b1e6f350-a984-4961-b023-e57421c542ee" />
   

10.Click Project → Build All.
<img width="1280" height="799" alt="image" src="https://github.com/user-attachments/assets/e3b2be5a-66fa-40be-9529-ca08573c0f55" />


11. Link the **HEX file** using the post-build process.
   <img width="1280" height="799" alt="image" src="https://github.com/user-attachments/assets/d2217d56-6037-47ce-9dba-8896ad5a97f5" />

12. Click **Debug** and connect the **STM Nucleo Board**.
<img width="1280" height="799" alt="image" src="https://github.com/user-attachments/assets/1f45d2c0-8387-45cd-8e9d-90eb0e078cf1" />

13. Click **Run** to execute the program.
    
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
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/3805e3d8-6675-48d4-a3b2-ded8ca0ff3e8" />

CASE 2: LED OFF
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/ecc19d1e-542f-4061-801b-23e7b6f5f130" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
