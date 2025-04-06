# 🚀 Installing vLLM + Triton on GH200
This guide provides a setup for running `vLLM` with `Triton` on NVIDIA GH200.

---

## 🔧 Step 1: Create Conda Environment

```bash
conda create -n env_vllm python=3.12 -y
conda activate env_vllm
```

## 🔥 Step 2: Install PyTorch Nightly

```bash
pip install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/cu126
```

## 📦 Step 3: Install vLLM from Source

```bash
git clone https://github.com/vllm-project/vllm.git
cd vllm
python use_existing_torch.py
pip install -r requirements/build.txt
export MAX_JOBS=32      #Important
pip install -e . -v --no-build-isolation
```

## ⚙️ Step 4: Install Triton from Source

```bash
cd ..
git clone https://github.com/triton-lang/triton.git
cd triton
pip install -r python/requirements.txt
export MAX_JOBS=4      #Important
pip install -v -e python
export PYTHONPATH=~/your-project/triton/python:$PYTHONPATH      #Important
```

---

## ✅ You're All Set!

With this setup, you can now run **vLLM** efficiently on **GH200**, an **aarch64-based architecture**. It's now **possible to serve large-scale models like LLaMA3.1-70B on a single GPU**, by offloading part of the model weights to CPU memory.

Happy inferencing! 🚀

