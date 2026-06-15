# CUDA Colab Runner Template

A beginner-friendly Google Colab template for running CUDA/C++ code on a GPU without needing a local NVIDIA GPU.

I made this because I was learning CUDA, but my laptop did not have an NVIDIA GPU. Google Colab was the easiest way for me to test CUDA code, so this template helps make that workflow simpler.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MashrafeeAryan/cuda-colab-runner-template/blob/main/CUDA_Colab_Runner_Template.ipynb)

---

## What This Template Does

This notebook helps you:

* Check if Colab is connected to an NVIDIA GPU
* Check if `nvcc` is available
* Clone your GitHub repository into Colab
* Compile CUDA/C++ code
* Run the compiled executable

---

## Who This Is For

This template is useful if:

* You are learning CUDA
* You do not have an NVIDIA GPU on your laptop
* You want to test CUDA code using Google Colab
* You want a simple example of compiling CUDA code with `nvcc`

---

## How to Use

### 1. Open the Notebook

Click the **Open in Colab** button above.

---

### 2. Turn On GPU Runtime

Before running the notebook, turn on the GPU runtime.

From the top menu in Colab, go to:

```text
Runtime → Change runtime type → T4 GPU → Save
```

After that, run the notebook cells from top to bottom.

---

### 3. Push Your Code to GitHub First

This notebook pulls your project from GitHub.

Make sure your latest code is already pushed to the **main branch** of your GitHub repository before running the clone cell.

If your code is only saved on your laptop or in VS Code, Colab cannot access it yet.

Simple flow:

```text
Write code locally
→ push to GitHub
→ open this notebook
→ clone the repo in Colab
→ compile and run CUDA code
```

---

### 4. Set Your Repo Information

In the notebook, update these values:

```python
folderName = "YOUR_REPO_FOLDER_NAME"
githubRepo = "YOUR_GITHUB_REPO_URL"
```

Example:

```python
folderName = "CUDA-Neural-Network-Engine"
githubRepo = "https://github.com/MashrafeeAryan/CUDA-Neural-Network-Engine.git"
```

---

### 5. Set Your Compile Information

Update these values for your own project:

```python
executableName = "my_cuda_program"
includePath = "include"

sourceFiles = [
    "src/main.cu",
    "src/helper.cpp"
]
```

Then the notebook will build an `nvcc` command automatically.

Example:

```python
compileCommand = f"nvcc -I {includePath} {' '.join(sourceFiles)} -o {executableName}"
```

---

## Example Compile Command

For a project with CUDA and C++ source files, the final command may look like:

```bash
nvcc -I include src/cuda/CUDA_MatrixMult.cu src/matrix/Matrix.cpp benchmarks/benchmark_matrix_cpu_vs_cuda.cu -o benchmark_matrix_cpu_vs_cuda
```

Then the notebook runs:

```bash
./benchmark_matrix_cpu_vs_cuda
```

---

## Important Note

This template does not automatically switch Colab from CPU to GPU.

You still need to manually choose the GPU runtime:

```text
Runtime → Change runtime type → T4 GPU → Save
```

If you see:

```text
nvidia-smi: command not found
```

it usually means the notebook is not connected to a GPU runtime.

---

## Limitations

* Google Colab GPU availability is not guaranteed.
* The notebook cannot fully automate switching from CPU runtime to GPU runtime.
* This is meant to be a simple beginner-friendly template, not a full cloud deployment system.
* For private GitHub repositories, you may need extra authentication steps.

---

## Why I Made This

While working on CUDA code, I wanted an easy way to test my code without having a local NVIDIA GPU.

I originally wanted to fully automate the process from VS Code to GitHub to Colab, but I learned that normal Colab does not reliably allow switching from CPU to GPU through code.

So I made this simple template to help students and beginners run CUDA code on Colab with fewer setup steps.

---

## Feedback

If you work with CUDA, cloud GPUs, Colab, or developer tooling, I would appreciate suggestions on how to improve or better automate this workflow.
