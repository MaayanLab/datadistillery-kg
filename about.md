## Data Distillery Knowledge Graph

![DD](https://minio.dev.maayanlab.cloud/datadistillery-kg/Dictionary/images/image41.png)

Maturation of data sharing projects between DCCs and CFDE data representation standards has produced an opportunity for integration at the data assertion level. This project employs use cases that drive the following three focused activities:

* data preparation from CF DCCs for use in a knowledge graph;   
* modeling, ingestion,  and testing of this data in the knowledge graph; and    
* developing algorithms to use this data to extract suggestions about CF data related to user queries.   
    
The assertions are derived from primary or secondary data at each DCC. Primary data asserts a particular experimental value associated with a dataset feature. For example, primary data represents gene expression values in cell types from HuBMAP, or within each tissue from GTEx, metabolite levels from Metabolomics Workbench associated with a specific disease or tissue, differentially expressed genes after drug perturbations from LINCS, or a phenotype related to a certain cohort from Kids First, or mutations or SNPs that lead to loss or gain of glycosylation sites from GlyGen, or attributes about small molecules from IDG. Secondary data includes p-values of cis-eQTLs in GTEx, or tissue-specific gene expression correlation measures, both which show the relationships between RNA expression of genes. Secondary data also includes TIGA GWAS p-values and effect sizes from IDG as well as TIN-X assertions about the druggable genome. Participating DCCs extracted and summarized primary data as assertions to support our specific use cases,  and if possible, provide useful secondary data for the use cases. Each DCC produced a list of assertions to contribute to the project as milestones. All DCCs are responsible for creating their own assertion sets. The project created a knowledge graph database using Neo4j to contain and link data assertions extracted from DCC data. The schema of this knowledge graph database has been previously developed. DCCs participate in the selection and design of important relationships between assertion types. Thus, the final design is implicitly defined with biological relevance and structure that allows for functional queries on biological questions. Methods and algorithms are designed to execute use cases, operant on the knowledge graph database. Participating DCCs contribute to algorithm design. Such algorithms are implemented as knowledge graph Cypher queries that produce textual (JSON), tables, or visual query results (network diagrams, bar charts, heatmaps).