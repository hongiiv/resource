---
template: overrides/main.html
---

# 신규분석요청

## 신규 분석 요청


[![release_01][1]{: width=60%}][1]

  [1]: ../../../assets/screenshots/login_05.png  

- DASHBOARD 화면에 있는 “New Analysis” 버튼을 클릭하여, 신규 분석을 진행한다.


## 암종 및 purity 설정


[![release_01][2]{: width=60%}][2]

  [2]: ../../../assets/screenshots/login_06.png  

- NGS를 수행한 RUN 이름을 입력한다.
- Instrument 에서 “Illumina MiSeq” 또는 “Illumina MiSeqDx”를 선택한다.
- “Local Fastq Files”을 선택하여 로컬 컴퓨터의 FASTQ 파일 또는 "Server Fastq Files"를 선택[^1]하여 원격지의 FASTQ 파일을 선택한다.
- 분석할 FASTQ 파일을 선택[^2]한 후, 열기 버튼을 클릭한다. 
- ONCOaccuPanel을 선택한다.
- Source는 “FFPE”, Disease는 해당하는 암종(tumor type)을 선택[^3]한다.
- Tumor의 purity 값을 입력한다. (tumor purity를 입력하지 않는 경우 CNV 분석에 있어서 50\%를 가정하여 계산)
- “SUBMIT” 버튼을 클릭하여, 분석을 시작한다.

[^1]:
	분석 서버가 NGS 장비와 연동된 경우 사용 가능
[^2]:
	컨트롤(Ctrl) 키 또는 쉬프트(Shift) 키를 이용하여 다중 파일 선택 가능
[^3]:
	선택 가능한 암종은 [oncotree][3]의 최상위(tissue)의 35개를 포함("부록 A. Cancer type mapping") 참고

[3]:  http://oncotree.mskcc.org

!!! note "분석 가능한 암종(tumor type)"
	
	1. 선택한 암종}에 따라 해석(interpreation)의 tier 정보가 달라진다.
	2. 선택한 암종에 따라 white list가 달라진다.


!!! note "Run 이름 및 샘플 이름 지정"

	1. Run 이름을 지정하지 않는 경우 기본적으로 현재 날짜가 지정된다.
	2. Run 이름은 영문 대소문자 및 -, _ , 공백만 가능하며 그 외 특수문자는 사용하지 못한다.
	3. Sample 이름은 FASTQ 파일명으로 기본적으로 지정되며, 별도로 변경이 불가능하다.


## FASTQ 업로드

[![release_01][3]{: width=60%}][3]
	
  [3]: ../../../assets/screenshots/login_07.png  


- item FASTQ 파일의 업로드 진행 상태를 확인한다.
- item 업로드가 완료되면, 업로드 완료 메세지 창이 나타난다.

!!! warning "데이터 업로드시 주의 사항"

	업로드가 완료되기 전에 소프트웨어를 종료할 경우, 분석이 진행되지 않는다. 반드시 업로드 완료 메세지 창을 확인한다. 업로드 완료 후에는 서버에서 분석이 진행되기 때문에 소프트웨어를 종료해도 된다.
