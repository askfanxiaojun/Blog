中金 \| AI十年展望（十六）：成本决定落地节奏，大模型轻量化、线性化趋势渐起
========================================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/u1xcYqSldxUzTAizJyMGTg)于钟海 魏鹳霏等 中金点睛

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FfzHRVN3sYsicmoVBv4D0mPib68kWJVkDjnEM91ZO46IRCPDfIfFpMEn2BoxwUa2fguPicQ4WwvNibdnOL4IqZj4XTA%2F640%3Fwx_fmt%3Dgif)

**文/于钟海 ,魏鹳霏 ,王之昊 ,游航**


**中金研究**


2023年ChatGPT引领产业界高度重视，产业落地节奏成为核心关注点。我们于2021年在《[人工智能十年展望（二）](http://mp.weixin.qq.com/s?__biz=MzI3MDMzMjg0MA==&mid=2247547307&idx=1&sn=00d20841f86a365cce43e0619fb77181&chksm=ead0df6cdda7567aa3e12edb24cf339d283fe0fc484f4c88dd5cafb8047a2914b00ff3c05a4c&scene=21#wechat_redirect)》提出边际成本决定竞争力，并提出大模型的泛化能力有望从算法侧解决这一问题。即便如此，在产业趋势起点，我们看到海外WAU\~1,000万的应用Perplexity基于微调GPT-3.5的算法成本约为4,500万美元/年；国内智谱GLM-4的API调用价格约为50元/百万中文字符，成本依然是阻碍应用落地的核心矛盾。**我们持续看好Transformer之外的模型轻量化、线性化的应用前景，将在本文对两大趋势进行探讨，有望为模型降本、应用落地、端侧部署带来新的可能。**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_gif%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAa5nWIB2zCSyBaspAozzUdgns7fYYrh1QB4VveTA2yYhvKFbQHYCQMA%2F640%3Fwx_fmt%3Dgif%26from%3Dappmsg)


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAzficcibpf3BYicceGpAs89gYQOZKtjXLyH0hI010Ml20ZnZ6FYBmj6SEQ%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)

**[点击小程序查看报告原文]()**


**Abstract**


**摘要**


**算法框架革新为AI应用降本、大规模落地的有效路径。**算力成本在摩尔定律指引下具备下降趋势外，如何在保证性能的同时降低成本，是AI大规模落地的首要问题。轻量化和线性化以不同思路显著提升计算效率，为算法革新提供思路，我们认为有望以降低成本逻辑打开AI应用普及天花板。

**► 轻量化：以小型化为基，混合专家模型（MoE）为主流路线，通过稀疏化优化性能与计算效率。**小型化模型以Mistral-7B、Gemini Nano、面壁MiniCPM、Gemma为代表，基于十亿级参数量，通过高质量AI基础设施、高效训练方法与优质数据集优化模型性能，降低大模型的使用门槛。MoE在模型小型化基础上兼具灵活性与准确性，以激活部分参数的稀疏特点提升推理速度，进一步降低模型成本。Mixtral 8\*7B以12.9B推理参数量达到媲美GPT-3.5的性能，Gemini 1.5 Pro性能对标Gemini 1.0 Ultra，验证了MoE的潜力。

**► 线性化：兼具RNN与Transformer优势，或为大模型时代下的降本破局之道。**循环神经网络（RNN）将历史序列信息压缩至固定大小的隐藏状态中，具有线性复杂度，但具备无法并行训练的明显不足；Transformer模型引入自注意力机制，具有二次方的推理复杂度，计算成本较高。在此背景下，线性化路径取二者优势，衍生出线性注意力方法与选择性状态空间方法，代表模型为RWKV、RetNet与Mamba，即通过压缩上下文信息实现线性复杂度、并结合Transformer并行训练，显著提升训练效率、压缩落地成本，我们认为线性化路径对大模型的端侧落地及广泛应用具有重要意义。


**风险**


算法落地过程中的内存、微调挑战，提示工程依赖度提升。


**Text**


**正文**


**总览：模型轻量化、线性化为算法降本带来新机遇**


**产业视角：算法边际成本高阻碍产业落地，框架革新注入新可能**


