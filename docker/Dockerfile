FROM python:3.11-slim

# Instalar herramientas y dependencias del sistema
RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    curl \
    wget \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Instalar PyTorch + CUDA (desde pip)
RUN pip install --upgrade pip
RUN pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118

# Instalar dependencias de Gemma
RUN pip install numpy==1.24.4 sentencepiece==0.1.99

# Copiar el código de Gemma
COPY . /workspace/gemma/
WORKDIR /workspace/gemma/

# Instalar Gemma
RUN pip install -e .

CMD ["python"]
