# glmnet_matlab_R2020

<img src="/glmnet_logo.jpg" alt="Glmnet Logo" width="400">

[Glmnet](https://web.stanford.edu/~hastie/glmnet_matlab/) compiled for MATLAB R2020b, Windows 10 64-bit.

**Update**: Glmnet compiled for R2020b seems to work fine on **R2021a**.

N.B. Check Releases and Branches for different MATLAB versions (e.g. R2020a).

I also fixed `cvglmnet.m`, updating the old functions for parallel computing (from `matlabpool` to `parpool`).

The code from this repository is plug-and-play: just download the folder, add it to your MATLAB path and run your GLM!

## Background
[Glmnet](https://web.stanford.edu/~hastie/glmnet_matlab/) is an extremely efficient package for fitting the entire lasso or elastic-net path for linear regression, logistic and multinomial regression, Poisson regression and the Cox model.
It is way faster than MATLAB `lassoglm` that comes with the Statistics and Machine Learning Toolbox.

Glmnet provided by the authors are not compatible with newer versions of MATLAB (>R2016, I read somewhere). Indeed, my Matlab 2020a on Windows 10 was going into fatal crash when running the original code. Also the code provided by [growlix](https://github.com/growlix/glmnet_matlab) did not work on my system.
So I compiled again the Fortran code which glmnet is based on (and makes it so fast). Glmnet does work fine now on my system (MATLAB R2020a, Windows 10 64-bit).

## Implementation
I installed:
- [Visual Studio Community 2019](https://visualstudio.microsoft.com/)
- [Intel Parallel Studio XE](https://software.intel.com/content/www/us/en/develop/tools/parallel-studio-xe/choose-download.html) (30-day trial version; in particular, install the FORTRAN compiler) 
- [MATLAB Support for MinGW-w64 C/C++ Compiler](https://www.mathworks.com/matlabcentral/fileexchange/52848-matlab-support-for-mingw-w64-c-c-compiler)

Then, in MATLAB, I moved into the glmnet folder and ran
```
mex -v COMPFLAGS='$COMPFLAGS /real_size:64 /integer_size:64' glmnetMex.F GLMnet.f
```

Please cite the authors if you use Glmnet:

```
Glmnet for Matlab (2013) Qian, J., Hastie, T., Friedman, J., Tibshirani, R. and Simon, N.
http://www.stanford.edu/~hastie/glmnet_matlab/
```

## Sources
- Glmnet https://web.stanford.edu/~hastie/glmnet_matlab/index.html
- https://web.stanford.edu/~hastie/glmnet_matlab/win64compile.html
- Thanks to [growlix](https://github.com/growlix/glmnet_matlab) for sharing his guidelines!
