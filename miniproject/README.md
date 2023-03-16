CN_arduino_miniProject

# 0. Discription
### Arduino Send Messages from Android to LCD with MIT App Inventor

## 1. 개요 및 기술 설명
MIT App Inventor를 사용하여 안드로이드 앱을 구축하여 블루투스를 통해 아두이노로 메시지를 보내 16 × 2 LCD에 표시하는 미니 프로젝트입니다. 
메시지의 전송은 HC-06 블루투스 모듈을 통해 이루어집니다.

안드로이드 앱은 텍스트 상자를 통해 사용자가 아두이노에 전송할 메시지를 입력할 수 있도록하며, '메시지 보내기' 버튼을 사용하여 메시지를 블루투스를 통해 아두이노로 전송합니다. 그러면 메시지가 아두이노에 연결된 16 × 2 LCD에 표시됩니다.

Bluetooth 연결을 가능하게하기 위해 'Bluetooth 연결'이라는 버튼이 있으며,이 버튼을 누르면 안드로이드 전화기에 현재 페어링 된 Bluetooth 기기가 열리는 List picker가 나타납니다. 사용자는 리스트에서 HC-06 블루투스 모듈을 선택할 수 있습니다. 또한 연결된 블루투스 또는 연결이 끊어진 것을 나타내는 레이블도 화면에 표시됩니다.

1. Arduino: 오픈 소스 하드웨어 및 소프트웨어를 사용하여 인터랙티브한 개체나 환경을 제어하고 모니터링하는 데 사용되는 마이크로컨트롤러 플랫폼
2. HC-06: 저전력 Bluetooth 모듈로, 시리얼 통신 프로토콜을 통해 데이터를 전송할 수 있으며, 보드와 연결하여 무선 통신이 가능하게 합니다.
3. MIT App Inventor: 비전문가도 안드로이드 앱을 개발할 수 있는 인터넷 기반 프로그래밍 환경입니다.
4. Bluetooth: 가까운 거리에서 무선 통신을 할 수 있는 통신 기술로, 인터넷, 모바일 기기, 주변기기 등 다양한 분야에서 사용됩니다.
5. LCD: 액정 표시장치로, 문자나 그래픽을 표시할 수 있습니다. 이 프로젝트에서는 16x2 LCD를 사용합니다

![MIT-APP-Inventor-Display-messages-Overview](https://user-images.githubusercontent.com/79437477/187805756-03593213-10b0-470e-9312-48c167c6091a.jpg)



## 2. Liquid Crystal Display(LCD)

### Types
LCD는 시리얼(serial)과 병렬(parallel) 두 가지 유형이 있습니다. 시리얼 유형은 UART 모듈과 같은 시리얼 통신을 사용하여 아두이노와 연결됩니다. 병렬 LCD는 Hitachi HD44780과 같이 디지털 I/O 핀을 사용하여 아두이노와 연결됩니다. 예를 들어, Hitachi HD44780 타입의 16×2 LCD는 디스플레이의 4-8 데이터 라인과 몇 개의 제어 핀을 사용하여 아두이노와 연결할 수 있습니다. 이 프로젝트에서는 가장 많이 사용되는 16×2 병렬 LCD만 사용합니다.

### 16×2 LCD 
전체 16×2 LCD 모듈에는 두 가지 유형의 핀이 있습니다. 일부 핀은 16×2 LCD로 전송하고 일부 핀은 명령 핀입니다. 즉, 각 핀은 디스플레이의 단일 픽셀을 제어하는 역할을 합니다.
16×2 LCD는 16개의 열과 2개의 행이 있습니다. 즉, 한 행당 16개의 문자를 표시할 수 있으며 두 개의 행이 있습니다. 마찬가지로 20×4 LCD는 4개의 행과 20개의 열이 있습니다. 즉, 한 행당 20개의 문자를 표시할 수 있습니다.

### Pinout Diagram
다이어그램은 16×2 디스플레이의 핀 구성을 보여줍니다. 16개의 핀이 있습니다.

![16X2-LCD-Pinout-diagram-Pic-Microcontroller-tutorial](https://user-images.githubusercontent.com/79437477/187806235-3fef2c6b-ff5c-4166-9e7f-fd2f0136e204.png)

* D0 – D7: 핀 번호 7-14는 Arduino에서 LCD에 표시하려는 데이터를 전송하는 데 사용되는 데이터 버스 라인입니다. 이 8개의 데이터 라인을 사용하여 데이터를 8비트 형식 또는 4비트 형식으로 전송할 수 있습니다. 4비트 형식에서는 상위 4비트 (D4-D7)만 사용하여 Arduino에서 LCD로 데이터를 전송합니다. 전체 바이트는 두 개의 연속된 전송으로 전송됩니다. 4비트 형식은 Arduino의 GPIO 핀을 저장하기 위해 사용됩니다. 더 적은 GPIO 핀이 필요하기 때문입니다.
Contrast Select (VEE): 16X2 LCD 빛에 따라 픽셀의 대조를 제어하는 데 도움이 됩니다.
* RS: 레지스터 선택 핀으로 명령어/데이터 레지스터를 토글하는 데 쓰니다.
* R/W: LCD에서 읽을 것인지 쓸 것인지를 결정합니다.
* EN: 데이터 핀과 다른 명령 핀에서 LCD로 명령을 전송하는 데 쓰입니다. 내부 레지스터에 대한 권한 역할을 합니다.
* VSS: 공통 그라운드를 위한 접지 핀입니다.
* VCC: 전압 입력을 위해 사용되는 전원 핀입니다.



## 3. 16x2 LCD와 HC-05 모듈을 아두이노 보드에 연결하는 방법
16x2 LCD와 아두이노의 다음 연결을 사용합니다.

* Bluetooth Tx with Arduino UNO Rx (D0)
* Bluetooth Rx with Arduino UNO Tx (D1)
* Bluetooth VCC with Arduino UNO +5V
* Bluetooth GND with Arduino UNO GND
아래 회로도는 16x2 LCD, HC-06 및 Arduino UNO 간의 연결을 나타낸 것 입니다.

![Arduino-with-16x2-LCD-and-HC-05](https://user-images.githubusercontent.com/79437477/187806430-e1e65c5e-b095-4ec6-8e33-8b2b97e64281.jpg)