**Transformer为大模型的主流架构，边际成本是大模型落地的一大痛点。** 2017年，Transformer模型的发布打破了循环神经网络（RNN）的统治地位，凭借其强大的语言理解能力在自然语言处理、图像处理等领域得到了学术界广泛共识。目前，各厂商的均脱胎于Transformer架构开发预训练大语言模型，千亿级参数为其带来性能跃迁，但训练和推理时需要充分的算力资源。此外，Transformer模型架构中核心的注意力机制意味着计算复杂度随序列长度增加呈二次方增长。**算力成本在摩尔定律指引下具备下降趋势之外，如何在保证性能的同时降低算法的边际成本，是AI大规模落地的首要问题。**

**轻量化和线性化以不同思路显著提升计算效率，为算法框架革新的两条有效路径。** AI应用的普及一定程度上需要以逆向思维，即大模型小型化，来降低训练与推理成本。2020年以GPT-3为代表的大模型路径彰显出优越性能以来，全球的研究人员持续对底层算法框架进行革新，轻量化和线性化为两大研究方向。其中，**1）轻量化** 以Mixtral 8\*7B模型为代表，其核心思路是采用混合专家模型，架构中基于多个专家并行机制，推理时只激活部分专家，以稀疏性压缩了参数数量和推理成本；**2）线性化**则包含线性注意力与选择性状态空间模型两种方法，分别以RWKV、RetNet及Mamba模型为代表，模型性能较优且推理复杂度从二次方降为线性增长。我们认为轻量化及线性化路径有望为大模型广泛落地、实现端侧部署提供重要启示。


**学界视角：轻量化与线性化模型尚有改进空间，发展前景可期**


**轻量化：Mixtral 8\*7B模型性能比肩GPT-3.5，更大参数量下有望实现性能突破。**轻量化首先基于模型小型化基础，即以十亿级别参数量训练更大体量数据。混合专家模型（MoE）最早可追溯至1991年，此后与主流算法框架持续融合迭代，当前发展较为成熟。Mixtral 8\*7B以46.7B的总参数量与12.9B的推理参数量实现了与GPT-3.5比肩的优越性能，充分展现了模型轻量化的潜力，我们认为随着参数规模的逐渐扩大，MoE有望实现性能突破。但同时，MoE具有占用较大内存、微调时易出现过拟合的现象，学术界尚亟待进一步解决。

**线性化：融合RNN路径思路，性能可达到类似规模的Transformer架构模型，兼具速度与成本优势。**Transformer架构模型在推理时与上下文内容进行逐字对比，而线性化模型对前文信息进行了压缩，实现了复杂度线性化，意味着更快的推理速度和更低的计算成本。然而面对细节问题时，线性化路径与RNN具备类似的不足，削弱了模型回望之前信息的能力，其表现较Transformer模型可能具备一定差异。

**大模型趋势下降本道阻且长，轻量化与线性化提供丰富想象力。**当下所有的开发生态均围绕Transformer架构展开，模型部署成本下降为重要课题，轻量化和线性化为大模型落地提供了其他可能，我们认为以上技术趋势值得关注，有望打开大模型应用普及的天花板。


**模型轻量化：MoE为基本路线，大模型降本新方向**


**模型小型化：压缩参数数量，以高效训模方法和优质数据扩展性能**


当下，大模型成为各家科技公司的必争之地，国内外大模型持续涌现，一大特点就是愈来愈多的参数数量和更为优越的模型性能。但与此同时，Mistral AI、谷歌、面壁智能等厂商另辟蹊径，聚焦于小型化的技术路线，开发出Mistral-7B、Gemini Nano、面壁MiniCPM等模型，通过高质量AI技术设施、高效训练方法与优质数据集探索十亿级参数量下的模型性能极限。**小型化基于十亿级别参数量，通过架构调整训练更大体量数据，从而实现匹敌千亿级参数的模型效果。小型化意味着更低的使用成本和部署门槛，部分模型甚至可以在手机等终端设备使用，拓宽了大模型的赋能场景，商业意义显著。**


图表1：在多个测试集上，Mistral 7B的表现均优于LLaMA2 13B、LLaMA 34B模型


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAR1iaoiaU1dRric3iciaPqve0I73Msfo7ibEypcibFrGvc12n1KngouStibCuoQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFATH86kd4cPDlMSrbtDuyibXpTmhVkosO5AGicHy6iaJyv2jav4SdbCicaUA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Jiang, Albert Qiaochu et al. "Mistral 7B." ArXiv abs/2310.06825 (2023): n. pag.，中金公司研究部


