
# ⚽️ 킥오프
> **축구 경기 일정 관리의 시작, 경기 시작 30분 전 알림으로 킥오프를 미리 준비하세요.**

<p align="left">
  <img src="https://img.shields.io/badge/Swift-6.2-F05138?style=flat-square&logo=Swift&logoColor=white">
  <img src="https://img.shields.io/badge/iOS-16.4+-000000?style=flat-square&logo=Apple&logoColor=white">
  <img src="https://img.shields.io/badge/Xcode-26.2-147EFB?style=flat-square&logo=Xcode&logoColor=white">
</p>

<p align="left">
  <a href="https://apps.apple.com/kr/app/%ED%82%A5%EC%98%A4%ED%94%84-%EC%B6%95%EA%B5%AC-%EA%B2%BD%EA%B8%B0-%EC%9D%BC%EC%A0%95/id6756507148">
    <img src="https://developer.apple.com/app-store/marketing/guidelines/images/badge-download-on-the-app-store.svg" width="150">
  </a>
</p>

---
<img src="https://github.com/user-attachments/assets/0f002d46-49a0-4546-ab95-e5183fc0028c" width="100%">

---

## 📌 프로젝트 소개
축구 팬으로서 경기 시작 직후에 오는 알림은 가끔 너무 늦게 느껴질 때가 있습니다. **킥오프**는 경기 시작 전 미리 준비할 수 있는 시간을 확보해주고, 흩어져 있는 경기 일정을 개인 캘린더와 연동하여 효율적으로 관리하기 위해 개발되었습니다.

* **문제 의식**: 경기 시작 시점의 알림은 시청 준비를 하기엔 다소 늦음.
* **해결 방안**: **경기 시작 30분 전 사전 푸시 알림**과 **iOS 시스템 캘린더 자동 등록**을 통해 끊김 없는 사용자 경험 제공.

---

## ✨ 주요 기능

⚽️ 리그 팔로잉 - 관심 리그를 팔로우해 사용자가 원하는 경기 일정만 확인할 수 있도록 구성

🔐 스마트 인증 - Supabase 기반의 안전한 로그인 및 데이터 실시간 동기화

🏠 커스텀 홈 - 팔로우한 경기만 표시되는 커스텀 홈 화면으로 정보 탐색 부담 최소화

🔔 30분 전 알림 - 경기 시작 30분 전 알림을 제공해 사전 준비가 가능하도록 지원

📅 원클릭 캘린더 - 관심 경기를 시스템 캘린더에 등록해 앱 외부에서도 일정 관리 가능

📋 알림 히스토리 - 전송된 알림 히스토리를 확인해 알림 상태를 점검할 수 있도록 구성

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

## 🔧 문제 해결
### 구독 사용자 타겟팅 푸시 알림
- **문제**: 모든 앱 사용자에게 푸시 메시지를 보내게 되는 문제가 발생했습니다. 알림 받고 싶은 경기를 구독한 특정 사용자에게만 푸시 메시지를 전송해야 했습니다.
- **해결**: OneSignal의 External User ID 기능을 활용하여 Supabase User ID를 연결했습니다. 로그인 시 OneSignal.login(Supabase User ID)로 External User ID를 동기화하고, OneSignal에서 사용자 External ID 정보를 조회한 후 해당 푸시를 전송하도록 구현했습니다.
- **결과**: 구독한 사용자에게만 정확히 알림이 전송되도록 구현하여 타겟팅 푸시 발송을 안정화하고 사용자 경험을 개선했습니다.

## 🗂 버전 업데이트 (Release Notes)

### v1.0.2 (2026-01-19)
**Fixed**
- **로그아웃 상태에서 `[경기 알림 추가]` 클릭 시 로그인 안내 얼럿 미노출 문제 수정**
  - 현상: 로그아웃 상태에서 알림 추가 버튼 클릭 시 로그인 안내 얼럿이 나타나지 않음
  - 원인: 로그인 상태 체크 및 `showLoginAlert = true` 처리가 `Task {}` 내부에서 실행되어 UI 업데이트가 메인 스레드에서 보장되지 않음
  - 해결: 로그인 상태 체크/얼럿 표시 로직을 `Task {}` 외부로 분리하여 UI가 정상 갱신되도록 수정

- **알림 권한 승인 직후 첫 푸시 `notification_id` 빈 값 저장 문제 수정**
  - 현상: `[경기 알림 추가]` → 알림 권한 허용 후, 첫 푸시 `notification_id`가 빈 값으로 저장되어 푸시 메시지 전송 실패
  - 원인: 알림 권한 허용 직후 OneSignal 등록 타이밍 문제로 첫 푸시 `notification_id` 생성 전에 요청이 실행됨
  - 해결: 앱 실행 시 알림 권한을 먼저 요청하고, 권한 허용 이후 OneSignal 준비 완료 후 푸시 예약 요청이 실행되도록 타이밍 보완

---

### v1.0.1 (2026-01-17)
**Fixed**
- **경기 알림 추가 시 권한 요청 후 `notification_id` 생성되지 않던 문제 수정**
  - 원인: 알림 권한 요청(Alert) 확인 버튼 클릭과 동시에 알림 추가 로직이 실행되어 권한 승인 완료 전 OneSignal 요청이 수행됨
  - 해결: 비동기 처리 순서를 개선하여 권한 요청 완료 이후 알림 생성 로직이 실행되도록 수정

**Changed**
- 알림 권한 요청 완료 이후 알림 생성 로직이 실행되도록 처리 순서 개선
