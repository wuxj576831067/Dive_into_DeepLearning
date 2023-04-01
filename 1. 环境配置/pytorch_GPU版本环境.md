
### 验证Pytorch+CUDA是否可用

```py

#判断是否安装了cuDNN
import torch
from torch.backends import  cudnn
import torch # 如果pytorch安装成功即可导入
print(torch.cuda.is_available()) # 查看CUDA是否可用
print(torch.cuda.device_count()) # 查看可用的CUDA数量
print(torch.version.cuda) # 查看CUDA的版本号
print(cudnn.is_available())  #返回True则说明已经安装了cuDNN


ngpu= 1
# Decide which device we want to run on
device = torch.device("cuda:0" if (torch.cuda.is_available() and ngpu > 0) else "cpu")
print(device)
print(torch.cuda.get_device_name(0))
print(torch.rand(3,3).cuda())
```



[更新nvidia显卡驱动](https://www.nvidia.cn/geforce/drivers/)

[NVIDIA-SMI命令系列详解](https://blog.csdn.net/handsome_bear/article/details/80903477)

[pytorch+cuda配置](https://zhuanlan.zhihu.com/p/106133822)

- 首先，根据本机cuda版本找到安装指令：https://pytorch.org/
👴神舟电脑上为CUDA11.4，所以
        
        conda install pytorch torchvision torchaudio cudatoolkit=11.3 
>小于电脑cuda版本即可，最好把-c pytorch删掉，否则默认用国外源，非常慢


[anaconda+pytorch](https://blog.csdn.net/qq_41282258/article/details/98961667?ops_request_misc=&request_id=&biz_id=102&utm_term=anaconda%E5%AE%89%E8%A3%85pytorch&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-98961667.pc_search_result_hbase_insert&spm=1018.2226.3001.4187)


[循环神经网络](https://zhuanlan.zhihu.com/p/123211148)

>现在换源中科大比较好，清华源有点问题：

    conda config --remove-key channels
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
    conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
    conda config --set show_channel_urls yes
    pip config set global.index-url https://mirrors.ustc.edu.cn/pypi/web/simple


> 踩坑：用了垃圾源，会下载CPU版本的！！！！
>  解决方法：卸载重装 科大源没有就加上 -c pytorch