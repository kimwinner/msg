# msg
현대 앱개발 공모전

## 레디맵 ReadyMap 웹 프로토타입

휴대폰에서 열기: https://kimwinner.github.io/msg/

- 휴대폰: 위치 권한을 허용하면 현재 위치에서 출발하는 실제 주행 안내(GPS), 유의지점 500m 전 음성 안내, 크루즈 개입 기록, 음성 체크인, 주행 리포트까지 동작합니다. 브라우저 메뉴의 "홈 화면에 추가"로 앱처럼 실행할 수 있습니다.
- 데스크탑: 경로 검색, 예상 소요시간, 유의지점 시뮬레이션, 모의 주행만 볼 수 있는 미리보기입니다.

데이터: 지도 OpenFreeMap · © OpenMapTiles · © OpenStreetMap contributors, 경로 OSRM, 검색 Photon · Nominatim, 도로 시설 Overpass API, 실시간 고속도로 소통·휴게소 한국도로공사 고속도로 공공데이터 포털.

## 레디맵 차량용 (리허설 3D + 주행 규제 준수)

열기: https://kimwinner.github.io/msg/car/

- 차량 모니터(가로로 넓은 화면)·휴대폰·아이폰(Safari, "홈 화면에 추가") 모두 같은 주소로 엽니다.
- 리허설 영상은 주차(P) 상태에서만 재생되고, 출발이 감지되면 바로 멈춥니다(도로교통법 제49조 제1항 제11호, Pleos 앱 심사 가이드).
- 주행 중에는 화면 조작을 잠그고 "준비", "여기 위험해" 같은 음성으로만 응답합니다(같은 조 제11호의2).
- 차량 신호는 Android 앱(Kotlin)이 `window.RMVehicle.update({ cruise, brake, steer, signal, gear, speed, ux, light })`로 넘겨 줍니다.
- 지도 OpenFreeMap · © OpenMapTiles · © OpenStreetMap contributors, 경로 OSRM·TMAP, 돌발상황 ITS, 3D 차량 모델 Kenney Car Kit(CC0).
