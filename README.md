# Individual Project 6CCS3PRJ 2022
# Author: Xiangyue Wei
# Student Number: 20041328
# Supervisor: Dr. Albert Merono Peuela
# Project Title: 
  Knowledge Graph generation from two Irish Tune Datasets with SPARQL Anything
# GitHub Repository Link: 
  https://github.com/LucyWei88/PRJ2022

# Output:
78,800 Knowledge graphs generated from the CRE and The Session datasets.
The knowledge graphs contain the general information and music code from each tune.
Please notice, as the outputs of this project are too large to submit,
please use the following links to get the generated knowledge graphs:

  GitHub:
     https://github.com/LucyWei88/PRJ2022/tree/main/Knowledge_Graph
  Zenodo(zip):
     https://zenodo.org/record/7792131#.ZCoouHbMK5c

# Links to datasets, including necessary and unnecessary:
(Unnecessary) Original ABC datasets:
The CRE dataset:
    https://github.com/polifonia-project/folk_ngram_analysis/tree/master/cre_corpus/abc
The Session dataset:
    https://github.com/polifonia-project/folk_ngram_analysis/tree/master/thesession_corpus/abc

(Unnecessary) Altered ABC datasets:
    https://github.com/LucyWei88/PRJ2022/tree/main/Altered_ABC

(Unnecessary) Original MusicXML files:
GitHub:
    https://github.com/LucyWei88/PRJ2022/tree/main/All_XML_Original
Zenodo(zip):
    https://zenodo.org/record/7792129#.ZConhHbMK5c

(Necessary) Cleaned MusicXML files, choose one of the followings:
GitHub:
    https://github.com/LucyWei88/PRJ2022/tree/main/All_XML
Zenodo(zip):
    https://zenodo.org/record/7792125#.ZCooF3bMK5c

#Requirements
1. requires Java >= 11 to be installed on the operating system
2. SPARQL Anything Command-line Interface version 0.8.1
   Download link:
   https://github.com/SPARQL-Anything/sparql.anything/releases/tag/v0.8.1

# Replication Guide
To replicate, there is a full replication guide in Appendix and Additional Material PDF submission.
My GitHub repository also has this guide separately:
    https://github.com/LucyWei88/PRJ2022/blob/main/Replication_Guide.pdf
We will not discuss how to prepare the directory here.
Here are the commands also included in the replication guide:
1. Getting the lists of MusicXML files paths and names:
      java -jar sparql-anything-0.8.1.jar -q queries/get_CRE_XML_Paths.sparql -o CRE_file_Paths.xml -f XML

      java -jar sparql-anything-0.8.1.jar -q queries/Get_The_Session_XML_Paths.sparql -o The_Session_file_Paths.xml -f XML
2. Generating the knowledge graphs contain the general information of each tune:
      java -jar sparql-anything-0.8.1.jar -q queries/CRE_Tune_Information.sparql --values CRE_file_Paths.xml -p "Knowledge_Graph/CRE_Tune_Information/?fileName.ttl" -f TTL

      java -jar sparql-anything-0.8.1.jar -q queries/The_Session_Tune_Information.sparql --values The_Session_file_Paths.xml -p "Knowledge_Graph/The_Session_Tune_Information/?fileName.ttl" -f TTL
3. Generating the knowledge graphs contain the muisc codes of each tune:
      java -jar sparql-anything-0.8.1.jar -q queries/CRE_Music_Notes.sparql --values CRE_file_Paths.xml -p "Knowledge_Graph/CRE_Music_Notes/?fileName.ttl" -f TTL

      java -jar sparql-anything-0.8.1.jar -q queries/The_Session_Music_Notes.sparql --values The_Session_file_Paths.xml -p "Knowledge_Graph/The_Session_Music_Notes/?fileName.ttl" -f TTL
