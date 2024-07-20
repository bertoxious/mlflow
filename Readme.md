Get started with mlflow
```bash
pip install mlflow
mlflow ui
```


Create and start an experiment

```python
import mlflow

experiment = mlflow.set_experiment(experiment_name='NAME_OF_EXPERIMENT',experiment_id="test")

with mlflow.start_run(experiment_id=experiment.id):
        """
            Here comes the logic to run the model
        """
```


After running mlflow ui here is the output folder structure


*Experiment folder structure*
```tree
├── mlruns
├────trash(stores the deleted runs and experiments)
|────0
|──────meta.yaml
|────experiment_id(creates a folder with experiment_id which is randdomly generated in case not provided and remains same for each experiment)
├──────meta.yml(contains the meta data information of experiment)
|──────multiple Runs folder(This can have one to many run folders depending upon the number of runs done by the user)

```

meta.yml values
```yml
artifact_uri: file:///Users/ashishuniyal/Downloads/ml-flow/mlruns/606783375233873416/1c6b2d5b909041df93e6e00b960de019/artifacts
end_time: 1721450907230
entry_point_name: ''
experiment_id: '606783375233873416'
lifecycle_stage: active
run_id: 1c6b2d5b909041df93e6e00b960de019
run_name: wistful-ant-659
run_uuid: 1c6b2d5b909041df93e6e00b960de019
source_name: ''
source_type: 4
source_version: ''
start_time: 1721450907221
status: 4
tags: []
user_id: ashishuniyal
```

*Run folder structure*

```tree
├── 1c6b2d5b909041df93e6e00b960de019
├──── artifacts
|     ├─── mymodel
|     |    ├─── conda.yml
|     |    ├─── ML model
|     |    ├─── model.pkl
|     |    ├─── python_env.yml
|     |    ├─── requirements.txt
├──── metrics (contains all the metrics logs with each metric file name in mlflow.log_metric("", metric))
|     ├──── metric_one
|     ├──── metric_two
|     ├──── metric_three
├──── params (contains all the params logs with each log file name in mlflow.log_param("", metric))
|     ├──── param_one
|     ├──── param_two
├──── tags (contains other meta data for the run)
├──── meta.yml (contains meta data of the run just like in experiment meta.yml)
```