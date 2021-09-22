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
    -  [cytester](https://github.com/MoreChickenDelivered/cytester)
-  ???

TODO: put where libttshared/libshared goes.

Yes, there are 2 cytesters that aren't very similar, which can be confusing. And yes, both C++ and Python backtesting involves both C++ and Python/Cython.



