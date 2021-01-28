---
template: overrides/main.html
---
# 분석 결과

## 분석 결과 목록

[![release_01][1]{: width=60%}][1]

  [1]: ../../../assets/screenshots/f_04_01.png  

- 해당 검체를 클릭하여, SAMPLES 탭으로 이동한다.
- Variant 컬럼을 통해 해당 검체의 변이 분석 결과를 확인할 수 있다.
- SNV/INDEL, CNV, SV, MSI, TMB, QC에 대한 결과값을 각각 보여주며,
- Tir 1,2의 임상적 의미가 있는 변이의 개수를 함께 표시한다.

!!! note "Tier 정보 내용"
	SW에서 자동으로 tiering 가능한 변이는 SNV/INDEL 및 CNV에 대해서만 가능하며, Fusion에 대해서는 추후 제공 예정임.

!!! note "분석 결과 검색"
	분석 결과 검색 기능(화면 우측의 SEARCH)을 이용하여, 사용자가 입력한 RUN 이름, 검체명, 패널명, 분석 날짜에 맞는 RUN과 SAMPLE을 검색할 수 있다.



## SNV/INDEL 분석 결과

### 변이 목록 화면


[![release_01][2]{: width=60%}][2]

  [2]: ../../../assets/screenshots/f_04_02_01.png  

- SAMPLES 탭의 변이 목록 화면에서 각 변이의 tier 정보를 확인한다. (해당 아이콘을 클릭하면 evidence 정보 확인 가능)
- 변이에 대한 상세 정보를 확인하기 위해, 변이를 더블 클릭하여 변이 상세 정보 화면으로 이동한다.

