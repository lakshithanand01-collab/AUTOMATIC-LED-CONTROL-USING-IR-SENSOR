# AUTOMATIC-LED-CONTROL-USING-IR-SENSOR
##  AIM
To design and implement a system using the **STM32 microcontroller** where an LED automatically turns ON or OFF based on the input from an **IR sensor**.

---

##  Components Required
- STM32 Nucleo or Discovery Board (e.g., **Nucleo-G071RB**)
- IR Sensor Module
- LED (5mm Green or any color)
- Jumper wires
- Breadboard

---

##  Theory
An **IR sensor** detects the presence of an object by emitting and receiving infrared light.

### IR Sensor Behavior
- When an **object is detected**, the IR sensor output goes **LOW (0V)**.
- When **no object is detected**, the output stays **HIGH (3.3V)**.

### Microcontroller Response
- If **IR output = LOW** → **LED ON**
- If **IR output = HIGH** → **LED OFF**
### **Procedure**

1. Open **STM32CubeIDE**.


2. Click **File → New STM32 Project**.
  <img width="1082" height="1024" alt="Screenshot 2025-11-05 104929" src="https://github.com/user-attachments/assets/7f55e3a4-d55f-4aa1-b6b3-99a0997cbf5b" />
<img width="1650" height="1191" alt="Screenshot 2025-11-05 111944" src="https://github.com/user-attachments/assets/fcd0eb00-bc05-42f4-a6a3-05a3751f651b" />



3. Select the **target microcontroller** or board and click **Next**.
  <img width="1864" height="1038" alt="Screenshot 2025-11-05 112142" src="https://github.com/user-attachments/assets/e085ec57-bfe5-4012-b709-8c5d8cd4efb8" />




4. Name the project.
   <img width="1670" height="1086" alt="image" src="https://github.com/user-attachments/assets/ce9ac496-fa92-4aa9-b58f-21c36f999092" />


5. The corresponding `.ioc` file will be generated automatically.
 <img width="1396" height="965" alt="Screenshot 2025-11-05 112253" src="https://github.com/user-attachments/assets/d2418882-bc14-4e4c-a323-6dffbe882b08" />


6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
  <img width="1683" height="937" alt="Screenshot 2025-11-05 112345" src="https://github.com/user-attachments/assets/5abd1f77-eb2d-45e6-8bd3-78e57fc18054" />


7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.





 
8. Edit the generated main program as required.
   
<<img width="1261" height="1087" alt="image" src="https://github.com/user-attachments/assets/877a4db5-6d6c-4bce-8d06-039a842948c0" />


9. Click **Project → Build All**.
 <img width="1015" height="890" alt="Screenshot 2025-11-05 105250" src="https://github.com/user-attachments/assets/de267a8a-4253-4b09-9cf3-4152c9639fca" />
>

10. Link the **HEX file** using the post-build process.
  <img width="1015" height="890" alt="Screenshot 2025-11-05 105250" src="https://github.com/user-attachments/assets/5540337a-a969-486c-818c-0c3d673264b0" />


11. Click **Debug** and connect the **STM Nucleo Board**.
   <img width="1891" height="1123" alt="Screenshot 2025-11-05 110527" src="https://github.com/user-attachments/assets/87d43ba5-47d3-45af-906f-07d9d2632b06" />


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
        GPIO_PinState ir = HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_10); // IR OUT at PA10 (D2)

	      if (ir == GPIO_PIN_RESET)  // IR sensor HIGH = object detected
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_SET); // Turn ON LED
	      }
	      else
	      {
	          HAL_GPIO_WritePin(GPIOB, GPIO_PIN_3, GPIO_PIN_RESET); // Turn OFF LED
	      }

	      HAL_Delay(100);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

CASE 2: LED OFF

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




