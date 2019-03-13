# SAM格式详解

[TOC]

## SAM格式

SAM的全称是sequence alignment/map format。

SAM是一种序列比对格式标准， 由sanger制定，是以TAB为分割符的文本格式。主要应用于测序序列mapping到基因组上的结果表示，当然也可以表示任意的多重比对结果。

不同的软件，不同的时期，不同的研究方向，都会创建一种或者多种格式标准，当然根据当时的需要，创建符合需求的标准，也是最容易的事情，而反过来想要真正的理解标准，也必须理解为什么要创建这样的标准，解决什么样的需要。

比如aln格式，是比对视图化的展示，存储的信息不够结构化，无法方便的作为另外程序的输入；表示信息的有限性，如果100个多重比对序列放到一个文件中，查看维护就会非常困难；还有些格式标准挺强大，但是太繁琐，同时不够灵活。那么反过来就是SAM格式的优点，那么SAM如何做到这一点的呢？

## SAM文件内容的结构

SAM分为两部分，注释信息（header section）和比对结果部分（alignment section），通常是把FASTQ文件格式的测序数据比对到对应的参考基因组版本得到的。

注释信息并不是SAM文件的重点，是该SAM文件产生以及被处理过程的一个记录，规定以@开头，用不同的tag表示不同的信息，主要有：

- @HD，说明符合标准的版本、对比序列的排列顺序；
- @SQ，参考序列说明；
- @RG，比对上的序列（read）说明；
- @PG，使用的程序说明；
- @CO，任意的说明信息。

![](https://ws3.sinaimg.cn/large/006tKfTcgy1fo7xvdk92dj30cf0a03zs.jpg)

一个简单的SAM文件例子

```bash
@HD VN:1.0 SO:unsorted
@SQ SN:chr1 LN:249250621
@SQ SN:chr2 LN:243199373
@PG ID:Bowtie VN:1.0.0 CL:"bowtie genome/hg19 -q reads/SRR3101251.fastq -m 1 -p 4 -S"
SRR3101251.1 0 chr19 9486878 255 49M * 0 0 NTACTCCCACTACTCTCAGATTCAAGCAATCCTCCCACCCTAGCCCACC #1=DDDFFHHHHHIHHIJJJHIJIIJIHIFHJIIJJJJJJJIIJJJJJJ XA:i:1 MD:Z:0A48 NM:i:1
SRR3101251.5 16 chr2 240279787 255 49M * 0 0 CCTGAATCCATCAGAGCAGCCGGGCTGTGACACTCACTGTCATGATGTT JIJJIHIIIIJJJJJJJJJGHJJJJIIHJHICJIGCHHHHHFFFFFCCC XA:i:0 MD:Z:49 NM:i:0
SRR3101251.6 4 * 0 0 * * 0 0 NATTCCCACCTATGAGTGAGAATATGCGGTGTTTGGTTTTTTGTTCTTG #1=DDDFFHHHHHJJJGHIJJJJJJJJJJCGGIIJJIIJJJIJHJIIJJ XM:i:1
```

前四行是注释信息，其后是比对结果，下面对比对结果进行解释，它是SAM格式文件的精华部分。

### 比对结果部分（alignment section）

```bash
SRR035022.2621862 163 16 59999 37 22S54M = 60102 179 CCAACCCAACCCTAACCCTAACCCTAACCCTAACCCTAACCCTAACCCTAACCCTAACCGACCCTCACCCTCACCC >AAA=>?AA>@@B@B?AABAB?AABAB?AAC@B?@AB@A?A>A@A?AAAAB??ABAB?79A?AAB;B?@?@<=8:8 XT:A:M XN:i:2 SM:i:37 AM:i:37 XM:i:0 XO:i:0 XG:i:0 RG:Z:SRR035022 NM:i:2 MD:Z:0N0N52 OQ:Z:CCCCCCCCCCCCCCCCCCCCCCCCCCCCCCBCCCCCCBBCC@CCCCCCCCCCACCCCC;CCCBBC?CCCACCACA@
```

所以在我们的例子中，每一个字段的说明如下：

```bash
QNAME	SRR035022.2621862
FLAG	163
RNAME	16
POS	59999
MAQ	37
CIGAR	22S54M
MRNM	=
MPOS	60102
ISIZE	179
SEQ	CCAACCCAACCCTAACCCTAACCCTAACCCTAACCCTAACCCTAACCCTAACCCTAACCGACCCTCACCCTCACCC
QUAL	>AAA=>?AA>@@B@B?AABAB?AABAB?AAC@B?@AB@A?A>A@A?AAAAB??ABAB?79A?AAB;B?@?@<=8:8
TAG	XT:A:M
TAG	XN:i:2
TAG	SM:i:37
TAG	AM:i:37
TAG	XM:i:0
TAG	XO:i:0
TAG	XG:i:0
TAG	RG:Z:SRR035022
TAG	NM:i:2
TAG	MD:Z:0N0N52
TAG	OQ:Z:CCCCCCCCCCCCCCCCCCCCCCCCCCCCCCBCCCCCCBBCC@CCCCCCCCCCACCCCC;CCCBBC?CCCACCACA
```

The alignment section consists of multiple TAB-delimited lines with each line describing an alignment. Each line is:

```bash
<QNAME> <FLAG> <RNAME> <POS> <MAPQ> <CIGAR> <MRNM> <MPOS> <ISIZE> <SEQ> <QUAL> [<TAG>:<VTYPE>:<VALUE> [...]]
```

每一行表示一个片段（segment）的比对信息，包括11个必须的字段（mandatory fields）和一个可选的字段，字段之间用tag分割。必须的字段有11个，顺序固定，不可用时，根据字段定义，可以为’0‘或者’*‘。

#### SAM每一列的含义

下文中read表示sam对应的read，mate表示sam对应read的pairRead

**第一列：**read name，read的名字通常包括测序平台等信息；

**第二列：**sum of flags，每个flag用数字来表示，分别为：

1 read是pair中的一条（read表示本条read，mate表示pair中的另一条read）

2 pair一正一负完美的比对上

4 这条read没有比对上

8 mate没有比对上

16 这条read反向比对

32 mate反向比对

64 这条read是read1

128 这条read是read2

256 第二次比对

512 比对质量不合格

1024 read是PCR或光学副本产生

2048 辅助比对结果

>（picard专门有一个工具解读sam的flag:http://broadinstitute.github.io/picard/explain-flags.html）
>
>0：比对到参考序列的正链上（待求证)

