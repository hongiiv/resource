---
template: overrides/main.html
---

# Evidence/Actionability analysis

각 샘플에서 발견된 변이에 대한 임상적 의의(clinical actionability)를 결정하기 위해 2개의 외부 clinical annotation database를 사용함
- Cancer Biomarkers database from CGI(Cancer Genome Interpreter) (Jan 17th 2018)
- CIVIC\cite{Griffith:2017fh} - Clinical interpretations of variants in cancer (November 5th 2019)

데이터를 통합하고 비교할 수 있도록 다음의 규칙을 사용하여 각 데이터베이스를 공통 데이터 모델(common data model)에 매핑함

## 근거 레벨 매핑- Level of evidence mapping

\begin{longtable}{|l|l|l|p{7cm}|}
\hline
\textbf{NGeneBio} & \textbf{AMP Guideline} & \textbf{CIViC} & \textbf{CGI} \\
\hline
A & A & A(Validated association) & FDA guidelines, NCCN guidelines, NCCN/CAP guidelines, CPIC guidelines, European Leukemia Net guideline \\
\hline
B & B & B(Clinical evidence) & Clinical trials, Late trials, Late trials, Pre-clinical \\
\hline
C & C & C(Case stuidy) & Early trials, Case report \\
\hline
D & D & D(Preclinical evidence) & Pre-clinical \\
\hline

\hline
\end{longtable}

## Response type mapping

\begin{longtable}{|l|l|l|p{7cm}|}
\hline
\textbf{NGeneBio} & \textbf{CIViC} & \textbf{CGI} & \textbf{비고} \\
\hline
Response & Sensitivity & Responsive &  \\
\hline
Resistant & Resistant or Non-Response & Responsive & \\

\hline
\end{longtable}