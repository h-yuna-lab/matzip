# 🍽️ 천안맛ZIP

> “천안 내 상황에 딱 맞는 진짜 맛집을 찾다”

리뷰의 방문 상황·테마 데이터를 활용해 사용자의 방문 목적에 맞는 천안 맛집 선택을 돕는 웹 서비스입니다.

**5인 팀 프로젝트를 홍유나의 개인 포트폴리오로 정리한 통합 저장소**입니다. 사용자 React 화면과 Spring Boot·Thymeleaf 서버를 한곳에 모았으며, 개인 담당은 **리뷰 CRUD 공동 구현, 관리자 맛집 수정·삭제, 기능 테스트와 발표자료 제작**입니다.

## 프로젝트 개요

| 항목 | 내용 |
| --- | --- |
| 개발 기간 | 2026.05.08 ~ 2026.05.18 |
| 구성 | 5명 |
| 사용자 화면 | React · Vite |
| 관리자 화면·서버 | Thymeleaf · Spring Boot · JDBC/JdbcTemplate |
| 인증·DB | Spring Security 세션·쿠키 · Oracle |
| 외부 서비스 | Firebase Storage · Kakao Map |

## 주요 기능

- 맛집 목록·상세 조회와 카테고리·상황·테마 기반 탐색
- 별점·재방문 의사·상황 태그·이미지를 포함한 리뷰 작성·수정·삭제
- 리뷰 변경에 따른 평균 별점·리뷰 수 반영
- 사용자·관리자 권한 구분과 Thymeleaf 관리자 맛집 관리

## 홍유나 담당 업무

- 리뷰 화면·API CRUD 공동 구현, 이미지·상황 태그 연동
- 관리자 맛집 수정·삭제와 사용자 화면의 변경 결과 연결
- 리뷰 기능·권한·관리자 변경 결과와 사용자 데이터 일치 여부 확인
- 기획 배경·역할 분담·기능 흐름·구현 결과·테스트를 담은 발표자료 제작

공동 구현 범위와 상세 구현 흐름은 [프론트 README](frontend/README.md)와 [백엔드 README](backend/README.md)에 정리했습니다. 프로젝트 전체를 개인 단독 구현으로 표시하지 않습니다.

## 저장소 구성

| 폴더 | 내용 |
| --- | --- |
| [frontend](frontend/README.md) | React·Vite 사용자 화면, 이미지·지도 연동, 화면 캡처 |
| [backend](backend/README.md) | Spring Boot API, Thymeleaf 관리자 화면, SQL·서버 설정 |
| [SOURCE.md](SOURCE.md) | 통합 기준 저장소·커밋·보존 범위 |

각 모듈의 소스·문서·화면 이미지와 기존 커밋 이력을 가져왔습니다. 프론트와 백엔드는 각각 실행합니다.

## 주요 화면

기존 개인 포트폴리오 저장소에 등록된 프로젝트 화면을 함께 보관했습니다. 이번 통합에서 새로 촬영하거나 전체 연동을 다시 검증한 화면은 아닙니다.

![천안맛ZIP 메인](frontend/image/main.png)

| 맛집 상세 | 리뷰 작성 |
| --- | --- |
| ![맛집 상세](frontend/image/restaurant-detail.png) | ![리뷰 작성](frontend/image/review-write.png) |

전체 화면 목록은 [프론트 README](frontend/README.md)에 있습니다.

## 실행 방법

Node.js·Java 실행 환경과 Oracle DB를 준비합니다. 백엔드가 사용하는 Java 버전은 [Gradle 설정](backend/build.gradle)을 확인하세요. 먼저 [백엔드 실행 안내](backend/README.md)에 따라 DB·테이블·비공개 설정 파일을 준비합니다.

프론트 폴더의 `.env`에 다음을 설정합니다.

```env
VITE_API_BASE_URL=http://localhost:8111
```

### 터미널 1 · 백엔드

통합 저장소 루트에서 실행합니다.

```powershell
cd backend
.\gradlew.bat bootRun
```

macOS/Linux에서는 `./gradlew bootRun`을 사용합니다.

### 터미널 2 · 프론트엔드

통합 저장소 루트에서 실행합니다.

```powershell
cd frontend
npm install
npm run dev
```

- API·관리자 서버: `http://localhost:8111`
- 사용자 화면: Vite가 터미널에 표시한 주소
- DB·Firebase·Kakao Map의 설정 항목은 각 모듈 README를 확인하세요.

## 확인 범위

기존 README에는 리뷰 CRUD·관리자 변경 반영·권한별 접근 등 개발 당시 기능 확인 항목이 기록되어 있습니다. 이번 통합에서는 소스 파일 보존과 문서·이미지 링크를 확인하며, Oracle·외부 서비스를 포함한 전체 실행을 새로 검증하지 않았습니다.

## 프로젝트 회고

리뷰 CRUD를 공동 구현하고 관리자 맛집 수정·삭제, 기능 테스트와 발표자료 제작을 담당했습니다. 리뷰 한 건의 변경이 목록뿐 아니라 맛집의 평균 별점과 리뷰 수에도 영향을 주기 때문에, 화면에서 요청이 성공하는 것과 관련 데이터가 올바르게 반영되는 것을 함께 확인해야 한다는 점을 배웠습니다. 관리자 화면에서 변경한 정보가 사용자 화면에도 반영되는지 확인하며 기능 사이의 연결을 이해했습니다.

다음 프로젝트에서는 리뷰 등록·수정·삭제와 권한별 접근, 관리자 변경 결과의 사용자 화면 반영을 공통 테스트 시나리오로 정리하고 반복 확인을 자동화하고 싶습니다. 공동 구현한 기능은 요청·응답 형식과 담당 범위를 먼저 맞추고, 변경 사항을 문서에 함께 남겨 팀원이 이어서 확인하기 쉽게 개선하겠습니다.

## 출처

- [통합 기준 및 출처 기록](SOURCE.md)
- 원본 팀 [프론트엔드](https://github.com/SangHyunPark1213/human_mini_project2_frontend) · [백엔드](https://github.com/SangHyunPark1213/human_mini_project2_backend)
