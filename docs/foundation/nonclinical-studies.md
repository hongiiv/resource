---
template: overrides/main.html
---

# Nonclinical Studies

성능 특성은 광범위한 FFPE 조직 유형에서 파생된 DNA를 사용하여 확립되었다. CDx 표시와 관련된 조직 유형이 각 연구에 포함되었다. 각 연구는 CDx 변형뿐만 아니라 다양한 유전자에 걸친 다양한 유전적 맥락에서 광범위한 대표적인 변형 유형(대체, 삽입-삭제, 복사 번호 변경, 재배열)을 포함했다. MSI와 TMB를 포함한 게놈 시그니처 분석도 실시되었다.


## 분석 정확도/일치도


### 기존 검사법 비교

* F1CDx에 의한 alteration 검출을 외부 검증 NGS 검사 (evNGS) 결과와 비교
* 46개의 종양 조직에서 추출한 188개의 샘플 포함한 기존 검사법으로 검출된 Short alteration (base substitutions, short indels) 비교 
* 표 6에 PPA와 NPA에 대한 요약 내용
* 전체적으로 F1CDx 검사와 기존 검사 사이에 157개의 중복 유전자가 있음.
* 플랫폼간의 차이는 VUS 변이 차이로 F1CDx와 비교 NGS간에 채택된 필터링의 차이로 예상되며,
* VUS 필터와 관련 없는 불일치는 주로 homopolymer region의 low alleic fraction을 가진 deletion
* F1CDx의 variant calling 파이프라인은 homopolymer region의 indel에 대해서 MAF of ≥ 0.10%의 필터를 통해 artifacts에서 비롯되는 false positive를 줄인다.
* 따라서, 관찰된 차이는 두 플랫폼 간의 필터 thresholds가 다르기 때문이다. 

### 기존 NTRK1/2/3 융합 검사 비교

* Analytical accuracy를 평가하기 위해 F1CDx와 외부 검증 NGS 검사 (evNGS) 의 NTRK1/2/3 rearragement 비교
* VITRAKVI (laroterctinib)을 위한 LOXO-TRK - 14001 (NCT02122913), -15002 (NAVIGATE, NCT02576431), and -15003 (SCOUT, NCT02637687)의 FFPE 잔여 38 검체 사용
* 38 검체의 구성은 clinical studies LOXO-TRK - 14001, - 15002, and -15003 included the following cancer types으로 구성
* 암종은 bone sarcoma (1), breast (1), cholangiocarcinoma (2), colorectal cancer (7), infantile fibrosarcoma (2), lung (4), melanoma (1), oral cancer (1), primary CNS (1), salivary gland (3), soft tissue sarcoma (10), neuroendocrine (2), thyroid (2), and urinary (1) cancer.
* 제한된 임상시험 샘플로 인해 이전 FMI에서 평가되었된 FMI 임상 기록 보관소 (FMI clinical archives)의 NTRK1/2/3 재배열 양성 (N=94) 샘플 포함
* 해당 94 샘플은 breast (14), cholagiocarcinoma (1), colorectal cancer (15), gastrointestinal stromal tumor GIST (2), head and neck (14), lung (10), neuroendocrine (1), reproductive (11), salivary gland (9), thyroid (6), and urinary (6) cancer 와 암종을 알 수 없은 5검체 포함
* 이전 일치성 검증 연구에서 exNGS의 NTRK1/2/3 재배열 음성 샘플 포함
* 이전 일치 연구는 NTRK1/2/3 재배열 유무에 대해 새로 평가되어 이전의 일치성 분석에서 검사한 474개의 검체가 포함
* 의도된 사용 모집단과 더 일치하도록 NTRK1/2/3 재배열 음성 샘플 세트의 일부로 10개 소아용 샘플 (bone sarcoma (1), GIST (1), head and neck (1), pancreas (1), soft tissue sarcoma (1), and urinary cancer (1) 와 1개의 알수 없는 암 유형 포함)
* 본 분석 정확도 연구에서 고형암 환자의 임상 FFPE 검체 (543 NTRK 음성, 83개 양성 검체) 총 626개플 평가
* F1CDx 또는 evNGS에서 잘못된 결과가 없습니다. 일치성을 평가하기 위해 두 가지 분석이 수행되었다.

