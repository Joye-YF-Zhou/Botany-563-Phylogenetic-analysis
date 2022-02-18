Phylogenetic analysis of Carbonic Anhydrase Gene family in Arthropods

QC details: I am using data that are uploaded on genome databases by other researchers. Therefore, I will not perform quality control using QC. Instead, I will perform my own "quality control" by selecting good genome that are gathered with NGS. This could be determined through BLASTing known D.mel paralogs. I omitt species that gives out multiple predicted paralogs that are >100 aa. 

Data details: I am collecting paralogs from various online databases, including Ensembl,Genbank,i5k,FlyBase,FleaBase,and WormBase. Once the new E.aff genome comes out, I will use local BLAST to update my paralogs. 

2/12:
constructed a preliminary tree ---- align from seperate clades w high Bootstrap values. 
Manual align ---- start all paralogs from the same point --- manually align from aa.
2/17:
Constructed an alignment with T-COFFEE`s M-COFFEE on my crustacean paralogs(E.aff,D.ma,T.ca)
command line: t_coffee -in=crustacea.txt Mpcma_msa Mmafft_msa Mclustalw_msa Mdialigntx_msa Mpoa_msa Mmuscle_msa Mprobcons_msa Mt_coffee_msa -output=score_html clustalw_aln fasta_aln score_ascii phylip -tree -maxnseq=150 -maxlen=2500 -case=upper -seqnos=off -outorder=input -run_name=result -multi_core=4 -quiet=stdout
Of the 44 paralogs inserted, 5 of them exhibited average cost value, which shows that it does not align well as the other paralogs (Dmag CAH5,7,CARP1,Eaff CAH3,6). I need to decide whether I want to pull them out of my data. Saved the alignment data as "crustacea align.txt" and visualized on UGENE.

