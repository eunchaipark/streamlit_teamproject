# 미리보기 
![image](https://github.com/user-attachments/assets/e37d200c-c0d0-4589-b658-3c9aaffa4366)

# Members

- [@eunchaipark](https://github.com/eunchaipark)
- [@awesome98](https://github.com/awesome98)
- [@yeji63](https://github.com/yeji63)
- [@dongmiii](https://github.com/dongmiii)
- [@eunhyea](https://github.com/eunhyea)
- [@SukbeomH](https://github.com/SukbeomH)

# streamlit_practice :: 따릉이 데이터 시각화

- `streamlit`을 활용하여 따릉이 데이터를 시각화
- `pandas` 데이터 전처리, 데이터프레임 생성
- `pydeck` 지도 시각화
- `geopy` 거리 계산, 좌표 정보 활용
- `requests` API 요청

## Example Page

[streamlit_cycle](https://practice001.streamlit.app/)

## 따릉이 데이터 시각화
- 따릉이 데이터를 활용하여 시각화를 진행합니다.
- 데이터는 **서울 열린 데이터 광장**에서 제공하는 따릉이 데이터를 활용합니다.

---

## 주요 기능
- 따릉이 대여소의 **위치를 지도에 시각화**합니다.
- 사용자가 입력한 위치로부터 **가장 가까운** 따릉이 대여소를 찾아줍니다.
- Streamlit의 **세션 관리**로 인한 새로고침 시 정보 증발을 방지하고, 사용자가 입력한 위치 정보를 유지합니다.
- 없어진 대여소를 제외하고 전처리를 진행합니다.
- 중복 API 요청을 방지하기 위해 **로컬에 데이터를 저장**합니다.

## 개선 사항
- **다크모드 지원**
  - 사이드바의 다크모드 시 글자가 보이지 않는 현상을 개선합니다.
- 대여소 **정보 표시**
  - 대여소 정보를 마커 클릭 시 표시하도록 개선합니다.
  - 자전거 실시간 현황을 표시하도록 개선합니다.
- 기존 서비스를 참고하여 추가적인 기능을 개발합니다.
  - 대여소 **정보를 표시**하는 기능을 추가합니다.
  - 대여 빈도를 통한 **혼잡도, 인기도 등을 시각화**합니다.

---

## 데이터 소개

- 데이터 주소 : [서울 열린 데이터 광장](https://data.seoul.go.kr/dataList/OA-21235/S/1/datasetView.do)
- 따릉이 데이터는 서울시 자전거 대여소별 대여정보를 제공합니다.
- 폐쇄된 대여소의 경우, 좌표 정보가 제공되지 않으므로 (0, 0)으로 표기되어 있습니다.
  - 이러한 대여소는 전처리 과정에서 필터링하여 제외하였습니다.

## 시각화 및 활용
- pydeck을 활용하여 지도 시각화를 진행합니다.
- 대여소의 좌표정보를 이용해서 사용자가 기입한 위치로 부터 가까운 대여소를 찾아주는 기능을 제공합니다.
  - 좌표 간의 거리 계산의 경우, geopy의 geodesic 함수를 활용하였습니다.

## 세팅 방법
```bash
$ git clone {repository} {directory}
$ pip install -r requirements.txt
$ streamlit run main.py
```

## 참고
- [서울 열린 데이터 광장](https://data.seoul.go.kr/dataList/OA-21235/S/1/datasetView.do)
- [pydeck](https://deckgl.readthedocs.io/en/latest/)
- [geopy](https://geopy.readthedocs.io/en/stable/)
- [requests](https://docs.python-requests.org/en/master/)

---

## 배운 점
- **API 활용**: `requests`를 통해 외부 API를 호출하고, 서울시 자전거 대여소 데이터를 활용하는 방법을 배웠습니다. 이를 통해 실시간으로 데이터를 처리하는 경험을 쌓았습니다.
- **데이터 전처리**: `pandas`를 이용한 데이터 정제와 필터링을 통해 유효하지 않은 데이터를 걸러내는 과정을 통해 데이터 분석의 중요성을 깨달았습니다.
- **시각화 도구**: `pydeck`을 활용한 지도 시각화를 통해 공간적 데이터를 효율적으로 표시하는 방법을 배웠습니다. `geopy`를 활용하여 거리 계산과 위치 데이터를 다루는 기술을 익혔습니다.

## 느낀 점
- **데이터의 중요성**: 실제 서비스를 위한 데이터가 얼마나 중요한지 깨닫게 되었습니다. 예를 들어, 폐쇄된 대여소를 필터링하고, 정확한 좌표를 제공하는 작업을 통해 데이터의 품질이 서비스 품질에 직접적인 영향을 미친다는 점을 느꼈습니다.
- **사용자 경험**: 사용자가 위치를 입력하면 가장 가까운 대여소를 찾을 수 있는 기능을 제공함으로써 사용자 중심의 서비스 제공이 얼마나 중요한지 깨달았습니다. 더 나은 사용자 경험을 제공하기 위해 어떻게 개선할지 고민하게 되었습니다.

## 극복 방법
1. **문제**: API 요청 중 중복 호출로 인해 데이터가 과도하게 요청되고 있었다.
   - **극복 방법**: 로컬에 데이터를 저장하여 중복 요청을 방지하고, 데이터를 한 번만 요청하도록 최적화했습니다.
   
2. **문제**: 다크모드에서 글자가 보이지 않는 문제 발생.
   - **극복 방법**: 스타일링을 수정하고 다크모드에서 글자가 잘 보이도록 색상과 배경을 조정했습니다.
   
3. **문제**: 지도에서 마커 클릭 시 대여소 정보가 표시되지 않는 문제.
   - **극복 방법**: 마커 클릭 시 해당 대여소의 정보를 표시하는 기능을 추가하여 문제를 해결했습니다.
   
4. **문제**: 실시간 자전거 현황을 업데이트하는 데 어려움이 있었다.
   - **극복 방법**: 자전거 대여소의 실시간 데이터를 주기적으로 요청하고 업데이트하는 시스템을 구현하여 문제를 해결했습니다.

---

## 프로젝트 개요
이 프로젝트는 서울시 자전거 대여소 정보를 시각화하고, 사용자가 원하는 위치에서 가장 가까운 대여소를 찾을 수 있도록 돕는 웹 애플리케이션을 개발하는 것을 목표로 했습니다. **Streamlit**을 활용하여 대여소 데이터를 지도에 시각화하고, **geopy**를 활용해 거리 계산을 수행하여 사용자가 빠르게 대여소를 찾을 수 있도록 했습니다.

---

## 주요 기능
- 지도에서 대여소 위치 시각화
- 사용자가 입력한 위치로부터 가장 가까운 대여소 찾기
- 사용자 세션 관리로 위치 정보 유지
- 폐쇄된 대여소 제외 및 중복 API 요청 방지

---

## 개발 환경
- **프레임워크**: Streamlit
- **언어**: Python
- **상태 관리**: Streamlit 세션 관리
- **시각화**: pydeck, geopy
- **API**: requests
- **데이터**: pandas
