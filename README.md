<div align="center">

# 현종화 · JongHwa Hyun

**A Developer under Development**

<a href="https://github.com/hynzzong?tab=repositories"><img src="https://img.shields.io/badge/Repositories-181717?style=flat-square&logo=github&logoColor=white"></a>

</div>

<br>

## 🛠 Tech Stack

**Backend**<br>
![Java](https://img.shields.io/badge/Java_17-007396?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot_3-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white)
![JPA](https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=flat-square&logo=spring&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white)

**AI / ML**<br>
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![ONNX](https://img.shields.io/badge/ONNX-005CED?style=flat-square&logo=onnx&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_SDK-D97757?style=flat-square&logo=anthropic&logoColor=white)

**Infra & Tools**<br>
![AWS](https://img.shields.io/badge/AWS_EC2·RDS·S3·SES-232F3E?style=flat-square&logo=amazonwebservices&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Gradle](https://img.shields.io/badge/Gradle-02303A?style=flat-square&logo=gradle&logoColor=white)

<br>

## 🚀 Projects

### 🎓 WishConnect — 장학금 큐레이팅 플랫폼

> 흩어진 장학금 정보를 한곳에 모아, **나에게 자격이 되는 공고만** 골라주는 서비스<br>
> [wish-connect.com](https://wish-connect.com) · [api.wish-connect.com](https://api.wish-connect.com)

대학생이 장학금을 놓치는 이유는 정보가 없어서가 아니라 너무 흩어져 있어서입니다.
한국장학재단 공공 API와 전국 대학 장학공지를 매일 배치로 수집·정제하고,
사용자의 학적·소득분위·거주지역·관심분야로 조건을 판정해 지원 가능한 공고만 보여줍니다.
마감 알림, 스크랩, AI 자기소개서 작성, 면접 준비까지 한 흐름으로 묶었습니다.

| Repository | Stack | 설명 |
|---|---|---|
| **[api-server](https://github.com/WishConnect/api-server)** | Java 17 · Spring Boot 3.3 · PostgreSQL · Redis · AWS | Java 파일 417개 · 엔티티 42개 · 테스트 클래스 78개 |
| **[frontend](https://github.com/WishConnect/frontend)** | React 19 · TypeScript · Vite · Tailwind · Zustand | Vercel 배포 |

**담당 파트 (BE)**
- 전국 대학 장학공지를 구조화하는 **LLM 파서**와 대학별 전용 수집기 레지스트리
- 서로 다른 출처에서 들어온 **중복 장학금 판정 · 병합 승인 큐**
- 장학금 공고별 **자기소개서 문항 생성**
- **면접 예상 질문 · 면접 준비 자료 생성**

<br>

### 🏁 AMET 2026 자율주행 해커톤 — Physicar

> 2026 자율주행 해커톤 경진대회 (한국자율주행산업협회 주최 · 2026.8.25~8.27 · 코엑스)<br>
> [amet-2026-autonomous-driving](https://github.com/hynzzong/amet-2026-autonomous-driving)

1/10 스케일 모형차 Physicar로 12m × 7m 트랙을 완주하는 랩타임 경쟁입니다.
`source run.sh` 한 번으로 완전 오프라인·비대화형 자율주행을 수행해야 합니다.

**담당 파트 — 차선(주행 복도) 인식**

GPU 없는 라즈베리파이에서 돌려야 해서, 픽셀 단위 세그멘테이션 대신
**고정된 12개 높이에서 x좌표를 회귀**하는 형태로 문제를 축소했습니다.

| 항목 | 내용 |
|---|---|
| 입력 | 224 × 168 RGB 1장 |
| 백본 | MobileNetV3-Small (전이학습) |
| 출력 | 높이별 `target_x` / `left_x` / `right_x` + 각각의 visibility |
| 배포 | ONNX + `model_contract.json` (행 위치·임계값을 계약으로 고정) |
| 데이터셋 | 9개 독립 녹화 세션 · 2,178 프레임 (직접 수집·라벨링) |

카메라 한 프레임을 트랙 인식과 YOLO 객체 인식이 공유하고,
`cone` bbox 각도 구간을 같은 방향의 LiDAR 클러스터와 연결해 매 프레임 지역 경로를 다시 고릅니다.
센서·제어 이상이 감지되면 즉시 정지하는 안전 조건을 기본값으로 두었습니다.

<br>

## 📚 KUIT 7기 · Server Part 스터디

건국대학교 IT 동아리 KUIT 7기 서버 파트에서 진행한 주차별 미션입니다.
프레임워크를 쓰기 전에 **그 프레임워크가 대신해주던 것을 직접 구현**해보는 순서로 진행했습니다.

| 주차 | 주제 | Repository |
|:---:|---|---|
| 1 | 문자열 계산기 — 요구사항 분해와 TDD | [string-calculator](https://github.com/hynzzong/string-calculator) |
| 2 | Parallel GC vs G1 GC — 힙 로그로 동작 차이 분석 | [KUIT7_Server_Week2_GC](https://github.com/hynzzong/KUIT7_Server_Week2_GC) |
| 3 | WAS 직접 구현 — HTTP 요청/응답 처리 | [KUIT7_Server-Custom-Tomcat](https://github.com/hynzzong/KUIT7_Server-Custom-Tomcat) |
| 4 | FrontController 패턴으로 Servlet MVC 구조 개선 | [KUIT7_Server_Week4_MVC](https://github.com/hynzzong/KUIT7_Server_Week4_MVC) |
| 5 | 직접 만든 MVC를 Spring Boot로 전환 + 트랜잭션 | [KUIT7_Server_Week5_Spring](https://github.com/hynzzong/KUIT7_Server_Week5_Spring) |
| 7 | JPA로 배달앱 REST API 설계·구현 | [KUIT7_REST-API](https://github.com/hynzzong/KUIT7_REST-API) |
| 8 | JWT 인증/인가 + Interceptor로 API 보호 | [KUIT7_Server-Auth](https://github.com/hynzzong/KUIT7_Server-Auth) |

<br>

## 📈 GitHub

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=hynzzong&theme=github_dark">
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=hynzzong&theme=github" alt="GitHub Stats" height="200">
</picture>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=hynzzong&theme=github_dark">
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=hynzzong&theme=github" alt="Most Commit Language" height="200">
</picture>

</div>
