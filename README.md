![GitHub](https://img.shields.io/github/license/nassernajibi/WGEN-v2.0)
![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/nassernajibi/WGEN-v2.0)
![GitHub repo size](https://img.shields.io/github/repo-size/nassernajibi/WGEN-v2.0)
![GitHub language count](https://img.shields.io/github/languages/count/nassernajibi/WGEN-v2.0)
![GitHub last commit](https://img.shields.io/github/last-commit/nassernajibi/WGEN-v2.0)
# Stochastic Weather Generator v2.0
## User Manual (Documentation Guide) ##

[**For the Public**](#Public)
| [**For Researchers**](#Researchers)
| [**Repository Organization**](#Repository)
| [**To Browse the Codes**](#Codes)
| [**To Run SWG**](#SWG)
| [**How to Cite**](#Citing)
| [**Issues and Comments**](#Issues)
| [**License**](#License)


The WGEN (or SWG) was first developed by [Prof. Scott Steinschneider](https://github.com/SteinschneiderLab) (Cornell University) (see *Steinschneider et al., 2019*). 
Since then, it has been upgraded, applied to different locations, and used for varying purposes by [the Steinschneider Research Group]( https://blogs.cornell.edu/steinschneider/) and their collaborators.

The SWG is designed to be a flexible tool that can facilitate computationally fast, internally consistent scenario generation to support climate vulnerability assessments of water systems in a way that is more easily connected to advances in climate science. 
It is well suited for risk-based simulation studies of system-of-systems that span large regions and multiple sectors (e.g., food, energy, and water).
The tool is useful in expediting the adoption of bottom-up vulnerability assessments across water, food, and energy sectors, by providing a regional set of scenarios that can be tailored for individual locations and analyses.

WGEN-v2.0 scripts were developed in the R Foundation for Statistical Computing Platform Desktop System Type x64-based PC with Intel(R) Core(TM) i7-9700 CPU 3.00 GHz 8 Cores 8 Logical Processors 64.0 GB RAM (64-bit) R version 4.3.1 (RStudio 2023-06-16 ucrt).

A permanent and archived version of this repository is available on Zenodo [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7311768.svg)](https://doi.org/10.5281/zenodo.7311768) (all versions DOI).

### Contents
* [**For the Public**](#Public)
* [**For Researchers**](#Researchers)
* [**Repository Organization**](#Repository)
* [**To Browse the Codes**](#Codes)
* [**To Run SWG**](#SWG)
* [**How to Cite**](#Citing)
* [**Issues and Comments**](#Issues)
* [**License**](#License)
  
### Public

This weather regime-based stochastic weather generator (WR-SWG) is a tool to simulate possible future weather conditions by capturing the statistical patterns and variability observed in historical weather data. This method groups similar weather patterns, known as regimes, which represent distinct atmospheric conditions. By analyzing these regimes, the generator creates synthetic weather sequences that mimic the variability and statistics of real-world weather. This technology is essential for public applications such as risk assessment, scenario development, infrastructure design, and assessing system vulnerability. It enables decision-makers to explore a range of potential weather outcomes, aiding in designing structures that can withstand various conditions, assessing the risks associated with extreme weather events, and developing strategies to enhance the resilience of communities and systems in the face of changing climate patterns.


### Researchers

We are committed to making our work findable, accessible, interoperable and reusable ([FAIR principles](https://www.nature.com/articles/sdata201618)) by the scientific community and the society at large.
The programming language/platform (i.e., [R](https://www.r-project.org/)) and data used here are publicly available via the public preservation repositories without any charges.
All code is posted on this repository.

The following sections outline the steps you can take to run the WGEN.

### Repository

- `README.md` is what you are looking at now.
- `R_sessionInfo.txt` contains a list of necessary packages in `R`. 
- `LICENSE` describes the terms of the MIT LICENSE under which our code is licensed. This is a "free, copyleft license for software and other kinds of works, that guarantees end users the four freedoms to run, study, share, and modify the software".
- `docs/` contains the articles (PDF format) published in peer-reviewed journals.
- `ClimateChangeScenarios.csv` contains the user inputs as a list of options to impose thermodynamic climate change scenarios, including changes in temperature (degree C), changes in precipitation mean (%), and changes for precipitation extremes quantile (i.e., Clausius–Clapeyron scaling) (%). It should be located in the base folder.
- `SimulationLength.csv` contains the user inputs for number of years of simulation per ensemble member and number of ensemble members. It should be located in the base folder.
- `Programs/` contains the scripts required to run the WGEN, from processing the meteorology raw data (`Programs/process.meteorology.R`), to inserting the simulation parameters and determining the stochastic settings (`Programs/config.simulations.R`), to running the stochastic weather generator, plotting the diagnostics, providing the output files (`Programs/run.stochastic.weather.generator.R`). This folder also contains the WeatherGenerator notebook (`Programs/WeatherGenerator.rmd`), which combines all 3 .R files into separate code chunks within 1 notebook. This notebook was designed to consolidate the 3 programs into 1 user-friendly notebook. The user can run this notebook chunk by chunk in order to complete the weather generator simulation.
- `Data/` contains a link to a permanent repository to download sample data/format to run the WGEN. The raw inputs are stored in `Data/raw.data.files` and `Data/processed.data.files/`. For the large-scale atmospheric circulations in `Data/processed.data.files/processed.hgt` and `Data/processed.data.files/processed.NHMM.data` and observational weather records `Data/processed.data.files/processed.meteorology`. The final output files are located in `Data/simulated.data.files/WGEN.out` (.RDATA) and `Data/simulated.data.files/output.data.files` (.csv).
- `Figures/` contains a list of diagnostics and statistics to examine the performance of WGEN outputs. _If you want to use these figures, you are responsible for complying with the policies of the journals our papers have been published, or going to be published, but we mainly ask that you cite our papers when you do so._

### Codes

> This section provide instructions on how to browse the code.

You will find R scripts/functions in `Programs/`.
You can open them and they will render in GitHub.
This will show you how we developed different modules of the WGEN, and produced the output files in `Data/`, along with some additional commentary.

If you want to dig deeper, but not run our codes, then you may want to look at the R functions in `Programs/functions/` and/or the modules as `Programs/config.simulations.R` and `Programs/run.stochastic.weather.generator.R`.


### SWG

> This section provides instructions on how to reproduce or modify results.

Please note: **running this will require ~ 1 GB of disk space, depending on the length of the input/output data**.
*All commands here assume standard Windows terminal; UNIX may be subtly different*.

First, you will need to install `R`, `Rstudio`, and `RTools`.

Next, you will need to `git clone` the repository to your machine, or download the repository as a .zip file and extract its contents to your desired location.


In order to run, you will need to follow the steps below:

1. Once you have installed `R`, `Rstudio`, and `RTools` and have dowloaded or cloned the repository, you can open the R Markdown notebook titled `WeatherGenerator.rmd`. Run the first code chunk to instal all the dependencies listed in `R_sessionInfo.txt`. This code chunk only needs to be run one time, on the first simulation.

2. Then, place your input files into the repository as indicated by the Repository section of this README. If you are planning to use the inputs provided from `wgen_input_example.zip` in [wgen_input_data](https://github.com/cadillac-desert/wgen_input_data), you must paste the contents from this zip file into the base folder of this repository and allow the current `Data/` folder to be replaced by what is in the zip file.

3. Next, run the second code chunk of `WeatherGenerator.rmd`, this second code chunk represents `process.meteorology.R` which prepares input meteorology raw data required to be sent to the weather generator.

4. Verify that `SimulationLength.csv` and `ClimateChangeScenarios.csv` contain the desired values, if they do not, modify the values in the .csv files, and save. Then run the third code chunk of `WeatherGenerator.rmd`. This chunk represents `config.simulations.R`. If required, modify the code to provide all the stochastic inputs and hyperparameters (e.g., directories, dates, regimes simulation mode, and so on).

5. **Now you can run the last code chunk of `WeatherGenerator.rmd` , which represents `run.stochastic.weather.generator.R`** 
  Note - The required dependencies listed at the begining of this code should be installed from running the first code chunk.

We again remind you that running will need a considerable disk space as it depends on the spatiotemporal dimensions of the input files and the length of outputs, e.g., *how many years of weather data to generate?*

#### To plot different weather diagnostics

You can run the diagnostic function `create.figures.baselines.stacked` given towards the end of last code chunk in `WeatherGenerator.rmd` to assess the performance of the WGEN through a set of selected statistics for precipitation and temperature (e.g., floods, droughts, monthly/yearly distributions, inter-annual variability, long-term dry/wet spells, heat/cold waves, and so on).

#### To save simulated weather in delimited format

Finally, you can run the `create.delimited.outputs` function in the last code chunk in `WeatherGenerator.rmd` to save outputs (simulation files) for individual gridded locations in .csv format.

### Citing

If you use the WGEN scripts (as a whole, or partially, and/or as a template for your research work), 
or its results/methods, please cite the references below.

1. Najibi, N., Steinschneider, S. (2023). Stochastic Weather Generator v2.0. *[Zenodo](https://doi.org/10.5281/zenodo.7311768)*, Software, MIT License, Creative Commons Attribution 3.0 United States.

```bibtex
@software{SWGEN_v2.0_2023,
  author = {Najibi, Nasser and Steinschneider, Scott},
  title = {Stochastic Weather Generator v2.0},
  url = {https://doi.org/10.5281/zenodo.7311768},
  version = {2.0},
  date = {2023-08-22},
}
```

2. Steinschneider, S., Ray, P., Rahat, S. H., & Kucharski, J. (2019). A weather‐regime‐based stochastic weather generator for climate vulnerability assessments of water systems in the western United States. *[Water Resources Research](https://doi.org/10.1029/2018WR024446)*, 55(8), 6923-6945.

```bibtex
@article{steinschneider2019weather,
  title={A weather-regime-based stochastic weather generator for climate vulnerability assessments of water systems in the western United States},
  author={Steinschneider, Scott and Ray, Patrick and Rahat, Saiful Haque and Kucharski, John},
  journal={Water Resources Research},
  volume={55},
  number={8},
  pages={6923--6945},
  year={2019},
  publisher={Wiley Online Library}
}
```

3. Najibi, N., Mukhopadhyay, S., & Steinschneider, S. (2021). Identifying weather regimes for regional‐scale stochastic weather generators. *[International Journal of Climatology](https://doi.org/10.1002/joc.6969)*, 41(4), 2456-2479.
```bibtex
@article{najibi2021identifying,
  title={Identifying weather regimes for regional-scale stochastic weather generators},
  author={Najibi, Nasser and Mukhopadhyay, Sudarshana and Steinschneider, Scott},
  journal={International Journal of Climatology},
  volume={41},
  number={4},
  pages={2456--2479},
  year={2021},
  publisher={Wiley Online Library}
}
```

### Issues

- If you have issues related to the software/packages, please raise an issue in the Issues tab.

### License
This project is licensed under the MIT License - see the [LICENSE.md](https://github.com/nassernajibi/WGEN-v2.0/blob/83e90d81cd08d2aa18e998d7ad42c8c437308f9a/LICENSE) file for details.

**Disclaimer:**
The scripts/functions are provided AS IS without warranty of any kind. Author(s) disclaim all implied warranties, including, without limitation, any implied warranties of merchantability or of fitness for a particular purpose. 
In no event shall the author(s) be held liable for any damages whatsoever (including, without limitation, any sort of damages or loss) arising out of the use of or inability to use the scripts or documentation.
Author(s) retain the right to alter this disclaimer at any time.
The contents contained in this repository or within the articles are not the opinions of the funding agencies, affiliated university, or the U.S. Government but reflect the authors' opinions.

![Screenshot](https://brand.cornell.edu/assets/images/examples/trademarks/brand_registered.svg)
