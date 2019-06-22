# Crash Course in Contributing to Scikit-learn:  Workflow

PR = Pull Request  
**Important Note:**  Please include **(#wimlds)** in your PR description so we can track them. 

---

It's best to follow the up-to-date instructions on the the
[development guide](https://scikit-learn.org/dev/developers/contributing.html#ways-to-contribute),
but here's also a set of hints which could be useful.

## PART A:  Set-up work environment

#### Set up virtual environment
```bash
conda create -n sklearndev numpy scipy matplotlib pytest sphinx cython ipykernel
```
#### Activate virtual environment:
#### Windows
```bash
activate sklearndev
```
or
```bash
activate.bat sklearndev
```

#### Installing development dependacies
```sh
pip install cython pytest flake8
```
---

## PART B:  Set-up repository

### Fork repo:  https://github.com/scikit-learn/scikit-learn

### Set up local repo  
#### `git clone` your forked repo url.  

>my example
```bash
git clone https://github.com/reshamas/scikit-learn.git
```

#### `cd scikit-learn` into your folder

>my example
```bash
cd scikit-learn
```

#### Add `upstream` remote
```
git remote add upstream https://github.com/scikit-learn/scikit-learn.git
```

#### Check remotes are there using `git remote -v`

>my example
```bash
origin	https://github.com/reshamas/scikit-learn.git (fetch)
origin	https://github.com/reshamas/scikit-learn.git (push)
upstream	https://github.com/scikit-learn/scikit-learn.git (fetch)
upstream	https://github.com/scikit-learn/scikit-learn.git (push)
```

### Update local repo
```bash
git pull upstream master
```

### To fetch (someone else's) PR:
```bash
git fetch https://github.com/theirusername/reponame.git theirbranch:ourbranch
```


#### Build and run tests
```bash
pip install -e .
```
Note:  this will overwrite existing installations
Reference:  ["Editable" Installs](https://pip.pypa.io/en/stable/reference/pip_install/#examples)

---

## PART C:  Select issue
- Pick an issue to work on:  https://github.com/scikit-learn/scikit-learn/issues
- Comment on issue with:  *I'm working on this*

---

## PART D:  Fixing issue
- Explore and fix issue.  This will take the majority of time (!)
- Make updates to file `<file_name>`


---

## PART E:  Committing change 

#### Create feature branch

```bash
git checkout -b <feature_branch>
```

#### Commit changes to branch
Please include **(#wimlds)** in your PR so we can track them.  
 
```bash
git add <file_name>
git commit -m 'description for fix (#wimlds)'
```

---

## PART F:  Run tests

#### `flake8` formatting test
- `flake8` tests for formatting errors

```bash
flake8 <file_name>
```

#### `pytest sklearn` tests
- The [full test suite](http://scikit-learn.org/stable/developers/tips.html) takes fairly long to run
- Run tests  
```bash
pytest sklearn
```

This is an **example** of the output of a *successful* `pytest sklearn`:  [pytest_sklearn_output](pytest_sklearn_output.md)

### Create test file

#### Run tests on individual test files  
- Create test file under `tests` directory
- Run test file

```bash
pytest <test_file>
```

>example
```bash
pytest /Users/reshamashaikh/scikit-learn/sklearn/metrics/tests/test_classifier.py
pytest /Users/reshamashaikh/scikit-learn/sklearn/metrics/tests/test_mixture.py
```

This is an **example** of the output of a *successful* `pytest test_classification.py`:  
```bash
(sklearndev) % pytest sklearn/metrics/tests/test_classification.py
============================================================ test session starts ============================================================
platform darwin -- Python 3.7.1, pytest-4.0.0, py-1.7.0, pluggy-0.8.0
rootdir: /Users/reshamashaikh/scikit-learn, inifile: setup.cfg
collected 75 items                                                                                                                          

sklearn/metrics/tests/test_classification.py ...........................................................................              [100%]

=================================================== 75 passed, 3 warnings in 9.49 seconds ===================================================
(sklearndev) %
```

---

## PART G:  Submit Pull Request
#### After all tests have passed, push update file(s) to feature branch
- `test_file` should be committed to feature branch as well

```bash
git add <test_file>
git commit -m 'description for test file'
git push origin <feature_branch>
```

#### Submit PR  
Do this on GitHub.

---

## Part H:  Regression Tests on GitHub
These tests happen automatically after a PR has been submitted:  

<p>
</p>

<kbd>
<img src="images/reg_tests.png"  width="80%" height="80%" />
</kbd>



<p>
</p>

This is what it looks like when **all the checks** have passed!  

<p>
</p>

<kbd>
<img src="images/checks_passed.png" border="5" width="70%" height="70%"/>
</kbd>


 

---

## Part I:  Next Steps
- Wait for reviews (be patient)
- Address review comments in the same branch
- Pushing to your fork will update the PR
- Reviewers will "approve" the PR or change title to [MRG + 1]
- You need **2 approvals for a merge**

This is what a **merged** icon looks like:   
<p>
</p>
<kbd>
<img src="images/merged.png" border="5" width="70%" height="70%"/>
</kbd>

---

## References
- [`flake8`](resources.md)
