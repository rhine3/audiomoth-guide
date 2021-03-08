[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3667065.svg)](https://doi.org/10.5281/zenodo.3667065)

# AudioMoth: a practical guide to the open-source ARU

This guide is intended to be comprehensive for both first-time AudioMoth users and those interested in scaling up their AudioMoth deployment. 

The information here complements official guides on the [Open Acoustic Devices website](https://www.openacousticdevices.info/getting-started) and a guide by [David Brown](https://sites.google.com/view/audiomoth/home). Some technical information about the devices themselves is excluded. We have also elaborated on each step by including images, procedures, and rules of thumb that we've created while deploying hundreds of AudioMoths. 

Please submit suggestions for modifications to this guide via creating pull requests on the GitHub repository, or emailing me at `tessa.rhinehart at pitt.edu`.


#### Suggested citation
If you find this guide helpful, please share it! It is available in both [PDF](https://github.com/rhine3/audiomoth-guide/raw/master/guide.pdf) and [Markdown](https://github.com/rhine3/audiomoth-guide/raw/master/guide.md) formats. 

The guide and the other materials in this repository are licensed under [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/). Please feel free to use and modify them with attribution. You may cite the guide as follows, replacing the `<>` with the DOI in the image at the top of this document.
```
Rhinehart, Tessa A (2020). AudioMoth: a practical  
guide to the open-source ARU. GitHub repository: 
https://github.com/rhine3/audiomoth-guide. DOI: <>
```

If you modify this document and would like to make a .pdf version, you can use `pandoc` on the command line to compile the PDF version from Markdown: `pandoc guide.md -o guide.pdf --variable urlcolor=cyan`. (You will have to remove the DOI image at the top of the document to do so, as `pandoc` doesn't support this image type.) On GitHub, `guide.pdf` automatically updates after a push to `guide.md` using GitHub Actions.

#### Acknowledgements

This guide was improved by the experiences and feedback of Alex Rogers, Trieste Devlin, Lauren Chronister, Lauren Schricker, Abram Fleishman, and other members of the AudioMoth community. The AudioMoth was developed by [Open Acoustic Devices](https://www.openacousticdevices.info/). Its first description in academic literature can be found in:

```
Hill, Andrew P., Peter Prince, Evelyn Piña Covarrubias, and 
C. Patrick Doncaster. “AudioMoth: Evaluation of a Smart Open 
Acoustic Device for Monitoring Biodiversity and the Environment.” 
Methods in Ecology and Evolution, December 3, 2017.
```


#### Table of contents

* [Quick start](#quick-start)
* [Setup](#setup)
  * [How to create a recording schedule](#how-to-create-a-recording-schedule)
  * [Apply recording schedule to your AudioMoth](#apply-recording-schedule-to-your-audiomoth)
  * [SD cards and batteries](#sd-cards-and-batteries)
  * [Turn on the recorder](#turn-on-the-recorder)
  * [Apply different firmware to the device](#apply-different-firmware-to-the-device)
* [Deployment](#deployment)
  * [Enclosures](#enclosures)
  * [Logistics](#logistics)
* [Scaling up](#scaling-up)
  * [Purchasing AudioMoths](#purchasing-audiomoths)
  * [Using protocols](#using-protocols)
  * [Pre-selecting recorder locations](#pre-selecting-recorder-locations)
  * [Other tips and tricks](#other-tips-and-tricks)
  * Calibration - *coming soon*
* [Data management](#data-management)
  * [Data upload](#data-upload)
  * [Metadata management](#metadata-management)
* [Data analysis](#data-analysis)


# Quick start

AudioMoths are very easy to set up out of the box. A good general introduction to the AudioMoth is available in the [AudioMoth guide](https://docs.wixstatic.com/ugd/d97703_9ac305905bdd4cdfab6aee99767a56e6.pdf) by Open Acoustic Devices. Our procedure is as follows.

* [Purchase AudioMoths](#purchasing-audiomoths) 
* Buy necessary supplies, including batteries and SD cards
* [Download](https://www.openacousticdevices.info/applications) the configuration app 
* Use the app to create a "program" (a recording schedule for the AudioMoth to follow) as described in detail below, **formatting time in UTC**
* Insert batteries and microSD card into AudioMoth
* Connect AudioMoth to computer and press green button on configuration app
* Create housings for your AudioMoths
* Devise a field protocol for deployment of the AudioMoths
* Deploy AudioMoths and put up legally required "recording in progress" signs


# Setup

Before using the AudioMoth, you will "program" it using the [Audiomoth configuration app](https://www.openacousticdevices.info/applications). Depending on your needs, you may customize the time of day during which recordings are made, the length of each recording, and the amount of time the recorder "sleeps" between each recording. 

The AudioMoth can be used in two modes which are be accessed using the switch on the device: DEFAULT, in which the AudioMoth will start recording immediately, and CUSTOM, in which the AudioMoth will only record at certain times. 

* The behavior in DEFAULT mode depends on the firmware you are using and whether the AudioMoth has been programmed, but in general, it results in the AudioMoth turning on and starting to record immediately. The DEFAULT mode can be used before programming a recording schedule to the AudioMoth.

* In CUSTOM mode, the AudioMoth also cycles through recording/sleeping, but only within "recording periods" that you have already configured. For instance, you could set the AudioMoth to record a minute-long file every 10 minutes for the first 6 hours after sunset. The CUSTOM mode can only be used when the AudioMoth has a recording schedule programmed onto it using the AudioMoth configuration app.

Use the AudioMoth configuration app to create a custom recording schedule for your AudioMoth. After creating your configuration, you will plug the AudioMoth into your computer, and set the current time and desired recording schedule via the app interface. For a simple and intuitive introduction to this process, see the [Open Acoustic Devices Config App Guide](https://www.openacousticdevices.info/config-app-guide). For more in-depth information, read the steps below.

Note that the switch is fragile and snaps off easily. A slow, careful, and firm touch reduces disappointing switch snapping when turning the AudioMoth on and off. If your switch has snapped, it is possible to [replace the switch slider](https://www.openacousticdevices.info/support/device-support/simple-audiomoth-switch-repair).

## How to create a recording schedule
Create a recording schedule using the configuration app, downloadable here: https://www.openacousticdevices.info/applications

The latest version of the configuration app has three tabs: Recording Settings, Schedule, and Advanced Settings.

# WARNING: RECORDING SCHEDULES MUST BE CREATED IN UTC, NOT YOUR OWN TIMEZONE! (see below)

Hopefully this warning will catch the eye of anyone quickly skimming this guide. This is one of the biggest and most commonly encountered silent failure points of using an AudioMoth. 

Follow the instructions in the next section carefully, or else you may program your AudioMoths to record at the wrong time. It's disappointing to bring your recorders back from 2 months of deployment and realize your "dawn chorus" recordings were actually taken at midnight.



### "Schedule" tab 

#### Recording periods
The "schedule" tab lets you set 1-4 recording period(s) in Coordinated Universal Time (UTC) using a 24-hour clock.

* **What is UTC?**: Instead of referring to a time zone (like Eastern Time, Pacific Time, etc.), recordings on the AudioMoth are scheduled in UTC, a universal time standard. This is done to avoid ambiguity in time zones. UTC is equivalent to Greenwich Mean Time (GMT), but does not observe Daylight Savings time as some countries in the GMT time zone do.

* Make sure to press "Add recording period" after typing in the desired time of each recording period. Recording periods will show up on the red/white graphic or the period listing on the right side of the program. Likewise, be sure to remove unwanted periods.

* The recording periods will only be adhered to when the AudioMoth is on CUSTOM mode. On DEFAULT mode, the recorder begins recording immediately, without regard to any scheduled recording periods. 

![Set recording period on AudioMoth configuration app](images/programming/recording-period-fast.gif)

### "Recording settings" tab
This tab controls the sample rate of recordings, the gain to be used on the microphone, the length and space between recordings, and a few other settings.

#### Sample rate
Set sample rate as 2x the highest frequency you want to record.

* **What sample rate should I use?** You should use a sample rate that is 2x higher than the highest frequency you want to record. This sample rate is known as the [Nyquist rate](https://en.wikipedia.org/wiki/Nyquist_rate) and is the minimum sample rate required to resolve a sound at a particular frequency. For birds, a 32kHz sample rate is fine. For bats' ultrasonic calls, a much higher sample rate is required.

* Sample rates > 192kHz are "experimental"--use with caution.

* Recording at high sample rates requires faster SD cards and takes up more storage space. See the section on [SD cards](#sd-cards-and-batteries) for more information. 

* What is a sample rate, anyway? A microphone captures audio by transforming the sound waves into voltage. Digital audio is recorded by sampling that voltage. The *sample rate* in Hertz is the number of times per second the voltage is sampled. For a helpful introduction to digital audio, check out [this guide](https://web.archive.org/web/20190201094638/https://docs.cycling74.com/max5/tutorials/msp-tut/mspdigitalaudio.html)

#### Gain
The gain is the amount that sounds from the microphone will be amplified once recorded. Selecting the optimal gain requires trial and error in your particular field conditions. If the gain is too high, your recordings will [clip](https://en.wikipedia.org/wiki/Clipping_(audio)), creating an unpleasant distortion that can be challenging, if not impossible, to analyze. Alternatively, if the gain is too low, sounds will be faint and hard to hear.

#### Sleep-record cycles
In the "schedule" tab you select the time of day that the AudioMoth should record each day (the "recording period" or periods). However, the AudioMoth doesn't have to record continuously every day. You can use a sleep/record schedule to record only a limited amount of time during the scheduled recording period.

![Set sleep and recording durations](images/programming/sleep-rec-fast.gif)

* When this feature is enabled, the recorder will create a recording for the number of seconds indicated in "recording duration" and then sleep for the number of seconds indicated in "sleep duration."

* If you do not wish to enable this feature, unclick "Enable sleep/record cyclic recording."
  
* With older versions of the firmware (<1.4.0), to make a single continuous file each recording period, you are not able to disable this feature manually. Instead, you must to set the recording duration length equal to the length of the longest recording period. 
  
* With older versions of the firmware (<1.4.2), you must make sure that your file sizes are less than the WAV file size limit of 4.3GB (4000MB).

* Even if sleep period is set to 0, the device will sleep briefly between recordings to save the prior recording to the card.

#### Enable LED
This feature allows you to turn on the LED lights for more information about your AudioMoth, though this might attract more attention from animals/curious humans. Lights are especially useful when testing the recorder. 

LED light meanings are:
* Blinking red = recording
* Blinking green = sleeping between recordings
* Constant red = memory card full
* Both green & red = recording cannot be made. Causes of this include, but are not limited to,

    * time or program not being set (while in CUSTOM mode);
    * the batteries falling out at some point after programming (while in CUSTOM mode);
    * the recorder getting wet; and
    * the SD card malfunctioning or not being formatted correctly.

* Flashing red after turned to USB/OFF: an indicator of battery life (see [official documentation](https://www.openacousticdevices.info/led-guide))


### "Advanced settings" tab
These two features can be used separately, or combined. For more information on these features, see [this document](https://github.com/OpenAcousticDevices/Application-Notes/blob/master/Using_AudioMoth_with_Filtering_and_Amplitude_Threshold_Recording.pdf)

#### Filtering
This feature allows you to only record data from a particular frequency band. When you enable filtering, you can choose the following filters. Each allows you to select the frequencies you want to include in the recording. All other frequencies will be filtered out.
* Low-pass: filter out high frequencies
* Band-pass: filter out both high and low frequencies
* High-pass: filter out low frequencies

#### Amplitude threshold
This feature allows you to only save samples to the file that meet a particular amplitude threshold. This allows you to save on storage by not saving empty files--especially helpful for high-sampling rate files, which are very large.

### Recording information calculation
The program will calculate the energy and storage used each day once you have specified the recording period and recording/sleep durations. This appears at the bottom of the configuration app in every tab.

* To refresh batteries and cards as infrequently as possible during multi-month deployments, use a battery/SD card combination where the battery life and card storage run out at roughly the same time, given the device's estimated energy and storage usage.

* Use [this code](https://trinket.io/python/ff8aeb66e1) to estimate the number of operational days of a battery and SD card. Input card size and capacity of a single battery (e.g., 2850 mAh for a Duracell alkaline AA battery), plus the config app's estimated and storage and energy usage. For more information on battery capacity, see the section on [batteries](#sd-cards-and-batteries).

* With older versions of the firmware (<1.4.2), you must make sure that your file sizes are less than the WAV file size limit of 4.3GB (4000MB). Current versions of the firmware handle file sizes that are approaching this limit by closing the current file and restarting a new one.

### Keeping track of recording schedules

Firmware versions 1.4.0 and later save the schedule description to the AudioMoth's microSD card to allow easier recordkeeping. This is saved when recordings are made, not when the AudioMoth itself is programmed.

Additionally, you may save the completed schedule as a file for later reference, reuse, copying, and sharing. Clicking a saved configuration file itself may not correctly open the program. Instead, open the saved program through the configuration app itself. Select the menu option AudioMoth > Open Configuration.

### Example programs

Below are some example programs created with an older version of the configuration app.

One creates a single 3-hour long recording per day at 32kHz, suitable for recording a bird dawn chorus. 

The other creates minute-long recordings with minute-long breaks in between, 30 each at two different times. The latter program records at a sample rate of 192kHz, perhaps for recording bat ultrasonic sounds, and will require a fast microSD card.

![Two example programs](images/programming/example-programs.jpg)


## Apply recording schedule to your AudioMoth

After you have configured the program that you want to use, you must load it onto an AudioMoth that contains batteries. 
Because the AudioMoth doesn’t have an onboard battery, if the batteries fall out, the programming and set time will be lost. **The AudioMoth must be reprogrammed if the batteries fall out.** 
* If you switch the AudioMoth to CUSTOM mode and its red and green lights flash simultaneously, this means that the AudioMoth is not able to record. One cause of this is the AudioMoth's batteries falling out. 
* If turned to DEFAULT mode after the batteries come out, the AudioMoth's behavior differs depending on what firmware is installed.
  * Firmware < 1.4.2: record for 10 seconds on, 5 seconds off
  * Firmware 1.4.2 and after: record continuously, ignoring sleep/duration settings

Follow the settings below to save the recording schedule to your AudioMoth:

* Turn switch to CUSTOM mode briefly. 
* Make sure both red and green LED lights flash. This means that your batteries are correctly connected to your AudioMoth, and the program will successfully save on the AudioMoth.
* Set switch on AudioMoth to USB/OFF mode.
* Plug into computer via microUSB.
* Verify that the AudioMoth is plugged in: the date, time, and recorder information on the programming app will switch from "grayed out" to black.
* Press green "Configure AudioMoth" button in the programming app. This saves the recording program to the AudioMoth, and sets the AudioMoth's internal clock to your computer's time in UTC.
* The AudioMoth now has a CUSTOM recording schedule. When ready to deploy, move AudioMoth switch to CUSTOM.

## SD cards and batteries

The above steps describe how to program an AudioMoth containing batteries and SD cards. Here is some guidance on selecting and using batteries and SD cards.

### microSD cards
The AudioMoth saves recordings on a microSD card.

#### Card formatting
* With versions of the firmware < 1.2.2, AudioMoth cards must first be reformatted to FAT32 prior to each use. Firmware versions 1.2.2 and beyond support exFAT formatting of cards as well. Most cards natively come formatted with exFAT.

* When reusing a microSD card that has already been deployed, check to make sure that the card is truly empty before reusing. 

  * On Mac computers, you can check the amount of space remaining on the card using Disk Utility. On some file systems, deleting files on the microSD card using the graphical user interface does not actually delete them until the trash bin is emptied. 
  * You can be certain a card is empty by reformatting the card every time you reuse it, or using the `rm` command in the terminal.
  
* FAT32 was originally intended for cards less than or equal to 32GB in size. Windows computers cannot natively format cards larger than this to FAT32 format, but there are [free programs](http://www.ridgecrop.demon.co.uk/index.htm?guiformat.htm) that allow Windows users to format larger cards. Mac computers can format cards at least up to 128GB; we haven't tested anything larger.

#### Choosing and using cards
* Recording with high sampling rate (e.g., recording bats) requires SD cards with fast read/write speeds. Files produced with high sampling rate are also larger, so they use up space on the SD card more quickly. We use SanDisk Extreme 128GB for bat recordings. See the [SD card guide](https://www.openacousticdevices.info/sd-card-guide) for more information.

* When an SD card fills, the unit will stop saving recordings to it, and the unit's red LED light will stay constantly lit until the SD card is removed.

* Insert the card into the AudioMoth with the contacts facing **up**, as shown on the graphic on the front of the AudioMoth. (It won't fit any other way.)

![Correct way to insert SD card](images/other/sd-card-position.jpg)


### Batteries

* Battery life depends on the type of battery you use. Check the battery's *capacity* in milliamp-hours (mAh). Lithium AA batteries have a larger capacity than typical alkaline AA batteries, but also cost more. On the AudioMoth, the capacities do not add up--the capacity of the three batteries connected in series is equal to the capacity of any single battery.

* While the AudioMoth's battery casing accepts 3 AA batteries, with some electronics expertise you can modify the device to increase its battery life. The modified bank of batteries must have the same voltage but a higher capacity in mAh. For instance, 3 D batteries have the same voltage as 3 AA batteries but a higher capacity.

    * The *voltage* of batteries connected in series (as they are on the AudioMoth) is equal to the number of batteries multiplied by the voltage of each battery. AudioMoth v1.0 uses 3 batteries at 1.5 volts each, so the voltage of the battery bank is `3 * 1.5V = 4.5V`.
    
    * The *capacity* of batteries in series is the capacity of any one battery in the series. (Don't mix batteries of different capacities, or new and old batteries.) For instance, a Duracell alkaline AA battery has a capacity of 2850mAh.
   

* Because the AudioMoth doesn’t have an onboard battery, if the batteries fall out, the programming and set time will be lost; if you have programmed a CUSTOM recording schedule it is no longer on the AudioMoth and will require reprogramming. 

    * Masking tape is a cheap, mostly secure way of preventing batteries from falling out
 
    * We take care not to jostle AudioMoths in transport, and we always bring several extra programmed AudioMoths with us during deployments, just in case we drop one and the batteries fall out. 
    
    * While deploying recorders in CUSTOM mode, it will be obvious if a device has lost its programming; its red and green lights will blink simultaneously when you try to flip the switch to CUSTOM.


## Turn on the recorder

The AudioMoth can be turned on in two ways: DEFAULT mode (move switch to the right) or CUSTOM mode (move switch to the left).

* **DEFAULT:** Device immediately starts recording. Recording period/schedule is irrelevant in DEFAULT mode.

  * With firmware versions before 1.4.2, the AudioMoth will take a recording for a desired amount of time, and then will sleep for a desired amount of time. The device repeats this cycle continuously. If the recorder has not been configured with the configuration app, the sleep/record duration settings default to 10 seconds recording - 5 seconds sleeping.

  * Starting in firmware version 1.4.2, DEFAULT mode records continuously, ignoring sleep/duration settings for recording duration time. 

* **CUSTOM:** 

  * If device is turned on outside of the scheduled recording periods, it waits until recording period starts, then begins its recording schedule. 
  
  * If it is turned on during the recording period, it behaves differently based on what firmware is used.
            * With firmware before version 1.4.1, the AudioMoth will not start recording until the next scheduled recording begins. For instance, consider an AudioMoth scheduled to record at 09:00, with a 2-minute recording duration and 2-minute sleep duration. If the AudioMoth was switched to CUSTOM mode at 9:01, it would skip the recording scheduled for 9:00-9:02, and wait until 09:04 to make its first recording.
            * With firmware version 1.4.1 and higher, the recording will be started mid-cycle, rather than waiting for the next cycle to begin.


## Apply different firmware to the device

As discussed above, several different firmware versions for the AudioMoth have been created and released. Some releases are just updates, but some have special functionality. For instance, version 1.4.0 enables users to trigger AudioMoth recording only when sound exceeds an amplitude threshold. Behavior of the AudioMoth in different firmware versions differs slightly but meaningfully. To see all of the features added or changed in each version of the firmware, view [the release descriptions in the GitHub repository](https://github.com/OpenAcousticDevices/AudioMoth-Firmware-Basic/releases).

If you want to flash new firmware to your device, download the application [here](https://www.openacousticdevices.info/flashing) and follow its instructions. All of the released firmware versions can be downloaded through the app and applied to the AudioMoth. AudioMoth batteries must be removed before flashing new firmware on the device.



### Recording troubleshooting

* If a unit's microSD card is full, the unit stops saving recordings. This avoids overwriting previous recordings. In this situation, the unit's red LED light will stay constantly lit until the SD card is removed.

* Turning the AudioMoth off while it is still recording will cause some data loss. This is because the speed at which the data are saved to the AudioMoth lags behind real time. We have found that turning off a recorder while it is recording causes about a 3% loss of data; e.g. a recording that was stopped an hour into the recording will lose 1.8 minutes (60 minutes * 0.03 = 1.8 minutes).

* The first versions of the AudioMoth firmware use filenames with compact representations of the date and time that the recording started. These filenames can be converted to date & time using the instructions in the AudioMoth user manual. In contrast, the "last modified" time represents the time in UTC that the file was saved, i.e., the time in UTC when the recording ended. More recent firmware saves more easily interpreted filenames.


# Deployment

"Deployment" is the process of putting recorders out into the field. Below are ideas and important notes to remember about deployments, including how to inform the public, record data, safely affix AudioMoths to trees, and more.

## Enclosures

AudioMoths may break if exposed to water, so it is necessary to house them in a secure, watertight enclosure. This is complicated by the fact that the mic, a MEMS mic, is attached to the circuitboard. The housing must be both watertight and acoustically transparent over the mic.

#### Ziploc baggies

![AudioMoth deployed on tree](images/housing/bag-housing.jpg)

AudioMoths can be deployed in Ziploc baggies using [buckling straps (Amazon link)](https://www.amazon.com/Release-Buckle-Black-Adjustable-Luggage/dp/B005DJIBYA). The baggie can be affixed to the strap using zip-ties or by looping the baggie around the strap and securing it with duct tape.

* Trees should be as small as possible; larger trees block sound from arriving in all directions.

* If possible, avoid placing AudioMoths in direct sunlight, as their enclosures may heat up.

The switch and corners of the AudioMoth v1.0 are sharp and can rip through a Ziploc bag. More recent AudioMoth designs have rounded corners and an inset switch to reduce this issue. Take steps to prevent moisture getting into AudioMoth enclosure:

* Don’t transport AudioMoths within the bags, as the bags are more likely to break. Instead, keep the AudioMoth and bag separated until you are ready to hook the bag to the tree. If it is raining, bring an umbrella and transport AudioMoths within a waterproof bag.

* Use freezer bags, not sandwich bags.

* Taping over the sharp parts of the AudioMoth, or judiciously applying hot glue, reduces the chance of punctures. 

    * We do not apply anything next to the mic, as we are currently unsure of the effect on the recording quality. Take care not to obstruct SD card insertion or switch movement.

    * [Example with tape by Jennifer Sheridan](https://twitter.com/JenASheridan/status/1047766465900818432)
   
* Include a desiccant pack in the bag to soak up lingering moisture in the bag, preventing condensation

* Before you walk away from a newly-deployed AudioMoth, inspect the bag for scratches or punctures. Replace if necessary.

#### Heat-sealed bags

Ziploc baggies are susceptible to puncture. These baggies can also be challenging to affix to straps. An alternative to Ziploc baggies is creating an enclosure using a heat-sealed bag. We create these using vacuum sealer with a "heat-seal-only" function. (Vacuuming air out of bags would reduce sound quality.)

![Heat-sealed bag](images/housing/heat-sealed.jpg)

You can use the following steps to create, deploy, and reuse a heat-sealed enclosure:
* Create seals on 3 sides of the bag
* Seal 2 inches below one of the sealed sides, then cut the corners off of this side. This creates a pocket for your strap to go through.
* Insert strap in pocket
* Program AudioMoth and turn it on
* Insert AudioMoth and any other desired components (e.g. desiccant packet, small notecard about study)
* Seal final edge of enclosure
* Strap enclosure to tree
* After deployment, cut open the bottom of the bag to release the AudioMoth

![Diagram for preparation of heat-sealed bag](images/housing/heat-sealed-diagram.png)

Two downsides to this method are:

* If you prepare the enclosures on a carpeted surface, you may encounter static shock. To prevent this, you can spray anti-static spray (like hairspray or [anti-static fabric spray](https://www.amazon.com/Static-Guard-Fabric-Spray-Ounce/dp/B0013IRBG4)) on the inside of the bag, or perhaps even rub a dryer sheet on the inside of the bag

* The AudioMoth needs to be programmed and turned on before you put it in the bag. Newer versions of AudioMoth firmware allow you to set a delayed start date for recording; without this, your AudioMoths will start recording on their daily schedule after being turned on, whether or not you've placed them in the field!


#### Hard cases

Ziploc baggies do not provide protection against intrusions like chewing by curious rodents, and rubbing by deer or bison. If these are a problem in your area, consider using hard enclosures for your AudioMoths.

Hard plastic or acrylic cases should have a hole through which sound can enter. This sound can be covered with a water-resistant acoustic membrane sticker or cloth.

Open Acoustic Devices provides a design for a laser-cut acrylic housing [here](https://www.openacousticdevices.info/single-post/2019/04/24/AA-acrylic-laser-cut-enclosure). OAD has also started selling injection-molded cases through [GroupGets campaigns](https://groupgets.com/campaigns/775-the-official-audiomoth-ipx7-waterproof-case?archived=true&page=1). In addition, many groups have shared their housing advice on the [WildLabs Acoustic Monitoring forum](https://www.wildlabs.net/community/group/acoustic-monitoring) and Twitter. Some examples:

* [Tupperware case by Emily Hoffman](https://twitter.com/em_hoffmann/status/1200221472641282048)

* [Tupperware case by Carolina Ocampo](https://twitter.com/CarOcampoA/status/1045013308900868096)

* [Hand-assembled case by Heather Wood](https://www.wildlabs.net/community/thread/554)

* [3D printable case by Robin Jones](https://www.thingiverse.com/thing:3292311)

* [3D printable case by Jon Flanders](https://twitter.com/jonrflanders/status/1084491613068513282) (design not released yet)

* [Hand-assembled case by Ruby Lee](https://www.wildlabs.net/resources/case-studies/trialing-audiomoth-detect-hidden-threats-under-canopies-belize) (design not released; scroll down to see picture)

## Logistics

* Create a packing list to make sure you have a few essential tools. [Example](https://github.com/rhine3/audiomoth-guide/blob/master/documents/packing-list.md)
* If you’re also using playback or imitation to survey the area, make sure these sounds can’t be mistaken on the recordings for actual birds. For instance:
    * Use playback or imitation only outside the hours of the recording
    * Use a distinctive unnatural sound (e.g., a “triple knock” instead of a “double knock”)
    * Verbally announce your presence so that all recorders that may capture your recording can hear your announcement
* In the case of SD card mixups, one can use the EXIF metadata (described below) to identify which unit created each recording.

#### Informing the public
* To legally deploy recording devices on public lands in the United States, you must make a good-faith effort to inform people that recording is occurring
* Place signs on all entry points (especially roads, parking lots). Signs must include the verbiage “By proceeding, you consent to being recorded.” An example of a complete sign:

```
Equipment for recording bird vocalizations is in use in this 
area within 3 hours of sunrise. This equipment may incidentally 
record other sounds, including human conversation. By 
proceeding during this period, you consent to being recorded. 
Please contact Jane Doe at jane.doe@university.edu
with questions about this study.
```

* Another idea is to add a note on each recorder with information about the study. However, it is unclear whether these notes would deter or encourage recorder loss. :-)

# Scaling up

For large deployments, special considerations must be taken into account. For instance, when deploying 100 recorders, an extra 5 minutes spent per recorder results in 8+ additional hours in the field!

## Purchasing AudioMoths

Wherever you purchase AudioMoths, make sure you check what version you're purchasing. For instance, AudioMoth v1.0.0 has sharp corners and a protruding switch; v1.1.0 has rounded corners and a recessed switch to reduce bag breakage.

* [GroupGets](https://groupgets.com/) purchases are run by [Alasdair Davies](https://twitter.com/Al2kA) every few months. These are helpful for folks looking to buy on the scale of a few dozen AudioMoths for $50 each. 

* For those who can't wait for the next GroupGets purchase, AudioMoth is available at higher prices on [LabMaker](https://www.labmaker.org/products/audiomoth). LabMaker prices are higher due to a smaller number of devices being assembled at once. 

* It may be possible to purchase AudioMoths at a lower price if larger volumes are ordered. Our lab has had excellent experiences purchasing from [RushPCB](https://rushpcb.com/). We bought the devices pre-assembled (i.e., components connected to boards, battery pack soldiered to board), but without the firmware flashed. We found it easy to flash the firmware in our lab.

* Parts of the original AudioMoth design are constantly going out of stock due to high demand. We enlisted the help of our school's electronics shop to find new parts that were interchangeable with the out-of-stock parts.

## Using protocols

Since so many recorders will be deployed, information about their identity and location has to be taken accurately and efficiently.

* Record the deployment date; information about the identity (ID number) of the AudioMoth, SD card, and location; any important notes about placement such as recorder direction; etc.
* See the section about pre-positioning recorder locations and ideas for location naming conventions.
* Some researchers use apps such as [Survey123](https://survey123.arcgis.com/) or [Fulcrum](https://apps.apple.com/us/app/fulcrum-mobile-data-collector/id467758260) to record these data in the field

We use protocols to speed up the process and keep track of repetitive tasks. (It's easy to leave out crucial steps, like turning the AudioMoth on, if you don't have to check them each off of a list.) Here are some example protocols that we use:
    
* [Packing for a deployment](https://github.com/rhine3/audiomoth-guide/blob/master/documents/packing-list.md)
* [Deploying recorders](https://github.com/rhine3/audiomoth-guide/blob/master/documents/deployment-protocol.pdf)
* [Bringing recorders home](https://github.com/rhine3/audiomoth-guide/blob/master/documents/return-protocol.pdf)
* [Post-field checklist](https://github.com/rhine3/audiomoth-guide/blob/master/documents/post-field-checklist.md) (which references the document below)
* [Template for protocols to check in data written down in the field](https://github.com/rhine3/audiomoth-guide/blob/master/documents/post-field-protocol-template.pdf) 
* [Example modification of the above template](https://github.com/rhine3/audiomoth-guide/blob/master/documents/post-field-protocol-example.pdf)


## Pre-selecting recorder locations

Lauren Schricker ([website](https://mountainlauren.weebly.com/) - [Twitter](https://twitter.com/mountain_laur)) developed this method of pre-positioning locations of recorders for deployments:

* Log in to your Google account.

* Create a new map: go to https://drive.google.com > New > More > Google My Maps

* Change the base map to "Satellite"

* Click on the "Add Marker" tool and add markers to your map. You might try to target specific locations, for example, identify particular trees that are good candidates for hanging AudioMoths.

    * We name all of our recorder locations with an alphanumeric code that gives the site of the deployments, and a numeric code that uniquely identifies the point at that site. For instance, our deployments at Powdermill Nature Reserve in the pond area are named PNRE-POND-0001, PNRE-POND-0002, etc. 

* Use the "measuring" tool to find even spacing between points (press "Enter" to temporarily save a measurement before you plot your next point)

* If multiple groups of people will deploy recorders, decide beforehand which group will deploy at which points. You can change the color of the point marker on Google Maps to easily see the group divisions.

![Google My Maps](images/programming/google-maps-demo.gif)


## Other tips and tricks

![Two hundred AudioMoth housings made from Ziploc bags](images/housing/bulk-housings.jpg)

* Save time in the field by pre-packing bags with desiccant and pre-attaching them to straps in the lab, instead of performing these tasks in the field.

* It is very helpful to have two people in the field.

    * One person can record data, e.g., the unique ID of the AudioMoth, its SD card, and the point at which it is deployed.

    * The other person can manage putting the AudioMoth on the tree and collecting a more accurate GPS point
 
* When writing down data in the field, use waterproof paper and permanent pens (e.g., fine-tipped Sharpies or Rite in the Rain brand pens).


# Data management

## Data upload
![Storage and SD card reader](images/other/nas.jpg)

Transferring audio files from hundreds of SD cards is a slow process to do manually. Instead, use a multi-port SD card reader. The photo above shows a network-attached storage device (NAS) with 48 TB of storage, plus a multi-port SD card reader.

* We designed a 32-port SD card reader that can be made using supplies purchased from Amazon, the ["hexadecapus"](https://github.com/kitzeslab/sd-transfer/blob/master/Hexadecapus/Hexadecapus%20multi-SD%20reader.pdf). 

* Each SD card has its number (e.g. 0526) written on the front of the card in Sharpie, but is also given a volume name (e.g., MSD-0526) when it is first reformatted to FAT32. These names are then used to organize the audio files copied off of each card.

* When microSD cards are all named in this way, the following `rsync` command automatically copies data: 

   `rsync -rhv /Volumes/MSD* --exclude .Spotlight* --exclude .fsevents* --exclude System* /Volumes/seagate/transfer_20200622/`

  * The command will find all cards in `/Volumes` named with the prefix "MSD" 
  
  * These data will be copied to a folder on an external hard drive, `/Volumes/seagate/transfer_20200622`
  
  * This command excludes some system files created by some operating systems
  
  * Use the flag `-n` to run a dry-run of this command first!

* Before you consider your data transfer complete, check to make sure that all of the expected folders have been created and they are of the expected size and number of recordings.

## Metadata management
It is important to keep track of metadata about the files that were created. 

* The AudioMoth stores metadata about the recording in the "Comments" field of the EXIF metadata. This includes recording date/time, sample rate, recording duration, gain setting, battery level, and AudioMoth serial number. For instance, here is an example metadata record automatically generated by an AudioMoth, accessed through `exiftool` (see below)

 ```
File Name                       : 5ACDE3A8.WAV
Directory                       : .
File Size                       : 27 MB
File Modification Date/Time     : 2018:04:11 10:35:00-04:00
File Access Date/Time           : 2018:04:17 11:16:05-04:00
File Inode Change Date/Time     : 2018:04:17 11:17:43-04:00
File Permissions                : rwxrwxrwx
File Type                       : WAV
File Type Extension             : wav
MIME Type                       : audio/x-wav
Encoding                        : Microsoft PCM
Num Channels                    : 1
Sample Rate                     : 48000
Avg Bytes Per Sec               : 96000
Bits Per Sample                 : 16
Comment                         : Recorded at 10:30:00 11/04/2018 (UTC) by AudioMoth 0FE081F80FE081F0 at gain setting 2 while battery state was 3.6V
Duration                        : 0:05:00
 ```

 * EXIF data can be accessed via [`exiftool`](http://owl.phy.queensu.ca/~phil/exiftool/) on Mac, Linux, and Windows. Once it is installed, open a Terminal window and run `exiftool FILENAME.wav`

* If SD cards get mixed up, this information can be used to recover what unit the recording was made on.

* Several metadata standards exist for audio recordings, including [Tethys](https://tethys.sdsu.edu/) and [GUANO](https://guano-md.org/). Recording metadata can be updated to be compliant with these standards using exiftool.


# Data analysis

Data analysis techniques vary from completely automated to completely manual. For instance, some software enables automated identification of species vocalizing in recordings. Other software makes it easier to look at, listen to, and organize recordings. Software may be free or paid. 

See [this list](resources/analysis-software.md) for brief descriptions of different data analysis techniques, and a list of softwares available.