[![NTRK_Samples][1]{: width=60%}][1]

  [1]: ../assets/screenshots/NTRK_Samples.png


* 1차 분석
	
	* 일차 분석은 F1CDx 및 evNGS 검사에 의한 NTRK1/2/3 재배열 검출의 일치성에 초점
	* 샘플의 출처에 따라 2개의 서브셋으로 분류 (588 samples from the FMI clinical archives) 하여 PPA, NPA 계산을 위해 별도 평가
	* 사용 모집단에서 NTRK1/2/3의 유병률(0.32%)에 따라 조정
	* 전체 데이터세트 (n=626) 두 부분 집합을 결합하여 10,000회 부스트래핑하여 weighted PPA 90.00 (75.00%, 100.00%), weighted NPA 99.94% (99.92%, 99.97%)


	[![NTRK_Samples][2]{: width=60%}][2]

    [2]: ../assets/screenshots/NTRK_PPA.png

	!!! warning "Bootstrapping"

		  Bootstrapping?


	* 일차 분석에 기반한 불일치 검체는 모두 20개로 18개에서 F1CDx 검사에서 양성인 반면 evNGS 검사에서는 재배열이 감지 되지 않았으며, 나머지 2개 검체에서 evNGS 검사에서는 검출되었지만, F1CDx 검사에서는 검출되지 않음
		* 9 샘플 had breakpoints residing outside of evNGS baited regions
		* 5 샘플 had the event observed but were not reported due to being below the evNGS assay limit of detection
		* 1 샘플 had an intragenic NTRK3-NTRK3 rearrangement that was intentionally not reported by evNGS duto to being intragenic
		* 2 샘플 were not reported by evNGS likely due to low sample quality as reported by the evNGS assay
		* 1 샘플 (NTRK3-KDM2A) was not detected by evNGS

* 2차 분석

	* 2차 분석은 NTRK1/2/3 rearrangement의 CDx 바이오마커에 대한 규칙에 따라 NTRK1/2/3 재결합 럼출의 일치성에 초점
	* 2차 분석에서는 샘플이 NTRK1/2/3 바이오마커 규칙을 만족하는 경우에만 F1CDx 양성으로 간주

	[![NTRK_PPA_2][3]{: width=60%}][3]

    [3]: ../assets/screenshots/NTRK_PPA_2.png


	* 2차 분석에서의 불일치는 17개 샘플로 13개는 F1CDx 바이오마커 음성이지만, evNGS 바이오마커 양성
	* 13개의 샘플 중 10개는 non-fusion rearragnement로 F1CDx 바이오마커 규칙에 따라 F1CDx에서 음성으로 간주
	* 그러나 이 10개는 evNGS 검사가 fusion과 rearragement를 구분할 수 없기 때문에 evNGS 바이오마커 양성으로 간주되어 따라서 이 10개 샘플은 1차 분석에서는 불일치 하는 것으로 간주되지 않음
	* evNGS 검사에서 양성이었지만, F1CDx에서 음성으로 나온 3개의 임상시험 샘플은 VITRAKVI에 반응하지 않은 임상시험에 등록된 환자에서 추출(두명의 환자는 안정된 질병을 가지고 있었고 1명은 진행성 질병을 가지고 있음)

	!!! warning "Fusion & rearagement"

		  Fusion & Rearragement?

### FoundationOne LDT와의 비교

* F1 LDT를 사용하여 생성된 후향 데이터를 F1 CDx에 대한 보충 및 지원 데이터로 사용할 수 있도록 F1 CDx 검사에 대한 일치성 연구 수행
* 두 검사를 모두 수행한 165 검체를 가지고 진행
* Tumor content가 20%-90%의 조직에서 추출한 35개의 서로 다른 tumor types에서 추출한 DNA를 포함
* Short variants, Substitutions, Indels, CNAs, Amplification, Losses, Rearragements에 대해 비교
* MSI와 TMB에 대해서도 비교

[![ppa_f1cdx][4]{: width=80%}][4]

  [4]: ../assets/screenshots/ppa_f1cdx.png

