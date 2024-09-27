---
description: Bring Your Own Model
---

# Integrating ORA's AI Oracle

In this tutorial we explain how to integrate your own AI model with ORA's AI Oracle. We will start by looking at [mlgo](https://github.com/OPML-Labs/mlgo) repository and trying to understand what's happening there. At the end we will showcase how [opML](https://github.com/ora-io/opml) works, by running a simple dispute game script inside a docker container.

### Learning Objectives

* Understand how to transform an AI model inference code and integrate it with ORA's AI Oracle&#x20;
* Execute a simple dispute game and understand the process of AI inference verification.

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

### Running the dispute game

Now that we compiled our AI model and inference code into MIPS VM executable code.

We can test the dispute game process. We will use a [bash script](https://github.com/ora-io/opml/blob/main/demo/challenge\_simple.sh) from opml repository to showcase the whole verification flow.

For this part of the tutorial we will use [Docker](https://www.docker.com/), so make sure to have it installed.

Let's first check the content of the [Dockerfile](https://github.com/ora-io/opml/blob/main/Dockerfile) that we are using:

1. First we need to specify the operating system that runs inside our container. In this case we're using ubuntu:22.04.

```docker
# How to run instructions:
# 1. Generate ssh command: ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
#    - Save the key in local repo where Dockerfile is placed as id_rsa
#    - Add the public key to the GitHub account
# 2. Build docker image: docker build -t ubuntu-opml-dev .
# 3. Run the hardhat: docker run -it --rm --name ubuntu-opml-dev-container ubuntu-opml-dev bash -c "npx hardhat node"
# 4. Run the challange script on the same container: docker exec -it ubuntu-opml-dev-container bash -c "./demo/challenge_simple.sh"


# Use an official Ubuntu as a parent image
FROM ubuntu:22.04
```

2. Then we need to install all the necessary dependencies in order to run [dispute game script](https://github.com/ora-io/opml/blob/main/demo/challenge\_simple.sh).

```docker
# Set environment variables to non-interactive to avoid prompts during package installations
ENV DEBIAN_FRONTEND=noninteractive

# Update the package list and install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    git \
    golang \
    wget \
    curl \
    python3 \
    python3-pip \
    python3-venv \
    unzip \
    file \
    openssh-client \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install Node.js and npm
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs
```

3. Then we configure ssh keys, so that docker container can clone all the required repositories.

```docker
# Copy SSH keys into the container
COPY id_rsa /root/.ssh/id_rsa
RUN chmod 600 /root/.ssh/id_rsa
# Configure SSH to skip host key verification
RUN echo "Host *\n\tStrictHostKeyChecking no\n" >> /root/.ssh/config
```

4. Position to the root directory inside docker container and clone opml repository along with its submodules.

```docker
# Set the working directory
WORKDIR /root

# Clone the OPML repository
RUN git clone git@github.com:ora-io/opml.git --recursive
WORKDIR /root/opml
```

5. Lastly, we tell docker to build executables and run the challenge script.

```docker
# Build the OPML project
RUN make build

# Change permission for the challenge script
RUN chmod +x demo/challenge_simple.sh

# Default command
CMD ["bash"]
```

#### Create docker container and run the script

1.  In order to successfully clone opml repository, you need to generate a new ssh key and add it to your Github account. Once it's generated, save the key in the local repository where Dockerfile is placed as `id_rsa`. Then add the public key to your GitHub account.\


    ```bash
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```


2.  Build the docker image\


    ```sh
    docker build -t ubuntu-opml-dev .
    ```


3.  Run the local Ethereum node\


    ```sh
    docker run -it --rm --name ubuntu-opml-dev-container ubuntu-opml-dev bash -c "npx hardhat node"
    ```


4.  In another terminal run the challenge script\


    ```bash
    docker exec -it ubuntu-opml-dev-container bash -c "./demo/challenge_simple.sh"
    ```



After executing the steps above you should be able to see interactive challenge process in the console.&#x20;

Script first deploys necessary contracts to the local node. Proposer opML node executes AI inference and then the challenger nodes can dispute it, if they think that the result is not valid. Challenger and proposer are interacting in order to find the differing step between their computations. Once the dispute step is found it's sent to the smart contract for the arbitration. If the challenge is successful the proposer node gets slashed.

### Conclusion

In this tutorial we achieved the following:

* converted our AI model from Python to ggml format
* compiled AI inference code written in go to MIPS VM executable format
* run the dispute game inside a docker container and understood the opML verification process

### Next steps

In order to use your AI model onchain, you need to run your own opML nodes, then this AI model will be able to integrated into OAO. Try to reproduce this tutorial with your own model.