**混合专家模型（MoE）：以稀疏化分而治之，实现计算效率优化**


**混合专家模型（MoE）的基本思想是将输入数据进行拆解并分配给不同专家进行处理，以稀疏性提升模型的整体性能。**在谷歌的Switch Transformer论文中1，研究人员将MoE思想与Transformer模型融合，由MoE层替换Transformer模型中的前馈神经网络（FFN）层，FFN层原本旨在对输入序列进行非线性变换以捕捉复杂特征，该步替换大幅提高了计算效率和模型性能。MoE模型主要由两个核心部分组成，即门控模型和专家模型：

**►门控模型 / 路由（Gating Network / Router）：**门控模型的作用是决定任意token被发送到哪个/哪些个专家进行处理。在下图示例中，"More"被发送到第二个专家，而"Parameters"被发送到第一个专家。输入数据后，门控模型接收数据并输出权重，衡量每个专家处理输入数据的贡献程度。若某个专家的权重为0，则表明其不参与该token的计算操作。

**►专家模型（Experts）：**每个专家模型都是一个独立的神经网络，处理输入数据产生输出，并根据门控模型计算出的权重进行加权组合，生成最终结果。Switch Transformer论文中，共有四个专家模型，门控模型选择一个专家进行处理。


图表2：Switch Transformer论文中的MoE架构


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAfOCiaM8KrhSiccDIu7OeruDhIpoHaDuWR2PjoicxJF7iaBmVy6eVaPcyPA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Fedus, William et al. "Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity." J. Mach. Learn. Res. 23 (2021): 120:1-120:39.，中金公司研究部


**混合专家模型充分汲取不同专家的优势，兼具准确性与灵活性。**MoE架构中，每个专家都是独立的神经网络，能够基于不同数据或领域进行训练，以针对性处理任务的不同部分。此外，门控网络可以根据任务需要激活效果最佳的专家模型，满足多个任务场景。混合专家模型既能结合多个专家的优势解决问题，又能实现对输入数据的灵活处理，面对复杂任务时具备准确性与灵活性的特点。


图表3：不同专家对多元化任务进行针对性处理


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAQUHK9MATib0mibZOhZuScGv43QbZe16KtjC6fvPSCQvCacII4HFMDs3w%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Mustafa, Basil et al. "Multimodal Contrastive Learning with LIMoE: the Language-Image Mixture of Experts." ArXiv abs/2206.02770 (2022): n. pag.，中金公司研究部


**稀疏性赋予混合专家模型更快的预训练速度与推理速度。**在传统的稠密模型中，模型通常为输入复用所有参数。但混合专家模型根据输入数据的特点只激活部分专家对输入进行处理，大多数专家包含的参数并未被调用，从而实现稀疏性。MoE模型调用部分专家的稀疏性使其计算效率大幅提升，预训练与推理均能以更快的速度完成。例如，在相同的训练效果下，Switch Transformer模型的训练速度相较于稠密模型T5提升了7倍。

**与相同参数量的稠密模型相比，混合专家模型的训练及推理算力成本更低，有望驱动大模型普惠发展。**训练阶段，算力取决于参数数量、训练数据集的大小、训练轮次与批次大小。MoE模型的稀疏性使得训练过程中调用的参数量减少，算力成本随之下降，模型厂商在一定的预算条件下可以显著增加参数规模并提升模型性能。谷歌的GLaM模型包含12,000亿参数，大约是GPT-3参数量的7倍，但其训练成本仅为GPT-3的40%。推理阶段，MoE模型激活部分参数进行预测，公有API调用及私有模型部署两种方式下，AI应用厂商成本均有所下降。我们认为，MoE有望降低应用成本，使大模型的普惠发展成为可能。


图表4：MoE架构下模型训练速度提高7倍


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFA0y35Iic0D2ITX0GIQ6WFicXmiae04qMrnf2nMOyiaG28BBjDeibuL8Qe8Xw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：1）32e、64e、128e分别表示32、64与128个专家；2）T5为稠密模型  
资料来源：Fedus, William et al. "Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity." J. Mach. Learn. Res. 23 (2021): 120:1-120:39.，中金公司研究部