!!! note "변이 필터 기능"
	변이 필터 기능(화면 좌측)을 사용하여 원하는 변이만을 선택할 수 있다(예, HRD(homologous recombination deficiency 또는 MMR(mismatch repair) 관련 유전자).


### 변이 상세 정보 확인


[![release_01][3]{: width=60%}][3]

  [3]: ../../../assets/screenshots/f_04_02_02.png  

- Variant Detail 창을 통해 Allele Fraction, HGVS Nomenclature 정보 등을 확인한다.
- “IGV” 버튼\footnote{화면 좌측의 IGV를 버튼을 통해서도 IGV를 실행 가능}을 클릭하여, IGV 프로그램을 실행한다.
- IGV 프로그램에서 해당 변이에 대한 alignment 정보를 확인한다. (\hyperref[sec:IGV]{“IGV 프로그램 결과 확인”} 부분 참고)


### 외부 링크를 통한 데이터베이스 정보 확인


[![release_01][4]{: width=60%}][4]

  [4]: ../../../assets/screenshots/f_04_02_03.png  

- “EXTERNAL LINKS”에 있는 웹 사이트를 클릭하여 해당 웹 사이트에서 변이 정보를 확인한다.
- “EXTERNAL LINKS”에서 “COSMIC”를 클릭하여, COSMIC database에서 해당 변이에 대한 정보를 확인할 수 있다.

### Evidence 정보 확인


[![release_01][5]{: width=60%}][5]

  [5]: ../../../assets/screenshots/f_04_02_04.png  

- “Clinical Significant” 버튼을 클릭하여, 해당 변이에 대한 evidence 확인 화면으로 이동한다.
- 해당 변이에 대해 AMP 가이드라인\cite{Li:2017ee}에 따라 소프트웨어에서 지정한 evidence 확인한다.
- 해당 변이에 대해 clinical database에서의 evidence를 확인한다. (SNV/INDEL에 대해서만 제공)

!!! note "근거 레벨 정보"

	유전변이가 종양 상태에 어떤 영향을 주는지에 대한 임상적 영향에 대해 진단(diagnosis), 예후(prognosis), 치료(therapeutic) 여부를 평가한 후 임상적 또는 실험적 증거의 강도를 평가한다.
	=== "Level A (validated association)"
		
		 특정 유형의 종양에 대해 FDA 승인 약물의 반응이나 저항성을 예측 할 수 있는 바이오마커 또는 전문가 가이드라인에 포함된 바이오마커

	=== "Level B (clinical evidence)"
		
		 잘 설계된 연구를 통해 뒷받침되고 그 분야의 전문가들의 의견이 모아진 바이오미커 

	=== "Level C (case study)"

		 서로 다른 유형의 종양에서 FDA 승인된 약물의 반응이나 저항성을 예측할 수 있는 바이오미커, 임상시험의 포함 조건을 만족하는 바이오마커 

	=== "Level D (preclinical evidence)"

		 전임상연구에서 타당한 치료적 중요성을 보여준 바이오마커 

!!! note "근거 tier 정보"
	=== "Tier I"

		  Variants of strong clinical significance (Level A, Level B)

	=== "Tier II" 

		 Variants of potential clinical significance (Level C, Level D)

	=== "Tier III"

		 Variants of unknown clinical significance

	=== "Tier IV" 

		 Benign or likely benign variants

### TMB (Tumor Mutation Burden)
- 화면 상단에 현재 SNV/INDEL의 개수에 따라 자동으로 계산된 TMB 결과값을 확인할 수 있다.
- SNV/INDEL 변이를 false로 지정하는 경우 실시간으로 반영된 TMB 결과값을 제공한다.


!!! note "TMB 계산 방법"
	TMB high = 모든 유전자의 somatic nonsynonymous mutation 개수 / coding region size (0.64 Mb) > 23 Muts/Mb 
		
	ONCOaccuPanel의 경우 somatic nonsynonymous mutation의 개수가 15개 이상인 경우 TMB high에 해당하며, somatic nonsynonymous mutation외에 HRD, MMR 유전자의 germline nonsynonymous mutation도 포함한다.


!!! note "암종에 따른 TMB"
	NGeneAnalySys에서는 모든 암종에 대해서 기준값 (>23 Muts/Mb)을 제공하지만, TMB의 high/low는 암 종마다 기준값이 달라질 수 있으며, 데이터 축적을 통해 암종별 TMB 기준값을 달리 적용하는 것을 권장한다.


[![release_01][6]{: width=60%}][6]

  [6]: ../../../assets/screenshots/f_04_02_10.png  

위 그림은 분석 결과 중 HTML에서 제공하는 것으로, 현재 샘플에서 추정된 TMB(빨간선)와 함께 TCG의 암 샘플에서 관찰된 암 종별 TMB의 분포를 나타낸다. 회색 영역은 NGeneAnalySys에서 정의한(>23 Muts/Mb) TMB high를 나타낸다. 아래에 제시된 TCGA 데이터셋의 특성을 참고하여 TMB 해석을 수행한다.
- TCGA의 종양 샘플은 약 100X의 평균 커버리지로 시퀀싱 
- TCGA의 somatic mutation은 variant caller간의 일치(각 변이가 최소 2개의 알고리즘에 의해 calling)에 기초
- TCCGA의 somatic mutation은 tumor-control 시퀀싱 기반(tumor-only 시퀀싱은 noise로 인해 더 높은 비율)

### MSI (Microsatellite Instability)

- 화면 상단에 현재 SNV/INDEL의 개수에 따라 자동으로 계산된 MSI 결과값을 확인할 수 있다.
- SNV/INDEL 변이를 false로 지정하는 경우 실시간으로 반영된 MSI 결과값을 제공한다.


!!! note "PCR을 이용한 MSI 검사 방법"
	PCR target analysis를 이용한 검사는 USA NCI(National Cancer Institute)를 시작으로 범용적으로 사용되는 Bethesa loci와 통계 데이터베이스를 통해 선정된 Qusi loci가 존재한다.

	=== "Bethsa markers"
	
		 D2S123, D17S250, D5S346, BAT-25, BAT-26
	
	=== "Quasi markers"
	
		 NR-27, NR-21, NR-24, BAT-25, BAT-26


!!! note "NGS를 이용한 MSI 검사 방법"
	NGS를 이용한 검사에는 다양한 마커를 사용하며 각 패널에 따라 다음과 같은 마커를 사용한다.

	=== "TruSight Oncology 500"

		 Internal tumor-only algorithm examining 130 repeat loci

	=== "FoundationOne CDx"

		 95 intronic homopolymer repeat loci(10-20bp)

	=== "Sophia STS+"

		 BAT-25, BAT-26, CAT-25, NR-21, NR-22, NR27

	=== "HMF OncoAct"

		 MSISeq tool



!!! note "ONCOaccuPanel MSI 검사 방법"
	Mutational burden(>30 Mutations)과 I-INDEX(모든 변이에서의 INDEL의 비율, >20\%)를 기반으로 microsatellite status(MSS/MSI)를 판정한다. 또한 다음의 내용을 추가적으로 고려하여 판단한다.

	- MSI marker인 ACVR2A 유전자의 K43Rfs*5 변이 유무
	- pathogenic MMR 유전자 mutation
	- pathogenic POLE gene actionable alteration(exonuclease domain mutations, such as P286R, V411L, F367C, S297Y)
	- POLE gene actionable alteration이 존재하는 경우 POLE mutation에 의한 hyper mutation phenotype으로 판단할 수 있음(SNV mutation이 많고 I-INDEX가 낮아짐)
	-  Low tumor purity로 인해 SNV, INDEL이 적게 발견되는 경우


POLE actionable alteration에 의한 hypermutation은 C에서A로 변하는 mutation(> 20%), C에서G로 변하는 mutation(< 3%)라는 특징이 있으며, HTML에서 제공하는 Mutational Signature에 S10 signature로 나타난다. 아래 그림은 POLE hypermutation 샘플에서의 Mutational Signature를 보여준다.


[![release_01][7]{: width=60%}][7]

  [7]: ../../../assets/screenshots/f_00_00.png  


[![release_01][8]{: width=60%}][8]

  [8]: ../../../assets/screenshots/f_00_02.png  

!!! note "Mutational Signature"

	=== "S1"
	
	    ACG, CCG, GCG, TCG의 CG(CpG) 영역에서 deamination이 되어 C>T로 즉, ATG, CTG, GTG, TGG 많이 발생한다는 것은 자연적인 현상이기 때문에 대부분의 암 종의 환자에서 나타나며 암의 진단 나이와 관련이 있다.
	
	=== "S3"
	    DNA repair pathway중 상동재조합(HR, homologus recombination)에 의해 double-strand break-repair가 결핍, failure-->HRD으로 인한 기전에 의해 나타나는 패턴이 바로 signature 3이다. S6, S20, S26: DNA mismatch repair와 관련

MMR 유전자 돌연변이 샘플에서의 Mutational Signature

[![release_01][9]{: width=60%}][9]

  [9]: ../../../assets/screenshots/f_00_04.png  

[![release_01][10]{: width=60%}][10]

  [10]: ../../../assets/screenshots/f_00_03.png  


### 리포트에 SNV/INDEL 추가/제외하기


[![release_01][11]{: width=60%}][11]

  [11]: ../../../assets/screenshots/f_04_02_06.png  

- 단일 변이 추가: Report 컬럼의 “리포트 아이콘” 버튼을 클릭하여 해당 변이를 리포트에 추가 한다.
- 복수 변이 추가: 리포트에 추가하고자 하는 변이를 모두 선택한 후 화면 좌측의 “Report” 버튼을 클릭하여 복수의 변이를 리포트에 추가한다.
- 리포트 변이 제외: 변이 추가 방법과 동일한 방법으로 리포트에서 제외한다.

!!! note "리포트 기본 포함 변이"
	소프트웨어에서는 기본적으로 Tier1, Tier2, Tier3 변이는 리포트에 포함되도록 설정되어 있다.

## CNV/SV 분석 결과

### CNV 분석 결과

[![release_01][12]{: width=60%}][12]

  [12]: ../../../assets/screenshots/f_04_03_01.png  

- VARIANTS 탭의 “CNV” 버튼을 클릭하여, CNV 분석 결과 화면으로 이동한다.
- CNV 컬럼에서 Copy Gain/Loss를 확인한다.


!!! note "Chromosome 1p/19q Co-Deletion or loss of heterozygosity (LOH) in Gliomas"
	- In gliomas, depending on the tumor histopathology and the patient’s clinical features, this integrated diagnosis may require assessing the tumor for IDH1 and IDH2 (IDH), H3F3A, and BRAF mutations, as well as the 1p/19q codeletion.
	- The 1p/19q co-deletion associated with oligodendroglial tumor is characterized by simultaneous whole-arm deletion of chromosome 1 and chromosome 19; therefore, arm-level evaluation is required.


### SV 결과 확인


[![release_01][13]{: width=60%}][13]

  [13]: ../../../assets/screenshots/f_04_03_02.png  

!!! note "Fusion 유전자에 대한 근거 정보 지정"
	- 현재 SV에 대해서는 tier 정보를 자동으로 지정해 주지 않기 때문에 사용자가 직접 아래 데이터베이스를 참고하여 fusion에 대한 tier를 설정하시기 바랍니다.
	- Fusion 유전자에 대한 근거는 "부록 D. Fusion Database"를 참고 하시기 바랍니다.
