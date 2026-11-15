# AVEN

현대자동차그룹 차량용 앱 개발 공모전 — 팀 MSG

## 앱 이름 및 한 줄 소개

**AVEN** — 경로에서 크루즈에 위임해도 되는 구간과 직접 운전해야 하는 구간을 출발 전에 미리 알려주고, 직접 운전할 타이밍을 가상 리허설로 대비시켜주는 주행보조 운전자용 내비게이션 앱.

## 실행 방법

### 1) 웹 동작 프로토타입 (차량용 UI, APK와 동일 화면)

- 접속: https://kimwinner.github.io/msg/car/
- 파일을 열고 **"자동 시연 보기"**를 누르면 브리핑 → 리허설 → 주행 → 리포트 전체 흐름을 바로 볼 수 있다.
- 같은 화면이 Android WebView 앱의 UI로도 그대로 쓰인다.
- 리허설 영상은 주차(P) 상태에서만 재생되고, 출발이 감지되면 바로 멈춘다. 주행 중에는 화면 조작이 잠기고 음성으로만 응답한다.

### 2) APK (Pleos Connect 에뮬레이터)

1. [`apk/MSG_AVEN_release.apk`](apk/MSG_AVEN_release.apk)를 Pleos Connect 에뮬레이터(AVD)에 설치한다.
2. 앱을 실행하고 위치 권한을 허용한다.
3. Virtual Console에서 조향각·브레이크 값을 조작하면 Vehicle SDK를 통해 앱 화면에 그대로 반영되는 것을 확인할 수 있다.

## 테스트 환경 및 필요한 설정

- Pleos Connect v2.1.0 에뮬레이터에서 실행 확인.
- AVD Cold boot로 기동해야 Virtual Console의 조향각·브레이크·크루즈 값이 Vehicle SDK로 정상 전달된다(Quick boot 시 VHAL 미동작).
- 위치 권한을 허용해야 실제 주행 안내(GPS)·유의지점 음성 안내·주행 리포트 기능이 동작한다.
- 사용 SDK: Vehicle(DrivingMode/Brake/SteeringWheel), FusedLocation, NaviHelper, TextToSpeech, SpeechToText.

## 개발에 사용한 Pleos Connect 에뮬레이터 버전과 화면 규격

- 에뮬레이터: Pleos Connect Emulator v2.1.0 (시스템 이미지 Android API 34, Form Factor: Automotive)
- AVD 설정: RAM 4GB, Boot option: Cold boot (Quick boot 시 VHAL 사용 불가)
- 화면 규격: 16:9 가로형 차량 디스플레이 (공식 문서에 해상도 수치 미기재, 화면 녹화 기준 약 1914x1074로 표시됨)
- 앱 최소 SDK: Android API 28 이상

## APK 파일 위치

- [`apk/MSG_AVEN_release.apk`](apk/MSG_AVEN_release.apk)

---

## 참고: 데스크탑 미리보기 (휴대폰용 경로 검색 프로토타입)

열기: https://kimwinner.github.io/msg/

- 휴대폰: 위치 권한을 허용하면 현재 위치에서 출발하는 실제 주행 안내(GPS), 유의지점 500m 전 음성 안내, 크루즈 개입 기록, 음성 체크인, 주행 리포트까지 동작합니다. 브라우저 메뉴의 "홈 화면에 추가"로 앱처럼 실행할 수 있습니다.
- 데스크탑: 경로 검색, 예상 소요시간, 유의지점 시뮬레이션, 모의 주행만 볼 수 있는 미리보기입니다.

데이터: 지도 OpenFreeMap · © OpenMapTiles · © OpenStreetMap contributors, 경로 OSRM, 검색 Photon · Nominatim, 도로 시설 Overpass API, 실시간 고속도로 소통·휴게소 한국도로공사 고속도로 공공데이터 포털.

## 참고: 차량용 (리허설 3D + 주행 규제 준수)

- 차량 모니터(가로로 넓은 화면)·휴대폰·아이폰(Safari, "홈 화면에 추가") 모두 같은 주소로 엽니다.
- 리허설 영상은 주차(P) 상태에서만 재생되고, 출발이 감지되면 바로 멈춥니다(도로교통법 제49조 제1항 제11호, Pleos 앱 심사 가이드).
- 주행 중에는 화면 조작을 잠그고 "준비", "여기 위험해" 같은 음성으로만 응답합니다(같은 조 제11호의2).
- 차량 신호는 Android 앱(Kotlin)이 `window.RMVehicle.update({ cruise, brake, steer, signal, gear, speed, ux, light })`로 넘겨 줍니다.
- 지도 OpenFreeMap · © OpenMapTiles · © OpenStreetMap contributors, 경로 OSRM·TMAP, 돌발상황 ITS, 3D 차량 모델 Kenney Car Kit(CC0).
