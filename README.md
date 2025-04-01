Domain-Adaptive Retrieval-Augmented Generation Model: Embedding Fine-Tuning for Bridge Damage Text Comprehension
==========================
This project proposes an adaptive retrieval enhanced generation model in the field of bridge damage diagnosis, which integrates report preprocessing, machine reading understanding dataset construction, efficient embedding model fine-tuning, embedding model evaluation, and information retrieval enhanced generation.
--------------------------

# Project Document Description

The files are divided into preprocessed Bridge Inspection Report (BIRD), Machine Reading Comprehension Dataset (MRC Dataset), Generative Embedding Model (Model), and Training Code.<br>

BIRD contains 4631 preprocessed bridge inspection reports. We collected 5183 bridge test reports from a province in Chinese Mainland from 2021 to 2023 as the data basis, and used text processing to desensitize, obtaining a data set BIRD containing 4637 bridge test reports. Bridge inspection reports mainly come from beam bridges, such as simply supported beam bridges and continuous beam bridges, while arch bridges, cable-stayed bridges, and suspension bridges account for a relatively small proportion, which is consistent with the distribution of bridge types in the real world. The core content of bridge inspection text is bridge disease analysis, including various diseases such as bridge cracks, exposed reinforcement, water seepage crystallization, honeycomb and pockmarks, and potholes, involving multiple key components such as beams, bridge piers, bridge piers, and bridge deck pavement. In paragraph extraction Q&A, paragraphs containing answers are recognized as basic facts.<br>

The MRC Dataset consists of two datasets, Bri-QuDDv1 and Bri-QuDDv2, with data sizes of 95158 and 52262, respectively. We use a large model to automatically generate a benchmark dataset for machine reading and understanding of bridge damage information, Bri-QuDDv1, which contains 95158 Q-D pairs. Based on this, after dataset screening, we generate a benchmark dataset for machine reading and understanding of bridge damage information, Bri-QuDDv2, which contains 52262 Q-D pairs. Both are currently the largest publicly available resources in this field.<br>

The Model consists of three models, namely BGE, Bri FtEMv1, and Bri FtEMv2. Selecting 1473 data pairs and 9390 data pairs from QuDDv2, the BGE model was fine tuned using the instruction fine-tuning method to generate bridge damage diagnosis generative embedding models Bri-FtEMv1 and Bri-FtEMv2 with domain task adaptability. These models are the only publicly known embedding models in the field of bridge damage identification.<br>

The Training Code includes all the training processes from report preprocessing, question and answer dataset extraction, machine reading comprehension dataset construction, embedded model retrieval performance evaluation, and retrieval enhancement generation model generation performance evaluation, compiled using a Python encoder. Next, we will provide a detailed description of this section:<br>


# Training code

## Report preprocessing
This section proposes a preprocessing method for addressing the issue of personalized information in bridge inspection reports. By removing non general information such as the span, structural form, and inspection unit of specific bridges, while retaining general content such as operational status and inspection results, and removing non textual information such as images and tables, the text is segmented and formatted for storage to enhance the applicability and practicality of the information, providing a more accurate data foundation for bridge damage analysis.<br>

## Q-A Extraction
This section proposes a data construction method based on a combination of large model automatic generation and screening optimization to address the scarcity of annotated data in the field of bridge diseases. By using a mixed channel of long and short texts to segment bridge detection reports, an initial question and answer dataset is generated using a pre trained model, and a two-stage scoring architecture is designed to screen high-quality Q-D pairs, effectively improving the model's semantic association parsing ability in professional fields, reducing data construction costs, and providing strong support for bridge disease analysis.<br>

## Fine tuning dataset construction for word embedding model (construction of machine reading comprehension dataset)
This section addresses the issue of insufficient correlation discrimination in bridge damage text recognition using retrieval enhanced generative models. The BGE open-source model is adopted and high-quality bridge damage Q-D data is innovatively introduced for fine-tuning. By implementing instruction based fine-tuning strategies, the model's query text correlation modeling ability in professional fields is enhanced, thereby improving the accuracy of the system's output answers and providing more effective support for bridge damage diagnosis information retrieval.<br>

## Evaluation of Embedded Model Retrieval Performance
When evaluating the accuracy of the response of the retrieval enhanced generative model, this section focuses on evaluating the document retrieval capability of the embedded model based on its complexity, using Hit Rate as the evaluation metric. By constructing a test database containing 420 and 950 Q-D pairs, and selecting 100 Q-D pairs as test sets respectively, text extraction tests were conducted on BGE, Bri FtEM v1, and Bri FtEM v2 models to verify whether the models could accurately retrieve relevant text fragments based on queries, thereby evaluating the recall accuracy of the embedded models in professional fields.<br>

## Evaluation of the generation effect of retrieval enhanced generative models<br>
This study proposes a retrieval enhanced generation model based on fine-tuning embedding model for information retrieval and generation in the field of bridge damage identification. This model combines the DeepSeeker R1 large language model and the Bri FtEM v1 embedding model, retrieves relevant document fragments through the embedding model, and fuses them with user input to generate accurate and rich answers from the large language model. The study used precision as the evaluation index and evaluated the answers generated by the model through domain experts, verifying the effectiveness and accuracy of the model in bridge damage information retrieval and generation.<br>
