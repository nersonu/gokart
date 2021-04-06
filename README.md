# gokart

[![Test](https://github.com/m3dev/gokart/workflows/Test/badge.svg)](https://github.com/m3dev/gokart/actions?query=workflow%3ATest)
[![](https://readthedocs.org/projects/gokart/badge/?version=latest)](https://gokart.readthedocs.io/en/latest/)
[![Python Versions](https://img.shields.io/pypi/pyversions/gokart.svg)](https://pypi.org/project/gokart/)
[![](https://img.shields.io/pypi/v/gokart)](https://pypi.org/project/gokart/)
![](https://img.shields.io/pypi/l/gokart)

Gokart solves reproducibility, task dependencies, constraints of good code, and ease of use for Machine Learning Pipeline.


# Good thing about gokart

Here are some good things about gokart.

- The following data for each Task is stored separately in a pkl file with hash value
    - task output data
    - imported all module versions
    - task processing time
    - random seed in task
    - displayed log
    - all parameters set as class variables in the task
- If change parameter of Task, rerun spontaneously.
    - The above file will be generated with a different hash value
    - The hash value of dependent task will also change and both will be rerun
- The above output is exchanged between tasks as an intermediate file, which is memory-friendly
- pandas.DataFrame type and column checking during I/O
- Directory structure of saved files is automatically determined from structure of script
- Seeds for numpy and random are automatically fixed
- Can code while adhering to SOLID principles as much as possible
- Tasks are locked via redis even if they run in parallel

*These are all functions baptized for creating Machine Learning batches. Provides an excellent environment for reproducibility and team development.*


# Getting Started

Within the activated Python environment, use the following command to install gokart.

```
pip install gokart
```

[Documentation](https://gokart.readthedocs.io/en/latest/) for the latest release is hosted on readthedocs.


# Quickstart

A minimal gokart tasks looks something like this:


```python
import gokart

class Example(gokart.TaskOnKart):
    def run(self):
        self.dump('Hello, world!')

task = Example()
output = gokart.build(task)
print(output)
```

`gokart.build` return the result of dump by `gokart.TaskOnKart`. The example will output the following.


```
Hello, world!
```


# Achievements

gokart is a proven product.

- It's actually been used by [m3.inc](https://corporate.m3.com/en) for over 3 years
- Natural Language Processing Competition by [Nishika.inc](https://nishika.com) 2nd prize : [Solution Repository](https://github.com/vaaaaanquish/nishika_akutagawa_2nd_prize)


# Thanks

gokart is a wrapper for luigi. Thanks to luigi and dependent projects!

- [luigi](https://github.com/spotify/luigi)
