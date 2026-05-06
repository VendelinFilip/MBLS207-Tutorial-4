# Tutorial 4 – part 2
Sequence similarity searching with BLAST

In the recent Bioinformatics lecture, you have learned about BLAST, which is like Google for DNA sequences. Indeed, the BLAST program and a well-annotated database is all you need to reproduce published (and nearly-published, as we will see below) bioinformatic analyses.

As you all very well know, in late 2019, a viral epidemic started spreading in China. Ground Zero for the outbreak of the new disease appeared to be a seafood market in the Chinese province Wuhan. In record time, the virus was analyzed, sequenced and soon after identified as a [Coronavirus](https://en.wikipedia.org/wiki/Coronavirus), similar to the viruses causing the SARS and MERS epidemics. This virus was named SARS-CoV2, although some early papers also used the name 2019-nCoV.

On 31st of January 2020, Pradhan et al. posted a preprint on bioRxiv¹ with an exciting title: "[Uncanny similarity of unique inserts in the 2019-nCoV spike protein to HIV-1 gp120 and Gag](https://www.biorxiv.org/content/10.1101/2020.01.30.927871v1)". In this article, the group claimed that "*Although, the 4 inserts represent discontiguous short stretches of amino acids in spike glycoprotein of 2019-nCoV, the fact that all three [sic!] of them share amino acid identity or similarity with HIV[...]* suggests that this is not a random fortuitous finding"[²](https://www.biorxiv.org/content/10.1101/2020.01.30.927871v1.full), implying that the Coronavirus pandemic was caused by a virus with similarities to HIV and possibly represented an artificial (man-made) pathogen consisting of parts from different viruses.

Despite the fact that the article was withdrawn by the authors within hours of being posted, it went viral, and ended up being picked up by newspapers around the world. *BioRxiv reacted swiftly by posting a warning above each article, stating "bioRxiv is receiving many new papers on coronavirus 2019-nCoV. A reminder: these are preliminary reports that have not been peer-reviewed. They should not be regarded as conclusive, guide clinical practice/health-related behavior, or be reported in news media as established information.*"[³](https://www.biorxiv.org/collection/)

---
¹ bioRxiv is a so-called preprint server that lets researchers publish their work before it has been peer-reviewed (that is, evaluated by other scientists in the same field). While a lot of research articles that are posted on preprint servers eventually get published in academic journals, some of them do not make it past the peer-review and get rejected. So, be critical of everything you read, especially if it is a preprint.

² Pradhan et al., 2020: [https://www.biorxiv.org/content/10.1101/2020.01.30.927871v1.full](https://www.biorxiv.org/content/10.1101/2020.01.30.927871v1.full)

³ [https://www.biorxiv.org/collection/](https://www.biorxiv.org/collection/)

---

Today, you are going to reproduce some results of the Pradhan et al. preprint and then you can decide how trustworthy their claims are. First, let's explore the NCBI virus database:

<ol type="a">
  <li>Go to NCBI Virus at https://www.ncbi.nlm.nih.gov/labs/virus/vssi/#/. NCBI Virus is a database that contains nucleic acid (DNA & RNA) and protein sequences of all viruses that have been sequenced so far. It contains subsets of the GenBank and Protein databases, which contain sequences of all organisms that have been sequenced.</li>
  <li>Scroll down to the NCBI visual data dashboard. How many viral protein and nucleic acid sequences does NCBI virus currently contain? Which host is most common among the viruses in the database? Are you surprised by that? Why (not)?</li>
  <li>Note that you can click on a group of viruses in the taxonomy browser and the numbers on top of the dashboard will change. Which viruses make up the largest part of the databases - DNA, RNA, or unclassified? Do you have an idea which virus has the most sequences in NCBI virus?</li>
  <li>Click on the taxonomy browser, and select RNA viruses > Pararnavirae > Artverviricota > Revtraviricetes > Retroviridae > Orthoretrovirinae > Lentivirus. One of the Lentiviruses is the most sequenced virus in history. Can you find it? What % of nucleotide sequences in the database belong to this virus? How many % of protein sequences belong to this virus?</li>
  <li>Now, check the same numbers for the SARS-Cov-2. For that, you can just scroll up and click on the interactive SARS-Cov-2 dashboard. Do the numbers surprise you? Would you have expected more or fewer sequences in the database?</li>
</ol>

Now that you know something about what the virus database looks like, let's reproduce some of Pradhan et al.'s research. Pradhan et al. compared all the SARS-Cov-2 virus genomes that were available in January 2020 (53 genomes) to the virus that caused the SARS epidemic in 2002-2004. The most interesting differences that they found were four inserts (short stretches of amino acids that are in SARS-Cov-2 but not the original SARS virus) in the so-called spike protein.

f. Look at the preprint's Figure 2 below. What you can see here is a sequence alignment. It is used to compare sequences to each other and visualize the differences. Write down the sequences of the four inserts.

g. Go to NCBI BLAST https://blast.ncbi.nlm.nih.gov/Blast.cgi. Look at your sequences. We want to compare the four inserts to proteins from HIV. Which BLAST flavour should you use?

h. You can search for all four inserts at the same time by typing them in the query box using the FASTA format that gives each sequence a unique identifier after a “>” sign, followed by the sequence on the next lines like this (note the amino acid alphabet):

>insert1
ACDEFG
>insert2
HIKLMN
...

---


## Page 3

i. Then, we have to choose in which database we want to search for targets that match our queries. Select the right BLAST flavor under “Program Selection”. In their Methods section Pradhan et al. mention that they searched the virus database. In the section “Choose search set” under “Organism”, choose “Viruses (taxid: 10239)”. As you have seen, at this point, we have many sequences for SARS-Cov-2, a lot compared to the 53 that Pradhan et al. looked at. Therefore, we have to exclude “SARS-CoV-2 (taxid:2697049)” from our search; otherwise the search will result only in SARS-CoV-2 sequences. You can do that by clicking on the + next to the Organism field, choosing SARS-CoV-2, and then checking the “exclude” box. Check the box that lets you show results in a new window. Finally, click on the + next to Algorithm Parameters and set “Max target sequences” to 5000. We do this because we expect many related sequences in the database and we want to find not just the best, but also some of the more distant hits. Now start the search.

<table>
  <thead>
    <tr>
      <th></th>
      <th>1</th>
      <th>10</th>
      <th>20</th>
      <th>30</th>
      <th>40</th>
      <th>50</th>
      <th>60</th>
      <th>70</th>
      <th>80</th>
      <th>90</th>
      <th>100</th>
      <th>110</th>
      <th>120</th>
      <th>130</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2019-nCoV</td>
      <td colspan="14">MFVFLVLLPLYSSQCVNLTTRTQ--LPPAYTN--SFTRGVYYPDKVFRSSYLHSTQDLFLPFFSNYTHFHAIHYSGTNGTKRFONPVLPFNDGYYFASTEKSNIIRGHIFGTTLDSKTQSLLIVNNATNY</td>
    </tr>
    <tr>
      <td>SARS-GZ02</td>
      <td colspan="14">MFIFLLFLTLTSGSDLDRCTTFDDVQAPNYTQHTSSMRGVYYPDEIFRSDTLYLTQDLFLPFYSNVTGFHTINHT</td>
    </tr>
    <tr>
      <td>Consensus</td>
      <td colspan="14">MF!FL11LpLtSgqdl #rcTrf#..qaPaYT#..SfnRGVYYPDe!FRSdtLh1TQDLFLPF%SNVTgFHaInhs</td>
    </tr>
    <tr>
      <td></td>
      <td>131</td>
      <td>140</td>
      <td>150</td>
      <td>160</td>
      <td>170</td>
      <td>180</td>
      <td>190</td>
      <td>200</td>
      <td>210</td>
      <td>220</td>
      <td>230</td>
      <td>240</td>
      <td>250</td>
      <td>260</td>
    </tr>
    <tr>
      <td>2019-nCoV</td>
      <td colspan="14">VIKYCEFQFCNDPFLGWYYHKNNKSHMESEFRVYSSANNCTFEYYSQPFLMDLEGKQGNFKNLREFYFKNIDGYFKIYSKHTPINLYRDLPQGFSALEPLYDLPIGINITRFQTLLALHRSYLTPGDSSS</td>
    </tr>
    <tr>
      <td>SARS-GZ02</td>
      <td colspan="14">VIRACNFELCONPFFA---SKPMGTQTHTHIFONAFNCTFEYISDAFSLDYSEKSGNFKHLREFVFKNKDGFLYVYKGYQPIDVVRDLPSGFNTLKPIFKLPLGINITNFRAILT---AFLPAQDT--</td>
    </tr>
    <tr>
      <td>Consensus</td>
      <td colspan="14">IraC#F#1C##PFla....nnkngn#sefr!%dnAnNCTFEY!S#aF1$DleeKqGNFKnLREFYFKNiDG%1k!YkghqPI#1VRDLPqGFnalePifdLPIGINITrFraila...a%LpaqDs..</td>
    </tr>
    <tr>
      <td></td>
      <td>261</td>
      <td>270</td>
      <td>280</td>
      <td>290</td>
      <td>300</td>
      <td>310</td>
      <td>320</td>
      <td>330</td>
      <td>340</td>
      <td>350</td>
      <td>360</td>
      <td>370</td>
      <td>380</td>
      <td>390</td>
    </tr>
    <tr>
      <td>2019-nCoV</td>
      <td colspan="14">GTAGAAAYYVGYLQPRTFLLKYNENGTITDAVDCALDPLSETKCTLKSFTVEKGIYQTSNFRVQPTESIVRFPNITNLCPFGEVFNATRFASVYAHNRKRISNCVADYSVLYNSASFSTFKCYGVSPTK</td>
    </tr>
    <tr>
      <td>SARS-GZ02</td>
      <td colspan="14">HGTSAAYFVGYLKPTTFMLKYDENGTITDAVDCSQNPLAELKCSYKSFEIDKGIYQTSNFRVVPSRDVVRFPNITNLCPFGEVFNATKFPSVYAHERKRISNCVADYSVLYNSTFFSTFKCYGVSATK</td>
    </tr>
    <tr>
      <td>Consensus</td>
      <td colspan="14">gagAAAYXVGYLqPrTF$LKY#ENGTITDAVDCaq#PLaE1KCs1KSFe!#KGIYQTSNFRYqPsrd!VRFPNITNLCPFGEVFNATrFaSVYAH#RKRISNCYADYSVLYNSafFSTFKCYGVSaTK</td>
    </tr>
    <tr>
      <td></td>
      <td>391</td>
      <td>400</td>
      <td>410</td>
      <td>420</td>
      <td>430</td>
      <td>440</td>
      <td>450</td>
      <td>460</td>
      <td>470</td>
      <td>480</td>
      <td>490</td>
      <td>500</td>
      <td>510</td>
      <td>520</td>
    </tr>
    <tr>
      <td>2019-nCoV</td>
      <td colspan="14">LNDLCFTNYYADSFVIRGDEVRQIAPGQTGKIADYNYKLPDDFTGCVIAHNSNNLDSKYGGNYNYLYRLFRKSNLKPFERDISTEIYQAGSTPCNGVEGFNCYFPLQSYGFQPTNGVGYQPYRYYYLSFE</td>
    </tr>
    <tr>
      <td>SARS-GZ02</td>
      <td colspan="14">LNDLCFSNVYADSFVVKGDDYRQIAPGQTGVIADYNYKLPDDFMGCYLAHNTRNIDATSTGNYNYKYRYLRHGKLRPFERDISNYPFSPDGKPCTP-PALNCYHPLNDYGFYTTTGIGYQPYRVVVLSFE</td>
    </tr>
    <tr>
      <td>Consensus</td>
      <td colspan="14">LNDLCFSNVYADSFY!rGD#VRQIAPGQTGKIADYNYKLPDDFGCViAHNsrNiDaksgGNYNY1YR11RhgnLrPFERDISnei%qadgkPCng.ealNCYfPL#dYGFqpTnG!GYQPYRVVVLSFE</td>
    </tr>
    <tr>
      <td></td>
      <td>521</td>
      <td>530</td>
      <td>540</td>
      <td>550</td>
      <td>560</td>
      <td>570</td>
      <td>580</td>
      <td>590</td>
      <td>600</td>
      <td>610</td>
      <td>620</td>
      <td>630</td>
      <td>640</td>
      <td>650</td>
    </tr>
    <tr>
      <td>2019-nCoV</td>
      <td colspan="14">LLHAPATYCGPKKSTNLVKNKCVNFNFNGLTGTGVLTESNKKFLPFQQFGRDIADTTDAVRDPQTLEILDITPCSFGGVSVITPGTNTSNQVAVLYQDVNCTEVPVAIHADQLTPTHRVYSTGSNVFQTR</td>
    </tr>
    <tr>
      <td>SARS-GZ02</td>
      <td colspan="14">LLNAPATYCGPKLSTDLIKNQCVNFNFNGLTGTGVLTPSSKRFQPFQQFGRDVSDFTDSVRDPKTSEILDISPCSFGGVSVITPGTNASSEVAVLYQDVNCTDVSTAIHADQLTPAHRIYSTGNNVFQTQ</td>
    </tr>
    <tr>
      <td>Consensus</td>
      <td colspan="14">LLnAPATYCGPK1ST#L!KNqCYNFNFNGLTGTGYLTeSnKrFqPFQQFGRD!aDfTDaVRDPqTIEILDISPCSFGGYSVITPGTNaSn#YAVLYQDVNCT#VptAIHADQLTPaHR!YSTGnNYFQTr</td>
    </tr>
    <tr>
      <td></td>
      <td>651</td>
      <td>660</td>
      <td>670</td>
      <td>680</td>
      <td>690</td>
      <td>700</td>
      <td>710</td>
      <td>720</td>
      <td>730</td>
      <td>740</td>
      <td>750</td>
      <td>760</td>
      <td>770</td>
      <td>780</td>
    </tr>
    <tr>
      <td>2019-nCoV</td>
      <td colspan="14">AGCLIGAEHVNNSYECDIPIGAGICASYQTOTNSPRRARSVASQSIIAYTMSLGAENSVAYSNNSIAIPTNFTISVTTEILPVSMTKTSVDCTMYICGDSTECSNLLLQYGSFCTQLNRALTGIAVEQDK</td>
    </tr>
    <tr>
      <td>SARS-GZ02</td>
      <td colspan="14">AGCLIGAEHYDTSYECDIPIGAGICASYHTVS----LLRSTSQKSIVAYTMSLGADSSIAYSNNTIAIPTNFSISITTEVMPVSHAKTSVDCNMYICGDSTECANLLLQYGSFCTQLNRALSGIAAEQDR</td>
    </tr>
    <tr>
      <td>Consensus</td>
      <td colspan="14">AGCLIGAEHV#nSYECDIPIGAGICASYqqs....raStaqqSI!AYTMSLGA#nS!AYSNNSIAIPTNFSIS!TTE!$PVSMAKTSVDCnMYICGDSTECANLLLQYGSFCTQLNRALsGIAaEQDr</td>
    </tr>
    <tr>
      <td></td>
      <td>781</td>
      <td>790</td>
      <td>800</td>
      <td>810</td>
      <td>820</td>
      <td>830</td>
      <td>840</td>
      <td>850</td>
      <td>860</td>
      <td>870</td>
      <td>880</td>
      <td>890</td>
      <td>900</td>
      <td>910</td>
    </tr>
    <tr>
      <td>2019-nCoV</td>
      <td colspan="14">NTQEVFAQVKQIYKTPPIKDFGGFNFSQILPDPSKPSKRSFIEDLLFNKYTLADAGFIKQYGDCLGDIAARDLICAQKFNGLTYLPPLLTDEMIAQYTSALLAGTITSGHTFGAGAALQIPFAMQMAYRF</td>
    </tr>
    <tr>
      <td>SARS-GZ02</td>
      <td colspan="14">NTREVFAQVKQMYKTPTLKDFGGFNFSQILPDPLKPTKRSFIEDLLFNKYTLADAGFMKQYGECLGDINARDLICAQKFNGLTVLPPLLTOOMIAAYTAALYSGTATAGHTFGAGAALQIPFAMQMAYRF</td>
    </tr>
    <tr>
      <td>Consensus</td>
      <td colspan="14">NTrEVFAQVKQiYKTPpiKDFGGFNFSQILPDPIKPSKRSFIEDLLFNKYTLADAGFIKQYG#CLGDIaARDLICAQKFNGLTYLPPLLTD#MIAaYTAALlaGTaTaGHTFGAGAALQIPFAMQMAYRF</td>
    </tr>
    <tr>
      <td></td>
      <td>911</td>
      <td>920</td>
      <td>930</td>
      <td>940</td>
      <td>950</td>
      <td>960</td>
      <td>970</td>
      <td>980</td>
      <td>990</td>
      <td>1000</td>
      <td>1010</td>
      <td>1020</td>
      <td>1030</td>
      <td>1040</td>
    </tr>
    <tr>
      <td>2019-nCoV</td>
      <td colspan="14">NGIGVTQNVLYENQKLIANQFNSAIGKIQDSLSSTASALGKLQDVVNQNAQALNTLVKQLSSNFGAISSVLNDILSRLDKVEAEVQIDRLITGRLQSLQTYVTQQLIRAAEIRASANLAATKHSECVLGQ</td>
    </tr>
    <tr>
      <td>SARS-GZ02</td>
      <td colspan="14">NGIGVTQNVLYENQKQIANQFNKAISQIQESLTTTSTALGKLQDVVNQNAQALNTLVKQLSSNFGAISSVLNDILSRLDKVEAEVQIDRLITGRLQSLQTYVTQQLIRAAEIRASANLAATKMSECVLGQ</td>
    </tr>
    <tr>
      <td>Consensus</td>
      <td colspan="14">NGIGYTONYLYENQKQIANQFNKAIgqIQ#SLssTasALGKLQDVVNQNAQALNTLYKQLSSNFGAISSYLNDILSRLDKVEAEVYQIDRLITGRLQSLQTYYTQQLIRAAEIRASANLAATKMSECVLGQ</td>
    </tr>
    <tr>
      <td></td>
      <td>1041</td>
      <td>1050</td>
      <td>1060</td>
      <td>1070</td>
      <td>1080</td>
      <td>1090</td>
      <td>1100</td>
      <td>1110</td>
      <td>1120</td>
      <td>1130</td>
      <td>1140</td>
      <td>1150</td>
      <td>1160</td>
      <td>1170</td>
    </tr>
    <tr>
      <td>2019-nCoV</td>
      <td colspan="14">SKRVDFCGKGYHLMSFPQSAPHGVVFLHYTYYPAQEKNFTTAPAICHDGKAHFPREGYFVSNGTHHFVTQRNFYEPQIITTONTFVSGNCDVVIGIVNNTVYDPLQPELDSFKEELDKYFKNHTSPDVDL</td>
    </tr>
    <tr>
      <td>SARS-GZ02</td>
      <td colspan="14">SKRVDFCGKGYHLMSFPQAAPHGVVFLHVTYVPSQERNFTTAPAICHEGKAYFPREGVFVFNGTSHFITQRNFFSPQIITTONTFVSGNCDVVIGIINNTVYDPLQPELDSFKEELDKYFKNHTSPDVDL</td>
    </tr>
    <tr>
      <td>Consensus</td>
      <td colspan="14">SKRVDFCGKGYHLMSFPQaAPHGVVFLHVTYVPaQErNFTTAPAICH#GKAHFPREGVFVFNGTHHF!TORNF%ePQIITTONTFVSGNCDVVIGI!NNTVYDPLQPELDSFKEELDKYFKNHTSPDVDL</td>
    </tr>
    <tr>
      <td></td>
      <td>1171</td>
      <td>1180</td>
      <td>1190</td>
      <td>1200</td>
      <td>1210</td>
      <td>1220</td>
      <td>1230</td>
      <td>1240</td>
      <td>1250</td>
      <td>1260</td>
      <td>1270</td>
      <td>1277</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td>2019-nCoV</td>
      <td colspan="14">GDISGINASVVNIQKEIDRLNEVAKNLNESLIDLQELGKYEQYIKHPHYIHLGFIAGLIAIVMVTIMLCCHTSCCSCLKGCCSCGSCCKFDEDDSEPVLKGVKLHYT</td>
    </tr>
    <tr>
      <td>SARS-GZ02</td>
      <td colspan="14">GDISGINASVVNIQEEIDRLNEVAKNLNESLIDLQELGKYEQYIKHPHYVHLGFIAGLIAIVMVTILLCCHTSCCSCLKGACSCGSCCKFDEDDSEPYLKGVKLHYT</td>
    </tr>
    <tr>
      <td>Consensus</td>
      <td colspan="14">GDISGINASVVNIQeEIDRLNEVAKNLNESLIDLQELGKYEQYIKHPHY!HLGFIAGLIAIVMVTISLCCMTSCCSCLKGaCSCGSCCKFDEDDSEPVLKGVKLHYT</td>
    </tr>
  </tbody>
</table>

Pradhan et al. Figure 2. Sequence alignment between 2019-nCoV (top row, SARS-CoV-2’s preliminary name in January 2020), the SARS virus that caused the 2002-2004 SARS epidemic (middle row), and their consensus sequence (bottom row). A consensus sequence is normally defined by the most common nucleotide(s) or amino acid residue(s) at each position in a multiple sequence alignment.

j. After a couple of minutes, you will get the results. You can switch between the four inserts by selecting them from the dropdown menu at “Results for”. You can filter your

---


## Page 4

results by organism. Choose HIV-1 (taxid: 11676) and look at the top hit. For each of the inserts write down: 1) the description of the hit, 2) the query coverage, 3) Percent Identity, and 4) the E-value. You can see the sequence alignment for each hit when you click on the description. Based on the numbers that you wrote down, do you think that these are good hits? Why (not)?

k. Repeat the search for insert 3, but this time, choose HIV-1 as the organism in the search set. Check the E-value. Is the E-value the same as before? Do you have any idea why (or why not)? What do you think is the difference between putting HIV-1 in the organism field before you start the search, and filtering your results by HIV-1?

l. Remember the information about interpreting BLAST hits, particularly about the E-value. Look back at the % of sequences in the Virus database that belong to HIV-1. Do you agree with Pradhan et al. when they say that the similarities shared between the four inserts and HIV-1 “suggests that this is not a random fortuitous finding”?

Here you have seen that you are able to replicate parts of the research done by Pradhan et al. and generating an informed opinion about your results, after a brief introduction to bioinformatics and BLAST. You have explored the NCBI virus database and learned that the database is heavily biased, because human viruses are predominantly used for research. You have seen that one human virus alone accounts for about 1 in 6 known protein sequences from viruses. You have also seen that accountability is an important theme when it comes to (bioinformatic) research. Considering the massive amount of sequence data that is uploaded to the databases every day, coincidental similarities between sequences are inevitable. To decide how meaningful our results are, we need statistics. Robust statistics prevent us from jumping to conclusions that could not just be wrong, but also lead to potentially dangerous conclusions, like in the preprint by Pradhan et al.
