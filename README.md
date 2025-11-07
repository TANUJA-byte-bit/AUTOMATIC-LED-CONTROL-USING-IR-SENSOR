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
  <img width="1920" height="1200" alt="Screenshot (3472)" src="https://github.com/user-attachments/assets/bb60e4d0-b325-48ea-afce-a77cd1779941" />


2. Click **File → New STM32 Project**.
   <img width="1920" height="1200" alt="Screenshot (3473)" src="https://github.com/user-attachments/assets/b7314701-813f-418b-a9e8-aa0360f5de48" />

   
3. Select the **target microcontroller** or board and click **Next**.
   


4. Name the project.
  <img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/60a2d475-dd83-4ced-97b6-0d1a104a3857" />

5. The corresponding `.ioc` file will be generated automatically.
 <img width="1920" height="1200" alt="Screenshot (3479)" src="https://github.com/user-attachments/assets/ccb2de7b-a5e3-4fa5-add3-78b2ff335073" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1920" height="1200" alt="Screenshot (3480)" src="https://github.com/user-attachments/assets/c680324a-612b-48f3-a6ae-eef32ffb2c38" />
   <img width="1920" height="1200" alt="Screenshot (3481)" src="https://github.com/user-attachments/assets/4e1a41a1-5e5e-4fb9-a626-cfea39438ae4" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
  <img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/84be164d-e234-4ae8-a657-6327fe47fb68" />

 
8. Edit the generated main program as required.
   <img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/2fb56aed-818a-45fe-be5b-81d1b43e967b" />


9. Click **Project → Build All**.
 <img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/323846a4-e3a3-44e9-a615-69e32f87b60c" />


10. Link the **HEX file** using the post-build process.
   <img width="1441" height="548" alt="image" src="https://github.com/user-attachments/assets/57b9253e-0d62-4487-8279-e9a376331925" />


11. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1280" height="800" alt="image" src="https://github.com/user-attachments/assets/aca3b8ea-37e6-4f38-96cd-4b4783341a83" />


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
<img width="1056" height="792" alt="image" src="https://github.com/user-attachments/assets/b47bbe13-8021-4420-ac91-ade59bfef197" />

CASE 2: LED OFF
<img width="1056" height="792" alt="image" src="https://github.com/user-attachments/assets/c91bdc6a-fe43-47fe-bfcb-1ee53c90d874" />

---
### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




