<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Welcome file</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__left">
    <div class="stackedit__toc">
      
<ul>
<li><a href="#mbs-培训">MBS 培训</a>
<ul>
<li><a href="#方法简介">方法简介</a></li>
<li><a href="#定位原理简述">定位原理简述</a></li>
<li><a href="#应用范围">应用范围</a></li>
<li><a href="#取样">取样</a></li>
<li><a href="#几个常见问题">几个常见问题</a></li>
<li><a href="#报告解读">报告解读</a></li>
<li><a href="#分析特色">分析特色</a></li>
<li><a href="#注意事项">注意事项</a></li>
<li><a href="#成功案例">成功案例</a></li>
<li><a href="#名词解释">名词解释</a></li>
</ul>
</li>
</ul>

    </div>
  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <h1 id="mbs-培训">MBS 培训</h1>
<blockquote>
<p>主要面向公司内部、非 MBS 分析员使用</p>
</blockquote>
<h2 id="方法简介">方法简介</h2>
<p>MBS <sup class="footnote-ref"><a href="#fn1" id="fnref1">1</a></sup> 全称为 Mapping By Sequencing（即“利用测序进行定位”）。针对 <strong>有参考基因组</strong> 的物种，利用 <strong><code>混合分组分析</code></strong> <sup class="footnote-ref"><a href="#fn2" id="fnref2">2</a></sup> 的策略，结合 <strong><code>全基因组重测序</code></strong> <sup class="footnote-ref"><a href="#fn3" id="fnref3">3</a></sup> 技术，将鉴别到的分子标记（即<code>突变位点</code> <sup class="footnote-ref"><a href="#fn4" id="fnref4">4</a></sup> ，包括 SNP <sup class="footnote-ref"><a href="#fn5" id="fnref5">5</a></sup> 、InDel <sup class="footnote-ref"><a href="#fn6" id="fnref6">6</a></sup> 等）与<code>性状</code> <sup class="footnote-ref"><a href="#fn7" id="fnref7">7</a></sup> 进行共分离分析（即寻找突变位点与性状的相关性），对锁定到的基因组目标区间（即连锁 <sup class="footnote-ref"><a href="#fn8" id="fnref8">8</a></sup> 区间）内的突变位点和基因进行功能注释，实现性状决定基因的快速定位。</p>
<h2 id="定位原理简述">定位原理简述</h2>
<p>在分离群体搭建过程中，子代会根据表型进行选择，筛选出突变型子代池和野生型子代池，根据遗传连锁交换定律，子代池的基因型会和表型产生共分离，反应在物理图谱层面，与表型连锁的染色体区段会和不连锁的染色体区间产生稳定的 SNP-index <sup class="footnote-ref"><a href="#fn9" id="fnref9">9</a></sup> 差异。</p>
<p>SNP-index 原理图（G 位点来自于突变亲本，C 位点来自于野生亲本）：</p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/SNP_index.jpg" alt=""></p>
<p>对于既有突变型子代池，也有野生型子代池的项目来说，可以利用两个子代池的 SNP-index 计算差值，得到 ΔSNP-index ，即两个子代池中在相同位点的 index 值的差值。</p>
<p>利用 ΔSNP-index 定位可以避免群体构建过程中奠基者效应 <sup class="footnote-ref"><a href="#fn10" id="fnref10">10</a></sup> 的影响，如下图所示：</p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/delta_SNP_index.jpg" alt=""></p>
<h3 id="与-bsa-的区别">与 BSA 的区别</h3>
<p>在传统的图位克隆中，我们一般先利用 BSA 原理进行粗定位，寻找和突变表型连锁的 Marker（分子标记），再在附近设计新的 Marker，利用作图群体进行精细定位，一步步缩小和突变表型连锁的染色体区段，直到鉴定出突变基因。MBS 的原理和图位克隆本质上是一样的，只不过把我们常规使用的 Marker 换成了 SNP，把通过 PCR 和酶切进行多态性鉴定，换成了用重测序的方法直接对 SNP 的多态性进行分析，节省了大量的人力、物力以及时间上的消耗。</p>
<h3 id="方法文献">方法文献</h3>
<p>Akira Abe, Shunichi Kosugi, Kentaro Yoshida, et al. <a href="https://www.nature.com/articles/nbt.2095">Genome sequencing reveals agronomically important loci in rice using MutMap</a>[J]. Nature Biotechnology, 2012, 30(2):174–178.</p>
<p>Hiroki Takagi, Akira Abe, Kentaro Yoshida, et al. <a href="http://onlinelibrary.wiley.com/doi/10.1111/tpj.12105/abstract">QTL-seq: rapid mapping of quantitative trait loci in rice by whole genome resequencing of DNA from two bulked populations</a>[J]. The Plant journal, 2013, 74(1):174-183.</p>
<h2 id="应用范围">应用范围</h2>
<p>并非所有以性状基因定位为目的的研究都可以使用 MBS 作为研究手段，实际上，MBS 对研究对象有一定的要求。</p>
<h3 id="性状类型">性状类型</h3>
<p>根据影响特定性状的位点单一与否，性状在定位群体中产生的分离比例是有不同特点的，准确的分离比信息能够正确引导分析方法的使用。</p>
<p>如果性状在群体中的分布频率不符合以下 2 种的性状类型，很可能是出现了致死、不育等特殊突变，分析风险很大。</p>
<p><strong>质量性状</strong>（Discrete Characters）指属性性状，即能观察而不能量测的性状，是指同一种性状的不同表现型之间不存在连续性的数量变化，而呈现质的中断性变化的那些性状。单基因遗传的性状也称质量性状。质量性状受遗传基因支配，较稳定，呈不连续分布。比如说某种抗性的有无，叶片颜色的不同等。</p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/%E5%9B%BE%E7%89%87%201.png" alt="图片 1"></p>
<p><strong>数量性状</strong>（Quantitative Characters）指在一个群体内的各个体间表现为连续变异的性状，如动植物的高度或长度等。数量性状较易受环境的影响，在一个群体内各个个体的差异一般呈连续的正态分布，难以在个体间明确地分组。数量性状是一个群体内的表现连续变异的性状，一般来说易受环境的影响，呈连续的正态分布。</p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/%E5%9B%BE%E7%89%87%202.png" alt="图片 2"></p>
<h3 id="定位群体">定位群体</h3>
<p>每个物种都具有众多性状，为了对感兴趣的特定性状进行分析，通常会利用不同性状品系个体之间的杂交 <sup class="footnote-ref"><a href="#fn11" id="fnref11">11</a></sup> 或自交 <sup class="footnote-ref"><a href="#fn12" id="fnref12">12</a></sup> 将特定性状凸显，形成一个具有某种特定性状或在某个特定性状上具有特殊表现的一群个体，这个过程称为定位群体的构建。</p>
<p>按照不同的分类标准，定位群体可以有非常多的种类。</p>
<h4 id="质量性状">质量性状</h4>
<p>对于质量性状群体的 MBS 来说，大致可以分为以下 5 种情况：</p>
<blockquote>
<ul>
<li>以下 5 幅图中，Ｘ表示杂交；Ⓧ表示自交；红色为分析必须的样品；突变体的突变来源以化学诱变为例，不局限。</li>
<li>这五种情况可简化为杂交、自交、回交 <sup class="footnote-ref"><a href="#fn13" id="fnref13">13</a></sup> 三类</li>
</ul>
</blockquote>
<p><strong>突变体杂交群体：</strong></p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/1.png" alt="1"></p>
<blockquote>
<ul>
<li>优势：定位标记密集，可以估算定位的 Peak（峰值），不受到突变类型的限制。</li>
<li>劣势：对一些 QTL <sup class="footnote-ref"><a href="#fn14" id="fnref14">14</a></sup> 性状受限制，可能不符合 3：1 或 1：2：1 分离比。</li>
<li>若是显性突变，则需要加测“4. 突变亲本”。</li>
</ul>
</blockquote>
<p><strong>自然变异杂交群体</strong></p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/2.png" alt="2"></p>
<blockquote>
<p>自然变异杂交群体中，野生亲本 1 与子代 1、野生亲本 2 与子代 2 表型相互对应。</p>
</blockquote>
<p><strong>突变体回交群体</strong></p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/3.png" alt="3"></p>
<blockquote>
<ul>
<li>回交群体适用于 EMS 诱变突变体，或者找不到合适杂交亲本的其他类型的诱变类型突变体。</li>
<li>优势：EMS 诱变基因快速定位。</li>
<li>劣势：标记少，对于定位的 Peak 值无法准确估算。对于不清楚变异类型的突变体，确定候选基因有一定难度。</li>
<li>若是显性突变，需要对野生亲本和突变亲本都进行测序。</li>
</ul>
</blockquote>
<p><strong>突变体自交群体</strong></p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/4.png" alt="4"></p>
<blockquote>
<ul>
<li>群体：杂合突变亲本，自身后代表型分离。</li>
<li>信号：杂合亲本自身与表型控制基因相互连锁的多态位点。</li>
<li>测序样品：至少两个子代池。</li>
<li>适用范围：表型特别，如致死、不育等。一般情况下我们不建议用自交群体定位，因为遗传背景相对较复杂，连锁图很难做出。所以，这个方法是对一些不好做的材料的方法补充，或者是客户太着急才做的。</li>
<li>若是显性突变，还是测两个子代。</li>
</ul>
</blockquote>
<p><strong>无亲本自交分离群体</strong></p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/5.png" alt="5"></p>
<blockquote>
<ul>
<li>无亲本的自然就只能直接自交了。</li>
<li>对于特殊情况，如显性突变、共显性突变、致死变异、亲本基因型为杂合子、以及动物的MBS等情况具体项目具体分析。</li>
</ul>
</blockquote>
<h4 id="数量性状">数量性状</h4>
<p>QTL-Seq <sup class="footnote-ref"><a href="#fn15" id="fnref15">15</a></sup> 与 MBS 区别：虽然所有性状表型都是受到多个基因控制的，因为都是通过通路和网络来实现功能的，但是我们研究的是在一定的遗传背景和环境条件下，有多少位点引起了表型的变化，那么这时候，一个基因的我们就说是单基因控制，多个的就是多基因控制。单基因控制是 MBS 项目，多基因控制是 QTL-Seq 项目。</p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/6.png" alt="6"></p>
<blockquote>
<ul>
<li>根据测序样品的个数可以分为：双亲本 QTL-Seq 、单亲本 QTL-Seq 和无亲本 QTL-Seq。</li>
<li>极端表型控制一般要求低于两端 10 %。</li>
<li>虽然说是多基因控制，但是如果其中有一个基因主效性极高，也可以近似看作单基因控制，当然这样分析会有风险。</li>
</ul>
</blockquote>
<h3 id="项目一般要求总结">项目一般要求总结</h3>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/7.png" alt="7"></p>
<h2 id="取样">取样</h2>
<p>MBS 一般不采用单株测序，DNA 量 &gt; 2 µg ，若基因组太大则应增加 DNA 量。</p>
<p>**亲本样品：**一般选择直接的杂交亲本测序，无则应选择同一表型的多株亲本型测序。选择与直接亲本世代相近、覆盖整个直接亲本基因库的多个个体，一般 20 - 50 株，等重量组织，一般 200 mg ，组织幼嫩可相对降低量。</p>
<p>**子代样品：**同时考虑基因型鉴定的准确性和个体数量。个体数量不低于 30 株，一般 50 - 100 株，污染率不高于 5 %，一般 200 mg ，组织幼嫩可相对降低量。</p>
<h2 id="几个常见问题">几个常见问题</h2>
<h3 id="野生型亲本是否也需要进行测序？是否也需要混池？">野生型亲本是否也需要进行测序？是否也需要混池？</h3>
<p>在分析过程中，需要进行背景噪声的扣除，因此一般都需要提供野生型亲本的基因型数据。如果能提供构建群体的直接亲本，则无需混池；对于无法明确直接亲本的项目，需要对直接亲本世代相近、覆盖整个亲本基因库的多个个体进行混池。</p>
<h3 id="显性性状能否采用-mbs-来做，如何取材？">显性性状能否采用 MBS 来做，如何取材？</h3>
<p>可以做，一般要同时对 F2 代中 3:1 分离的两种表型分别混池测序，且分离比为 3 的株系我们建议通过F3 代的表型分离来确定 F2 代的基因型，在这里选取 F2 代基因型为纯合系的株系测序。</p>
<h3 id="mbs-混池需要混多少个个体？">MBS 混池需要混多少个个体？</h3>
<p>因为要计算位点的概率，那么理论上当然是混的越多越准，但是实际上不可能无限制的混样，那有没有“性价比”比较高的一个范围？有文章对这方面专门做过研究，结果（示意图见下图）表明，虽然增加每池的样品数确实能够缩小性状基因候选区的范围，但是混样数量的影响力在降低。做质量性状建议混 50 个以上，数量性状建议混 30 个以上。为了缩小定位的区间，混池中的个体越多越好，<strong>前提是个体的表型判别尽可能准确</strong>。另外，对于数量性状，注意单侧极端池个体占总群体比例不超过 10 % 。</p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/8.png" alt="8"></p>
<blockquote>
<p>混池 40 个相对于混池 20 个，候选区缩小了 32 % ；<br>
混池 80 个相对于混池 40 个，候选区缩小了 18 % 。</p>
</blockquote>
<h2 id="报告解读">报告解读</h2>
<p><a href="https://share.weiyun.com/5C0WH3V">报告模板</a></p>
<blockquote>
<p>现在 MBS 的分析报告除 CNV <sup class="footnote-ref"><a href="#fn16" id="fnref16">16</a></sup> 和 SV <sup class="footnote-ref"><a href="#fn17" id="fnref17">17</a></sup> 外的内容都是默认全部提供的。</p>
<blockquote>
<p>只有在性状并非受点突变影响的时候，才会提供 CNV 和 SV 的分析结果以供参考。</p>
</blockquote>
</blockquote>
<h2 id="分析特色">分析特色</h2>
<ul>
<li>与传统的图位克隆相比，耗时短、成本低、定位更准确</li>
<li>根据每个客户的研究目标和内容灵活定制研究方案</li>
<li>除标准 MBS 项目分析内容外，可根据客户需求提供个性化数据分析</li>
<li>已成功完成拟南芥、水稻、玉米等诸多物种突变体定位项目</li>
</ul>
<h2 id="注意事项">注意事项</h2>
<p>在与客户进行沟通时，在技术层面上需要对材料的遗传背景做充分的沟通。</p>
<h3 id="突变来源">突变来源</h3>
<p>客户关注的表型或性状可能是由突变引起的，而不同的突变来源造成的基因组改变的特点是不同的。例如 化学诱变一般是点突变，物理诱变一般是小片段变异等。了解突变来源信息有助于进行针对性的数据处理。</p>
<h3 id="遗传背景是否过于复杂">遗传背景是否过于复杂</h3>
<p>我们曾遇到过一些样本的遗传背景非常复杂、群体构建过程非常“曲折”的项目。以常见的 EMS 诱变株性状基因定位为例，如果客户在进行EMS诱变前后，还进行过 T-DNA 插入、与其他品种植株杂交，甚至进行了更多影响基因组结构的实验操作，那么我们在绘制连锁图寻找与性状有关的连锁峰时，就会看到各种各样非常奇怪的现象，可能会到处都是峰，可能出现很多负向峰，可能会出现很多空白片段（没有突变位点）等。</p>
<p>在做分析时遇到这样的情况，就必须和客户重新、从头沟通整个遗传背景，包括群体的构建；需要从客户最原始的样本来源开始，梳理出整个得到我们进行测序的样本的完整过程，才能具体分析是什么原因造成了定位图异常、并找到可行的解决办法，从而有可能利用已有的数据完成候选基因的定位。</p>
<h3 id="基因组倍性">基因组倍性</h3>
<p>目前多倍体基因组的分析方法还不成熟，所以目前 MBS 项目仅限 2 倍体物种。</p>
<blockquote>
<p>除非该物种有 2 倍体参考基因组，分析部评估该物种可以尝试使用 2 倍体参考基因组进行分析，且客户对风险完全知悉并同意执行。</p>
</blockquote>
<h3 id="物种">物种</h3>
<p>具有参考基因组且易于构建家系的物种。</p>
<h2 id="成功案例">成功案例</h2>
<p>已成熟运用 MBS 技术进行诸多物种的性状基因定位，如：白菜，辣椒，水稻，拟南芥，玉米，黄瓜，番茄等。</p>
<p>也成功运用于一些特殊遗传背景或特殊需求的性状基因定位，例如：</p>
<ul>
<li>由于 T-DNA 插入，导致部分染色体片段拷贝，造成的表型</li>
</ul>
<blockquote>
<p>T-DNA 插入（或转基因）有可能会在连锁定位图上显示出和标准 MBS 项目类似的连锁峰，从而能够确定定位区间，但大多数情况下，会造成连锁定位图异常，不能直接找到定位区间，需要先找到 T-DNA 插入的位置，再做具体分析，而不能使用标准的 MBS 分析流程。</p>
</blockquote>
<ul>
<li>致死突变</li>
</ul>
<blockquote>
<p>原本 MBS 项目会根据群体中表型的分离比来对 SNP&amp;InDel 频率的筛选参数进行调整，但是一旦出现致死突变，那么会造成子代表型统计失真，不能根据测序结果得到的突变频率直接进行分析，必须通过其他手段（例如根据子代母本的表型）推测子代的情况，且在测序结果中得到验证后，才能继续进行分析，不能使用标准的 MBS 分析流程。</p>
</blockquote>
<ul>
<li>3 个基因控制的质量性状</li>
</ul>
<blockquote>
<p>会导致基因组上的连锁情况复杂化，且可能导致连锁定位图峰值不明显，对连锁区间的定位产生干扰，不能使用标准的 MBS 分析流程。</p>
</blockquote>
<ul>
<li>筛选 CNV 和 SV 的差异</li>
</ul>
<blockquote>
<p>某些特殊情况的样本（例如经过物理诱变）突变表型的诱因可能不是点突变造成（即不是 SNP&amp;InDel 造成），而是大片段的基因组结构变异造成（如 CNV 或 SV），然而 MBS 技术使用二代测序获得数据，对于大片段的变异本身检测效率就不高；我们尝试了数十种相关分析的软件、算法，利用项目现有的数据，成功对一些 CNV 或 SV 造成的表型变异候选基因进行了定位。</p>
</blockquote>
<h3 id="mbs-优秀案例">MBS 优秀案例</h3>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/MBS%E4%BC%98%E7%A7%80%E6%A1%88%E4%BE%8B-%E5%AE%A3%E4%BC%A0-%E7%AB%96.png" alt="MBS 优秀案例"></p>
<h3 id="已发表客户文章">已发表客户文章</h3>
<p>Yaobin Q, Peng C, Yichen C, et al. <a href="https://www.sciencedirect.com/science/article/pii/S1672630818300180">QTL-Seq Identified a Major QTL for Grain Length and Weight in Rice Using Near Isogenic F2 Population</a>. Rice Sci 2018; 25(3): 121-131.</p>
<blockquote>
<p>单位：中国水稻研究所<br>
第一作者：Yaobin Qin<br>
通讯作者：宋献军(中科院-植物所)、应杰政<br>
物种：水稻<br>
日期：2018-04-12<br>
明确提到欧易</p>
</blockquote>
<p>Liu C, Zheng S, Gui J, et al. <a href="https://www.sciencedirect.com/science/article/pii/S167420521730374X">Shortened Basal Internodes Encodes a Gibberellin 2-Oxidase and Contributes to Lodging Resistance in Rice</a>. Mol Plant 2018; 11(2): 288-299. (IF: 8.827).</p>
<blockquote>
<p>单位：中科院-植生所<br>
第一作者：Chang Liu<br>
通讯作者：杨远柱(隆平高科)、李来庚<br>
物种：水稻<br>
IF：8.827<br>
日期：2017-12-15<br>
明确提到欧易</p>
</blockquote>
<p>Wang N, Liu Z, Zhang Y, et al. <a href="https://link.springer.com/article/10.1007%2Fs00122-017-3028-8">Identification and fine mapping of a stay-green gene (Brnye1) in pakchoi (Brassica campestris L. ssp. chinensis)</a>. Theor Appl Genet 2018; 131(3): 673-684. (IF: 4.132).</p>
<blockquote>
<p>单位：沈阳农业大学<br>
第一作者：王楠、刘志勇<br>
通讯作者：冯辉<br>
物种：白菜<br>
IF：4.132<br>
日期：2017-12-05<br>
明确提到欧易</p>
</blockquote>
<h3 id="文献案例">文献案例</h3>
<h4 id="质量性状定位：mbs-加速水稻耐盐新品种培育">质量性状定位：MBS 加速水稻耐盐新品种培育</h4>
<p>研究背景：</p>
<p>2011 年，地震和海啸导致日本大面积的稻田被海水污染，日本地方水稻品种 Hitomebore 口感优良、产量高、但不具备耐盐性，无法适应骤然上升的高盐环境，急需培育 Hitomebore 的耐盐品种。如果采用传统育种需要至少 10 年时间。</p>
<p>研究内容：</p>
<p>本文对 EMS 诱变的 Hitomebore 突变品系进行筛选，获得一个耐盐的突变株 <em>hst1</em> ，对 <em>hst1</em> 和野生型 Hitomebore 杂交构建 F2 分离群体。基于 MBS 的策略，对 F2 代中具有耐盐性的 20 株个体混池与野生型亲本同时进行基因组重测序，通过 Mutmap 分析方法鉴别到发生非同义突变的基因 <em>OsRR22</em> ，并通过等位基因突变体的杂交试验确认该基因是控制水稻耐盐性状的关键基因。以 <em>hst1</em> 为基础，通过与 Hitomebore 株系杂交，仅用两年的时间培育出了水稻耐盐品种 Kaijin ，该品种既有突变体 <em>hst1</em> 的高耐盐性，又保留了 Hitome-bore 株系的优良性状。</p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-10-15%2013.38.59.png" alt="屏幕快照 2018-10-15 13.38.59"></p>
<p>研究结果：</p>
<p>● 1. EMS 诱变筛选耐盐突变体</p>
<p>对野生型 Hitomebore 株系进行 EMS 诱变，从 6000 株突变体中筛选到能耐受 1.5 % 的 NaCl 浓度的水稻突变体 <em>hst1</em> 。</p>
<p>● 2. MBS 策略定位候选基因</p>
<p>将 <em>hst1</em> 株系和野生型 Hitomebore 株系杂交，F1 代株系再进行自交获得 F2 代分离群体。对 F2 耐盐性个体 20 株混池进行基因组重测序 ，同时测序野生型亲本。利用 Mutmap 分析软件鉴别 SNP-Index 差异最为显著的区域，将耐盐性状定位到 6 号染色体上 2.76 Mb - 8.57 Mb 区间。在该候选区间内， <em>OsRR22</em> 基因发生了终止突变，编码色氨酸 TGG 突变成终止子 TAG ，可能是导致耐盐性状的候选基因。</p>
<p>● 3. 候选基因的验证</p>
<p>在 <em>Tos17</em> 转座子插入突变库中筛选 <em>OsRR22</em> 基因的等位基因突变体（NE0017 和 NF6804），NF6804 突变株自交纯合子代、<em>hst1</em> 和 NE0017 杂交 F1 代株系同样具有盐度耐受。</p>
<p>● 4. <em>hst1</em> 表型验证</p>
<p>通过表型观察和转录组测序，发现突变体hst1产量、品质、株高、花序数及大小都与 Hitomebore 株系无差异。</p>
<p>● 5. 耐盐品种 Kaijin 的培育</p>
<p>从实际应用角度考虑，以耐盐突变体 <em>hst1</em> 与 Hitomebore 株系杂交，最终培育出耐盐品种 Kaijin ，该品种既有突变体 <em>hst1</em> 的高耐盐性，又保留了 Hitomebore 株系的优良性状。整个新品种培育过程只需两年时间。</p>
<h4 id="数量性状定位：qtl-seq-进行鹰嘴豆粒重主效基因定位">数量性状定位：QTL-Seq 进行鹰嘴豆粒重主效基因定位</h4>
<p>研究背景 ：</p>
<p>鹰嘴豆是重要的粮食作物，提高其总产量、单产量具有重要的经济与社会价值。鹰嘴豆的百粒重常被视为衡量其单产量的一个重要性状，但决定百粒重的 QTL 基因尚未经充分报道。传统 QTL 定位主要采用基于分子标记的图位克隆，费时费力，特别是对于分子标记数量有限的鹰嘴豆实现 QTL 的精细定位更为困难。</p>
<p>研究内容 ：</p>
<p>本研究对鹰嘴豆粒重差异明显的两个亲本杂交所产生的 F4 代分离群体，分别对分离群体的粒重极端个体混合成池，与杂交亲本同时进行基因组重测序。采用 QTL-Seq 分析方法，筛选与粒重性状相关的基因组区域，在 1 号染色体上定位一个主效 QTL（<em>CaqSW1.1</em>），并结合传统的 QTL 定位方式将该主效 QTL 区间缩小到包含 6 个基因的 35 Kb 范围内。对这 6 个基因的 RT-PCR 定量显示，其中的 <em>CSN8</em> 基因在种子中特异性表达，并且表达量在两个极端池中存在差异。</p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-10-15%2013.50.51.png" alt="屏幕快照 2018-10-15 13.50.51"></p>
<p><img src="http://p5o85qxhq.bkt.clouddn.com/%E5%B1%8F%E5%B9%95%E5%BF%AB%E7%85%A7%202018-10-15%2013.51.06.png" alt="屏幕快照 2018-10-15 13.51.06"></p>
<p>研究结果 ：</p>
<p>● 1、QTL-Seq 定位：低粒重与高粒重亲本杂交，单粒传获得 F4 代分离群体，测定百粒重，根据性状的分布，选择粒重最低和最高的 10 株，分别混合成池进行基因组重测序，同时测序杂交的两个亲本。结合 QTL-Seq 分析方法，计算两个极端池间的 ΔSNP-index ，在 1 号染色体前端定位到一个区间大小约为 35 Kb 的主效 QTL ，该区间共包含 6 个基因。</p>
<p>● 2. 传统 QTL 定位验证：基于传统的 QLT 定位，利用 1 号染色体上 95 个多态性标记同样将粒重的主效 QTL 定位在1号染色体相同位置。</p>
<p>与传统 QTL 定位结果相比，QTL-Seq 定位结果更为精确（ 1.8 cM vs 0.6 cM）。</p>
<p>● 3. 候选区间基因功能验证：通过 RT-PCR 对 6 个候选基因分别在粒重高、低植株的叶片和种子中进行基因表达量的测定，结果显示， <em>CSN8</em> 基因在种子中特异性表达，并且在高粒重的植株中表达量显著上升。</p>
<h3 id="更多内容">更多内容</h3>
<p>可在欧易生物微信公众号搜索包含关键字“功能基因筛选干货系列”、“MBS”、“BSA”的文章，有更多原理和案例解析。</p>
<h2 id="名词解释">名词解释</h2>
<hr class="footnotes-sep">
<section class="footnotes">
<ol class="footnotes-list">
<li id="fn1" class="footnote-item"><p><strong>MBS</strong>（Mapping By Sequencing）：可以这样理解：MBS 特指使用测序技术获得数据并进行数据分析的方法来获得分子标记的 BSA，主要利用了 BSA 凸显性状相关突变位点的策略并与测序数据分析相结合；分析手段与 BSA 有差别，群体构建策略、取样策略、分析目的与 BSA 一致。 <a href="#fnref1" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn2" class="footnote-item"><p><strong>BSA</strong>（Bulked Segregant Analysis）：称为混合分组分析法，是一种利用极端性状进行性状连锁分子标记定位的一种方法。主要比较两组具有极端性状的群体在多态位点（SNP）的等位基因频率 <sup class="footnote-ref"><a href="#fn18" id="fnref18">18</a></sup> 是否具有显著差异，即而将目标性状相关的分子标记定位在特定染色体区段上。传统 BSA 分析样本 DNA 的方法有 Southern Blotting ，基于 PCR 的 RFLP、RAPD 等。BSA法克服了很多作物难以得到近等基因系的限制，并且比近等基因系法省时省力，是一种非常实用的基因标记定位的方法，应用非常广泛。 <a href="#fnref2" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn3" class="footnote-item"><p><strong>WGS</strong>（Whole Genome Resequencing）：全基因组重测序是对已知基因组序列的物种进行不同个体的基因组测序，并在此基础上对个体或群体进行差异性分析。 <a href="#fnref3" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn4" class="footnote-item"><p><strong>SNV</strong>（Single Nucleotide Variation）：单核苷酸变异主要是指在基因组水平上由单个核苷酸的变异所引起的DNA序列变异。在这篇文档中，我们说的<code>突变位点</code>指的是<code>点突变</code>，也就是<code>SNP</code>或<code>InDel</code>。 <a href="#fnref4" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn5" class="footnote-item"><p><strong>SNP</strong>（Single Nucleotide Polymorphism）：单核苷酸多态性，即单个碱基的改变。 <a href="#fnref5" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn6" class="footnote-item"><p><strong>InDel</strong>（Insert or Deletion）：单个碱基的插入或缺失；存在较长的 InDel，但大多只有几个 bp 的长度差异。 <a href="#fnref6" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn7" class="footnote-item"><p><strong>Trait；Character</strong>（性状）：指可遗传的发育个体和全面发育个体所能观察到的(表型的)特征，包括生化特性、细胞形态或动态过程、解剖构造、器官功能或精神特性总和。任何生物都有许许多多性状。有的是形态特征（如豌豆种子的颜色，形状），有的是生理特征（如人的ABO血型，植物的抗病性，耐寒性），有的是行为方式（如狗的攻击性，服从性），等等。在孟德尔以后的遗传学中把作为表型的显示的各种遗传性质称为性状。在诸多性状中只着眼于一个性状即单位性状以进行遗传学分析，已成一种遗传学研究中的常规手段。 <a href="#fnref7" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn8" class="footnote-item"><p><strong>Linkage</strong>（连锁）：某些基因组区域由于位于相同的染色体上且在一起遗传，被称为连锁。MBS 属于连锁分析。 <a href="#fnref8" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn9" class="footnote-item"><p><strong>SNP-index</strong>：是一个与 SNP 位点测序深度相关的参数，该参数是指子代某个位点含有突变亲本来源 SNP 的 Reads 数与测到该位点的总 Reads 数的比值，大小范围为 0-1 。若该参数为 0 ，代表子代所有测到的 Reads 都来野生亲本；若该参数为 1 ，代表子代所有 Reads 都来自突变亲本；该参数为 0.5 ，则代表此子代混池中 SNP 来自两个亲本的基因组的频率一致。 <a href="#fnref9" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn10" class="footnote-item"><p><strong>Founder Effect</strong>（奠基者效应）：是遗传漂变 <sup class="footnote-ref"><a href="#fn19" id="fnref19">19</a></sup> 的一种形式，是由少数个体的基因频率决定了他们后代中的基因频率的效应，是一种为数不多的几个个体所建立起来的新群体所产生的一种极端的遗传漂变作用。 <a href="#fnref10" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn11" class="footnote-item"><p><strong>Hybridization；Cross；Crossing</strong>（杂交）：两条单链DNA或RNA的碱基配对。遗传学中经典的也是常用的实验方法。通过不同的基因型的个体之间的交配而取得某些双亲基因重新组合的个体的方法。一般情况下，把通过生殖细胞相互融合而达到这一目的过程称为杂交。 <a href="#fnref11" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn12" class="footnote-item"><p><strong>Inbred；Self</strong>（自交）：指来自同一个体的雌雄配子的结合或具有相同基因型个体间的交配或来自同一无性繁殖系的个体间的交配。显花植物雌雄同株十分普遍，因此，自交也很普遍。 <a href="#fnref12" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn13" class="footnote-item"><p><strong>Back Cross</strong>（回交）：对于性状遗传的研究具有重要意义，特别是用隐性亲本进行回交，是检验子一代基因型的重要方法（实为测交）以及获得隐性（重要或稀有基因）纯合的后代的重要方法。子一代和两个亲本的任一个进行杂交的方法叫做回交。在育种工作中，常利用回交的方法来加强杂种个体中某一亲本的性状表现。用回交方法所产生的后代称为回交杂种。被用来回交的亲本称为轮回亲本，未被用来回交的亲本称为非轮回亲本。 <a href="#fnref13" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn14" class="footnote-item"><p><strong>QTL</strong>（Quantitative Trail Loci）：数量性状位点。分离群体表型分布符合连续分布、正态分布或近似正态分布。 <a href="#fnref14" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn15" class="footnote-item"><p><strong>QTL-Seq</strong>（Quantitative Trail Loci sequencing）：数量性状位点测序分析，针对数量性状多位点分离群体。 <a href="#fnref15" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn16" class="footnote-item"><p><strong>CNV</strong>（Copy Number Variation）：拷贝数变异是由基因组发生重排而导致的, 一般指长度为 1 kb 以上的基因。 <a href="#fnref16" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn17" class="footnote-item"><p><strong>SV</strong>（Structure Variation）：主要指染色体结构变异，一般是内因和外因共同作用的结果，外因有各种射线、化学药剂、温度的剧变等，内因有生物体内代谢过程的失调、衰老等。主要类型有缺失、重复、倒位、易位。 <a href="#fnref17" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn18" class="footnote-item"><p><strong>AF</strong>（Allele Frequency）：在利用二代测序进行的数据分析过程中，用在同一位点检测到的不同碱基的占比作为该位点的等位基因频率。 <a href="#fnref18" class="footnote-backref">↩︎</a></p>
</li>
<li id="fn19" class="footnote-item"><p><strong>Genetic Drift</strong>（遗传漂变）：遗传漂变是小的群体中，由于不同基因型个体生育的子代个体数有所变动而导致基因频率的随机波动称为遗传漂变。群体中，不同基因型个体所生子女数目不尽相同，致使子代的等位基因数发生改变，在处于相对隔离状态的小群体中会产生基因频率的随机波动。如某基因座上有 A，B 两个等位基因，假设 A 基因频率占优而 B 等位基因罕见，即携带 B 等位基因的个体很少，若这些个体无子女，则 B 基因在子代中便会消失。遗传漂变的结果也可使一些基因的频率升高。 <a href="#fnref19" class="footnote-backref">↩︎</a></p>
</li>
</ol>
</section>

    </div>
  </div>
</body>

</html>
