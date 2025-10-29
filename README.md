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
   ![WhatsApp Image 2025-10-29 at 08 08 22_5f8f162e](https://github.com/user-attachments/assets/05de4272-045e-43a0-bb24-f25e99e65541)


2. Click **File → New STM32 Project**.
   ![WhatsApp Image 2025-10-29 at 08 08 49_c8bea81f](https://github.com/user-attachments/assets/9aa3b7fb-5a06-4192-a66d-abf1cbc34c36)
   ![WhatsApp Image 2025-10-29 at 08 09 10_4f673879](https://github.com/user-attachments/assets/8277ff37-c8b7-4425-9bba-bfeb44db2f28)



4. Select the **target microcontroller** or board and click **Next**.
  ![WhatsApp Image 2025-10-29 at 08 09 36_ee447f83](https://github.com/user-attachments/assets/de2a8ebf-bf29-46a2-aeae-d6cf3814f60c)



5. Name the project.
   ![WhatsApp Image 2025-10-29 at 08 10 08_2d7dfd98](https://github.com/user-attachments/assets/0ca929e7-f1b7-4f95-ab40-371eadad0ba8)


6. The corresponding `.ioc` file will be generated automatically.
  ![WhatsApp Image 2025-10-29 at 08 10 33_a425aeed](https://github.com/user-attachments/assets/da960d1c-a35c-4494-b63d-18caa00bc5d7)

7. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  ![WhatsApp Image 2025-10-29 at 08 11 02_b4ded41d](https://github.com/user-attachments/assets/b387d916-b735-44e2-b04d-6e1d44889ce3)
 
   
8. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   ![WhatsApp Image 2025-10-29 at 08 11 30_b88525c7](https://github.com/user-attachments/assets/31f9acce-6d8c-42d2-bf2a-c84c0792103f)

 
9. Edit the generated main program as required.
   ![WhatsApp Image 2025-10-29 at 08 12 03_78170707](https://github.com/user-attachments/assets/85c3cd3b-b836-48eb-a358-9a601607145f)
   ![WhatsApp Image 2025-10-29 at 08 12 25_02c718de](https://github.com/user-attachments/assets/9c4aa2f1-ef60-4370-bb91-af51c4bf05fb)

10. Click **Project → Build All**.
    ![WhatsApp Image 2025-10-29 at 08 12 56_6eb9f925](https://github.com/user-attachments/assets/caf83dfe-f93c-48c4-aa16-0ac488c1ecc9)


11. Link the **HEX file** using the post-build process.
    <img width="1920" height="1200" alt="Screenshot (77)" src="https://github.com/user-attachments/assets/42530c9a-f952-4ef6-90f6-e32ec5b875f7" />


12. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1920" height="1200" alt="Screenshot (77)" src="https://github.com/user-attachments/assets/61e40d5d-f3fe-4de1-a2b5-c7699ae77962" />


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
![WhatsApp Image 2025-10-28 at 20 45 03_68d30f33](https://github.com/user-attachments/assets/d5f325e3-a664-40d0-8ac7-6869a2168f7f)


CASE 2: LED OFF
![WhatsApp Image 2025-10-28 at 20 45 04_375b5962](https://github.com/user-attachments/assets/f5b4422c-8580-4e47-8004-7c3f8facf88f)


---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
