# GPS 데이터 전처리 및 시각화 파이프라인

자동화된 GPS 로그 통합, 전처리, 탐색적 데이터 분석(EDA), 시각화 리포트 생성을 위한 Python 기반 모듈입니다.

---

## 🔍 주요 특징

- 디렉터리 단위의 차량 GPS 로그 통합 및 자동 전처리
- 이동 거리, 속도, 정지 여부 등 다양한 **파생 변수 생성**
- **월별 / 장치별 / 시간대별** 분석 및 시각화 리포트 자동 생성
- **차종별 교차 분석** (정지/운행 판별 등) 지원
- 주요 **요약 통계 / 상관계수** CSV 및 시각화 이미지 자동 저장

---

## 📦 설치 및 환경 설정

```bash
git clone https://github.com/yourusername/gps-preprocessing-pipeline.git
cd gps-preprocessing-pipeline
pip install -r requirements.txt

