---
template: overrides/main.html
---

# 리뷰
변이 리뷰는 Single Nucleotide Variant (SNV) / Insertion-Deletion Mutations (INDEL), Copy-Number Variation (CNV), Microsatellite Instability (MSI), Tumor Mutational Burden (TMB) 분석 결과에 대한 리뷰 및 검증 작업으로써, 분석 결과에 대한 거짓 양성(false positive) 변이를 분석 결과에서 제외하는 것이 일차적인 목적이다.

## 낮은 VAF 변이 리뷰
SNV/INDEL 탐지는 주어진 염기서열 데이터에서 depth가 30 이상이고, 최소 3개의 이상의 변이를 가지고 있을 때, 3% 수준의 Variant Allele Frequency (VAF)까지 탐지가 가능하다. 하지만 암 종별 주요 유전자에 대한 변이는 VAF 기준이 최소 0.1%까지 낮아 질 수 있어, 이에 따른 false positive 변이도 다수 포함될 수 있기 때문에 변이 대한 매뉴얼 리뷰 과정이 필요하다.


### VAF 10% 미만 변이 필터
탐지한 변이 중 VAF가 10% 미만 경우, false positive 변이가 주로 발생하는 것으로 나타나기 때문에 10% 미만 변이에 대한 리뷰를 우선 진행한다.
- 변이 결과 리스트 창에서 왼쪽 상단의 New Filter 버튼을 클릭한다.
- 필터 창에서 Read Coverage 항목의 Allele Fraction 값을 10%로 설정한 후 Save Filter를 클릭하여 필터 설정을 완료한다.
- 변이 결과 정보 리스트 창에서 왼쪽 상단에 있는 Variant Filter 항목 아래에 있는 New Filter 버튼을 클릭하여 저장된 필터를 선택한다.

### Warning 변이 확인

- VAF 10% 이하 인 변이의 Warning 표시된 변이(아래 Mutect2 warning 메세지 참고)에 대해 메세지를 확인한다.
- Warning 메세지는 변이 탐지 하였으나 Mutect2의 변이 조건에 적합하지 않은 경우 나타나는 메세지로 Mutect2 변이 규정에 PASS 되지 않은 변이를 의미하며, IGV 등을 통해 주변 시퀀스를 확인한다.

[![release_01][1]{: width=60%}][1]

  [1]: ../../../assets/screenshots/f_09_03.png  

  
- 해당 변이에 대해 IGV 확인 전 variant detail을 선택하여 주변 시퀀스 확인하여 repeat region인지를 확인 한다.
 

[![release_01][2]{: width=60%}][2]

  [2]: ../../../assets/screenshots/f_09_04.png  

- 확인 된 변이에 대해서 false 처리한다.
  

!!! note "Mutect2 warning 메세지"

	=== "Site filtered due to contraction of short tandem repeat region"

	    repeat region에서 발생하는 false positive 변이는 주로 INDEL이 많았으며, 1bp 수준으로 VAF가 20\%미만으로 나타난다. 그러므로 repeat region에 존재하는 1bp 수준의 VAF 20\%미만 INDEL변이는 false positive 가능성이 높을 것으로 예상된다.
	
	=== "Clustered events observed in the tumor"

	    Clustering Event 변이가 공통적으로 나타난 Read는 Mapping Quality 정보를 나타내는 MAPQ 값이 30 보다 낮거나, 서열 불일치를 나타내는 Number of Mismatch(NM)의 값이 보통 3 이상의 값을 가지고 있다.

  
## 통계 정보를 활용한 변이 리뷰
분석된 변이에 대해 샘플, 패널, 그리고 그룹 단위의 통계 빈도에 대해서 제공하고 있다. 이 빈도 정보를 이용하여 리뷰에 활용할 수 있다. RUN은 해당 샘플과 동시에 분석을 진행한 샘플들에 대한 정보, PANEL은 해당 샘플과 동일한 패널을 사용한 샘플들에 대한 정보, 마지막으로 GROUP은 접속한 아이디와 동일한 그룹으로 분석을 진행한 샘플들에 대한 정보를 제공한다.

- 변이 통계 자료는 확인하고자하는 변이를 마우스로 더블 클릭하여 변이에 대한 상세보기 화면으로 이동한다.
- 변이 통계에서 사용자가 선택한 변이가 높은 비율로 나타났다면, 빈번하게 발생하는 변이인 만큼 false positive 변이로 지정한다.

