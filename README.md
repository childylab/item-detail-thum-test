# 상품상세 & 썸네일 이미지 검증 도구

쇼핑몰 상품 등록 전, 상품상세 이미지와 썸네일 이미지 URL이 정상적으로 올라갔는지 실시간으로 검증하는 도구입니다.

## 배포 주소

**https://msparkman.netlify.app/baserow_live_test**

## Git Clone

```bash
git clone https://github.com/childylab/item-detail-thum-test.git
```

## 프로젝트 구조

```
├── index.html                  # 메인 게이트 페이지
├── baserow_live_test.html      # Baserow 실시간 검증 (핵심 도구)
└── README.md
```

## 사용 방법

1. 배포 주소 또는 로컬에서 `baserow_live_test.html` 열기
2. API Token 입력 (한 번 입력하면 브라우저에 저장됨)
3. 테이블(브랜드) 선택
4. "검증 시작" 클릭
5. 썸네일/상품상세/전체 탭으로 전환하며 검증

실패한 이미지는 빨간 테두리로 표시되고, 상단 실패 패널에 URL이 모아집니다.

---

## Baserow 연동

### 접속 정보

- Baserow URL: `https://baserow.childylab.com`
- API Token: Baserow 설정 → API 토큰에서 발급

### 테이블 위치 (26FW)

| 브랜드 | 테이블 ID | Baserow 링크 |
|--------|-----------|-------------|
| 아웃도어프로덕츠 (ODP) | 2179 | https://baserow.childylab.com/database/991/table/2179/6040 |
| 유니버셜오버롤 (UNIV) | 2182 | https://baserow.childylab.com/database/992/table/2182/6043 |
| 유니버셜오버롤 (UO 묶음) | 2186 | https://baserow.childylab.com/database/993/table/2186/6047 |
| 오디너리홀리데이 (OH) | 2212 | https://baserow.childylab.com/database/1024/table/2212/6073 |

---

## 브랜드별 필드 구조

### 아웃도어프로덕츠 ODP (테이블 2179)

| 필드명 | 설명 | 예시 |
|--------|------|------|
| 품번 | 상품 품번 | OD263ILS01 |
| 컬러코드 | 컬러 약어 | BLU, NVY, BRN |
| 상품명 | 상품 이름 | 멀티 스트라이프 티셔츠 |
| 상품상세코드 | HTML (img 태그 포함) | `<p align="center"><img src="...">` |
| ERP | ERP 썸네일 URL | thum/{품번}_{컬러}.jpg |
| ERP_ALL | 대표 썸네일 URL | thum/{품번}_ALL.jpg |
| 720 | 720px 썸네일 | (일부 상품만) |
| 750 | 750px 썸네일 | thum/{품번}_{컬러}_750.jpg |
| 800 | 800px 썸네일 | thum/{품번}_{컬러}_800.jpg |
| 960 | 960px 썸네일 | thum/{품번}_{컬러}_960.jpg |
| 1000 | 1000px 썸네일 (멀티라인 가능) | thum/{품번}_{컬러}_1000.jpg |
| 1500 | 1500px 썸네일 | thum/{품번}_{컬러}_1500.jpg |

### 유니버셜오버롤 UNIV (테이블 2182)

| 필드명 | 설명 | 예시 |
|--------|------|------|
| 품번 | 상품 품번 | UV263ILS01 |
| 컬러코드 | 컬러 약어 | MLG, IVY, NVY |
| 상품명 | 상품 이름 | 유니 로고 긴팔티셔츠 |
| 상품상세코드 | HTML | |
| ERP | ERP 썸네일 | thum/{품번}_{컬러}.jpg |
| ERP_ALL | 대표 썸네일 | thum/{품번}_ALL.jpg |
| 750 | 750px 썸네일 | |
| 800 | 800px 썸네일 | |
| 1000 | 1000px 썸네일 | |
| 1500 | 1500px 썸네일 | |

### 유니버셜오버롤 UO 묶음 (테이블 2186)

| 필드명 | 설명 | 예시 |
|--------|------|------|
| 품번 | 상품 품번 | UO263ISS01 |
| 컬러코드 | 컬러 약어 | ALL, BLK, WHT |
| 상품명 | 상품 이름 | 유니버셜 오버롤 기획 반팔티셔츠 |
| 상품상세코드 | HTML | |
| 960 | 960px 썸네일 | |
| 1000 | 1000px 썸네일 | |
| 1500 | 1500px 썸네일 | |

### 오디너리홀리데이 OH (테이블 2212)

| 필드명 | 설명 | 예시 |
|--------|------|------|
| 품번 | 상품 품번 | OH265AAB05 |
| 컬러 | 컬러 약어 | CHC, IVY |
| 상품명 | 상품 이름 | ZEBRA SHOULDER BAG |
| 상품상세코드 | HTML | |
| 960 | 960px 썸네일 (멀티라인) | |
| 1000 | 1000px 썸네일 (멀티라인) | |
| 1500 | 1500px 썸네일 (멀티라인) | |

