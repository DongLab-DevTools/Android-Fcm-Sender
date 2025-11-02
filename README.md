# Android-Fcm-Sender

Firebase Cloud Messaging(FCM) 테스트를 위한 안드로이드 애플리케이션입니다.  
서버 없이 앱에서 직접 FCM HTTP v1 API를 호출하여 푸시 메시지를 전송하고 테스트할 수 있습니다.

## 📌 개요

개발 및 QA 단계에서 푸시 알림 기능을 빠르게 검증할 수 있는 도구입니다.  
Firebase Console이나 별도의 백엔드 서버 없이 로컬에서 푸시 메시지를 구성하고 전송할 수 있습니다.

## ✨ 주요 기능

- **서비스 계정 키 관리** - Firebase Service Account JSON 파일 업로드
- **Notification 필드 구성** - title, body, image, channelId 등 설정
- **Data 필드 구성** - 커스텀 key-value 데이터 추가
- **우선순위 설정** - high/normal 메시지 우선순위 지정
- **실시간 전송 테스트** - FCM API 직접 호출 및 응답 확인
- **UI 기반 조작** - 코드 수정 없이 앱에서 간편하게 테스트

## 🚀 사용 방법

1. Firebase Console에서 서비스 계정 비공개 키(JSON) 다운로드  
   `프로젝트 설정 → 서비스 계정 → 새 비공개 키 생성`

2. 앱 실행 후 JSON 파일 업로드

3. 수신 디바이스 토큰 및 메시지 내용 입력

4. 전송 버튼 클릭 후 결과 확인

## 🛠 기술 스택

| 항목 | 내용 |
|------|------|
| **언어** | Kotlin |
| **플랫폼** | Android (minSdk 24) |
| **API** | Firebase Cloud Messaging HTTP v1 |
| **인증** | Google Service Account OAuth2 (JWT) |
| **라이브러리** | Retrofit2, Gson, OkHttp |

## 📱 스크린샷

<table>
  <tr>
    <td align="center"><b>메인 화면</b></td>
    <td align="center"><b>JSON 미업로드</b></td>
    <td align="center"><b>속성 설정</b></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/164afd0c-24d8-4844-b578-472b9e864d4f" width="240"></td>
    <td><img src="https://github.com/user-attachments/assets/26c3e82c-7c24-43e5-af59-c08e98d37ef3" width="240"></td>
    <td><img src="https://github.com/user-attachments/assets/872da42c-231d-4512-b277-e2ccff9fb7e2" width="240"></td>
  </tr>
  <tr>
    <td align="center"><b>Notification 전송</b></td>
    <td align="center"><b>Data 전송</b></td>
    <td align="center"><b>데이터 삭제</b></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/735ea9e4-8323-4938-9c5a-081711ea270e" width="240"></td>
    <td><img src="https://github.com/user-attachments/assets/23963942-7706-4584-b4d7-40589d1c4da9" width="240"></td>
    <td><img src="https://github.com/user-attachments/assets/e738fbde-8d34-425e-9f72-4ffeb551911a" width="240"></td>
  </tr>
</table>

## 🔜 예정된 기능

- **전송 이력 관리** - 이전 메시지 저장 및 재전송
- **로그 뷰어** - 수신 성공/실패 로그 확인
- **템플릿 시스템** - 자주 사용하는 메시지 구조 저장
- **Payload 미리보기** - JSON 포맷팅 및 전송 전 검증
- **테마 지원** - Dark/Light 모드 전환
