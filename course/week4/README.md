# Week 4 Project: Retrieval augmented generation

```
pip install -e .
```

This project will explore data-centric approaches to building high quality RAG systems.

### Setup

Please copy the `.env.template` to a `.env` file. 
- Please ask the teaching team for an OpenAI API key to use GPT 3.5. You will set this key to the `OPENAI_API_KEY` variable in `.env`.
- Please ask the teaching team for a Starpoint API key to use the Starpoint vector db. You will set this key to the `STARPOINT_API_KEY` variable in `.env`.

### Project

There is code for you to complete in the following files

- `scripts/build_eval_set.py`
- `scripts/insert_docs.py`
- `scripts/optimizer_params.py`

We recommend you to follow the instructions on Uplimit closely.

## Final Hyperparameters

The following are the final hyperparameters chosen for deployment of the RAG system:

- **questions_file**: `data/questions/questions.csv`
- **starpoint_api_key**: `YOUR_STARPOINT_API_KEY`
- **embedding_model**: `thenlper/gte-small`
- **max_workers**: `1`
- **text_search_weight**: `0.0`
- **hyde**: `False`

These hyperparameters were selected based on extensive experimentation and evaluation to ensure optimal performance of the RAG system.


## Results

|hit_rate|embedding|text_search_weight|hyde_embeddings
|-------------------|:------------------:|:------------------:|---------------:|
|0.9898477157360406|thenlper/gte-small|0.0|False
|0.9898477157360406|thenlper/gte-small|0.5|False
|0.9695431472081218|all-MiniLM-L6-v2|0.5|False
|0.868020304568528|thenlper/gte-small|0.0|True
|0.8527918781725888|thenlper/gte-small|0.5|True
|0.8477157360406091|all-MiniLM-L6-v2|0.0|True
|0.9695431472081218|all-MiniLM-L6-v2|0.0|False
|0.8426395939086294|all-MiniLM-L6-v2|0.5|True

## Explanation

Due to the stupid data.zip file of 3 GB that can not be committed my whole codespaces got unstable and none of my code could be committed. 
Add this in your gitignore or provide some better solution for this. Not redoing all the work this time.

## RAW Terminal Output

