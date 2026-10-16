# 명일방주 리세계 찾기 아이디팜 전용

원본 판매사이트와 같은 계정 검색 화면을 제공하며, 판매 링크와 가격은 아이디팜만 표시합니다. 가격 필터와 가격 정렬도 표시된 아이디팜 최종 결제가 기준입니다. 오퍼레이터 및 잠재 검색은 원본과 같습니다.

- 전용 사이트: https://mbreset.github.io/arknights-accounts-search-idfarm/
- 원본 사이트: https://mbreset.github.io/arknights-accounts-search/
- 저장소: https://github.com/mbreset/arknights-accounts-search-idfarm
- 아이디팜 판매글: https://idfarm.co.kr/ItemMarket/gameItem/1543613

## 데이터 갱신

계정 데이터와 오퍼레이터 스프라이트는 원본 사이트의 `data/accounts.json`과 `assets/operators.png`를 직접 읽습니다. 원본 판매 데이터가 갱신되면 전용 사이트에도 같은 데이터가 표시됩니다. 별도 데이터 복사나 재배포는 필요하지 않습니다.

Vite의 `publicDir`는 꺼져 있습니다. 로컬 `public/`에 남아 있는 복사본은 배포하거나 읽지 않습니다. 방문자 통계는 원본과 같은 Cloudflare Worker를 사용하며 두 사이트의 방문 횟수가 합산됩니다. `worker/`는 공유 통계 서버의 참고 소스이며 별도의 통계 서버를 생성할 필요가 없습니다.

## 실행과 검증

```powershell
npm ci
npm run dev
npm run build
node --test tests/operator-search.test.mjs
```

개발 서버의 `/arknights-accounts-search-idfarm/tests/operator-search.html`에서 가상 데이터 기반 브라우저 테스트를 실행합니다. 아이디팜 전용 링크와 가격, 가격 필터 경계값, 검색 동작을 검사합니다. 테스트는 실제 방문자 API에 요청하지 않습니다.

## 배포

`main`에 푸시하면 `.github/workflows/deploy-pages.yml`이 빌드하여 GitHub Pages에 배포합니다. 저장소 Pages 설정은 GitHub Actions 방식으로 사용합니다. 원본 판매사이트 저장소와 배포는 별도로 유지됩니다.
