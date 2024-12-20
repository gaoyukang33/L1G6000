# L1G6000 #
## 安装评测环境 ##       
按照文档引导，使用如下命令安装必要的包       
```
pip install -e .        
pip install -r requirements.txt         
pip install huggingface_hub==0.25.2           
pip install importlib-metadata        
```
## 评测 API 模型 ##     
### 第一步：配置token ###
使用`export INTERNLM_API_KEY=xxxxxxxxxxxxxxxxxxxxxxx # 填入你申请的 API Key`引入token     
![image](https://github.com/gaoyukang33/L1G6000/blob/main/IMG/d23c331f6e13762ab36d161ddfd7885.png)            
### 第二步：配置模型 ###  
在`openai/puyu_api.py`中贴入代码，获取token       
![image](https://github.com/gaoyukang33/L1G6000/blob/main/IMG/7b1795c3bc65c4f53592c7806443c89.png)         
### 第三步：配置数据集 ###
在`demo_cmmlu_chat_gen.py`中贴入代码，这里要注意，`opencompass`的根目录下下还有一个`opencompass`的文件夹，后续我们的操作都是在根目录下的`opencompass`中进行的，而不是在根目录下进行       
![image](https://github.com/gaoyukang33/L1G6000/blob/main/IMG/f742aefd7af22b60eb0e7d9795c8c9d.png)                
### 第四步：评测模型 ###
运行`python run.py --models puyu_api.py --datasets demo_cmmlu_chat_gen.py --debug`完成评测      
![image](https://github.com/gaoyukang33/L1G6000/blob/main/IMG/64a739c63209c3e7363bf8edfe0c2c2.png)       
## 评测本地模型 ##
### 第一步：安装相关包 ###
运行以下命令，安装必要的包     
```
conda install pytorch==2.1.2 torchvision==0.16.2 torchaudio==2.1.2 pytorch-cuda=12.1 -c pytorch -c nvidia -y
apt-get update
apt-get install cmake
pip install protobuf==4.25.3
pip install huggingface-hub==0.23.2
```
### 第二步：加载本地模型进行评测 ###
同上一部分的模型评测一样，对`hf_internlm2_5_1_8b_chat.py`文件进行修改     
![image](https://github.com/gaoyukang33/L1G6000/blob/main/IMG/ea76ef482cf2c1ed10bf0961c2a4f3a.png)     
### 第三步：评测模型 ###
通过以下命令评测 InternLM2-Chat-1.8B 模型在 C-Eval 数据集上的性能         
`python run.py --datasets ceval_gen --models hf_internlm2_5_1_8b_chat --debug`   
运行结果如下：     
![image](https://github.com/gaoyukang33/L1G6000/blob/main/IMG/1734701756996.jpg)   
