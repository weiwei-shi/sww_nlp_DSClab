# Table-BERT+GNN操作文档

### 1.配置环境

1. python=3.6.13

2. pytorch=1.9.0

   `conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch`

3. transformers=2.6.0

   `pip install transformers==2.6.0`

4. tensorboardX=2.4

   `pip install tensorboardX`

5. pandas=0.25.1

   `conda install pandas=0.25.1`

6. allennlp==0.9.0

   `pip install allennlp==0.9.0`

   > 注：如果安装allennlp时遇到报错ERROR: Failed building wheel for jsonnet，执行`conda install -c conda-forge jsonnet`

### 2.训练过程

1. 下载代码文件

   `git clone  https://github.com/wenhuchen/GNN-TabFact.git`

2. 在代码文件里创建文件夹存放模型

   `mkdir models`

3. 下载预训练模型

   `ln -s TABFACT/data/all_csv`

   `cd models`

   `wget https://gnntabfact.s3-us-west-2.amazonaws.com/gnn_fp16_numeric.zip`

   `unzip gnn_fp16_numeric.zip`

4. 进入代码文件里加载GNN模型训练结果

   `CUDA_VISIBLE_DEVICES=0 python gnn.py --model bert-base-multilingual-uncased --do_test --encoding gnn --load_from models/gnn_fp16_numeric/model_ep4.pt`

   > 注：遇到ModuleNotFoundError: No module named 'google'问题，执行
   >
   > `pip install google`
   >
   > `conda install protobuf`

5. 重新训练模型

   `CUDA_VISIBLE_DEVICES=0 python gnn.py --model bert-base-multilingual-uncased --do_train --encoding gnn --output_dir models/gnn_fp16_numeric_test --attention cross --lr_default 5e-6`

   > 注：如果遇到提示说all_csv里某个文件没有，就删去all_csv的链接，直接下载TabFact数据集
   >
   > `git clone <https://github.com/wenhuchen/Table-Fact-Checking.git`>
   >
   > 然后将其中的all_csv文件移动到GNN-TabFact目录里
   >
   > `mv all_csv /wwtorch/GNN-TabFact`（后面是GNN-TabFact目录的绝对地址）

6. 得到结果

   4的结果：0.7225134987088192

   ![result4](images\4result.png)

   5的结果：最高0.7105407308866108

   ![result5](images\5result.png)

