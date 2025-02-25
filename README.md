# React Native

[앱 개발시 선택하는 방법]

- Native (Java, Kotlin, Swift, Objective-C) 말고 `Flutter` 또는 `React Native` 사용
- React Native 개발 도구 : `Expo` , `React Native CLI` 사용
- React Native CLI 는 환경설정이 까다로움
- iOS , Android 개발이 가능한데 , iOS 는 반드시 Mac 에서 개발

## 환경설정

- https://velog.io/@it-ju/React-native-cli-개발환경-세팅하기
- https://reactnative.dev/docs/0.72/environment-setup

### 1. choco 설치 및 환경확인

- PowerShell `관리자 권한 실행`
- https://chocolatey.org/install

- 아래 문장을 입력후 엔터

```bash
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

- Power Shell 에 `choco` 입력후 버전 출력되었는지 확인

```bash
Chocolatey v2.4.2
Please run 'choco -?' or 'choco <command> -?' for help menu.
```

- choco를 이용해서 설치 필요

```bash
choco install -y nodejs-lts microsoft-openjdk17
```

### 2. Android Studio 설치

- https://developer.android.com/studio?hl=ko

#### 2.1 시작화면에서 > More Actions > SDK Manager 클릭

#### 2.2 File > settings... 메뉴

#### 2.3. Android SDK 세팅

- Android API 35("VanillaIceCream")

```
  Android SDK Platform 35
  ARM 64 v8a System Image
  Intel x86_64 Atom System Image
  Google APIs ARM 64 v8a System Image
  Google APIs Intel x86_64 Atom System Image
  Google Play ARM 64 v8a System Image
  Google Play Intel x86_64 Atom System Image
```

- Android 14.0("UpsideDownCake")

```
Android SDK Platform 34
Source for Android 34
ARM 64 v8a System Image
Intel x86_64 Atom System Image
Google APIs ARM 64 v8a System Image
Google APIs Intel x86_64 Atom System Image
Google Play ARM 64 v8a System Image
Google Play Intel x86_64 Atom System Image
```

- Android 13.0("Tiramisu")

```
Android SDK Platform 33
ARM 64 v8a System Image
Intel x86_64 Atom System Image
Google APIs ARM 64 v8a System Image
Google APIs Intel x86_64 Atom System Image
Google Play ARM 64 v8a System Image
Google Play Intel x86_64 Atom System Image
```

#### 2.4. SDK Tools 세팅

- Android SDK Buil-Tools 36-rc5
- NDK
- CMake
- Android Emulator
- Android Emulator hypervisor driver
- Android SDK Platform-Tools
- Google Play Service

#### 2.5. Android SDK Location 을 복사

```
C:\Users\Administrator\AppData\Local\Android\Sdk
```

#### 2.6. Android Virtual Device

- 시작화면에서 > More Action 에서 > Virtual Machine Manager 실행 후 추가
- 또는 우축 화면 상단의 Device Manager 에서 추가
- `Pixcel 7' 으로 생성하자.

### 3. Path 설정

- 윈도우 하단 툴바의 검색창에서 `시스템 환경 변수` 검색
- `환경 변수 버튼` 클릭
- 새로 만들기
  - 변수명 : `ANDROID_HOME`
  - 변수값 : `C:\Users\Administrator\AppData\Local\Android\Sdk`
- 수정 및 추가
- `path` 항목 더블 클릭
- 항목 추가 : `%ANDROID_HOME%\platform-tools`
- 확인 버튼 클릭

### 4. Path 설정 실행 확인(Power Shell 관리자 모드)

- `Get-ChildItem -Path Env:\` 엔터
- `adb --version` 엔터
- 결과가 안나오면 PC를 껐다가 켜고 다시 시도

## 프로젝트 생성

- 절대 한글 폴더에 생성 금지
- 절대 특수기호가 포함된 앱이름 금지
- `npx react-native@0.72.6 init 앱이름 --version 0.72.6`

## 프로젝트 실행 전 반드시 준비

- Android Studio 실행 > Device Virtual Marchine 을 실행해 놓고 진행

### 만약 실행이 안되면 해 보아야 하는 것

- `cd android` 로 anodroid 폴더로 이동
- 터미널에 `./gradlew clean` 으로 프로젝트 다시 초기화
- 완료 후 `cd ..` 상위폴더 이동
- 다시 `npm run start` 실행 후 결과 확인
- 그래도 안되면 `npx react-native doctor` 명령으로 현재 상태 확인 후 조치

# Webview 적용하기

- https://www.npmjs.com/package/react-native-webview
- `npm i react-native-webview`

# 추후 브랜치

- webview
- splash screen
- icon
- back 키
- apk 생성
- webview 와 js 연동

```tsx
import React from 'react';
import {SafeAreaView, StyleSheet} from 'react-native';
import WebView from 'react-native-webview';

const App = (): JSX.Element => {
  const webViewUrl = 'https://app-fish-y3pa.vercel.app';
  // const webViewUrl = 'http://112.222.157.157:5234/';
  return (
    <SafeAreaView style={styles.container}>
      <WebView source={{uri: webViewUrl}} style={styles.webView} />
    </SafeAreaView>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#111',
  },
  webView: {
    flex: 1,
  },
});

export default App;
```
