# Tutorial 4 – part 1
Sequence similarity searching with BLAST
MBLS207 - Bioinformatics

1. Which type of mutation should cause the minimal change in a BLAST score for a nucleotide alignment?
    - a. 3-nucleotide insertion
    - b. 1-nucleotide substitution
    - c. 4-nucleotide insertion
    - d. 1-nucleotide deletion
    - e. 3-nucleotide deletion

2. Which type of mutation should cause the minimal change in a BLAST score for a protein alignment?
    - a. 3-nucleotide insertion
    - b. 4-nucleotide substitution
    - c. 2-nucleotide insertion
    - d. 1-nucleotide deletion
    - e. 3-nucleotide deletion

3. A researcher wants to determine the genetic relatedness of several breeds of dog (Canis familiaris). The researcher should compare homologous sequences of ________ that are known to be ________. Which words can be placed in the gaps? Explain.
    - a. carbohydrates; poorly conserved
    - b. DNA; highly conserved
    - c. fatty acids; poorly conserved
    - d. proteins or nucleic acids; poorly conserved
    - e. amino acids; highly conserved

4. Assume all nucleotides occur independently of each other with the same frequency in DNA sequences.
    - a. What is the probability of finding the nucleotide sequence 5'-GGATATCCGC-3' by chance in a random DNA molecule?
    - b. How often do you expect to find this same sequence in a given 10 kb DNA molecule?
    - c. Imagine we have a genome with a total size of 4 × 10⁹ base pairs. What is the probability of finding a specific 20-nucleotide sequence in this genome?
    - d. What about a specific 3-nucleotide sequence, or a specific 16-nucleotide sequence?

5. We do a BLAST search to predict the function of a human query protein on two different websites that provide a BLAST search tool. The alignments of best hits are as follows.

```
>gb|AAC60279.1| ubiquitin/ribosomal protein [Gallus gallus]
Length=156
  Score = 47.8 bits (112), E-value = 1e-04
  Identities = 47/95 (49%), Positives = 50/95 (52%), Gaps = 36/95 (37%)
Query  1   IRKETTLHKVLRLWGGAYKDXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXKKKSY  60
           I+KE+TLH VLRL GGA K                                    KKKSY
Sbjct  61  IQKESTLHLVLRLRGGAKK-----------------------------------RKKKSY  85
Query  61  TMPXXXXXXXXXX-AVLPYYKIDEYGKISRFRRE  94
           T P           AVL YYK+DE GKISR RRE
Sbjct  86  TTPKKNKHKRKKVKLAVLKYYKVDENGKISRLRRE  120
```

```
>sp|P42568|AF9_HUMAN Protein AF-9 (Myeloid/lymphoid or mixed-lineage leukemia associated)
Length=568
  Score = 68.9 bits (167), E-value = 5e-11
  Identities = 40/52 (76%), Positives = 44/52 (84%), Gaps = 0/52 (0%)
Query   21  SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSKKKSYTMPKKNKHKHKK  72
            SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS   S++ P K   +HK+
Sbjct  154  SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSTSFSKPHKLMKEHKE 205
```


   - a. Which hit is statistically more significant? Explain.
   - b. What is the reason for the difference between the two BLAST results? Which of the two hits do you think is most likely to be a true homolog? Explain.

6. You have a query sequence that is 40 amino acids long. We BLAST this sequence against a small protein database with 29,318 sequences, and having a total length of 6,548,585 amino acids. You observe the following alignment of the best hit with an alignment score of 26.

```
Query 27 NFSSSQ 32
Sbjct 73 NFSTSQ 78
```

 - a. How many hits do you expect to find by chance with this alignment score? Use the following parameter values: *L* = 0.04 and λ = 0.27.
 - b. Is this hit significant/non-significant?

7. Imagine you discovered a novel fungus and sequenced its genome. You use a gene prediction program to identify 6,500 protein-coding genes and translate them into protein. Using these protein sequences, you perform a blastp search against known fungal genomes.
   - a. Of the 6,500 proteins, 5,500 have a match in other species of fungi (*Saccharomyces cerevisiae*, *Schizosaccharomyces pombe*, or *Neurospora crassa*) with a very low E-value. What can you say about these proteins?
   - b. The remaining 1,000 proteins each have a best match with an E-value larger than 10. What can you say about these proteins?
   - c. Of these last 1,000 proteins, can you make another BLAST search to verify your conclusion? What else can you try?

8. A bioinformatician wants to know what genetic functions are encoded on the DNA in a drop of rainwater. She isolates the metagenomic DNA from the rainwater and sends it to a company to be sequenced. Meanwhile, she writes a homology search program so that she can compare the sequences to an annotated database as soon as they come in. Her program builds an index of all the k-mers in the database sequences, and after she gets the data back from the company, the program searches this index for the k-mers in the sequences from the raindrop. For each query DNA sequence in the raindrop, she defines homologous hits as all the database sequences with a k-mer that matches the query.
   - a. She runs her algorithm with k=99. Would you expect many hits? Why (not)?
   - b. Does her algorithm identify local or global homology?
   - c. Sketch a graph illustrating how the probability of finding at least one hit depends on the length of k if all the database sequences are random.
   - d. From a biological perspective, explain what it means if the length of k is too high.
   - e. She compares the speed of her program with another way of identifying local sequence homology in a database: BLAST. Explain which of the two approaches is faster and why.
   - f. She compares the sensitivity of her program for detecting distant homologs with blastn and tblastx. Explain which of these three approaches is the most sensitive and which is the least sensitive.

9. We have a short protein segment from chicken:
```
FGGHNAITYPPGVSLAVGHFFSEWAEKFGDPLYRSSSSSSSSSSSSSSSTENKLAFGTHRDRDVGHFFCKAGAAEKF
```

We do a BLAST search to predict its function. Top 10 hits are as follows.

```
                                                                 Score    E
Sequences producing significant alignments:                     (Bits)  Value
gi|76638832|ref|XP_60 similar to SRp25 nuclease [Bos taurus]      40.8  0.017
gi|6649242|gb|AAF21439.1| splicing coactivator subunit SRm300 ... 40.0  0.028
gi|66828915|ref|XP_647811.1| hypothetical protein DDB0206273 ...  40.0  0.028
gi|66358726|ref|XP_626541.1| hypothetical protein cgd2_3540 ....  39.7  0.037
gi|66910579|gb|AAH97374.1| ADP-ribosylation factor-like 6 int...  39.7  0.037
gi|66816197|ref|XP_642108.1| hypothetical protein DDB0204407 ...  39.7  0.037
gi|71121770|gb|AAH99769.1| Arl6ip4 protein [Rattus norvegicus]    39.7  0.037
gi|50549999|ref|XP_502472.1| hypothetical protein ..............  39.3  0.048
gi|18676544|dbj|BAB84924.1| FLJ00169 protein [Homo sapiens]       39.3  0.048
gi|109472504|ref|XP_001059| similar to enolase [Gallus gallus]    39.3  0.048
gi|50365567|gb|AAT76079.1| GP60 [Cryptosporidium hominis]         38.9  0.063
```
  - a. Can you predict the function of this protein based on this output?
  - b. What could you do to improve this search?

[Go to part 2](02-Part.md)
