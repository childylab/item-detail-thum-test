# UO 26FW 상품상세코드 규칙

## 기본 경로
`https://img.childy.kr/img/UNIVERSALOVERALL/UO26_FW/`

하위에 `common/`과 `detail/` 폴더가 각각 존재함 (상하위 관계 아님).

## 이미지 순서 및 파일명

1. `common/26FW_main.jpg`
2. `common/26FW_intro.jpg`
3. `detail/{품번}_{컬러코드}_top.jpg`
4. `detail/{품번}_{컬러코드}_model.jpg`
5. `detail/{품번}_{컬러코드}_detail.jpg`
6. `detail/{품번}_size.jpg`
7. `common/26FW_washingtip_1.jpg`

## HTML 양식

각 이미지마다 아래 형태로 작성:

```html
<p align="center"><img title="" alt="" src="https://img.childy.kr/img/UNIVERSALOVERALL/UO26_FW/{폴더}/{파일명}"></p>
```

## Git 저장소

- GitHub: https://github.com/childylab/item-detail-thum-test
- 브랜치: main
- 검증기 파일: `index.html` (Baserow API 연동 이미지 검증, 게이트페이지 겸용)
- GitHub Pages: 비활성 상태 (필요시 Settings → Pages에서 main 선택)

## Baserow 테이블

- 테이블 ID: 2186
- `상품상세코드` 필드에 위 HTML을 넣음
- 컬러별로 각각 row가 존재하며, 컬러코드에 맞게 detail 이미지 파일명이 달라짐
- common 이미지와 size 이미지는 모든 컬러 공통

## 썸네일 규칙

- 기본 경로: `https://img.childy.kr/img/UNIVERSALOVERALL/UO26_FW/thum/`
- 파일명 패턴: `{품번}_{컬러코드}_{사이즈}_{번호}.jpg`
  - 사이즈: 960, 1000, 1500
  - 번호: 1~7
- Baserow 필드: `960`, `1000`, `1500` 각각에 URL 7개를 줄바꿈(`\n`)으로 구분하여 입력
- imsi 폴더에 파일명 참조용 파일이 들어있음 (워크스페이스 하위 imsi/)
- 썸네일 갯수는 품번/컬러별로 다를 수 있음 (6장 또는 7장). 실제 파일 갯수에 맞춰야 함
  - 7장: ILS01, OCD01, BPT03, BPT04_BLK, AAC01
  - 6장: ILS03, ILS04, BPT02, BPT04_KHA

## 차수 구분

- Baserow `차수` 필드로 배치 구분
  - `0`: FA 시즌 (UO263ISS01)
  - `1`: 26FW 1차 — ILS01, OCD01, ILS03, ILS04, BPT02, BPT03, BPT04, AAC01
  - `2`: 26FW 2차 — OJK01, 264OJK01, OJK04, IMM01, IMM02, BPT01, BPT05
- 검증기(index.html)에서도 배치 필터 드롭다운(전체/1차/2차)으로 분리 검증 가능
- 검증기 필터는 품번 기준 하드코딩 + Baserow `차수` 필드 병행

## 검증기 참고

- `index.html` 하나로 통합 (게이트페이지 겸용)
- 드롭다운: 테이블 선택 (아웃도어프로덕츠/UNIV/UO/오디너리홀리데이) + 배치 필터
- 테이블 표기: `UNIV 26FW`, `UO 26FW` (브랜드 풀네임 X)
- 썸네일 필드 내 줄바꿈(`\n`)으로 구분된 다건 URL을 각각 이미지 로드 검증