通过这个和可以直接推断出匹配的情况。假如说标记不是以上列举出的数字，比如说83=（64+16+2+1），就是这几种情况值和。

**第三列：**RNAM，reference sequence name，实际上就是比对到参考序列上的染色体号。若是无法比对，则是*；

**第四列：**position，read比对到参考序列上，第一个碱基所在的位置。若是无法比对，则是0；

**第五列：**Mapping quality，比对的质量分数，越高说明该read比对到参考基因组上的位置越唯一；  

**第六列：**CIGAR值，read比对的具体情况，

“M”表示 match或 mismatch；

“I”表示 insert；

“D”表示 deletion；

“N”表示 skipped（跳过这段区域）；

“S”表示 soft clipping（被剪切的序列存在于序列中）；

“H”表示 hard clipping（被剪切的序列不存在于序列中）；

“P”表示 padding；

“=”表示 match；

“X”表示 mismatch（错配，位置是一一对应的）；

**第七列：**MRNM(chr)，mate的reference sequence name，实际上就是mate比对到的染色体号，若是没有mate，则是*；

**第八列：**mate position，mate比对到参考序列上的第一个碱基位置，若无mate,则为0；

**第九列：**ISIZE，Inferred fragment size.详见Illumina中paired end sequencing 和 mate pair sequencing，是负数，推测应该是两条read之间的间隔(待查证)，若无mate则为0；

**第十列：**Sequence，就是read的碱基序列，如果是比对到互补链上则是reverse completed   eg.CGTTTCTGTGGGTGATGGGCCTGAGGGGCGTTCTCN 

**第十一列：**ASCII，read质量的ASCII编码。

**第十二列之后：**Optional fields，可选的区域

可选字段（optional fields)，格式如：TAG:TYPE:VALUE，其中TAG有两个大写字母组成，每个TAG代表一类信息，每一行一个TAG只能出现一次，TYPE表示TAG对应值的类型，可以是字符串、整数、字节、数组等。

