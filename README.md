<!-- README.md is generated from README.Rmd. Please edit that file -->



gutenbergr: R package to search and download public domain texts from Project Gutenberg
----------------

**Authors:** [David Robinson](http://varianceexplained.org/)<br/>
**License:** [MIT](https://opensource.org/licenses/MIT)

[![Build Status](https://travis-ci.org/dgrtwo/gutenbergr.svg?branch=master)](https://travis-ci.org/dgrtwo/gutenbergr)

Download and process public domain works from the [Project Gutenberg](https://www.gutenberg.org/) collection. Includes

* A function `gutenberg_download()` that downloads one or more works from Project Gutenberg by ID: e.g., `gutenberg_download(84)` downloads the text of Frankenstein.
* Metadata for all Project Gutenberg works as R datasets, so that they can be searched and filtered:
  * `gutenberg_metadata` contains information about each work, pairing Gutenberg ID with title, author, language, etc
  * `gutenberg_authors` contains information about each author, such as aliases and birth/death year
  * `gutenberg_subjects` contains pairings of works with Library of Congress subjects and topics

### Installation

Install using [devtools](https://github.com/hadley/devtools) with:


```r
devtools::install_github("dgrtwo/gutenbergr")
```

### FAQ

#### What do I do with the text once I have it?

We recommend the [tidytext](https://github.com/juliasilge/tidytext) package for tokenization and analysis!

#### How were the metadata R files generated?

See the [data-raw](data-raw) directory for the scripts that generate these datasets. As of now, these were generated from [the Project Gutenberg catalog](https://www.gutenberg.org/wiki/Gutenberg:Feeds#The_Complete_Project_Gutenberg_Catalog) on **April 27 2016**.

There are no guarantees about how often the metadata will be updated in the package. If you're interested in works that have just been added or heavily edited on Project Gutenberg, you may want to run the scripts yourself.

#### Do you respect the rules regarding robot access to Project Gutenberg?

Yes! The package respects [these rules](https://www.gutenberg.org/wiki/Gutenberg:Information_About_Robot_Access_to_our_Pages) and complies to the best of our ability. Namely:

* Project Gutenberg allows wget to harvest Project Gutenberg using [this list of links](http://www.gutenberg.org/robot/harvest?filetypes[]=html). The gutenbergr package visits that page once to find the recommended mirror for the user's location.
* We retrieve the book text directly from that mirror using links in the same format. For example, Frankenstein (book 84) is retrieved from `http://www.gutenberg.lib.md.us/8/84/84.zip`.
* We retrieve the .zip file rather than txt to minimize bandwidth on the mirror.

Still, this package is *not* the right way to download the entire Gutenberg corpus (or all from a particular language). For that, follow [their recommendation](https://www.gutenberg.org/wiki/Gutenberg:Information_About_Robot_Access_to_our_Pages) to use wget or set up a mirror. This package is recommended for downloading a single work, or works for a particular author or topic for analysis.