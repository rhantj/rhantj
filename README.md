`AI · DATA · BACKEND ENGINEERING`

# 고무서

시스템을 설계하고 구현하는 개발자

| | |
| --- | --- |
| **GitHub** | [@rhantj](https://github.com/rhantj) |
| **Portfolio** | [rhantj.github.io](https://rhantj.github.io/) |
| **Games** | [rhantj.github.io/games](https://rhantj.github.io/games/) |
| **Focus** | LLM · RAG · ML · Spring Boot · FastAPI |

---

`— CONTENTS`

| | | |
| --- | --- | --- |
| **01** | [기술 스택](#-01--tech-stack) | 언어 · 프론트엔드 · 백엔드 · ML/AI |
| **02** | [주요 프로젝트](#-02--featured-projects) | 협업 플랫폼 · 감성분석 · 생성모델 · 예측모델 |
| **03** | [활동 지표](#-03--metrics) | GitHub Stats |

---

`— 01 · TECH STACK`

## 기술 스택

| 구성 | 기술 |
| --- | --- |
| **Languages** | ![C++](https://img.shields.io/badge/C++-00599C?style=flat-square&logo=cplusplus&logoColor=white) ![C](https://img.shields.io/badge/C-A8B9CC?style=flat-square&logo=c&logoColor=white) ![C#](https://img.shields.io/badge/C%23-239120?style=flat-square&logo=csharp&logoColor=white) ![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black) |
| **Frontend** | ![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black) ![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white) ![Tailwind CSS](https://img.shields.io/badge/Tailwind-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white) |
| **Backend** | ![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white) |
| **Data** | ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white) ![pgvector](https://img.shields.io/badge/pgvector-4169E1?style=flat-square&logo=postgresql&logoColor=white) |
| **ML / AI** | ![LLM](https://img.shields.io/badge/LLM-412991?style=flat-square&logo=openai&logoColor=white) ![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white) ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white) ![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white) ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikitlearn&logoColor=white) |
| **Infra** | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![NGINX](https://img.shields.io/badge/NGINX-009639?style=flat-square&logo=nginx&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white) |
| **Graphics** | ![Unity](https://img.shields.io/badge/Unity-000000?style=flat-square&logo=unity&logoColor=white) ![VFX](https://img.shields.io/badge/VFX-000000?style=flat-square&logo=adobeaftereffects&logoColor=white) |

---

`— 02 · FEATURED PROJECTS`

## 주요 프로젝트

### ▸ [work-flow](https://github.com/rhantj/work-flow)

팀 프로젝트의 **회의록 → 업무 → 진행률 → 산출물 → 기여도**를 하나의 데이터 흐름으로 잇는 협업·평가 보조 플랫폼.
회의록을 올리면 요약·결정사항·To-Do가 자동 생성돼 업무 보드와 대시보드에 반영되고, LightGBM이 업무 지연 위험과 업무 편중을 예측하며, pgvector RAG 어시스턴트가 출처를 붙여 답한다.

```
React (nginx) → Spring Boot (인증·RBAC·도메인) → FastAPI (LLM·RAG·ML 추론)
                                                  ├── PostgreSQL + pgvector
                                                  ├── Redis
                                                  └── Ollama / Hugging Face
```

`Spring Boot` `FastAPI` `React` `LangGraph` `pgvector` `LightGBM` `Whisper` `Docker`

[**Live Demo**](https://t3-workflow-ai.site) · [Repository](https://github.com/rhantj/work-flow)

---

### ▸ [review-check](https://github.com/rhantj/review-check)

Steam 게임 리뷰 641만 건에서 균형 샘플을 뽑아 감성을 분류하고, LLM이 장단점을 요약하며, RAG가 근거를 붙여 답하는 웹 데모.
비사전학습(LSTM)과 사전학습(DistilBERT)을 같은 조건에서 비교해 전이학습의 효과를 정량 검증했다.

| 모델 | Accuracy | F1 |
| --- | --- | --- |
| LSTM (비사전학습) | 0.763 | 0.753 |
| **DistilBERT (사전학습)** | **0.856** | **0.855** |

`LSTM` `DistilBERT` `Qwen2.5` `LangChain` `Chroma` `Streamlit`

[**Live Demo**](https://review-check-oyfyk5sun59hw3tinasxkr.streamlit.app/) · [Repository](https://github.com/rhantj/review-check)

---

### ▸ [lpc-sprite-vae](https://github.com/rhantj/lpc-sprite-vae)

LPC 64×64 RGBA 스프라이트 프레임을 생성하는 VAE 기반 이미지 생성 프로젝트.
키워드 조합으로 5개 레이어를 각각 CVAE로 생성한 뒤 합성한다.

`VAE` `CVAE` `β-VAE` `Perceptual Loss` `TensorFlow` `PyTorch`

[**Live Demo**](https://lpcsprite.streamlit.app/) · [Repository](https://github.com/rhantj/lpc-sprite-vae)

---

### ▸ [Heart-Disease](https://github.com/rhantj/Heart-Disease)

UCI Heart Failure 데이터셋 기반 심장질환 위험 예측.
여러 분류 모델을 비교해 최적 모델을 선정하고 웹 앱으로 배포했다.

`Logistic Regression` `Random Forest` `XGBoost` `LightGBM` `Streamlit`

[**Live Demo**](https://heartdiseasemachine.streamlit.app/) · [Repository](https://github.com/rhantj/Heart-Disease)

---

`— 03 · METRICS`

## 활동 지표

<p align="left">
  <img height="165" src="https://github-readme-stats.vercel.app/api?username=rhantj&show_icons=true&hide_border=true&bg_color=0e1116&title_color=ff7a59&text_color=e8edf3&icon_color=4fd1c5" />
  <img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=rhantj&layout=compact&hide_border=true&bg_color=0e1116&title_color=ff7a59&text_color=e8edf3" />
</p>

<p align="left">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=rhantj&hide_border=true&background=0e1116&stroke=2a323d&ring=ff7a59&fire=ff7a59&currStreakLabel=4fd1c5&sideLabels=8b97a6&dates=8b97a6&currStreakNum=e8edf3&sideNums=e8edf3" />
</p>

---

`— APPENDIX`

이 README와 프로젝트 보고서에 쓰인 슬라이드 덱 디자인 규칙은 [보고서 덱 스타일 가이드](docs/report-deck-style.md)에 정리되어 있습니다.

더 많은 작업물은 [포트폴리오 사이트](https://rhantj.github.io/)에서,
Unity·웹 게임은 [게임 포트폴리오](https://rhantj.github.io/games/)에서 확인할 수 있습니다.
