# 천안맛ZIP 프론트엔드 · 기술 안내

React·Vite 사용자 화면의 실행·API 연결 안내입니다. 프로젝트 소개·담당 업무·화면·회고는 [최상위 README](../README.md)에 있습니다.

## 의존성

React, Vite, JavaScript, Axios, CSS, Firebase Storage, Kakao Map API를 사용합니다. 버전과 실행 스크립트는 [package.json](package.json)을 확인하세요.

## 실행·환경 설정

이 `frontend` 폴더에 `.env` 파일을 생성합니다.

```env
VITE_API_BASE_URL=http://localhost:8111
```

패키지를 설치하고 개발 서버를 실행합니다.

```bash
npm install
npm run dev
```

백엔드 서버가 실행된 상태에서 프론트엔드 서버를 실행해야 합니다.

## 프로덕션 빌드

`frontend` 폴더에서 실행합니다.

```bash
npm run build
npm run preview
```

개발·미리보기 주소는 Vite가 터미널에 표시한 주소를 확인하세요.

## 리뷰·이미지 처리 순서

1. 맛집 상세에서 리뷰 작성을 선택합니다.
2. 별점·내용·재방문 의사와 상황·테마를 입력합니다.
3. Firebase Storage에 이미지를 업로드합니다.
4. 반환된 이미지 URL과 리뷰 데이터를 서버 Review API에 전송합니다.
5. 등록 완료 후 리뷰 목록을 갱신합니다.

로그인 상태를 유지하도록 Axios 요청에 세션 쿠키를 포함합니다.

```javascript
const api = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL,
  withCredentials: true,
});
```

백엔드의 세션·권한과 리뷰 API는 [백엔드 기술 안내](../backend/README.md)에 있습니다.

## 상황·테마 입력

리뷰에서 상황·테마를 복수 선택하며 맛집 상세에서 많이 선택된 태그를 추천 상황으로 표시합니다. 입력 항목과 이미지 제한은 백엔드 API와 함께 확인하세요.

## 확인 범위

이번 문서 정리에서는 코드와 이미지 위치를 보존하고 링크를 확인했습니다. 전체 서비스 실행 결과를 새로 측정하지 않았으며 개발 당시 기능 테스트 항목은 [백엔드 기술 안내](../backend/README.md)에 있습니다.

## 문서

- [프로젝트 포트폴리오·화면·회고](../README.md)
- [백엔드 API·DB·서버 설정](../backend/README.md)
- [통합 출처](../SOURCE.md)
