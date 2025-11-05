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
  <img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/8aefd084-9289-4ab5-a6cb-e2a9a87fa5d5" />


2. Click **File → New STM32 Project**.
   ![WhatsApp Image 2025-10-29 at 07 53 46_3e34e272](https://github.com/user-attachments/assets/4e1c76c8-e712-4f89-83ab-985d4149d6ee)


3. Select the **target microcontroller** or board and click **Next**.
   ![WhatsApp Image 2025-10-29 at 07 54 04_c80005fb](https://github.com/user-attachments/assets/299a3cb6-5a81-4df3-bc86-886f5ada60ce)

4. Name the project.
![WhatsApp Image 2025-11-04 at 18 15 08_6ee05bb1](https://github.com/user-attachments/assets/c4b741f7-8fc6-4b85-82aa-d97482b4f18d)
  
5. The corresponding `.ioc` file will be generated automatically.
  <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/8900847c-6745-43e2-9ecf-2e66877fdc49" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/acc4f1c4-5e33-431b-8a76-3b102016baa6" />
<img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/b7abcd80-797d-451f-a7c3-23f303822423" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1080" height="608" alt="image" src="https://github.com/user-attachments/assets/dbf4b205-5db9-4e9b-8150-94f441c8b116" />
 
8. Edit the generated main program as required.
   <img width="1110" height="624" alt="image" src="https://github.com/user-attachments/assets/05b39060-35d6-420d-9f4d-8721439bd82f" />
<img width="1104" height="621" alt="image" src="https://github.com/user-attachments/assets/2ec55709-a45f-4e6e-8738-6aa94138eab1" />

9. Click **Project → Build All**.
    ![WhatsApp Image 2025-11-04 at 18 15 14_6fc37175](https://github.com/user-attachments/assets/2d14c3bd-eaae-46fb-933d-2069d259d684)

10. Link the **HEX file** using the post-build process.
  ![WhatsApp Image 2025-11-04 at 18 15 33_a50e373b](https://github.com/user-attachments/assets/6773b1eb-75df-4988-9d56-1a2e80393678)

11. Click **Debug** and connect the **STM Nucleo Board**.
   ![WhatsApp Image 2025-11-04 at 18 16 18_5062efd9](https://github.com/user-attachments/assets/a4bc86b2-cb04-4664-841e-4317cee9e90e)


13. Click **Run** to execute the program.
![WhatsApp Image 2025-11-04 at 18 16 18_7bf09efe](https://github.com/user-attachments/assets/e700eeab-2391-485c-a29c-345ad8e2cb8b)


### 💻 **Program**
c
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
### OUTPUT
CASE 1: LED ON
![WhatsApp Image 2025-10-29 at 08 08 16_1569c06b](https://github.com/user-attachments/assets/162098eb-97d8-499a-b733-346927dc3ea2)
CASE 2: LED OFF
![WhatsApp Image 2025-10-29 at 08 08 17_2ec60835](https://github.com/user-attachments/assets/14d0c2e6-eb94-42ff-9b40-0f0d42cf10b7)

### RESULT

The experiment on IR Sensor-Based Automatic LED Control using STM32 was successfully carried out. The STM32 microcontroller accurately read the IR sensor output and controlled the LED based on object detection. When an object was detected, the LED glowed (ON) and when no object was present, the LED remained OFF. Thus, the objective of the experiment was achieved.




