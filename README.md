# engrXiv-print-count

This is a pair of documents used to calculate the statistics behind documents posted on Engineering Archive. The data is collected using the PHP script (modified from [here](https://bitbucket.org/octogroup/osf-preprint-list)). The jupyter notebook here is used on: https://blog.engrxiv.org/stats/

## To use the PHP script
Use the OSF's API (https://developer.osf.io/) to gather a list of papers in engrXiv so we can gather stats.

You will need an Authorization Token (https://developer.osf.io/#tag/Authentication) to make requests.

We use the PHP Curl Class library to handle our GET requests: https://github.com/php-curl-class/php-curl-class

You can pass the token to the script by appending `-p$osf_token` to the end of your php command, where `$osf_token` is your OSF authorization token.


## The Jupyter Notebook
The Jupyter notebook is just a small bit of Python to plot the results that are stored in the CSV file generated by the PHP script. The current data file used in the notebook is hosted here: https://osf.io/ns9yr/

[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/OpenEngr/engrXiv-print-count/blob/master/engrXiv_prints.ipynb)

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/OpenEngr/engrXiv-print-count/master?filepath=engrXiv_prints.ipynb)

## Download all engrXiv files
The bash script `download_engrxiv.sh` uses the `engrxiv-papers.csv` file which is created using the PHP script, there is an occasionally updated version [available on OSF](https://osf.io/ns9yr/). The CSV file is read using `csvtool` and then the primary file for each preprint is downloaded using `wget`. Each file is saved as *GUID.pdf*.
