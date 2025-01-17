Copyright (c) Facebook, Inc. and its affiliates.

This source code is licensed under the MIT license found in the
LICENSE file in the root directory of this source tree.

# Robyn MMM Open Source 2.0 - a Beta Project from Facebook Marketing Science

2021-03-03 [Deprecated]

## Quick start

**1. Getting .R scripts**
  * There are three .R script files:
    - fb_robyn.exec.R # you only need this script to execute, it calls the
      other 2 scripts
    - fb_robyn.func.R # this contains feature engineering, modelling functions and plotting
    - fb_robyn.optm.R # this contains the budget allocator and plotting
  * Two .csv files as sample data:
    - de_simulated_data.csv # this is our simulated data set. 
    - generated_holidays.csv # this contains holidays of all countries from the library prophet. Please check if your country is included and if all holidays are included. It's also recommended to add extra events into this table, for example school holidays.
  * All files must be placed in the same folder

**2. R version and libraries**
  * It's highly recommended to update to R version 4.0.3 to avoid potential errors
  * Please make sure you've installed all library specified in fb_robyn.exec.R first
  * Please also install Anaconda for reticulate. Simple instruction please check fb_robyn.exec.R in the library section
  * For Windows, if you get openssl error, please see instructions [here](https://stackoverflow.com/questions/54558389/how-to-solve-this-error-while-installing-python-packages-in-rstudio/54566647) and [here](https://dev.to/danilovieira/installing-openssl-on-windows-and-adding-to-path-3mbf) to install and update openssl

**3. Test run with sample data**
  * Please follow all instructions in fb_robyn.exec.R
  * After above steps, if you select all and run in fb_robyn.exec.R, the script should execute 20k iterations (500 iterations * 40 trials) and save some plots on your selected folder
  * An example model onepager looks like this:
![result](https://user-images.githubusercontent.com/14415136/116684824-c12a1c00-a9b1-11eb-84d5-b28680796999.png)

  * The final function f.budgetAllocator() might throw error "provided ModID is not within the best result". First of all, please read all instructions behind the function. Model IDs are encoded in each onepager .png name and also in the title. Also, execute model_output_collect$allSolutions will output all final model IDs. Please pick one and put it into f.budgetAllocator(). 
  * An example optimised model looks like this:
![result_optimised](https://user-images.githubusercontent.com/14415136/110111552-ceab9700-7db0-11eb-84b5-9f105c49b09b.png)


## Step-by-step Guide Website

* Guidelines on the website: https://facebookexperimental.github.io/Robyn/docs/step-by-step-guide

## Model selection with evolutionary algorithm

Using Facebook AI's open source gradient-free optimisation library [Nevergrad](https://facebookresearch.github.io/nevergrad/), Robyn is able to leverage evolutionary algorithms to perform multi-objective hyperparameter optimisation and output a set of Pareto-optimal solutions. Besides NRMSE as loss function for the optimisation, Robyn also minimises on a business logic "decomposition distance", or DECOMP.RSSD that is aiming to steer the model towards more realistic decomposition results. In case of calibration, a third loss function MAPE.LIFT is added too.

The following plot demonstrates typical Pareto fronts 1-3 on NRMSE and DECOMP.RSSD:
![paretofront](https://user-images.githubusercontent.com/14415136/110000483-a3269f00-7d13-11eb-85de-0bae918f4f5c.png)


## Join the FB Robyn MMM community
[Robyn MMM users Facebook Group](https://www.facebook.com/groups/954715125296621)

## Case studies
* [Case study: Resident](https://www.facebook.com/business/success/resident)
* [Case study: Central Group](https://www.facebook.com/business/success/central-retail-corporation)


## FB Contact

* gufeng@fb.com, Gufeng Zhou, Marketing Science Partner
* leonelsentana@fb.com, Leonel Sentana, Marketing Science Partner
* aprada@fb.com, Antonio Prada, Marketing Science Partner
* igorskokan@fb.com, Igor Skokan, Marketing Science Partner

See the [CONTRIBUTING](CONTRIBUTING.md) file for how to help out.

## License

FB Robyn MMM R script is MIT licensed, as found in the LICENSE file.

- Terms of Use - https://opensource.facebook.com/legal/terms 
- Privacy Policy - https://opensource.facebook.com/legal/privacy