```python
AS:i:<N>
    Alignment score.可以为负的，在local下可以为正的。 只有当Align≥1 time才出现
XS:i:<N>
    Alignment score for second-best alignment.  当Align>1 time出现
YS:i:<N>
    Alignment score for opposite mate in the paired-end alignment.   当该read是双末端测序中的一条时出现
XN:i:<N>
    The number of ambiguous bases in the reference covering this alignment.（推测是指不知道错配发生在哪个位置，推测是针对于插入和缺失，待查证）
XM:i:<N>
    错配碱基的数目
XO:i:<N>
    The number of gap opens(针对于比对中的插入和缺失)
XG:i:<N>
    The number of gap extensions(针对于比对中的插入和缺失)
NM:i:<N>
    The edit distance(read string转换成reference string需要的最少核苷酸的edits:插入/缺失/替换)
YF:Z:<S>
    该reads被过滤掉的原因。可能为LN(错配数太多，待查证)、NS(read中包含N或者．)、SC(match bonus低于设定的阈值)、QC(failing quality control，待证)
YT:Z:<S>
    值为UU表示不是pair中一部分(单末端？)、CP(是pair且可以完美匹配)
    DP(是pair但不能很好的匹配)、UP(是pair但是无法比对到参考序列上)
MD:Z:<S>
    比对上的错配碱基的字符串表示
```

---

## SAM要处理好的问题

- 非常多序列（read)，mapping到多个参考基因组（reference）上
- 同一条序列，分多段（segment）比对到参考基因组上
- 无限量的，结构化信息表示，包括错配、删除、插入等比对信息

>**Using SAM to store various types of alignments:**
>
>- **Clipped alignment**
>
>In Smith-Waterman alignment, a sequence may not be aligned from the first residue to the last one. Subsequences at the ends may be clipped off. We introduce operation 'S' to describe clipped alignment. Suppose the clipped alignment is:
>
>```bash
>REF: AGCTAGCATCGTGTCGCCCGTCTAGCATACGCATGATCGACTGTCAGCTAGTCAGACTAGTCGATCGATGTG
>READ:       gggGTGTAACC-GACTAGgggg
>```
>
>where on the read sequence, bases in uppercase are matches and bases in lowercase are clipped off. The CIGAR for this alignment is: 3S8M1D6M4S (which I interpret as 3 soft, 8 match, 1 deletion, 6 match and 4 soft).
>
>- **Spliced alignment**
>
>In cDNA-to-genome alignment, we may want to distinguish introns from deletions in exons. We introduce openation 'N' to represent long skip on the reference sequence. Suppose the spliced alignment is:
>
>```bash
>REF: AGCTAGCATCGTGTCGCCCGTCTAGCATACGCATGATCGACTGTCAGCTAGTCAGACTAGTCGATCGATGTG
>READ:          GTGTAACCC................................TCAGAATA
>```
>
>where '...' on the read sequence indicates intron. The CIGAR for this alignment is : 9M32N8M.
>
>- **Multi-part alignment**
>
>One query sequence may be aligned to multiple places on the reference genome, either with or without overlaps. In SAM, we keep multiple hits as multiple alignment records. To avoid presenting the full query sequence multiple times for non-overlapping hits, we introduce operation 'H' to describe hard clipped alignment. Hard clipping (H) is similar to soft clipping (S). They are different in that hard clipped subsequence is not present in the alignment record. The example alignment in "clipped alignment" can also be represented with CIGAR: 3H8M1D6M4H, but in this case, the sequence stored in SAM is "GTGTAACCGACTAG", instead of "GGGGTGTAACCGACTAGGGGG" if soft clipping is in use.
>
>- **Padded alignment**
>
>Most sequence aligners only give the sequences inserted to the reference genome, but do not present how these inserted sequences are aligned against each other. Alignment with inserted sequences fully aligned is called padded alignment. Padded alignment is always produced by de novo assemblers and is important for an alignment viewer to display the alignment properly. To store padded alignment, we introduce operation 'P' which can be considered as a silent deletion from padded reference sequence. In the following example, GA on READ1 and A on READ2 are inserted to the reference. With unpadded CIGAR, we would not be able to distinguish the following padded multi-alignments:
>
>```bash
>REF:  CACGATCA**GACCGATACGTCCGA
>READ1:  CGATCAGAGACCGATA
>READ2:    ATCA*AGACCGATAC
>READ3:   GATCA**GACCG
>
>The padded CIGAR are different:
>READ1: 6M2I8M
>READ2: 4M1P1I9M
>READ3: 5M2P5M
>```
>
>Note that it is hard to convert unpadded CIGAR to padded one. Fully resolving the alignment between inserted sequences would essentially require a de novo assembler. However, it is easy vice versa. By simply removing all P operations we get the CIGAR without padding.
>
>**Alignments in colour space** Colour alignments are stored as normal nucleotide alignments with additional tags describing the raw colour sequences, qualities and colour-specific properties.

