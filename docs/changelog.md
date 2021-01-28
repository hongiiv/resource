---
template: overrides/main.html
---

# v1.5.2

* 엔젠바이오는 NGeneAnalySys 버전 1.5.2.0의 출시를 발표하게 되어 기쁘게 생각합니다. (January 15, 2021)
* 퀵 매뉴얼이 업데이트되었습니다. NGeneAnalSys를 최대한 직관적으로 만드는 것이 목표이지만, 시간을 내어 자세히 살펴보는 것이 좋습니다.
* NGeneAnalySys 클라이언트는 서버에 연결할 때 자동으로 수행되므로 업그레이드를 수동으로 설치할 필요가 없습니다. 예기치 않은 문제가 발생할 경우 설치가 더 오래 걸릴 수 있습니다. (클라우드 버전만 해당하며 로컬 설치 버전은 별도로 연락 바랍니다.)
* 궁금한 사항은 support@ngenebio 로 문의하십시오.

## 새로운 기능 :material-new-box:{: style="color: #EE0F0F" } 


### 변이 통계 기능 (Variants Statistics)

* [x] Statistics 항목에 선택한 샘플 및 다른 샘플에서 탐지된 동일 변이에 대한 통계(동일한 변이를 가진 샘플 갯수, VAF, 최종 pathogenic 정보)
* [x] VAF 분포 및 해석 분포 차트의 각 항목을 클릭하면 해당되는 변이들의 샘플, Run, 질병, 해석, 패널, VAF, 분석 완료일을 테이블로 확인

[![release_01][1]{: width=60%}][1]

  [1]: ../assets/screenshots/release_01.png   

### 근거 데이터베이스 선택 기능

* [x] 내부 구축된 internal database와 CIViC 등 공개 데이터베이스를 선택하여 근거로 활용
* 패널 설정에서 Clinical Evidence Source를 PUBLIC 또는 INTERNAL로 설정


[![release_01][2]{: width=60%}][2]

  [2]: ../assets/screenshots/release_03.png   

### 데이터 상태에 따른 분석 진행 상태 표시
* [x] 예상 분석 시간 표시: 샘플의 분석 상태 메시지에 분석 시간 안내 메시지 표시
* [x] 예상 분석 시간 초과 표시: 분석에 오래 걸리는 샘플은 이에 대한 안내 메시지를 샘플의 분석 상태 메시지로 표시

### SOLIDaccuTest
* [x] SNV, CNV 결과 화면에 공개 DB (CGI, CIViC) 기반 근거 제공
* [x] HTML 리포트 추가

[![release_01][3]{: width=70%}][3]

  [3]: ../assets/screenshots/release_02.png  

### ONCOaccuTest
* [x] SNV 결과에 White-List 포함 여부 항목 제공
* [x] SV의 Tier 및 근거 데이터를 자동으로 제공
* [x] 결과 리포트에 분석에 사용한 파이프라인 버전 정보가 추가
* [x] 먼저 분석이 완료된 샘플의 결과를 바로 확인 가능

### BRCAaccuTest
* [x] Primer 지역에서 Deletion이 발생할 경우 샘플 분석 결과 화면의 샘플 이름 바로 옆에 경고 아이콘을 표시


## 업데이트된 기능 :material-update:{: style="color: #EE0F0F" }


### ExAC browser link-out
* [x] Exome Aggregation Consortium (ExAC) browser 가 중단되고 Genome Aggregation Database (gnomAD)에 통합된 컨텐츠를 제공함에 따라 더이상 ExAC 브라우저 링크를 사용할 수 없게 되어 gnomAD 링크로 제공

### Contact information

* [x] Office 전화 번호 수정

## 버그 수정 :material-adjust:{: style="color: #EE0F0F" } 

* [x] Tier를 변경했을 때 변경된 결과가 표시되지 않고 기존에 확인한 변이의 Tier 결과가 표시되는 버그 수정
* [x] Manager 화면에서 데이터 수정 시 결과 테이블의 페이지가 첫 페이지로 강제 이동하는 문제 수정

