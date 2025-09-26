# D3.3.3 Machine learning-based enrichment of social media

**Project:** [FIN-CLARIAH](https://www.kielipankki.fi/organization/fin-clariah/)  
**Grant agreement:** Research Council of Finland no. 358720  
**Start date:** 01-01-2024  
**Duration:** 24 months

**W3.3:** Report on Machine learning-based enrichment of social media  
**Date of reporting:** 22-09-2025

**Report authors:** Erik Henriksson (University of Turku), Tuomas Lundberg (University of Turku), Veronika Laippala (University of Turku)  
**Contributors:** Erik Henriksson (University of Turku), Tuomas Lundberg (University of Turku), Veronika Laippala (University of Turku)  
**Deliverable location:** 

* Main repository: [https://github.com/TurkuNLP/social-media-enrichment-fin-clariah](https://github.com/TurkuNLP/social-media-enrichment-fin-clariah)  
* Models: [https://huggingface.co/TurkuNLP/web-register-classification-multilingual-bge](https://huggingface.co/TurkuNLP/web-register-classification-multilingual-bge), [https://huggingface.co/TurkuNLP/bge-embeddings-subregister-classification](https://huggingface.co/TurkuNLP/bge-embeddings-subregister-classification)  
* Data: [https://huggingface.co/datasets/TurkuNLP/hplt-social-media-registers](https://huggingface.co/datasets/TurkuNLP/hplt-social-media-registers)  
* Demonstration: [https://colab.research.google.com/drive/1VV\_I0VNbIJbt\_dbhB-WH5uZM92rF5o-8](https://colab.research.google.com/drive/1VV_I0VNbIJbt_dbhB-WH5uZM92rF5o-8)

**Keywords:** machine learning; social media; web registers; register variation

**Description**

Web-crawled datasets have become invaluable resources for SSH research, supporting diverse fields including corpus linguistics, digital humanities, and computational social science. However, publicly available web datasets like HPLT 2.0 and FineWeb provide only basic metadata about their contents, such as document URLs and crawl dates, which limits their research potential. Enriching these noisy collections with contextual metadata would greatly improve their value for SSH research. 

In this deliverable, we focus on automatically identifying *social media text varieties* in web datasets, using machine learning. We publish the following resources:

* [A multilingual classifier](https://huggingface.co/TurkuNLP/web-register-classification-multilingual-bge) for labeling web documents by their register (or genre), including social media categories such as *blogs* and *forums*.   
* [Social media subtype classifiers](https://huggingface.co/TurkuNLP/web-register-classification-multilingual-bge,%20https://huggingface.co/TurkuNLP/bge-embeddings-subregister-classification) for English, Finnish, and Swedish for identifying thematic groups within social media registers (e.g. *travel* topics within *Narrative Blogs*).  
* [Datasets](https://huggingface.co/datasets/TurkuNLP/hplt-social-media-registers) labeled with register and fine-grained social media subtype metadata.  
* [A demonstration pipeline](https://colab.research.google.com/drive/1VV_I0VNbIJbt_dbhB-WH5uZM92rF5o-8) and tutorial on Google Colab  
* [A code repository](https://github.com/TurkuNLP/social-media-enrichment-fin-clariah) on Github

We approach the web text classification problem using the framework of register variation (Egbert and Biber 2018; Biber and Conrad 2019), where “register” denotes a text variety associated with a particular situational context, such as *News report* or *Recipe.* We use the 25-class [web register taxonomy](https://turkunlp.org/register-annotation-docs/) developed by Skantsi and Laippala (2023) to label 3 million randomly selected documents from the HPLT 2.0 corpus  (Burchell et al. 2025\) in English, Finnish, and Swedish (1M samples each). This automatic labeling uses the multilingual BGE-M3 model (Chen et al. 2024), [fine-tuned for register classification](https://huggingface.co/TurkuNLP/web-register-classification-multilingual-bge) following Henriksson et al. (2024). 

From this 3M document sample we then select a social media subset by choosing documents labeled with any of the following three registers: *Narrative Blog*, *Opinion Blog*, or *Interactive Discussion*. We also include so-called “hybrids” – documents assigned to more than one register label, such as *Narrative blog \+ Recipe*. This process yields a [dataset](https://huggingface.co/datasets/TurkuNLP/hplt-social-media-registers) of approximately 113,000 English, 290,000 Finnish, and 335,000 Swedish social media documents, with *Narrative Blogs* being the most common category across all languages.

To further analyze the contents of the identified social media documents, we apply HDBSCAN clustering (McInnes et al. 2017\) on their semantic vector representations, revealing meaningful thematic subgroups within some register categories. For instance, applying keyword analysis on the clusters, we identify *hand-crafting* and *cooking* themes in hybrid documents labeled *Narrative Blog* \+ *How-to/Instructional*. We develop simple [logistic regression classifiers](https://huggingface.co/TurkuNLP/web-register-classification-multilingual-bge,%20https://huggingface.co/TurkuNLP/bge-embeddings-subregister-classification) trained on these thematic clusters, allowing SSH researchers to first categorize text by register, then select social media registers of interest, and finally identify specific thematic subgroups where applicable.

**References**

Biber, Douglas, and Susan Conrad. 2019\. *Register, Genre, and Style.* Cambridge: Cambridge University Press.  
Burchell, Laurie, Ona de Gibert, Nikolay Arefyev, Mikko Aulamo, Marta Bañón, Pinzhen Chen, Mariia Fedorova et al. 2025\. “An expanded massive multilingual dataset for high-performance language technologies.” arXiv e-prints: arXiv-2503.  
Chen, Jianlv, Shitao Xiao, Peitian Zhang, Kun Luo, Defu Lian, and Zheng Liu. 2024\. “Bge m3-embedding: Multi-lingual, multi-functionality, multi-granularity text embeddings through self-knowledge distillation.” arXiv preprint arXiv:2402.03216.  
Egbert, Jesse, and Douglas Biber. 2018\. *Register Variation Online.* Cambridge: Cambridge University Press.  
Henriksson, Erik, Amanda Myntti, Saara Hellstrom, Anni Eskelinen, Selcen Erten-Johansson and Veronika Laippala. 2024\. “Automatic register identification for the open web using multilingual deep learning.” arXiv preprint arXiv:2406.19892.  
McInnes, Leland, John Healy, and Steve Astels. 2017\. “hdbscan: Hierarchical density based clustering.” *J. Open Source Softw.* 2:11, 205\.  
Skantsi, Valtteri, and Veronika Laippala. 2023\. “Analyzing the unrestricted web: The finnish corpus of online registers.” *Nordic Journal of Linguistics* 48:1, 1-31.

*FIN-CLARIAH project has received funding from the European Union – NextGenerationEU instrument and is funded by the Research Council of Finland under grant number 358720\.*  

# social-media-enrichment-fin-clariah
D3.3.3 Machine-learning based enrichment of social media

_FIN-CLARIAH project has received funding from the European Union – NextGenerationEU instrument and is funded by the Research Council of Finland under grant number 358720._

![](NetGenerationEU.jpg)