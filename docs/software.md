---
template: overrides/main.html
---
# 소프트웨어 시작하기

## 소프트웨어 목적

- 본 소프트웨어는 암 환자를 위해 종양학에서 전문적인 지침에 따라 의료전문가가 사용할 종양 돌연변이 프로파일링 (provide tumor mutation profiling) 제공하는 소프트웨어로 클라언트/서버 구조로 되어 있다. 
- 엔젠바이오 제품은 Research Use Only 제품이며 연구용으로만 사용됩니다. 
- 엔젠바이오 제품은 진단, 예후, 치료 또는 치료를 위한 것이 아닙니다.

## 소프트웨어 구조

- 소프트웨어는 클라이언트/서버 구조로 __NGAS Server__ 쪽의 __API Sever__ 를 통해 __NGAS Client__ 와 분석 요청 및 결과를 제공하는 구조이다. 
-  __NGAS Server__ 는 __NGAS Client__ 및 __Analysis Server__ 와 연동되며
-  __Anaysis Server__ 는 파이프라인을 실행하는 __Analysis Engine__ 과 실제 분석 대상이 되는 __Panels__ 로 구성되어 있다.
-  __Panels__ 은 분석 용도에 따른 파이프라인, 어노테이션, 해석 부분으로 구성된다.

[![software architecture][1]{: width=70%}][1]

  [1]: assets/screenshots/software_architecture.png

## 패널


| Panel                    | Panel version     | Pipeline            | Pipeline version    | Annotation          | Interpretation         |
|--------------------------|-------------------|---------------------|---------------------|---------------------|------------------------|
| BRCAaccuTest             | v1.5              | BRCA                | v1.5                |                     |                        |
| HEMEaccuTest DNA         | v1.4              | DNA                 | v1.3                |                     |                        |
| HEMEaccuTest RNA         | v1.0.1            | RNA                 | v1.0                |                     |                        |
| SOLIDaccTest DNA         | v1.5              | DNA                 | v1.3                |                     |                        |
| ONCOaccuPanel            | v1.2              | ONCO                | v1.2                |                     |                        |

## 파이프라인

파이프라인은 __DNA__, __RNA__, __ONCO__, __BRCA__ 의 4가지 파이프라인이 존재하며, 6개의 패널이 이들 4개의 분석 파이프라인을 사용한다.


- 각 파이프라인은 분석할 수 있는 패널(제품)이 매칭되며, 동일한 파이프라인이라도 적용되는 패널마다 파이프라인이 설정 가능한 고유한 설정값들을 가진다.
- 패널은 분석시약과 고유한 설정값이 적용된 파이프라인이 포함된 분석 소프트웨어와 결합한 형태로 제공된다.


| Pipeline                 | Version           | Mutation type                  | Pipeline validation | Update date                                  |
|--------------------------|-------------------|--------------------------------|---------------------|----------------------------------------------|
| DNA                      | v1.4              | SNV/INDEL, large InDel, CNV    | yes                 |                                              |
| RNA                      | v1.0.1            | Fusion, MET exon 14 skipping   | yes                 |                                              |
| ONCO                     | v1.2.0            | SNV/INDEL, CNV, Fusion         | yes                 |                                              |
| BRCA                     | v1.5              | SNV/INDEL, CNV                 | No                  |                                              |

[![software overview] [2]{: width=70%}][2]

  [2]: assets/screenshots/overview.png 


## 성능 검증

- 파이프라인의 성능 시험
	- 파이프라인은 분석하고자 하는 목적(SNV/INDEL, Large Indel, CNV, Fusion 등)에 따라 패널에 종속되지 않고 성능 시험을 한다.
- 성능 시험 샘플 종류
	- NGS 또는 기존의 검사법으로 확인된 임상 샘플
	- 분석하고자 변이에 대한 정보를 알려진 표준물질(standard material)
	- 인위적으로 변이를 추가한 in-silico 데이터
- 성능 시험 데이터 생산 플랫폼
	- 타 패널 또는 WGS, WES와 상관없이 생산된 NGS 데이터
	- 자사의 패널을 통해 생산된 NGS 데이터

!!! warning "파이프라인 버전"

	파이프라인의 성능 평가와 패널의 성능 평가는 각기 다른 목적을 가지고 있다. 파이프라인의 성능 평가는 플랫폼에 상관없이 파이프라인 자체가 변이들을 얼마나 정확하게 찾아내는지에 목적이 있다면, 패널의 성능평가는 패널이 생산한 데이터를 통해 얼마나 정확하게 변이를 찾아내는지가 목적이다. 따라서 가장 최적화된 파이프라인과 패널의 성능 검증은 해당 패널을 통해 생산된 데이터를 가지고 파이프라인을 검증하는 것이다.
	
	* 파이프라인 성능 검증시에는 다양한 패널로 부터 생산된 데이터를 활용하는 것이 바람직하다. 
	* 패널 자체의 성능 검증에 사용된 파이프라인이 곧 SW에 적용되는 파이프라인은 아니다.   

