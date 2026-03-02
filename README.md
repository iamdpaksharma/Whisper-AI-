# Whisper-AI-
Open Ai General Purpose Technology
[Blog] [Paper] [Model card] [Colab example]
Whisper is a general-purpose speech recognition model. It is trained on a large dataset of diverse audio and is also a multitasking model that can perform multilingual speech recognition, speech translation, and language identification.
# Approach
<img width="940" height="713" alt="image" src="https://github.com/user-attachments/assets/3bc6b0e6-bf87-454f-9354-3bd932befb58" />
A Transformer sequence-to-sequence model is trained on various speech processing tasks, including multilingual speech recognition, speech translation, spoken language identification, and voice activity detection. These tasks are jointly represented as a sequence of tokens to be predicted by the decoder, allowing a single model to replace many stages of a traditional speech-processing pipeline. The multitask training format uses a set of special tokens that serve as task specifiers or classification targets.
