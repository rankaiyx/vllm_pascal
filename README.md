2025.11.22 update

https://github.com/rankaiyx/vllm_pascal/tree/pascal_2025.11.22

Please switch branches as needed during the following operations.

-----------------------
Pre-install:

wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-keyring_1.1-1_all.deb

sudo dpkg -i cuda-keyring_1.1-1_all.deb

sudo apt-get update

sudo apt-get -y install cuda-toolkit-12-6

Add nvcc to the PATH environment variable

wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

bash Miniconda3-latest-Linux-x86_64.sh

do you wish to update your shell profile to automatically initialize conda? yes

Install:

mkdir vllm
 
cd vllm
 
conda create --prefix ./conda_env python=3.12
 
conda activate ./conda_env
 
git clone https://github.com/rankaiyx/vllm_pascal.git

cd vllm_pascal

export MAX_JOBS=14   //Select the number of concurrent compilations based on the number of CPU cores, and reduce it if the RAM is out of memory.

pip install -vvv -e .  --extra-index-url https://download.pytorch.org/whl/cu126 

or 

pip install -vvv -e .  --extra-index-url https://download.pytorch.org/whl/cu126 --index-url some-mirror

Successfully installed MarkupSafe-3.0.2 aiohappyeyeballs-2.6.1 aiohttp-3.12.15 aiosignal-1.4.0 annotated-types-0.7.0 anyio-4.11.0 astor-0.8.1 attrs-25.3.0 blake3-1.0.6 cachetools-6.2.0 cbor2-5.7.0 certifi-2025.8.3 cffi-2.0.0 charset_normalizer-3.4.3 click-8.3.0 cloudpickle-3.1.1 compressed-tensors-0.11.0 cupy-cuda12x-13.6.0 depyf-0.19.0 dill-0.4.0 diskcache-5.6.3 distro-1.9.0 dnspython-2.8.0 einops-0.8.1 email-validator-2.3.0 fastapi-0.117.1 fastapi-cli-0.0.13 fastapi-cloud-cli-0.2.1 fastrlock-0.8.3 filelock-3.19.1 frozendict-2.4.6 frozenlist-1.7.0 fsspec-2025.9.0 gguf-0.17.1 h11-0.16.0 hf-xet-1.1.10 httpcore-1.0.9 httptools-0.6.4 httpx-0.28.1 huggingface-hub-0.35.1 idna-3.10 interegular-0.3.3 jinja2-3.1.6 jiter-0.11.0 jsonschema-4.25.1 jsonschema-specifications-2025.9.1 lark-1.2.2 llguidance-0.7.30 llvmlite-0.44.0 lm-format-enforcer-0.11.3 markdown-it-py-4.0.0 mdurl-0.1.2 mistral_common-1.8.5 mpmath-1.3.0 msgpack-1.1.1 msgspec-0.19.0 multidict-6.6.4 networkx-3.5 ninja-1.13.0 numba-0.61.2 numpy-2.2.6 nvidia-cublas-cu12-12.6.4.1 nvidia-cuda-cupti-cu12-12.6.80 nvidia-cuda-nvrtc-cu12-12.6.77 nvidia-cuda-runtime-cu12-12.6.77 nvidia-cudnn-cu12-9.10.2.21 nvidia-cufft-cu12-11.3.0.4 nvidia-cufile-cu12-1.11.1.6 nvidia-curand-cu12-10.3.7.77 nvidia-cusolver-cu12-11.7.1.2 nvidia-cusparse-cu12-12.5.4.2 nvidia-cusparselt-cu12-0.7.1 nvidia-nccl-cu12-2.27.3 nvidia-nvjitlink-cu12-12.6.85 nvidia-nvtx-cu12-12.6.77 openai-1.109.1 openai-harmony-0.0.4 opencv-python-headless-4.12.0.88 outlines_core-0.2.11 packaging-25.0 partial-json-parser-0.2.1.1.post6 pillow-11.3.0 prometheus-fastapi-instrumentator-7.1.0 prometheus_client-0.23.1 propcache-0.3.2 protobuf-6.32.1 psutil-7.1.0 py-cpuinfo-9.0.0 pybase64-1.4.2 pycountry-24.6.1 pycparser-2.23 pydantic-2.11.9 pydantic-core-2.33.2 pydantic-extra-types-2.10.5 pygments-2.19.2 python-dotenv-1.1.1 python-json-logger-3.3.0 python-multipart-0.0.20 pyyaml-6.0.3 pyzmq-27.1.0 ray-2.49.2 referencing-0.36.2 regex-2025.9.18 requests-2.32.5 rich-14.1.0 rich-toolkit-0.15.1 rignore-0.6.4 rpds-py-0.27.1 safetensors-0.6.2 scipy-1.16.2 sentencepiece-0.2.1 sentry-sdk-2.39.0 setproctitle-1.3.7 shellingham-1.5.4 six-1.17.0 sniffio-1.3.1 soundfile-0.13.1 soxr-1.0.0 starlette-0.48.0 sympy-1.14.0 tiktoken-0.11.0 tokenizers-0.22.1 torch-2.8.0+cu126 torchaudio-2.8.0+cu126 torchvision-0.23.0+cu126 tqdm-4.67.1 transformers-4.56.2 triton-3.4.0 typer-0.19.2 typing-inspection-0.4.1 typing_extensions-4.15.0 urllib3-2.5.0 uvicorn-0.37.0 uvloop-0.21.0 vllm-0.11.0rc2.dev27+g69a7cf9b6.cu126 watchfiles-1.1.0 websockets-15.0.1 xformers-0.0.32.post1 xgrammar-0.1.25 yarl-1.20.1

Manual patching:

```
    sed -e "s/.major < 7/.major < 6/g" \
        -e "s/.major >= 7/.major >= 6/g" \
        -i \
        ../conda_env/lib/python3.12/site-packages/torch/_inductor/scheduler.py \
        ../conda_env/lib/python3.12/site-packages/torch/utils/_triton.py
```
  
pip uninstall triton

pip install triton_pascal-3.2.0-cp312-cp312-manylinux2014_x86_64.manylinux_2_17_x86_64.whl (from https://github.com/sasha0552/pascal-pkgs-ci/releases/tag/wheels)
