---
template: overrides/main.html
---

# Device Description

* Site의 위치는 캠브리지와 모리스빌
* Assay 구성은 reagents, software, instruments, FFPE 종양 샘플에서 추출한 DNA 테스트 절차를 포함
* 유전자는 substitutions, indels, CNSs를 검출하기 위한 전체 코딩 영역 영역을 포함하는 유전자, rearragnement 검출을 위한 intronic 영역을 포함하는 유전자, 프로모터와 ncRNA 유전자로 구성
* 엑손의 99% 이상이 100X 이상으로 시퀀싱
* 시퀀스 데이터는 각 변이들을 감지하도록 설계된 파이프라인을 사용하여 처리
* MSI, TMB, HRD (tBRCA-positive and/or LOH high)를 포함한 genomic signature 보고
* 결과물
	
	* Category 1: CDx와 관련된 결과
	* Category 2: 임상적인 근거 (evidence) 가 있는 암 돌연변이
	* Category 3: 임상적으로 근거의 가능성 (potential) 이 있는 암 돌연변이

* 테스트 키트 구성

	* 테스트는 샘플 배송 키트가 포함되어 있으며, 키트는 실험실로 보내지게 된다.
	* 배송키트는 검체준비 지침, 배송 지침, 반송 발송 라벨이 포함된다.
* 사용되는 장비

	* F1CDx 검사는 시리얼 번호로 관리되는 기기들로 모든 기기들은 FMI의 품질 시스템템에 따라 FMI의 인증을 받음

## 검사 절차

F1 CDX 검사 프로세스에 포함된 모든 검사 시약은 FMI의 인증을 받았으며 의료 기기 품질 시스템 규정(QSR)을 준수합니다.

* **검체 수집 및 전처리** (Speciment collection and preparation)
* **DNA 추출** (DNA extraction)
* **라이브러리 구축** (Library construction)
* **캡처** (Hybrid Capture)
* **시퀀싱** (Sequencing)
* **시퀀스 분석** (Sequence analysis)
* **리포트 생성** (Report generation)
* **Positive 컨트롤과 관련된 내부 프로세스** (Internal process controls related to the system positive control)
* **변이 분류** (Variant classification)

## 시퀀스 분석 (Sequence analysis)

시퀀스 분석은 매핑과 duplication 제거, 로컬 재정렬의 기초 분석 과정 후 각각의 변이 종류별(base substitution, indels, CNAs, genomic rearragements, MSI, TMB, QC) 분석법에 대해서 설명한다.

### 기초 분석

* 시퀀스 데이터는 FMI가 개발한 독점(proprietary) 소프트웨어를 사용하여 분석
* ``BWA v0.5.9`` 를 사용하여 ``hg19`` 에 매핑
* PCR duplicate read removal and metric collection을 위한 ``Picard 1.47`` 및 ``SAMTools 0.12a``
* 로컬 정렬 최적화를 위해 ``GATK 1.0.4705.6``
* 타겟 영역에 대해서 변이 호출 (variant calling)

### Base substituion 분석


* Base substitution을 탐지는 tissue-specific한 prior expectations을 통해, 
* 낮은 muant allele frequency (MAF)에서 novel한 somatic alterations과 hotspot 지역에서의 sensitivity를 높이는 베이지안을 사용 (Forbes SA, 2011)
* 낮은 mapping (mapping quality < 25) 또는 calling quality (base calls with quality ≤ 2)는 배제함
* 최종 call은 MAF ≥ 5% 이며, hotspot은 MAF ≥ 1%로 함 

### Indels 분석


