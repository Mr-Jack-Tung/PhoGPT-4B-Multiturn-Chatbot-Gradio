# PhoGPT-4B-Multiturn-Chatbot-Gradio
- Author: Mr.Jack _ Công ty www.BICweb.vn
- Start: 23Feb2024 - 10PM
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
https://arxiv.org/abs/2311.02945

### PHOGPT-4B: MODEL ARCHITECTURE AND PRE-TRAINING
PhoGPT-4B is a Transformer decoder-based model (Brown et al., 2020; Vaswani et al., 2017), which incorporates (Triton) flash attention (Dao et al., 2022) and ALiBi (Press et al., 2022) for context length extrapolation. We train a Vietnamese-specific byte-level BPE tokenizer with a vocabulary of 20480 tokens using the “tokenizers” library. In addition, we use a “max_seq_len” of 8192, “d_model” of 3072, “n_heads” of 24 and “n_layers” of 32, resulting in a model size of 3.7B param- eters (∼4B). Utilizing the Mosaicml “llm-foundry” library (Team, 2023), we pre-train PhoGPT-4B from scratch on a 482GB deduplicated and cleaned pre-training corpus of Vietnamese texts (∼102B tokens). Our pre-training Vietnamese corpus consists of:
- 1GB of Wikipedia texts (version 20/05/2023);
- 1.5GBofmedical-relatedtextscrawledfromawiderangeofpubliclyavailableandmedical
domain-specific websites such as medical journals and universities;
- 3GB of publicly available books spanning a range of genres;
- 12GB of legal data crawled from thuvienphapluat.vn and lawnet.vn;
- a 40GB variant of the "binhvq" news corpus (version 21/05/2021);
- an 88GB variant of the Vietnamese OSCAR-2301 subset;
- a 336GB variant of the Vietnamese mC4 subset.

### PHOGPT-4B-CHAT: SUPERVISED FINE-TUNING
We then fine-tune the base pre-trained PhoGPT-4B using a dataset consisting of 70K instructional prompts and their responses, along with an additional 290K conversations, constructed by concate- nating the following sources:
- 500 instructional prompt and response pairs for poem writing, 500 for essay writing, 500 for spelling correction, 500 for single-document summarization and 1000 for context-based question answering;
- 67K instructional prompt and response pairs from the Vietnamese subset of Bactrian-X (Li et al., 2023);
- 20K Vietnamese-translated ChatAlpaca conversations;
- 40K Vietnamese-translated ShareGPT conversations (without code and mathematics);
- 230K Vietnamese-translated UltraChat conversations (Ding et al., 2023);

The resulting fine-tuned model is named PhoGPT-4B-Chat.

## Note:
Kết hợp Colab và Gradio cũng rất tuyệt ^.^

![alt text](https://github.com/Mr-Jack-Tung/PhoGPT-4B-Multiturn-Chatbot-Gradio/blob/main/PhoGPT_4B_Chat_v01_Gradio_Multiturn_chatbot_23Feb2024.jpg)
