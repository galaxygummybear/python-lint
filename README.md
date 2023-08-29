# Pre-commit Hook


## To use the pre-commit hook, run the following command:
```pwsh
pre-commit run --show-diff-on-failure --color=always --files <allthefiles>
```

##### Replace `<allthefiles>` with the list of files you want to run the pre-commit hooks on.

##### For Example:
```pwsh
pre-commit run --show-diff-on-failure --color=always --files ivy/functional/backends/jax/activations.py ivy/functional/backends/mxnet/activations.py ivy/functional/backends/numpy/activations.py ivy/functional/backends/paddle/activations.py ivy/functional/backends/tensorflow/activations.py ivy/functional/backends/torch/activations.py ivy/functional/frontends/tensorflow/nn.py ivy/functional/frontends/tensorflow/raw_ops.py ivy/functional/ivy/activations.py ivy_tests/test_ivy/test_frontends/test_tensorflow/test_raw_ops.py
```

## Explanation:
* ##### `pre-commit run` : Executes pre-commit hooks on the specified files.
* ##### `--show-diff-on-failure` : Displays the changes made by the hooks if any hook fails.
* ##### `--color=always` : Provides colorized output for better visualization.
* ##### `--files <allthefiles>` : Specifies the list of files to run the pre-commit hooks on.



## Example Output:
```
black....................................................................Passed
autoflake................................................................Passed
flake8...................................................................Failed
- hook id: flake8
- exit code: 1

docformatter.............................................................Passed
pydocstyle...............................................................Passed
ivy-lint.................................................................Passed
All changes made by hooks:
```


## If you want to use this in a new project, then create `.pre-commit-config.yaml` file with some basic configuration. 
##### You can run this command: 
```bash
pre-commit sample-config
```
to get the basic configurations. 
Or you can use this configurations:

```bash
repos:
  - repo: https://github.com/psf/black
    rev: 23.7.0
    hooks:
      - id: black
        language_version: python3
        args:
          - "--preview"
  - repo: https://github.com/PyCQA/autoflake
    rev: v2.2.0
    hooks:
      - id: autoflake
  - repo: https://github.com/pycqa/flake8
    rev: 6.1.0
    hooks:
      - id: flake8
  - repo: https://github.com/PyCQA/docformatter
    rev: v1.7.5
    hooks:
      - id: docformatter
  - repo: https://github.com/pycqa/pydocstyle
    rev: 6.3.0
    hooks:
      - id: pydocstyle
```

Once you have this configurations, then install the git hook scripts, using :
```bash
pre-commit install
``` 
command. This will set up the git hook scripts.

### Then just commit add and commit your repo as usual. It will initialise the process.
