# ChatGLM6B_lora_finetunig
Finetuing chatglm-6b LLM base on peft and huggingface   

使用huggingface和peft中的lora对chatglm6b模型进行微调   

- 成功运行时占用显存27G左右（输入输出长度512），如果显卡只有24G可以降低输入输出长度；   
- 文件里有较多注释，可以简单看懂；
- 依赖库较少，较大概率可以一次跑通；
- 如果使用huggingface官方镜像则只需要安装peft则可以运行；
- deepspeed文件夹里有使用ds的案例，以及使用deepspeed的情况说明（deepspeed里的训练文件版本较老，还有一些冗余代码）。

```bash
# 拉取huggingface官方镜像
docker pull huggingface/transformers-all-latest-gpu

# 进入huggingface镜像，显卡设置全部可见，将当前目录映射到容器内的/home/myprojects文件夹，将宿主机的10086端口映射到容器的8888端口，并且进入命令行模式
# 需求宿主机装好nvidia驱动
# 8888是jupyter notebook的默认端口
docker run -itd --gpus all -v $PWD:/home/myprojects -p 10086:8888 huggingface/transformers-all-latest-gpu:latest /bin/bash 
```
```bash
# 进入容器后
pip install peft 
# 或使用清华源加速
pip install peft -i https://pypi.tuna.tsinghua.edu.cn/simple  
```

在容器内运行jupyter notebook需要提前进行一些配置，过程较简单，网络教程多，不再赘述。

配置完成启动后，外部浏览器输入xxx.xxx.xxx.xxx:10086(宿主机地址)即可访问容器内的notebook。

或者也可以将jupyter notebook转换为py文件直接在容器内运行。

# files
```
--
|--deepspeed--
|            |--chatglm-lora-ds.ipynb  # Fitune ChatGLM-6B model using deepspeed
|            |--ds_config_zero2.json   # config of deepspeed (zero2 strategy)
|            |--ds_config_zero3.json   # config of deepspeed (zero3 strategy)
|--chatglm-lora-finetune.ipynb  # Finetune your own ChatGLM-6b model.
|--chatglm-lora-inference.ipynb  # Read model paramaters and inference using own data.
|--README.md
|--requirement.txt
```

# reference

https://aizpy.com/2023/03/30/chatglm-6b-lora/#预测
