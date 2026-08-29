# Ant Revolution — 홈페이지

**앤트레볼루션(Ant Revolution)** 의 원페이지 정적 사이트입니다. Cloudflare Pages로 서빙합니다.

🔗 **배포 주소: https://ant-revolution.pages.dev**

## 구성

```
index.html          사이트 전체 (CSS·JS 인라인, 빌드 과정 없음)
assets/             로고, 파비콘, OG 이미지 (원본 PNG에서 가공)
_headers            Cloudflare Pages 보안·캐시 헤더
robots.txt
.claude/launch.json 로컬 프리뷰용 설정 (배포에는 불필요)
```

## 로컬에서 미리보기

```bash
python -m http.server 8912
```

실행 후 http://localhost:8912 접속. 에셋 경로가 루트 절대경로(`/assets/...`)라서
`file://`로 직접 열지 말고 반드시 서버를 통해 열어야 합니다.

## Cloudflare Pages 배포

Cloudflare 대시보드에서 저장소를 연결하고(**Workers & Pages → Create → Pages → Connect to Git**) 아래 값을 사용합니다.

| 설정 항목 | 값 |
| --- | --- |
| Framework preset | None |
| Build command | *(비워둠)* |
| Build output directory | `/` |

또는 Wrangler로 바로 푸시:

```bash
npx wrangler pages deploy . --project-name=ant-revolution
```

## 남은 작업

`index.html`에서 `EDIT ME` 를 검색하면 교체할 자리표시자가 나옵니다.

- "Fields of work" 카드 3개 — 실제 제품이나 사례로 바꾸고 싶다면 교체
- `robots.txt`의 sitemap 주소, 그리고 `og:image` / canonical 호스트 — 커스텀 도메인을 연결한 뒤 갱신
  (현재는 `https://antrevolution.com` 기준으로 적혀 있고, 실제 배포는 `https://ant-revolution.pages.dev` 입니다)