图表5：谷歌GLaM与GPT-3的推理成本（左）和训练能耗（右）对比


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAnUk48ouO8aMrib4fpgpVhWMtqxgaLnE54rNlSmGBl3xZcyMqLw2iaW0w%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：1）GLaM模型为MoE模型，GPT-3为稠密模型  
资料来源：Du, Nan et al. "GLaM: Efficient Scaling of Language Models with Mixture-of-Experts." ArXiv abs/2112.06905 (2021): n. pag.，中金公司研究部


**不足及未来方向探讨**


**混合专家模型面临内存及微调挑战。**1）内存挑战：虽然在预训练和推理过程中只使用模型中的部分参数，但MoE模型包含多个专家模型和门控网络，需要将所有参数都加载到内存中，对VRAM的要求比较高。2）微调挑战：稀疏模型通常存在众多参数，大量的参数数量可能导致模型学习训练数据的细节性特征，甚至用于拟合训练数据中的噪声，从而对训练数据的变化较为敏感。因此混合专家模型面临泛化能力不足的问题，容易导致过拟合现象。此外，完全微调MoE架构意味着更新所有参数，仍然需要大量计算资源。在实践过程中，可以使用权重衰减、使用更高比例的dropout等正则化技术减少参数数量，减轻模型的过拟合风险。

**稀疏MoE的蒸馏与MoE的量化为前沿探索方向。**首先，可以考虑从稀疏混合专家模型蒸馏得到具备更少参数总量但实际参数量近似的稠密模型。蒸馏过程可以提取原始MoE模型中的知识，保留原有的模型性能，同时提高模型的内存效率并优化泛化能力。其次，MoE的量化也是一个新颖的研究领域。2023年10月，来自奥地利科技学院（ISTA）的研究人员提出一种全新的模型量化方法QMoE\[1\]，在轻微精度损失的情况下将1.6万亿参数的Switch Transformer模型所需的存储从3.2TB压缩至160GB，解决了MoE面临的内存挑战。


图表6：混合专家模型总结


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFA3wHFqteU5tHpFxzial7wk2qPSs8zYVY7gDlfvhBRmfHmpboU7iaC7H8g%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：中金公司研究部


**模型线性化：降低模型落地成本的探路者，兼具Transformer与RNN模型优势**


**线性化：主流路径从RNN到Transformer，线性化兼收并蓄**


**RNN将序列信息压缩至隐藏状态，复杂度低但无法并行训练。**循环神经网络（RNN）与人类的语言理解逻辑类似，注重上下文的顺序及逻辑关系。RNN将历史序列信息压缩到固定大小的隐藏状态中，输入序列的每一项时更新隐藏状态，模型从输入和上步隐藏状态中提取信息并输出权重。虽然这种方法具有线性复杂度，但对前步结果的依赖限制了模型的可扩展性，使得RNN无法并行训练，且在长序列时存在梯度消失现象。

**Transformer模型引入自注意力机制，性能较为优越，2020年以来成为主流路径，但计算成本较高。**Transformer模型的核心为自注意力机制，使得模型自主学习输入序列中不同位置之间的依赖关系，对上下文内容完全没有压缩，但每次推理时都需要跟上下文进行比较，因此具有二次复杂度，且在长序列任务中计算成本高、占用内存多。

**线性化模型兼具RNN与Transformer模型优点，存在线性注意力与选择性状态空间模型两种实现路径，或成为大模型背景下的破局之道。**目前，线性化模型的代表为RetNet、RWKV与Mamba，RetNet与RWKV为线性注意力方法，Mamba为选择性状态空间方法。其共同点为通过压缩上下文信息实现线性复杂度，并结合Transformer模型可以并行训练的优势，带来了显著的效率提升、落地成本压缩，对大模型的端侧落地及广泛应用具有重要意义。


图表7：结合RNN、Transformer路径的优势，线性化模型将空间复杂度降低为线性


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAuicGWO7EL4B3b7r5xvzMpDB5M73x04ic76ibdpgReE46HibrBvc1qrNf4w%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：时间及空间复杂度描述中，N代表context长度  
资料来源：机器之心公众号，中金公司研究部


**线性注意力模型：以RWKV和RetNet为例，实现RNN与Transformer思想的有效融合**


