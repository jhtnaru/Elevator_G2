# Elevator Project
**2025.6.25 / 경기인력개발원 Semicon 설계 검증**

## 📌 개요
**STM32F411 마이크로컨트롤러**를 이용하여 제작한 **엘리베이터 시스템**입니다.\
실제 엘리베이터와 유사하게 **다층 이동, 안전 기능** 등을 구현했습니다.

- **목적**: STM32를 활용하여 엘리베이터 동작 및 제어 Logic 구현
- **주요 기능**:
  - Button 입력 (층 선택, 문 열림, 비상 정지)
  - Photo Interrupter (위치 및 문 안전 감지)
  - Stepper Motor (엘리베이터 상하 이동)
  - Servo Motor (문 제어, 기어 사용)
  - Buzzer (경고음, 알림음)
  - LCD, FND, LED Bar (상태 및 층 표시)

---

## 📐 시스템 기능
### 🖲 Button
- 중복 입력될 경우 상황에 맞게 순차 적용하여 다층 이동 구현
- 내부: 1층, 2층, 3층, 문 열림, 비상 버튼
- 외부: 1층 UP, 2층 UP, 2층 DOWN, 3층 DOWN  
- EXTI 인터럽트 입력, 디바운스 처리 적용

### 📷 Photo Interrupter
- 엘리베이터 위치 및 도착 확인  
- 문 닫힘 시 사람 감지 → 닫힘 방지 기능

### 🔔 Buzzer
- 비상 상황 시 경고음 출력  
- 문 열림 알림음 출력  
- Timer PSC/CCR 설정으로 주파수·볼륨 조절

### ⚙️ Stepper Motor
- Half Step 방식 → 부드러운 회전 및 정밀 제어  
- 줄 감는 방식으로 상하 운동 구현

### ⚙️ Servo Motor (문 제어)
- 50Hz 주파수 설정  
- 기어(3D 프린터 제작) 적용 → 좌우 이동 통한 문 열림/닫힘

### 📺 LCD
- I2C 통신으로 배선 단순화  
- 층/상태 표시 및 시간 출력

### 🔢 FND
- 층 표시 및 이동시 깜빡임 출력

### 📊 LED Bar
- 상하 이동 방향 표시  
- 문 상태 출력 (열림/닫힘)

---

## 🛠 제작 및 구현
- 층 높이 차이 명확히 표현하기 위해 키트 개조
- 내부 / 외부 버튼 위치 분리  
- LCD, FND, LED Bar, 부저 등 다양한 출력 방식 활용  

---

## 📌 시연영상 및 Code
- [시연 영상 1](https://youtu.be/ItRWSdfe4UA?si=Y0ut0N3RjKUCXeC7)  
- [시연 영상 2](https://youtu.be/nzP6Srg53ek?si=j1t8GTjf2vBfKlCj)  
- [코드 및 문서 (Notion)](https://junaru.notion.site/Elevator-Project-G2-Code-21a571106f8780d1b73cf86911aec522?source=copy_link)
  
---

## 🚧 문제 해결
- **복잡한 경우의 수** → Flag 및 변수 활용하여 상황 정리  
- **비상 Toggle 문제** → 입력 방식 변경 및 Debounce 적용  
- **문 닫힘 안전 문제** → Photo Interrupter 추가 설치  
- **배선 불량 문제** → Debug Mode 활용해 변수 변화 추적  

---

## 🔄 개선 및 향후 계획
- 버튼 눌림 표시 및 토글 기능 추가  
- 환풍기 설치  
- 기어 개선을 통한 문 열림 기능 향상  
- 포토 인터럽터 활용 무게 초과 경고  
- RTC 시간 동기화 기능 추가  

---

## ✅ 결론
- 다양한 상황에 따른 **조건 처리 및 제어 경험** 습득  
- **시제품 Test 및 Debugging**의 중요성 확인  
- 하드웨어 외관 제작을 통한 **사실적 구현 노력**  
