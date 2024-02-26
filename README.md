Building docker image

This will download and install the required packages.

Using CPU

docker-compose build stablediff-cpu

Using CUDA

docker-compose build stablediff-cuda

Using ROCm

docker-compose build stablediff-rocm

Setting up launch parameter

Edit stablediff.env to match your use cases.

You can also add launch parameter such as --lowvram.


Using CPU
export COMMANDLINE_ARGS="--listen --no-half --skip-torch-cuda-test"
Using CUDA
export COMMANDLINE_ARGS="--listen"
Using ROCm
export COMMANDLINE_ARGS="--listen --precision full --no-half"

Initial run
This will create two directory called stablediff-web and stablediff-models.
After initial run, you will get message about missing Stable Diffusion ckpt model.
Grab one and copy it to stablediff-models. in linux, you might need sudo to
do this.

Using CPU
docker-compose up stablediff-cpu
Using CUDA
docker-compose up stablediff-cuda
Using ROCm
docker-compose up stablediff-rocm
Subsequent run
Use the command below every time you want to run Stable Diffusion.

Using CPU
docker start -a stablediff-cpu-runner
Using CUDA
docker start -a stablediff-cuda-runner
Using ROCm
docker start -a stablediff-rocm-runner
Stopping Stable Diffusion
To stop Stable Diffusion press Ctrl + C and use the command below.

Using CPU
docker stop stablediff-cpu-runner
Using CUDA
docker stop stablediff-cuda-runner
Using ROCm
docker stop stablediff-rocm-runner


Source: https://github.com/AUTOMATIC1111/stable-diffusion-webui/discussions/5049
