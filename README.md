# GPS 데이터 전처리 및 시각화 파이프라인

자동화된 GPS 로그 통합, 전처리, 탐색적 데이터 분석(EDA), 시각화 리포트 생성을 위한 Python 기반 모듈입니다.

## 🔍 주요 특징

- 디렉터리 단위의 차량 GPS 로그 통합 및 자동 전처리
- 이동 거리, 속도, 정지 여부 등 다양한 **파생 변수 생성**
- **월별 / 장치별 / 시간대별** 분석 및 시각화 리포트 자동 생성
- **차종별 교차 분석** (정지/운행 판별 등) 지원
- 주요 **요약 통계 / 상관계수** CSV 및 시각화 이미지 자동 저장

---

## 📦 설치 및 환경 설정

git clone https://github.com/yourusername/gps-preprocessing-pipeline.git
cd gps-preprocessing-pipeline
pip install -r requirements.txt
🔧 폰트 설정
한글 시각화를 위해 Malgun Gothic 폰트를 자동 설정하며, tkinter 기본 폰트도 함께 사용됩니다.

---

🚀 사용 방법
분석할 GPS CSV 파일들을 하위 폴더에 구성

aicar_cartype_list.csv (차종 테이블) 포함

---

🛠️ 주요 함수 및 구조
✅ 데이터 전처리 및 유틸리티
haversine(lat1, lon1, lat2, lon2): 두 지점 간 거리(km) 계산

preprocess_gps(df):

컬럼명 표준화 및 시간 파싱

이상치 제거

파생 변수 생성 (속도, 거리, 정지여부 등)

범주형 인코딩, 월/시간대 추출

scan_all_csv_and_preprocess(root_dir, data_type):

하위 폴더의 CSV 자동 탐색 및 병합

인코딩 처리 및 예외 처리 포함

---

📊 시각화 및 분석 함수
함수명	설명
plot_gps_monthly_distance()	월별 누적 주행거리 타임라인
plot_top_devices_by_distance()	누적거리 기준 상위 20대 장치 바 플롯
plot_month_device_heatmap()	월 × 장치 데이터 빈도 히트맵
plot_speed_distribution()	전체 속도 분포 히스토그램
plot_confusion_matrix_speed_stop_by_cartype()	차종별 정지/운행 판별 confusion matrix
plot_hourly_distribution()	시간대별 기록 분포
plot_correlation_heatmap()	주요 특성 간 상관계수 히트맵
plot_violin_stopped_diff()	정지여부별 violin plot
plot_device_corr()	장치별 평균 속도 - 총 거리 상관
plot_monthly_speed_dist_corr()	월별 속도-이동거리 상관 변화

---

📁 모든 이미지(.png) 및 요약 통계(.csv)는 지정 폴더에 자동 저장됩니다.
⏱️ 자동 저장 후 일정 시간이 지나면 창은 자동 종료됩니다.

---

📂 디렉터리 구조 예시

---

gps-preprocessing-pipeline/
│
├── data/
│   ├── 2023-01/
│   │   ├── gps_log_01.csv
│   │   └── ...
│   └── aicar_cartype_list.csv
│
├── outputs/
│   ├── images/
│   ├── stats/
│   └── logs/
│
├── main.py
├── preprocessing.py
├── visualization.py
└── README.md

---

📌 TODO
이상치 탐지 고도화

실시간 스트리밍 데이터 대응

GUI 기반 리포트 뷰어 추가

---

📄 라이선스
MIT License

--- 

필요 시 다음도 추가 가능합니다:
- 예시 이미지
- 데모 실행 결과
- 성능 비교표 (EDA 시간/파일 수 기준)

수정이나 확장할 부분 있다면 알려주세요!
