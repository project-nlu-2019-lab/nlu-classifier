## train+evaluation
调用 run_classifier_nlu_0.py 函数
python run_classifier_nlu_0.py \
  --task_name=nlu \
  --do_train=true \
  --do_eval=true \
  --data_dir=/home1/lzj2019/lab/nlu/bert-master/dataset \
  --vocab_file=/home1/lzj2019/lab/nlu/bert-master/chinese_L-12_H-768_A-12/vocab.txt \
  --bert_config_file=/home1/lzj2019/lab/nlu/bert-master/chinese_L-12_H-768_A-12/bert_config.json \
  --init_checkpoint=/home1/lzj2019/lab/nlu/bert-master/chinese_L-12_H-768_A-12/bert_model.ckpt \
  --max_seq_length=32 \
  --output_dir=/home1/lzj2019/lab/nlu/bert-master/tmp/nlu_output/


## 调用 prediction
直接调用 main 函数：

```
main(
        DATA_DIR = "dataset",  # 预测数据存放位置
        BERT_CONFIG_FILE = "chinese_L-12_H-768_A-12/bert_config.json",
        TASK_NAME = "nlu",
        VOCAB_FILE = "chinese_L-12_H-768_A-12/vocab.txt",
        OUTPUT_DIR = "tmp/nlu_output",
        INIT_CHECKPOINT = "chinese_L-12_H-768_A-12/bert_model.ckpt",  # checkpoint
        DO_LOEWR_CASE = True,
        MAX_SEQ_LENGTH = 128,
        DO_TRAIN = False,
        DO_EVAL = False,
        DO_PREDICT = True
      )
```

函数返回：
```
[[样本1对应各个标签预测分数],
...,
[样本n对应各个标签预测分数]]
```
example:
```
[[0.08273943, 0.08760738, 0.1262754, 0.22605933, 0.09481912, 0.21038206, 0.17211731], [0.08268463, 0.104869336, 0.12503317, 0.24566595, 0.09843083, 0.18239415, 0.16092198], [0.08268463, 0.104869336, 0.12503317, 0.24566595, 0.09843083, 0.18239415, 0.16092198], [0.08268463, 0.104869336, 0.12503317, 0.24566595, 0.09843083, 0.18239415, 0.16092198], [0.08268463, 0.104869336, 0.12503317, 0.24566595, 0.09843083, 0.18239415, 0.16092198], [0.08268463, 0.104869336, 0.12503317, 0.24566595, 0.09843083, 0.18239415, 0.16092198], [0.08268463, 0.104869336, 0.12503317, 0.24566595, 0.09843083, 0.18239415, 0.16092198]]
```