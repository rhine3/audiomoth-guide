# Bioacoustics software

A variety of free and paid software is available for bioacoustic analyses. Software packages vary from complete graphical interfaces, to command-line interfaces, to utility libraries that can be used to create analysis pipelines in Python, R, or other programming languages. 

The inclusion criteria for this list are (1) that the software is targeted to or widely used by bioacoustics researchers, and (2) that the software either is stable, is currently in active development, or was recently released. 

This list is not necessarily a recommendation or a guarantee of quality of particular software packages or analysis techniques, but I have indicated in **bold** which software I've seen used most frequently. I haven't used all of the software below. Some I use frequently and can't live without, whereas some I haven't found to be useful or accurate for my purposes.

You should always judge the performance of an analysis method by its performance on *your* dataset. Analysis methods are often published along with metrics to describe their performance, such as accuracy, precision, and recall. However, different recording conditions or different distributions of sounds present in your dataset can result in starkly different performance of the same method.

**Listening and viewing**: general-purpose, non-bioacoustics software for listening to/editing recordings and generating spectrograms.
* [Adobe Audition](https://www.adobe.com/products/audition.html) (paid) - geared toward sound editing
* [**Audacity**](https://www.audacityteam.org/) (free) - simple, lightweight listening and spectrogram viewing, comparison, and manipulation
* [**librosa**](https://librosa.org/librosa/) (free) - Python package with audio loading, spectrogram creation utilities, and per-channel energy normalization
* [GoldWave](https://www.goldwave.com/) (free) - view and manipulate audio
* [Reaper](https://www.reaper.fm/) (free) - spectrogram visualization; enables Python and C/C++ coding within 
* [**scipy.signal**](https://docs.scipy.org/doc/scipy/reference/signal.html) (free) - Python library including spectrogram creation and cross-correlation functions
* [SonicVisualizer](https://www.sonicvisualiser.org/) (free) - spectrogram visualization

**Manual review and annotation**: bioacoustics-focused software for organizing and annotating recordings, usually also including features for listening to recordings and generating spectrograms.
* [Anabat Insight](https://www.titley-scientific.com/us/anabat-insight.html) (free and paid versions) - recording organization, annotation, and mapping
* [AviaNZ](http://www.avianz.net/index.php) (free) - graphical user interface for organizing and analyzing recordings
* [BatExplorer](https://www.batlogger.com/en/products/batexplorer/) (free and paid versions) - organize and annotate bat recordings
* [BatScope](https://www.wsl.ch/en/services-and-products/software-websites-and-apps/batscope-4.html) (free) - manage, sort, view, and play databases of recordings, geared toward bats
* [DetEdit](https://github.com/MarineBioAcousticsRC/DetEdit) (free) - visualize and annotate detections
* [GlassOFire](http://www.oldbird.org/glassofire.htm) (free) - Windows software for avian nocturnal flight call review and sorting
* [Ishmael](http://bioacoustics.us/ishmael.html) (free) - annotation and real-time recording
* [Koe Bioacoustics Software](https://koe.io.ac.nz/) (free) - web-based acoustic data management platform geared towards analysis of small acoustic units
* [Luscinia](https://rflachlan.github.io/Luscinia/) (free) - database management and recording archiving
* [Praat](https://www.fon.hum.uva.nl/praat/) (free) - annotation, especially for individual song analysis (software originally intended for human phonetics)
* [**Raven Lite**](https://ravensoundsoftware.com/software/raven-lite/) (free) - listening and spectrogram viewing; tools to manually select and annotate recordings
* [seewave](http://rug.mnhn.fr/seewave/) (free) - R package to display spectrograms
* [SoundSort](https://github.com/macster110/aipam) (free) - visualize, cluster, and annotate recordings, then export these annotations
* [Tadarida-L](https://github.com/YvesBas/Tadarida-L) (free) - labeling interface of 3-part "Tadarida" software
* [Triton](http://cetus.ucsd.edu/technologies_Software.html) (free) - condense/annotate very long recordings using Long Term Spectral Averages
* [Vesper](https://github.com/HaroldMills/Vesper) (free, in development) - web-based application for avian nocturnal flight call analysis; also implements BirdVoxDetect, BirdVoxClassify, and others (see below)
* [warbleR](https://marce10.github.io/warbleR/) (free) - highly multipurpose R package

**Detection**: locating potential sounds of interest in recordings. Methods include supervised machine learning, amplitude-based detection, and clustering to group sounds into similar-sounding clusters (e.g. unsupervised machine learning)
* [Anabat Insight](https://www.titley-scientific.com/us/anabat-insight.html) (free and paid versions) - bat call detection and custom filtering in full-spectrum and zero-crossing recordings
* [AviaNZ](http://www.avianz.net/index.php) (free) - capable of clustering
* [**Avisoft-SASLab Pro**](http://www.avisoft.com/sound-analysis/) (paid) - automated detection
* [BatExplorer](https://www.batlogger.com/en/products/batexplorer/) (free and paid versions) - bat call detection
* [BatDetect](https://github.com/macaodha/batdetect) (free) - bat detection in full-spectrum (i.e., not zero-crossing) recordings
* [bioacoustics](https://github.com/wavx/bioacoustics/) (free) - R package for sound filtering, automated detection, and extraction of acoustic features
* [BirdVoxDetect](https://github.com/BirdVox/birdvoxdetect) (free) - machine learning-based detection for nocturnal flight calls
* [gibbonR](https://github.com/DenaJGibbon/gibbonR-package) (free) - R package with automated detection and segmentation algorithms
* [Ishmael](http://bioacoustics.us/ishmael.html) (free) - automated detection, geared towards marine wildlife
* [**Kaleidoscope**](https://www.wildlifeacoustics.com/products/kaleidoscope-pro) (paid, 15-day free trial) - capable of clustering and amplitude-based detection
* [monitoR](http://www.uvm.edu/rsenr/vtcfwru/R/?Page=monitoR/monitoR.htm) (free) - R package for automated detection via template matching 
* [PAMguard](https://www.pamguard.org/) - detect vocalizations and clicks; geared toward cetacean monitoring
* [**Raven Pro**](https://ravensoundsoftware.com/software/raven-pro) (paid) - configurable band-limited energy detection (amplitude-based)
* [scikit-maad](https://github.com/scikit-maad/scikit-maad) (free) - Python package including detection functionality
* [seewave](http://rug.mnhn.fr/seewave/) (free) - compute cross-correlation and signal envelopes
* [SoundSort](https://github.com/macster110/aipam) (free) - capable of clustering similar pre-detected clips
* [Tadarida-D](https://github.com/YvesBas/Tadarida-D) (free) - detection and feature extraction for 3-part "Tadarida" software
* [warbleR](https://marce10.github.io/warbleR/) (free)

**Classification**: predict the identity of sounds captured in recordings, e.g. training a convolutional neural network to identify bird species in a recording
* [Anabat Insight](https://www.titley-scientific.com/us/anabat-insight.html) (free and paid versions) - contains open-source BatClassify classifier and can be used with other algorithms
* [ARBIMON](https://arbimon.sieve-analytics.com/) - web-based interface for creating own classifiers
* [Avisoft-SASLab Pro](http://www.avisoft.com/sound-analysis/) (paid) - classification by spectrographic template cross-correlation
* [AviaNZ](http://www.avianz.net/index.php) (free) - configure your own "filters" for certain species or download pre-configured filters
* [BatExplorer](https://www.batlogger.com/en/products/batexplorer/) (free and paid versions) - bat classification
* [BatScope](https://www.wsl.ch/en/services-and-products/software-websites-and-apps/batscope-4.html) (free) - classify bat recordings
* [Banter](https://github.com/EricArcher/banter) (free) - create your own hierarchical acoustic classifiers
* [BirdNET](https://github.com/kahst/BirdNET) (free) - pre-created neural network classifiers for common birds of North America and Europe
* [BirdVoxClassify](https://github.com/BirdVox/birdvoxclassify) (free) - pre-created nocturnal flight call classifiers for a limited number of North American bird species
* [gibbonR](https://github.com/DenaJGibbon/gibbonR-package) (free) - R package that enables user to train neural networks, GMMs, and others
* [Kaleidoscope](https://www.wildlifeacoustics.com/products/kaleidoscope-pro) (paid, 15-day free trial) - pre-created bat classification
* [Koe Bioacoustics Software](https://koe.io.ac.nz/) (free) - clustering with human annotation
* [OpenSoundscape](https://github.com/ktizeslab/opensoundscape) (free, in development) - pulse rate analysis of repeating calls; features to create own neural network classifiers are in development
* [scikit-maad](https://github.com/scikit-maad/scikit-maad) (free) - Python library enabling creation of own classifiers using scikit learn
* [SonoBat](https://sonobat.com/) (paid) - classification of bat calls
* [Tadarida-C](https://github.com/YvesBas/Tadarida-C) (free) - discriminant analysis-based classification; part of 3-part "Tadarida" software

**Measuring acoustic parameters**: acoustic metrics for soundscapes or individual sounds
* [Acoustic_Indices](https://github.com/patriceguyot/Acoustic_Indices) (free) - Python package for calculating acoustic indices
* [Avisoft-SASLab Pro](http://www.avisoft.com/sound-analysis/) (paid) - "sound parameter measurement" and noise level measurement
* [Koe Bioacoustics Software](https://koe.io.ac.nz/) (free) - assess song sequence structure
* [Luscinia](https://rflachlan.github.io/Luscinia/) (free) - wide variety of acoustic signal analyses
* [PAMr](https://github.com/TaikiSan21/PAMr) (free) - measure acoustic parameters
* [Raven Lite](https://ravensoundsoftware.com/software/raven-lite/) (free) - basic measurements of acoustic properties through GUI annotation
* [Raven Pro](https://ravensoundsoftware.com/software/raven-pro) (paid) - advanced measurements of acoustic properties
* [soundecology](https://cran.r-project.org/web/packages/soundecology/vignettes/intro.html) (free) - calculate soundscape-wide acoustic indices
* [**warbleR**](https://marce10.github.io/warbleR/) (free) - offers variety of measurements acoustic signal structure and timing

**Acoustic localization**: estimation of animal position using recordings from time-synchronized recorders
* [Ishmael](http://bioacoustics.us/ishmael.html) (free) - localization and beamforming
* Others to be added soon from [This review](https://onlinelibrary.wiley.com/doi/10.1002/ece3.6216)
