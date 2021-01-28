---
template: overrides/main.html
---
# 리포트

## 임상 리포트 출력


[![release_01][1]{: width=60%}][1]

  [1]: ../../../assets/screenshots/f_05.png  

- “REPORT” 탭을 클릭하여, REPORT 화면으로 이동한다. 
- 최종적으로 리포트에 출력 될 변이 정보를 확인한다.
- 변이에 대한 정보를 토대로 사용자의 소견을 작성한다.
- 검체에 대한 추가 정보를 입력한다.
- “Final Report” 버튼을 클릭하여 해당 검체에 대한 리포트를 출력한다.

## QC 리포트

### 런 단위에서의 QC 리포트

[![release_01][2]{: width=60%}][2]

  [2]: ../../../assets/screenshots/f_07_01.png  

- “RESULTS” 탭을 클릭하여, RESULTS 화면으로 이동한다. 
- 각 런의 오른쪽에 위치한 다운로드 버튼을 클릭한다.
- QC REPORT(PDF 포맷) 또는 QC SUMMARY(Excel 포맷)를 다운로드 한다.
- QC SUMMARY는 하나의 파일에 런에 속한 모든 샘플에 대한 QC 데이터를 확인할 수 있으며,
- QC REPORT는 각 샘플별로 PDF 포맷으로 확인할 수 있다.

### 샘플 단위에서의 QC 리포트


[![release_01][3]{: width=60%}][3]

  [3]: ../../../assets/screenshots/f_07_02.png  

- QC 리포트를 보고자 하는 샘플을 선택한다.
- 화면 오른쪽 상단의 다운로드 버튼을 클릭한다.
- QC_REPORT를 선택하면 PDF 포맷의 QC 보고서를 다은로드 할 수 있다.

## HTML 리포트
변이 및 근거 정보에 대해서 HTML 형식의 리포트를 제공한다.

<div class="tx-columns" markdown="1">
- [x] Sample info: 샘플의 정보를 제공
- [x] Panel info: 패널의 정보를 제공
- [x] Summary results: Actionable(tier1,2)의 변이 정보 및 MSI, TMB 요약 정보 제공
- [x] Data QC: QC 정보를 제공(Raw Read Quality, Gene Coverage, Gene Coverage Table)
- [x] Somatic SNVs/INDEs: 모든 유전변이 목록 제공(Variants statistics, VAF distribution, Caller agreement, Total variant table, Tier1/2)
- [x] CNV results: CNV 결과 제공(CNV Table, Tier1/2)
- [x] Structure Variants: SV 결과 제공
- [x] Microsatellite stability
- [x] Tumor Mutational Burden
- [x] Tumor Purity
- [x] Mutational Signatures
- [x] List of genes assayed
- [x] Resources
</div>


[![release_01][4]{: width=60%}][4]

  [4]: ../../../assets/screenshots/f_10_01.png  
