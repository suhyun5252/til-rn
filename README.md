# apk 관련

## 1. QR 코드 생성

- https://me-qr.com/ko/qr-code-generator/link

## 2. 마켓에 등록하지 않은 상태로 외부인에게 앱파일을 전달하는 경우

```bash
cd android
```

```bash
./gradlew assembleRelease
```

- apk 별도 생성 작업

  - android/app/build/outputs/apk/release/app-release.apk 복사
  - /test/ 붙여넣고
  - /test/test.apk 로 변경

- github push 후 QR 생성 및 배포
