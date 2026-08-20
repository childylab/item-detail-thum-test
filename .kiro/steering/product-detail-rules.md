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
