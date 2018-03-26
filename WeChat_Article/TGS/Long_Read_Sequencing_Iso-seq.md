# 想知道三代转录组测序“长”在哪里吗？

NTLx

❝

不同于大家熟知的二代转录组测序，三代转录组测序有个专有名词与之区分，叫做“全长转录组测序”。在这个专有名词里面，“全长”指的自然就是三代测序平台的拿手好戏：一次性得到转录本的全长。但是“长”还有“长处”即优势这一层含义。小编借一篇刚发表不久的无参全长转录组测序文章向大家展示一下全长转录组的“长处”。

❞

[TOC]

---

![paper](https://ws3.sinaimg.cn/large/006tNc79gy1fl3sz079haj31kw0stgt4.jpg)

- 黄芪是使用最广泛的中药之一。

![](https://ws3.sinaimg.cn/large/006tNc79gy1fl3talrx1fj308f0co47v.jpg)

![](https://ws1.sinaimg.cn/large/006tNc79gy1fl3tb67oeoj30ca09n46r.jpg)

![](https://ws3.sinaimg.cn/large/006tNc79gy1fl3tbjdn8lj30co09qn5c.jpg)

- 黄芪中药配方已被用于治疗各种疾病，如心血管疾病，II型糖尿病，肾炎和癌症。药理研究表明，黄芪提取物中存在免疫调节，抗高血糖，抗炎，抗氧化和抗病毒活性。因此，黄芪生物活性化合物的生物合成，如黄芪苷，胆固醇苷和毛蕊异黄酮苷的生物合成，对黄芪的进一步遗传研究尤其重要。
- 这篇文章用PacBio RS II平台Iso-Seq方法，对叶（共得到27975个转录本）和根（共得到22343个转录本）两种来源的RNA进行测序。除了拿到更长的转录本、鉴定了新的Isoform以外，还鉴定了参与黄芪苷、胆钙素和毛蕊异黄酮苷生物合成的基因潜在的转录本。

## 材料与建库

作者使用BluePippin对叶和根RNA反转录得到的cDNA进行片段大小选择，为每种组织来源都建立了1-2kb和2-3kb两种文库。作者对叶和根都测了8个SMRT Cell的数据。

![](https://ws1.sinaimg.cn/large/006tNc79gy1fl3tkttruyj30ye0jeq5t.jpg)

##结果与分析

- 该研究提供了一个探索黄芪活性化合物生物合成的无参全长转录组分析流程。

![](https://ws1.sinaimg.cn/large/006tNc79gy1fl3tcs8cfjj30tq0vbtji.jpg)

### *A. membranaceus* transcriptome analysis using PacBio Iso-Seq

![](https://ws4.sinaimg.cn/large/006tNc79gy1fl3tnbz9lgj31bf0nggp5.jpg)

### *A. membranaceus* transcriptome analysis using PacBio Iso-Seq

![](https://ws4.sinaimg.cn/large/006tNc79gy1fl3to95rstj30lx0pidm6.jpg)

a. Iso-Seq与454&Illumina共有转录本的N50是后两者的2倍（图a，Length distribution ）根据文献，454的N50为1205

b. Iso-Seq与Illumina共有转录本ORF的对比（图b，Cumulative density plot ）：Iso-Seq明显包含更多full-lengthORFs(covered 100% of curatedfull-length protein)

- ORF用UniProtKnowledgebase注释得到

### Reconstruction of unique full-length transcript models of *A. membranaceus* without a reference genome

![](https://ws4.sinaimg.cn/large/006tNc79gy1fl3tq95x8qj30ks0kn785.jpg)

> Length distribution of Iso-Seq consensus transcripts (standard Iso-Seq pipeline) and full-length UniTransModels (full pipeline).

![](https://ws3.sinaimg.cn/large/006tNc79gy1fl3tqv1yqfj30xi0ehahp.jpg)

> Example showing two steps of the pipeline for full-length UniTransModel reconstruction.

与标准Iso-Seq得到的转录本相比，该文完整pipeline得到的转录本与其长度相似，但显著降低了长度为~1 600nt和~2 800nt转录本的数量，表明标准Iso-Seq中仍有不少冗余。

![](https://ws4.sinaimg.cn/large/006tNc79gy1fl3tscurzej30rn0jdq5b.jpg)

> About half of the UniTransModelswere only detected in one of two tissues  (13105 out of 27 975 in leaf, and 11 011 out of 22 343 in root).

###Functional annotation of full-length *A. membranaceus* transcriptomes from two tissues

![](https://ws4.sinaimg.cn/large/006tNc79gy1fl3ttm664fj30kq0d2jt0.jpg)

- 在两种组织中small molecular metabolic process是富集最显著的条目
- 与不同metabolic process相关的条目更多地富集在叶中
- 与Biological process类别中的localisation、transport相关的条目更多富集在根中
- Molecular function类别中类似nucleotide binding这样的条目更多在叶中富集
- Molecular function类别中与enzyme ‘activity’有关的条目，例如ATPase activity和nucleoside-triphosphatase activity等更多在根中富集

**为了更综合地获得转录本注释：**

- 作者annotated full-length UniTransModels from each tissue by similarity search against protein sequences curated in UniProtKB and soybean reference proteins
- 和根中注释到的UniTransModels总数分别为96.7％和96.2％
- 少数未知的UniTransModel（叶933个，根843个）可能代表新的黄芪特异基因

![](https://ws4.sinaimg.cn/large/006tNc79gy1fl3tvcasdoj30pg03k756.jpg)

**利用大豆的UniProtKB对黄芪UniTransModels进行功能分类，叶和根分别有11 046和9 919个得到注释：**

![](https://ws3.sinaimg.cn/large/006tNc79gy1fl3twfsidpj30pe0aj40t.jpg)

- 总体而言，在叶和根组织中UniTransModels的GO功能分类非常相似。
- 其中，metabolic process是两种组织中最常见的（约25%）条目，‘cellular process’ and ‘localisation’次之；
- ‘Molecularfunction’ and ‘Cellular component’分类中，‘catalytic activity’ and ‘cell part’是两种组织中最多的。

**Further classification of UniTransModels involved in ‘metabolic process’ functional terms in GO：**

![](https://ws3.sinaimg.cn/large/006tNc79gy1fl3txdrza7j30nu09wt9y.jpg)

- ‘metabolicprocess代谢过程’这个分类中的条目，差不多一半都与两种组织中的‘primary metabolic process初级代谢过程’有关，约15％的UniTransModel参与‘nitrogen compound metabolic process氮化合物代谢过程’。
- 约0.8%的UniTransModels在两个组织中被分类为‘secondarymetabolic process次要代谢过程’。

**KEGG pathway classification of A. membranaceus UniTransModels in leaf and root：**

![](https://ws1.sinaimg.cn/large/006tNc79gy1fl3tyk3lllj30pg09yac6.jpg)

- 与Go注释的结果一样，不同组织的KEGG通路富集结果非常类似，注释的UniTransModel中超过一半被归类为“代谢”相关途径，两种组织中的Top3通路为‘Carbohydrate metabolism’, ‘Folding,sorting and degradation’ and ‘Amino acid metabolism’。
- 叶和根KEGG注释的差异主要在‘Folding, sorting and degradation’ and‘Energy metabolism’两种通路涉及的转录本数目上的差别。
- 相比于根，叶中‘Folding, sorting and degradation’比对到的转录本较少(17.54% compared with 20.75%)；而‘Energy metabolism’比对到的转录本较多(8.13% compared with 5.25%)。
- 结合GO和KEGG注释的结果，通路水平（pathway level）的转录组通常是保守的，尽管单个基因（individual gene）的表达量可能不同。

### AS detection without a reference genome

![](https://ws1.sinaimg.cn/large/006tNc79gy1fl3tzaa9owj30p608pab1.jpg)

> 左图：Distributionof isoform numbers for UniTransModelsin leaf and root.
>
> 右图：Numbers of different AS events detected in full-length transcriptomes from rootand leaf.

- PacBioIso-Seq的一个优点是能够描述AS在整个转录组规模上的复杂性。这篇文章就是通过前面分析流程中展示的，把Iso-Seq产生的转录本重建为Full-length UniTransModel来鉴定Isoform。

**左图：叶和根中UniTransModels的Isoform数量的分布。**

- 叶中36.53%的UniTransModel有不止一个Isoform，根的比例略少(34.46%)。有趣的是，与根（107，0.48％）相比，叶有更多的UniTransModel具有超过10个Isoform（299，1.07％）。

**右图：在根和叶的全长转录本中检测到的不同AS事件的数量。**

- 使用UniTransModels作为参考来检测这些AS事件，这与基于基因组序列的AS事件不同。 SE，外显子跳过；RI，内含子保留; A5，替代5'剪接位点; A3，替代3’剪接位点; AF，替代第一外显子; AL，替代最后一个外显子。

作者分别在叶和根组织中鉴定了6 494和4 399个基于UniTransModel的AS事件。内含子保留是两种组织中最多的As事件，算上5‘端和3’端剪接位点替换，这三种类型占全部As事件的90%。

**Sashimi plot showing an example of the same gene generating different transcript isoforms detected with our pipeline in two tissues：**

![](https://ws4.sinaimg.cn/large/006tNc79gy1fl3u21at34j30p20afdht.jpg)

- Sashimi Plot展示了作者的pipeline在两个组织中检测到的，相同基因产生不同转录本Isoform的例子。
- 叶中有四种Isoform，包含8个splicing junction sites (SJ)；根中有5种Isoform，包含5个SJ（剪接位点）。
- 在两个组织中的Isoform之间共享四种SJ（对应于根中的SJ2-SJ5的叶中的SJ3-SJ6，以蓝色着色）。
- 红色的峰表示short read的覆盖度，红色的线表示剪接位点，有数字标识。
- 对于每个Isoform，蓝色的块表示外显子，其间的线代表内含子。
- 通过将Illumina short reads map到transcript models，就可以将其用来在没有参考基因组的情况下确认Isoform检测的可靠性。
- 作者还检测到不同组织中相同UniTransModels的不同剪接产生的不同Isoform。

**Distribution of numbers of isoforms for genes in different GO biological process functional terms：**

![](https://ws1.sinaimg.cn/large/006tNc79gy1fl3u40rv0qj31js1qh4ib.jpg)

> (A)Distribution of numbers of isoforms for genes in top­‐levelGO biological process terms. Only terms with more than 10 genes wereconsidered. 
>
> (B)Distribution of number of isoforms for genes in sub‐levelGO functional terms under the top­‐levelof “metabolic process”. Only terms with more than 10 genes were considered.

这就是一张GO富集TOP10图。

- 作者为了看基因对应的Isoform在数量上与其对应的不同GO条目是否有偏好性，做了一个GO富集分析。
- A图：最多的9个‘Biological process’分类下的功能条目的分布十分相似；而在根中，注释到‘multicellular organismal process’的基因有更少的转录本，与注释到其他条目的其他基因相比，这些基因会多出至少一种Isoform。
- B图：对于注释到‘metabolic process’条目的部分，作者发现与其他代谢过程功能条目相比，有更多数量的基因被注释为具有多于一种Isoform的“coenzyme metabolic process辅酶代谢过程”。此外，与叶片和根组织中的“secondary metabolic process次生代谢过程”相比，作者还发现“primary metabolic process初级代谢过程”中具有多于一种Isoform的基因的百分比较高。

### LncRNA identification in *A. membranaceus* full-length transcriptomes

![](https://ws1.sinaimg.cn/large/006tNc79gy1fl3u774psmj30q4083t9y.jpg)

>Identificationof A. membranaceuslncRNAs.
>
>(a)Pipelineused to identify lncRNAs.Text in black: data sets used/processed in different steps. Text in blue: toolsand thresholds used for filtering protein-coding transcripts. Text in red:numbers of transcripts in each data set, with left for leaf and right for root.
>
>(b)Lengthdistribution of identified lncRNAsin leaf and root. 
>
>(c)Distributionof isoform numbers for lncRNAsin two tissues.

- 通过Rfam ncRNA families检索，这些lncRNA中只有少数能够用已知信息注释，能注释的这些里面大多数似乎是snoRNA或miRNA的转录前体（precursor transcripts）。
- 这些lncRNA的功能，特别是未注释的功能需要进一步研究。

### Re-characterisation of genes involved in biosynthesis of bioactive compounds in *A. membranaceus*

![](https://ws2.sinaimg.cn/large/006tNc79gy1fl3u8o2xpwj30o80cgabw.jpg)

- Sashimi Plot显示叶（a）和根（b）中AmMVD基因（编码甲羟戊酸二磷酸脱羧酶）的转录本Isoform。叶和根中的“亚型3”是与NCBI参考文献相同的Isoform（登录号：KF355964）。 
- AST，碳水化合物和CG是研究较多的生物活性化合物，其生物合成途径中的关键基因已被鉴定。使用来自参与AST生物合成的18个基因的NCBI mRNA序列和涉及碳水化合物和CG生物合成的14个基因来搜索UniTransModels。
- 在AST生物合成途径中鉴定了14个叶UniTransModel和13个根UniTransModels，与17个NCBI mRNA相对应。该研究得到的Iso-Seq全长序列与17个NCBI mRNA序列相比更长，其中大部分（17个中有15个）的序列几乎完全存在于Iso-Seq全长序列（覆盖率> 95％）。作者还发现，这些基因中的几个可能在两个组织中都具有多个Isoform。此外，AmMVD还可以在两个组织中具有组织特异性Isoform。
- 对于碳水化合物和CG生物合成，作者鉴定了对应于12个NCBI mRNA的11个叶UniTransModels和对应于10个NCBI mRNA的9个根UniTransModels，其中所有NCBI mRNA的序列几乎完全存在于（覆盖率> 95％）叶或根Iso-Seq全长UniTransModels。与AST生物合成途径一样，在作者的全长Iso-Seq转录组中，对于参与碳水化合物和CG生物合成的这些UniTransModel，也发现了更长的序列和多种Isoform。

## 看到这里的都是学霸

看到这里的同学应该已经对这篇文章有了大致的了解，我们可以看到作者在文章中的主要结果有两块内容：除了构建无参全长转录组的分析pipeline外，作者始终围绕分析所得转录本的结构和功能进行研究。这实际上也正符合三代测序平台在转录组测序方面的“长处”，那就是在转录本结构方面有着无可比拟的优势。

当然，三代测序平台产出单位数据量的价格要比二代测序平台贵不少，所以通常数据量都不足以做差异表达研究。当我们做完三代全长转录组测序之后，再做一个二代转录组测序提供差异表达信息，二者结合就能够拿到比以往丰富得多的数据，为我们的研究提供强有力的支持。

怎么样？是不是也想尝尝三代的味道？欧易生物三代测序平台期待您的合作哦~~~