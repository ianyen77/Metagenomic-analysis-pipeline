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
(base)$ fastp -i {你的序列1.fq} -I {你的序列2.fq} -o {修剪完的序列1.fq} -O{修剪完的序列2.fq}
```
基本參數設定

## Taxanomic Profile
### Kraken
short reads taxanomic assigment(k-mer algorithm)  
**Install**  
```
$ conda install kraken2
#檢查版本
kraken2 –version
#安裝更新
$ conda update kraken2 -c bioconda
#安裝資料庫
#先設置存放位置(設定環境變數)
$DBNAME={~/db/kraken2/database(你要把資料庫建在哪裡)}
$mkdir -p DBNAME
#測試設定之環境變數是否成功
$cd $DBNAME
# 下載物種註釋資料庫
kraken2-build --download-taxonomy --threads{你要使用之線程數} --db $DBNAME
```
**Usage**  

## Assembly
### Megahit
組裝reads  
https://github.com/voutcn/megahit  
**Install**  
```
conda install -c bioconda megahit
```   
**Usage**  
```
conda activate
(base)$ megahit -1 {乾淨的pe序列1.fq} -2 {乾淨的pe序列2.fq} -o {輸出的檔名} 
```   
＃有些參數需要在寫  

### Quast
評估你組裝contigs的質量  
https://github.com/ablab/quast  

**Install**  
從他們的官網下載http://quast.sourceforge.net/ 並在你想要的資料夾中解壓縮  
```
tar -xf {下載檔案}
```

**Usage**  
```
cd {安裝的資料夾}

＃因為他要在python的環境下運行 我們的python裝在conda的環境中 所以要把conda打開
conda activate
(base)/{安裝的資料夾}$ ./quast.py {所要評估contigs的所在位置} -o {輸出資料位置}
```


### Prodigal
prokaryotic open reading fram prediction  
**Install**    
```
conda install -c bioconda prodigal
```  
**Usage**    
