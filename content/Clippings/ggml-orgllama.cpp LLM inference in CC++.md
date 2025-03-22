---
title: "ggml-org/llama.cpp: LLM inference in C/C++"
source: "https://github.com/ggml-org/llama.cpp?tab=readme-ov-file"
author:
  - "[[GitHub]]"
published:
created: 2025-03-20
description: "LLM inference in C/C++. Contribute to ggml-org/llama.cpp development by creating an account on GitHub."
tags:
  - "clippings"
---
## llama.cpp

[![llama](https://user-images.githubusercontent.com/1991296/230134379-7181e485-c521-4d23-a0d6-f7b3b61ba524.png)](https://user-images.githubusercontent.com/1991296/230134379-7181e485-c521-4d23-a0d6-f7b3b61ba524.png)

[Roadmap](https://github.com/users/ggerganov/projects/7) / [Project status](https://github.com/ggml-org/llama.cpp/discussions/3471) / [Manifesto](https://github.com/ggml-org/llama.cpp/discussions/205) / [ggml](https://github.com/ggml-org/ggml)

Inference of Meta's [LLaMA](https://arxiv.org/abs/2302.13971) model (and others) in pure C/C++

> [!IMPORTANT]
> New llama.cpp package location: ggml-org/llama.cpp

## Recent API changes

- [Changelog for `libllama` API](https://github.com/ggml-org/llama.cpp/issues/9289)
- [Changelog for `llama-server` REST API](https://github.com/ggml-org/llama.cpp/issues/9291)

## Hot topics

- **How to use [MTLResidencySet](https://developer.apple.com/documentation/metal/mtlresidencyset?language=objc) to keep the GPU memory active?** [#11427](https://github.com/ggml-org/llama.cpp/pull/11427)
- **VS Code extension for FIM completions:** [https://github.com/ggml-org/llama.vscode](https://github.com/ggml-org/llama.vscode)
- Universal [tool call support](https://github.com/ggml-org/llama.cpp/blob/master/docs/function-calling.md) in `llama-server` [#9639](https://github.com/ggml-org/llama.cpp/pull/9639)
- Vim/Neovim plugin for FIM completions: [https://github.com/ggml-org/llama.vim](https://github.com/ggml-org/llama.vim)
- Introducing GGUF-my-LoRA [#10123](https://github.com/ggml-org/llama.cpp/discussions/10123)
- Hugging Face Inference Endpoints now support GGUF out of the box! [#9669](https://github.com/ggml-org/llama.cpp/discussions/9669)
- Hugging Face GGUF editor: [discussion](https://github.com/ggml-org/llama.cpp/discussions/9268) | [tool](https://huggingface.co/spaces/CISCai/gguf-editor)

---

## Description

The main goal of `llama.cpp` is to enable LLM inference with minimal setup and state-of-the-art performance on a wide range of hardware - locally and in the cloud.

- Plain C/C++ implementation without any dependencies
- Apple silicon is a first-class citizen - optimized via ARM NEON, Accelerate and Metal frameworks
- AVX, AVX2, AVX512 and AMX support for x86 architectures
- 1.5-bit, 2-bit, 3-bit, 4-bit, 5-bit, 6-bit, and 8-bit integer quantization for faster inference and reduced memory use
- Custom CUDA kernels for running LLMs on NVIDIA GPUs (support for AMD GPUs via HIP and Moore Threads MTT GPUs via MUSA)
- Vulkan and SYCL backend support
- CPU+GPU hybrid inference to partially accelerate models larger than the total VRAM capacity

The `llama.cpp` project is the main playground for developing new features for the [ggml](https://github.com/ggml-org/ggml) library.

Models

Typically finetunes of the base models below are supported as well.

Instructions for adding support for new models: [HOWTO-add-model.md](https://github.com/ggml-org/llama.cpp/blob/master/docs/development/HOWTO-add-model.md)

#### Text-only

- LLaMA 🦙
- LLaMA 2 🦙🦙
- LLaMA 3 🦙🦙🦙
- [Mistral 7B](https://huggingface.co/mistralai/Mistral-7B-v0.1)
- [Mixtral MoE](https://huggingface.co/models?search=mistral-ai/Mixtral)
- [DBRX](https://huggingface.co/databricks/dbrx-instruct)
- [Falcon](https://huggingface.co/models?search=tiiuae/falcon)
- [Chinese LLaMA / Alpaca](https://github.com/ymcui/Chinese-LLaMA-Alpaca) and [Chinese LLaMA-2 / Alpaca-2](https://github.com/ymcui/Chinese-LLaMA-Alpaca-2)
- [Vigogne (French)](https://github.com/bofenghuang/vigogne)
- [BERT](https://github.com/ggml-org/llama.cpp/pull/5423)
- [Koala](https://bair.berkeley.edu/blog/2023/04/03/koala/)
- [Baichuan 1 & 2](https://huggingface.co/models?search=baichuan-inc/Baichuan) + [derivations](https://huggingface.co/hiyouga/baichuan-7b-sft)
- [Aquila 1 & 2](https://huggingface.co/models?search=BAAI/Aquila)
- [Starcoder models](https://github.com/ggml-org/llama.cpp/pull/3187)
- [Refact](https://huggingface.co/smallcloudai/Refact-1_6B-fim)
- [MPT](https://github.com/ggml-org/llama.cpp/pull/3417)
- [Bloom](https://github.com/ggml-org/llama.cpp/pull/3553)
- [Yi models](https://huggingface.co/models?search=01-ai/Yi)
- [StableLM models](https://huggingface.co/stabilityai)
- [Deepseek models](https://huggingface.co/models?search=deepseek-ai/deepseek)
- [Qwen models](https://huggingface.co/models?search=Qwen/Qwen)
- [PLaMo-13B](https://github.com/ggml-org/llama.cpp/pull/3557)
- [Phi models](https://huggingface.co/models?search=microsoft/phi)
- [PhiMoE](https://github.com/ggml-org/llama.cpp/pull/11003)
- [GPT-2](https://huggingface.co/gpt2)
- [Orion 14B](https://github.com/ggml-org/llama.cpp/pull/5118)
- [InternLM2](https://huggingface.co/models?search=internlm2)
- [CodeShell](https://github.com/WisdomShell/codeshell)
- [Gemma](https://ai.google.dev/gemma)
- [Mamba](https://github.com/state-spaces/mamba)
- [Grok-1](https://huggingface.co/keyfan/grok-1-hf)
- [Xverse](https://huggingface.co/models?search=xverse)
- [Command-R models](https://huggingface.co/models?search=CohereForAI/c4ai-command-r)
- [SEA-LION](https://huggingface.co/models?search=sea-lion)
- [GritLM-7B](https://huggingface.co/GritLM/GritLM-7B) + [GritLM-8x7B](https://huggingface.co/GritLM/GritLM-8x7B)
- [OLMo](https://allenai.org/olmo)
- [OLMo 2](https://allenai.org/olmo)
- [OLMoE](https://huggingface.co/allenai/OLMoE-1B-7B-0924)
- [Granite models](https://huggingface.co/collections/ibm-granite/granite-code-models-6624c5cec322e4c148c8b330)
- [GPT-NeoX](https://github.com/EleutherAI/gpt-neox) + [Pythia](https://github.com/EleutherAI/pythia)
- [Snowflake-Arctic MoE](https://huggingface.co/collections/Snowflake/arctic-66290090abe542894a5ac520)
- [Smaug](https://huggingface.co/models?search=Smaug)
- [Poro 34B](https://huggingface.co/LumiOpen/Poro-34B)
- [Bitnet b1.58 models](https://huggingface.co/1bitLLM)
- [Flan T5](https://huggingface.co/models?search=flan-t5)
- [Open Elm models](https://huggingface.co/collections/apple/openelm-instruct-models-6619ad295d7ae9f868b759ca)
- [ChatGLM3-6b](https://huggingface.co/THUDM/chatglm3-6b) + [ChatGLM4-9b](https://huggingface.co/THUDM/glm-4-9b) + [GLMEdge-1.5b](https://huggingface.co/THUDM/glm-edge-1.5b-chat) + [GLMEdge-4b](https://huggingface.co/THUDM/glm-edge-4b-chat)
- [SmolLM](https://huggingface.co/collections/HuggingFaceTB/smollm-6695016cad7167254ce15966)
- [EXAONE-3.0-7.8B-Instruct](https://huggingface.co/LGAI-EXAONE/EXAONE-3.0-7.8B-Instruct)
- [FalconMamba Models](https://huggingface.co/collections/tiiuae/falconmamba-7b-66b9a580324dd1598b0f6d4a)
- [Jais](https://huggingface.co/inceptionai/jais-13b-chat)
- [Bielik-11B-v2.3](https://huggingface.co/collections/speakleash/bielik-11b-v23-66ee813238d9b526a072408a)
- [RWKV-6](https://github.com/BlinkDL/RWKV-LM)
- [QRWKV-6](https://huggingface.co/recursal/QRWKV6-32B-Instruct-Preview-v0.1)
- [GigaChat-20B-A3B](https://huggingface.co/ai-sage/GigaChat-20B-A3B-instruct)

#### Multimodal

- [LLaVA 1.5 models](https://huggingface.co/collections/liuhaotian/llava-15-653aac15d994e992e2677a7e), [LLaVA 1.6 models](https://huggingface.co/collections/liuhaotian/llava-16-65b9e40155f60fd046a5ccf2)
- [BakLLaVA](https://huggingface.co/models?search=SkunkworksAI/Bakllava)
- [Obsidian](https://huggingface.co/NousResearch/Obsidian-3B-V0.5)
- [ShareGPT4V](https://huggingface.co/models?search=Lin-Chen/ShareGPT4V)
- [MobileVLM 1.7B/3B models](https://huggingface.co/models?search=mobileVLM)
- [Yi-VL](https://huggingface.co/models?search=Yi-VL)
- [Mini CPM](https://huggingface.co/models?search=MiniCPM)
- [Moondream](https://huggingface.co/vikhyatk/moondream2)
- [Bunny](https://github.com/BAAI-DCAI/Bunny)
- [GLM-EDGE](https://huggingface.co/models?search=glm-edge)
- [Qwen2-VL](https://huggingface.co/collections/Qwen/qwen2-vl-66cee7455501d7126940800d)

Bindings

- Python: [abetlen/llama-cpp-python](https://github.com/abetlen/llama-cpp-python)
- Go: [go-skynet/go-llama.cpp](https://github.com/go-skynet/go-llama.cpp)
- Node.js: [withcatai/node-llama-cpp](https://github.com/withcatai/node-llama-cpp)
- JS/TS (llama.cpp server client): [lgrammel/modelfusion](https://modelfusion.dev/integration/model-provider/llamacpp)
- JS/TS (Programmable Prompt Engine CLI): [offline-ai/cli](https://github.com/offline-ai/cli)
- JavaScript/Wasm (works in browser): [tangledgroup/llama-cpp-wasm](https://github.com/tangledgroup/llama-cpp-wasm)
- Typescript/Wasm (nicer API, available on npm): [ngxson/wllama](https://github.com/ngxson/wllama)
- Ruby: [yoshoku/llama\_cpp.rb](https://github.com/yoshoku/llama_cpp.rb)
- Rust (more features): [edgenai/llama\_cpp-rs](https://github.com/edgenai/llama_cpp-rs)
- Rust (nicer API): [mdrokz/rust-llama.cpp](https://github.com/mdrokz/rust-llama.cpp)
- Rust (more direct bindings): [utilityai/llama-cpp-rs](https://github.com/utilityai/llama-cpp-rs)
- Rust (automated build from crates.io): [ShelbyJenkins/llm\_client](https://github.com/ShelbyJenkins/llm_client)
- C#/.NET: [SciSharp/LLamaSharp](https://github.com/SciSharp/LLamaSharp)
- C#/VB.NET (more features - community license): [LM-Kit.NET](https://docs.lm-kit.com/lm-kit-net/index.html)
- Scala 3: [donderom/llm4s](https://github.com/donderom/llm4s)
- Clojure: [phronmophobic/llama.clj](https://github.com/phronmophobic/llama.clj)
- React Native: [mybigday/llama.rn](https://github.com/mybigday/llama.rn)
- Java: [kherud/java-llama.cpp](https://github.com/kherud/java-llama.cpp)
- Zig: [deins/llama.cpp.zig](https://github.com/Deins/llama.cpp.zig)
- Flutter/Dart: [netdur/llama\_cpp\_dart](https://github.com/netdur/llama_cpp_dart)
- Flutter: [xuegao-tzx/Fllama](https://github.com/xuegao-tzx/Fllama)
- PHP (API bindings and features built on top of llama.cpp): [distantmagic/resonance](https://github.com/distantmagic/resonance) [(more info)](https://github.com/ggml-org/llama.cpp/pull/6326)
- Guile Scheme: [guile\_llama\_cpp](https://savannah.nongnu.org/projects/guile-llama-cpp)
- Swift [srgtuszy/llama-cpp-swift](https://github.com/srgtuszy/llama-cpp-swift)
- Swift [ShenghaiWang/SwiftLlama](https://github.com/ShenghaiWang/SwiftLlama)
- Delphi [Embarcadero/llama-cpp-delphi](https://github.com/Embarcadero/llama-cpp-delphi)

UIs

*(to have a project listed here, it should clearly state that it depends on `llama.cpp`)*

- [AI Sublime Text plugin](https://github.com/yaroslavyaroslav/OpenAI-sublime-text) (MIT)
- [cztomsik/ava](https://github.com/cztomsik/ava) (MIT)
- [Dot](https://github.com/alexpinel/Dot) (GPL)
- [eva](https://github.com/ylsdamxssjxxdd/eva) (MIT)
- [iohub/collama](https://github.com/iohub/coLLaMA) (Apache-2.0)
- [janhq/jan](https://github.com/janhq/jan) (AGPL)
- [johnbean393/Sidekick](https://github.com/johnbean393/Sidekick) (MIT)
- [KanTV](https://github.com/zhouwg/kantv?tab=readme-ov-file) (Apache-2.0)
- [KodiBot](https://github.com/firatkiral/kodibot) (GPL)
- [llama.vim](https://github.com/ggml-org/llama.vim) (MIT)
- [LARS](https://github.com/abgulati/LARS) (AGPL)
- [Llama Assistant](https://github.com/vietanhdev/llama-assistant) (GPL)
- [LLMFarm](https://github.com/guinmoon/LLMFarm?tab=readme-ov-file) (MIT)
- [LLMUnity](https://github.com/undreamai/LLMUnity) (MIT)
- [LMStudio](https://lmstudio.ai/) (proprietary)
- [LocalAI](https://github.com/mudler/LocalAI) (MIT)
- [LostRuins/koboldcpp](https://github.com/LostRuins/koboldcpp) (AGPL)
- [MindMac](https://mindmac.app/) (proprietary)
- [MindWorkAI/AI-Studio](https://github.com/MindWorkAI/AI-Studio) (FSL-1.1-MIT)
- [Mobile-Artificial-Intelligence/maid](https://github.com/Mobile-Artificial-Intelligence/maid) (MIT)
- [Mozilla-Ocho/llamafile](https://github.com/Mozilla-Ocho/llamafile) (Apache-2.0)
- [nat/openplayground](https://github.com/nat/openplayground) (MIT)
- [nomic-ai/gpt4all](https://github.com/nomic-ai/gpt4all) (MIT)
- [ollama/ollama](https://github.com/ollama/ollama) (MIT)
- [oobabooga/text-generation-webui](https://github.com/oobabooga/text-generation-webui) (AGPL)
- [PocketPal AI](https://github.com/a-ghorbani/pocketpal-ai) (MIT)
- [psugihara/FreeChat](https://github.com/psugihara/FreeChat) (MIT)
- [ptsochantaris/emeltal](https://github.com/ptsochantaris/emeltal) (MIT)
- [pythops/tenere](https://github.com/pythops/tenere) (AGPL)
- [ramalama](https://github.com/containers/ramalama) (MIT)
- [semperai/amica](https://github.com/semperai/amica) (MIT)
- [withcatai/catai](https://github.com/withcatai/catai) (MIT)
- [Autopen](https://github.com/blackhole89/autopen) (GPL)

Tools

- [akx/ggify](https://github.com/akx/ggify) – download PyTorch models from HuggingFace Hub and convert them to GGML
- [akx/ollama-dl](https://github.com/akx/ollama-dl) – download models from the Ollama library to be used directly with llama.cpp
- [crashr/gppm](https://github.com/crashr/gppm) – launch llama.cpp instances utilizing NVIDIA Tesla P40 or P100 GPUs with reduced idle power consumption
- [gpustack/gguf-parser](https://github.com/gpustack/gguf-parser-go/tree/main/cmd/gguf-parser) - review/check the GGUF file and estimate the memory usage
- [Styled Lines](https://marketplace.unity.com/packages/tools/generative-ai/styled-lines-llama-cpp-model-292902) (proprietary licensed, async wrapper of inference part for game development in Unity3d with pre-built Mobile and Web platform wrappers and a model example)

Infrastructure

- [Paddler](https://github.com/distantmagic/paddler) - Stateful load balancer custom-tailored for llama.cpp
- [GPUStack](https://github.com/gpustack/gpustack) - Manage GPU clusters for running LLMs
- [llama\_cpp\_canister](https://github.com/onicai/llama_cpp_canister) - llama.cpp as a smart contract on the Internet Computer, using WebAssembly
- [llama-swap](https://github.com/mostlygeek/llama-swap) - transparent proxy that adds automatic model switching with llama-server
- [Kalavai](https://github.com/kalavai-net/kalavai-client) - Crowdsource end to end LLM deployment at any scale
- [llmaz](https://github.com/InftyAI/llmaz) - ☸️ Easy, advanced inference platform for large language models on Kubernetes.

Games

- [Lucy's Labyrinth](https://github.com/MorganRO8/Lucys_Labyrinth) - A simple maze game where agents controlled by an AI model will try to trick you.

## Supported backends

| Backend | Target devices |
| --- | --- |
| [Metal](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md#metal-build) | Apple Silicon |
| [BLAS](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md#blas-build) | All |
| [BLIS](https://github.com/ggml-org/llama.cpp/blob/master/docs/backend/BLIS.md) | All |
| [SYCL](https://github.com/ggml-org/llama.cpp/blob/master/docs/backend/SYCL.md) | Intel and Nvidia GPU |
| [MUSA](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md#musa) | Moore Threads MTT GPU |
| [CUDA](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md#cuda) | Nvidia GPU |
| [HIP](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md#hip) | AMD GPU |
| [Vulkan](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md#vulkan) | GPU |
| [CANN](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md#cann) | Ascend NPU |
| [OpenCL](https://github.com/ggml-org/llama.cpp/blob/master/docs/backend/OPENCL.md) | Adreno GPU |

## Building the project

The main product of this project is the `llama` library. Its C-style interface can be found in [include/llama.h](https://github.com/ggml-org/llama.cpp/blob/master/include/llama.h). The project also includes many example programs and tools using the `llama` library. The examples range from simple, minimal code snippets to sophisticated sub-projects such as an OpenAI-compatible HTTP server. Possible methods for obtaining the binaries:

- Clone this repository and build locally, see [how to build](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md)
- On MacOS or Linux, install `llama.cpp` via [brew, flox or nix](https://github.com/ggml-org/llama.cpp/blob/master/docs/install.md)
- Use a Docker image, see [documentation for Docker](https://github.com/ggml-org/llama.cpp/blob/master/docs/docker.md)
- Download pre-built binaries from [releases](https://github.com/ggml-org/llama.cpp/releases)

## Obtaining and quantizing models

The [Hugging Face](https://huggingface.co/) platform hosts a [number of LLMs](https://huggingface.co/models?library=gguf&sort=trending) compatible with `llama.cpp`:

- [Trending](https://huggingface.co/models?library=gguf&sort=trending)
- [LLaMA](https://huggingface.co/models?sort=trending&search=llama+gguf)

You can either manually download the GGUF file or directly use any `llama.cpp`\-compatible models from Hugging Face by using this CLI argument: `-hf <user>/<model>[:quant]`

After downloading a model, use the CLI tools to run it locally - see below.

`llama.cpp` requires the model to be stored in the [GGUF](https://github.com/ggml-org/ggml/blob/master/docs/gguf.md) file format. Models in other data formats can be converted to GGUF using the `convert_*.py` Python scripts in this repo.

The Hugging Face platform provides a variety of online tools for converting, quantizing and hosting models with `llama.cpp`:

- Use the [GGUF-my-repo space](https://huggingface.co/spaces/ggml-org/gguf-my-repo) to convert to GGUF format and quantize model weights to smaller sizes
- Use the [GGUF-my-LoRA space](https://huggingface.co/spaces/ggml-org/gguf-my-lora) to convert LoRA adapters to GGUF format (more info: [#10123](https://github.com/ggml-org/llama.cpp/discussions/10123))
- Use the [GGUF-editor space](https://huggingface.co/spaces/CISCai/gguf-editor) to edit GGUF meta data in the browser (more info: [#9268](https://github.com/ggml-org/llama.cpp/discussions/9268))
- Use the [Inference Endpoints](https://ui.endpoints.huggingface.co/) to directly host `llama.cpp` in the cloud (more info: [#9669](https://github.com/ggml-org/llama.cpp/discussions/9669))

To learn more about model quantization, [read this documentation](https://github.com/ggml-org/llama.cpp/blob/master/examples/quantize/README.md)

## [`llama-cli`](https://github.com/ggml-org/llama.cpp/blob/master/examples/main)

#### A CLI tool for accessing and experimenting with most of `llama.cpp`'s functionality.

- Run in conversation mode

Models with a built-in chat template will automatically activate conversation mode. If this doesn't occur, you can manually enable it by adding `-cnv` and specifying a suitable chat template with `--chat-template NAME`

```
llama-cli -m model.gguf

# > hi, who are you?
# Hi there! I'm your helpful assistant! I'm an AI-powered chatbot designed to assist and provide information to users like you. I'm here to help answer your questions, provide guidance, and offer support on a wide range of topics. I'm a friendly and knowledgeable AI, and I'm always happy to help with anything you need. What's on your mind, and how can I assist you today?
#
# > what is 1+1?
# Easy peasy! The answer to 1+1 is... 2!
```
- Run in conversation mode with custom chat template
```
# use the "chatml" template (use -h to see the list of supported templates)
llama-cli -m model.gguf -cnv --chat-template chatml

# use a custom template
llama-cli -m model.gguf -cnv --in-prefix 'User: ' --reverse-prompt 'User:'
```
- Run simple text completion

To disable conversation mode explicitly, use `-no-cnv`

```
llama-cli -m model.gguf -p "I believe the meaning of life is" -n 128 -no-cnv

# I believe the meaning of life is to find your own truth and to live in accordance with it. For me, this means being true to myself and following my passions, even if they don't align with societal expectations. I think that's what I love about yoga – it's not just a physical practice, but a spiritual one too. It's about connecting with yourself, listening to your inner voice, and honoring your own unique journey.
```
- Constrain the output with a custom grammar
```
llama-cli -m model.gguf -n 256 --grammar-file grammars/json.gbnf -p 'Request: schedule a call at 8pm; Command:'

# {"appointmentTime": "8pm", "appointmentDetails": "schedule a a call"}
```

The [grammars/](https://github.com/ggml-org/llama.cpp/blob/master/grammars) folder contains a handful of sample grammars. To write your own, check out the [GBNF Guide](https://github.com/ggml-org/llama.cpp/blob/master/grammars/README.md).

For authoring more complex JSON grammars, check out [https://grammar.intrinsiclabs.ai/](https://grammar.intrinsiclabs.ai/)

## [`llama-server`](https://github.com/ggml-org/llama.cpp/blob/master/examples/server)

#### A lightweight, [OpenAI API](https://github.com/openai/openai-openapi) compatible, HTTP server for serving LLMs.

- Start a local HTTP server with default configuration on port 8080
```
llama-server -m model.gguf --port 8080

# Basic web UI can be accessed via browser: http://localhost:8080
# Chat completion endpoint: http://localhost:8080/v1/chat/completions
```
- Support multiple-users and parallel decoding
```
# up to 4 concurrent requests, each with 4096 max context
llama-server -m model.gguf -c 16384 -np 4
```
- Enable speculative decoding
```
# the draft.gguf model should be a small variant of the target model.gguf
llama-server -m model.gguf -md draft.gguf
```
- Serve an embedding model
```
# use the /embedding endpoint
llama-server -m model.gguf --embedding --pooling cls -ub 8192
```
- Serve a reranking model
```
# use the /reranking endpoint
llama-server -m model.gguf --reranking
```
- Constrain all outputs with a grammar
```
# custom grammar
llama-server -m model.gguf --grammar-file grammar.gbnf

# JSON
llama-server -m model.gguf --grammar-file grammars/json.gbnf
```

## [`llama-perplexity`](https://github.com/ggml-org/llama.cpp/blob/master/examples/perplexity)

#### A tool for measuring the perplexity <sup><a href="https://github.com/ggml-org/?tab=readme-ov-file#user-content-fn-1-a4d03b2a2a65205b581fafae324058e2" id="user-content-fnref-1-a4d03b2a2a65205b581fafae324058e2" data-footnote-ref="">1</a></sup><sup><a href="https://github.com/ggml-org/?tab=readme-ov-file#user-content-fn-2-a4d03b2a2a65205b581fafae324058e2" id="user-content-fnref-2-a4d03b2a2a65205b581fafae324058e2" data-footnote-ref="">2</a></sup> (and other quality metrics) of a model over a given text.

- Measure the perplexity over a text file
```
llama-perplexity -m model.gguf -f file.txt

# [1]15.2701,[2]5.4007,[3]5.3073,[4]6.2965,[5]5.8940,[6]5.6096,[7]5.7942,[8]4.9297, ...
# Final estimate: PPL = 5.4007 +/- 0.67339
```
- Measure KL divergence
```
# TODO
```

## [`llama-bench`](https://github.com/ggml-org/llama.cpp/blob/master/examples/llama-bench)

#### Benchmark the performance of the inference for various parameters.

- Run default benchmark
```
llama-bench -m model.gguf

# Output:
# | model               |       size |     params | backend    | threads |          test |                  t/s |
# | ------------------- | ---------: | ---------: | ---------- | ------: | ------------: | -------------------: |
# | qwen2 1.5B Q4_0     | 885.97 MiB |     1.54 B | Metal,BLAS |      16 |         pp512 |      5765.41 ± 20.55 |
# | qwen2 1.5B Q4_0     | 885.97 MiB |     1.54 B | Metal,BLAS |      16 |         tg128 |        197.71 ± 0.81 |
#
# build: 3e0ba0e60 (4229)
```

## [`llama-run`](https://github.com/ggml-org/llama.cpp/blob/master/examples/run)

#### A comprehensive example for running `llama.cpp` models. Useful for inferencing. Used with RamaLama <sup><a href="https://github.com/ggml-org/?tab=readme-ov-file#user-content-fn-3-a4d03b2a2a65205b581fafae324058e2" id="user-content-fnref-3-a4d03b2a2a65205b581fafae324058e2" data-footnote-ref="">3</a></sup>.

- Run a model with a specific prompt (by default it's pulled from Ollama registry)
```
llama-run granite-code
```

## [`llama-simple`](https://github.com/ggml-org/llama.cpp/blob/master/examples/simple)

#### A minimal example for implementing apps with `llama.cpp`. Useful for developers.

- Basic text completion
```
llama-simple -m model.gguf

# Hello my name is Kaitlyn and I am a 16 year old girl. I am a junior in high school and I am currently taking a class called "The Art of
```

## Contributing

- Contributors can open PRs
- Collaborators can push to branches in the `llama.cpp` repo and merge PRs into the `master` branch
- Collaborators will be invited based on contributions
- Any help with managing issues, PRs and projects is very appreciated!
- See [good first issues](https://github.com/ggml-org/llama.cpp/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22) for tasks suitable for first contributions
- Read the [CONTRIBUTING.md](https://github.com/ggml-org/llama.cpp/blob/master/CONTRIBUTING.md) for more information
- Make sure to read this: [Inference at the edge](https://github.com/ggml-org/llama.cpp/discussions/205)
- A bit of backstory for those who are interested: [Changelog podcast](https://changelog.com/podcast/532)

## Other documentation

- [main (cli)](https://github.com/ggml-org/llama.cpp/blob/master/examples/main/README.md)
- [server](https://github.com/ggml-org/llama.cpp/blob/master/examples/server/README.md)
- [GBNF grammars](https://github.com/ggml-org/llama.cpp/blob/master/grammars/README.md)

#### Development documentation

- [How to build](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md)
- [Running on Docker](https://github.com/ggml-org/llama.cpp/blob/master/docs/docker.md)
- [Build on Android](https://github.com/ggml-org/llama.cpp/blob/master/docs/android.md)
- [Performance troubleshooting](https://github.com/ggml-org/llama.cpp/blob/master/docs/development/token_generation_performance_tips.md)
- [GGML tips & tricks](https://github.com/ggml-org/llama.cpp/wiki/GGML-Tips-&-Tricks)

#### Seminal papers and background on the models

If your issue is with model generation quality, then please at least scan the following links and papers to understand the limitations of LLaMA models. This is especially important when choosing an appropriate model size and appreciating both the significant and subtle differences between LLaMA models and ChatGPT:

- LLaMA:
- [Introducing LLaMA: A foundational, 65-billion-parameter large language model](https://ai.facebook.com/blog/large-language-model-llama-meta-ai/)
- [LLaMA: Open and Efficient Foundation Language Models](https://arxiv.org/abs/2302.13971)
- GPT-3
- [Language Models are Few-Shot Learners](https://arxiv.org/abs/2005.14165)
- GPT-3.5 / InstructGPT / ChatGPT:
- [Aligning language models to follow instructions](https://openai.com/research/instruction-following)
- [Training language models to follow instructions with human feedback](https://arxiv.org/abs/2203.02155)

## Completions

Command-line completion is available for some environments.

#### Bash Completion

```
$ build/bin/llama-cli --completion-bash > ~/.llama-completion.bash
$ source ~/.llama-completion.bash
```

Optionally this can be added to your `.bashrc` or `.bash_profile` to load it automatically. For example:

```
$ echo "source ~/.llama-completion.bash" >> ~/.bashrc
```

## References

## Footnotes

[^1]: [examples/perplexity/README.md](https://github.com/ggml-org/examples/perplexity/README.md)

[^2]: [https://huggingface.co/docs/transformers/perplexity](https://huggingface.co/docs/transformers/perplexity)

[^3]: [RamaLama](https://github.com/containers/ramalama)