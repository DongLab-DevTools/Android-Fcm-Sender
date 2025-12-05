# Android-Fcm-Sender

[![Hits](https://myhits.vercel.app/api/hit/https%3A%2F%2Fgithub.com%2FDongLab-DevTools%2FAndroid-Fcm-Sender%3Ftab%3Dreadme-ov-file?color=blue&label=hits&size=small)](https://myhits.vercel.app)
[![Platform](https://img.shields.io/badge/platform-Android-3DDC84?style=flat-square&logo=android)](https://developer.android.com)
[![Min SDK](https://img.shields.io/badge/min%20sdk-24-green?style=flat-square)](https://developer.android.com)
[![Jitpack](https://jitpack.io/v/DongLab-DevTools/Android-Fcm-Sender.svg)](https://jitpack.io/#DongLab-DevTools/Android-Fcm-Sender)

**[English README](./README.md)**

## 개요

Android-Fcm-Sender는 Firebase Cloud Messaging(FCM) 테스트를 위한 라이브러리로, 백엔드 서버 없이 안드로이드 디바이스에서 직접 푸시 알림을 전송할 수 있는 Activity를 제공합니다.

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

<br>
<br>

개발 및 QA 단계에서 푸시 알림 기능을 빠르게 검증할 수 있는 라이브러리입니다. 

프로젝트에 추가하고 제공되는 Activity를 통해, Firebase Console이나 별도의 백엔드 서버 없이 FCM HTTP v1 API를 사용하여 로컬에서 푸시 메시지를 구성하고 전송할 수 있습니다.

<br>

## 주요 기능

- **서비스 계정 키 관리**: Firebase Service Account JSON 파일 업로드 및 관리
- **Notification 필드 구성**: title, body, image, channelId 등 알림 속성 설정
- **Data 필드 구성**: 커스텀 key-value 데이터 페이로드 추가
- **우선순위 설정**: 메시지 우선순위(high/normal) 지정
- **실시간 전송 테스트**: FCM API 직접 호출 및 응답 확인
- **UI 기반 조작**: 사전 빌드된 Activity 인터페이스로 간편하게 테스트

<br>

## 설치

### Step 1: Jitpack 저장소 추가

프로젝트의 `settings.gradle.kts`에 Jitpack 저장소를 추가합니다:

```kotlin
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven { url = uri("https://jitpack.io") }
    }
}
```

### Step 2: 의존성 추가

모듈의 `build.gradle.kts`에 라이브러리를 추가합니다:

```kotlin
dependencies {
    implementation("com.github.DongLab-DevTools:Android-Fcm-Sender:latestVersion")
}
```

<br>

### 요구사항

- Android API 24 (Android 7.0) 이상
- Cloud Messaging이 활성화된 Firebase 프로젝트
- Firebase Service Account JSON 키 파일

<br>

## 사용법

### FCM Sender Activity 실행

앱 내 어디서든 FCM Sender Activity를 실행하세요:

```kotlin
import android.content.Intent
import com.your.package.FcmSenderActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        // FCM Sender Activity 실행
        findViewById<Button>(R.id.openFcmSender).setOnClickListener {
            val intent = Intent(this, FcmSenderActivity::class.java)
            startActivity(intent)
        }
    }
}
```

### FCM Sender 화면 사용하기

1. **Firebase 서비스 계정 키 획득**
   - [Firebase Console](https://console.firebase.google.com/)로 이동
   - 프로젝트 선택
   - **프로젝트 설정 → 서비스 계정**으로 이동
   - **새 비공개 키 생성** 클릭 후 JSON 파일 다운로드

2. **JSON 파일 업로드**
   - FCM Sender Activity에서 업로드 버튼 탭
   - Service Account JSON 파일 선택
   - 앱이 자격 증명을 파싱하고 저장

3. **메시지 구성**
   - **Device Token**: 대상 디바이스의 FCM 등록 토큰 입력
   - **Title**: 알림 제목
   - **Body**: 알림 메시지 본문
   - **Image URL**: (선택사항) 리치 알림을 위한 이미지 URL
   - **Channel ID**: Android 알림 채널 ID
   - **Priority**: HIGH 또는 NORMAL 선택

4. **메시지 전송**
   - **전송** 버튼을 탭하여 FCM HTTP v1 API를 통해 전송
   - 응답 상태와 오류 확인

<br>

## 기술 스택

| 항목 | 내용 |
|------|------|
| **언어** | Kotlin |
| **플랫폼** | Android (minSdk 24) |
| **API** | Firebase Cloud Messaging HTTP v1 |
| **인증** | Google Service Account OAuth2 (JWT) |
| **라이브러리** | Retrofit2, Gson, OkHttp |

<br>

## 예정된 기능

- **전송 이력 관리**: 이전 메시지 저장 및 재전송
- **로그 뷰어**: 전송 성공/실패 로그 확인
- **템플릿 시스템**: 자주 사용하는 메시지 구조 저장
- **Payload 미리보기**: JSON 포맷팅 및 전송 전 검증
- **테마 지원**: Dark/Light 모드 전환

<br>