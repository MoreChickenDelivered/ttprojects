# LINKS NEED REVIEW

# C++ HFT Market Making
C++ already support protobuf, supports market making, target position, has some less used stuff like arbitrage and "LSD".u

Vanilla BGMarketMaker figures out a "fair price" from the current BBO and spreads the allocation amount into 2 sides, one 'above' and one 'below' the fair price (with some 'distance' in terms of price). Each side is split into __levels__ which correspond to single limit orders sitting in the exchange. Each level/order is general of the same quantity because the allocation is split evenly across levels (except when reaping profit the most inner levels get extra amount).
The levels are spaced apart by a even amount. Many of these quantities are determined by both the current market and certain coefficients and/or ratios that were deemed the most profitable by the backtester optimization run.

-  [live execution binary - cytester](https://github.com/MoreChickenDelivered/cytester2) - live strategy deployment

   The live component that, instead of replaying static historical data, gets the market data from a live exchange websocket and sends actual orders. Otherwise comparable to a backtesting run.
-  Backtesting
    -  [backtest binary - cytester](https://github.com/MoreChickenDelivered/cytester2) - used to backtest a C++ strategy given a set of parameter configs.
     
       Given a bunch of input data binaries, containing market data (trades and orderbooks). it replays those datas into a simulation of an exchange, making calculations of PnL as it goes and fees. The strategies is the same code used by the live component.
    -  ["other" cytester](https://github.com/ebenali/cytester-blankrepo) and [strcy](https://github.com/MoreChickenDelivered/strcycopy) - Python libraries used to optimize parameters
-  [HFT Plugin](https://github.com/ebenali/hft-plugin-base) - gets fed data and contains logic to generate orders. Run by live execution and backtest binaries
   
   was split out from the main `cytester` repositories in order to allow for restricted-access to external teams without exposing the inner workings of the backtester/live and how it handles exchange/protobuf I/O and other details.

-  [Docker containers](https://github.com/MoreChickenDelivered/tthft-docker-image) - contains containers for building and research.

   These were made to avoid incompatibilities between different versions of runtimes and libraries and ETL job outputs between collaborators machines and ensure a close resemblance to the deployment environment.

# Python mid-frequency
-  [luigi live execution](https://github.com/MoreChickenDelivered/luigi)
   ## brief explanation
   This a execution bot for interacting with exchanges in a unified manner (from the perspective of the strategy/pysdk).

   This is the precursor to 'cytester' C++ execution.

   Unlike cytester which does it all including the strategy logic and network I/O with the exchange, luigi only worries about network IO (and in a later iteration, does a rahter simple target following control loop called mOMS). It communicates through MQ and uses mySQL for some storage. ---ebenali
-  Backtesting
    -  Traders have their own private backtesting procedures and data sets. 
   - pysdk : the "strategy", current maintainer: yfan 

Used by cytester  
[tthftshared](https://github.com/MoreChickenDelivered/tthftshared) - constants used by cytester and hftbackend  
[walter protobuf](https://github.com/MoreChickenDelivered/walter_protobuf) - converts data from JSON -> protobuf -> BIN  
[liblogger](https://github.com/MoreChickenDelivered/liblogger) - logging and slack utilities 
[hftbackend](https://github.com/MoreChickenDelivered/hftbackend) - clients for various exchanges to subscribe to market data and submit orders 

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
