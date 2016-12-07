---
event: '2015 Brainhack Montreal'

title:  'Automatic Extraction of Academic Collaborations in Neuroimaging'

affiliations: 

- id: aff1
  orgname: 'Montreal Neurological Institute, McGill University'
  street: 3801 University Street
  postcode: H3A 2B4
  city: Montreal
  state: QC
  country: Canada

author:

- initials: SD
  surname: Dery
  firstname: Sebastien
  email: sebastien.dery@mail.mcgill.ca
  affiliation: aff1
  corref: aff1

url: http://github.com/sderygithub/Clubs-of-Science

coi: None

acknow: The authors would like to thank the organizers and attendees of Brainhack Montreal.

contrib: SD wrote the software, performed tests, and wrote the report.
  
bibliography: brainhack-report

gigascience-ref: \href{http://gigadb.org/dataset/100221}{doi:10.5524/100221}
...

#Introduction
Our ability to quantitatively study large-scale social and behavioural phenomena such as peer influence and confirmation bias within scientific circles rest on quality and relevant data \cite{BiologicalNetworks:Freeman2004}. Yet the compilation of specific coauthorship databases are often restricted to certain well-defined fields of study or publication resources, limiting the extent and depth by which investigations can be performed. Ultimately, we aim to understand how the social construct and its underlying dynamics influence the trajectories of scientific endeavours \cite{Sarigol2014:PredictingSuccess}. This work is motivated by an interest in observing social patterns, monitoring their evolution, and possibly understanding the emergence and spreading of ideas and their biases in the neuroimaging community; central themes to deciphering facts from opinions. However, before being able to fully investigate and address these fundamental and inherently complex questions, we need to address the extraction and validation of data. The goal of this project was to leverage publicly available information on Google Scholar (GS) to  automaticaly extract coauthorship networks. 

#Approach
The tool can be accessed through a public website at (http://cos.dery.xyz). The site is constructed using a set of openly accessible libraries allowing the display of coauthorship networks as interactive graphs \cite{Holten2009:ForceDirected}. Visitors can peruse a set of pre-computed networks extracted using custom Python scripts designed to crawl GS based on a set of predefined constraints (e.g. search topic, publication journal). The proposed interface offers seamless manipulation to keep interaction straightforward and easy to use. The simplicity of the design aims to reach a maximum number of users, assuming a minimal level of technical knowledge. 

##### \texttt{GraphConstruction}:
Scholarly citations are commonly found in standardized format, suggesting the structure can be reliably used within an automatic procedure. Moreover, while the result of typical search engines are not structured towards data mining (i.e. mixture of natural language embedded in semi-structured tags and page links), particular combinations of HTML tags and CSS identifiers can be leveraged to extract specific information. This simple scheme allows the reconstruction of large-scale networks of collaborations. Interestingly, Google Scholar also hosts individual pages for authors’ rich with pre-computed metrics of scientific productivity and impact (e.g. cumulative number of citations, h-index, i10-index). This data can be further exploited to structure and highlight part of the network.

##### \texttt{CommunityDetection}:
Scientific communities were detected using a greedy agglomerative modularity optimization process \cite{Blondel08fastunfolding}. 

\begin{table*}[t!]
\centering
\caption{\label{stattable}Completeness study: accuracy between the faculty roster of five major neuroimaging institutes and the neuroimaging network.}
\begin{tabular}{rccccc}
\hline
\multicolumn{1}{c}{\textbf{Institute}} & \textbf{\begin{tabular}[c]{@{}c@{}}Total Count\end{tabular}} & \textbf{Recovered} & \textbf{\begin{tabular}[c]{@{}c@{}}On Google Scholar\end{tabular}} & \textbf{Accuracy} & \textbf{\begin{tabular}[c]{@{}c@{}}Corrected Accuracy\end{tabular}} \\ \hline
\begin{tabular}[c]{@{}r@{}}McConnell Brain Imaging Center\\ (Montreal Neurological Institute)\end{tabular} & 12 & 7 & 9 & 58.33\% & 77.77\% \\
\begin{tabular}[c]{@{}r@{}}Martinos Center for Biomedical Imaging\\ (Harvard University)\end{tabular} & 39 & 12 & 22 & 30.76\% & 54.54\% \\
\begin{tabular}[c]{@{}r@{}}Cognitive-Neuroimaging Unit\\ (INSERM-CEA, France)\end{tabular} & 15 & 7 & 8 & 46.66\% & 87.50\% \\
\begin{tabular}[c]{@{}r@{}}Wellcome Trust Center for Neuroimaging\\ (University College London)\end{tabular} & 16 & 10 & 11 & 62.50\% & 90.90\% \\
\begin{tabular}[c]{@{}r@{}}FMRIB\\ (Oxford University)\end{tabular} & 17 & 8 & 11 & 47.05\% & 72.72\% \\ \hline
Totals & 99 & 44 & 61 & 49.06\% & 76.69\% \\ \hline
\end{tabular}
\end{table*}

##### Validation:
To assess the recovered network’s reliability we performed a spot check on its content. First we examined the accuracy of 100 randomly selected researchers from the network and sought after their departmental affiliation and publication journals to confirm their belongin to the broad field of neuroimaging. The dependence on profiles availability injects a strong negative bias. To better appreciate the crawling ability to construct network we further compare with the number of members having a Google Scholar page in the form of a corrected accuracy.

# Results
96 researchers were confirmed to have direct institutional affiliation to neuroscience, psychology, or biomedical engineering departments. The remaining 4 randomly selected researchers were found to work in the fields of human genome sequencing, image analysis, nano particles, and pharmacology. Note that these individuals were located on the outskirts of the main graph. To further assess completeness of the network, we compared results with faculty rosters of 5 major neuroimaging institutes (Table 1).


\begin{figure}[h!]
  \includegraphics[width=.47\textwidth]{neuroimaging-500}
  \caption{\label{centfig}
  Coauthorship network for the field of neuroimaging. Each disk represent a single researcher with its radius encoding log10(Nc), where Nc is the number of citations. Edges stand for a binary relation of coauthorship between two researchers.}
\end{figure} 


# Conclusions
Accuracy results suggest a sufficient number of individuals are registered through GS to make it a useful platform of discovery. Meticulous inspection of the grouping suggest that communities typically embed either a geographical or a topical component, that is to say, certain communities are seemingly brought together by either proximity or similarity of interest. With the increasing complexity of science, finding accurate and relevant information on specific topics is a challenging task.  We feel that a better appreciation of the wealth and variety of opinions within scientific communities may help enforcing the notion that grand claims require grand evidence.

