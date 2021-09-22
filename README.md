# C++ HFT Market Making
-  [live execution binary](https://github.com/MoreChickenDelivered/hftbackend) - live strategy deployment
-  Backtesting
    -  [backtest binary](https://github.com/MoreChickenDelivered/hfttester) - used to backtest a C++ strategy given a set of parameter configs
    -  [cytester library](https://github.com/ebenali/cytester-blankrepo) and [strcy](https://github.com/MoreChickenDelivered/strcycopy) - Python libraries used to optimize parameters
-  [Plugin](https://github.com/ebenali/hft-plugin-base) -  logic to generate orders. Run by live execution and backtest binaries
-  [Docker containers](https://github.com/MoreChickenDelivered/tthft-docker-image) - contains containers for building and research

# Python mid-frequency
-  [luigi live execution](https://github.com/MoreChickenDelivered/luigi) - live strategy deployment
-  Backtesting
    -  [cytester](https://github.com/MoreChickenDelivered/cytester2)
-  ???

[tthftshared](https://github.com/MoreChickenDelivered/tthftshared) - constants used by cytester and hftbackend

Yes, there are 2 cytesters that aren't very similar, which can be confusing. And yes, both C++ and Python backtesting involves both C++ and Python/Cython (technically, C++ doesn't "need" Python/Cython, but Python/Cython is used for optimization).

USE THE `develop` BRANCH UNLESS OTHERWISE SPECIFIED OR IT DOESN'T EXIST

See [MISC](https://github.com/MoreChickenDelivered/ttprojects/blob/main/MISC.md) for other repos.

## Making changes
To make changes to a repository maintained by multiple people:
1. create a branch called <firstname>-<bugfix | feature>. For example, if I wanted to create a new feature, I would create a branch called `shile-feature`
2. go to Github and create a pull request between the develop (if it exists) or the main branch and your new branch
3. send it to Shile for a review, then make changes based on feedback

## New projects
If you are working on a new project, please share the project with Shile so he can review the code once per day to check that good style/documentation is maintained