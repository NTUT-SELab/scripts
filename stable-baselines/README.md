# stable-baselines 腳本

## build_docker.sh
我們可以建置４種版本的image分別是(GPU, GPU-MPI, CPU, CPU-MPI)
通常只有使用(GAIL, DDPG, TRPO, PPO1)需要安裝MPI。因為openMPI有些問題，建議使用沒有MPI的版本。
詳細請參考: [stable-baselines 安裝](https://stable-baselines.readthedocs.io/en/master/guide/install.html#stable-release)

> ### GPU
> ```
> USE_GPU=True ./scripts/build_docker.sh
> ```

> ### GPU-MPI
> ```
> USE_GPU=True INSTALL_MPI=True ./scripts/build_docker.sh
> ```

> ### CPU
> ```
> ./scripts/build_docker.sh
> ```

> ### CPU-MPI
> ```
> INSTALL_MPI=True ./scripts/build_docker.sh
> ```

## run_docker

假如:
```
stable-baselines 專案目錄:
/homes/user/stable-baselines/
```

> ### 運行 GPU 版本
> [Build and run Docker containers leveraging NVIDIA GPUs](https://github.com/NVIDIA/nvidia-docker) 
> ```
> # Default all GPU
> SB_PATH=/homes/user/stable-baselines/ ./run_docker_gpu.sh python train.py
>
> # Starting a GPU enabled container on specific GPUs
> # https://github.com/NVIDIA/nvidia-docker#usage
> GPUS="device=1,2" SB_PATH=/homes/user/stable-baselines/ ./run_docker_gpu.sh python train.py
> ```

> ### 運行 CPU 版本
> ```
> SB_PATH=/homes/user/stable-baselines/ ./run_docker_cpu.sh python train.py
> ```

## run_docker_tensorboard

移動到 tensorboard 紀錄存放資料夾

> ```
> # Default port: 6006
> ./run_docker_tensorboard.sh tensorboard --logdir=./ --host=0.0.0.0
>
> # Port 80
> TARGET_PORT=80 ./run_docker_tensorboard.sh tensorboard --logdir=./ --host=0.0.0.0
> ```
