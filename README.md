# Whisper-AI-
Open Ai General Purpose Technology
[Blog] [Paper] [Model card] [Colab example]
Whisper is a general-purpose speech recognition model. It is trained on a large dataset of diverse audio and is also a multitasking model that can perform multilingual speech recognition, speech translation, and language identification.
# Approach
<img width="940" height="713" alt="image" src="https://github.com/user-attachments/assets/3bc6b0e6-bf87-454f-9354-3bd932befb58" />
A Transformer sequence-to-sequence model is trained on various speech processing tasks, including multilingual speech recognition, speech translation, spoken language identification, and voice activity detection. These tasks are jointly represented as a sequence of tokens to be predicted by the decoder, allowing a single model to replace many stages of a traditional speech-processing pipeline. The multitask training format uses a set of special tokens that serve as task specifiers or classification targets.
# Setup
We used Python 3.9.9 and PyTorch 1.10.1 to train and test our models, but the codebase is expected to be compatible with Python 3.8-3.11 and recent PyTorch versions. The codebase also depends on a few Python packages, most notably OpenAI's tiktoken for their fast tokenizer implementation. You can download and install (or update to) the latest release of Whisper with the following command:
pip install -U openai-whisper
Alternatively, the following command will pull and install the latest commit from this repository, along with its Python dependencies:
pip install git+https://github.com/openai/whisper.git 
To update the package to the latest version of this repository, please run:
pip install --upgrade --no-deps --force-reinstall git+https://github.com/openai/whisper.git
It also requires the command-line tool ffmpeg to be installed on your system, which is available from most package managers:
     # on Ubuntu or Debian
     sudo apt update && sudo apt install ffmpeg

     # on Arch Linux
     sudo pacman -S ffmpeg

     # on MacOS using Homebrew (https://brew.sh/)
     brew install ffmpeg

     # on Windows using Chocolatey (https://chocolatey.org/)
     choco install ffmpeg

     # on Windows using Scoop (https://scoop.sh/)
     scoop install ffmpeg
You may need rust installed as well, in case tiktoken does not provide a pre-built wheel for your platform. If you see installation errors during the pip install command above, please follow the Getting started page to install Rust development environment. Additionally, you may need to configure the PATH environment variable, e.g. export PATH="$HOME/.cargo/bin:$PATH". If the installation fails with No module named 'setuptools_rust', you need to install setuptools_rust, e.g. by running:
pip install setuptools-rust
# Available models and languages
There are six model sizes, four with English-only versions, offering speed and accuracy tradeoffs. Below are the names of the available models and their approximate memory requirements and inference speed relative to the large model. The relative speeds below are measured by transcribing English speech on a A100, and the real-world speed may vary significantly depending on many factors including the language, the speaking speed, and the available hardware.
| Size   | Parameters | English-only model | Multilingual model | Required VRAM | Relative speed |
|--------|------------|-------------------|--------------------|---------------|---------------|
| tiny   | 39 M       | tiny.en           | tiny               | ~1 GB         | ~10x         |
| base   | 74 M       | base.en           | base               | ~1 GB         | ~7x          |
| small  | 244 M      | small.en          | small              | ~2 GB         | ~4x          |
| medium | 769 M      | medium.en         | medium             | ~5 GB         | ~2x          |
| large  | 1550 M     | N/A               | large              | ~10 GB        | 1x           |
| turbo  | 809 M      | N/A               | turbo              | ~6 GB         | ~8x          |