**线性注意力的基本思想是将Transformer自注意力机制中的Softmax函数转换为线性表达式，同时引入衰减向量将前步信息压缩为状态矩阵，既能降低计算复杂度，又能保证模型性能。**我们将以RWKV和RetNet为例，对线性注意力的实现方法和效果进行分析。

**RWKV：在Transformer时代重塑RNN，端侧布局的重要参与者**

**非Transformer开源大模型，致力于打造AI时代的开源生态。**RWKV模型由香港大学物理系毕业的彭博开发，截至2024年1月，彭博秉持开源理念将模型迭代至RWKV-6版本。2023年彭博与刘潇、孔晴、罗璇联合成立元始智能，其愿景是成为AI时代的安卓，目前已开展两轮融资。

**改写AFT的线性注意力公式，解决当前架构的局限性。**2021 年，苹果发布《An Attention Free Transformer》，提出一种不需要注意力机制的 Transformer 模型。RWKV的开发者彭博对论文中的公式进行改写，添加时间衰减向量W，将AFT转变为RNN形式，将复杂信息量压缩为1个token加入模型，推理的计算复杂度降为线性增长。同时，RWKV将RNN拆分为多个层级，每层的隐藏状态可以独立用于计算同层的下一个隐藏状态，从而允许模型并行计算，兼具Transformer与RNN的优点。RWKV的模型架构由多个RWKV Block（区块）组成，再由语言建模网络（Language Modeling Head）输出下一个token的分布概率。每个区块内均包含时间、通道混合模块。

**RWKV-5多语言能力超过Mistral，RWKV-6实现再升级。**此前学术界有研究者尝试将Transformer模型改写为RNN架构，皆以性能损失为代价。RWKV不仅避免了性能的损失，还在模型规模扩大时呈现出性能超越Transformer大模型的趋势。RWKV-5"Eagle"7B在仅训练1.1T tokens语料的前提下，多语言能力显著超过现有的同规模主流Transformer模型（包括Mistral-7B），英文能力接近LLaMa2。而RWKV-5在训练过程中并未添加多语言任务数据，模型的多语言能力完全依靠语言间的迁移实现。2024年2月9日，RWKV-6 Finch 1.6B已完成测试并正式开源。相较于RWKV-5，RWKV-6展现出更加强大的多语言能力，数据相同的情况下RWKV-6 在角色扮演方面的表现也更加优越。


图表8：RWKV-6模型表现


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAptnYia6x7zoLUGREdcjvibzYLqiatMM4SVC8iasZoibTNE6RNs6CJYUzy5A%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：RWKV元始智能公众号，中金公司研究部


**推理效率和成本优势显著，成为英特尔、联想、联发科、高通等厂商端侧布局的合作伙伴，大模型端侧落地可期。**复杂度方面，RWKV的累计文本生成时间随序列长度线性增长，而Transformer则呈现平方增长。除性能外，同等参数下RWKV的速度和显存占用较Transformer模型都更为优越。据RWKV元始智能公众号，RWKV模型基于推理效率和成本优势目前已适配多种平台，CPU上支持Intel和AMD，同时正在适配华为Atlas和爱芯元智等厂商。此外，2023年RWKV曾作为英特尔、联想、联发科、高通的端侧模型合作伙伴出席其新品发布会，我们认为未来有望充分释放大模型在PC、手机、汽车等端侧落地的潜力。


图表9：RWKV的文本生成时间呈线性增长，而非二次方增长


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFA5t7chYd2mG16m9SakvfbqhR1OBhXpjgmiacicJ6Eun38MfCASFvyl8FQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Peng, Bo et al. "RWKV: Reinventing RNNs for the Transformer Era." Conference on Empirical Methods in Natural Language Processing (2023)., 中金公司研究部


**RetNet：Transformer的继承和部分替代**

**RetNet引入多尺度保持机制替代标准的自注意力机制，实现递推与分块处理。**与Transformer模型的标准自注意力机制相比，RetNet的保持机制具备以下特点：（1）采用位置相关的指数衰减项代替Softmax函数，简化计算的同时以指数衰减形式保留前步信息；（2）引入复数空间表达位置信息，取代绝对或相对位置编码，容易转换为递归形式；（3）使用多尺度的衰减率增加模型的表达能力，并利用 GroupNorm（组归一化） 的缩放不变性提高数值精度。RetNet共有三种等价形式，分别为并行、循环和分块。


