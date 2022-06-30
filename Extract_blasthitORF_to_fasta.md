#需先準備好 1.contig預測的ORF(核酸序列) 2.Diamond比對特定資料庫的output文件(BLAST tabular format)   

1.create a ID_list.txt (can use excel) 
```
#format
k141_111843_1
k141_186432_4
k141_167714_1
k141_149241_1
.....
.....
.....
```   
2.利用seqkit從所有的ORF中抽出比對到的ORF
```
conda install -c bioconda seqkit
conda activate
(base)$ seqkit grep -f {ID_list.txt} {contig預測的ORF.fa(nucleic acid)} -o{outputfile.fa}
```