* Indel 검출을 위해 de novo local assembly를 각 타겟 엑손에 대해서 de-Bruijin 기법을 사용
* 타겟 영역에 한개라도 매핑된 리드의 read-pair를 수집
* 각 read를 k-mers로 분해하고 de-Bruijn 그래프로 구성
* Evaluating the support of each alternate haplotype with respect to the raw read data to generate mutational candidates. 
* All reads are compared to each of the candidate haplotypes via ungapped alignment, and a read ‘vote’ for each read is assigned to the candidate with best match. 
* Ties between candidates are resolved by splitting the read vote, weighted by the number of reads already supporting each haplotype. 
* This process is iterated until a ‘winning’ haplotype is selected.
* Aligning candidates against the reference genome to report alteration calls.

### Indel 필터링


* 후보 indel 필터링은 base substitutions와 유사하다. 
* GATK에 구현된 반복 및 인접 시퀀스의 품질 매트릭에서 경험적으로 증가한 frequency threshold

	* 주변 base의 mismatches < 25%
	* 주변 base의 평균 base quality > 25
	* 평균 supporting read mismatch ≤ 2
	* 최종 call은  MAF ≥ 5% (MAF ≥ 3% at hotspots)

### CNAs 분석


* CNAs를 탐지하는 방법은 CGH를 이용하는 방법과 유사한 방법을 사용
* 정상 대조군의 모든 엑손 및 게놈 전체의 약 3,500개의 SNP의 시퀀스 커버리지를 정규화하여 log-ratio profile을 획득
* 해당 profile은 SNP의 frequency를 사용하여 segment에서 tumor purity와 copy number를 각 세그먼트에서 추정
* Amplification은 tumor purity가 ≥ 20%인 샘플에서 segment가 ≥ 6 copies (또는 ≥ 7 for triploid, ≥ 8 for tetraploid tumors) 이며 homozygous deletion은 0 copies
* ERBB2 amplification은 diploid tumor에서 세그먼트가 ≥ 5 copies 인 경우 양성

### Genomic rearrangements 분석


* Rearrangements는 chimeric read pairs를 분석하여 식별
* Chimeric read pairs는 다른 염색체에 read가 매핑되거나 10 Mb 이상 떨어진 경우
* 게놈 좌표를 통해 클러스터를 생성 클러스터는 최소한 5개의 chimeric pairs를 (알려진 fusion은 3개) 가진 경우 후보로 식별
* 후보 필터링은 매핑 품질 (클러스터의 평균 read mapping quality가 30 또는 그 이상)과 정렬 위치의 분포를 통해 진행
* Rearragne에는 예측되는 기능 (predicted function ex, creation of fusion gene)에 대한 주석

### MSI 분석


* 95개의 intronic homopolymer repeat loci (10-20 bp long in the human reference genome)의 길이 분석과 PCA를 통해 MSI score
* 95 loci를 사용하여 각 샘플의 반복 길이를 계산
* 반복 길이의 평균 분산 기록
* PCA는 데이터 분리에 가장 많은 영향을 주는 첫번째 주성분에 190 dimension 데이터를 투영하여 MSI score를 생성
* 각 샘플에는 MSI-High (MSI-H) 또는 MSI-Stable (MSS)가 할당, MSI 점수 범위는 manual unsupervised 클러스터링에 의해 MSI-H 또는 MSS가 할당
* 낮은 coverage의 샘플 (< 250X median)은 MSI-unknown이 할당

### TMB 분석


* TMB는 5% 이상의 allele frequency를 가지는 모든 syn, non-sym의 개수를 카운팅 후 dbSNP, ExAC의 알려지거나 가능성이 있는 germline polymerphisms을 필터링
* 이후에도 잠재적인 germline을 제거하기 위해 somatic-germline/zygosity (SGZ) 알고리즘을 사용하여 필터링
* 또한 데이터셋의 bias를 제거하기 위해 알려지거나 likely driver muations에 대해 필터링
* Mutation 개수는 카운트 된 총 변이 수 또는 794 kb에 해당 하는 코딩 영역으로 나눈어 Mb 당 돌연변이 (mut/Mb)로 변환

!!! warning "SGZ(somatic-germline-zygosity)"
	 [SGZ(somatic-germline-zygosity) 논문][5] A computational approach to distinguish somatic vs. germline origin of genomic alterations from deep sequencing of cancer specimens without a matched normal, 2018

