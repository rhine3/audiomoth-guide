# Software for analysis of acoustic recordings

A variety of free and paid acoustic analysis software is available. Software packages vary from complete graphical interfaces, to command-line interfaces, to utility libraries that can be used to create analysis pipelines in Python, R, or other programming languages. 

This list is not necessarily a recommendation or a guarantee of quality of the software or analysis techniques. I have not used all of the software below. Some I use frequently, whereas some I haven't found to be useful or accurate for my purposes. You should always judge the performance of an analysis technique based on *your* dataset, as different recording conditions or species distributions can result in starkly different performance.

* **Manual review**: listening to recordings or looking at spectrograms
    * [Audacity](https://www.audacityteam.org/) (free) - simple, lightweight listening and spectrogram viewing and comparison
    * [AviaNZ](http://www.avianz.net/index.php) (free)
    * [Raven Lite](https://ravensoundsoftware.com/software/raven-lite/) (free) - listening and spectrogram viewing; tools to manually select and annotate recordings
    * [WarbleR](https://marce10.github.io/warbleR/) (free) - multipurpose R package
    * [GlassOFire](http://www.oldbird.org/glassofire.htm) (free) - Windows software for nocturnal flight call review and sorting
* **Detection**: locating potential sounds of interest in recordings
    * [AviaNZ](http://www.avianz.net/index.php) (free)
    * [BirdVoxDetect](https://github.com/BirdVox/birdvoxdetect) (free) - machine learning-based detection for nocturnal flight calls
    * [Kaleidescope](https://www.wildlifeacoustics.com/products/kaleidoscope-pro) (paid)
    * [Raven Pro](https://ravensoundsoftware.com/software/raven-pro) (paid) - configurable amplitude triggering-based detection
    * [WarbleR](https://marce10.github.io/warbleR/) (free)
* **Clustering**: grouping sounds into similar-sounding "clusters", which can then be manually annotated
    * [AviaNZ](http://www.avianz.net/index.php) (free)
    * [Kaleidescope](https://www.wildlifeacoustics.com/products/kaleidoscope-pro) (paid)
* **Machine learning-based classification**: using a trained machine learning algorithm to predict the identity of sounds captured in recordings, e.g. identifying bird species in a recording
    * [ARBIMON](https://arbimon.sieve-analytics.com/) - web-based interface for creating own classifiers
    * [BirdNET](https://github.com/kahst/BirdNET) (free) - pre-created classifiers for birds of North America and Europe
    * [BirdVoxClassify](https://github.com/BirdVox/birdvoxclassify) (free) - pre-created nocturnal flight call classifiers for North American species
    * [Kaleidescope](https://www.wildlifeacoustics.com/products/kaleidoscope-pro) (paid) - pre-created bat classification
    * [OpenSoundscape](https://github.com/ktizeslab/opensoundscape) (free, in development) - create own classifiers
* **Measuring acoustic parameters**: soundscape metrics
    * [soundecology](https://cran.r-project.org/web/packages/soundecology/vignettes/intro.html) (free) - calculate soundscape-wide acoustic indices
    * [warbleR](https://marce10.github.io/warbleR/) (free) - measure acoustic signal structure