图表10：RetNet的并行结构


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAvu4X1xsybSYWPh7KgISljYiasbibaVGd3iamRKxh1n6fRTNeA8WRREuug%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：Q、K、V分别表示查询（Query）、键值（Key）与内容（Value）；D矩阵表示指数加权方案；"GN"是GroupNorm的缩写。

资料来源：Sun, Yutao et al. "Retentive Network: A Successor to Transformer for Large Language Models." ArXiv abs/2307.08621 (2023): n. pag., 中金公司研究部


图表11：RetNet的循环结构


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAdO2AddZZSlEjjXaZ3IQ8AyB8MxXia47NHjtAb3acJdSylMeIyQBrBTg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：Q、K、V分别表示查询（Query）、键值（Key）与内容（Value）；S表示状态（State）；"GN"是GroupNorm的缩写。

资料来源：Sun, Yutao et al. "Retentive Network: A Successor to Transformer for Large Language Models." ArXiv abs/2307.08621 (2023): n. pag., 中金公司研究部


**在保证模型性能的情况下，RetNet推理速度为Transformer模型的8.4倍，内存占用减少70%，有望降低大模型的使用门槛。**相较于Transformer，RetNet占用的GPU内存减少70%，推理速度高达8.4倍，延迟也大幅下降。在模型性能方面，随着模型参数规模扩大，RetNet的困惑度逐渐下降至低于Transformer。我们认为，RetNet有望在保证性能不弱于 Transformer 的情况下，提升模型运行效率，降低大模型的训练与使用门槛，有效促进大模型在应用层及手机、电脑等终端设备上的发展。


图表12：相较于Transformer，RetNet实现低成本训练和良好性能


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAnPZQSeBA2iaib62eDaHzQauHA5SoKqOksWwica0CiavVtBVKSRBum47Smg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Sun, Yutao et al. "Retentive Network: A Successor to Transformer for Large Language Models." ArXiv abs/2307.08621 (2023): n. pag., 中金公司研究部


**选择性状态空间模型：以Mamba为代表，实现线性复杂度和高吞吐量**


**2023年12月，来自卡内基梅隆大学和普林斯顿大学的学者发布选择性状态空间模型Mamba，可以根据内容动态过滤和处理信息，具有线性扩展的优势\[2\]。**测试显示，Mamba的模型性能与Transformer模型相媲美，同时具有高达5倍的推理吞吐量。

**► 选择机制：**Mamba通过"参数化SSM的输入"设计一个简单的选择机制，使得模型可以过滤掉不相关的信息并永久记住相关信息，可以在固定的状态大小下压缩上下文。

**► 硬件感知算法：**为了保证模型在GPU上的高效运算，论文设计了一种硬件感知算法，通过扫描来计算模型。在更高速的SRAM内存中完成离散化和递归操作后将输出写回HBM，当输入从HBM加载到SRAM时不保存中间状态，而是在反向传播中重新计算。

**► 模型架构：**将此前的状态空间模型架构设计与Transformer的多层感知机模块（该模块主要负责每个位置的特征向量进行非线性变换和组合）进行合并，形成了一种包含选择性状态空间的简单、同质的架构设计。


图表13：随序列长度增加，Mamba与其他模型表现对比


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAVyoQg1UhUNwrMC2a8ojSwZbG95tiaNw6bItvrQUmeSaIXx3rOFKaafg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Gu, Albert and Tri Dao. "Mamba: Linear-Time Sequence Modeling with Selective State Spaces." ArXiv abs/2312.00752 (2023): n. pag., 中金公司研究部


图表14：相较于规模相当的Transformer架构，Mamba具备5倍的吞吐量


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFA5vuWcd0gHdia7ER0TOWCQkjIhkJ0alYDBQzicI0AqXdFlicn4LGP3ibVLw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Gu, Albert and Tri Dao. "Mamba: Linear-Time Sequence Modeling with Selective State Spaces." ArXiv abs/2312.00752 (2023): n. pag., 中金公司研究部


**不足及未来方向探讨**


**线性化路径可能存在丢失细节的缺陷，提示工程或对任务表现更为关键：**

