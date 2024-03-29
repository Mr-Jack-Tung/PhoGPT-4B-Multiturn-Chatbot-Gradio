# PhoGPT-4B-Multiturn-Chatbot-Gradio
- Author: Mr.Jack _ Công ty www.BICweb.vn
- Start: 23Feb2024 - 09PM
- End: 23Feb2024 - 12PM

## Model:
- Model: vinai/PhoGPT-4B-Chat-v0.1
- Type: Instruction following & Chat
- Model Size: 3.7B
- Context length: 8192
- Vocab size: 20K
- Training data size: 70K instructional prompt and response pairs & 290K conversations
- Note: PROMPT_TEMPLATE = "### Câu hỏi: {instruction}\n### Trả lời:"


### PhoGPT: Generative Pre-training for Vietnamese
- Paper: https://arxiv.org/abs/2311.02945
- Github: https://github.com/VinAIResearch/PhoGPT
- Huggingface: https://huggingface.co/vinai/PhoGPT-4B-Chat-v0.1
- Source code: https://huggingface.co/vinai/PhoGPT-4B-Chat-v0.1/tree/main

### PHOGPT-4B: MODEL ARCHITECTURE AND PRE-TRAINING
PhoGPT-4B is a Transformer decoder-based model (Brown et al., 2020; Vaswani et al., 2017), which incorporates (Triton) flash attention (Dao et al., 2022) and ALiBi (Press et al., 2022) for context length extrapolation. We train a Vietnamese-specific byte-level BPE tokenizer with a vocabulary of 20480 tokens using the “tokenizers” library. In addition, we use a “max_seq_len” of 8192, “d_model” of 3072, “n_heads” of 24 and “n_layers” of 32, resulting in a model size of 3.7B param- eters (∼4B). Utilizing the Mosaicml “llm-foundry” library (Team, 2023), we pre-train PhoGPT-4B from scratch on a 482GB deduplicated and cleaned pre-training corpus of Vietnamese texts (∼102B tokens). Our pre-training Vietnamese corpus consists of:
- 1GB of Wikipedia texts (version 20/05/2023);
- 1.5GB of medical-related texts crawled from a wide range of publicly available and medical
domain-specific websites such as medical journals and universities;
- 3GB of publicly available books spanning a range of genres;
- 12GB of legal data crawled from thuvienphapluat.vn and lawnet.vn;
- a 40GB variant of the "binhvq" news corpus (version 21/05/2021); https://github.com/binhvq/news-corpus
- an 88GB variant of the Vietnamese OSCAR-2301 subset; https://huggingface.co/datasets/oscar-corpus/OSCAR-2301
- a 336GB variant of the Vietnamese mC4 subset. https://huggingface.co/datasets/allenai/c4/tree/mC4_3.1.0

### PHOGPT-4B-CHAT: SUPERVISED FINE-TUNING
We then fine-tune the base pre-trained PhoGPT-4B using a dataset consisting of 70K instructional prompts and their responses, along with an additional 290K conversations, constructed by concate- nating the following sources:
- 500 instructional prompt and response pairs for poem writing, 500 for essay writing, 500 for spelling correction, 500 for single-document summarization and 1000 for context-based question answering;
- 67K instructional prompt and response pairs from the Vietnamese subset of Bactrian-X (Li et al., 2023);
- 20K Vietnamese-translated ChatAlpaca conversations; https://github.com/cascip/ChatAlpaca
- 40K Vietnamese-translated ShareGPT conversations (without code and mathematics); https://huggingface.co/datasets/anon8231489123/ShareGPT_Vicuna_unfiltered
- 230K Vietnamese-translated UltraChat conversations (Ding et al., 2023); https://huggingface.co/datasets/HuggingFaceH4/ultrachat_200k

The resulting fine-tuned model is named PhoGPT-4B-Chat.

## Note:
Kết hợp Colab và Gradio cũng rất tuyệt ^.^ Cấu hình chạy cũng nhẹ nhàng, chỉ cần dùng Colab-T5 là dùng được, mà chỉ cần chạy có 50% nghĩa là khoảng 7GB GPU thôi nhé.

