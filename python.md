# Python

(base) PS C:\Users\chris> conda create -n rankenv python=3.10
Retrieving notices: ...working... done
Channels:
 - defaults
Platform: win-64
Collecting package metadata (repodata.json): done
Solving environment: done

## Package Plan ##

  environment location: C:\Users\chris\.conda\envs\rankenv

  added / updated specs:
    - python=3.10


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    pip-24.0                   |  py310haa95532_0         2.9 MB
    python-3.10.14             |       he1021f5_1        15.9 MB
    setuptools-69.5.1          |  py310haa95532_0        1013 KB
    vc-14.2                    |       h2eaa2aa_4          10 KB
    vs2015_runtime-14.29.30133 |       h43f2093_4         1.1 MB
    wheel-0.43.0               |  py310haa95532_0         136 KB
    ------------------------------------------------------------
                                           Total:        21.1 MB

The following NEW packages will be INSTALLED:

  bzip2              pkgs/main/win-64::bzip2-1.0.8-h2bbff1b_6
  ca-certificates    pkgs/main/win-64::ca-certificates-2024.7.2-haa95532_0
  libffi             pkgs/main/win-64::libffi-3.4.4-hd77b12b_1
  openssl            pkgs/main/win-64::openssl-3.0.14-h827c3e9_0
  pip                pkgs/main/win-64::pip-24.0-py310haa95532_0
  python             pkgs/main/win-64::python-3.10.14-he1021f5_1
  setuptools         pkgs/main/win-64::setuptools-69.5.1-py310haa95532_0
  sqlite             pkgs/main/win-64::sqlite-3.45.3-h2bbff1b_0
  tk                 pkgs/main/win-64::tk-8.6.14-h0416ee5_0
  tzdata             pkgs/main/noarch::tzdata-2024a-h04d1e81_0
  vc                 pkgs/main/win-64::vc-14.2-h2eaa2aa_4
  vs2015_runtime     pkgs/main/win-64::vs2015_runtime-14.29.30133-h43f2093_4
  wheel              pkgs/main/win-64::wheel-0.43.0-py310haa95532_0
  xz                 pkgs/main/win-64::xz-5.4.6-h8cc25b3_1
  zlib               pkgs/main/win-64::zlib-1.2.13-h8cc25b3_1


Proceed ([y]/n)? y


Downloading and Extracting Packages:

Preparing transaction: done
Verifying transaction: done
Executing transaction: done
#
# To activate this environment, use
#
#     $ conda activate rankenv
#
# To deactivate an active environment, use
#
#     $ conda deactivate

(base) PS C:\Users\chris> conda activate rankevn

EnvironmentNameNotFound: Could not find conda environment: rankevn
You can list all discoverable environments with `conda info --envs`.


Invoke-Expression : Cannot bind argument to parameter 'Command' because it is an empty string.
At C:\anaconda3\shell\condabin\Conda.psm1:76 char:36
+         Invoke-Expression -Command $activateCommand;
+                                    ~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidData: (:) [Invoke-Expression], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorEmptyStringNotAllowed,Microsoft.PowerShell.Commands.Invo
   keExpressionCommand

(base) PS C:\Users\chris> conda env list
# conda environments:
#
rankenv                  C:\Users\chris\.conda\envs\rankenv
base                  *  C:\anaconda3

(base) PS C:\Users\chris> conda activate rankenv
(rankenv) PS C:\Users\chris> pip --version
pip 24.0 from C:\Users\chris\.conda\envs\rankenv\lib\site-packages\pip (python 3.10)
(rankenv) PS C:\Users\chris> pip install -q tensorflow-ranking
(rankenv) PS C:\Users\chris> pip show tensorflow-ranking
Name: tensorflow-ranking
Version: 0.5.5
Summary: Pip package setup file for TensorFlow Ranking.
Home-page: https://github.com/tensorflow/ranking
Author: Google Inc.
Author-email: packages@tensorflow.org
License: Apache 2.0
Location: c:\users\chris\.conda\envs\rankenv\lib\site-packages
Requires: absl-py, numpy, six, tensorflow, tensorflow-serving-api
Required-by:
(rankenv) PS C:\Users\chris> pip show tensorflow
Name: tensorflow
Version: 2.15.1
Summary: TensorFlow is an open source machine learning framework for everyone.
Home-page: https://www.tensorflow.org/
Author: Google Inc.
Author-email: packages@tensorflow.org
License: Apache 2.0
Location: c:\users\chris\.conda\envs\rankenv\lib\site-packages
Requires: tensorflow-intel
Required-by: tensorflow-ranking, tensorflow-serving-api
(rankenv) PS C:\Users\chris>
