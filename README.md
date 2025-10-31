# Android-Fcm-Sender

Android-Fcm-Sender는 Firebase Cloud Messaging(FCM) 테스트용 안드로이드 애플리케이션입니다.  
서버 없이 앱 내에서 직접 FCM HTTP v1 API를 호출하여 푸시 메시지를 전송할 수 있습니다.  
Firebase Console이나 별도의 서버 환경 없이, 로컬에서 푸시 메시지를 구성하고 테스트하는 데 유용합니다.

---

## 기능 목적

- 서버 없이 푸시 메시지를 전송할 수 있는 테스트 도구
- Notification 및 Data 필드를 자유롭게 구성하여 FCM 수신 테스트 가능
- 개발 및 QA 단계에서 푸시 수신 로직 검증에 활용
- 실제 FCM 전송 형식을 그대로 사용하여 실환경과 동일한 동작 테스트 가능

---

## 주요 기능

| 분류 | 설명 |
|------|------|
| **서비스 계정 키 관리** | Firebase Service Account JSON 파일 업로드 및 로드 지원 |
| **Notification 필드 구성** | title, body, image, channelId 등 알림 필드를 직접 입력 |
| **Data 필드 구성** | 임의의 key-value 데이터 추가 가능 |
| **푸시 우선순위 설정** | high, normal 등 메시지 우선순위 지정 |
| **FCM API 호출** | `https://fcm.googleapis.com/v1/projects/{projectId}/messages:send` 엔드포인트 직접 호출 |
| **응답 로그 출력** | 요청 결과 및 HTTP 응답 코드 표시 |
| **UI 기반 조작** | 코드 수정 없이 앱 UI에서 입력 후 버튼 클릭만으로 테스트 가능 |

---

## 기술 명세

| 항목 | 내용 |
|------|------|
| 플랫폼 | Android |
| 언어 | Kotlin |
| API | Firebase Cloud Messaging HTTP v1 |
| 인증 | Google Service Account OAuth2 (JWT) |
| 최소 SDK | 24 |
| 필요한 권한 | INTERNET |
| 주요 라이브러리 | Retrofit2, Gson, OkHttp |

---

## 사용 방법

1. Firebase Console에서 서비스 계정 비공개 키(JSON) 파일을 다운로드  
   (경로: 프로젝트 설정 → 서비스 계정 → 새 비공개 키 생성)
2. 앱 실행 후 JSON 파일 업로드
3. Notification 또는 Data 필드 입력
4. 전송 버튼 클릭 후 결과 확인

> 실제 디바이스 토큰을 입력하면 해당 기기에 바로 푸시를 전송할 수 있습니다.

---

## 스크린샷

| 메인 화면 | JSON 파일 미업로드 시 | Notification 속성 설정 |
|:--:|:--:|:--:|
| <p align="center"><img src="https://github.com/user-attachments/assets/164afd0c-24d8-4844-b578-472b9e864d4f" width="280" height="560" style="object-fit:contain;"></p> | <p align="center"><img src="https://github.com/user-attachments/assets/26c3e82c-7c24-43e5-af59-c08e98d37ef3" width="280" height="560" style="object-fit:contain;"></p> | <p align="center"><img src="https://github.com/user-attachments/assets/872da42c-231d-4512-b277-e2ccff9fb7e2" width="280" height="560" style="object-fit:contain;"></p> |

| 푸시 전송 (Notification 필드 포함) | 푸시 전송 (Data 필드만 포함) | 푸시 데이터 삭제 |
|:--:|:--:|:--:|
| <p align="center"><img src="https://github.com/user-attachments/assets/735ea9e4-8323-4938-9c5a-081711ea270e" width="280" height="560" style="object-fit:contain;"></p> | <p align="center"><img src="https://github.com/user-attachments/assets/23963942-7706-4584-b4d7-40589d1c4da9" width="280" height="560" style="object-fit:contain;"></p> | <p align="center"><img src="https://github.com/user-attachments/assets/e738fbde-8d34-425e-9f72-4ffeb551911a" width="280" height="560" style="object-fit:contain;"></p> |
