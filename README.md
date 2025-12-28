
# ⚽️ 킥오프
> **축구 경기 일정 관리의 시작, 경기 시작 30분 전 알림으로 킥오프를 미리 준비하세요.**

<p align="left">
  <img src="https://img.shields.io/badge/Swift-6.2-F05138?style=flat-square&logo=Swift&logoColor=white">
  <img src="https://img.shields.io/badge/iOS-16.4+-000000?style=flat-square&logo=Apple&logoColor=white">
  <img src="https://img.shields.io/badge/Xcode-26.2-147EFB?style=flat-square&logo=Xcode&logoColor=white">
</p>
<p align="left">
  <a href="여기에_앱스토어_링크_복사">
    <img src="https://developer.apple.com/app-store/marketing/guidelines/images/badge-download-on-the-app-store.svg" width="150">
  </a>
</p>

---
<img src="https://private-user-images.githubusercontent.com/120799762/530512805-6c650469-6155-4c67-88ae-18d2873b4f12.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjY4ODM4NzEsIm5iZiI6MTc2Njg4MzU3MSwicGF0aCI6Ii8xMjA3OTk3NjIvNTMwNTEyODA1LTZjNjUwNDY5LTYxNTUtNGM2Ny04OGFlLTE4ZDI4NzNiNGYxMi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUxMjI4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MTIyOFQwMDU5MzFaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0yNTA4OTY2YTYyNDI0MWUwYjdmM2Q1ODllMmNhNThmZTNiNzAzZjUzZWExNzE1ODVlN2Y3NzBhM2FhZjUyM2IwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.LlO1EMzCfbn2mkjSaOukHPfHpzrdVlaVKuxDXXtek7w" >

---

## 📌 프로젝트 소개
축구 팬으로서 경기 시작 직후에 오는 알림은 가끔 너무 늦게 느껴질 때가 있습니다. **킥오프**는 경기 시작 전 미리 준비할 수 있는 시간을 확보해주고, 흩어져 있는 경기 일정을 개인 캘린더와 연동하여 효율적으로 관리하기 위해 개발되었습니다.

* **문제 의식**: 경기 시작 시점의 알림은 시청 준비를 하기엔 다소 늦음.
* **해결 방안**: **경기 시작 30분 전 사전 푸시 알림**과 **iOS 시스템 캘린더 자동 등록**을 통해 끊김 없는 사용자 경험 제공.

---

## ✨ 주요 기능

⚽️ 리그 팔로잉 - 내가 응원하는 리그(EPL, 라리가 등)만 쏙쏙 골라 담기

🔐 스마트 인증 - Supabase 기반의 안전한 로그인 및 데이터 실시간 동기화

🏠 커스텀 홈 - 내가 팔로우한 경기로만 가득 채운 나만의 경기 일정표

🔔 30분 전 알림 - 경기 시작 전 준비 시간까지 챙겨주는 세심한 푸시 알림

📅 원클릭 캘린더 - 터치 한 번으로 경기 일정을 내 시스템 캘린더에 저장

📋 알림 히스토리 - OneSignal로 전송된 알림 목록을 한눈에 확인하고 관리

---

## 👤 담당 역할
**1인 개발 (기여도 100%)**

* **iOS 개발**: 기획부터 앱스토어 배포까지 앱 개발 전 과정 수행
* **UI/UX 디자인**: 사용자 경험 중심의 인터페이스 설계 및 SwiftUI 구현
* **백엔드 설계**: Supabase를 활용한 DB 스키마 설계 및 데이터 동기화 구현
* **알림 시스템**: OneSignal API를 활용한 사전 알림 예약 및 수신 로직 구현

## 🛠 기술 스택

### 프레임워크 & 라이브러리
* **UI/Reactive**: `SwiftUI`, `Combine`
* **System Services**: `EventKit`, `EventKitUI` (Calendar 연동)
* **Networking**: `Alamofire`, `Kingfisher` (이미지 캐싱)
* **Database/Auth**: `Supabase`
* **Push Service**: `OneSignal`
* **UI Helpers**: `AlertToast`

---

## 🏗 아키텍처 및 구조 

### MVVM 패턴
- **View**: SwiftUI를 활용한 선언적 UI 구성.
- **ViewModel**: `ObservableObject`를 기반으로 UI 상태 관리 및 비즈니스 로직 처리.
- **Service Layer**: 캘린더 접근(`CalendarService`), API 통신(`APIService`) 등 외부 의존성 로직을 분리하여 ViewModel의 독립성 확보.

### 📂 프로젝트 구조
```text
KickOff
 ┣ App                # 앱 진입점 (App Delegate, Main)
 ┣ Components         # 공용 UI 컴포넌트 (Alert, Onboarding)
 ┣ Core               # 외부 의존성 및 공통 로직
 ┃ ┣ Network          # SDK 래핑 (Supabase, OneSignal)
 ┃ ┣ Service          # 계층 분리 (API, Calendar)
 ┃ ┗ Utils            # Extensions, Helpers
 ┣ Feature            # MVVM 기반 기능 모듈
 ┃ ┣ Auth             # 로그인/회원가입
 ┃ ┣ Home             # 경기 목록 및 일정 관리
 ┃ ┣ Notification     # 알림 센터
 ┃ ┗ Setting          # 앱 설정 및 사용자 정보
 ┣ Models             # 데이터 모델 (DTO)
 ┗ Assets             # 이미지 및 리소스
```


## 💡 기술적 선택 이유

### 🔔 OneSignal: 푸시 메시지 및 예약 발송
- **서버리스 예약 발송**: 별도의 백엔드 스케줄러를 구축하지 않고도, OneSignal API의 `send_after` 파라미터를 활용해 클라이언트에서 직접 발송 시점을 지정할 수 있어 개발 효율을 높였습니다.
- **시간대 최적화**: 사용자가 앱을 사용하지 않는 시간에도 안정적으로 알림이 전달되도록 원격 푸시 서버를 활용하여 신뢰성을 확보했습니다.
- **비용 및 관리 편의성**: 무료 티어에서도 강력한 푸시 관리 기능을 제공받아 초기 구축 비용을 절감하고, 알림 히스토리 관리의 편의성을 도모했습니다.
- **효율적인 운영 관리**: 코드 수정 없이 대시보드상에서 직접 예약된 알림을 취소하거나 테스트 메시지를 발송하는 등 디버깅과 운영 관리의 편의성을 높였습니다.

### ⚡️ Supabase: 백엔드 인프라 및 인증
- **비용 효율성**: 별도의 서버 인프라 유지보수 비용 없이 무료 티어 내에서 데이터베이스(DB)와 인증 시스템을 구축하여 프로젝트 운영의 경제성을 확보했습니다.
- **생산성 극대화**: 실시간 데이터 동기화와 소셜 로그인 기능을 SDK 형태로 제공받아, 인프라 구축에 소요되는 시간을 줄이고 iOS 클라이언트의 핵심 비즈니스 로직 구현에 집중할 수 있었습니다.
