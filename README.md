# PyTorch
Cuda Installation
Ya, tentu bisa! Instalasi Python dan CUDA di Windows sangat memungkinkan dan cukup straightforward. Berikut langkah-langkahnya:

## Instalasi Python

**Opsi 1: Download langsung dari python.org**
- Kunjungi https://www.python.org/downloads/
- Download versi terbaru Python (3.11 atau 3.12 recommended)
- Jalankan installer dan pastikan centang "Add Python to PATH"

**Opsi 2: Menggunakan Anaconda/Miniconda** (recommended untuk data science)
- Download Anaconda dari https://www.anaconda.com/
- Installer sudah include banyak package scientific computing

## Instalasi CUDA

**Langkah 1: Cek GPU NVIDIA**
- Pastikan PC memiliki GPU NVIDIA yang support CUDA
- Buka Device Manager → Display adapters untuk mengecek

**Langkah 2: Download CUDA Toolkit**
- Kunjungi https://developer.nvidia.com/cuda-downloads
- Pilih Windows → versi Windows Anda → x86_64
- Download dan install CUDA Toolkit (versi 11.8 atau 12.x)

**Langkah 3: Install cuDNN (opsional tapi recommended)**
- Download dari https://developer.nvidia.com/cudnn
- Extract dan copy file ke folder CUDA installation

## Verifikasi Instalasi

Setelah instalasi, buka Command Prompt dan test:

```bash
# Test Python
python --version

# Test CUDA
nvcc --version

# Test di Python
python -c "import torch; print(torch.cuda.is_available())"
```

Apakah ada spesifikasi khusus untuk project yang akan dikerjakan? Ini bisa membantu menentukan versi CUDA yang tepat.

Bagus! Instalasi Python dan CUDA sudah berhasil, tapi ada satu masalah yang perlu diperbaiki:

## Status Instalasi Anda:
✅ **Python 3.11.0rc2** - Terinstall dengan baik
✅ **CUDA 12.9** - Terinstall dengan baik
❌ **PyTorch** - Belum detect CUDA (menunjukkan `False`)

## Solusi untuk PyTorch + CUDA:

PyTorch yang terinstall sepertinya versi CPU-only. Anda perlu install versi yang support CUDA:

**Uninstall PyTorch yang sekarang:**
```bash
pip uninstall torch torchvision torchaudio
```

**Install PyTorch dengan CUDA support:**
```bash
# Untuk CUDA 12.x (sesuai dengan CUDA 12.9 Anda)
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
```

**Atau menggunakan conda (jika pakai Anaconda):**
```bash
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
```

## Verifikasi ulang setelah reinstall:
```bash
python -c "import torch; print(f'CUDA available: {torch.cuda.is_available()}'); print(f'CUDA version: {torch.version.cuda}'); print(f'Device count: {torch.cuda.device_count()}')"
```

Setelah ini, PyTorch seharusnya bisa detect dan menggunakan GPU NVIDIA Anda. Coba jalankan perintah di atas dan lihat hasilnya!

# TensorFlow