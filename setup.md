## Setup Instructions

_Updated: Jan 27th 2021_

Here's how you can set up your system to run the [examples from the book](https://media.pragprog.com/titles/pplearn/code/pplearn-code.zip). If these instructions don't work for you, please drop me a message on the [book's forum](https://devtalk.com/books/programming-machine-learning). I'll check out the issue and update this page.

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

The libraries will stay visible as long as the environment is active. Once you deactivate the environment with `conda deactivate`, or close the terminal, the
libraries are gone. To re-activate the environment and get back the libraries, use `conda activate machinelearning` again.

Remember to [let me know](https://devtalk.com/books/programming-machine-learning) if these instructions don't work for you. Happy hacking!