**► 细节丢失问题：**通过前文分析，可知线性化的核心思想是将前文信息压缩为隐状态并进行更新，避免了Transformer模型中保持保留全部信息、与前文逐一对比带来的复杂度问题。但这种压缩的方法可能会限制模型对上下文细节的记忆能力，与完全的自注意力机制相比仍有信息丢失。在实际应用过程中，需要在计算效率和完备信息之间做出权衡。

**► 提示工程的重要性有所增加：**提示词（Prompt）指用户输入给大模型，让其完成特定任务的自然语言文本。大模型生成内容时，会先对输入指示词进行处理，再根据对提示词的理解预测下一个词出现的概率，逐字进行输出。因此，高质量的提示词可以最大化大模型潜力，引导其精确理解任务。线性化限制了前文的信息传递，因此精心设计提示词可能对模型在任务上的表现更加关键。


图表15：模型线性化总结


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFAGwFZfsOXsxVUDzENNEoFW9zbNw0eViazZuFXVMkNsc2Aj5pGNAusmjw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：中金公司研究部


**总结：模型轻量化、线性化对AI行业潜在影响**


**我们认为模型轻量化、线性化趋势在大模型背景下具备重要意义，主要体现在降低算力需求、降低算法成本、释放端侧AI的潜力、加速应用层落地等方面：**

**► 算力层面，模型轻量化及线性化或将缓解推理算力需求：**算力是大模型研发及应用落地的基座，决定模型上限。虽然单个推理场景对计算性能要求较低，但实际应用过程中仍需要基于大量GPU并行计算，我们认为大规模AI应用也有望拉动推理成本指数级提升，从而限制应用层落地。通过轻量化及线性化路径，大模型的推理成本有望下降，对算力的需求或涉及更少数量GPU、甚至CPU主体，例如，RWKV在CPU上支持Intel和AMD，在BF16的新Intel芯片上速度仍然较快。我们认为有望部分抵消推理侧算力供给不足的情况，为AI应用落地打开天花板。

**► 算法层面，成本有望进一步降低，市场份额或向拥有高性能轻量化或线性化模型的厂商集中。**当前主流模型仍为Transformer大模型，轻量化与线性化仍处于探索进步阶段。我们认为，随着轻量化、线性化模型的性能表现与商业化成熟，其成本与计算效率优势将进一步凸显，加速赋能多种应用场景。此外，我们认为拥有高性能轻量化或线性化模型的厂商市场份额也有望提升。

**► 端侧AI视角，短期端侧模型有望基于现有芯片合理利旧，发挥效能；长期或将加速AI PC、AI手机更新换代。短期来看，**Transformer大模型在PC、手机等终端的部署需要依靠高通 X Elite等专用AI芯片实现，唯有换机方能享受AI功能。线性化路径下，大模型可以依靠现有芯片完成端侧落地。我们认为，基于现有端侧芯片，线性化模型有望释放利旧空间，带来端侧AI能力的早期渗透。长期来看，我们认为AI成为PC产品创新驱动力，联想、戴尔、惠普和华硕等PC厂商陆续发布AI PC产品，华为、三星、荣耀等手机厂商纷纷布局AI手机并发布相关产品，模型创新带来的端侧AI能力也有望进一步强化AI PC、AI手机的周期性，加速换机潮的到来。

**► 应用落地视角，我们认为模型轻量化及线性化等趋势有望强化应用层厂商的使用意愿，促进应用层百花齐放。**在AI应用落地的过程中，成本、投入产出比是应用层厂商决策的核心要素。我们认为，模型轻量化、线性化等趋势能够显著降低训练及推理成本，或加速应用层的不断创新和生态繁荣。


**风险提示**


**算法落地过程中的内存、微调挑战。**混合专家模型包含多个专家模型和门控网络，需要将所有参数都加载到内存中，对内存要求较高。此外，对其进行微调将更新所有参数，仍需大量计算资源，面临一定挑战。

**提示工程依赖度提升。**线性化路径通过对上下文信息的压缩避免Transformer模型与前步信息逐步对比所引致的二次复杂度，因此压缩过程中或将根据提示词对重要信息进行过滤，对提示工程的依赖程度有所提升。