[5]: https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005965
### 서열 QC 지표 (Sequence QC metrics)


* 분석 파이프라인 완료 후에는 variant 데이터는 FMI에서 개발한 CATi 소프트웨어를 통해 sequence QC 매트릭과 함께 보여진다.
* 모든 샘플에 대해 데이터 분석 QC로 SNP 프로파일 알고리즘을 사용하여 교차 오염을 평가하여 예상치 못한 오염으로 발생할 수 있는 false-positive의 위험을 줄인다.
* 숙련된 생물정보학자(trained bioinformatics personnel)가 시퀀스 데이터를 검토
* QC 매트릭에 실패한 샘플은 자동으로 보관되고 릴리즈 되지 않음


## 리포트 생성 (Report generation)

* 승인된 결과는 CDx 관련 정보가 포함된 자동화된 소프트웨어에 의해 주석이 추가됨
* 실험실 책임자 또는 지정자가 승인 및 릴리스하기 전에 FMI가 전문 서비스로 제공하는 환자 인구통계 정보와 추가 정보와 통합

## Positive 컨트롤과 관련된 내부 프로세스


### 양성 대조군 (Positive Control)


* Each assay run includes a control sample run in duplicate
* 컨트롤 샘플에는 10개의 HapMap 셀라인 있는 풀이 포함되어 양성 돌연변이 검출 (positive mutation detection)을 위해 사용됨
* 전체 영역에 걸쳐 존재하는 100개의 germline SNP는 분석 파이프라인에 의해 검출되어야 하며, 
* SNP가 검출되지 않으면 잠재적인 오류를 의미하기 때문에 QC 오류가 발생함

### Sensitivity Control


* 양성 대조군으로 사용되는 HapMap control 풀은 분석 파이프라인에 의해 감지되는 5% - 10% MAF의 변이를 포함

### 음성 대조군 (Negative Control)


* 샘플은 라이브러리 구축 과정 (LC stage)에서 분자 바코드딩
* 완벽하게 바코딩된 시퀀스 리드망 분석에 사용
* 분석 파이프라인에는 각 시료의 SNP 프로파일을 분석하여 분자 바코딩 이전에 발생했을 수 있는 잠재적인 오염을 파악하여 1% 미만의 오염을 검출할 수 있는 알고리즘이 포함

## 변이 분류 (Variant classification)


### MET exon 14 skipping을 유도하는 SNVs, indels 바이오마커 규칙


다음 기준 중 하나 이상이 충족되는 경우 MET에서 exon 14 skipping으로 간주

* MET exon 14의 5' 주변의 splice acceptor site, 인트론 지역의 -3에서 -30에서의 5 bp 이상의 deletion
* MET exon 14의 5' 주변의 -1 또는 -2 splice acceptor site의 indels
* MET exon 14의 3' 주변의 splice donor site (0, +1, +2, or +3)의 base substitutions 및 indels

!!! warning "Archer 패널"
	 Archer 패널을 이용한 [MET exon 14 skipping mutation 논문][8] MET Exon 14 Skipping Mutation in Non-Small Cell Lung Cancer Identified by Anchored Multiplex PCR and NextGeneration Sequencing
	 
	 [![exon14 skipping][1]{: width=60%}][1]

    [1]: ../assets/screenshots/met_exon_14.png
    [8]: https://bit.ly/3qjNlbP

### Homologous Recombination Repair (HRR) Genes


* F1CDx 검사에 대한 임상 보고서(clinical report) 가 의사에게 (ordering physician)에게 제공
* 각 보고서는 치료법 확인을 위해 양성인 돌연변이에 대해 임상생물정보학 분석가, 과학자, 큐레이터 및 병리학자로 구성된 내부 팀에 의해 생성 검토
* 각 샘플은 ATM, BARD1, BRCA1, BRCA2, BRIP1, CDK12, CHEK1, CHEK2, FANCL, PALB2, RAD51B, RAD51C, RAD51D, and RAD54L의 14개의 유전자에 돌연변이를 평가

