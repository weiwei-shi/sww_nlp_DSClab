# TableBert操作文档

1. python=3.5
   `conda create -n TableBert python=3.5`
   `activate TableBert`

2. pytorch=1.2.0
   `conda install pytorch==1.2.0 torchvision==0.4.0 cudatoolkit=10.0 -c pytorch`

3. ujson
   `pip install ujson`

4. pytorch-pretrained-bert
   `pip install pytorch-pretrained-bert`

   > **注：**
   >
   > 1. error: Microsoft Visual C++ 14.0 is required.
   >    使用solved_packageMissInInstalling_mu_visual_cpp_build_tools_2015_update_3_x64_dvd_dfd9a39c安装包安装Microsoft Visual C++ 14.0
   > 2. ERROR: Failed building wheel for regex
   >    cmd运行
   >    docker cp C:\Users\dscl\Desktop\regex-2020.1.8-cp35-cp35m-win_amd64.whl b3520091246919b0cdaa5124a977e9bb87dfdc7938d41b5b17ae100cf5c3b73f:/wwtorch/regex-2020.1.8-cp35-cp35m-win_amd64.whl
   >    容器中运行
   >    `pip install "F:\regex-2020.1.8-cp35-cp35m-win_amd64.whl"`

5. pandas
   `pip install pandas`

6. tqdm
   `pip install tqdm/conda install -c conda-forge tqdm`

7. tensorboardX
   `pip install tensorboardX`

8. unidecode
   `pip install unidecode`

9. nltk
   `pip install -U nltk`
   进入python

   > -- import nltk
   > -- nltk.download()
   > 选择d和l
   > 如果下载不成功，可以手动安装，下载nltk_data到本地，在python中
   > -- nltk.download('punkt')
   > 得到多个路径
   > 将nltk_data放入其中一个路径`D:\\Anaconda3.5\\envs\\TableBert\\nltk_data`
   > 容器中直接放入路径/usr/local/lib

10. 运行
    `cd code/`
    `python run_BERT.py --do_train --do_eval --scan horizontal --fact first`

    > **注：**
    >
    > 1. ImportError: No module named 'scipy'
    >    `pip install scipy`
    >
    > 2. ImportError: No module named 'sklearn'
    >    `pip install sklearn`
    >
    > 3. RuntimeError: CUDA out of memory.
    >
    >    尚未解决