\[1\]Frantar, Elias and Dan Alistarh. "QMoE: Practical Sub-1-Bit Compression of Trillion-Parameter Models." ArXiv abs/2310.16795 (2023): n. pag.

\[2\]Gu, Albert and Tri Dao. "Mamba: Linear-Time Sequence Modeling with Selective State Spaces." ArXiv abs/2312.00752 (2023): n. pag.


**Source**


**文章来源**


本文摘自：2024年2月23日已经发布的《人工智能十年展望（十六）：成本决定落地节奏，大模型轻量化、线性化趋势渐起》

于钟海 分析员 SAC 执证编号：S0080518070011 SFC CE Ref：BOP246

魏鹳霏 分析员 SAC 执证编号：S0080523060019 SFC CE Ref：BSX734

王之昊 分析员 SAC 执证编号：S0080522050001 SFC CE Ref：BSS168

游航 分析员 SAC 执证编号：S0080523010001 SFC CE Ref：BTI822


**Legal Disclaimer**


**法律声明**


特别提示

本公众号不是中国国际金融股份有限公司（下称"中金公司"）研究报告的发布平台。本公众号只是转发中金公司已发布研究报告的部分观点，订阅者若使用本公众号所载资料，有可能会因缺乏对完整报告的了解或缺乏相关的解读而对资料中的关键假设、评级、目标价等内容产生理解上的歧义。订阅者如使用本资料，须寻求专业投资顾问的指导及解读。

本公众号所载信息、意见不构成所述证券或金融工具买卖的出价或征价，评级、目标价、估值、盈利预测等分析判断亦不构成对具体证券或金融工具在具体价位、具体时点、具体市场表现的投资建议。该等信息、意见在任何时候均不构成对任何人的具有针对性的、指导具体投资的操作意见，订阅者应当对本公众号中的信息和意见进行评估，根据自身情况自主做出投资决策并自行承担投资风险。

中金公司对本公众号所载资料的准确性、可靠性、时效性及完整性不作任何明示或暗示的保证。对依据或者使用本公众号所载资料所造成的任何后果，中金公司及/或其关联人员均不承担任何形式的责任。

本公众号仅面向中金公司中国内地客户，任何不符合前述条件的订阅者，敬请订阅前自行评估接收订阅内容的适当性。订阅本公众号不构成任何合同或承诺的基础，中金公司不因任何单纯订阅本公众号的行为而将订阅人视为中金公司的客户。

一般声明

本公众号仅是转发中金公司已发布报告的部分观点，所载盈利预测、目标价格、评级、估值等观点的给予是基于一系列的假设和前提条件，订阅者只有在了解相关报告中的全部信息基础上，才可能对相关观点形成比较全面的认识。如欲了解完整观点，应参见中金研究网站（http://research.cicc.com）所载完整报告。

本资料较之中金公司正式发布的报告存在延时转发的情况，并有可能因报告发布日之后的情势或其他因素的变更而不再准确或失效。本资料所载意见、评估及预测仅为报告出具日的观点和判断。该等意见、评估及预测无需通知即可随时更改。证券或金融工具的价格或价值走势可能受各种因素影响，过往的表现不应作为日后表现的预示和担保。在不同时期，中金公司可能会发出与本资料所载意见、评估及预测不一致的研究报告。中金公司的销售人员、交易人员以及其他专业人士可能会依据不同假设和标准、采用不同的分析方法而口头或书面发表与本资料意见不一致的市场评论和/或交易观点。

在法律许可的情况下，中金公司可能与本资料中提及公司正在建立或争取建立业务关系或服务关系。因此，订阅者应当考虑到中金公司及/或其相关人员可能存在影响本资料观点客观性的潜在利益冲突。与本资料相关的披露信息请访http://research.cicc.com/disclosure_cn，亦可参见近期已发布的关于相关公司的具体研究报告。

本订阅号是由中金公司研究部建立并维护的官方订阅号。本订阅号中所有资料的版权均为中金公司所有，未经书面许可任何机构和个人不得以任何形式转发、转载、翻版、复制、刊登、发表、修改、仿制或引用本订阅号中的内容。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYs9SuulmPUY7zyTicoWTsibNFALSmCEroctiaGTcNecVicZdR97QlFBLUVEn1BCMcDQWO1ia9H7wNW8K5GQ%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)


[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7166705531573241279)
