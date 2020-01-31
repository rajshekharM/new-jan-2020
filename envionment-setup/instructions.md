# Instructions on setting up the working environment

We provide a docker image for you to work on the test, if you do not have `docker` and `docker-compose` already installed on your device, please follow the instructions on the official website:

- [install `docker`](https://docs.docker.com/install/linux/docker-ce/)
- [install `docker-compose`](https://docs.docker.com/compose/install/)

Once you have `docker` and `docker-compose` successfully installed, inside the environment-setup folder, run the following command:

```shell
sudo docker-compose up --build
```

If the container is built successfully, you will see the following information on terminal:

```shell
Successfully built f29650af971d
Successfully tagged imrsv-ml-test:latest
Starting imrsv-ml-test ... 
Starting imrsv-ml-test_1 ... done
Attaching to imrsv-ml-test_1
imrsv-ml-test_1  | [I 13:13:38.568 NotebookApp] Serving notebooks from local directory: /home/python_user/app
imrsv-ml-test_1  | [I 13:13:38.568 NotebookApp] The Jupyter Notebook is running at:
imrsv-ml-test_1  | [I 13:13:38.568 NotebookApp] http://127.0.0.1:8888/?token=773b66f1d5842802bd9d358d06937d0be6007e2e41d44132
imrsv-ml-test_1  | [I 13:13:38.568 NotebookApp]  or http://127.0.0.1:8888/?token=773b66f1d5842802bd9d358d06937d0be6007e2e41d44132
imrsv-ml-test_1  | [I 13:13:38.568 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
imrsv-ml-test_1  | [C 13:13:38.573 NotebookApp] 
```

Copy and paste the url `http://127.0.0.1:8888/?token=773b66f1d5842802bd9d358d06937d0be6007e2e41d44132` into your browser to start `jupyter notebook`. Please see README.md for the test.

## FAQ

1. The Jupyter Notebook link won't open in browser.

If you are using Windows 10 and Docker toolbox, there would be a line on top of Docker terminal:
`docker is configured to use default machine with IP xxxx.xx.xxx`,
please use replace `127.0.0.1` with this IP. 

For more details, please refer to [this issue](https://github.com/jupyter/docker-stacks/issues/634#issuecomment-387318354)
