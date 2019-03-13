# 基因组测序、组装与分析总结

## 1. 测序前的准备

搜集物种相关信息，比如基因组大小，杂合度，

### 1.1 获取基因组大小

基因组大小的获取关系到对以后组装结果的大小的正确与否判断；基因组太大（>10Gb），超出了目前denovo组装基因组软件的对机器内存的要求，从客观条件上讲是无法实现组装的。

一般物种的基因组大小可以从（http://www.genomesize.com/ ）这个数据库查到。如果没有搜录，需要考虑通过实验（流式细胞仪）获得基因组大小。

**1.1.1 流式细胞仪估计基因组大小的例子：**

Yoshida, S., J. K. Ishida, et al. (2010). "A full-length enriched cDNA library and expressed sequence tag analysis of the parasitic weed, Striga hermonthica." BMC Plant Biol 10: 55.

**1.1.2 基于福尔根染色估计基因组大小的描述：**

这本书比较经典，重点推荐：Gregory, T. (2005). The evolution of the genome, Academic Press.

**1.1.3 定量pcr估计基因组大小的例子：**

Wilhelm, J., A. Pingoud, et al. (2003). "Real-time PCR-based method for the estimation of genome sizes." Nucleic Acids Res 31(10): e56.

Jeyaprakash, A. and M. A. Hoy (2009). "The nuclear genome of the phytoseiid Metaseiulus occidentalis (Acari: Phytoseiidae) is among the smallest known in arthropods." Exp Appl Acarol 47(4): 263-273.

**1.1.4 Kmer估计基因组大小的例子：**

Kim, E. B., X. Fang, et al. (2011). "Genome sequencing reveals insights into physiology and longevity of the naked mole rat." Nature 479(7372): 223-227.

### 1.2 杂合度估计

杂合度对基因组组装的影响主要体现在不能合并姊妹染色体，杂合度高的区域，会把两条姊妹染色单体都组装出来，从而造成组装的基因组偏大于实际的基因组大小。

一般是通过SSR在测序亲本的子代中检查SSR的多态性。杂合度如果高于0.5%，则认为组装有一定难度。杂合度高于1%则很难组装出来。

杂和度估计一般通过kmer分析来做，这里有一个例子：

http://www.nature.com/nature/journal/vaop/ncurrent/full/nature11413.html

降低杂合度可以通过很多代近交来实现。

杂合度高，并不是说组装不出来，而是说，装出来的序列不适用于后续的生物学分析。比如拷贝数、基因完整结构。

### 1.3 是否有遗传图谱可用

随着测序对质量要求越来越高和相关技术的逐渐成熟，遗传图谱也快成了denovo基因组的必须组成。构建遗传图构建相关概念可以参考这本书（The handbook of plant genome mapping: genetic and physical mapping ）

### 1.4 生物学问题的调研

这一步也是很重要的

## 2. 测序样品准备

确定第一步没问题，就意味着这个物种是可以尝试测序的。测序样品对一些物种也是很大问题的，某些物种取样本身就是一个挑战的问题。

基因组测序用的样品最好是来自于同一个个体，这样可以降低个体间的杂和对组装的影响。大片段对此无要求。

## 3. 测序策略的选择

一般都是用不同梯度的插入片段来测序，小片段（200,500,800）和大片段（1k, 2kb 5kb 10kb 20kb 40kb）。如果是杂合度高和重复序列较多的物种，可能要采取fosmid-by-fosmid或者fosmid pooling的策略。

不言而喻，后者花费是相当高的。

## 4. 基因组组装

### 4.1 组装相关综述：

Li, Z., Y. Chen, et al. (2012). "Comparison of the two major classes of assembly algorithms: overlap-layout-consensus and de-bruijn-graph." Brief Funct Genomics 11(1): 25-37.

Treangen, T. J. and S. L. Salzberg (2012). "Repetitive DNA and next-generation sequencing: computational challenges and solutions." Nat Rev Genet 13(1): 36-46.

http://www.cbcb.umd.edu/research/assembly_primer.shtml

