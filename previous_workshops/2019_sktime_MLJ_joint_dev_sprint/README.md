The [Alan Turing Institute](https://turing.ac.uk) is developing ML/AI toolboxes, including
* a Julia package called [MLJ](https://github.com/alan-turing-institute/MLJ.jl), Machine Learning in Julia,
* the sktime Python package.

The aims of this joint development sprint are to:
* Conduct first-line user testing of our latest stable version,
* Create tutorials,
* Improve documentation,
* Interface, implement or integrate existing models from other packages,
* Implement new features.

Please find below:
* the [schedule](#schedule),
* a [getting started guide](#getting-started) for Python and sktime,
* [exercises](#exercises-for-user-testing) for user testing,
* potential sktime [projects](#workshop-projects) to work on,
* interesting [design questions](#design-questions) to discuss. 

Please also check out:
* our [Code of Conduct](https://github.com/alan-turing-institute/sktime/blob/dev/CODE_OF_CONDUCT.md), 
* our [tips](https://github.com/alan-turing-institute/sktime/blob/dev/CONTRIBUTING.md) on how to best contribute to sktime,
* the accompanying [MLJ wiki pages](https://github.com/alan-turing-institute/MLJ.jl/wiki/2019-Sprint-Resources).

# Schedule

**Day 1 – Introductions, tutorials, user testing**

* 9-10am arrival, registration, breakfast

*arrival*: Torrington Place 1-19, ground floor, main entrance reception, please wait in lobby

* 10am-11:00am: welcome, introduction rounds (what bring to table, expectations, interest), overview of week, fire walk
* 11am – 12:30pm: (short) Julia intro, MLJ intro
* 12:30pm: lunch
* 1:30-2:30pm: MLJ user testing
* 2:30pm – 4pm: time series learning intro, (short) scikit-learn reminder, sktime intro 
* 4pm – 5pm: sktime user testing
* Evening: dinner/social

**Day 2 – API overview, writing new models, contributing interfaced models**
* 10am – 10:45am: ML APIs, with focus on “joint principles”; contrib via Github
* 10:45am – 11:30am: MLJ/sktime interfaces, interfacing models, models to interface (medium difficulty projects)
* 11:30am: discussion of projects, brainstorming and coordination (split in groups) 
* 11:30am – 5pm: user testing/ model implementation
* 12:30pm: lunch
* 4pm: joint design questions discussion
* Evening: dinner

**Day 3 – special projects**
* 10-11am: “MLJ special projects part I”: tutorial & todos -> Turing.jl integration 
* 11am – 1pm: work + lunch
* 1-2pm: “sktime special projects part I”: tutorial & todos -> pipelines and reduction
* 2-5pm: work
* 4pm post: joint design questions discussion 
* Evening: dinner/social

**Day 4 – special projects**
* 10-11am: “sktime special projects part II”: tutorial & todos -> supervised forecasting, deep learning 
* 11am – 1pm: work + lunch
* 1-2pm: “MLJ special projects part II”: tutorial & todos -> MLJFlux.jl (flux integration)
* 2-5pm: work
* 4pm post: joint design questions discussion 
* Evening: dinner

**Day 5 – wrap-up and next step**
* 10am – 2pm: work & lunch
* 2-3:30pm: next steps discussion, planning 
* 3:30-4pm: goodbye
* 4pm post: social

# Getting started
To install Python, we recommend downloading the [Anaconda Distribution](https://www.anaconda.com) and follow their installation instructions [here](https://docs.anaconda.com/anaconda/user-guide/getting-started/). You will also need Jupyter Notebooks (which should come with the default Anaconda Distribution), here's a [guide](https://jupyter.org/install.html) on how to get started with Jupyter.  

To install sktime, follow our installation instructions [here](https://github.com/alan-turing-institute/sktime/blob/dev/README.rst). 

In order to contribute to sktime, you may also want to [fork](https://help.github.com/en/articles/fork-a-repo) the repository on Github and create a local [clone](https://help.github.com/en/articles/cloning-a-repository) of it, following the instructions in our [contributing guidelines](https://github.com/alan-turing-institute/sktime/blob/master/CONTRIBUTING.md).

# Exercises for user testing
Please find the exercise notebook for the sktime user testing session [here](https://github.com/sktime/sktime-workshops/previous-workshops/2019_sktime_MLJ_joint_dev_sprint/user_testing.ipynb).

# Workshop projects

## Time series classification
### Time Series Classification with Deep Learning

Lead: James Large

List of tasks: https://github.com/alan-turing-institute/sktime/projects/5

Deep learning has become the most popular approach for time series classification. In this project we wish to provide an interface between sktime and keras that makes it easy to develop alternative network structures within the same framework we use for other classification algorithms. For background, the starting point is this [paper](https://arxiv.org/abs/1809.04356), the lead author, Hassan Fawaz, has begun the integration. 

See (https://github.com/James-Large/sprint-dlsetup) for details

### Time Series Classification with Shapelets

Lead: David Guijo

List of tasks: https://github.com/alan-turing-institute/sktime/projects/6

Shapelets are a popular time series data mining primitive. We use them as a transform (overlap with project 5). Other popular uses are as a forest and as a form of convolution. There is some shapelet functionality already in sktime. This project will look at standardising this, then porting in popular variants, such as Shapelet Forest ([paper](https://dl.acm.org/citation.cfm?id=2992709), [repo](https://github.com/isakkarlsson/wildboar))

### Time Series Classification with Dictionary Based Classifiers


Lead: Matthew Middlehurst

List of tasks: https://github.com/alan-turing-institute/sktime/projects/7

Dictionary based classifiers count the frequency of patterns, then classify based on the similarity of a series. For each series, the steps involve running a sliding window across the whole series. For each window, the sub-time series is discretised into a word (sequence of discrete symbols). A count is made of the occurrence of each word, and the resulting histogram is used as features to classify. A good visual is [here](https://www2.informatik.hu-berlin.de/~schaefpa/boss/). This project will involve adding the functionality of three algorithms to sktime:
1) Bag-of-Patterns (BoP), [paper](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.444.177&rep=rep1&type=pdf)
2) Bag-of-SFA-Symbols (BOSS), [paper](https://www2.informatik.hu-berlin.de/~schaefpa/boss.pdf)
3) Word ExtrAction for time SEries cLassification (WEASEL), [paper](https://arxiv.org/pdf/1701.07681.pdf)

The author of the last two papers, Patrick Schäfer (<patrick.schaefer@hu-berlin.de>) is happy to help. There is a Python implementation [here](https://github.com/johannfaouzi/pyts/tree/master/pyts) to use as a comparison.

### Time Series to Series Transformers

Lead: Tony Bagnall

List of tasks: https://github.com/alan-turing-institute/sktime/projects/8

Many time series tasks are based on transformation. This project will involve the inclusion of many popular transformation based techniques. This is a good project for those getting started, as most transformations can be performed by interfacing to sklearn. Details of existing implementations we might use are [here](https://github.com/alan-turing-institute/sktime/issues/6). We are happy to interface to tools from common packages such as scipy or [tsfresh](https://tsfresh.readthedocs.io/en/latest/), but will want to port in code from less established repos such as tslearn. 

## Classical forecasting

Lead: Markus Löning

List of tasks: https://github.com/alan-turing-institute/sktime/projects/3

A central time series related learning task is classical forecasting, i.e. the temporal forward prediction of a single series given data on its past realisation and potentially other covariate time series. The main tasks will be the following: 

* Integrate existing methods, see e.g. the time series module from [statsmodels](https://www.statsmodels.org/stable/index.html) and the [M4 competition](https://github.com/M4Competition/M4-methods) for additional baseline and advanced methods, 
* Adding regressor counterparts to existing time series classifiers, e.g. TimeSeriesForestRegressor 
* Implement pipeline and transformer functionality for classical forecasting,
* Develop tuning framework,
* Extend orchestration and evaluation from time series classification to forecasting setting,
* Add other reduction strategies.

## Supervised forecasting

Lead: Markus Löning

List of tasks: https://github.com/alan-turing-institute/sktime/projects/4

Supervised forecasting describes the learning task of temporal forward prediction when multiple i.i.d. samples of the same time series are available, usually known as longitudinal or panel data. 

## Other projects
* Create new tutorials,
* Improve documentation,
* Improve extension guidelines and tests,
* Write and integrate consistent data input checks for algorithms,
* Extend unit tests.

# Design questions
* Scientific typing of complex objects, e.g. data arrays for time series,
* Tuning of heterogeneous ensembles.