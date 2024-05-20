---
description: Bring Your Own Model into OAO
---

# Integration into OAO - Tutorial

In this tutorial we explain how to integrate your own AI model into Onchain AI Oracle (OAO). We will start by looking at [mlgo](https://github.com/OPML-Labs/mlgo) repository and trying to understand what's happening there.

### Learning Objectives

* Understand how to transform AI model and inference code in order to integrate it into Onchain AI Oracle (OAO).

### Prerequisites

* [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) installed

### Setup

1. Clone [mlgo](https://github.com/ora-io/opml/tree/main) repository

```sh
git clone git@github.com:OPML-Labs/mlgo.git
```

2. Navigate to cloned repository

```bash
cd mlgo
```

3. To install the required dependencies for your project, run the following command:

```python
pip install -r requirements.txt
```

If there are some missing dependencies, make sure to install them in your Python environment.

### Train the model using Pytorch

First we need to train a DNN model using Pytorch. The training part is shown in  _examples/mnist/trainning/mnist.ipynb._

After the training model is saved at _examples/mnist/models/mnist/mnist-small.state\_dict._

### Convert model into ggml format

[Ggml](https://github.com/ggerganov/ggml) is a file format that consists of version number, followed by three components that define a large language model: the model's hyperparameters, its vocabulary, and its weights. Ggml allows for more efficient inference runs on CPU. We will now convert the Python model to ggml format by executing following steps:

1. Position to mnist folder

```bash
cd examples/mnist
```

2. Convert python model into ggml format

```python
python3 convert-h5-to-ggml.py models/mnist/mnist-small.state_dict
```

In order to convert AI model written in Python to ggml format we are executing python script and providing a file that stores the model as a parameter to the script. The output is the binary file in ggml format. Note that the model is saved in big-endian, making it easy to process in the big-endian MIPS-32 VM.

### Converting inference code to MIPS VM executable

Next step is to write inference code in go language. Then we will transform go binary into MIPS VM executable file.&#x20;

Go supports compilation to MIPS. However, the generated executable is in ELF format. We'd like to get a pure sequence of MIPS instructions instead. To build a ML program in MIPS VM execute the following steps:

1. Navigate to the mnist\_mips directory and build go inference code

```bash
cd ../mnist_mips && ./build.sh
```

Build script will compile go code and then run [compile.py](https://github.com/OPML-Labs/mlgo/blob/6b6d69394efc7268160a4b5218488e1b8f6b9795/compile.py) script that will transform compiled go code to the MIPS VM executable file.

### Conclusion

In this tutorial we achieved the following:

* converted our AI model from Python to ggml format
* compiled AI inference code written in go to MIPS VM executable format

### Next steps

In order to use your model with Opml check the following [tutorial](https://github.com/ora-io/opml/blob/main/docs/tutorial.md).

In order to use your AI model onchain, you need to run your own Opml nodes and write your own contracts for the dispute game.
