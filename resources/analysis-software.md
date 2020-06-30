# Bioacoustics software

A variety of free and paid software is available for bioacoustic analyses. Software packages vary from complete graphical interfaces, to command-line interfaces, to utility libraries that can be used to create analysis pipelines in Python, R, or other programming languages. 

This list is not necessarily a recommendation or a guarantee of quality of the software or analysis techniques. I have not used all of the software below. Some I use frequently, whereas some I haven't found to be useful or accurate for my purposes. 

You should always judge the performance of an analysis technique based on *your* dataset, as different recording conditions or species distributions can result in starkly different performance of analysis techniques.

* **Manual review and organization**: organizing, listening to, or looking at spectrograms of recordings
    * [Audacity](https://www.audacityteam.org/) (free) - simple, lightweight listening and spectrogram viewing and comparison
    * [AviaNZ](http://www.avianz.net/index.php) (free) - graphical user interface for organizing and analyzing recordings
    * [Raven Lite](https://ravensoundsoftware.com/software/raven-lite/) (free) - listening and spectrogram viewing; tools to manually select and annotate recordings
    * [WarbleR](https://marce10.github.io/warbleR/) (free) - multipurpose R package
    * [GlassOFire](http://www.oldbird.org/glassofire.htm) (free) - Windows software for avian nocturnal flight call review and sorting
    * [Vesper](https://github.com/HaroldMills/Vesper) (free) - web-based application for avian nocturnal flight call analysis; also implements BirdVoxDetect, BirdVoxClassify, and others (see below)
* **Detection**: locating potential sounds of interest in recordings. Methods include supervised machine learning, amplitude-based detection, and clustering to group sounds into similar-sounding clusters (e.g. unsupervised machine learning)
    * [AviaNZ](http://www.avianz.net/index.php) (free) - capable of clustering
    * [BirdVoxDetect](https://github.com/BirdVox/birdvoxdetect) (free) - machine learning-based detection for nocturnal flight calls
    * [Kaleidescope](https://www.wildlifeacoustics.com/products/kaleidoscope-pro) (paid) - capable of clustering and amplitude-based detection
    * [Raven Pro](https://ravensoundsoftware.com/software/raven-pro) (paid) - configurable band-limited energy detection (amplitude-based)
    * [WarbleR](https://marce10.github.io/warbleR/) (free)
* **Classification**: predict the identity of sounds captured in recordings, e.g. training a convolutional neural network to identify bird species in a recording
    * [ARBIMON](https://arbimon.sieve-analytics.com/) - web-based interface for creating own classifiers
    * [AviaNZ](http://www.avianz.net/index.php) (free) - user can configure "filters" for certain species
    * [BirdNET](https://github.com/kahst/BirdNET) (free) - pre-created neural network classifiers for common birds of North America and Europe
    * [BirdVoxClassify](https://github.com/BirdVox/birdvoxclassify) (free) - pre-created nocturnal flight call classifiers for a limited number of North American bird species
    * [Kaleidescope](https://www.wildlifeacoustics.com/products/kaleidoscope-pro) (paid) - pre-created bat classification
    * [OpenSoundscape](https://github.com/ktizeslab/opensoundscape) (free, in development) - pulse rate analysis of repeating calls; features to create own neural network classifiers are in developent
* **Measuring acoustic parameters**: recording metrics for soundscapes or individual calls
    * [soundecology](https://cran.r-project.org/web/packages/soundecology/vignettes/intro.html) (free) - calculate soundscape-wide acoustic indices
    * [warbleR](https://marce10.github.io/warbleR/) (free) - measure acoustic signal structure
    * [Raven Lite](https://ravensoundsoftware.com/software/raven-lite/) (free) and [Raven Pro](https://ravensoundsoftware.com/software/raven-pro) (paid)
