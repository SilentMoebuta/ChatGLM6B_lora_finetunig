# ChatGLM6B_lora_finetunig
Finetuing chatglm-6b LLM base on peft and huggingface   

使用huggingface和peft中的lora对chatglm6b模型进行微调   

成功运行时占用显存20+G   

文件里有较多注释，可以简单看懂   

依赖库较少，较大概率可以一次跑通   

如果使用huggingface官方镜像则只需要安装peft则可以运行   

deepspeed文件夹里有使用ds的案例，以及使用deepspeed的情况说明

```
docker pull huggingface/transformers-all-latest-gpu
```
```
pip install peft
# pip install peft -i https://pypi.tuna.tsinghua.edu.cn/simple  
```


# reference
https://aizpy.com/2023/03/30/chatglm-6b-lora/#预测

# files
```
--
|--deepspeed--
|			|--chatglm-lora-ds.ipynb  # Fitune ChatGLM-6B model using deepspeed
|			|--ds_config_zero2.json   # config of deepspeed (zero2 strategy)
|			|--ds_config_zero3.json   # config of deepspeed (zero3 strategy)
|--chatglm-lora-finetune.ipynb  # Finetune your own ChatGLM-6b model.
|--chatglm-lora-inference.ipynb  # Read model paramaters and inference using own data.
|--README.md
|--requirement.txt
```
