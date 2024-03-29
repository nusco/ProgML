## Setup Instructions

_Updated: Set 17th 2023_

Here's how you can set up your system to run the [examples from the book](https://media.pragprog.com/titles/pplearn/code/pplearn-code.zip).

The situation with Python versions and ML libraries is… complicated. Even if I pinned down all the library versions, these instructions might not work for your specific case. If that happens, please try two things:

* Look at the [Troubleshooting](#troubleshooting) section below.
* If that doesn't help, please drop me a message on the [book's forum](https://devtalk.com/books/programming-machine-learning). I'll check out the issue and update this page.

### Installing Globally

If you're looking for a quick setup, you can install Python and the libraries globally. However, this approach can fail if you already have clashing versions of the libraries or Python. In that case, check out the <a href="#installing-with-conda">Conda installation instructions</a> instead.

To install globally, you need Python 3.7. Check your version of Python:

    python3 --version

If you don't have Python 3.7.x, check out [how to install it for your system](https://www.python.org/). 

Once you have Python, install the libraries:

    pip3 install numpy==1.19.5
    pip3 install matplotlib==3.2.2
    pip3 install seaborn==0.11.1
    pip3 install scikit-learn==0.24.1
    pip3 install keras==2.3.1

If you want to run the code in a Jupyter Notebook, then you also need Jupyter:

    pip3 install jupyter==1.0.0

Any trouble? Then read forward for Conda installation instructions.


### Installing with Conda

To control the visibility of your libraries, you can install them with the [Conda](https://conda.io) package manager. Compared to pip, Conda helps you keep Python environments tidy and isolated. On the minus side, Conda doesn't always play nice with other package managers, such as Homebrew. I prefer Conda to pip, but your mileage may vary.

If you opt for Conda, consider downloading the minimal distribution [Miniconda](https://docs.conda.io/en/latest/miniconda.html), because the complete distribution is a large install.

Here is how you create a new Python 3 environment named `machinelearning` with Conda:

    conda create --name=machinelearning python=3.7

Now you can make `machinelearning` the current active environment:

    conda activate machinelearning

Next step, you can install libraries in the active environment:

    conda install numpy=1.19.5
    conda install matplotlib=3.2.2
    conda install seaborn=0.11.1
    conda install scikit-learn=0.24.1
    conda install keras=2.3.1
    conda install jupyter=1.0.0

The libraries will stay visible as long as the environment is active. Once you deactivate the environment with `conda deactivate`, or close the terminal, the libraries are gone. To re-activate the environment and get back the libraries, use `conda activate machinelearning` again.

 Happy hacking!

<a name="troubleshooting"/>
### Troubleshooting

#### “Installing Keras didn't install Tensorflow.”

Then install a compatible version of Tensorflow. If you're using pip:

    pip3 install tensorflow

If you're using Conda:

    conda install tensorflow


#### “I cannot install Python 3.7 on my Mac.”

I stumbled upon this issue myself: Python 3.7 isn't supported on the latest Apple silicon. You can still install it using [PyEnv](https://github.com/pyenv/pyenv#basic-github-checkout), but the process is error-prone.

Your best bet is to use more recent versions of both Python and the libraries. That will force you to tweak some of the later examples in the book–-but it's a minor change. Here is how it works:

1. Follow the same instructions as above, but use `Python 3.9` instead of `Python 3.7`.

2. Install these libraries:

    - `numpy 1.19.5`
    - `matplotlib 3.5`
    - `seaborn 0.11.1`
    - `scikit-learn 0.24.1`
    - `keras 2.6.0`
    - `tensorflow 2.6.0`
    - `jupyter 1.0.0`

3. You shouldn't have any issue running the code in Parts I and II of the book. Once you get to Part III, and you start using Keras, you'll get error messages like this:

    `ImportError: cannot import name 'RMSprop' from 'keras.optimizers'`

Here is the issue: as Keras progressed from version 2.3 to 2.6, the `keras.*` packages moved to `tensorflow.keras.*`. Wherever you have one of these errors, you can quickly fix it manually. For example, if you get an error on an import such as this one…

    from keras.optimizers import […]

…you should change that line to:

    from tensorflow.keras.optimizers import […]

#### “I'm getting an error: `unexpected keyword argument 'projection'`”

If you're still getting this issue after following the instructions above, then edit the code as suggested in [this forum message](https://forum.devtalk.com/t/programming-machine-learning-some-plot-files-are-throwing-error/83609/5).

#### “I'm still having trouble.”

Then please [let me know](https://devtalk.com/books/programming-machine-learning).