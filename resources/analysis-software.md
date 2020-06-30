# Bioacoustics software

A variety of free and paid software is available for bioacoustic analyses. Software packages vary from complete graphical interfaces, to command-line interfaces, to utility libraries that can be used to create analysis pipelines in Python, R, or other programming languages. 

The inclusion criteria for this list are (1) that the software is targeted to or widely used by bioacoustics researchers, and (2) that the software either is stable, is currently in active development, or was recently released. This list is not necessarily a recommendation or a guarantee of quality of particular software packages or analysis techniques. I have not used all of the software below. Some I use frequently and can't live without, whereas some I haven't found to be useful or accurate for my purposes.

You should always judge the performance of an analysis technique by its performance on *your* dataset. Analysis techniques are often published along with metrics to describe their performance, such as accuracy, precision, and recall. However, different recording conditions or different distributions of sounds present in your dataset can result in starkly different performance of the same analysis technique.

* **Listening and viewing**: general-purpose, non-bioacoustics software for listening to recordings and generating spectrograms
   * [Audacity](https://www.audacityteam.org/) (free) - simple, lightweight listening and spectrogram viewing, comparison, and manipulation
   * [GoldWave](https://www.goldwave.com/) (free) - view and manipulate audio
   * [SonicVisualizer](https://www.sonicvisualiser.org/) (free) - spectrogram visualization
* **Manual review and annotation**: bioacoustics-focused software for organizing and annotating recordings, usually also including features for listening to recordings and generating spectrograms
   * [AviaNZ](http://www.avianz.net/index.php) (free) - graphical user interface for organizing and analyzing recordings
   * [DetEdit](https://github.com/MarineBioAcousticsRC/DetEdit) (free) - visualize and annotate detections
   * [GlassOFire](http://www.oldbird.org/glassofire.htm) (free) - Windows software for avian nocturnal flight call review and sorting
   * [Raven Lite](https://ravensoundsoftware.com/software/raven-lite/) (free) - listening and spectrogram viewing; tools to manually select and annotate recordings
   * [SoundSort](https://github.com/macster110/aipam) (free) - visualize, cluster, and annotate recordings, then export these annotations
   * [Triton](http://cetus.ucsd.edu/technologies_Software.html) (free) - condense/annotate very long recordings using Long Term Spectral Averages
   * [Vesper](https://github.com/HaroldMills/Vesper) (free) - web-based application for avian nocturnal flight call analysis; also implements BirdVoxDetect,     BirdVoxClassify, and others (see below)
   * [WarbleR](https://marce10.github.io/warbleR/) (free) - highly multipurpose R package
* **Detection**: locating potential sounds of interest in recordings. Methods include supervised machine learning, amplitude-based detection, and clustering to group sounds into similar-sounding clusters (e.g. unsupervised machine learning)
   * [AviaNZ](http://www.avianz.net/index.php) (free) - capable of clustering
   * [BatDetect](https://github.com/macaodha/batdetect) (free) - bat detection in full-spectrum (i.e., not zero-crossing) recordings
   * [BirdVoxDetect](https://github.com/BirdVox/birdvoxdetect) (free) - machine learning-based detection for nocturnal flight calls
   * [Kaleidescope](https://www.wildlifeacoustics.com/products/kaleidoscope-pro) (paid) - capable of clustering and amplitude-based detection
   * [PAMguard](https://www.pamguard.org/) - detect vocalizations and clicks; geared toward cetacean monitoring
   * [Raven Pro](https://ravensoundsoftware.com/software/raven-pro) (paid) - configurable band-limited energy detection (amplitude-based)
   * [SoundSort](https://github.com/macster110/aipam) (free) - capable of clustering similar pre-detected clips
   * [WarbleR](https://marce10.github.io/warbleR/) (free)
* **Classification**: predict the identity of sounds captured in recordings, e.g. training a convolutional neural network to identify bird species in a recording
   * [ARBIMON](https://arbimon.sieve-analytics.com/) - web-based interface for creating own classifiers
   * [AviaNZ](http://www.avianz.net/index.php) (free) - configure your own "filters" for certain species or download pre-configured filters
   * [banter](https://github.com/EricArcher/banter) (free) - create your own hierarchical acoustic classifiers
   * [BirdNET](https://github.com/kahst/BirdNET) (free) - pre-created neural network classifiers for common birds of North America and Europe
   * [BirdVoxClassify](https://github.com/BirdVox/birdvoxclassify) (free) - pre-created nocturnal flight call classifiers for a limited number of North American bird species
   * [Kaleidescope](https://www.wildlifeacoustics.com/products/kaleidoscope-pro) (paid) - pre-created bat classification
   * [OpenSoundscape](https://github.com/ktizeslab/opensoundscape) (free, in development) - pulse rate analysis of repeating calls; features to create own neural network classifiers are in development
* **Measuring acoustic parameters**: recording metrics for soundscapes or individual calls
   * [PAMr](https://github.com/TaikiSan21/PAMr) (free) - measure acoustic parameters
   * [Raven Lite](https://ravensoundsoftware.com/software/raven-lite/) (free) - basic measurements of acoustic properties through GUI annotation
   * [Raven Pro](https://ravensoundsoftware.com/software/raven-pro) (paid) - advanced measurements of acoustic properties
   * [soundecology](https://cran.r-project.org/web/packages/soundecology/vignettes/intro.html) (free) - calculate soundscape-wide acoustic indices
   * [warbleR](https://marce10.github.io/warbleR/) (free) - offers variety of measurements acoustic signal structure
