Phylogenetic analysis of Carbonic Anhydrase Gene family in Arthropods

QC details: I am using data that are uploaded on genome databases by other researchers. Therefore, I will not perform quality control using QC. Instead, I will perform my own "quality control" by selecting good genome that are gathered with NGS. This could be determined through BLASTing known D.mel paralogs. I omitt species that gives out multiple predicted paralogs that are >100 aa. 

Data details: I am collecting paralogs from various online databases, including Ensembl,Genbank,i5k,FlyBase,FleaBase,and WormBase. Once the new E.aff genome comes out, I will use local BLAST to update my paralogs. 

2/12:
constructed a preliminary tree ---- align from seperate clades w high Bootstrap values. 
Manual align ---- start all paralogs from the same point --- manually align from aa.

2/17:
Constructed an alignment with T-COFFEE`s M-COFFEE on my crustacean paralogs(E.aff,D.ma,T.ca)

T-COFFEE relies on the construction of a library,both local and global, that is later changed into an alignment. The algorithm will compute the "best" tree that encompasses teh most library constraints.T-COFFEE has its limitation in that it is more CPU intensive in comparison to Clustal W. Although T-COFFEE tends to be more accurate, it takes twice as much time. In addition, T-COFFEE (especially M-COFFEE), as the nature of its algorithm, assumes that a divergent branch with a lot of noise is not considered as important even when it contains alot of information. This is because the algorithm prefer not to extravagate extra noise for the information, thus leaving it unpreferred.  

command line: t_coffee -in=crustacea.txt Mpcma_msa Mmafft_msa Mclustalw_msa Mdialigntx_msa Mpoa_msa Mmuscle_msa Mprobcons_msa Mt_coffee_msa -output=score_html clustalw_aln fasta_aln score_ascii phylip -tree -maxnseq=150 -maxlen=2500 -case=upper -seqnos=off -outorder=input -run_name=result -multi_core=4 -quiet=stdout

Of the 44 paralogs inserted, 5 of them exhibited average cost value, which shows that it does not align well as the other paralogs (Dmag CAH5,7,CARP1,Eaff CAH3,6). I need to decide whether I want to pull them out of my data. Saved the alignment data as "crustacea align.txt" and visualized on UGENE. Interestingly, it has aligned much less sequences compared to the MUSCLE algorithm, which is favorable. The MUSCLE software aligned many unconserved lines that made it really hard to manually edit. 

3/14:
found papers regarding to CA domains --- pulled paralogs lacking CAH domains. Especially the GSEH, ELH, and NNGH domains. These include  LPol_5,14,16,17 D_Mag_2,8,CARP3 TCal_CAH5 DMel_CAH4,10,11,12 MSex_CAH4,9. 

3/15: 
Mined European Centipede SMar from Ensembl Metazoa ---- Assembly from Chipman AD. 2013 w paper (https://doi.org/10.1371/journal.pbio.1002005)----- a rigid rejection limit was taken at an E value of E^-5. BLASTed against Drosophila paralogs (DMel_1 to DMel_CARPb)----- Mined  15 paralogs, in which 9 sequences had 200+, indicating a possible usability. ---- Confirmed all paralogs by BLASTing them against C.elegans and F.candida for confirmation.

3/17:
Tried to rescue some sequences from well annotated species that seem to be missing exons. Dmel_2,3,4. From JBrowse, it seems like these CAHs are do not transcribe certain conserved domains, unless possible annotation errors. I decide to keep CAH2, but tossed CAH3,4.

3/23:
Pulled sequence:Lpol5,14,16,17. Dmag2,8. Eaff13. TCal5. MSex9. These are pulled due to the poor alignment. Some are obviously missing multiple domains and is likely inrescuable. 

3/27:
Ran MUSCLE with the new sequences. on ebi.ac.uk web server. output format:FASTA. The M-COFFEE alignment contained alot of errors.... misaligned domains, random shifts that is just straight up wrong. MUSCLE seems to be much consistent and accurate in that sight. I do like how it spits out the sequences in the order of the initial NJ tree it utilized.

4/6:
Ran IQ-TREE: local optima approximated through stochastic, hill climbing NNI. Each move is randomly tested and the move is accepted if it increases the tree likelihood. In order to escape from being stuck in a single optima, stochastic NNI will radically perturb the tree to increase the chance of escaping. This method is good since it offers the user model and parameter choice. I, howver, think that Mr.Bayes might be better...

settings: ran "20species-edited" in protein. Subs model: GTR with Gamma rate and 4 #rate categories. Bootstrap --- ultrafast w 1000 iterations and a minimum correlation coefficient of 0.99. 1000 replicates was utilized. Perturbation strength of 0.5 and stopping rule of 100 is chosen. 
