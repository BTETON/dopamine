# dopamine chinese

## 学习过程补充
<div align="center">
  <img src="https://raw.githubusercontent.com/BTETON/dopamine/BTETON-dev/Screenshot_2018-09-28%20TensorBoard.png"><br><br>
</div>
修改 dopamine/agents/dqn/configs/dqn.gin

...
# 变更前
#Runner.num_iterations = 200
#Runner.training_steps = 250000  # agent steps
#Runner.evaluation_steps = 125000  # agent steps
#Runner.max_steps_per_episode = 27000  # agent steps

# 変更後
Runner.num_iterations = 20
Runner.training_steps = 2500  # agent steps
Runner.evaluation_steps = 1250  # agent steps
Runner.max_steps_per_episode = 270  # agent steps
...
这样操作简化了，gtx1060只需要大概10分钟甚至更少，注意是否使用 -um 参数

python dopamine/atari/train.py   --agent_name=dqn   --base_dir=/tmp/dopamine   --gin_files='dopamine/agents/dqn/configs/dqn.gin'

训练完成后，模型会保存在/tmp目录下
```
ls /tmp/dopamine
# checkpoints  events.out.tfevents.xxxx  logs

tensorboard --logdir=/tmp/dopamine
```
这样就可以看到模型训练情况了 http://localhost:6006

## 参考

    https://ai.googleblog.com/2018/08/introducing-new-framework-for-flexible.html
    http://ensekitt.hatenablog.com/entry/2018/01/28/200000
    https://qiita.com/uni-3/items/643e25027981adc5b201

