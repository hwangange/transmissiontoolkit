# Transmission Toolkit


## Table Of Contents
* [Introduction](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#introduction)
* [Requirements](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#requirements)
* [Tools](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#tools)
  * [VCF Parsing](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#vcf-parsing)
  * [Phylogenetic Tree Generation](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#phylogenetic-tree-generation)
  * [Phylogenetic Tree Visualization](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#phylogenetic-tree-visualization)
  * [Figure Creation](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#figure-creation)
  * [Bottleneck Estimate](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#bottleneck-estimate)
* [Installation](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#installation)
* [How to Use](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#how-to-use)
* [Contributors](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#contributors)
* [References](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#references)

## Introduction
Transmission Toolkit is a python-based program that provides many different tools for transmission analysis all in one place. The Transmission Toolkit has many functionalities including [parsing](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#vcf-parsing), [phylogenetic tree creation](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#phylogenetic-trees), [figure creation](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#figure-creation), and [bottleneck estimation](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#bottleneck-estimate).

The Transmission Toolkit parses through vcfs in a number of ways, including finding donor-recipient relations, getting all variants of a vcf, finding low and high frequency variants, and more. The parsing functionality has a variety of parameters users can alter to suit the vcf parsing to their needs.

The Transmission Toolkit can also create 5 unique figures to make data analysis even easier. These figures range from pair comparisons to analysis of all possible pairs in a data set. There are many parameters within the figure creation that allow users to customize these figures.

The Transmission Toolkit also can generate phylogenetic trees and corresponding heatmaps. The toolkit uses RAxML to generate the trees, and uses Toytree and Toyplot to transform the basic trees into a very visually appealing and useful figure for your analysis.

Finally, the Transmission Toolkit offers use of the [BB_bottleneck](https://github.com/weissmanlab/BB_bottleneck) software. The toolkit creates input files for the software and can run the software to generate a bottlneck size estimation of any pair from your data.

All of these functionalities are packaged together in one place, including a Jupyter Notebook showcasing the functions of the toolkit on a sample set of data-all you have to do is click run!

To use your own data, go to the empty_template folder, open the data template jupyter notebook, and follow the instructions.

## Features
### VCF Parsing
The Transmission Toolkit parses input VCF files as neccessary, to analyze data between pairs, to create phylogenetic trees, to create bottleneck estimation input, and more. This is all done automatically when you chose a function to perform. There are many parameters that users can alter to their liking to get the best parse of the data.
#### Parameters
- min_freq: minimum frequency all variants must hold, useful for filtering potential errors
- min_read_depth: minimum number of reads required to support a variant, useful for filtering potential errors
- max_AF: maximum frequency to include in parse, useful for extracting low frequency variants
- masks: a txt file with a list of erroneous positions you wish to mask
- parse_type: either 'biallelic' or 'multiallelic', handles the case of when there are multiple variants at the same position
- store_reference: a boolean that determines if the reference allele is treated as a variant in certain cases
#### Examples
### Phylogenetic Trees
The Transmission Toolkit uses RAxML to generate the most likely phylogenetic tree out of the inputted data, as well as Toyplot and Toytree to visualize the phylogenetic trees created by RAxML. Some parameters users can input to customize the tree visualization include focusing on small clusters, looking at low frequency variants to determine likely transmission pairs, and more.
#### Examples
##### Phylogenetic Tree
![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/phylotree.jpg)
Parameters:
color_groups: method that allows users to color the tree nodes of an identical sequence
##### Phylogenetic Tree and Heatmap 
![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/aligned.jpg)
Parameters: 
- add_heatmap: method that allows users to add a heatmap to the tree
- height & width: parameters that allow user to control the size of the heatmap
- position range: allows users to choose which positions to include on the heatmap
### Figure Creation
The Transmission Toolkit uses matplotlib to create a multitude of figures analyzing the data, including analyzing low frequency shared variant between possible transmission pairs, showing the number of pairs that share a certain variant, illustrating bottleneck sizes of possible transmission pairs, and more. All figures have the parsing parameters available as well, to control how the data is formed before it is displayed in a figure.
#### Examples
##### Standard Bar Plot
This figure shows the frequency of variants in a pair in a donor-recipient manner.
![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/standardbarplot.jpg)
Parameters:
- output_folder: chooses where figures get outputted
- plot_type: parameter for standard bar plot, determines if thickness of bars is weighted by number of reads or if it is left standard
##### Weighted Bar Plot
This figure shows the frequency of variants in a pair in a donor-recipient manner, with weighted bars representing the amount of reads supporting each variant.
![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/weightedbarplot.jpg)
Parameters
- output_folder: chooses where figures get outputted
- plot_type: parameter for standard bar plot, determines if thickness of bars is weighted by number of reads or if it is left standard
##### Number of Shared Variants Figure
This figure shows the number of shared variants each pair has, both masked and complete.
![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/numvariants.jpg)
Parameters:
- output_folder: chooses where figures get outputted
- high_shared: a parameter that allows users to select a threshold for which pairs with shared variants above that threshold will be printed along with the figure for easy analysis
##### Variants at Position Figure
This figure shows the number of pairs with shared variants at 
![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/positions.jpg)
Parameters:

- output_folder: chooses where figures get outputted
- shown_variants: chooses the number of positions to be displayed
### Bottleneck Estimate
The Transmission Toolkit uses the BB_bottleneck software to generate bottleneck size estimates of possible transmission pairs. This data can be used by itself to learn more about a potential transmission pair, and it is also included in the figures for easy analysis.
#### Parameters
- filename: a txt created by bb_file_writer
- var_calling_threshold: 
- nb_min:
- nb_max:
- confidence_level:
#### Examples
##### Bottleneck Size Input File
This is a bottleneck input file generated by the transmission toolkit for use in the bb_bottleneck software.
![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/bottleneckfile.jpg)
##### Bottleneck Size Estimation
This is the sample output of a bb_bottleneck software run.
![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/bottleneck.jpg)
## How to Use
There are 3 ways to access transmission toolkit on your device.

### mybinder.org Link
To access TransmissionToolkit via mybinder.org, simply click this [link](https://mybinder.org/v2/gh/marybrady722/transmissiontoolkit/master). Alternatively, you can copy and paste this url into the browsaer of your choice.

https://mybinder.org/v2/gh/marybrady722/transmissiontoolkit/master

Once you reach the link, you should see a loading page that looks like this:

![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/binder4.jpg)

Now, just wait until the binder loads. That screen should change to one that looks like this after the binder has loaded:

![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/binder1.jpg)

Click on the folder called sample_data. That should bring you to a page that looks like this:

![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/binder2.jpg)

From there, click on Sample Data.ipynb. You should reach a page that looks like this:

![image](https://github.com/marybrady722/transmissiontoolkit/blob/master/images/binder3.jpg)

Now that you're in the notebook, click the run button for each code block to run through and generate tha sample data!

### Docker Image
To access TransmissionToolkit via Docker, follow the instructions below.

First, [install Docker](https://docs.docker.com/get-docker/) on your computer. 

Once Docker is installed on your machine, run the following commands on your computer:

     docker pull marybrady722/transmission_project
     docker run -p 8888:8888 marybrady722/transmission_project
     
After running these two commands in the terminal, follow the instructions to access the Juptyer Notebook. You should reach a screen like this:
![image](change)
Click on Sample Mason Data.ipynb to view the sample data. To use your own data, upload a folder of vcfs into the main folder, change the inputs in the notebook, and run!

### GitHub Download
To use TransmissionToolkit by downloading the source code and dependencies yourself on your machine, follow the instructions below.

First, ensure you have downloaded all of the [required packages and libraries.](https://github.com/marybrady722/transmissiontoolkit/blob/master/README.md#Requirements-(for-GitHub-download-&-use))

Once you have all of the requirements, download all of the code from this repo. 

To access the Jupyter Notebook with the data demo, first ensure you have [Jupyter](https://jupyter.org/install) installed on your machine. Then navigate to the sample_data folder within the terminal. Once in the sample_data folder, run the following command:

    jupyter notebook

You should reach a screen like this:

From here, click on Sample Data.ipynb, and run the code blocks to generate the sample data!

To add your own data, create a new folder of vcfs within the sample_data folder, change the input folder in the Sample Data.ipynb, and run.

## Requirements (for GitHub download & use)
In order to successfully run the Transmission Toolkit on your device, you will need Python version 3.8.3 and the following Python libraries:
- [NumPy](https://numpy.org/install/)
- [PyVCF](https://pypi.org/project/PyVCF/)
- [matplotlib](https://matplotlib.org/users/installing.html)
- [Toytree](https://toytree.readthedocs.io/en/latest/3-installation.html)
- [Toyplot](https://toyplot.readthedocs.io/en/stable/installation.html)
- [BioPython Version 1.77](https://biopython.org/wiki/Download) Verison 1.77 MUST be used for TransmissionToolkit to work. Make sure to scroll down to old releases and select version 1.77.

To use the bottleneck calculation function, you will need the [BB_bottleneck](https://github.com/weissmanlab/BB_bottleneck) and its dependencies.

To use the phylogenetic tree generation and visualization features, you will need [RAxML](https://github.com/stamatak/standard-RAxML).


## Contributers
Leo Elworth

Qi "Maria" Wang

Nick Sapoval

Mary Brady

Kaiyu Hernandez
## References

Leonard, Ashley Sobel, et al. "Transmission bottleneck size estimation from pathogen deep-sequencing data, with an application to human influenza A virus." Journal of virology 91.14 (2017).


