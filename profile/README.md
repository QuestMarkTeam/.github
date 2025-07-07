# Cluvr Organization

**Cluvr**는 사용자가 클럽(스터디, 프로젝트, 커뮤니티 등)을 생성하고, 실시간 채팅 및 알림을 통해 소통하며, 활동 내역을 분석받을 수 있도록 지원하는 **소셜 커뮤니티 플랫폼**입니다.
본 Organization은 플랫폼 전반을 구성하는 4개의 핵심 서버로 이루어져 있으며, 각 서버는 독립적인 역할을 수행하며 모듈 간 통신을 통해 통합 동작합니다.

---

## Repository 구성

| 서버                  | 설명                                                     |
| -------------------- | ------------------------------------------------------ |
| `cluvrapi`           | 클럽 생성/참여, TIL 작성, 커뮤니티 기능 등을 제공하는 **백엔드 API 서버**       |
| `cluvr-chat`         | 클럽 내 **실시간 채팅 기능**을 제공하는 WebSocket 기반 서버               |
| `cluvr-notification` | 채팅, 신청 승인, 댓글 등 **다양한 알림을 전송하는 서버**    |
| `cluvr-batch`        | OpenAI 기반 피드백, 주간 요약 처리, 좋아요 및 조회수 등 **정기적 백그라운드 작업을 수행하는 배치 서버** |
| `cluvr-front`        | 클럽 탐색, 가입, 커뮤니티 활동, 실시간 채팅을 지원하는 React 기반 웹 클라이언트 |

---

## 핵심 기능 요약

<details> <summary><b> 클럽 기능(cluvrapi)</b></summary>
  <li>  클럽 생성/참여, 가입양식 관리, TIL 및 커뮤니티 게시판</li>
  <li>  사용자 프로필, 점수 시스템(클로버), 내공(젬) 연동</li>
</details>

<details> <summary><b> 실시간 채팅 (cluvr-chat)</b></summary>
  <li>  WebSocket 기반 채팅</li>
  <li>  클럽 별 채널 구조 지원</li>
  <li>  채팅 알림 연동</li>
</details>

<details> <summary><b> 알림 서버 (cluvr-notification)</b></summary>
  <li>  클럽 가입 승인, 댓글, 채팅 알림 등 다채로운 이벤트 기반 알림 발송</li>
  <li>  Firebase Cloud Messaging(FCM) 연동</li>
</details>

<details> <summary><b> 배치 서버 (cluvr-batch)</b></summary>
 <li>  클로버 로그 적재</li>
 <li>  젬 로그 적재</li>
 <li>  OpenAI 기반 TIL 피드백 분석 </li>
 <li>  게시판 통계 적재 </li>
 <li>  게시글 조회수 적재 </li>
</details>

---

## 🛠기술 스택

| 영역           | 기술                                        |
| ------------ | ----------------------------------------- |
| Backend      | Java 17, Spring Boot 3.x                  |
| Realtime     | WebSocket, STOMP, Redis Pub/Sub           |
| Notification | Firebase Cloud Messaging, Kafka           |
| Batch        | Spring Batch, MongoDB (임시 캐시), OpenAI API |
| Infra        | AWS, Docker, Nginx, MySQL, Redis          |
| Monitoring   | Prometheus, Grafana                       |
| Testing      | JMeter, RestAssured, Testcontainers       |

---

## 공통 설정 및 CI/CD

* 공통 `.env` 또는 `application.yml` 설정이 필요할 수 있습니다.
* GitHub Actions, Jenkins 기반 CI/CD (각 레포지토리 참고)
* Docker 및 docker-compose 기반 로컬 개발환경 구성 가능

---

## 참고 문서

* [API 서버 문서](https://github.com/QuestMarkTeam/cluvr-api/wiki)
* [Batch 서버 문서]([https://github.com/QuestMarkTeam/cluvr-batch](https://github.com/QuestMarkTeam/cluvr-batch#cluvr-batch))
* [Chat 서버 문서](https://github.com/QuestMarkTeam/cluvr-chat/wiki)
* [Notifiaction 서버 문서](https://github.com/QuestMarkTeam/cluvr-notification#cluvr-notifications-service)


