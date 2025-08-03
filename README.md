# gps-data-viewer

GPS 데이터 전처리 및 시각화 파이프라인
자동화된 GPS 로그 통합, 전처리, 탐색적 데이터 분석(EDA) 및 시각화 리포트 생성을 위한 파이썬 기반 모듈입니다.

특징
여러 차량 GPS 로그를 디렉터리 단위로 일괄 통합 및 자동 전처리

이동거리, 속도, 정지여부 등 다양한 파생변수 생성

월별, 장치별, 시간대별 데이터 분포 및 분석 결과 시각화

차종별 교차분석(정지/운행 판별 등) 지원

주요 요약 통계 및 상관계수 CSV, 시각화 이미지 자동 저장

주요 기능 및 구조
환경 및 폰트 설정
한글 데이터 정상 시각화를 위해 Malgun Gothic 폰트와 tkinter 기본 폰트 설정

환경설정(저장 경로, delay 등) 커스터마이징 가능

데이터 전처리 및 유틸리티
haversine(): 위/경도 좌표 간 거리를 km 단위로 계산

preprocess_gps(df):

컬럼명 표준화, 시간 파싱, 이상치 제거, 이동거리·정지여부·방향 증분 등 파생 변수 생성

범주형 변수 인코딩 및 월/시간대 추출

scan_all_csv_and_preprocess(root_dir, data_type):

모든 하위폴더의 CSV 자동 스캔/인코딩 처리 및 데이터 유형별 전처리

에러 파일 예외처리 및 자동 병합

시각화 및 EDA 함수
월별 누적주행거리 타임라인(plot_gps_monthly_distance)

누적거리 기준 상위 20대 장치 바플롯(plot_top_devices_by_distance)

월X장치 데이터 빈도 히트맵(plot_month_device_heatmap)

전체 속도 분포 히스토그램(plot_speed_distribution)

차종별 정지판별 confusion matrix(plot_confusion_matrix_speed_stop_by_cartype)

시간대별 기록 분포(plot_hourly_distribution)

주요 특성 간 상관계수 히트맵(plot_correlation_heatmap)

정지여부별 violin plot(plot_violin_stopped_diff)

장치별 평균속도-총거리 상관(plot_device_corr)

월별 속도-이동거리 상관 변화(plot_monthly_speed_dist_corr)

모든 플롯은 지정 폴더에 PNG·CSV로 자동 저장 & 일정 시간 후 자동 종료

메인 실행 절차
폴더 내 모든 GPS CSV 통합 전처리

외부 차종 테이블(aicar_cartype_list.csv)로 장치 번호별 차종 병합

분석/시각화 함수 호출(주석 해제 등으로 선택 실행)

주요 요약/상관/분석 결과는 root dir에 저장