[![release_01][3]{: width=60%}][3]

  [3]: ../../../assets/screenshots/f_09_05.png  

## 7가지 false positive 사례로 본 리뷰
VAF나 Warning 메세지 뿐만 아니라 모든 변이들은 사용자가 직접 리뷰를 수행해아 한다. 여기서는  FP가 빈번히 나타나는 6가지 사례를 기반으로 리뷰하는 방법에 대해 기술한다. 대부분의 사례는 변이 정보 리스트 창에서 변이를 선택 한 뒤, IGV 프로그램으로 실행하여 리뷰를 진행한다.

<div class="tx-columns" markdown="1">
- [x] 반복 영역의 INDEL 변이
- [x] Short Tandem Repeat 영역 변이
- [x] Clustered Event 변이
- [x] Strand Bias 변이
- [x] Low Mapping Quality 변이
- [x] MNP(multiple nucleotide polymorphism) 변이
- [x] Low Alternative Count 변이
</div>

[![release_01][4]{: width=60%}][4]

  [4]: ../../../assets/screenshots/f_09_13.png  

### 반복 영역의 INDEL 변이 예

- 리뷰하고자 하는 INDEL 변이를 더블클릭하여 선택한 후 variant detail 화면에서 변이 주변 서열을 확읺나다.
- INDEL 변이인 경우 repeat 영역 변이인지 확인한다.

[![release_01][5]{: width=60%}][5]

  [5]: ../../../assets/screenshots/f_09_01.png  


[![release_01][6]{: width=60%}][6]

  [6]: ../../../assets/screenshots/f_09_02.png  

  
### Short Tandem Repeat 영역 변이

- 변이 타입이 Insertion 일 경우, IGV 화면 창에서 변이 탐지 위치 위에 마우스 오른쪽 버튼을 클릭 한다. 메뉴 리스트에서 “Sort alignment by”항목 아래에 있는 “base”를 선택하여 read를 정렬한다.
- 정렬 후 IGV 화면에서 Insertion 변이를 가지고 있는 read가 윗부분에 나타나는 것을 확인 할 수 있다.


[![release_01][7]{: width=60%}][7]

  [7]: ../../../assets/screenshots/f_09_06.png  

- 반면, 변이 타입이 Deletion 일 경우, 변이 탐지 위치의 오른쪽으로 1 base pair 이동 후, 2번에서 진행한 과정과 같이 마우스 오른쪽 버튼을 클릭하여 read 정렬 옵션들 중 base기준으로 read를 정렬한다. 정렬 후 IGV 화면에서 deletion변이를 가지고 있는 read가 윗부분에 나타나는 것을 확인 할 수 있다.
- Read를 정렬 후 INDEL 변이가 나타난 위치가 repeat region이고, VAF가 20\% 미만이라면 false positive변이로 볼 수 있다.


[![release_01][8]{: width=60%}][8]

  [8]: ../../../assets/screenshots/f_09_07.png  

!!! note "Short Tandem Repeat Region"

	Short Tandem Repeat Region변이는 repeat region에서 발견되는 변이를 말한다. Short Tandem Repeat Region의 경우 시퀀싱 과정 중에 repeat region에 대한 장비의 에러(Erorr)율 영향으로 repeat서열을 끝까지 읽지 못하는 한계가 존재하여 발생한 문제이다.



### Clustered Event 변이

- 변이를 Base 기준으로 정렬한다.
- 변이가 나타난 주변 정보를 좀 더 넓게 보기 위해 IGV 프로그램에서 Zoom Out기능을 활용한다. Zoom Out기능은 IGV 프로그램 오른쪽 상단의 - 버튼을 클릭하여 적용 가능하다. 반대로 Zoom In 기능으로 IGV 프로그램 오른쪽 상단의 + 버튼으로 화면 조절이 가능하다.
- 변이의 인접한 지역에 또 다른 변이가 존재하고, 인접한 지역에 나타나는 변이가 동일 read상에 존재하고 있으면, Clustered Events 변이라 볼 수 있다. 해당 변이는 false positive로 볼 수 있기 때문에 변이 정보 리스트 창에서 FALSE 버튼을 클릭하여 처리한다.