[![HRR genes][2]{: width=60%}][2]

  [2]: ../assets/screenshots/hrr_genes.png

* 이 유전자들은 유해하거나 의심되는 short variant, copy number alteration, rearrangement 변이가 in-house software pipeline에 의해 결정
* COSMIC 데이터베이스에 존재하거나 homozygous deletion은 유해(deleterious)한 것으로 간주
* 유해한 돌연변이가 의심되는 truncating event (splice, frameshift, nonsense alteration)와 코딩 시퀀스를 disrup하는 large rearragements를 포함 
* COSMIC 확인은 HRR 양성으로 의심되는 변이에 대한 second layer 확인
* HRR 유전자의 모든 splice, nonsense, frameshift 변이는 양성 바이오마커로 간주되며, 유해한 변이(또는 FMI reporting 룰에 의한 likely 상태)로 간주
* F1CDx 검사는 아래 규칙에 의해 확인되거나 유해한 HRR 변이를 가진 전립선암 환자에 대해 린판자(olaparib) 치료를 선택하기 위한 수단
* BRCA1, BRCA2, ATM의 특별한 deleterious mutation (DM)과 의심되는 deleterious mutation (SDM) missense 변이 또는 non-frameshift 변이는 아래 표와 같다.
* 그러나 다른 12개의 유전자의 missense, non-frameshift mutation은 HRR 양성으로 간주되지 않는다.

[![deleterious_mutation][3]{: width=50%}][3]

  [3]: ../assets/screenshots/deleterious_mutation.png

### Biomarker Rules for Rearrangements that Lead to NTRK1, NTRK2, or NTRK3 Fusions

* NTRK1, NTRK2, NTRK3 재배열(rearrangements)은 CDx 바이오마커의 양성으로 NTRK1/2/3 RNA fusion으로 이어진다.
* Rearrangement CDx biomarker criterion: 

	* 이전에 보고 되었거나 kinase domain이 중단되지 (not disrupted) 않은 새로운 파트너 유전자와의 NTRK1, NTRK2, NTRK3의 RNA fusion으로 인한 in-strand 재배열로
	* 여기에는 상호간 융합 (reciprocal fusions) 재배열 이벤트 (NTRK-3', 5'-NTRK) 도 포함
* 즉, out-of-strand 이벤트는 non-fusion 재배열 (non-fusion rearrangements)로 분류되어 CDx 음성
* NTRK1, NTRK2, NTRK3 유전자의 internal 재배열 (NTRK1-NTRK1, NTRK2-NTRK2, NTRK3-NTRK3 이벤트) 인 intragenic fusion은 바이오미커 음성
* 확인되지 않은 파트너(encodes as N/A) 또는 LINC non-coding 파트너는 CDx 바이오마커 음성

[![trk_fusion][4]{: width=70%}][4]

  [4]: ../assets/screenshots/trk_fusion.png

!!! warning "DNA 패널에서의 fusion"
	F1CDx는 DNA 기반이기 때문에 NTRK1/2/3의 fusion을 유발하는 rearrangements를 마커로 사용

!!! warning "in-strand"
	in-strand, out-of-strand event?? in-frame, out-frame?

**General NGS**

* High sensitivity and specificity potential
* Multiplexing: simultaneously queries multiple potentially actionable targets4 (eg, ALK, ROS1, RET)
* Detects both known and novel fusions, regardless of breakpoin or fusion patener (depending on the library prep method)

**RNA-Based NGS**

* Able to distinguish in-frame, transcribed gene fusion vs out-of-froame fusions
* Avoid difficulties of sequencing large intronic regions in the NTRK genes

!!! warning "Bayer NTRK testing"
	`Bayer NTRK testing <https://global.ntrktesting.com/>`_

