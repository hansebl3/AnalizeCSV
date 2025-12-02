    • 리눅스 서버에서 도커로 돌아가는 웹어플리케이션
    • csv파일을 현지에서 불러와서 컬럼내용을 간략히 보여주고 필요한 컬럼의 시간에대한 그래프를 그려주는 앱
    • 컬럼 중에 시간컬럼을 선택, 그래프를 그릴 컬럼을 선택
    • 상단에 전체 데이터 시간에 대한 변화추이를 보여주고, 시간범위를 설정할수 있는 슬라이드바가 있음
    • 시간범위가 지정되면 메인그래프영역의 왼쪽에 시간에 따른 데이터 추이, 오른쪽에는 히스토그램을 보여줌
    • 그래프의 x, y축에 들어갈 레이블을 수정할수 있음
    • 이미지파일로 현지pc에 저장

## Docker 실행 방법 (DB 설정 저장 포함)

1. **이미지 빌드:**
   ```bash
   docker build -t csv-analyzer .
   ```

2. **컨테이너 실행:**
   DB 설정(`db_config.json`)을 유지하려면 아래 명령어로 실행하세요.
   ```bash
   docker run -d \
     --network host \
     -v $(pwd)/db_config.json:/app/db_config.json \
     --name csv-analyzer-app \
     csv-analyzer
   ```

3. **접속:**
   브라우저에서 [http://localhost:8501](http://localhost:8501) 로 접속하세요.
