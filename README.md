# bazel-pip-tensorflow-lookup-error

See: https://github.com/bazelbuild/rules_python

`piptool` is bundling an old version of `pip==9.0.3`; which cannot find `tensorflow==2.3.0`

## Install with virtualenv + pip ...

Constructing / testing the environment with `virtualenv` works:

    $ virtualenv -p python3.7 ve
    $ source ve/bin/activate
    $ pip-sync


## Install with bazel ...

Syncing bazel with `pip_install` does not:

    $ bazel --version
    bazel 3.3.1
    $ bazel sync

Which blows up with this::

    ERROR: no such package '@pip_deps//': pip_import failed: Collecting absl-py==0.10.0 (from -r /home/crutcher/git/bazel-pip-tensorflow-lookup-error/requirements.txt (line 7))
      Downloading https://files.pythonhosted.org/packages/b9/07/f69dd3367368ad69f174bfe426a973651412ec11d48ec05c000f19fe0561/absl_py-0.10.0-py3-none-any.whl (127kB)
      Saved ./absl_py-0.10.0-py3-none-any.whl
    Collecting astunparse==1.6.3 (from -r /home/crutcher/git/bazel-pip-tensorflow-lookup-error/requirements.txt (line 8))
      Downloading https://files.pythonhosted.org/packages/2b/03/13dde6512ad7b4557eb792fbcf0c653af6076b81e5941d36ec61f7ce6028/astunparse-1.6.3-py2.py3-none-any.whl
      Saved ./astunparse-1.6.3-py2.py3-none-any.whl
    ...
    Collecting tensorboard==2.3.0 (from -r /home/crutcher/git/bazel-pip-tensorflow-lookup-error/requirements.txt (line 34))
      Downloading https://files.pythonhosted.org/packages/e9/1b/6a420d7e6ba431cf3d51b2a5bfa06a958c4141e3189385963dc7f6fbffb6/tensorboard-2.3.0-py3-none-any.whl (6.8MB)
      Saved ./tensorboard-2.3.0-py3-none-any.whl
    Collecting tensorflow-estimator==2.3.0 (from -r /home/crutcher/git/bazel-pip-tensorflow-lookup-error/requirements.txt (line 35))
      Downloading https://files.pythonhosted.org/packages/e9/ed/5853ec0ae380cba4588eab1524e18ece1583b65f7ae0e97321f5ff9dfd60/tensorflow_estimator-2.3.0-py2.py3-none-any.whl (459kB)
      Saved ./tensorflow_estimator-2.3.0-py2.py3-none-any.whl
    Collecting tensorflow==2.3.0 (from -r /home/crutcher/git/bazel-pip-tensorflow-lookup-error/requirements.txt (line 36))
     (  Could not find a version that satisfies the requirement tensorflow==2.3.0 (from -r /home/crutcher/git/bazel-pip-tensorflow-lookup-error/requirements.txt (line 36)) (from versions: 1.13.0rc1, 1.13.0rc2, 1.13.1, 1.13.2, 1.14.0rc0, 1.14.0rc1, 1.14.0, 2.0.0a0, 2.0.0b0, 2.0.0b1)
    No matching distribution found for tensorflow==2.3.0 (from -r /home/crutcher/git/bazel-pip-tensorflow-lookup-error/requirements.txt (line 36))
    )
    
    
        
