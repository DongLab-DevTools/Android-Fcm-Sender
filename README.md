# Android-Fcm-Sender

Firebase Cloud Messaging(FCM) 테스트용 안드로이드 앱입니다.  
서버 없이 **앱 내에서 직접 FCM HTTP v1 API를 호출**하여 푸시 메시지를 전송할 수 있습니다.  
Firebase Console을 열거나 서버 코드를 수정하지 않아도, **로컬에서 즉시 푸시 전송 테스트**가 가능합니다.

---

## 기능 목적 (Purpose)

- **서버 의존 없이 푸시 테스트:**  
  백엔드 서버 없이, Android 클라이언트만으로 FCM HTTP v1 API를 직접 호출하여 테스트 가능
- **개발·QA 단계에서 유용:**  
  Notification 또는 Data payload 테스트, 포그라운드/백그라운드 수신 동작 검증에 활용
- **커스텀 데이터 전송:**  
  `title`, `body`, `priority`, `data` 등 모든 필드를 직접 입력 가능
- **로컬 JSON 키 업로드:**  
  Firebase 프로젝트의 `service-account.json` 파일을 앱에 업로드하여 인증

---

## 주요 기능 (Features)

| 분류 | 기능 설명 |
|------|------------|
| **API Key 파일 관리** | Firebase Service Account JSON 파일을 업로드 및 로드 |
| **Notification 필드 구성** | `title`, `body`, `priority`, `image`, `channelId` 등 푸시 알림 속성 직접 입력 |
| **Data 필드 구성** | 임의의 `key-value` 데이터를 자유롭게 추가 |
| **푸시 우선순위 설정** | `high`, `normal` 등 메시지 우선순위 선택 |
| **푸시 전송 기능** | `https://fcm.googleapis.com/v1/projects/{projectId}/messages:send` 엔드포인트 직접 호출 |
| **결과 로그 출력** | 성공/실패 응답 및 서버 응답 코드 표시 |
| **UI 기반 조작** | 코드 수정 없이 앱 내 UI에서 필드 입력 및 전송 버튼 클릭만으로 동작 |

---

## 사용 방법 (Usage)

1. Firebase Console에서 **서비스 계정 키(JSON)** 파일을 다운로드  
   - 경로: **프로젝트 설정 → 서비스 계정 → 새 비공개 키 생성**
2. 앱 실행 → "파일 선택" 클릭 → 해당 JSON 파일 업로드
3. `Notification` 또는 `Data` 필드 입력
4. `푸시 전송` 버튼 클릭 → 즉시 전송 결과 확인

> 💡 실제 디바이스 토큰(Token)을 `to` 필드에 입력하면  
> 특정 기기 대상으로 바로 푸시 테스트를 진행할 수 있습니다.

---

## 스크린샷

| 메인 화면 | JSON 미업로드 시 |
|:--:|:--:|
| <p align="center"><img src="https://github.com/user-attachments/assets/164afd0c-24d8-4844-b578-472b9e864d4f" width="280" height="560" style="object-fit:contain;"></p> | <p align="center"><img src="https://github.com/user-attachments/assets/26c3e82c-7c24-43e5-af59-c08e98d37ef3" width="280" height="560" style="object-fit:contain;"></p> |

| Notification 속성 설정 | Data-only 푸시 전송 | 푸시 데이터 삭제 |
|:--:|:--:|:--:|
| <p align="center"><img src="https://github.com/user-attachments/assets/872da42c-231d-4512-b277-e2ccff9fb7e2" width="280" height="560" style="object-fit:contain;"></p> | <p align="center"><img src="https://github.com/user-attachments/assets/23963942-7706-4584-b4d7-40589d1c4da9" width="280" height="560" style="object-fit:contain;"></p> | <p align="center"><img src="https://github.com/user-attachments/assets/e738fbde-8d34-425e-9f72-4ffeb551911a" width="280" height="560" style="object-fit:contain;"></p> |
