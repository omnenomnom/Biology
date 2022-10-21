#useful lessons: inheritance, fileIO, expressions


##Goals
#classes main and for dna and protein
#find sequences
#print matches into final text doc with locations

#Imports
import os
import re

#Find file
os.chdir("C:/Users/omnen/Documents/Class/440")

# Parent class (Base function)
class FASTAIO:
    def __init__(self, filename):
        self.filename = filename
        self.contents = None
        self.header = None

    def is_human(self):
        return 'Homo sapiens' in self.header

    def print_is_human(self):
        if self.is_human():
            print('This sample is human')
        else:
            print('This sample is not human')

# F1 Child Class (read)
class FASTAInput(FASTAIO):
    def __init__(self, filename):
        super().__init__(filename)
        self.readfile()

    def readfile(self):
        with open(self.filename, 'r') as file:
            self.header = file.readline()   #first line for later is_human function
            self.contents = file.read()     #skip first line for later source_find function

#F1 Child class (write results into new file)
class FASTAOutput(FASTAIO):
    def __init__(self, filename):
        super().__init__(filename)

    def writefile(self):
        with open(self.filename, 'w') as file:
            file.write(self.contents)

#F2 child class
class SeqData(FASTAInput):
    def __init__(self, filename):
        super().__init__(filename)

#Finds source (DNA vs. Protein) if unknown by checking second line down
    def source_find(self):
        # check if string present or not
        if 'R' in self.contents:  # text ment to represent anything not 'A''T''G''C'
            print('This sample is a protein')
        else:
            print('this is DNA sequence')  # DNA only has A, C, T, or G

#allows search for match if sample unknown
    def search(self, match):
        site = re.search(match, self.contents)
        if site is None:
            print("Could not find site")
        else:
            return site

#F3 Child class for DNA samples specifically (Only works on DNA Sequence)
class DNA(SeqData):
    def __init__(self, filename):
        super().__init__(filename)
        self.search_terms = ['AGTACT', 'AGCGCC','AGCGCT','GGCGCC', 'GGCGCT', 'AACGGCACGGG'] #Housekeeping Gene Libary Update to target genes of interest
        self.search_results = {}

    # allows search for specific sequence
    def search(self, match):
        site = re.search(match, self.contents)
        if site is None:
            reverse = re.search(match, self.contents[::-1])
            if reverse is None:
                print("No site found")
            else:
                return site
        else:
            return site

#Search for housekeeping libary 
    def search_all(self):
        for search_term in self.search_terms:
            self.search_results[search_term] = str(self.search(search_term))


#F3 Child class for Protein samples specifically (Only works on protein)
class Protein(SeqData):
    def __init__(self, filename):
        super().__init__(filename)
        self.search_terms = ["TSEEESQ", "EIAMLRLEL", "EESTRL", "QPSEETRLE" ]   #Housekeeping Gene library: Fill as desired
        self.search_results = {}

    def search(self, match):
        site = re.search(match , self.contents)
        if site is None:
            print("Could not find site")
        else:
            return site


    def search_all(self):
        for search_term in self.search_terms:
            self.search_results[search_term] = str(self.search(search_term))


#Assign text file to run> Assign write file name > Assign specific match to search for
input1 = DNA('NMM1 MAFA.txt')
output1= FASTAOutput("NMM1 MAFA_results.txt")
match = 'AACGGCACGGG'

input1.search(match)
input1.search_all()
print(input1.contents)
input1.print_is_human()
print(input1.search_results)
output1.contents = str(input1.filename +  "\nMatch sites found:")+ str(input1.search_results)
output1.writefile()


#