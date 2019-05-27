> Written with [StackEdit](https://stackedit.io/).

# Guide to Setting up your Computer

#### Install python and the required packages

Follow this instructions if you don't have python installed in your computer.

-   Visit the [continuum analytics websit](https://www.anaconda.com/download/)[e](https://www.continuum.io/downloads)
    
-   Scroll down and download the python 3.6 version
    
-   Install it according to your operating system by following the instructions
    

If you already have a regular Python 3 installation, you may risk conflicting version issues with Anaconda if the PYTHONPATH is not updated correctly. If you don't manage to run the notebooks in your current python installation, instead of installing Anaconda, try first creating a virtual environment using your python installation with python 3.6 and the package versions required for these lectures.

  

#### Install Keras, Theano and Tensorflow

**Note**: we use Keras only in section 13 at the end of the course. You may as well choose to install it towards the end of the course.

Keras supports up to python 3.6. So if you are using the latest version of python, we suggest you create a virtual environment and install a former python version. We are going to show you how to create virtual environments in a later section. For now, if you are using anaconda follow this  [link](https://docs.conda.io/projects/conda/en/latest/user-guide/getting-started.html#managing-python)  to create the environment of your choice.  

Briefly (for windows users) in the anaconda prompt:

1.  conda create -n py36 python=3.6 anaconda
2.  activate py36
3.  conda install theano
4.  pip install tensorflow
5.  pip install keras

If you are using mac or Ubuntu, follow the recommendations in the  [Keras](https://keras.io/#installation),  [Theano](http://deeplearning.net/software/theano/install.html#install)  and  [Tensorflow](https://www.tensorflow.org/install/)  documentation.

To switch backends between Theano and Tensorflow follow this  [link](https://keras.io/backend/).

To add the created environments to the Jupyter notebook follow this  [link](https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments). Briefly, if using conda, from anaconda prompt:

1.  source activate py36
2.  python -m ipykernel install --user --name py36 --display-name "Python py36"
3.  source activate other-env
4.  python -m ipykernel install --user --name other-env --display-name "Python (other-env)"

  

#### Create a Kaggle account

-   Visit [Kaggle's website](http://www.kaggle.com/)
    
-   Click on the "Create an account" button and follow the instructions to set up your account
    

Download data sets from Kaggle

-   Visit the [House Sale Price competition](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data) website, scroll down and click on train.csv.zip and then on the download button on the right. Unzip the content. Rename the data set to houseprice.csv
    
-   Visit the [V2 Plant Seedlings Dataset](https://www.kaggle.com/vbookshelf/v2-plant-seedlings-dataset/home) website, go to the tab "Data" and click on the buttom "Download (2GB)". Unzip the file. Make sure you remove the apostrophe in the folder "Sheperd's Purse" so that it is renamed to "Sheperds Purse" to avoid python string parsing issues.
    

-   [Cours](https://www.udemy.com/deployment-of-machine-learning-models/learn/lecture/13595392#content)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NTk3MTI1MTZdfQ==
-->