Schatz, M. C., J. Witkowski, et al. (2012). "Current challenges in de novo plant genome sequencing and assembly." Genome Biol 13(4): 243

Baker, M. (2012). "De novo genome assembly: what every biologist should know." Nat Methods 9(4): 333-337. （重点推荐）

Compeau, P. E., et al. (2011). "How to apply de Bruijn graphs to genome assembly." Nat Biotechnol 29(11): 987-991.

Birney, E. (2011). "Assemblies: the good, the bad, the ugly." Nat Methods 8(1): 59-60.

Schatz, M. C., et al. (2010). "Assembly of large genomes using second-generation sequencing." Genome Res 20(9): 1165-1173.

### 4.2 纠错软件：

Kelley, D. R., M. C. Schatz, et al. (2010). "Quake: quality-aware detection and correction of sequencing errors." Genome Biol 11(11): R116.

### 4.3 组装软件比较

Salzberg, S. L., A. M. Phillippy, et al. (2012). "GAGE: A critical evaluation of genome assemblies and assembly algorithms." Genome Res 22(3): 557-567.

Zhang, W., et al. (2011). "A practical comparison of de novo genome assembly software tools for next-generation sequencing technologies." PLoS One 6(3): e17915.

Narzisi, G. and B. Mishra (2011). "Comparing de novo genome assembly: the long and short of it." PLoS One 6(4): e19175.

Lin, Y., et al. (2011). "Comparative Studies of de novo Assembly Tools for Next-generation Sequencing Technologies." Bioinformatics.

Hayden, E. C. (2011). "Genome builders face the competition." Nature 471(7339): 425.

Finotello, F., et al. (2011). "Comparative analysis of algorithms for whole-genome assembly of pyrosequencing data." Brief Bioinform.

Earl, D. A., et al. (2011). "Assemblathon 1: A competitive assessment of de novo short read assembly methods." Genome Res.

### 4.4 组装质量评估

Schatz, M. C., et al. (2011). "Hawkeye and AMOS: visualizing and assessing the quality of genome assemblies." Brief Bioinform.

Riba-Grognuz, O., et al. (2011). "Visualization and quality assessment of de novo genome assemblies." Bioinformatics.

个人见解：

目前大基因组的denovo组装主流软件还是ALLPATH-LG SOAPdenovo

ALLPATH-LG的优点是：组装的连续性最好，准确性最好，但是消耗内存较大，不是太好使用

SOAPdenovo的优点是：速度快，消耗的内存可以接受，组装的连续性还可以，但是错误相对要多一些。

当然，上述评述并不是在所有情况下的，对不同物种，不同数据，他们的表现可能会不一样。

基于Overlap-layout的方法的组装软件首推CABOG，这是当年用来组装果蝇基因组的原型。另外，快要发布的MSR-CA貌似也不错，其整合了上述所有软件的优点，来势很猛啊。

## 5. 基因组注释

Yandell, M. and D. Ence (2012). "A beginner's guide to eukaryotic genome annotation." Nat Rev Genet 13(5): 329-342.

## 6. 基因组可视化

Nielsen, C. B., M. Cantor, et al. (2010). "Visualizing genomes: techniques and challenges." Nat Methods 7(3 Suppl): S5-S15.

## 7. 进化分析

Yang, Z. and B. Rannala (2012). "Molecular phylogenetics: principles and practice." Nat Rev Genet 13(5): 303-314.

## 8. 经典案例

Colbourne, J. K., M. E. Pfrender, et al. (2011). "The ecoresponsive genome of Daphnia pulex." Science 331(6017): 555-561.

Kim, E. B., X. Fang, et al. (2011). "Genome sequencing reveals insights into physiology and longevity of the naked mole rat." Nature 479(7372): 223-227.

Grbic, M., T. Van Leeuwen, et al. (2011). "The genome of Tetranychus urticae reveals herbivorous pest adaptations." Nature 479(7374): 487-492.

以上内容转载自：测序中国seq.cn（http://seq.cn/4607-48597）

欢迎大家更新补充，参与讨论。