``` bash
    scripts/optimize_params.py:1:0: F0002: /workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py: Fatal error while checking '/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py'. Please open an issue in our bug tracker so we address this. There is a pre-filled template that you can use in '/home/vscode/.cache/pylint/pylint-crash-2024-08-04-20-05-10.txt'. (astroid-error)
    Pylint is not happy:
    Fix Pylint warnings listed above or say --no-pylint.

@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ python scripts/optimize_params.py --no-pylint
Metaflow 2.12.7 executing OptimizeRagParams for user:vscode
Validating your flow...
    The graph looks good!

'/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py show' shows a description of this flow.
'/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py run' runs the flow locally.
'/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py help' shows all available commands and options.

@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ python scripts/optimize_params.py --no-pylint show
Metaflow 2.12.7 executing OptimizeRagParams for user:vscode

MetaFlow to optimize a RAG hyperparameters by maximizing a retrieval 
metric on top of an evaluation set.

Arguments
---------
questions_file (str, default: data/questions/questions.csv): path to generated questions CSV
starpoint_api_key (str, default: env['STARPOINT_API_KEY']): Starpoint API key

Step start
    Start node.
    Set random seeds for reproducibility.
    => get_search_space

Step get_search_space
    Define a set of RAG configurations to search over.
    => optimize

Step optimize
    Compute retrieval accuracy.
    :param hparam: Hyperparameter for this RAG retrieval system
    => find_best

Step find_best
    Given the outputs from the optimization, find the best hyperparameters
    by hit rate.
    => end

Step end
    End node!

@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ python scripts/optimize_params.py --no-pylint run
Metaflow 2.12.7 executing OptimizeRagParams for user:vscode
Validating your flow...
    The graph looks good!
2024-08-04 20:05:44.330 Workflow starting (run-id 1722801944329017):
2024-08-04 20:05:44.341 [1722801944329017/start/1 (pid 19387)] Task is starting.
2024-08-04 20:05:48.026 [1722801944329017/start/1 (pid 19387)] Task finished successfully.
2024-08-04 20:05:48.030 [1722801944329017/get_search_space/2 (pid 19435)] Task is starting.
2024-08-04 20:05:51.761 [1722801944329017/get_search_space/2 (pid 19435)] Foreach yields 8 child steps.
2024-08-04 20:05:51.761 [1722801944329017/get_search_space/2 (pid 19435)] Task finished successfully.
2024-08-04 20:05:51.764 [1722801944329017/optimize/3 (pid 19488)] Task is starting.
2024-08-04 20:05:51.766 [1722801944329017/optimize/4 (pid 19489)] Task is starting.
2024-08-04 20:05:51.770 [1722801944329017/optimize/5 (pid 19490)] Task is starting.
2024-08-04 20:05:51.778 [1722801944329017/optimize/6 (pid 19491)] Task is starting.
2024-08-04 20:05:51.799 [1722801944329017/optimize/7 (pid 19492)] Task is starting.
2024-08-04 20:05:51.815 [1722801944329017/optimize/8 (pid 19493)] Task is starting.
2024-08-04 20:05:51.827 [1722801944329017/optimize/9 (pid 19494)] Task is starting.
2024-08-04 20:05:51.839 [1722801944329017/optimize/10 (pid 19495)] Task is starting.
2024-08-04 20:06:01.302 [1722801944329017/optimize/10 (pid 19495)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0.5, hyde_embeddings=True)
2024-08-04 20:06:01.927 [1722801944329017/optimize/9 (pid 19494)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0.5, hyde_embeddings=False)
2024-08-04 20:06:02.151 [1722801944329017/optimize/3 (pid 19488)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0, hyde_embeddings=False)
2024-08-04 20:06:02.455 [1722801944329017/optimize/7 (pid 19492)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0, hyde_embeddings=False)
2024-08-04 20:06:02.487 [1722801944329017/optimize/5 (pid 19490)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0.5, hyde_embeddings=False)
2024-08-04 20:06:02.519 [1722801944329017/optimize/4 (pid 19489)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0, hyde_embeddings=True)
2024-08-04 20:06:02.558 [1722801944329017/optimize/8 (pid 19493)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0, hyde_embeddings=True)
2024-08-04 20:06:02.609 [1722801944329017/optimize/6 (pid 19491)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0.5, hyde_embeddings=True)
  0%|          | 0/197 [00:00<?, ?it/s]17/optimize/6 (pid 19491)] 0%|          | 0/197 [00:00<?, ?it/s]
  0%|          | 0/197 [00:00<?, ?it/s]17/optimize/4 (pid 19489)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:06:04.876 [1722801944329017/optimize/6 (pid 19491)] <flow OptimizeRagParams step optimize[3] (input: DotMap(embedding='al...)> failed:
2024-08-04 20:06:04.876 [1722801944329017/optimize/6 (pid 19491)] Internal error
2024-08-04 20:06:04.880 [1722801944329017/optimize/4 (pid 19489)] <flow OptimizeRagParams step optimize[1] (input: DotMap(embedding='al...)> failed:
2024-08-04 20:06:04.880 [1722801944329017/optimize/4 (pid 19489)] Internal error
2024-08-04 20:06:04.881 [1722801944329017/optimize/6 (pid 19491)] Traceback (most recent call last):
2024-08-04 20:06:04.881 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:06:04.881 [1722801944329017/optimize/6 (pid 19491)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:06:04.881 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:06:04.881 [1722801944329017/optimize/6 (pid 19491)] return func(args, kwargs)
2024-08-04 20:06:04.882 [1722801944329017/optimize/4 (pid 19489)] Traceback (most recent call last):
2024-08-04 20:06:04.885 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:06:04.885 [1722801944329017/optimize/4 (pid 19489)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:06:04.885 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:06:04.886 [1722801944329017/optimize/4 (pid 19489)] return func(args, kwargs)
2024-08-04 20:06:04.886 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:06:04.887 [1722801944329017/optimize/4 (pid 19489)] return self.main(args, kwargs)
2024-08-04 20:06:04.887 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:06:04.887 [1722801944329017/optimize/6 (pid 19491)] return self.main(args, kwargs)
2024-08-04 20:06:04.888 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:06:04.888 [1722801944329017/optimize/6 (pid 19491)] rv = self.invoke(ctx)
  0%|          | 0/197 [00:00<?, ?it/s]17/optimize/3 (pid 19488)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:06:04.895 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:06:04.895 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:06:04.896 [1722801944329017/optimize/6 (pid 19491)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:06:04.896 [1722801944329017/optimize/4 (pid 19489)] rv = self.invoke(ctx)
2024-08-04 20:06:04.896 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:06:04.896 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:06:04.896 [1722801944329017/optimize/6 (pid 19491)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:06:04.896 [1722801944329017/optimize/4 (pid 19489)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:06:04.897 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:06:04.897 [1722801944329017/optimize/4 (pid 19489)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:06:04.907 [1722801944329017/optimize/3 (pid 19488)] <flow OptimizeRagParams step optimize[0] (input: DotMap(embedding='al...)> failed:
2024-08-04 20:06:04.907 [1722801944329017/optimize/3 (pid 19488)] Internal error
  0%|          | 0/197 [00:00<?, ?it/s]17/optimize/5 (pid 19490)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:06:04.909 [1722801944329017/optimize/3 (pid 19488)] Traceback (most recent call last):
2024-08-04 20:06:04.909 [1722801944329017/optimize/5 (pid 19490)] <flow OptimizeRagParams step optimize[2] (input: DotMap(embedding='al...)> failed:
2024-08-04 20:06:04.917 [1722801944329017/optimize/5 (pid 19490)] Internal error
2024-08-04 20:06:04.918 [1722801944329017/optimize/5 (pid 19490)] Traceback (most recent call last):
2024-08-04 20:06:04.918 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:06:04.918 [1722801944329017/optimize/5 (pid 19490)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:06:04.919 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:06:04.919 [1722801944329017/optimize/5 (pid 19490)] return func(args, kwargs)
2024-08-04 20:06:04.920 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:06:04.920 [1722801944329017/optimize/5 (pid 19490)] return self.main(args, kwargs)
2024-08-04 20:06:04.920 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:06:04.920 [1722801944329017/optimize/5 (pid 19490)] rv = self.invoke(ctx)
2024-08-04 20:06:04.920 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:06:04.920 [1722801944329017/optimize/5 (pid 19490)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:06:04.920 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:06:04.921 [1722801944329017/optimize/5 (pid 19490)] return ctx.invoke(self.callback, ctx.params)
  0%|          | 0/197 [00:00<?, ?it/s]17/optimize/8 (pid 19493)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:06:05.627 [1722801944329017/optimize/8 (pid 19493)] <flow OptimizeRagParams step optimize[5] (input: DotMap(embedding='th...)> failed:
2024-08-04 20:06:05.628 [1722801944329017/optimize/8 (pid 19493)] Internal error
2024-08-04 20:06:05.629 [1722801944329017/optimize/8 (pid 19493)] Traceback (most recent call last):
2024-08-04 20:06:05.629 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:06:05.630 [1722801944329017/optimize/8 (pid 19493)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:06:05.630 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:06:05.630 [1722801944329017/optimize/8 (pid 19493)] return func(args, kwargs)
2024-08-04 20:06:05.630 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:06:05.631 [1722801944329017/optimize/8 (pid 19493)] return self.main(args, kwargs)
2024-08-04 20:06:05.631 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:06:05.631 [1722801944329017/optimize/8 (pid 19493)] rv = self.invoke(ctx)
2024-08-04 20:06:05.632 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:06:05.632 [1722801944329017/optimize/8 (pid 19493)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:06:05.632 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:06:05.633 [1722801944329017/optimize/8 (pid 19493)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:06:05.633 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:06:05.633 [1722801944329017/optimize/8 (pid 19493)] return callback(args, kwargs)
2024-08-04 20:06:05.634 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:06:05.634 [1722801944329017/optimize/8 (pid 19493)] return f(get_current_context(), args, kwargs)
2024-08-04 20:06:05.634 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:06:05.634 [1722801944329017/optimize/8 (pid 19493)] task.run_step(
2024-08-04 20:06:05.635 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:06:05.635 [1722801944329017/optimize/8 (pid 19493)] self._exec_step_function(step_func)
2024-08-04 20:06:05.635 [1722801944329017/optimize/8 (pid 19493)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:06:05.636 [1722801944329017/optimize/8 (pid 19493)] step_function()
2024-08-04 20:06:05.636 [1722801944329017/optimize/8 (pid 19493)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:06:05.636 [1722801944329017/optimize/8 (pid 19493)] retrieved_docs = retrieve_documents(
2024-08-04 20:06:05.637 [1722801944329017/optimize/8 (pid 19493)] TypeError: retrieve_documents() got an unexpected keyword argument 'hyde_embeddings'
2024-08-04 20:06:05.637 [1722801944329017/optimize/8 (pid 19493)] 
  0%|          | 0/197 [00:00<?, ?it/s]17/optimize/10 (pid 19495)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:06:05.751 [1722801944329017/optimize/10 (pid 19495)] <flow OptimizeRagParams step optimize[7] (input: DotMap(embedding='th...)> failed:
  0%|          | 0/197 [00:00<?, ?it/s]17/optimize/9 (pid 19494)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:06:05.768 [1722801944329017/optimize/10 (pid 19495)] Internal error
2024-08-04 20:06:05.769 [1722801944329017/optimize/9 (pid 19494)] <flow OptimizeRagParams step optimize[6] (input: DotMap(embedding='th...)> failed:
2024-08-04 20:06:05.801 [1722801944329017/optimize/9 (pid 19494)] Internal error
2024-08-04 20:06:05.803 [1722801944329017/optimize/9 (pid 19494)] Traceback (most recent call last):
2024-08-04 20:06:05.803 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:06:05.803 [1722801944329017/optimize/9 (pid 19494)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:06:05.804 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:06:05.804 [1722801944329017/optimize/9 (pid 19494)] return func(args, kwargs)
2024-08-04 20:06:05.804 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:06:05.805 [1722801944329017/optimize/9 (pid 19494)] return self.main(args, kwargs)
2024-08-04 20:06:05.805 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:06:05.805 [1722801944329017/optimize/9 (pid 19494)] rv = self.invoke(ctx)
2024-08-04 20:06:05.806 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:06:05.806 [1722801944329017/optimize/9 (pid 19494)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:06:05.806 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:06:05.807 [1722801944329017/optimize/9 (pid 19494)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:06:05.808 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:06:05.808 [1722801944329017/optimize/9 (pid 19494)] return callback(args, kwargs)
2024-08-04 20:06:05.808 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:06:05.808 [1722801944329017/optimize/9 (pid 19494)] return f(get_current_context(), args, kwargs)
2024-08-04 20:06:05.809 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:06:05.809 [1722801944329017/optimize/9 (pid 19494)] task.run_step(
2024-08-04 20:06:05.809 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:06:05.810 [1722801944329017/optimize/9 (pid 19494)] self._exec_step_function(step_func)
2024-08-04 20:06:05.810 [1722801944329017/optimize/9 (pid 19494)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:06:05.810 [1722801944329017/optimize/9 (pid 19494)] step_function()
2024-08-04 20:06:05.810 [1722801944329017/optimize/9 (pid 19494)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:06:05.811 [1722801944329017/optimize/9 (pid 19494)] retrieved_docs = retrieve_documents(
2024-08-04 20:06:05.811 [1722801944329017/optimize/9 (pid 19494)] TypeError: retrieve_documents() got an unexpected keyword argument 'hyde_embeddings'
2024-08-04 20:06:05.811 [1722801944329017/optimize/9 (pid 19494)] 
  0%|          | 0/197 [00:00<?, ?it/s]17/optimize/7 (pid 19492)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:06:06.117 [1722801944329017/optimize/7 (pid 19492)] <flow OptimizeRagParams step optimize[4] (input: DotMap(embedding='th...)> failed:
2024-08-04 20:06:06.117 [1722801944329017/optimize/7 (pid 19492)] Internal error
2024-08-04 20:06:06.118 [1722801944329017/optimize/7 (pid 19492)] Traceback (most recent call last):
2024-08-04 20:06:06.119 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:06:06.119 [1722801944329017/optimize/7 (pid 19492)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:06:06.119 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:06:06.120 [1722801944329017/optimize/7 (pid 19492)] return func(args, kwargs)
2024-08-04 20:06:06.148 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:06:06.149 [1722801944329017/optimize/6 (pid 19491)] return callback(args, kwargs)
2024-08-04 20:06:06.149 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:06:06.149 [1722801944329017/optimize/6 (pid 19491)] return f(get_current_context(), args, kwargs)
2024-08-04 20:06:06.149 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:06:06.150 [1722801944329017/optimize/6 (pid 19491)] task.run_step(
2024-08-04 20:06:06.150 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:06:06.150 [1722801944329017/optimize/6 (pid 19491)] self._exec_step_function(step_func)
2024-08-04 20:06:06.150 [1722801944329017/optimize/6 (pid 19491)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:06:06.150 [1722801944329017/optimize/6 (pid 19491)] step_function()
2024-08-04 20:06:06.151 [1722801944329017/optimize/6 (pid 19491)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:06:06.151 [1722801944329017/optimize/6 (pid 19491)] retrieved_docs = retrieve_documents(
2024-08-04 20:06:06.151 [1722801944329017/optimize/6 (pid 19491)] TypeError: retrieve_documents() got an unexpected keyword argument 'hyde_embeddings'
2024-08-04 20:06:06.152 [1722801944329017/optimize/6 (pid 19491)] 
2024-08-04 20:06:06.152 [1722801944329017/optimize/6 (pid 19491)] Task failed.
2024-08-04 20:06:06.153 Workflow failed.
2024-08-04 20:06:06.153 Terminating 7 active tasks...
2024-08-04 20:06:06.153 [1722801944329017/optimize/4 (pid 19489)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.154 [1722801944329017/optimize/4 (pid 19489)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.154 [1722801944329017/optimize/9 (pid 19494)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.154 [1722801944329017/optimize/9 (pid 19494)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.155 [1722801944329017/optimize/7 (pid 19492)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.155 [1722801944329017/optimize/7 (pid 19492)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.155 [1722801944329017/optimize/5 (pid 19490)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.155 [1722801944329017/optimize/5 (pid 19490)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.156 [1722801944329017/optimize/10 (pid 19495)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.156 [1722801944329017/optimize/10 (pid 19495)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.156 [1722801944329017/optimize/3 (pid 19488)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.157 [1722801944329017/optimize/3 (pid 19488)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.157 [1722801944329017/optimize/8 (pid 19493)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:06.157 [1722801944329017/optimize/8 (pid 19493)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:06:07.157 Flushing logs...
2024-08-04 20:06:07.157 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:06:07.157 [1722801944329017/optimize/3 (pid 19488)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] return func(args, kwargs)
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] return self.main(args, kwargs)
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] rv = self.invoke(ctx)
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] return callback(args, kwargs)
2024-08-04 20:06:07.158 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] return f(get_current_context(), args, kwargs)
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] task.run_step(
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] self._exec_step_function(step_func)
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] step_function()
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] retrieved_docs = retrieve_documents(
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] TypeError: retrieve_documents() got an unexpected keyword argument 'hyde_embeddings'
2024-08-04 20:06:07.159 [1722801944329017/optimize/3 (pid 19488)] 
2024-08-04 20:06:07.160 [1722801944329017/optimize/3 (pid 19488)] Task failed.
2024-08-04 20:06:07.160 This failed task will not be retried.
2024-08-04 20:06:07.160 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:06:07.160 [1722801944329017/optimize/4 (pid 19489)] return callback(args, kwargs)
2024-08-04 20:06:07.160 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] return f(get_current_context(), args, kwargs)
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] task.run_step(
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] self._exec_step_function(step_func)
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] step_function()
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] retrieved_docs = retrieve_documents(
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] TypeError: retrieve_documents() got an unexpected keyword argument 'hyde_embeddings'
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] 
2024-08-04 20:06:07.161 [1722801944329017/optimize/4 (pid 19489)] Task failed.
2024-08-04 20:06:07.162 This failed task will not be retried.
2024-08-04 20:06:07.162 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:06:07.162 [1722801944329017/optimize/5 (pid 19490)] return callback(args, kwargs)
2024-08-04 20:06:07.162 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:06:07.162 [1722801944329017/optimize/5 (pid 19490)] return f(get_current_context(), args, kwargs)
2024-08-04 20:06:07.162 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:06:07.162 [1722801944329017/optimize/5 (pid 19490)] task.run_step(
2024-08-04 20:06:07.162 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:06:07.162 [1722801944329017/optimize/5 (pid 19490)] self._exec_step_function(step_func)
2024-08-04 20:06:07.162 [1722801944329017/optimize/5 (pid 19490)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:06:07.163 [1722801944329017/optimize/5 (pid 19490)] step_function()
2024-08-04 20:06:07.163 [1722801944329017/optimize/5 (pid 19490)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:06:07.163 [1722801944329017/optimize/5 (pid 19490)] retrieved_docs = retrieve_documents(
2024-08-04 20:06:07.163 [1722801944329017/optimize/5 (pid 19490)] TypeError: retrieve_documents() got an unexpected keyword argument 'hyde_embeddings'
2024-08-04 20:06:07.163 [1722801944329017/optimize/5 (pid 19490)] 
2024-08-04 20:06:07.163 [1722801944329017/optimize/5 (pid 19490)] Task failed.
2024-08-04 20:06:07.164 This failed task will not be retried.
2024-08-04 20:06:07.164 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:06:07.164 [1722801944329017/optimize/7 (pid 19492)] return self.main(args, kwargs)
2024-08-04 20:06:07.164 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:06:07.164 [1722801944329017/optimize/7 (pid 19492)] rv = self.invoke(ctx)
2024-08-04 20:06:07.164 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:06:07.164 [1722801944329017/optimize/7 (pid 19492)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:06:07.164 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:06:07.164 [1722801944329017/optimize/7 (pid 19492)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:06:07.165 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:06:07.165 [1722801944329017/optimize/7 (pid 19492)] return callback(args, kwargs)
2024-08-04 20:06:07.165 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:06:07.165 [1722801944329017/optimize/7 (pid 19492)] return f(get_current_context(), args, kwargs)
2024-08-04 20:06:07.165 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:06:07.165 [1722801944329017/optimize/7 (pid 19492)] task.run_step(
2024-08-04 20:06:07.165 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:06:07.165 [1722801944329017/optimize/7 (pid 19492)] self._exec_step_function(step_func)
2024-08-04 20:06:07.165 [1722801944329017/optimize/7 (pid 19492)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:06:07.165 [1722801944329017/optimize/7 (pid 19492)] step_function()
2024-08-04 20:06:07.166 [1722801944329017/optimize/7 (pid 19492)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:06:07.166 [1722801944329017/optimize/7 (pid 19492)] retrieved_docs = retrieve_documents(
2024-08-04 20:06:07.166 [1722801944329017/optimize/7 (pid 19492)] TypeError: retrieve_documents() got an unexpected keyword argument 'hyde_embeddings'
2024-08-04 20:06:07.166 [1722801944329017/optimize/7 (pid 19492)] 
2024-08-04 20:06:07.166 [1722801944329017/optimize/7 (pid 19492)] Task failed.
2024-08-04 20:06:07.166 This failed task will not be retried.
2024-08-04 20:06:07.167 [1722801944329017/optimize/8 (pid 19493)] Task failed.
2024-08-04 20:06:07.167 This failed task will not be retried.
2024-08-04 20:06:07.167 [1722801944329017/optimize/9 (pid 19494)] Task failed.
2024-08-04 20:06:07.168 This failed task will not be retried.
2024-08-04 20:06:07.168 [1722801944329017/optimize/10 (pid 19495)] Traceback (most recent call last):
2024-08-04 20:06:07.168 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:06:07.168 [1722801944329017/optimize/10 (pid 19495)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:06:07.168 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:06:07.168 [1722801944329017/optimize/10 (pid 19495)] return func(args, kwargs)
2024-08-04 20:06:07.168 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:06:07.168 [1722801944329017/optimize/10 (pid 19495)] return self.main(args, kwargs)
2024-08-04 20:06:07.169 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:06:07.169 [1722801944329017/optimize/10 (pid 19495)] rv = self.invoke(ctx)
2024-08-04 20:06:07.169 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:06:07.169 [1722801944329017/optimize/10 (pid 19495)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:06:07.169 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:06:07.169 [1722801944329017/optimize/10 (pid 19495)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:06:07.169 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:06:07.169 [1722801944329017/optimize/10 (pid 19495)] return callback(args, kwargs)
2024-08-04 20:06:07.169 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:06:07.169 [1722801944329017/optimize/10 (pid 19495)] return f(get_current_context(), args, kwargs)
2024-08-04 20:06:07.170 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:06:07.170 [1722801944329017/optimize/10 (pid 19495)] task.run_step(
2024-08-04 20:06:07.170 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:06:07.170 [1722801944329017/optimize/10 (pid 19495)] self._exec_step_function(step_func)
2024-08-04 20:06:07.170 [1722801944329017/optimize/10 (pid 19495)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:06:07.170 [1722801944329017/optimize/10 (pid 19495)] step_function()
2024-08-04 20:06:07.170 [1722801944329017/optimize/10 (pid 19495)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:06:07.170 [1722801944329017/optimize/10 (pid 19495)] retrieved_docs = retrieve_documents(
2024-08-04 20:06:07.170 [1722801944329017/optimize/10 (pid 19495)] TypeError: retrieve_documents() got an unexpected keyword argument 'hyde_embeddings'
2024-08-04 20:06:07.170 [1722801944329017/optimize/10 (pid 19495)] 
2024-08-04 20:06:07.171 [1722801944329017/optimize/10 (pid 19495)] Task failed.
2024-08-04 20:06:07.171 This failed task will not be retried.
    Step failure:
    Step optimize (task-id 6) failed.

@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ python scripts/optimize_params.py --no-pylint --max-workers 1 run
Usage: optimize_params.py [OPTIONS] COMMAND [ARGS]...
Try 'optimize_params.py --help' for help.

Error: no such option: --max-workers
@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ python scripts/optimize_params.py --no-pylint run
Metaflow 2.12.7 executing OptimizeRagParams for user:vscode
Validating your flow...
    The graph looks good!
2024-08-04 20:17:40.957 Workflow starting (run-id 1722802660956446):
2024-08-04 20:17:40.965 [1722802660956446/start/1 (pid 24048)] Task is starting.
2024-08-04 20:17:44.693 [1722802660956446/start/1 (pid 24048)] Task finished successfully.
2024-08-04 20:17:44.696 [1722802660956446/get_search_space/2 (pid 24092)] Task is starting.
2024-08-04 20:17:48.454 [1722802660956446/get_search_space/2 (pid 24092)] Foreach yields 8 child steps.
2024-08-04 20:17:48.454 [1722802660956446/get_search_space/2 (pid 24092)] Task finished successfully.
2024-08-04 20:17:48.458 [1722802660956446/optimize/3 (pid 24153)] Task is starting.
2024-08-04 20:17:48.460 [1722802660956446/optimize/4 (pid 24154)] Task is starting.
2024-08-04 20:17:48.463 [1722802660956446/optimize/5 (pid 24155)] Task is starting.
2024-08-04 20:17:48.476 [1722802660956446/optimize/6 (pid 24156)] Task is starting.
2024-08-04 20:17:48.487 [1722802660956446/optimize/7 (pid 24157)] Task is starting.
2024-08-04 20:17:48.507 [1722802660956446/optimize/8 (pid 24158)] Task is starting.
2024-08-04 20:17:48.530 [1722802660956446/optimize/9 (pid 24159)] Task is starting.
2024-08-04 20:17:48.551 [1722802660956446/optimize/10 (pid 24160)] Task is starting.
2024-08-04 20:17:58.648 [1722802660956446/optimize/3 (pid 24153)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0, hyde_embeddings=False)
2024-08-04 20:17:58.652 [1722802660956446/optimize/7 (pid 24157)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0, hyde_embeddings=False)
2024-08-04 20:17:58.772 [1722802660956446/optimize/8 (pid 24158)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0, hyde_embeddings=True)
2024-08-04 20:17:58.985 [1722802660956446/optimize/9 (pid 24159)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0.5, hyde_embeddings=False)
2024-08-04 20:17:59.208 [1722802660956446/optimize/6 (pid 24156)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0.5, hyde_embeddings=True)
2024-08-04 20:17:59.232 [1722802660956446/optimize/5 (pid 24155)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0.5, hyde_embeddings=False)
2024-08-04 20:17:59.292 [1722802660956446/optimize/10 (pid 24160)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0.5, hyde_embeddings=True)
2024-08-04 20:17:59.312 [1722802660956446/optimize/4 (pid 24154)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0, hyde_embeddings=True)
  0%|          | 0/197 [00:00<?, ?it/s]46/optimize/3 (pid 24153)] 0%|          | 0/197 [00:00<?, ?it/s]
  0%|          | 0/197 [00:00<?, ?it/s]46/optimize/7 (pid 24157)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:18:00.475 [1722802660956446/optimize/3 (pid 24153)] <flow OptimizeRagParams step optimize[0] (input: DotMap(embedding='al...)> failed:
2024-08-04 20:18:00.476 [1722802660956446/optimize/7 (pid 24157)] <flow OptimizeRagParams step optimize[4] (input: DotMap(embedding='th...)> failed:
2024-08-04 20:18:00.488 [1722802660956446/optimize/7 (pid 24157)] Internal error
2024-08-04 20:18:00.489 [1722802660956446/optimize/7 (pid 24157)] Traceback (most recent call last):
2024-08-04 20:18:00.489 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:18:00.489 [1722802660956446/optimize/7 (pid 24157)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:18:00.490 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:18:00.490 [1722802660956446/optimize/7 (pid 24157)] return func(args, kwargs)
  0%|          | 0/197 [00:00<?, ?it/s]46/optimize/9 (pid 24159)] 0%|          | 0/197 [00:00<?, ?it/s]
  0%|          | 0/197 [00:00<?, ?it/s]46/optimize/4 (pid 24154)] 0%|          | 0/197 [00:00<?, ?it/s]
  0%|          | 0/197 [00:00<?, ?it/s]46/optimize/5 (pid 24155)] 0%|          | 0/197 [00:00<?, ?it/s]
  0%|          | 0/197 [00:00<?, ?it/s]46/optimize/6 (pid 24156)] 0%|          | 0/197 [00:00<?, ?it/s]
  0%|          | 0/197 [00:00<?, ?it/s]46/optimize/8 (pid 24158)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:18:01.097 [1722802660956446/optimize/4 (pid 24154)] <flow OptimizeRagParams step optimize[1] (input: DotMap(embedding='al...)> failed:
2024-08-04 20:18:01.097 [1722802660956446/optimize/6 (pid 24156)] <flow OptimizeRagParams step optimize[3] (input: DotMap(embedding='al...)> failed:
2024-08-04 20:18:01.097 [1722802660956446/optimize/9 (pid 24159)] <flow OptimizeRagParams step optimize[6] (input: DotMap(embedding='th...)> failed:
  0%|          | 0/197 [00:00<?, ?it/s]46/optimize/10 (pid 24160)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:18:01.235 [1722802660956446/optimize/8 (pid 24158)] <flow OptimizeRagParams step optimize[5] (input: DotMap(embedding='th...)> failed:
2024-08-04 20:18:01.235 [1722802660956446/optimize/9 (pid 24159)] Internal error
2024-08-04 20:18:01.235 [1722802660956446/optimize/8 (pid 24158)] Internal error
2024-08-04 20:18:01.236 [1722802660956446/optimize/10 (pid 24160)] <flow OptimizeRagParams step optimize[7] (input: DotMap(embedding='th...)> failed:
2024-08-04 20:18:01.255 [1722802660956446/optimize/10 (pid 24160)] Internal error
2024-08-04 20:18:01.256 [1722802660956446/optimize/10 (pid 24160)] Traceback (most recent call last):
2024-08-04 20:18:01.257 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:18:01.257 [1722802660956446/optimize/10 (pid 24160)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:18:01.257 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:18:01.257 [1722802660956446/optimize/10 (pid 24160)] return func(args, kwargs)
2024-08-04 20:18:01.257 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:18:01.257 [1722802660956446/optimize/10 (pid 24160)] return self.main(args, kwargs)
2024-08-04 20:18:01.258 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:18:01.258 [1722802660956446/optimize/10 (pid 24160)] rv = self.invoke(ctx)
2024-08-04 20:18:01.258 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:18:01.258 [1722802660956446/optimize/10 (pid 24160)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:18:01.258 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:18:01.258 [1722802660956446/optimize/10 (pid 24160)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:18:01.258 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:18:01.259 [1722802660956446/optimize/10 (pid 24160)] return callback(args, kwargs)
2024-08-04 20:18:01.259 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:18:01.259 [1722802660956446/optimize/10 (pid 24160)] return f(get_current_context(), args, kwargs)
2024-08-04 20:18:01.259 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:18:01.259 [1722802660956446/optimize/10 (pid 24160)] task.run_step(
2024-08-04 20:18:01.259 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:18:01.260 [1722802660956446/optimize/10 (pid 24160)] self._exec_step_function(step_func)
2024-08-04 20:18:01.260 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:18:01.260 [1722802660956446/optimize/10 (pid 24160)] step_function()
2024-08-04 20:18:01.260 [1722802660956446/optimize/10 (pid 24160)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:18:01.260 [1722802660956446/optimize/10 (pid 24160)] retrieved_docs = retrieve_documents(
2024-08-04 20:18:01.260 [1722802660956446/optimize/10 (pid 24160)] File "/workspaces/data-centric-deep-learning/course/week4/rag/vector.py", line 80, in retrieve_documents
2024-08-04 20:18:01.260 [1722802660956446/optimize/10 (pid 24160)] response = starpoint.query(
2024-08-04 20:18:01.260 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/starpoint/db.py", line 154, in query
2024-08-04 20:18:01.260 [1722802660956446/optimize/10 (pid 24160)] return self.reader.query(
2024-08-04 20:18:01.260 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/starpoint/reader.py", line 110, in query
2024-08-04 20:18:01.261 [1722802660956446/optimize/10 (pid 24160)] response = requests.post(
2024-08-04 20:18:01.261 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 115, in post
2024-08-04 20:18:01.261 [1722802660956446/optimize/10 (pid 24160)] return request("post", url, data=data, json=json, kwargs)
2024-08-04 20:18:01.261 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 59, in request
2024-08-04 20:18:01.261 [1722802660956446/optimize/10 (pid 24160)] return session.request(method=method, url=url, kwargs)
2024-08-04 20:18:01.261 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 575, in request
2024-08-04 20:18:01.261 [1722802660956446/optimize/10 (pid 24160)] prep = self.prepare_request(req)
2024-08-04 20:18:01.261 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 486, in prepare_request
2024-08-04 20:18:01.261 [1722802660956446/optimize/10 (pid 24160)] p.prepare(
2024-08-04 20:18:01.262 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 371, in prepare
2024-08-04 20:18:01.262 [1722802660956446/optimize/10 (pid 24160)] self.prepare_body(data, files, json)
2024-08-04 20:18:01.262 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 511, in prepare_body
2024-08-04 20:18:01.262 [1722802660956446/optimize/10 (pid 24160)] body = complexjson.dumps(json, allow_nan=False)
2024-08-04 20:18:01.262 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/json/__init__.py", line 238, in dumps
2024-08-04 20:18:01.262 [1722802660956446/optimize/10 (pid 24160)] kw).encode(obj)
2024-08-04 20:18:01.262 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/json/encoder.py", line 199, in encode
2024-08-04 20:18:01.262 [1722802660956446/optimize/10 (pid 24160)] chunks = self.iterencode(o, _one_shot=True)
2024-08-04 20:18:01.262 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/json/encoder.py", line 257, in iterencode
2024-08-04 20:18:01.263 [1722802660956446/optimize/10 (pid 24160)] return _iterencode(o, 0)
2024-08-04 20:18:01.263 [1722802660956446/optimize/10 (pid 24160)] File "/usr/local/lib/python3.10/json/encoder.py", line 179, in default
2024-08-04 20:18:01.263 [1722802660956446/optimize/10 (pid 24160)] raise TypeError(f'Object of type {o.__class__.__name__} '
2024-08-04 20:18:01.263 [1722802660956446/optimize/10 (pid 24160)] TypeError: Object of type SentenceTransformer is not JSON serializable
2024-08-04 20:18:01.263 [1722802660956446/optimize/10 (pid 24160)] 
2024-08-04 20:18:01.315 [1722802660956446/optimize/3 (pid 24153)] Internal error
2024-08-04 20:18:01.315 [1722802660956446/optimize/3 (pid 24153)] Traceback (most recent call last):
2024-08-04 20:18:01.316 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:18:01.316 [1722802660956446/optimize/3 (pid 24153)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:18:01.316 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:18:01.316 [1722802660956446/optimize/3 (pid 24153)] return func(args, kwargs)
2024-08-04 20:18:01.316 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:18:01.316 [1722802660956446/optimize/3 (pid 24153)] return self.main(args, kwargs)
2024-08-04 20:18:01.316 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:18:01.316 [1722802660956446/optimize/3 (pid 24153)] rv = self.invoke(ctx)
2024-08-04 20:18:01.316 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:18:01.316 [1722802660956446/optimize/3 (pid 24153)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:18:01.317 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:18:01.317 [1722802660956446/optimize/3 (pid 24153)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:18:01.317 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:18:01.317 [1722802660956446/optimize/3 (pid 24153)] return callback(args, kwargs)
2024-08-04 20:18:01.317 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:18:01.317 [1722802660956446/optimize/3 (pid 24153)] return f(get_current_context(), args, kwargs)
2024-08-04 20:18:01.317 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:18:01.317 [1722802660956446/optimize/3 (pid 24153)] task.run_step(
2024-08-04 20:18:01.318 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:18:01.318 [1722802660956446/optimize/3 (pid 24153)] self._exec_step_function(step_func)
2024-08-04 20:18:01.318 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:18:01.318 [1722802660956446/optimize/3 (pid 24153)] step_function()
2024-08-04 20:18:01.319 [1722802660956446/optimize/3 (pid 24153)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:18:01.319 [1722802660956446/optimize/3 (pid 24153)] retrieved_docs = retrieve_documents(
2024-08-04 20:18:01.319 [1722802660956446/optimize/3 (pid 24153)] File "/workspaces/data-centric-deep-learning/course/week4/rag/vector.py", line 80, in retrieve_documents
2024-08-04 20:18:01.319 [1722802660956446/optimize/3 (pid 24153)] response = starpoint.query(
2024-08-04 20:18:01.320 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/starpoint/db.py", line 154, in query
2024-08-04 20:18:01.320 [1722802660956446/optimize/3 (pid 24153)] return self.reader.query(
2024-08-04 20:18:01.320 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/starpoint/reader.py", line 110, in query
2024-08-04 20:18:01.321 [1722802660956446/optimize/3 (pid 24153)] response = requests.post(
2024-08-04 20:18:01.321 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 115, in post
2024-08-04 20:18:01.327 [1722802660956446/optimize/3 (pid 24153)] return request("post", url, data=data, json=json, kwargs)
2024-08-04 20:18:01.328 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 59, in request
2024-08-04 20:18:01.328 [1722802660956446/optimize/3 (pid 24153)] return session.request(method=method, url=url, kwargs)
2024-08-04 20:18:01.328 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 575, in request
2024-08-04 20:18:01.328 [1722802660956446/optimize/3 (pid 24153)] prep = self.prepare_request(req)
2024-08-04 20:18:01.329 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 486, in prepare_request
2024-08-04 20:18:01.329 [1722802660956446/optimize/3 (pid 24153)] p.prepare(
2024-08-04 20:18:01.329 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 371, in prepare
2024-08-04 20:18:01.330 [1722802660956446/optimize/3 (pid 24153)] self.prepare_body(data, files, json)
2024-08-04 20:18:01.330 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 511, in prepare_body
2024-08-04 20:18:01.330 [1722802660956446/optimize/3 (pid 24153)] body = complexjson.dumps(json, allow_nan=False)
2024-08-04 20:18:01.335 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/json/__init__.py", line 238, in dumps
2024-08-04 20:18:01.335 [1722802660956446/optimize/3 (pid 24153)] kw).encode(obj)
2024-08-04 20:18:01.336 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/json/encoder.py", line 199, in encode
2024-08-04 20:18:01.336 [1722802660956446/optimize/3 (pid 24153)] chunks = self.iterencode(o, _one_shot=True)
2024-08-04 20:18:01.336 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/json/encoder.py", line 257, in iterencode
2024-08-04 20:18:01.337 [1722802660956446/optimize/3 (pid 24153)] return _iterencode(o, 0)
2024-08-04 20:18:01.337 [1722802660956446/optimize/3 (pid 24153)] File "/usr/local/lib/python3.10/json/encoder.py", line 179, in default
2024-08-04 20:18:01.337 [1722802660956446/optimize/3 (pid 24153)] raise TypeError(f'Object of type {o.__class__.__name__} '
2024-08-04 20:18:01.337 [1722802660956446/optimize/3 (pid 24153)] TypeError: Object of type SentenceTransformer is not JSON serializable
2024-08-04 20:18:01.338 [1722802660956446/optimize/3 (pid 24153)] 
2024-08-04 20:18:01.338 [1722802660956446/optimize/3 (pid 24153)] Task failed.
2024-08-04 20:18:01.340 Workflow failed.
2024-08-04 20:18:01.340 Terminating 7 active tasks...
2024-08-04 20:18:01.340 [1722802660956446/optimize/8 (pid 24158)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.341 [1722802660956446/optimize/8 (pid 24158)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.341 [1722802660956446/optimize/6 (pid 24156)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.341 [1722802660956446/optimize/6 (pid 24156)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.341 [1722802660956446/optimize/9 (pid 24159)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.342 [1722802660956446/optimize/9 (pid 24159)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.342 [1722802660956446/optimize/7 (pid 24157)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.342 [1722802660956446/optimize/7 (pid 24157)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.342 [1722802660956446/optimize/10 (pid 24160)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.343 [1722802660956446/optimize/10 (pid 24160)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.343 [1722802660956446/optimize/5 (pid 24155)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.343 [1722802660956446/optimize/5 (pid 24155)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.343 [1722802660956446/optimize/4 (pid 24154)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:01.346 [1722802660956446/optimize/4 (pid 24154)] [KILLED BY ORCHESTRATOR]
2024-08-04 20:18:02.740 Flushing logs...
2024-08-04 20:18:02.740 [1722802660956446/optimize/4 (pid 24154)] Internal error
2024-08-04 20:18:02.740 [1722802660956446/optimize/4 (pid 24154)] Traceback (most recent call last):
2024-08-04 20:18:02.740 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:18:02.740 [1722802660956446/optimize/4 (pid 24154)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] return func(args, kwargs)
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] return self.main(args, kwargs)
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] rv = self.invoke(ctx)
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] return callback(args, kwargs)
2024-08-04 20:18:02.741 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] return f(get_current_context(), args, kwargs)
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] task.run_step(
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] self._exec_step_function(step_func)
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] step_function()
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] retrieved_docs = retrieve_documents(
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] File "/workspaces/data-centric-deep-learning/course/week4/rag/vector.py", line 80, in retrieve_documents
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] response = starpoint.query(
2024-08-04 20:18:02.742 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/starpoint/db.py", line 154, in query
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] return self.reader.query(
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/starpoint/reader.py", line 110, in query
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] response = requests.post(
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 115, in post
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] return request("post", url, data=data, json=json, kwargs)
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 59, in request
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] return session.request(method=method, url=url, kwargs)
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 575, in request
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] prep = self.prepare_request(req)
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 486, in prepare_request
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] p.prepare(
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 371, in prepare
2024-08-04 20:18:02.743 [1722802660956446/optimize/4 (pid 24154)] self.prepare_body(data, files, json)
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 511, in prepare_body
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] body = complexjson.dumps(json, allow_nan=False)
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/json/__init__.py", line 238, in dumps
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] kw).encode(obj)
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/json/encoder.py", line 199, in encode
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] chunks = self.iterencode(o, _one_shot=True)
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/json/encoder.py", line 257, in iterencode
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] return _iterencode(o, 0)
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] File "/usr/local/lib/python3.10/json/encoder.py", line 179, in default
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] raise TypeError(f'Object of type {o.__class__.__name__} '
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] TypeError: Object of type SentenceTransformer is not JSON serializable
2024-08-04 20:18:02.744 [1722802660956446/optimize/4 (pid 24154)] 
2024-08-04 20:18:02.745 [1722802660956446/optimize/4 (pid 24154)] Task failed.
2024-08-04 20:18:02.745 This failed task will not be retried.
2024-08-04 20:18:02.745 [1722802660956446/optimize/5 (pid 24155)] <flow OptimizeRagParams step optimize[2] (input: DotMap(embedding='al...)> failed:
2024-08-04 20:18:02.745 [1722802660956446/optimize/5 (pid 24155)] Internal error
2024-08-04 20:18:02.745 [1722802660956446/optimize/5 (pid 24155)] Traceback (most recent call last):
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] return func(args, kwargs)
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] return self.main(args, kwargs)
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] rv = self.invoke(ctx)
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:18:02.746 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:18:02.747 [1722802660956446/optimize/5 (pid 24155)] return callback(args, kwargs)
2024-08-04 20:18:02.747 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:18:02.747 [1722802660956446/optimize/5 (pid 24155)] return f(get_current_context(), args, kwargs)
2024-08-04 20:18:02.747 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:18:02.747 [1722802660956446/optimize/5 (pid 24155)] task.run_step(
2024-08-04 20:18:02.747 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:18:02.747 [1722802660956446/optimize/5 (pid 24155)] self._exec_step_function(step_func)
2024-08-04 20:18:02.747 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:18:02.747 [1722802660956446/optimize/5 (pid 24155)] step_function()
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] retrieved_docs = retrieve_documents(
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] File "/workspaces/data-centric-deep-learning/course/week4/rag/vector.py", line 80, in retrieve_documents
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] response = starpoint.query(
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/starpoint/db.py", line 154, in query
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] return self.reader.query(
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/starpoint/reader.py", line 110, in query
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] response = requests.post(
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 115, in post
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] return request("post", url, data=data, json=json, kwargs)
2024-08-04 20:18:02.748 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 59, in request
2024-08-04 20:18:02.749 [1722802660956446/optimize/5 (pid 24155)] return session.request(method=method, url=url, kwargs)
2024-08-04 20:18:02.749 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 575, in request
2024-08-04 20:18:02.749 [1722802660956446/optimize/5 (pid 24155)] prep = self.prepare_request(req)
2024-08-04 20:18:02.749 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 486, in prepare_request
2024-08-04 20:18:02.749 [1722802660956446/optimize/5 (pid 24155)] p.prepare(
2024-08-04 20:18:02.749 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 371, in prepare
2024-08-04 20:18:02.749 [1722802660956446/optimize/5 (pid 24155)] self.prepare_body(data, files, json)
2024-08-04 20:18:02.749 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 511, in prepare_body
2024-08-04 20:18:02.749 [1722802660956446/optimize/5 (pid 24155)] body = complexjson.dumps(json, allow_nan=False)
2024-08-04 20:18:02.749 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/json/__init__.py", line 238, in dumps
2024-08-04 20:18:02.750 [1722802660956446/optimize/5 (pid 24155)] kw).encode(obj)
2024-08-04 20:18:02.750 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/json/encoder.py", line 199, in encode
2024-08-04 20:18:02.750 [1722802660956446/optimize/5 (pid 24155)] chunks = self.iterencode(o, _one_shot=True)
2024-08-04 20:18:02.750 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/json/encoder.py", line 257, in iterencode
2024-08-04 20:18:02.750 [1722802660956446/optimize/5 (pid 24155)] return _iterencode(o, 0)
2024-08-04 20:18:02.750 [1722802660956446/optimize/5 (pid 24155)] File "/usr/local/lib/python3.10/json/encoder.py", line 179, in default
2024-08-04 20:18:02.750 [1722802660956446/optimize/5 (pid 24155)] raise TypeError(f'Object of type {o.__class__.__name__} '
2024-08-04 20:18:02.750 [1722802660956446/optimize/5 (pid 24155)] TypeError: Object of type SentenceTransformer is not JSON serializable
2024-08-04 20:18:02.750 [1722802660956446/optimize/5 (pid 24155)] 
2024-08-04 20:18:02.751 [1722802660956446/optimize/5 (pid 24155)] Task failed.
2024-08-04 20:18:02.751 This failed task will not be retried.
2024-08-04 20:18:02.751 [1722802660956446/optimize/6 (pid 24156)] Internal error
2024-08-04 20:18:02.751 [1722802660956446/optimize/6 (pid 24156)] Traceback (most recent call last):
2024-08-04 20:18:02.751 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:18:02.751 [1722802660956446/optimize/6 (pid 24156)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:18:02.752 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:18:02.752 [1722802660956446/optimize/6 (pid 24156)] return func(args, kwargs)
2024-08-04 20:18:02.752 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:18:02.752 [1722802660956446/optimize/6 (pid 24156)] return self.main(args, kwargs)
2024-08-04 20:18:02.752 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:18:02.752 [1722802660956446/optimize/6 (pid 24156)] rv = self.invoke(ctx)
2024-08-04 20:18:02.752 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:18:02.752 [1722802660956446/optimize/6 (pid 24156)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:18:02.752 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:18:02.752 [1722802660956446/optimize/6 (pid 24156)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:18:02.753 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:18:02.753 [1722802660956446/optimize/6 (pid 24156)] return callback(args, kwargs)
2024-08-04 20:18:02.753 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:18:02.753 [1722802660956446/optimize/6 (pid 24156)] return f(get_current_context(), args, kwargs)
2024-08-04 20:18:02.753 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:18:02.753 [1722802660956446/optimize/6 (pid 24156)] task.run_step(
2024-08-04 20:18:02.753 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:18:02.753 [1722802660956446/optimize/6 (pid 24156)] self._exec_step_function(step_func)
2024-08-04 20:18:02.753 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:18:02.753 [1722802660956446/optimize/6 (pid 24156)] step_function()
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] retrieved_docs = retrieve_documents(
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] File "/workspaces/data-centric-deep-learning/course/week4/rag/vector.py", line 80, in retrieve_documents
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] response = starpoint.query(
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/starpoint/db.py", line 154, in query
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] return self.reader.query(
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/starpoint/reader.py", line 110, in query
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] response = requests.post(
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 115, in post
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] return request("post", url, data=data, json=json, kwargs)
2024-08-04 20:18:02.754 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 59, in request
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] return session.request(method=method, url=url, kwargs)
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 575, in request
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] prep = self.prepare_request(req)
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 486, in prepare_request
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] p.prepare(
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 371, in prepare
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] self.prepare_body(data, files, json)
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 511, in prepare_body
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] body = complexjson.dumps(json, allow_nan=False)
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/json/__init__.py", line 238, in dumps
2024-08-04 20:18:02.755 [1722802660956446/optimize/6 (pid 24156)] kw).encode(obj)
2024-08-04 20:18:02.756 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/json/encoder.py", line 199, in encode
2024-08-04 20:18:02.756 [1722802660956446/optimize/6 (pid 24156)] chunks = self.iterencode(o, _one_shot=True)
2024-08-04 20:18:02.756 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/json/encoder.py", line 257, in iterencode
2024-08-04 20:18:02.756 [1722802660956446/optimize/6 (pid 24156)] return _iterencode(o, 0)
2024-08-04 20:18:02.756 [1722802660956446/optimize/6 (pid 24156)] File "/usr/local/lib/python3.10/json/encoder.py", line 179, in default
2024-08-04 20:18:02.756 [1722802660956446/optimize/6 (pid 24156)] raise TypeError(f'Object of type {o.__class__.__name__} '
2024-08-04 20:18:02.756 [1722802660956446/optimize/6 (pid 24156)] TypeError: Object of type SentenceTransformer is not JSON serializable
2024-08-04 20:18:02.756 [1722802660956446/optimize/6 (pid 24156)] 
2024-08-04 20:18:02.756 [1722802660956446/optimize/6 (pid 24156)] Task failed.
2024-08-04 20:18:02.757 This failed task will not be retried.
2024-08-04 20:18:02.757 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:18:02.757 [1722802660956446/optimize/7 (pid 24157)] return self.main(args, kwargs)
2024-08-04 20:18:02.757 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:18:02.757 [1722802660956446/optimize/7 (pid 24157)] rv = self.invoke(ctx)
2024-08-04 20:18:02.757 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:18:02.757 [1722802660956446/optimize/7 (pid 24157)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] return callback(args, kwargs)
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] return f(get_current_context(), args, kwargs)
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] task.run_step(
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] self._exec_step_function(step_func)
2024-08-04 20:18:02.758 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:18:02.759 [1722802660956446/optimize/7 (pid 24157)] step_function()
2024-08-04 20:18:02.759 [1722802660956446/optimize/7 (pid 24157)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:18:02.759 [1722802660956446/optimize/7 (pid 24157)] retrieved_docs = retrieve_documents(
2024-08-04 20:18:02.759 [1722802660956446/optimize/7 (pid 24157)] File "/workspaces/data-centric-deep-learning/course/week4/rag/vector.py", line 80, in retrieve_documents
2024-08-04 20:18:02.759 [1722802660956446/optimize/7 (pid 24157)] response = starpoint.query(
2024-08-04 20:18:02.759 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/starpoint/db.py", line 154, in query
2024-08-04 20:18:02.759 [1722802660956446/optimize/7 (pid 24157)] return self.reader.query(
2024-08-04 20:18:02.759 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/starpoint/reader.py", line 110, in query
2024-08-04 20:18:02.759 [1722802660956446/optimize/7 (pid 24157)] response = requests.post(
2024-08-04 20:18:02.759 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 115, in post
2024-08-04 20:18:02.760 [1722802660956446/optimize/7 (pid 24157)] return request("post", url, data=data, json=json, kwargs)
2024-08-04 20:18:02.760 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 59, in request
2024-08-04 20:18:02.760 [1722802660956446/optimize/7 (pid 24157)] return session.request(method=method, url=url, kwargs)
2024-08-04 20:18:02.760 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 575, in request
2024-08-04 20:18:02.760 [1722802660956446/optimize/7 (pid 24157)] prep = self.prepare_request(req)
2024-08-04 20:18:02.760 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 486, in prepare_request
2024-08-04 20:18:02.760 [1722802660956446/optimize/7 (pid 24157)] p.prepare(
2024-08-04 20:18:02.760 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 371, in prepare
2024-08-04 20:18:02.760 [1722802660956446/optimize/7 (pid 24157)] self.prepare_body(data, files, json)
2024-08-04 20:18:02.760 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 511, in prepare_body
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] body = complexjson.dumps(json, allow_nan=False)
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/json/__init__.py", line 238, in dumps
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] kw).encode(obj)
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/json/encoder.py", line 199, in encode
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] chunks = self.iterencode(o, _one_shot=True)
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/json/encoder.py", line 257, in iterencode
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] return _iterencode(o, 0)
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] File "/usr/local/lib/python3.10/json/encoder.py", line 179, in default
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] raise TypeError(f'Object of type {o.__class__.__name__} '
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] TypeError: Object of type SentenceTransformer is not JSON serializable
2024-08-04 20:18:02.761 [1722802660956446/optimize/7 (pid 24157)] 
2024-08-04 20:18:02.762 [1722802660956446/optimize/7 (pid 24157)] Task failed.
2024-08-04 20:18:02.762 This failed task will not be retried.
2024-08-04 20:18:02.762 [1722802660956446/optimize/8 (pid 24158)] Traceback (most recent call last):
2024-08-04 20:18:02.762 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:18:02.762 [1722802660956446/optimize/8 (pid 24158)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:18:02.762 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:18:02.763 [1722802660956446/optimize/8 (pid 24158)] return func(args, kwargs)
2024-08-04 20:18:02.763 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:18:02.763 [1722802660956446/optimize/8 (pid 24158)] return self.main(args, kwargs)
2024-08-04 20:18:02.763 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:18:02.763 [1722802660956446/optimize/8 (pid 24158)] rv = self.invoke(ctx)
2024-08-04 20:18:02.763 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:18:02.763 [1722802660956446/optimize/8 (pid 24158)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:18:02.763 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:18:02.763 [1722802660956446/optimize/8 (pid 24158)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:18:02.763 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] return callback(args, kwargs)
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] return f(get_current_context(), args, kwargs)
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] task.run_step(
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] self._exec_step_function(step_func)
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] step_function()
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:18:02.764 [1722802660956446/optimize/8 (pid 24158)] retrieved_docs = retrieve_documents(
2024-08-04 20:18:02.765 [1722802660956446/optimize/8 (pid 24158)] File "/workspaces/data-centric-deep-learning/course/week4/rag/vector.py", line 80, in retrieve_documents
2024-08-04 20:18:02.765 [1722802660956446/optimize/8 (pid 24158)] response = starpoint.query(
2024-08-04 20:18:02.765 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/starpoint/db.py", line 154, in query
2024-08-04 20:18:02.765 [1722802660956446/optimize/8 (pid 24158)] return self.reader.query(
2024-08-04 20:18:02.765 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/starpoint/reader.py", line 110, in query
2024-08-04 20:18:02.765 [1722802660956446/optimize/8 (pid 24158)] response = requests.post(
2024-08-04 20:18:02.765 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 115, in post
2024-08-04 20:18:02.765 [1722802660956446/optimize/8 (pid 24158)] return request("post", url, data=data, json=json, kwargs)
2024-08-04 20:18:02.765 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 59, in request
2024-08-04 20:18:02.765 [1722802660956446/optimize/8 (pid 24158)] return session.request(method=method, url=url, kwargs)
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 575, in request
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] prep = self.prepare_request(req)
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 486, in prepare_request
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] p.prepare(
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 371, in prepare
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] self.prepare_body(data, files, json)
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 511, in prepare_body
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] body = complexjson.dumps(json, allow_nan=False)
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/json/__init__.py", line 238, in dumps
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] kw).encode(obj)
2024-08-04 20:18:02.766 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/json/encoder.py", line 199, in encode
2024-08-04 20:18:02.767 [1722802660956446/optimize/8 (pid 24158)] chunks = self.iterencode(o, _one_shot=True)
2024-08-04 20:18:02.767 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/json/encoder.py", line 257, in iterencode
2024-08-04 20:18:02.767 [1722802660956446/optimize/8 (pid 24158)] return _iterencode(o, 0)
2024-08-04 20:18:02.767 [1722802660956446/optimize/8 (pid 24158)] File "/usr/local/lib/python3.10/json/encoder.py", line 179, in default
2024-08-04 20:18:02.767 [1722802660956446/optimize/8 (pid 24158)] raise TypeError(f'Object of type {o.__class__.__name__} '
2024-08-04 20:18:02.767 [1722802660956446/optimize/8 (pid 24158)] TypeError: Object of type SentenceTransformer is not JSON serializable
2024-08-04 20:18:02.767 [1722802660956446/optimize/8 (pid 24158)] 
2024-08-04 20:18:02.767 [1722802660956446/optimize/8 (pid 24158)] Task failed.
2024-08-04 20:18:02.768 This failed task will not be retried.
2024-08-04 20:18:02.768 [1722802660956446/optimize/9 (pid 24159)] Traceback (most recent call last):
2024-08-04 20:18:02.768 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 1126, in main
2024-08-04 20:18:02.768 [1722802660956446/optimize/9 (pid 24159)] start(auto_envvar_prefix="METAFLOW", obj=state)
2024-08-04 20:18:02.768 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/tracing/__init__.py", line 27, in wrapper_func
2024-08-04 20:18:02.768 [1722802660956446/optimize/9 (pid 24159)] return func(args, kwargs)
2024-08-04 20:18:02.768 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 829, in __call__
2024-08-04 20:18:02.768 [1722802660956446/optimize/9 (pid 24159)] return self.main(args, kwargs)
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 782, in main
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] rv = self.invoke(ctx)
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1259, in invoke
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] return _process_result(sub_ctx.command.invoke(sub_ctx))
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 1066, in invoke
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] return ctx.invoke(self.callback, ctx.params)
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/core.py", line 610, in invoke
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] return callback(args, kwargs)
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/_vendor/click/decorators.py", line 21, in new_func
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] return f(get_current_context(), args, kwargs)
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/cli.py", line 468, in step
2024-08-04 20:18:02.769 [1722802660956446/optimize/9 (pid 24159)] task.run_step(
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 650, in run_step
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] self._exec_step_function(step_func)
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/metaflow/task.py", line 62, in _exec_step_function
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] step_function()
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] File "/workspaces/data-centric-deep-learning/course/week4/scripts/optimize_params.py", line 128, in optimize
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] retrieved_docs = retrieve_documents(
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] File "/workspaces/data-centric-deep-learning/course/week4/rag/vector.py", line 80, in retrieve_documents
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] response = starpoint.query(
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/starpoint/db.py", line 154, in query
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] return self.reader.query(
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/starpoint/reader.py", line 110, in query
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] response = requests.post(
2024-08-04 20:18:02.770 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 115, in post
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] return request("post", url, data=data, json=json, kwargs)
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/requests/api.py", line 59, in request
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] return session.request(method=method, url=url, kwargs)
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 575, in request
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] prep = self.prepare_request(req)
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/requests/sessions.py", line 486, in prepare_request
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] p.prepare(
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 371, in prepare
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] self.prepare_body(data, files, json)
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/site-packages/requests/models.py", line 511, in prepare_body
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] body = complexjson.dumps(json, allow_nan=False)
2024-08-04 20:18:02.771 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/json/__init__.py", line 238, in dumps
2024-08-04 20:18:02.772 [1722802660956446/optimize/9 (pid 24159)] kw).encode(obj)
2024-08-04 20:18:02.772 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/json/encoder.py", line 199, in encode
2024-08-04 20:18:02.772 [1722802660956446/optimize/9 (pid 24159)] chunks = self.iterencode(o, _one_shot=True)
2024-08-04 20:18:02.772 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/json/encoder.py", line 257, in iterencode
2024-08-04 20:18:02.772 [1722802660956446/optimize/9 (pid 24159)] return _iterencode(o, 0)
2024-08-04 20:18:02.772 [1722802660956446/optimize/9 (pid 24159)] File "/usr/local/lib/python3.10/json/encoder.py", line 179, in default
2024-08-04 20:18:02.772 [1722802660956446/optimize/9 (pid 24159)] raise TypeError(f'Object of type {o.__class__.__name__} '
2024-08-04 20:18:02.772 [1722802660956446/optimize/9 (pid 24159)] TypeError: Object of type SentenceTransformer is not JSON serializable
2024-08-04 20:18:02.772 [1722802660956446/optimize/9 (pid 24159)] 
2024-08-04 20:18:02.772 [1722802660956446/optimize/9 (pid 24159)] Task failed.
2024-08-04 20:18:02.773 This failed task will not be retried.
2024-08-04 20:18:02.773 [1722802660956446/optimize/10 (pid 24160)] Task failed.
2024-08-04 20:18:02.773 This failed task will not be retried.
    Step failure:
    Step optimize (task-id 3) failed.

@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ python scripts/optimize_params.py --no-pylint run
Metaflow 2.12.7 executing OptimizeRagParams for user:vscode
Validating your flow...
    The graph looks good!
2024-08-04 20:26:18.616 Workflow starting (run-id 1722803178615534):
2024-08-04 20:26:18.623 [1722803178615534/start/1 (pid 27471)] Task is starting.
2024-08-04 20:26:22.717 [1722803178615534/start/1 (pid 27471)] Task finished successfully.
2024-08-04 20:26:22.720 [1722803178615534/get_search_space/2 (pid 27529)] Task is starting.
2024-08-04 20:26:26.793 [1722803178615534/get_search_space/2 (pid 27529)] Foreach yields 8 child steps.
2024-08-04 20:26:26.793 [1722803178615534/get_search_space/2 (pid 27529)] Task finished successfully.
2024-08-04 20:26:26.796 [1722803178615534/optimize/3 (pid 27582)] Task is starting.
2024-08-04 20:26:26.798 [1722803178615534/optimize/4 (pid 27583)] Task is starting.
2024-08-04 20:26:26.801 [1722803178615534/optimize/5 (pid 27584)] Task is starting.
2024-08-04 20:26:26.805 [1722803178615534/optimize/6 (pid 27585)] Task is starting.
2024-08-04 20:26:26.823 [1722803178615534/optimize/7 (pid 27586)] Task is starting.
2024-08-04 20:26:26.851 [1722803178615534/optimize/8 (pid 27587)] Task is starting.
2024-08-04 20:26:26.868 [1722803178615534/optimize/9 (pid 27588)] Task is starting.
2024-08-04 20:26:26.887 [1722803178615534/optimize/10 (pid 27589)] Task is starting.
2024-08-04 20:26:37.653 [1722803178615534/optimize/10 (pid 27589)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0.5, hyde_embeddings=True)
2024-08-04 20:26:38.095 [1722803178615534/optimize/4 (pid 27583)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0, hyde_embeddings=True)
2024-08-04 20:26:38.287 [1722803178615534/optimize/5 (pid 27584)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0.5, hyde_embeddings=False)
2024-08-04 20:26:38.307 [1722803178615534/optimize/6 (pid 27585)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0.5, hyde_embeddings=True)
2024-08-04 20:26:38.330 [1722803178615534/optimize/7 (pid 27586)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0, hyde_embeddings=False)
2024-08-04 20:26:38.407 [1722803178615534/optimize/3 (pid 27582)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0, hyde_embeddings=False)
2024-08-04 20:26:38.413 [1722803178615534/optimize/9 (pid 27588)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0.5, hyde_embeddings=False)
2024-08-04 20:26:38.414 [1722803178615534/optimize/8 (pid 27587)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0, hyde_embeddings=True)
100%|██████████| 197/197 [03:59<00:00,  1.21s/it]e/10 (pid 27589)] 0%|          | 0/197 [00:00<?, ?it/s]
100%|██████████| 197/197 [01:38<00:00,  2.00it/s]e/3 (pid 27582)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:30:38.166 [1722803178615534/optimize/3 (pid 27582)] Task finished successfully.
100%|██████████| 197/197 [03:52<00:00,  1.18s/it]e/4 (pid 27583)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:30:38.168 [1722803178615534/optimize/4 (pid 27583)] Task finished successfully.
100%|██████████| 197/197 [01:38<00:00,  2.00it/s]e/5 (pid 27584)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:30:38.169 [1722803178615534/optimize/5 (pid 27584)] Task finished successfully.
100%|██████████| 197/197 [03:51<00:00,  1.17s/it]e/6 (pid 27585)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:30:38.170 [1722803178615534/optimize/6 (pid 27585)] Task finished successfully.
100%|██████████| 197/197 [01:40<00:00,  1.96it/s]e/7 (pid 27586)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:30:38.174 [1722803178615534/optimize/7 (pid 27586)] Task finished successfully.
100%|██████████| 197/197 [04:01<00:00,  1.23s/it]e/8 (pid 27587)] 0%|          | 0/197 [00:00<?, ?it/s]
100%|██████████| 197/197 [01:40<00:00,  1.96it/s]e/9 (pid 27588)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:30:41.444 [1722803178615534/optimize/9 (pid 27588)] Task finished successfully.
2024-08-04 20:30:41.449 [1722803178615534/optimize/10 (pid 27589)] Task finished successfully.
2024-08-04 20:30:42.171 [1722803178615534/optimize/8 (pid 27587)] Task finished successfully.
2024-08-04 20:30:42.175 [1722803178615534/find_best/11 (pid 29332)] Task is starting.
2024-08-04 20:30:46.533 [1722803178615534/find_best/11 (pid 29332)] Task finished successfully.
2024-08-04 20:30:46.536 [1722803178615534/end/12 (pid 29379)] Task is starting.
2024-08-04 20:30:50.129 [1722803178615534/end/12 (pid 29379)] done! great work!
2024-08-04 20:30:50.872 [1722803178615534/end/12 (pid 29379)] Task finished successfully.
2024-08-04 20:30:50.873 Done!
@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ python scripts/optimize_params.py --no-pylint run
Metaflow 2.12.7 executing OptimizeRagParams for user:vscode
Validating your flow...
    The graph looks good!
2024-08-04 20:39:52.910 Workflow starting (run-id 1722803992909851):
2024-08-04 20:39:52.918 [1722803992909851/start/1 (pid 32717)] Task is starting.
2024-08-04 20:39:57.283 [1722803992909851/start/1 (pid 32717)] Task finished successfully.
2024-08-04 20:39:57.286 [1722803992909851/get_search_space/2 (pid 32778)] Task is starting.
2024-08-04 20:40:01.766 [1722803992909851/get_search_space/2 (pid 32778)] Foreach yields 8 child steps.
2024-08-04 20:40:01.766 [1722803992909851/get_search_space/2 (pid 32778)] Task finished successfully.
2024-08-04 20:40:01.769 [1722803992909851/optimize/3 (pid 32831)] Task is starting.
2024-08-04 20:40:01.771 [1722803992909851/optimize/4 (pid 32832)] Task is starting.
2024-08-04 20:40:01.775 [1722803992909851/optimize/5 (pid 32833)] Task is starting.
2024-08-04 20:40:01.778 [1722803992909851/optimize/6 (pid 32834)] Task is starting.
2024-08-04 20:40:01.795 [1722803992909851/optimize/7 (pid 32835)] Task is starting.
2024-08-04 20:40:01.815 [1722803992909851/optimize/8 (pid 32836)] Task is starting.
2024-08-04 20:40:01.831 [1722803992909851/optimize/9 (pid 32837)] Task is starting.
2024-08-04 20:40:01.841 [1722803992909851/optimize/10 (pid 32839)] Task is starting.
2024-08-04 20:40:13.476 [1722803992909851/optimize/9 (pid 32837)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0.5, hyde_embeddings=False)
2024-08-04 20:40:13.500 [1722803992909851/optimize/6 (pid 32834)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0.5, hyde_embeddings=True)
2024-08-04 20:40:13.559 [1722803992909851/optimize/8 (pid 32836)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0, hyde_embeddings=True)
2024-08-04 20:40:13.627 [1722803992909851/optimize/5 (pid 32833)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0.5, hyde_embeddings=False)
2024-08-04 20:40:13.674 [1722803992909851/optimize/10 (pid 32839)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0.5, hyde_embeddings=True)
2024-08-04 20:40:13.689 [1722803992909851/optimize/3 (pid 32831)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0, hyde_embeddings=False)
2024-08-04 20:40:13.717 [1722803992909851/optimize/7 (pid 32835)] Evaluating configuration: DotMap(embedding='thenlper/gte-small', text_search_weight=0, hyde_embeddings=False)
2024-08-04 20:40:13.853 [1722803992909851/optimize/4 (pid 32832)] Evaluating configuration: DotMap(embedding='all-MiniLM-L6-v2', text_search_weight=0, hyde_embeddings=True)
100%|██████████| 197/197 [03:50<00:00,  1.17s/it]e/6 (pid 32834)] 0%|          | 0/197 [00:00<?, ?it/s]
100%|██████████| 197/197 [01:36<00:00,  2.04it/s]e/3 (pid 32831)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:44:05.443 [1722803992909851/optimize/3 (pid 32831)] Task finished successfully.
100%|██████████| 197/197 [03:53<00:00,  1.18s/it]e/4 (pid 32832)] 0%|          | 0/197 [00:00<?, ?it/s]
100%|██████████| 197/197 [01:37<00:00,  2.03it/s]e/5 (pid 32833)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:44:08.161 [1722803992909851/optimize/5 (pid 32833)] Task finished successfully.
100%|██████████| 197/197 [01:38<00:00,  2.00it/s]e/7 (pid 32835)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:44:08.163 [1722803992909851/optimize/7 (pid 32835)] Task finished successfully.
100%|██████████| 197/197 [03:50<00:00,  1.17s/it]e/8 (pid 32836)] 0%|          | 0/197 [00:00<?, ?it/s]
100%|██████████| 197/197 [01:39<00:00,  1.98it/s]e/9 (pid 32837)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:44:08.164 [1722803992909851/optimize/9 (pid 32837)] Task finished successfully.
100%|██████████| 197/197 [03:58<00:00,  1.21s/it]e/10 (pid 32839)] 0%|          | 0/197 [00:00<?, ?it/s]
2024-08-04 20:44:14.190 [1722803992909851/optimize/4 (pid 32832)] Task finished successfully.
2024-08-04 20:44:14.191 [1722803992909851/optimize/6 (pid 32834)] Task finished successfully.
2024-08-04 20:44:14.192 [1722803992909851/optimize/8 (pid 32836)] Task finished successfully.
2024-08-04 20:44:14.922 [1722803992909851/optimize/10 (pid 32839)] Task finished successfully.
2024-08-04 20:44:14.925 [1722803992909851/find_best/11 (pid 34628)] Task is starting.
2024-08-04 20:44:19.263 [1722803992909851/find_best/11 (pid 34628)] Task finished successfully.
2024-08-04 20:44:19.266 [1722803992909851/end/12 (pid 34688)] Task is starting.
2024-08-04 20:44:22.867 [1722803992909851/end/12 (pid 34688)] done! great work!
2024-08-04 20:44:23.612 [1722803992909851/end/12 (pid 34688)] Task finished successfully.
2024-08-04 20:44:23.613 Done!
@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ git gc
git fsck
Enumerating objects: 792, done.
Counting objects: 100% (792/792), done.
Delta compression using up to 4 threads
Compressing objects: 100% (511/511), done.
Writing objects: 100% (792/792), done.
Total 792 (delta 267), reused 739 (delta 242), pack-reused 0 (from 0)
Enumerating cruft objects: 3, done.
Traversing cruft objects: 7, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
Checking object directories: 100% (256/256), done.
Checking objects: 100% (795/795), done.
dangling tree b354a7bfab575c932fd3ca032b6f77940cb2fdd2
dangling tree 78dea8daa7e753cd9693cb38b3ee4bb6aac42ed3
Verifying commits in commit graph: 100% (51/51), done.
@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ git push
Enumerating objects: 71, done.
Counting objects: 100% (71/71), done.
Delta compression using up to 4 threads
Compressing objects: 100% (50/50), done.
error: RPC failed; HTTP 500 curl 22 The requested URL returned error: 500
send-pack: unexpected disconnect while reading sideband packet
Writing objects: 100% (57/57), 2.73 GiB | 55.89 MiB/s, done.
Total 57 (delta 11), reused 51 (delta 5), pack-reused 0 (from 0)
fatal: the remote end hung up unexpectedly
Everything up-to-date
@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ git reset --hard origin/main
HEAD is now at 3fe1901 FEAT: Week 4 Project (#26)
@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ git commit
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ git revert
usage: git revert [--[no-]edit] [-n] [-m <parent-number>] [-s] [-S[<keyid>]] <commit>...
   or: git revert (--continue | --skip | --abort | --quit)

    --quit                end revert or cherry-pick sequence
    --continue            resume revert or cherry-pick sequence
    --abort               cancel revert or cherry-pick sequence
    --skip                skip current commit and continue
    --[no-]cleanup <mode> how to strip spaces and #comments from message
    -n, --no-commit       don't automatically commit
    --commit              opposite of --no-commit
    -e, --[no-]edit       edit the commit message
    -s, --[no-]signoff    add a Signed-off-by trailer
    -m, --[no-]mainline <parent-number>
                          select mainline parent
    --[no-]rerere-autoupdate
                          update the index with reused conflict resolution if possible
    --[no-]strategy <strategy>
                          merge strategy
    -X, --[no-]strategy-option <option>
                          option for merge strategy
    -S, --[no-]gpg-sign[=<key-id>]
                          GPG sign commit
    --[no-]reference      use the 'reference' format to refer to commits

@giterinhub ➜ /workspaces/data-centric-deep-learning/course/week4 (main) $ 

```