# Rasa中文demo

本文代码需配合以下博文使用，目前教程还在更新中，demo也会持续更新

[Rasa使用指南01](https://terrifyzhao.github.io/2018/09/17/Rasa%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%9701.html)

[Rasa使用指南02](https://terrifyzhao.github.io/2019/02/26/Rasa%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%9702.html)

### 如何使用

cd 到对应的demo路径下执行以下命令

训练rasa_core
```
python -m rasa_core.train -d domain.yml -s stories.md -o models/dialogue -c policy_config.yml
```


训练rasa_nlu
```
python -m rasa_nlu.train -c nlu_config.yml --data nlu.md -o models --fixed_model_name nlu --project current --verbose
```

如果有自定义action，请执行此命令，注意把此处的`action_name`换成自定义的action的文件名，如果你的action文件叫做action.py，则写--actions action
```
python -m rasa_core_sdk.endpoint --actions action_name
```

启动对话
```
python -m rasa_core.run -d models/dialogue -u models/current/nlu --endpoints endpoints.yml
```
