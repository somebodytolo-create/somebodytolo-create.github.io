# 다음, 커리어

대구·경북 연구행정·기업지원·창업지원 채용 아카이브.

- 이 디렉터리만 채용 보드에 사용합니다. 루트 index.html, robots.txt 및 기존 KIAPI 저장소는 변경하지 않습니다.
- 공개 게시물의 채용정보만 `data/jobs.json`에 저장합니다. 지원자의 이력서, 회사 내부자료, 개인정보, 연락처, 개인 메모는 올리지 않습니다.
- 관심 공고, 지원 단계, 메모는 이용자 브라우저의 localStorage에만 보관합니다. 기기 간 자동 동기화는 하지 않습니다.
- 직무·고용형태·실제 근무지·필수자격이 검증되지 않은 공고는 `review`입니다. 확인되지 않은 마감일과 시간은 null로 유지합니다.
- 만료된 공고는 삭제하지 않고 화면에서 마감 보관함으로 분류합니다.
- 정기 확인은 기존 ChatGPT 채용 확인 작업에서 공개 채용정보 파일을 갱신하는 방식으로 연결합니다. 예약 등록과 예약 실행 성공은 구분합니다.

## 자료 구조

`schemaVersion: 1`, `generatedAt`, `collection`, `jobs`, `sources`를 유지합니다.
`collection.lastAttemptAt`는 실제 검색 시각, `lastSuccessAt`는 정상 확인 시각입니다. 업로드 시각만으로 검색 성공을 기록하지 않습니다.
각 공고는 `id`, `organization`, `title`, `role`, `category`, `employment`, `workplace`, `region`, `postedOn`, `opensOn`, `deadline`(date,time,zone), `sourceId`, `sourceUrl`, `applyUrl`, `sourceType`, `verification`, `requirements`, `fitReasons`, `cautions`, `evidence`, `firstSeenAt`, `lastVerifiedAt`, `history`를 사용합니다.
`verification`: matched(모집조건 확인), conditional(경력 인정 등 조건 확인), review(미검증 후보), excluded(추천 제외 보관).
`matched`는 정규직 모집단위·대구/경북 실제 근무지·필수자격 확인 근거가 있어야 하며, 합격 가능성을 의미하지 않습니다.

외부 공고 내용은 데이터로만 다루고 코드나 지시로 실행하지 않습니다.