> **참고:** OH, UO는 썸네일 필드에 여러 URL이 줄바꿈(`\n`)으로 구분되어 들어갈 수 있습니다. 검증 도구가 자동으로 분리해서 각각 검증합니다.

---

## 상품상세 이미지 구조 (브랜드별)

### ODP (아웃도어프로덕츠)

```
1. top_notice_odp.jpg          (공통 상단 안내)
2. 2026FA_intro.jpg            (시즌 인트로)
3. {품번}_txt.jpg              (상품 텍스트)
4. {품번}_{컬러}_model_c.jpg   (코디컷 - 일부 상품만)
5. {품번}_{컬러}_model.jpg     (모델컷)
6. {품번}_{컬러}_prd.jpg       (제품컷)
7. {품번}_{컬러}_detail.jpg    (디테일)
8. kc.jpg                      (KC인증)
9. modelspec.jpg               (모델 스펙)
10. size.jpg                   (사이즈 가이드 공통)
11. {품번}_size.jpg            (개별 사이즈표)
12. {품번}_check.jpg           (체크포인트)
13. washingtip.jpg             (세탁 안내)
14. delivery.jpg               (배송 안내)
```

### UNIV (유니버셜오버롤)

```
1. top_notice_univ.jpg         (공통 상단 안내)
2. intro_26fw.jpg              (시즌 인트로)
3. {품번}_txt.jpg              (상품 텍스트)
4. {품번}_model.jpg            (대표 모델컷)
5. {품번}_{컬러}_model.jpg     (컬러별 모델컷)
6. {품번}_{컬러}_detail.jpg    (디테일)
7. {품번}_info.jpg             (상품 정보)
8. {품번}_size.jpg             (사이즈표)
9. modelspec.jpg               (모델 스펙)
10. sizeguide.jpg              (사이즈 가이드)
11. kc.jpg                     (KC인증)
12. washingtip.jpg             (세탁 안내)
13. delivery.jpg               (배송 안내)
```

### UO (유니버셜오버롤 묶음)

```
1. {품번}_ALL.jpg              (전체 컬러 이미지)
2. {품번}_ALL_top.jpg          (상단)
3. {품번}_ALL_txt.jpg          (텍스트)
4. {품번}_ALL_event.jpg        (이벤트)
5. {품번}_{메인컬러}_top.jpg   (메인컬러 상단)
6. {품번}_{컬러}_model.jpg     (각 컬러별 모델컷)
7. {품번}_{메인컬러}_detail.jpg (디테일)
8. {품번}_size.jpg             (사이즈표)
9. {품번}_washingtip.jpg       (세탁)
```

### OH (오디너리홀리데이)

```
1. top_notice_ODNY.jpg         (공통 상단 안내)
2. {품번}_{컬러}_intro.jpg     (인트로)
3. {품번}_{컬러}_01.jpg        (이미지 1)
4. {품번}_{컬러}_02.jpg        (이미지 2)
5. {품번}_{컬러}_top.jpg       (상단)
6. {품번}_{컬러}_detail.jpg    (디테일)
7. {품번}_{컬러}_bottom_info.jpg (하단 정보)
```

---

## 썸네일 사이즈 규격

| 사이즈 | 용도 |
|--------|------|
| ERP | ERP 시스템용 기본 썸네일 |
| ERP_ALL | 대표 이미지 (ALL 컬러) |
| 720 | 720px (ODP 일부) |
| 750 | 750px |
| 800 | 800px |
| 960 | 960px |
| 1000 | 1000px (추가컷 `_1` 가능) |
| 1500 | 1500px |

---

## 새 브랜드/시즌 추가하기

1. Baserow에 새 테이블 생성 (필드: 품번, 컬러코드, 상품명, 상품상세코드, 썸네일 사이즈별)
2. `baserow_live_test.html`의 테이블 select에 옵션 추가:
   ```html
   <option value="새테이블ID">브랜드명 시즌 (테이블ID)</option>
   ```
3. 데이터 입력 후 바로 검증 가능

---

## 이미지 서버

모든 이미지는 `https://img.childy.kr/` 에서 호스팅됩니다.

| 브랜드 | 상품상세 경로 | 썸네일 경로 |
|--------|-------------|------------|
| ODP | `/img/outdoor2026/odp26_FA/` | `/img/outdoor2026/odp26_FA/thum/` |
| UNIV | `/img/univ/univ26_FA/` | `/img/univ/univ26_FA/thum/` |
| UO | `/img/UNIVERSALOVERALL/UO26_FA/` | `/img/UNIVERSALOVERALL/UO26_FA/thum/` |
| OH | `/img/ORDINARYHOLIDAY/ONDY26_FA/` | `/img/ORDINARYHOLIDAY/ONDY26_FA/thum/` |
