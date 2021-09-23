# LINKS NEED REVIEW

# C++ HFT Market Making
-  [live execution binary - cytester](https://github.com/MoreChickenDelivered/cytester2) - live strategy deployment
-  Backtesting
    -  [backtest binary - cytester](https://github.com/MoreChickenDelivered/cytester2) - used to backtest a C++ strategy given a set of parameter configs
    -  ["other" cytester](https://github.com/ebenali/cytester-blankrepo) and [strcy](https://github.com/MoreChickenDelivered/strcycopy) - Python libraries used to optimize parameters
-  [HFT Plugin](https://github.com/ebenali/hft-plugin-base) - gets fed data and contains logic to generate orders. Run by live execution and backtest binaries
-  [Docker containers](https://github.com/MoreChickenDelivered/tthft-docker-image) - contains containers for building and research

# Python mid-frequency
-  [luigi live execution](https://github.com/MoreChickenDelivered/luigi)
   This a execution bot for interacting with exchanges in a unified manner (from the perspective of the strategy/pysdk).

   This is the precursor to 'cytester' C++ execution.

   Unlike cytester which does it all including the strategy logic and network I/O with the exchange, luigi only worries about network IO (and in a later iteration, does a rahter simple target following control loop called mOMS). It communicates through MQ and uses mySQL for some storage.

-  Backtesting
    -  [???]()
-  ???

[tthftshared](https://github.com/MoreChickenDelivered/tthftshared) - constants used by cytester and hftbackend
[walter protobuf](https://github.com/MoreChickenDelivered/walter_protobuf) - ???

Yes, there are 2 cytesters that aren't very similar, which can be confusing. And yes, both C++ and Python backtesting involves both C++ and Python/Cython (technically, C++ doesn't "need" Python/Cython, but python is currently used for parameter optimization and as driver code for concurrent multi-phase backtesting and generating PnL plots).

USE THE BRANCH USED IN [cytester CMakeLists](https://github.com/MoreChickenDelivered/cytester2/blob/main/CMakeLists.txt)

See [MISC](https://github.com/MoreChickenDelivered/ttprojects/blob/main/MISC.md) for other repos.

## Making changes
To make changes to a repository maintained by multiple people:
1. create a branch called <firstname>-<bugfix | feature>. For example, if I wanted to create a new feature, I would create a branch called `shile-feature`
2. go to Github and create a pull request between the develop (if it exists) or the main branch and your new branch
3. send it to Shile for a review, then make changes based on feedback

## New projects
If you are working on a new project, please share the project with Shile so he can review the code once per day to check that good style/documentation is maintained
