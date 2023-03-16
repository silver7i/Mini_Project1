# mini Project1 - 블루투스 모듈을 사용한 아두이노 프로젝트
    코딩을 배운지 두달이 안된 시점에서 진행된 미니팀프로젝트입니다.
---
#### 프로젝트 기간
- 2022.(08.29 ~ 08.31) 
---
#### 주 역할
- 아두이노 버저, LED 제어 코드 작성 및 구현
---
- 운영체제 및 툴 - Window / Arduino IDE
- 사용언어 - C++
---
    ● 프로포즈 형식으로 구현
    - 블루투스 모듈을 사용하여, App와 LCD 통신
    - Arduino UNO를 사용한 서보모터, LED, 버저, 세그먼트 제어
    
      ① 조도 센서 - LCD 화면 밝기 조절
       (불이 꺼진 공간에서 LCD 화면만 보일 수 있도록)
      ② LCD - 블루투스 모듈을 사용한 App(App Inventor) / LCD 통신
       (App를 통해 입력한 메시지를 LCD 화면에 띄움)
      ③ 버튼 – LCD를 제외한 나머지 부품들 실행
       (아두이노 코드에 따라 순서대로 동작)
      ④ LED - 하트를 그리듯 두 개씩 점등 후 전부 점등
      ⑤ 버저 - LED 전부 점등 후 멜로디 출력
      ⑥ 세그먼트 - 버저 출력이 끝난 후 타이머 작동
      ⑦ 서보모터 - 타이머가 작동되는 동시에 1초마다 180도 각도로 왕복
---
<table>
  <tr>
    <th>
      [구성도]
    </th>
    <th>
      [결과 화면]
    </th>
  </tr> 
  <tr>
    <td>
      <img src="https://user-images.githubusercontent.com/77370836/225534311-b0623531-00d5-494f-b43c-290370af406b.png" width="600" height="350">
    </td>
    <td colspan="2" align=center> 
        <img src="https://user-images.githubusercontent.com/77370836/225534506-6e8c0d30-c0bd-47c7-a482-f0f001df6860.png" width="600" height="350">
    </td>
  </tr>
</table>