[![release_01][9]{: width=60%}][9]

  [9]: ../../../assets/screenshots/f_09_08.png  

!!! note "Clustered Event"
	Clustered Event 변이란, 단일 read(1 bp)에서 복수의 변이가 동시에 존재하는 것을 말한다. Clustered Event 변이가 발생하는 이유는 염기서열 해독하는 과정에서 실험적인 오류 또는 Quality가 낮은 서열이 들어가 있는 Read의 존재, 그리고 Read가 가지고 있는 서열이 특정 유전자 지역 외에 다른 유전자에도 유사한 서열이 존재하여 Mapping이 정확히 되지 않는 것이 주요 원인이다.


### Strand Bias 변이

- 변이를 Base 기준으로 정렬한다.
- Read의 색상이 한쪽 strand에서만 발생하는 즉, 변이가 나타나는 곳이 파란색이거나 혹은 빨간색에만 존재한다면, strand bias변이로 false positive 변이로 판단해야 한다.
- IGV 프로그램에서 read의 색깔이 회색만 존재한다면, read의 색깔을 strand 별로 처리하는 옵션을 선택하여 (IGV 화면에 read 위치에 마우스 위치를 놓고, 오른쪽 마우스 클릭을 통해, IGV 기능 메뉴를 볼 수 있으며, 여기서 Color Alignment By 목록 아래에 있는 read strand를 클릭을 하면 된다), read의 strand의 색깔을 변경 할 수 있다. 옵션 처리 후에 read의 색은 + strand의 경우 빨간색, - strand의 경우 파란색으로 나타난다


[![release_01][10]{: width=60%}][10]

  [10]: ../../../assets/screenshots/f_09_09.png  

!!! note "Strand bias"
	Strand bias 변이란, 변이가 나타난 read의 strand가 특정 방향에서 주로 발생한 경우를 말한다. 이러한 변이는 read의 한 쪽 방향에서만 변이가 나왔을 경우 염기서열 해독 과정의 오류의 영향으로 인해, 발생하는 false positive 변이일 가능성이 높다. 


### Low Mapping Quality 변이

- 변이를 Base 기준으로 정렬한다.
- IGV 프로그램에서 변이를 가지고 있는 read 상세 정보 창의 mapping 부분에서 MAPQ 값을 확인 할 수 있다. IGV 화면에서 read 그림 위에 마우스 위치 놓으면, 자동으로 read의 Mapping quality 정보가 포함된 노란색 POP-UP 창이 생긴다. POP-UP창에서 Mapping = Primary @ MAPQ \#\#이란 항목에 있는 점수를 통해 Mapping Quality 정보를 알 수 있다.
- 변이를 가지고 read의 MAPQ 값이 대부분 30 이하 경우, low-mapping quality 변이이자 false positive변이 임으로, 분석결과 변이 정보 리스트 창에서 False 버튼을 클릭하여 false positive 변이로 규정을 한다.

[![release_01][11]{: width=60%}][11]

  [11]: ../../../assets/screenshots/f_09_10.png  

!!! note "Low Mapping Quality"
	Low-Mapping Quality 변이란, 변이를 가지고 있는 read의 mapping quality가 낮아, 변이 탐지 결과의 신뢰도가 낮을 수 있는 변이를 말한다. 변이를 가지고 있는 read의 서열이 특정 유전자뿐만 아니라 다른 유전자의 서열과 유사도가 높다면, 여러 지역에 mapping 될 수 있어 mapping에 대한 정확도가 떨어지게 된다. 이러한 확인은 mapping quality 수치로 확인 할 수 있으며, IGV 프로그램을 통해 MAPQ의 정보를 알 수 있다. 보통 60이면 mapping quality가 높은 편이고, 30 이하 일 경우 낮은 수치임으로 Low-mapping quality로 정의를 내린다. 이러한 변이는 대부분은 false positive 경우가 많으며, 이에 대한 사용자의 매뉴얼 및 후속 분석과 검증이 필요하다.


### MNP 변이