!!! warning "양성일치율"
	 * 양성 일치율 (Positive percent agreement, PPA): 양성 결과를 보이는 검사법이 대조 검사법과 양성 검사 결과가 일치하는 비율
		 * PPA of All short variants = 100xa/(a+c) = 100*1282/(1282+73) = 94.6%
		 * PPA of Substitutions = 96.6%
		 * PPA of Indels = 83.4%
	 * 음성 일치율 (Negative percent agreement, NPA): 음성 결과를 보이는 검사법이 대조 검사법과 음성 결과가 일치하는 비율

	
	[![ppa][5]{: width=55%}][5]

    [5]: ../assets/screenshots/ppa.png


## 분석 민감도

### 최소검출한계 (LoD)

* EGFR exon 21 L858R, EGFR Exon 20 T790M, EGFR exon 19 deletion, KRAS codons 12/13 substitution and BRAF V600E 의 5개 CDx 바이오마커에 대해 테스트
* BRCA1/2의 alteration in non-repetitive regions or homopolymer repeats < 4 bp alteration in a homopolymer region > 4bp (P160018 참고)
* 각 variant 카테고리당 하나의 FFPE tumor 샘플 선택
* 각 샘플당 6개의 레벨의 MAF에 대해 13회 반복 실험 (샘플당 78회) 
* CLSI EP17-A2에서 제안된 반복실험 횟수를 충족하기 위해 단일 FFPE 샘플과 뱅킹된 DNA 샘플에서 여러개의 서로 다른 DNA 풀링
* Indels은 그룹화 (homopolymer repeat context)
* Indels의 범위는 1bp - 42bp insertion, deletion은 최대 276bp
* homopolymer 반복 지역의 indels은 반복 길이에 따라 더 높은 LoD

### 최소검출한계 (LoD)

* 다양한 암종의 7개의 샘플을 통해 F1CDx LoD 수행

[![ppa][6]{: width=55%}][6]

  [6]: ../assets/screenshots/ntrk_lod.png

* 각 샘플의 LoD를 평가하기 위해 5개의 타겟 computational tumor purity levels (2.5%, 5%, 10%, 15%, 20%)
* Computational tumor purity는 genome-wide copy number, tumor ploidy, purity를 예측하는 통계 모델에 관찰된 log-ratio, minor allele frequency 데이터를 fitting하여 계산
* The log-ratio profile is obtained by normalizing aligned tumor sequence reads by dividing read depth by that of a process-matched normal control, followed by a GC-content bias correction using Loess regression. 
* The minor allele frequency profile is obtained from the heterozygous genome-wide SNPs.
* Twenty (20) replicates were assessed for each dilution level, except 20%, which examined fourteen (14) replicates. Ninety-four (94) replicates were tested per sample. Each specimen was evaluated close to the minimum input requirements of the assay (50 ng), representing the most challenging evaluation of rearrangement detection.
* LoDs were determined based on tumor purity and reads using the empirical hit rate method for NTRK1, NTRK2, and NTRK3

	* Empirical hit rate approach was used when there were less than three hit rate levels. The LoD is defined as the lowest level (tumor purity or reads) with at least 95% detection.
* A summary of the LoD results based on reads and tumor purity using the empirical hit rate method for NTRK gene alteration in each sample evaluated are shown in Table 22.

[![ntrk_lod_result][7]{: width=55%}][7]

  [7]: ../assets/screenshots/ntrk_lod_result.png

* The final LoD for each NTRK gene fusion presented was determined as the highest LoD observed per gene. The LoD for each gene are:
	* NTRK1 fusion: 12.10% tumor purity and 24.55 for chimeric reads
	* NTRK2 fusion: 11.50% tumor purity and 24.16 for chimeric reads
	* NTRK3 fusion: 6.10 % tumor purity and 14.65 for chimeric reads
* Given the limited number of samples with NTRK1 and NTRK2 fusions evaluated to determine the assay LoD, a post-market study is planned with additional NTRK1 and NTRK2 fusions samples
	
### Limit of Blank (LoB)


### Analytical Sensitivity – Tumor Purity

* F1CDx의 견고성(robustness)을 지원하는데 필요한 최소 종양 분율(tumor fraction) 평가
* 6개의 레벨의 tumor content에 레벨당 13회 반복 총 78 per sample
* ALK fusion과 ERBB2 amplification의 CDx 바이오마커의 분석 민감도 결정