## 扩展&备注

![](https://ws2.sinaimg.cn/large/006tKfTcgy1fo7x9relxkj30mu0q0goc.jpg)

![](https://ws3.sinaimg.cn/large/006tKfTcgy1fo7xw8k9z8j30w70fz79w.jpg)

### QNAME

The QNAME is the query name. For the FLAG of 163 we transform this into a binary string: 10100011. So accordingly to the flag table:

![](https://ws1.sinaimg.cn/large/006tKfTcgy1fo7xvw2vjuj30vz0bedjw.jpg)

### FLAG

Each bit in the FLAG field is defined as:

![](https://ws4.sinaimg.cn/large/006tKfTcgy1fo7xajdrtsj30mu0p1wgx.jpg)

### RNAME

The RNAME is chromosome 16; the POS is the 59_999; the MAQ is 37.

And now the CIGAR format:

A CIGAR string is comprised of a series of operation lengths plus the operations. The conventional CIGAR format allows for three types of operations: M for match or mismatch, I for insertion and D for deletion. The extended CIGAR format futher allows four more operations, as is shown in the following table, to describe clipping, padding and splicing:

| op   | Description                                                  |
| ---- | ------------------------------------------------------------ |
| M    | Alignment match (can be a sequence match or mismatch         |
| I    | Insertion to the reference                                   |
| D    | Deletion from the reference                                  |
| N    | Skipped region from the reference                            |
| S    | Soft clip on the read (clipped sequence present in <seq>)    |
| H    | Hard clip on the read (clipped sequence NOT present in <seq>) |
| P    | Padding (silent deletion from the padded reference sequence) |

### Optional fields

Optional fields are in the format: <TAG>:<VTYPE>:<VALUE>. Each tag is encoded in two alphanumeric characters and appears only once for an alignment. The <VTYPE> follows Perl's rule (see perldoc -f pack). Valid types in SAM are:

| Type | Description                    |
| ---- | ------------------------------ |
| A    | Printable character            |
| i    | Signed 32-bin interger         |
| f    | Single-precision float number  |
| Z    | Printable string               |
| H    | Hex string (high nybble first) |

There are a bunch of predefined tags, please see the SAM manual for more information. For the tags used in this example:

Any tags that start with X? are reserved fields for end users: **XT:A:M, XN:i:2, XM:i:0, XO:i:0, XG:i:0**

**SM:i:37** - Mapping quality if the read is mapped as a single read rather than as a read pair

**AM:i:37** - Smaller single-end mapping quality of the two reads in a pair

**RG:Z:SRR035022** - Read group. Value matches the header RG-ID tag if @RG is present in the header

**NM:i:2** - Number of nucleotide differences (i.e. edit distance to the reference sequence)

**MD:Z:0N0N52** - String for mismatching positions in the format of [0-9]+(([ACGTN]|\^[ACGTN]+)[0-9]+)*

**OQ:Z:CCCCCCCCCCCCCCCCCCCCCCCCCCCCCCBCCCCCCBBCC@CCCCCCCCCCACCCCC;CCCBBC?CCCACCACA@** - Original base quality. Encoded in the same wasy as QUAL

![](https://ws2.sinaimg.cn/large/006tKfTcgy1fo7xwkdiawj30np0m3107.jpg)

---

要注意的**几个概念**，以及与之对应的模型：

- reference
- read
- segment
- template（参考序列和比对上的序列共同组成的序列为template）
- alignment
- seq

---




## Parsing SAM files using Perl

http://search.cpan.org/~lds/Bio-SamTools/lib/Bio/DB/Sam.pm

## SAM Format Specification

http://samtools.sourceforge.net/SAM1.pdf