- 인접한 SNV변이가 같은 read에서 나타나는지 확인 필요하다. 인접한 유사한 사례로 추정이 되면, 본 변이는 false positive 변이이자, MNP 변이 될 수 있는 확률이 높게 된다. 이러한 과정에서 해당 변이의 변이 통계 확인을 통해, 한 번 더 검토가 필요하다.
- 앞서 언급 했듯이, 해당 변이의 변이 통계를 확인하고, 다른 샘플 및 분석에서도 빈번하게 발생하는 변이라면 false positive 변이로 판단 할 수 있으며, FALSE 버튼을 클릭하여 처리한다.

[![release_01][12]{: width=60%}][12]

  [12]: ../../../assets/screenshots/f_09_11.png  

!!! note "Multi-Nucleotide Polymorphism (MNP)"
	Multi-Nucleotide Polymorphism (MNP) 변이는 2개 이상의 SNV변이가 인접한 위치에 탐지되는 변이를 말한다. 분석결과 변이 정보 리스트 창에서 해당되는 변이 타입 정보를 Complex로 정의를 하였다. 이러한 변이 현상은 앞에 소개된 target 변이 통계 정보를 통해서 확인이 가능하다 (변이 통계를 확인하여 자주 나타나는 변이라면, false positive 변이라고 정의를 내릴 수 있다). 

### Low Alternative Count 변이

- 변이를 Base 기준으로 정렬한다.
- IGV 화면에서, 변이를 가지고 있는 read의 수를 확인하고, 혹시 read의 수가 6개 미만인 경우, IGV 화면에서 read 위치에 놓은 다음, 마우스 오른쪽 버튼을 클릭하여, View as Pairs 항목을 클릭을 하여, paired read 모드로 변경한다. 그 다음 sort alignment by 항목 아래에 있는 base 기준으로 read를 다시 정렬 한다.
- View as pair의 IGV 환경에서, 변이를 가지고 있는 read의 수가 3개 미만이라면, 해당 변이는 false positive변이로 판단됨으로, FALSE 버튼을 클릭하여 처리한다

[![release_01][13]{: width=60%}][13]

  [13]: ../../../assets/screenshots/f_09_12.png  

!!! note "Low Alternative Count"
	Low alternative count변이란, alternative allele을 가진 read의 수가 후속 분석 작업을 통해 최종 확인하였을 때, 3개 미만인 경우 변이를 말한다. 즉 IGV 프로그램을 통해 변이를 가진 read의 수가 3개를 충족했다고 하더라도, 3개 중에서 paired read에서 변이가 나왔다면 결국 변이를 가지고 있는 독립적인 read의 수는 2개라고 볼 수 있다. 변이를 가지고 있는 read의 수가 최종 2개라면, 변이 탐지를 위한 최소 read 수 3개를 만족하지 못한다. 결국 이러한 변이는 변이 탐지 결과의 신뢰 수준 및 정확도 떨어짐으로, 사용자는 이러한 변이를 매뉴얼 및 후속 분석과 검증 작업을 통해서 선별이 꼭 필요하다.


## 기타 변이  리뷰

### MSI 리뷰
MSI는 대장암 샘플에서만 사용하며, 분석 샘플에서 SNV/INDEL의 개수가 30개 넘고, INDEL의 비율이 20% 이상일 경우, MSI-High로 규정해 놓았다. 그리고 MSI marker로 ACVR2A 유전자에서 K43Rfs*5변이가 있는 경우에는 MSI-High로 표시가 된다.

변이에 대해 false로 지정하는 경우 실시간으로 반영되어 MSI 결과는 자동으로 업데이트 되며, 또한 MSI-High와 MSI-Stable에 대한 정의도 자동화로 업데이트가 되며, 함꼐 제공되는 타 MSI 분석 결과(mSINGs, MSIseq, MSIpred)를 참고한다.


### TMB 리뷰
분석 결과 SNV/INDEL변이 개수가 15개 이상인 경우 TMB High에 해당되며, 15개 미만일 경우는 TMB Low 선정된다. 변이에 대해 false로 지정하는 경우 실시간으로 반영되어 TMB 결과는 자동으로 업데이트 된다.

### CNV 리뷰
CNV분석결과에 대한 데이터 기준은 Copy Number 값이 5 이상이면 Copy gain, 0 이면 Copy loss로 처리 된다. CNV 판정에 대한 기준는 Tumor purity가 반영되어 결과에 영향을 주기 때문에 Tumor purity가 50\% 미만이라면 CNV가 여러 유전자에서 나올 수 있기 때문에 Tumor Purity가 50% 미만이고, Copy number 값이 기준인 5 또는 0인 경우 Log2 Value 나 실제 유전자의 coverage정보를 확인하여 CNV를 판정한다.

