Omnenomnom in Conjuction with DantesDoesThings

Class: 440 Washington Univeristy in St. Louis

Citation names: Erica Marquez and Michael Baramidze

This code reads and searches for target segments within a FASTA gene and/or Protien sequence by single gene or by a stored target gene libary. 

A breif explaination by section:

1. Imports: OS and re are the only required imports for this. 
The search function is based off of re. Os is for file finding as I over organize. 
If file is saved as txt within local file OS is not needed.

2. Finds file
Replace with your file and location.
Note: For windows, default filepath has forward slash. Change to back slashes.

3. Parent class
Base function on all data ran through.
Identifies files. 
If source unknown; run print_is_human

4. F1 Child classes
Read: opens and reads file; firstline skip is for use of DNA/RNA identification later
Write: Saves results in new file

5. F2 Child classes
Seqdata: identifies
source_find: locates if DNA or protien by looking for a target "r" that cannnot exisit within a DNA sequence.
	Can be altered to any other letter if "null" letter for DNA sequence is "r"
	Logic is if/else 
search: Looks for specfic site/sequence

6. F3 classes
DNA: searches specifically for DNA 
	Searches for libarary (EDIT SLECTED GENES HERE)
Protien: searches specifically for Protien 
	Searches for libarary (EDIT SLECTED GENES HERE)

Input Commands: ("FN"= "File Name")

print_is_human("FN")
source_find("FN")
SeqData("FN")
FASTAOutput("Results FN")
Match (Target Sequence)
