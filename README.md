# Metagenomic-analysis-pipeline 
分析metagenomic的pipeline
## Reads download & Reads QC/Trimming

### SRAtool
從NCBI下載reads

**Install**  
請先在Linux 上安裝conda並安裝bioconda  
```~$ conda install -c bioconda sra-tools```  

**Usage**  
```
conda activate

#下載序列
(base)$ prefetch {srr的號碼}  

#從下載的sra檔案中提取fastq檔，特別注意新版的指令是 (base)$fasterq-dump
(base)$ fastq-dump {srr的號碼} 
``` 
fastq檔會出現在sra的資料夾中

### FastQC
檢查序列質量