HTML의 CNV 시각화 자료는 염색체 순서로 Log2 Value에 따라 작성되었으며, CNV 결과에 따라 색깔로 구분되어 진다. CNV로 판정된 유전자 주변의 CNV로 판정되지 않는 다른 유전자의 Log2 Value값이 비슷하다면 false positive로 볼 수 있기 때문에 CNV 결과 리스트 창에서 False 버튼을 클릭하여 처리해야 한다. 


[![release_01][14]{: width=60%}][14]

  [14]: ../../../assets/screenshots/f_09_14.png  

### SV 리뷰

- SV의 Target 컬럼에서 타겟 유전자에 대해서 일어났는지 확인 한다.
- SV가 일어난 유전자의 Coverage 정보를 확인한다.
- SV는 발생한 위치정보 또한 중요하기 때문에, IGV 프로그램을 이용하여 SV가 일어난 상세 위치 정보를 확인 한다.
- SV가 일어난 상세 위치 확인은 SV리스트 왼쪽 하단의 IGV 버튼을 클릭하면, IGV 프로그램으로 SV를 확인 할 수 있다.
- IGV 프로그램에서는 SV가 일어난 read의 정보 중에서 Mate start를 확인해야 한다. 
- Mate start 위치는 SV가 일어난 read의 Pair read 위치 정보로 SV 결과의 근거 자료가 될 수 있다.
- IGV 프로그램에서 SV 위치에 근거가 될 수 있는 read 정보가 없다면, false positive로 볼 수 있기 때문에 SV 결과 리스트 창에서 False 버튼을 클릭하여 처리 한다. 
- 시퀀싱 데이터의 품질에 따라 soft-clip 비율이 차이가 있으며(품질이 떨어질 경우 soft-clip 리드 비율 증가), soft-clip 의 비율이 감소하면 false positive 로 추정되는 fusion 결과는 감소 할 수 있다.

[![release_01][15]{: width=60%}][15]

  [15]: ../../../assets/screenshots/f_09_15.png  


!!! note "Fusion traget 유전자"
	Fusion을 보기 위한 주요 target 유전자는 NTRK1, ALK, ROS1, EGFR, RET 유전자로 해당 유전자에서 fusion을 발견한 경우 Target에 T 버튼이 활성화 된다. 본 패널에서는 Non-small cell lung cancer인 경우에는 파트너 유전자와 관계없이 EGFR, ROS1, RET, ALK 유전자가 포함된 Gene Fusion에 대해서는 주요한 Gene Fusion로 판정하며, NTRK1 유전자가 포함된 Gene Fusion는 앞서 언급한 Non-small cell lung cancer를 포함한 모든 고형암에서 주요한 Gene Fusion로 판정한다.

!!! note "Fusion 분석"
	Fusion 분석은 soft-clip 또는 unmapped read를 사용하여 contig를 생성하고, 이때 contig 생성을 위한 최소 read가 >2이다. 이 contig서열을  BLAT을 통해 매핑시킨 후 하나의 contig에 2개 이상의 유전자가 매핑되어야 break point와 함께 fusion으로 보고된다. 따라서 unmapped read를 이용하여 contig를 생성한 경우 IGV상에서 확인이 불가능하다.


## Gene fusion 근거 리뷰
Clinical Interpretation of Variants in Cancer (CIViC) 기반으로 Gene Fusion에 대한 Tier 정보를 제공 "부록 D. Fusion Database" 참고 한다.

- SV 변이 리스트 항목의 왼쪽과 오른쪽 유전자의 염색체 번호와 위치 정보를 확인한다.
- 확인한 정보를 fusion db에 존재하는지 확인하여, 두 유전자 영역 중 1개라도 Gene Fusion의 Breakpoint가 포함되는지 확인한다.
- Fusion db에 있는 리스트 정보와 SV 변이 리스트의 정보가 일치하면 해당 Tier 정보를 적용한다.
- 검체의 암종과 동일하지 않는 경우, 앞서 언급한 AMP/ASCO/CAP 가이드라인에 따라서 Tier II로 적용한다.
