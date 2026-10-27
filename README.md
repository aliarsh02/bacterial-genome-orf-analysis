# Python analysis of bacterial genome: Staphylococcus Condimenti

INTRODUCTION

Advancements in genome sequencing and bioinformatics have allowed researchers to
identify regions of similarity between specific gene or biological sequences across species.
One of these tools includes NCBI BLAST (Basic Local Alignment Search Tool), allowing users
to compare protein and nucleotide sequences against sequence databases to identify
similarities; therefore, this may suggest potential functions for proteins predicted from the
genome through BLAST. Therefore, the goal of this project was to examine the genome of
Staphylococcus Condimenti and identify potential open reading frames (ORF) on both strands
to find protein coding regions, translate those prospective DNA sequences into proteins,
calculate the molecular mass of proteins, and extract/find similar proteins using BLAST. Five
proteins were selected and compared with BLAST sequences in NCBI’s protein database.

METHODS

The complete genome assembly Staphylococcus condimenti was found using UCSC Genome
Browser (datafile ID: GCF_900637235.1) downloaded as FASTA file. The file contained one
chromosome sequence (chromosome sequence ID: NZ_LR134360.1) which had 2,650,496
nucleotides. To write a script, the analysis was completed in Jupyter Notebook using Python.
The packages that were used included pandas for data analysis and cleaning, as well as
Biopython packages (Bio) to process sequences, DNA translation, molecular mass
calculations, and BLAST (NCBIWWW and NCBIXML) and pandas. Overall, the data
sources/databases used in this project include the UCSC Genome Browser and NCBI BLAST
protein database, which was used to find similar protein sequence. Final BLAST results were
saved as XML files for each of the five proteins.
In the first phase of the code, the DNA sequence was converted to uppercase and the reverse
complement of the sequence was generated. The code below searches for possible protein-
coding regions within the genome by checking/scanning three reading frames for each forward
and reverse-complement strand (i.e scanning all six reading frames of a DNA sequence for start
and stop codons). Each start codon has an in-frame stop codon and the coding length is
calculated by counting the number of codons from the start codon up to its first in-frame stop
codon (but excluding the stop given it signals the end of translation). If candidates had longer
than 50 coding codons, they were saved as dictionaries containing the sequence ID, strand,
frame, position, length, DNA sequence, etc. The dataframe was shown as a table with all the
respective information described previously. DNA positions are zero-based (the first base is
position zero) with an exclusive end, measured along either the forward or reverse-
complement strand.

The candidate ORFs were translated to protein sequences using .translate (used cds=TRUE
which translates alternative start codons as methionine and the terminal stop is removed). The
molecular mass for each protein was calculated in daltons (Da) and were divided 1000 to find
the mass in kilodaltons (kDa). The dataframe was shown as a table with all the respective
information described previously, now including the molecular mass of each protein. Five
candidate proteins were chosen between 200-599 aa and chose to avoid proteins that share
the same start, stop , strand, and frame position. Using NCBI protein BLAST (blastp), these
proteins were searched against NCBI nr database (nonredundant protein) with low-complexity
filtering to avoid redundant segments. The results for each protein (5 protein sequences) were
saved as XML files with the number of matched protein sequences, alignment score, query
protein sequence, BLAST-NCBI aligned protein sequence, and the top protein/protein
information.

RESULTS AND CONCLUSION:

The number of potential ORFs that were longer than 50 coding codons were 121,496 across
both DNA strands (this includes candidates with varying start positions). The protein
sequence length and molecular masses of candidates that had lengths between 200-599 aa
were: 453 (52.181 kDa), 435 (49.517 kDa), 595 (67.2719 kDa), 471 (52.963 kDa), and 599
(68.396 kDa).

Protein BLAST returned 50 databased for each of the five selected proteins with reported E-
values of 0.0 for each one, indicating a strong similarity between the sequences. The top
alignments were noted as chromosomal replication initiator protein DnaA, serine-tRNA
ligase, DGG family phosphoesterase, replicative DNA helicase, and cell wall metabolism
sensor histidine kinase WalK. These candidates may be DNA regions within the
Staphylococcus condimenti that encode a protein involved in (in order): DNA replication, in
attaching serine to its tRNA for protein synthesis, breaking phosphate-containing bonds,
unwinding DNA double helix, protein kinase (WalK) involved in cell wall metabolism.
Therefore, these are candidates may showcase possible protein-coding regions with
specific biological functions due to regions of similarity by comparing the genome of our
bacterial genome (Staphylococcus Condimenti) with known sequences on BLAST.
