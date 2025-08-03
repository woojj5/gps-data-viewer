# GPS 데이터 전처리 및 시각화 파이프라인

GPS 차량 전처리, 데이터 분석(EDA), 시각화 리포트입니다.

---

## 🔍 주요 특징

- 디렉터리 단위의 차량 GPS 로그 통합 및 자동 전처리
- 이동 거리, 속도, 정지 여부 등 다양한 **파생 변수 생성**
- **월별 / 장치별 / 시간대별** 분석 및 시각화 리포트 자동 생성
- **차종별 교차 분석** (정지/운행 판별 등) 지원
- 주요 **요약 통계 / 상관계수** CSV 및 시각화 이미지 자동 저장

---

---

## 📦 설치 및 환경 설정

```bash
git clone https://github.com/yourusername/gps-preprocessing-pipeline.git
cd gps-preprocessing-pipeline
pip install -r requirements.txt
```

## ✅ 데이터 전처리 및 유틸리티 함수

haversine(lat1, lon1, lat2, lon2)
→ 두 GPS 좌표 간 거리(km) 계산

preprocess_gps(df)

→ 컬럼명 표준화, 시간 파싱, 이상치 제거, 파생 변수 생성

→ 범주형 인코딩, 월/시간대 추출

scan_all_csv_and_preprocess(root_dir, data_type)

→ 하위 폴더의 CSV 파일 자동 탐색 및 병합

→ 인코딩 처리 및 예외 처리 포함

---

## 📊 시각화 및 분석 함수

| 함수명                                             | 설명                            |
| ----------------------------------------------- | ----------------------------- |
| `plot_gps_monthly_distance()`                   | 월별 누적 주행거리 타임라인               |
| `plot_top_devices_by_distance()`                | 누적거리 기준 상위 20대 장치 바플롯         |
| `plot_month_device_heatmap()`                   | 월 × 장치 데이터 빈도 히트맵             |
| `plot_speed_distribution()`                     | 전체 속도 분포 히스토그램                |
| `plot_confusion_matrix_speed_stop_by_cartype()` | 차종별 정지/운행 판별 confusion matrix |
| `plot_hourly_distribution()`                    | 시간대별 기록 분포                    |
| `plot_correlation_heatmap()`                    | 주요 특성 간 상관계수 히트맵              |
| `plot_device_corr()`                            | 장치별 평균 속도-총 거리 상관             |
| `plot_monthly_speed_dist_corr()`                | 월별 속도-이동거리 상관 변화              |

---

## 🧩 TODO

1. **이상치 탐지 로직 고도화**
    
    - 다양한 이상치 탐지 기법 도입 및 변수별 맞춤 임계값 적용, 복합(멀티변량) 이상치 검출 등
        
2. **실시간 스트리밍 데이터 대응**
    
    - 스트리밍 데이터 실시간 ingest, 처리, 이상 탐지 및 알림 체계
        
3. **GUI 기반 리포트 뷰어 기능 추가**
    
    - 데이터 리포트 대시보드, 차트/테이블 실시간 갱신, PDF/Excel 등 내보내기
        
4. **BMS 관련 데이터 분석 기능 고도화**
    
    - BMS(배터리 관리 시스템) 데이터에 관한 전문 분석 모듈 추가 필요
        
    - SOH(충전상태) 트렌드, 셀 전압 불균형, 0V 셀 발생률, 차종별/기간별 주요 지표 자동 시각화
        
    - 누적 거리·에너지·온도·이상 상태 등 다양한 변수 간 상관관계 분석
        
    - 실시간/주기적 BMS 데이터 진단 및 리포트 자동 생성
        
    - 차종별 비교 분석, User Drill-down, 이상 구간 탐색 등 분석 확장성 제공
