# Metagenomic-analysis-pipeline 

## Reads Download/QC/Trimming

### SRAtool
從NCBI下載reads

**Install**  
請先在Linux 上安裝conda並安裝bioconda  
```
$ conda install -c bioconda sra-tools
```  

**Usage**  
```
conda activate

#下載序列
(base)$ prefetch {SRR的號碼}  

#從下載的sra檔案中提取fastq檔，特別注意新版的指令是 (base)$fasterq-dump
(base)$ fastq-dump {SRR的號碼} 
``` 
fastq檔會出現在sra的資料夾中

### FastQC
檢查序列質量

**Install**  
請先在Linux 上安裝conda並安裝bioconda  
```
$conda install -c bioconda fastqc
```  

**Usage**  
```
conda activate
(base)$ fastqc
```

### fastp
修剪序列，將低質量序列去除  
https://github.com/OpenGene/fastp#install-with-bioconda

**Install**  
請先在Linux 上安裝conda並安裝bioconda  
```
# note: the fastp version in bioconda may be not the latest
conda install -c bioconda fastp
```  

**Usage**  
```
conda activate
(base)$ fastp -i {你的序列1.fq} -I {你的序列2.fq} -o {你的修剪完的序列1.fq} -O{你的修剪完的序列2.fq}
```
基本參數設定