!!! warning "CLSI EP17-A2"

	 CLSI EP17-A2 : Clinical Laboratory Standards Institute의 검출단계별 강도 측정 가이드

!!! warning "공시료"

	 공시료 (blank sample)란 측정하고자 하는 물질이 실험시료에 포함되지 않은것을 의미

## 분석 특이도


* 간섭 물질 (Interfering Substances)
* In silico Analysis – Hybrid Capture Bait Specificity

## Carryover/Cross-Contamination

## Precision and Reproducibility
* **Intermediate Precision**

	* NTRK1/2/3 융합 검출을 위한 F1CDx의 성능 특서을 위해 고형암 환자 7 샘플에 정밀도는 50ng에 가까운 DNA input을 가지고 평가
	* 평가 샘플들은 17.2% ~40.1%에 이르는 계산된 종양 purity (computational tumor purity) 
	* 통과된 샘플의 컷오프는 20% 정도로 정밀 연구에 평가된 샘플에는 F1CDx 검사에 대한 20% 근처의 tumor purity 샘플이 포함
	* 샘플의 chimeric read의 평균 8.48~159.04
	* Fold LoD 기반 chimeric read는 0.58 xLoD ~ 10.86 xLoD

[![precision][8]{: width=55%}][8]

  [8]: ../assets/screenshots/precision.png

* **Site-to-Site reproducibility**

	* 모리스빌 포함하기 위한 재현성 연구는 NTRK 지원하기 위해 수행되지 않음
	* Site-to-site 재현성의 연구 결과가 post-market study로 제공될 예정

!!! warning "Computational tumor purity"

	Computational tumor purity

## NTRK 변이 QC metric

* NTRK1/2/3 rearragement를 위한 coverage analysis 기반 real-world data
* F1CDx 승인 후 76,597 샘플을 사용
* Median exon coverage는 900x 근처로 QC 기준인 250x 이상임

[![exon_coverage][9]{: width=55%}][9]

  [9]: ../assets/screenshots/exon_coverage.png

* Post-DNA extraction QC metrix (LC DNA yield, HC DNA yield, median exon coverage, % target 100x coverage)


[![qc_metrix][10]{: width=55%}][10]

  [10]: ../assets/screenshots/qc_metrix.png

## NTRK Bait set 커버리지의 In-silico 평가

* DX1 baitset은 NTRK1/2/3의 coding 영역, NTRK1 (introns 8,9,10,11), NTRK2 (intron 12)를 커버
* NTRK1 intron 8과 NTRK2 intron 12는 not fully baited
* NTRK3 intron은 비록 포함되지 않지만, NTRK3의 흔한 ETV6는 ETV6-NTRK3 fusion (ETV6 introns 5,6)을 위해 baited
* ETV6의 intron 5는 not fully baited
* ETV6 intron 4는 not having baits
* In-silico 분석을 위해 12,464 임상 검체로 NTRK의 커버리지 계산
* 타겟 영역에 평가결과 median exon coverage는 >250x in >99%
* NTRK1 intron 8에서 부분적으로 coverage 감소를 보였지만 이는 partially baited로 인한 것임

!!! warning "DNA 검사"

	여기서 확실히 bait에 intron을 포함하는 것으로 봐서 DNA 검사임이 확실함 


## Reagent Lot 교환성

## Stability

* Reagent Stability
* DNA Stabilit
* FFPE Slide Stability

## 일반 실험실 장비 및 시약 평가


## Guard banding/Robustness


## Tissue Comparability


## NTRK 변이 탐지를 위한 In-silico 평가

A study analyzing F1CDx assay data was conducted to provide coverage analysis based on real-world data to support the pan-tumor indication for NTRK1/2/3 rearrangements. Since F1CDx’s approval, 76,597 samples have been processed by the DX1 baitset used by F1CDx for the most prevalent NTRK tumor specimen sites listed in Figure 1. An in-silico analysis was performed to present median exon coverage across these tumor specimen sites. Figure 1 and Table 26 show median exon coverage for all tumor specimen sites to be around 900x, which is above the quality control (QC) threshold of 250x.

Table 26 summarizes critical post-DNA extraction QC metrics, namely, the mean of LC DNA yield, HC DNA yield, median exon coverage, % target 100X coverage, and the pass rate for the 15 different biopsy specimen sites.

