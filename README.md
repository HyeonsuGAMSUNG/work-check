# 감성사운드 업무 체크

남현수(마케팅·강의 기획)의 전체 업무 정리 사이트: https://hyeonsugamsung.github.io/work-check/

- **광고 효율 보고서**: 광고 동향, 소재별 일별 성과, 일별 광고 액션의 이유와 결과, A/B 테스트, 채널별 일 비용, 상담 → 등록 성과
- **업무 리마인드**: 오늘 꼭 / 이번 주 / 대기, 일별 내가 한 일, 진행·예정 클래스, 고정 데일리 업무, 다가오는 일정, 누락 점검
- **광고 마케팅 예정**: 날짜가 정해진 것, 판단 대기

`index.html`은 화면만, 내용은 전부 `data.js`(`window.WORK = {...};`)에 있다.

## 공개 저장소 규칙

- 상담자·수강생 실명은 성+○○(예: 박○○). 전화번호·이메일은 넣지 않는다.
- 발송 대상은 인원수로만 적는다.

## data.js 키

| 키 | 내용 |
|---|---|
| `meta` | 마지막 갱신 시각, 기준 노션 페이지 |
| `tasks` | 미완료 `{id, group: today/week/wait, tag, title, note, since, due, flag: old/dup/stale}` |
| `log` | 일별 내가 한 일 `[{date, items:[{title, why, result, tag}]}]`. tag가 `광고`면 보고서 탭에도 나온다 |
| `plans` | 광고 마케팅 예정 `{date 또는 "", title, channel, why, status, est}` |
| `projects` | 진행·예정 클래스 `{name, who, lecture, open, note}` |
| `ads.insights` | 광고 동향 `{date, text}` |
| `ads.campaigns` | 소재 `{id, name, product, market, channel, meta, angle, start, status}` |
| `ads.daily` | `{date, campaign, cost, ctr, clicks, cpc, partial}` |
| `ads.tests` | A/B `{name, start, why, variants:[{name, stat}], result, status}` |
| `ads.channelDaily` | 채널별 일 비용 `{days, rows:[{name, v}]}` |
| `fixed` / `missing` / `consults` / `schedule` | 고정 업무, 누락 후보, 상담 집계, 10일 이내 일정 |

## 갱신 (요청할 때만)

1. 광고 캡처: `ads.daily` 추가 → 전날 대비 분석을 `ads.insights`에 → 예산·소재 변경은 `log`에 "이유 → 결과"로 → `ads.tests`, `plans` 상태 갱신
2. 업무: 노션 주간업무·상담 일지를 다시 읽어 `tasks`, `missing`, `fixed`, `consults`, `schedule` 갱신. `ads`, `log`, `plans`, `projects`는 덮어쓰지 않는다
3. `git pull --ff-only` → commit → `git push`. 1~2분 뒤 사이트 반영

GitHub에서 `data.js`를 직접 고쳐도 된다. 쉼표·따옴표가 하나라도 틀리면 화면이 비니 큰 수정은 클로드에게 맡긴다.