![alt text](https://github.com/Mr-Jack-Tung/PhoGPT-4B-Multiturn-Chatbot-Gradio/blob/main/PhoGPT_4B_Chat_v01_Gradio_Multiturn_chatbot_23Feb2024.jpg)

Kết hợp Colab, Gradio và Langchain RAG, hóa ra là RAG cũng khá đơn giản, chỉ cần lôi dữ liệu ra và nhồi vào phần câu hỏi (few-shot prompting) là em nó tự hiểu được cần phải làm gì tiếp theo rồi, em nó mà đủ thông tin là cũng ra gì và này nọ phết đấy ^^

- https://python.langchain.com/docs/expression_language/cookbook/retrieval
- https://python.langchain.com/docs/modules/data_connection/retrievers/parent_document_retriever
- https://github.com/FullStackRetrieval-com/RetrievalTutorials/blob/main/5_Levels_Of_Text_Splitting.ipynb

![alt text](https://github.com/Mr-Jack-Tung/PhoGPT-4B-Multiturn-Chatbot-Gradio/blob/main/PhoGPT_4B_Chat_v01_Gradio_with_RAG.jpg)

Khả năng đặt câu hỏi của em nó cũng khá ấn tượng ^^

{"Intel lên kế hoạch xây dựng nhà máy sản xuất chip hoàn toàn tự động bằng AI và robot"}

Hỏi: Hãy đặt 10 câu hỏi để tìm hiểu và làm rõ nội dung trên nhé.
![alt text](https://github.com/Mr-Jack-Tung/PhoGPT-4B-Multiturn-Chatbot-Gradio/blob/main/PhoGPT_Ask-questions-01.jpg)


Hỏi: Hãy đưa ra một số cách tìm kiếm thông tin, nghiên cứu để trả lời làm rõ các câu hỏi trên nhé.
![alt text](https://github.com/Mr-Jack-Tung/PhoGPT-4B-Multiturn-Chatbot-Gradio/blob/main/PhoGPT_Ask-questions-02.jpg)

### Tham khảo mở rộng:
- F1 score metric (in Van Rijsbergen's book 1992 ???):
  - https://huggingface.co/spaces/evaluate-metric/f1
  - https://en.wikipedia.org/wiki/F-score
  - https://en.wikipedia.org/wiki/Precision_and_recall
  - Information theory (1924; 1948): https://en.wikipedia.org/wiki/Information_theory
  - https://phamdinhkhanh.github.io/deepai-book/ch_donation/information_theory.html
  - https://en.wikipedia.org/wiki/Entropy_(information_theory)
  - Đánh giá các mô hình học máy: https://viblo.asia/p/danh-gia-cac-mo-hinh-hoc-may-RnB5pp4D5PG [...mô hình phân loại (classification), mô hình hồi quy (regression) và xếp hạng (Ranking)]
  - Đánh giá mô hình phân loại trong ML: https://phamdinhkhanh.github.io/2020/08/13/ModelMetric.html
- Okapi BM25 (= IDF * ((k + 1) * tf) / (k * (1.0 - b + b * (|d|/avgDl)) + tf)):
  - https://en.wikipedia.org/wiki/Okapi_BM25
  - https://opensourceconnections.com/blog/2015/10/16/bm25-the-next-generation-of-lucene-relevation/
  - Áp dụng Okapi BM25 vào tìm kiếm thông tin dựa trên Tiếng Việt: https://ndquy.github.io/posts/okapi-bm-25-tim-kiem-tieng-viet/
- BLEU Metric (bilingual evaluation understudy) - 2002:
  - Bleu: a Method for Automatic Evaluation of Machine Translation (Kishore Papineni, Salim Roukos, Todd Ward, and Wei-Jing Zhu. 2002): https://aclanthology.org/P02-1040/
  - https://huggingface.co/spaces/evaluate-metric/bleu
  - https://en.wikipedia.org/wiki/BLEU
  - Tìm hiểu về BLEU và WER - Metric cho 1 số tác vụ trong NLP: https://viblo.asia/p/tim-hieu-ve-bleu-va-wer-metric-cho-1-so-tac-vu-trong-nlp-Eb85oA16Z2G#_4-reference-8
- Rouge metric (Recall-Oriented Understudy for Gisting Evaluation) - 2004:
  - ROUGE: A Package for Automatic Evaluation of Summaries (Chin-Yew Lin. 2004): https://aclanthology.org/W04-1013/
  - https://huggingface.co/spaces/evaluate-metric/rouge
  - https://en.wikipedia.org/wiki/ROUGE_(metric)
  - 2 phút để hiểu cách tính ROUGE metric: https://viblo.asia/p/2-phut-de-hieu-cach-tinh-rouge-metric-5OXLAPEBJGr
- ROUGE-WE (Ng & Abrecht, 2015) - Better Summarization Evaluation with Word Embeddings for ROUGE: https://arxiv.org/abs/1508.06034
- ROUGE 2.0: Updated and Improved Measures for Evaluation of Summarization Tasks - 2018:
  - Paper: https://arxiv.org/abs/1803.01937
  - Github: https://github.com/kavgan/ROUGE-2.0
  - https://kavita-ganesan.com/rouge2-usage-documentation/
- ReAct: Synergizing Reasoning and Acting in Language Models - 2022: 
  - Paper: https://arxiv.org/abs/2210.03629
  - Github: https://github.com/ysymyth/ReAct
- (Self-Instruct) Aligning LM with Self Generated Instructions - 2022:
  - Paper: https://arxiv.org/abs/2212.10560 ;
  - Github: https://github.com/yizhongw/self-instruct
- (SELF-RAG) Learning to Retrieve, Generate and Critique through Self-reflection - 2023:
  - Paper: https://arxiv.org/abs/2310.11511 ;
  - Github: https://github.com/AkariAsai/self-rag
- (SPIN) Self-Play Fine-Tuning Converts Weak Language Models to Strong Language Models - 2024:
  - Paper: https://arxiv.org/abs/2401.01335
  - Github: https://github.com/uclaml/SPIN
  - Website: https://uclaml.github.io/SPIN/
- (CRAG) Corrective Retrieval Augmented Generation - 2024:
  - Paper: https://arxiv.org/abs/2401.15884 ;
  - Github: https://github.com/HuskyInSalt/CRAG


![alt text](https://github.com/Mr-Jack-Tung/PhoGPT-4B-Multiturn-Chatbot-Gradio/blob/main/crag_method_overview.jpg)
