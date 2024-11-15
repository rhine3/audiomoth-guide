[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4976243.svg)](https://doi.org/10.5281/zenodo.4976243)

# AudioMoth: a practical guide to the open-source ARU
by [Tessa Rhinehart](https://tessarhinehart.com), [Kitzes Lab](https://kitzeslab.org/), University of Pittsburgh

Originally published 2019. Revised November 2024.

### About

This document is intended to be comprehensive guide for both first-time AudioMoth users and experienced users interested in scaling up their AudioMoth deployment. Our goal with this guide is to help you gain intuition for using AudioMoths; to provide tips and resources that we've developed while deploying thousands of AudioMoths; and to troubleshoot the wide variety of challenges that you might encounter while using these devices. 

This version of the guide reflects the newest firmware available at the time of writing (v.1.5.0); previous versions of the guide are also available on [GitHub](https://github.com/rhine3/audiomoth-guide).

### Other guides and support

The information here complements official [Open Acoustic Devices documentation](https://www.openacousticdevices.info/getting-started) and a guide by [David Brown](https://sites.google.com/view/audiomoth/home). Since the original release of this guide in 2019, Open Acoustic Devices posted an official manual similar to this material [on their website](https://www.openacousticdevices.info/open-source). These documents contain similar information. The guide below also shares additional information about using AudioMoths in practice, including housing options, deployment procedures and protocols, acoustic tests, common stumbling blocks, and rules of thumb for scaling up.

If you have a question or comment that you can't find addressed in any of these guides, several forums are available to help you. Try searching or posting on the following:

* [AudioMoth support forum](https://www.openacousticdevices.info/support) for AudioMoth-specific questions
* [WILDLABS Acoustic Monitoring forum](https://www.wildlabs.net/community/group/acoustic-monitoring) for general bioacoustics questions
* Twitter communities: use hashtags #AudioMoth or #bioacoustics; follow [OpenAcoustics](https://twitter.com/OpenAcoustics)

Please submit questions suggestions for modifications to this guide via creating pull requests on the GitHub repository, or emailing me at `tessa.rhinehart at pitt.edu`. This guide is released under a [CC-BY](https://creativecommons.org/licenses/by/4.0/) license, meaning you are free to modify it and redistribute it for almost any purpose with proper [attribution](#citing-this-guide).

# Table of contents

This document contains both [links to external websites](https://www.openacousticdevices.com) and [internal links](#table-of-contents).

* [Quick start](#quick-start)
* [Supplies](#supplies)
  * [Purchase AudioMoths](#purchase-audiomoths)
  * [MicroSD cards](#microsd-cards)
  * [Batteries](#batteries)
* [Firmware](#firmware)
* [Create configuration](#create-configuration)
  * ["Recording settings" tab](#recording-settings-tab)
  * ["Schedule" tab](#schedule-tab)
  * ["Advanced settings" tab](#advanced-settings-tab)
  * [Example configurations](#example-configurations)
* [Set configuration and time](#set-configuration-and-time)
  * [Save and open configurations](#save-and-open-configurations)
  * [Apply configuration](#apply-configuration)
  * [Set the time](#set-the-time)
  * [CONFIG.txt](#configtxt)
* [Recording](#recording)
  * [Switch on the recorder](#switch-on-the-recorder)
  * [Recording troubleshooting](#recording-troubleshooting)
  * [How many hours will my AudioMoth record?](#how-many-hours-will-my-audiomoth-record)
  * [Recording quality and calibration](#recording-quality-and-calibration)
* [Enclosures](#enclosures)
  * [Plastic bags](#plastic-bags)
  * [Heat-sealed bags](#heat-sealed-bags)
  * [Hard enclosures](#hard-enclosures)
  * [Camouflage](#camouflage)
* [Deployment](#deployment)
  * [Select deployment positions](#select-deployment-positions)
  * [Deployment metadata](#deployment-metadata)
  * [Written deployment protocols](#written-deployment-protocols)
  * [Electronic deployment aids](#electronic-deployment-aids)
  * [Inform the public](#informing-the-public)
  * [Other tips](#other-tips)
* [Data management](#data-management)
  * [Data upload](#data-upload)
  * [Metadata management](#metadata-management)
* [Data analysis](#data-analysis)
* [Citing this guide](#citing-this-guide)
* [Acknowledgements](#acknowledgements)


# Quick start

Using AudioMoths is a pretty simple process. A good general introduction to the AudioMoth is available on the Open Acoustic Devices ["Getting Started" page](https://www.openacousticdevices.info/getting-started). Here's a high-level view of what is involved in using AudioMoths:

* Purchase [AudioMoths](#purchase-audiomoths), [microSD cards](#microsd-cards), and [batteries](#batteries)
* Insert batteries and microSD card into AudioMoth
* Download the [configuration app](https://www.openacousticdevices.info/applications) to your computer
* Use the app to [create a recording schedule](#configuration-app) for the AudioMoth to record on
* Connect AudioMoth to computer to set the clock and apply the configuration
* Flip switch to "CUSTOM" to start recording on schedule
* Create or purchase waterproof [enclosures](#enclosures) for your AudioMoths
* Leave AudioMoths to record in the field
* Pick up AudioMoths
* [Download data](#data-management) from microSD cards onto computer
* Use manual review or automated programs to [analyze the data](#data-analysis)

# Supplies

The first step to assembling an AudioMoth is getting the necessary supplies and assembling them to create a working recorder.

## Purchase AudioMoths

There are several ways to purchase AudioMoths. 

Wherever you purchase AudioMoths, make sure you check what version you're purchasing. For instance, AudioMoth v1.0.0 has sharp corners and a protruding switch; v1.1.0 has rounded corners and a recessed switch to reduce bag breakage.

**Option 1: GroupGets**: [GroupGets](https://groupgets.com/manufacturers/open-acoustic-devices/products/audiomoth) group purchases are the main way to purchase the latest version of AudioMoths. These purchases open periodically. Make sure to purchase your AudioMoths far in advance of your study, as these purchases are not always open, and the lead time on manufacturing the AudioMoths can be several months.

**Option 2: LabMaker**: For those who can't wait for the next GroupGets purchase, AudioMoth is available at higher prices on LabMaker. Currently the AudioMoth versions available on LabMaker are [AudioMoth v1.2.0](https://www.labmaker.org/products/audiomoth-v1-2-0) and [AudioMoth v1.1.0](https://www.labmaker.org/products/audiomoth-v1-1-0). LabMaker prices are higher because a smaller number of devices are assembled at once, so there is less of an economy of scale.

**Option 3: large-scale PCB manufacturing**: For some versions of the AudioMoth, it may be possible to get AudioMoths at a lower price and larger volumes if you place a large order directly through a PCB manufacturer.

* The PCB manufacturer will create the AudioMoths based off the schematic you provide. The schematic for older versions of AudioMoths (1.0.0 and 1.1.0) has been released publicly. The version 1.2.0 schematic has not been released, so this version cannot currently be purchased through this method. 
* Our lab has had excellent experiences purchasing from [RushPCB](https://rushpcb.com/). We bought the devices pre-assembled (i.e., components connected to boards, battery pack soldiered to board), but without the firmware flashed. We found it easy to flash the firmware in our lab.
* Parts of the original AudioMoth design are constantly going out of stock due to high demand. We enlisted the help of our school's electronics shop to find new parts that were interchangeable with the out-of-stock parts and replace these in the schematic.

## MicroSD cards

The AudioMoth saves recordings on a microSD card. 

### Choose a card

Your card choice will primarily depend on the frequency at which you plan to record.

For recording at sample rates of 48 kHz and below, we typically use SanDisk Ultra 64GB microSD cards. We have found that if using a 64GB card and recording at a 32 kHz sample rate, AudioMoths' storage and battery life run out at approximately the same time.

For recording at sample rates above 48 kHz, we use SanDisk Extreme 128GB microSD cards. These sample rates require SD cards with fast read/write speeds. Files produced with high sampling rate are also larger, so they use up space on the SD card more quickly.  

For more details on microSD card selection, see the Open Acoustic Devices [SD card guide](https://www.openacousticdevices.info/sd-card-guide) for more information.

### Card naming and formatting

You may wish to name or number your cards to organize your data. This is especially helpful for organization during [data upload](#data-upload). This can be achieved by plugging the card into your computer and renaming it. It can also be achieved while reformatting the cards.

Out of the box, microSD cards are typically supplied with one of two file systems: exFAT (for cards larger than 32GB) and FAT32 (for cards 32GB and less). AudioMoth firmware versions 1.2.2 and after can handle either of these formats. However, firmware versions 1.2.1 and before only support FAT32 cards. 

In either case, you might wish to reformat your cards every time they are used, to ensure that the card has no lingering data on it (see "Card usage" below).

If you wish to use an AudioMoth firmware version before 1.2.2, you must reformat your cards to the FAT32 file system. Windows computers cannot natively format cards larger than 32GB to the FAT32 format, but there are [free programs](http://ridgecrop.co.uk/index.htm?guiformat.htm) that allow Windows users to format larger cards. Mac computers can format cards at least up to 128GB; we haven't tested anything larger.

### Card usage

Insert the card into the AudioMoth with the contacts facing **up**, as shown on the graphic on the front of the AudioMoth. (It won't fit any other way.)

![Correct way to insert SD card](images/other/sd-card-position.jpg)

When an SD card fills, the unit will stop saving recordings to it, and the unit's red LED light will stay constantly lit until the SD card is removed.

When reusing a microSD card that has already been deployed, check to make sure that the card is truly empty before reuse:

* On Mac computers, you can check the amount of space remaining on the card using Disk Utility. Deleting files on the microSD card using the graphical user interface does not actually delete them until the trash bin is emptied!
* You can be certain a card is empty by reformatting the card every time you reuse it, or using the `rm` command in the terminal.


## Batteries

### Choose batteries
The battery life depends on the type of battery you use. Check the battery's *capacity* in milliamp-hours (mAh). 

* Lithium AA batteries have a larger capacity than typical alkaline AA batteries, but also cost more. 
* On the AudioMoth, the batteries are connected in series, so their capacities do not add up: the capacity of the three batteries connected in series is equal to the capacity of any single battery.

### Increase battery life
With some electronics expertise you can connect different batteries to the device to increase its battery life. 

* The modified bank of batteries should have a higher *capacity* while maintaining the same *voltage*. For instance, 3 D batteries have the same voltage as 3 AA batteries, but have a higher capacity, so will last longer.
* The *voltage* of batteries connected in series (as they are on the AudioMoth) is equal to the number of batteries multiplied by the voltage of each battery. AudioMoth v1.0 uses 3 batteries at 1.5 volts each, so the voltage of the battery bank is `3 * 1.5V = 4.5V`.
* The *capacity* of batteries in series is the capacity of any one battery in the series. (Don't mix batteries of different capacities, or new and old batteries.) For instance, a Duracell alkaline AA battery has a capacity of 2850mAh.

### Battery usage
Because the AudioMoth doesn’t have an onboard battery, the set time will be lost if a battery is replaced or jostled. On AudioMoth firmwares before 1.5.0, the recording schedule will also be lost as well. Some suggestions to handle this are:

* If you are replacing the batteries of your AudioMoth, use one of the [time setting apps](#set-the-time) to reset the time.
* Take care not to drop or jostle AudioMoths in transit. Reduce the likelihood of batteries being jostled by wrapping painter's tape around the back of the AudioMoth
* While deploying recorders in CUSTOM mode, it will be obvious if a device has lost its time; its red LED will stay lit constantly while its green LED flashes when you try to flip the switch to CUSTOM.
* Bring several extra programmed AudioMoths during deployments, just in case one is dropped and the batteries fall out

### Battery level indication

When the AudioMoth is switched from DEFAULT or CUSTOM mode to USB/OFF mode, the red LED will flash a number of times corresponding to the battery level. There are two scales, one for use with alkaline batteries (default) and one for use with NiMH and LiPo batteries. The latter scale can be used by selecting the "Use NiMH/LiPo voltage range for battery level indication" option in the ["Advanced Settings" tab](#advanced-settings-tab) of the AudioMoth-Config computer app. You can disable this feature in the config app.

On the standard scale, more flashes indicates a higher battery level except when the battery voltage is very low. The battery levels are:

* 4 flashes: >= 4.6 V
* 3 flashes: 4.4-4.5 V
* 2 flashes: 4.0-4.3 V
* 1 flash: 3.6-3.9 V
* 10 rapid flashes: <= 3.5 V; battery voltage too low to reliably record.

On the NiMH/LiPo scale, more flashes indicates a lower battery level:

* 1 flash: >= 4.3 V
* 2 flashes: 4.2 V
* 3 flashes: 4.1 V
* 4 flashes: 4.0 V
* 5 flashes: 3.9 V
* 6 flashes: 3.8 V
* 7 flashes: 3.7 V
* 8 flashes: 3.6 V
* 10 rapid flashes: <= 3.5 V; battery voltage too low to reliably record.

# Firmware

As discussed above, several different firmware versions for the AudioMoth have been created and released. These firmwares often fix bugs and introduce new features: for instance, version 1.4.0 enabled users to trigger AudioMoth recording only when sound exceeds an amplitude threshold. Behavior of the AudioMoth in different firmware versions differs slightly but meaningfully. To see all of the features added or changed in each version of the firmware, view [the release descriptions in the GitHub repository](https://github.com/OpenAcousticDevices/AudioMoth-Firmware-Basic/releases). You can also modify the firmware yourself and apply custom firmware to your AudioMoth.

If you want to flash new firmware to your device, download the application [here](https://www.openacousticdevices.info/flashing). This app allows you to download and apply any of the standard firmware releases released by Open Acoustic Devices (under the "Use Standard Release" tab). If you wish to customize the AudioMoth firmware, you can use the flashing app to apply custom firmware to the AudioMoth as well (under the "Use Local File" tab).

If you encounter problems while flashing your AudioMoth, it may be helpful to use a paperclip to reset your AudioMoth. While the AudioMoth is plugged into a computer in USB/OFF mode with the batteries removed, press a paperclip to the two metal pins on the AudioMoth board that are labeled "PROG." The paperclip should align with the white graphic printed underneath the "PROG" label.

# Create configuration

Before using the AudioMoth, you will typically want to create a custom recording configuration. This involves creating a configuration using the AudioMoth-Config computer app. We have provided some example configurations below. You may save configurations into separate files and reload them from the app. When your configuration is created, plug the AudioMoth into the computer to apply it and set the time on the AudioMoth.

Depending on your needs, you may customize the time of day during which recordings are made, the length of each recording, the amount of time the recorder "sleeps" between each recording, and more. In general, AudioMoths that are recording according to a configuration cycle through recording/sleeping phases within "recording periods" that you have already configured. For instance, you could set the AudioMoth to record a minute-long file every 10 minutes for the first 6 hours after sunset. (But see the information about the [default mode](#default) below, which causes the AudioMoth to start recording immediately).

Download the [Audiomoth configuration app](https://www.openacousticdevices.info/applications) onto your computer to create a custom recording schedule for your AudioMoth. The latest version of the configuration app has three tabs to control different aspects of the recorder configurations: Recording Settings, Schedule, and Advanced Settings. 

For a simple and intuitive graphical introduction to this process, see the [Open Acoustic Devices Config App Guide](https://www.openacousticdevices.info/config-app-guide). The description below includes a few additional details.

## "Recording settings" tab
This tab controls the sample rate of recordings, the gain to be used on the microphone, the length and space between recordings, and a few other settings.

### Sample rate
Set sample rate as 2x the highest frequency you want to record.

* **What sample rate should I use?** You should use a sample rate that is 2x higher than the highest frequency you want to record. This sample rate is known as the [Nyquist rate](https://en.wikipedia.org/wiki/Nyquist_rate) and is the minimum sample rate required to resolve a sound at a particular frequency. For birds, a 32kHz sample rate is fine. For bats' ultrasonic calls, a much higher sample rate is required.

* Sample rates > 192kHz are "experimental"--use with caution.

* Recording at high sample rates requires faster SD cards and takes up more storage space. See the section on [SD cards](#sd-cards-and-batteries) for more information. 

* What is a sample rate, anyway? A microphone captures audio by transforming the sound waves into voltage. Digital audio is recorded by sampling that voltage. The *sample rate* in Hertz is the number of times per second the voltage is sampled. For a helpful introduction to digital audio, check out [this guide](https://web.archive.org/web/20190201094638/https://docs.cycling74.com/max5/tutorials/msp-tut/mspdigitalaudio.html)

### Gain
The gain is the amount that sounds from the microphone will be amplified once recorded. Selecting the optimal gain requires trial and error in your particular field conditions. If the gain is too high, your recordings will [clip](https://en.wikipedia.org/wiki/Clipping_(audio)), creating an unpleasant distortion that can be challenging, if not impossible, to analyze. Alternatively, if the gain is too low, sounds will be faint and hard to hear.

### Sleep-record cycles
In the "Schedule" tab you select the time of day that the AudioMoth should record each day (the "recording period" or periods). However, the AudioMoth doesn't have to record continuously within that time period. You can use a sleep/record schedule to record only a limited amount of time during the scheduled recording period.

* When this feature is enabled, the recorder will create a recording for the number of seconds indicated in "recording duration" and then sleep for the number of seconds indicated in "sleep duration."

* If you do not wish to enable this feature, unclick "Enable sleep/record cyclic recording."
  
* With older versions of the firmware (<1.4.0), to make a single continuous file each recording period, you are not able to disable this feature manually. Instead, you must to set the recording duration length equal to the length of the longest recording period. 
  
* With older versions of the firmware (<1.4.2), you must make sure that your file sizes are less than the WAV file size limit of 4.3GB (4000MB).

* Even if sleep period is set to 0, the device will sleep briefly between recordings to finish saving the previous recording to the card.

### Enable LED
This feature allows you to turn on the LED lights for more information about your AudioMoth, though this might attract more attention from animals/curious humans. Lights are especially useful when testing the recorder. 

In general, when the AudioMoth is in CUSTOM or DEFAULT mode, a red LED means the AudioMoth is recording, a green LED means the AudioMoth is sleeping between recordings, and simultaneous red and green LEDs mean that the AudioMoth recording has failed or will fail in some way. Failures come in two flavors:

1. Constantly lit red LED, flashing green LED: the AudioMoth has a configuration, but the time is not set. 
   * This can be caused by loss of battery power or by configuring the AudioMoth with the "Always require acoustic chime on switching to CUSTOM" option."
   * This can be solved by setting the time using the computer or phone apps (see information about how to [set the time](#set-the-time))
2. Flashing red LED, flashing green LED: the "double flash" means that the AudioMoth has encountered a recording error. This happens in three circumstances:
   * 100ms flash on first switching to CUSTOM mode: no recording schedule has been set. On earlier firmware versions, this would happen if the AudioMoth lost its configuration when its batteries were lost; now, the AudioMoth keeps its configuration even if the batteries are lost.
   * 500ms flash: there is currently a recording failure due to the recorder malfunctioning (e.g. getting wet), the SD card malfunctioning, being full, or not being formatted correctly, or a low battery. This happens in CUSTOM mode when the recorder is attempting to record, or in DEFAULT mode.
   * 10ms flash: there was a recording failure on a previous recording. This happens when the AudioMoth is scheduled to sleep in CUSTOM mode.

The LED also functions to:

* Show acoustic chime progress (see information about the [timesetter mobile apps](#set-time-with-mobile-apps))
* Show battery level (see information about [battery level indication](#battery-level-indication))

For complete information and diagrams of the LED meanings, see [this webpage](https://www.openacousticdevices.info/led-guide)

### Enable low-voltage cut-off

When battery voltage is too low, writing to the microSD card may be inconsistent or unreliable. This option causes the AudioMoth to stop taking recordings when the battery voltage is too low for reliable writing.

### Enable battery level indication

When this option is checked, the AudioMoth indicates its battery level with LEDs when it is switched to USB/OFF mode from either CUSTOM mode or DEFAULT mode. For information about the meanings of these flashes, see the section on [battery level indication](#battery-level-indication). If you are using rechargeable batteries, an option to use a more precise battery level indication is available under the "Advanced Settings" tab.

## "Schedule" tab 

The "schedule" tab lets you set 1-4 recording period(s) in Coordinated Universal Time (UTC) or your local time zone using a 24-hour clock. 

# WARNING: CHECK WHETHER YOU ARE CREATING YOUR RECORDING SCHEDULE IN UTC OR YOUR OWN TIMEZONE! (see below)

Hopefully this warning will catch the eye of anyone quickly skimming this guide. This is one of the most commonly encountered silent failure points of using an AudioMoth. 

Follow the instructions in the next section carefully, or else you may program your AudioMoths to record at the wrong time. It's disappointing to bring your recorders back from 2 months of deployment and realize your "dawn chorus" recordings were actually taken at midnight.

### UTC vs. local time
Instead of referring to a time zone (like Eastern Time, Pacific Time, etc.) recordings on the AudioMoth are scheduled in UTC by default.

**What is UTC?**: UTC is a universal time standard that is used to avoid ambiguity in time zones. UTC is equivalent to Greenwich Mean Time (GMT), but does not observe Daylight Savings time as some countries in the GMT time zone do.

**Can I program AudioMoths in local time?**: Yes, you can use local time instead of UTC to program your devices. To do so, click on the main program menu ("File" at the top left of the app on Windows computers; "AudioMoth-Config" at the top of your screen on Mac computers). There you can toggle the "Local time" setting. 

**When should I use local time?**: Here are some examples of factors to consider.

* Will you or your collaborators deploy your recorders across multiple time zones?
* Do you or your collaborators work in a different time zone than your recorders will be deployed in? 
* Are your collaborators expecting to see the recordings in a certain time zone?
* Will you be creating the recording file in a different time zone than the recording file will be applied to the AudioMoth?

Because our lab works across multiple time zones and using local time introduces ambiguity, we only program our recorders in UTC. However, sometimes we switch on the "local time" option to double-check that we have correctly calculated the time in UTC. You can switch this on to check, then switch it back off before applying it to a recorder.

Note that when a recording is created in local time, even though the filename is in local time, the UTC time at which it was created is still saved to each recording's [metadata](#metadata).

### Recording periods

These are the time each day that the AudioMoth will record. The recording periods will only be adhered to when the AudioMoth is on CUSTOM mode. On DEFAULT mode, the recorder begins recording immediately, without regard to any scheduled recording periods. 

Length of recordings:

* By default, the AudioMoth will make one long recording for each separate period. 
* You can specify a shorter recording length if you turn on sleep/record cyclic recording
* The recordings will be split up if your recording period is so long that the size of the WAV files would exceed the max filesize that can be saved to the microSD card.

Creating recording periods:

* Type in the time for the period start and end in **the correct time zone ([UTC or local time](#utc-vs-local-time))**
* Press "Add recording period" after typing in the desired start/end time of each recording period
* Recording periods will show up on the red/white graphic and the period listing on the right side of the program
* Remove a single unwanted periods either by clicking on the period in the graphic or in the period listing on the right side of the program and clicking "Remove selected period"
* Clear all recording periods by clicking the "Clear all periods" button

The animation below illustrates the steps above (does not appear in PDF):

![Set recording period on AudioMoth configuration app](images/programming/recording-period.gif)

### Select first and last recording date
By default, when the AudioMoth is turned to CUSTOM mode it starts following its recording schedule immediately. When these features are enabled, the AudioMoth on CUSTOM mode will instead start following the schedule on the day you specified and stop recording on the day you specified. 

This is helpful if you want to deploy your recorders in advance of your desired study dates (e.g., if your site is inaccessible on those dates, or if you have a lot of recorders to deploy and want them to start recording simultaneously)

## "Advanced settings" tab

The first two features can be used separately, or combined to create an "amplitude in band triggered recording," popular for capturing bat vocalizations. For more information on these features, see [this document](https://github.com/OpenAcousticDevices/Application-Notes/blob/master/Using_AudioMoth_with_Filtering_and_Amplitude_Threshold_Recording.pdf)

### Filtering
This feature allows you to only record data from a particular frequency band. When you enable filtering, you can choose the following filters. Each allows you to select the frequencies you want to include in the recording. All other frequencies will be filtered out.

* Low-pass: filter out high frequencies
* Band-pass: filter out both high and low frequencies
* High-pass: filter out low frequencies

### Amplitude threshold
This feature causes the AudioMoth to only save audio segments to the file when they contain a sample that exceeds a particular amplitude threshold. This allows you to save on storage by not saving empty files--especially helpful for high-sampling rate files, which are very large. 

The AudioMoth continues to record as scheduled during this mode, but only saves a file to the microSD card when the amplitude threshold is reached. The original length and timing of these recordings can be restored using the "Expand AudioMoth Recordings" option in the [main program menu](#main-program-menu).

This method is primarily intended for animals that call at high frequencies; the high sample rate recordings required to capture these animals' calls take a lot of storage. We would not recommend using this method for animals that call at audible frequencies, where there is a lot of noise that could cause false triggers. Additionally, keep in mind that using triggering limits the applicability of your recordings to other taxa.

### Always require acoustic chime

This option means that an acoustic chime from a phone app is required to start the AudioMoth's recording every time it is initially switched to CUSTOM mode. With this option enabled, upon first switching to CUSTOM mode the AudioMoth will act as if it has no time setting, even if it has not lost its time keeping: its red LED will be lit constantly, its green LED will blink, and it will not start recording on schedule. Playing the acoustic chime will kick the AudioMoth out of this mode and cause the AudioMoth to start recording on its configured schedule. 

This setting could be useful when using the RFCx app. Its chime also gives the recorder a unique deployment ID that will be embedded in the [metadata](#metadata) of every recording. This deployment ID can also be associated with a location in the app. By requiring a chime, you would remember to use the app to set the deployment ID every time.

### Use NiMH/LiPo voltage range for battery level indication

If you are using rechargeable (NiMH/LiPo) batteries, checking this box will change the meanings of the number of LED flashes used in [battery level indication](#battery-level-indication). This scale is apparently more precise.


## Main program menu

Some additional options are available on the main program menu. To access this menu click "File" at the top left of the app on Windows computers; or click "AudioMoth-Config" at the top of your screen on Mac computers. 

* **Open configuration**/**Save configuration**: save or open a saved configuration file (see [below](#save-and-open-configurations))
* **Copy device ID**: every device has a unique hardware ID. When the device is plugged in, this menu option copies the unique device ID. The device ID is saved into the metadata of every recording the device makes, so this can be a helpful way to double-check where a recording was taken.
* **Local time**: program the AudioMoth to keep time in, and save recordings in, local time. For more information, see the section on [UTC vs. local time](#utc-vs-local-time)
* **Expand AudioMoth recordings**: this setting expands recordings made when an AudioMoth uses [amplitude threshold recording](#amplitude-threshold) to restore their original recording length and relative timings. It only applies to recordings with the "T.WAV" suffix.

## Example configurations

Below are links to two example configuration files. Configuration files are composed of structured text that can be viewed in a text editor. The contents of the config file are also displayed below the configuration. 

**Example dawn chorus configuration**: This configuration, [example_bird_config.config](documents/example_bird_config.config), creates a single 3-hour long recording per day between 08:30 UTC (`"startMins":510` = 510 minutes after midnight) and 11:30UTC (`"endMins":690` = 690 minutes after midnight). The AudioMoth is scheduled to begin recording on May 10, 2021 and end recording on July 10, 2021. The recorder's sample rate is set to 32kHz, meaning it will record sounds up to 16kHz. This configuration would be suitable for capturing dawn chorus in much of the northeastern United States. 

If you choose to use this file as a template for your own recording, make sure to change the first and last recording dates.

```
{
"timePeriods": [{"startMins":510,"endMins":690}],
"ledEnabled": true,
"lowVoltageCutoffEnabled": true,
"batteryLevelCheckEnabled": true,
"sampleRate": 32000,
"gain": 2,
"recordDuration": 55,
"sleepDuration": 5,
"localTime": false,
"firstRecordingDate": "2021-05-10",
"lastRecordingDate": "2021-07-10",
"dutyEnabled": false,
"passFiltersEnabled": false,
"filterType": "band",
"lowerFilter": 6000,
"higherFilter": 16000,
"amplitudeThresholdingEnabled": false,
"amplitudeThreshold": 0,
"requireAcousticConfig": false,
"displayVoltageRange": false
}
```
Although this configuration gives values for certain settings like recording and sleep durations for cyclic duty cycle recording, and parameters for a bandpass filter, these settings are turned off (`"dutyEnabled": false` and `"passFiltersEnabled": false`).

**Example bat recording**: This configuration, [example_bat_config.config](document/example_bat_config.config), is set to record between 03:00UTC and 05:00UTC. It cyclically records 55s on and 5s off. It also includes a combination of a 50kHz high pass filter and an amplitude threshold at 512. The amplitude threshold means that only segments of recordings that contain a sample higher than 512 will be saved to the AudioMoth. Because this feature is combined with a high-pass filter that reduces noise in the lower frequencies, loud noise in the lower frequencies will not trigger the recording to be saved to the microSD card. 

I have not tested these settings for the high pass filter and amplitude triggering features; if you choose to use this file as a template for your own configuration, make sure to test and adjust the values for these settings to work for your own use case, and to read the [Open Acoustic Devices white paper about this feature](https://github.com/OpenAcousticDevices/Application-Notes/blob/master/Using_AudioMoth_with_Filtering_and_Amplitude_Threshold_Recording.pdf).

```
{
"timePeriods": [{"startMins":180,"endMins":300}],
"ledEnabled": true,
"lowVoltageCutoffEnabled": true,
"batteryLevelCheckEnabled": true,
"sampleRate": 384000,
"gain": 2,
"recordDuration": 55,
"sleepDuration": 5,
"localTime": false,
"dutyEnabled": true,
"passFiltersEnabled": true,
"filterType": "high",
"lowerFilter": 50000,
"higherFilter": 65535,
"amplitudeThresholdingEnabled": true,
"amplitudeThreshold": 512,
"requireAcousticConfig": false,
"displayVoltageRange": false
}
```

# Set configuration and time

## Save and open configurations

You can save your completed schedule as a file for later reference, reuse, copying, and sharing. These features are accessed through the main program menu ("File" at the top left of the app on Windows computers; "AudioMoth-Config" at the top of your screen on Mac computers). 

To save a configuration:

* Go the main menu
* Click "Save Configuration"
* Save it with a descriptive filename 

To open a saved configuration: Clicking a .config file in your file browser does not open the file in the AudioMoth-Config app. Instead, open the saved program through the configuration app itself.

* Go to the main menu
* Click "Open Configuration"
* Navigate to your .config file and open it.

# WARNING: Bandpass filter added when opening saved configuration

As of 2023 March 04, the newer version of the Audiomoth configuration app changes the way that bandpass filter settings are encoded into configuration files in a way that can cause a **critically important silent failure**. 

If you load a config file created with an older version of the AudioMoth config app, by default the configuration app will add a 4-12khz bandpass filter. Thus, if you open an old config file in a new app--for instance, if you are basing a new config off of one you used before--make sure to check the filter settings and save the config again using the newer app version.

We found when this problem happens in our app, the following warning appeared:


![Warning that appears when loading an old config file into the new config app (Screenshot credit: Chapin Czarnecki)](images/programming/config_app_filter_error.png)



## Apply configuration

After creating your configuration, you will plug the AudioMoth into your computer, and set the current time and desired recording schedule via the app interface.

* Set switch on AudioMoth to USB/OFF mode.
* Plug into computer via microUSB.
* Verify that the AudioMoth is plugged in: the date, time, and recorder information on the programming app will switch from "grayed out" to black.
* Press green "Configure AudioMoth" button in the programming app. This saves the recording program to the AudioMoth, and sets the AudioMoth's internal clock.
* The time that will be shown depends on whether you are using UTC or local time (see [UTC vs. local time](#utc-vs-local-time)).

The AudioMoth now has a custom recording configuration and can be detached from the computer. 

**Why do my AudioMoths count up from 00:00:00, 01/01/1970 UTC when I first plug them in?**: 

* Midnight on January 1, 1970 is called the "Unix epoch." Most operating systems measure time and date as a measure of how much time has elapsed since this time and date. 
* When you first insert batteries into the AudioMoth, it will start counting up from this time and date, so the time the AudioMoth shows when it is plugged into the computer is a measure of how much time the batteries have been your AudioMoth. So, usually you will not see a time of exactly 00:00:00, but instead 
* Watch the time when you first plug your AudioMoth into your computer. If the time starts counting up from exactly 00:00:00, this may indicate that the batteries were not correctly inserted into the AudioMoth, and it never started keeping time. Detach your AudioMoth and check your batteries.

On firmware v1.5.0 and beyond, applying the configuration to the AudioMoth once saves the configuration on the AudioMoth even if the batteries are replaced or jostled. 

## Set the time

The time is automatically set when you set the configuration, unless you select the "Always require acoustic chime on switching to CUSTOM" option in the "Advanced Settings" tab of the configuration app. If that option is selected, or if the AudioMoth is configured but loses time due to batteries being replaced or jostled, the time on the AudioMoth will need to be set. If the AudioMoth is configured but the time needs to be set, the AudioMoth LEDs will have the following flashing pattern: red LED continuously lit; green LED flashing quickly. 

There are three methods of setting the time.

### Set time with computer apps

Either computer app can be used to set the time on an AudioMoth that has lost its time. However, if the AudioMoth was configured with the "Always require acoustic chime on switching to CUSTOM" option, the AudioMoth will require programming by an acoustic chime, even if you set the time with either of these computer apps.

#### AudioMoth-Config app
You can use the configuration app to reset the time. Just be careful: if your desired recording configuration (schedule, sample rate, etc.) is not loaded into the config app when you attempt to reset the time, it will remove your configuration from your AudioMoth!

#### AudioMoth-Time app
Open Acoustic Devices offers a standalone computer-based timesetter app ("AudioMoth Time App" on [this webpage](https://www.openacousticdevices.info/applications)) that allows you to set the time without having the recording configuration loaded.

### Set time with mobile apps

You can set the time using two mobile (phone/tablet) apps that encode date and time in an acoustic signal. AudioMoths can be programmed this way when they enter "acoustic mode," a special mode when the switch is set to CUSTOM where the red LED is lit constantly and the green LED is flashing. There are three ways to enter this mode:

* The AudioMoth is switched to CUSTOM but the time is not set, e.g. due to battery loss
* The AudioMoth is switched to CUSTOM and was configured with the "Always require acoustic chime on switching to CUSTOM" option
* Playing a specific tone (see below) as the AudioMoth is switched from USB/OFF to CUSTOM mode.

We recommend that before you rely on any app in the field, you test it to make sure it behaves as you expect it to, e.g., by programming your AudioMoth then plugging it into your computer to check the set time.

Two apps are available for programming AudioMoths:

The [AudioMoth mobile app](https://www.openacousticdevices.info/mobileapplications) is available for [Android](https://play.google.com/store/apps/details?id=info.openacousticdevices.audiomoth) and [iOS](https://apps.apple.com/us/app/audiomoth/id1530808973). 

* It only resets the time on recorders that are already in acoustic mode; it cannot switch a recorder into acoustic mode, so will not reset the time on any previously-programmed recorders. 
* You can manually force a recorder into acoustic mode by removing the batteries, causing it to lose its set time, and then switching it to custom mode.

The [RFCx Companion app](https://support.rfcx.org/article/65-using-the-companion-app) is available for [Android](https://play.google.com/store/apps/details?id=org.rfcx.companion&hl=en_US&gl=US) only.

* It switches recorders into acoustic mode by emitting a tone at a specific frequency. When you switch the AudioMoth from USB/OFF mode into CUSTOM mode while playing this tone, the AudioMoth is switched into acoustic mode. 
* This acoustic chime also assigns a unique deployment ID to the AudioMoth. We briefly describe this and some of the other functions of this app [below](#rfcx-companion-app).


## CONFIG.txt

In later firmware versions (1.4.0 and on), information about the configuration file is saved to the AudioMoth's microSD card in a file named CONFIG.txt. This allows for easier recordkeeping. 

This file is saved to the microSD card when the AudioMoth is recording in either CUSTOM or DEFAULT mode. Nothing is saved to the card until the AudioMoth is turned on.

Here is an example of a CONFIG.txt file:

```
Device ID                       : 247AA5015C02F90F
Firmware                        : AudioMoth-Firmware-Basic (1.5.0)

Deployment ID                   : 94DB49FDC0B963A6

Time zone                       : UTC

Sample rate (Hz)                : 48000
Gain                            : Medium

Sleep duration (s)              : 5
Recording duration (s)          : 55

Active recording periods        : 1

Recording period 1              : 13:15 - 14:15 (UTC)

Earliest recording time         : ---------- --:--:--
Latest recording time           : ---------- --:--:--

Filter                          : -
Amplitude threshold             : -
Minimum threshold duration (s)  : -

Enable LED                      : Yes
Enable low-voltage cutoff       : Yes
Enable battery level indication : Yes

Always require acoustic chime   : Yes
```

The CONFIG.txt file will be overwritten as new recordings are taken -- so if you change the recording schedule on your AudioMoth but do not replace its card, keep in mind that the CONFIG.txt on the AudioMoth will only refer to the most recently used recording schedule.

The AudioMoth saves CONFIG.txt files even when the recorder is switched to DEFAULT mode. The information in the CONFIG.txt still refers to the recording periods and other settings selected in the custom program applied to the AudioMoth, even though in DEFAULT mode the AudioMoth starts recording without regard to the custom recording periods.


# Recording

## Switch on the recorder

The AudioMoth has a switch on the device for accessing its three modes: USB/OFF, DEFAULT, and CUSTOM.

### USB/OFF
This mode has two purposes.

* USB: When the AudioMoth is plugged into the computer via USB, The switch should also be switched to this mode when plugging the AudioMoth into the computer to apply a recording schedule or update firmware (USB).
* OFF: When not plugged into the computer, the recorder is in a low-power state, but continues to keep time.

### DEFAULT
The DEFAULT mode generally causes the AudioMoth to turn on and start recording immediately. 

* Behavior in DEFAULT mode depends on the firmware version applied to the AudioMoth and whether the AudioMoth has been programmed. 
* Firmware 1.4.2 and after: Record continuously, ignoring sleep/duration settings
  * If AudioMoth has been configured, uses the same sample rate and gain level of the configuration
* Firmware < 1.4.2: Create recordings with sleep interspersed
  * If AudioMoth schedule is configured, uses with the sleep/duration settings of that configuration
  * If AudioMoth schedule is not, record for 10 seconds on, 5 seconds off

### CUSTOM
This is the mode used to record according to the custom configuration.
Note that the switch is fragile and snaps off easily. A slow, careful, and firm touch reduces disappointing switch snapping when turning the AudioMoth on and off. If your switch has snapped, it is possible to [replace the switch slider](https://www.openacousticdevices.info/support/device-support/simple-audiomoth-switch-repair).

The AudioMoth can be turned on in two ways: DEFAULT mode (move switch to the right) or CUSTOM mode (move switch to the left).

* **DEFAULT:** Device immediately starts recording. Recording period/schedule is irrelevant in DEFAULT mode.

  * With firmware versions before 1.4.2, the AudioMoth will take a recording for a desired amount of time, and then will sleep for a desired amount of time. The device repeats this cycle continuously. If the recorder has not been configured with the configuration app, the sleep/record duration settings default to 10 seconds recording - 5 seconds sleeping.

  * Starting in firmware version 1.4.2, DEFAULT mode records continuously, ignoring sleep/duration settings for recording duration time. 

* **CUSTOM:** 

  * If device is turned on outside of the scheduled recording periods, it waits until recording period starts, then begins its recording schedule. 
  
  * If it is turned on during the recording period, it behaves differently based on what firmware is used.
            * With firmware before version 1.4.1, the AudioMoth will not start recording until the next scheduled recording begins. For instance, consider an AudioMoth scheduled to record at 09:00, with a 2-minute recording duration and 2-minute sleep duration. If the AudioMoth was switched to CUSTOM mode at 9:01, it would skip the recording scheduled for 9:00-9:02, and wait until 09:04 to make its first recording.
            * With firmware version 1.4.1 and higher, the recording will be started mid-cycle, rather than waiting for the next cycle to begin.


## Recording troubleshooting

* If a unit's microSD card is full, the unit stops saving recordings. This avoids overwriting previous recordings. In this situation, the unit's red LED light will stay constantly lit until the SD card is removed.

* Turning the AudioMoth off while it is still recording will cause some data loss. This is because the speed at which the data are saved to the AudioMoth lags behind real time. We have found that turning off a recorder while it is recording causes about a 3% loss of data; e.g. a recording that was stopped an hour into the recording will lose 1.8 minutes (60 minutes * 0.03 = 1.8 minutes).

* The first versions of the AudioMoth firmware use filenames with compact representations of the date and time that the recording started. These filenames can be converted to date & time using the instructions in the AudioMoth user manual or using one of several scripts, e.g. [`audiomoth-scripts` by Nathan Wolek](https://github.com/nwolek/audiomoth-scripts). In contrast, the "last modified" time represents the time in UTC that the file was saved, i.e., the time in UTC when the recording ended. More recent firmware saves more easily interpreted filenames.

* The AudioMoth is under continued development. New versions of firmware sometimes change AudioMoth behavior. If your AudioMoth has unexpected behavior, check the [release notes](https://github.com/OpenAcousticDevices/AudioMoth-Firmware-Basic/releases) for the version of the firmware that your AudioMoth was made with and make use of the Open Acoustic Devices Support Forum. (A good rule of thumb is to use the same version of the firmware for all AudioMoths in a given deployment.)

* The expected AudioMoth drift is ~2s per day. This impacts multi-device synchronization for applications such as, e.g., localization. Use of a sound-producing device with known distance that produces sound at a known time of day can be used for rough synchronization.

* Corrosion around the battery terminals can prevent the AudioMoth from recording, or can make the battery voltage appear to be low when the AudioMoth is plugged into the config app, even if the device has new batteries. Use of a pencil eraser can remove corrosion from the terminals.

## How many hours will my AudioMoth record?

The number of hours an AudioMoth will record depends on a combination of the capacity of your batteries, the storage size of your microSD card, the sample rate at which you are recording, and whether or not you are using triggered recording.

The AudioMoth Configuration app will calculate the energy and storage used *per day* once you have specified the recording period and recording/sleep durations. This appears at the bottom of the configuration app in every tab. Your recorder will stop recording either when it uses up all of the storage on the microSD card, or when its battery dies: whichever happens first.

* To refresh batteries and cards as infrequently as possible during multi-month deployments, use a battery/SD card combination where the battery life and card storage run out at roughly the same time, given the device's estimated energy and storage usage. For instance, we use Duracell alkaline AA batteries and 64GB microSD cards. At a 32kHz sampling rate, our storage capacity runs out at about the same time that our recorders' batteries die.

* Use [this code](https://trinket.io/python/ff8aeb66e1) to estimate the number of operational days of a battery and SD card. Input card size and capacity of a single battery (e.g., 2850 mAh for a Duracell alkaline AA battery), plus the config app's estimated and storage and energy usage. For more information on battery capacity, see the section on [batteries](#sd-cards-and-batteries).

* With older versions of the firmware (<1.4.2), you must make sure that your file sizes are less than the WAV file size limit of 4.3GB (4000MB). Current versions of the firmware handle file sizes that are approaching this limit by closing the current file and restarting a new one.

* You can extend your recorder's storage space by using triggered recording (see [Advanced settings information](#advanced-settings)).


## Recording quality and calibration

The Open Acoustic Devices team and several others have tested the recording quality of AudioMoths under a variety of scenarios:

* Open Acoustic Devices introductory document about sound quality: [link](https://www.openacousticdevices.info/audio)
* Audible sound quality tests: on- and off-axis frequency response curves, polar sensitivity charts, comparisons of protective housings, effects of strapping AudioMoths to trees of different sizes by Sam Lapp (Kitzes Lab): [here](https://github.com/kitzeslab/audiomoth-performance).
* Ultrasonic sound quality tests, comparisons to other bat recorders, and assessment of enclosures by Kevin Darras: [link](https://www.openacousticdevices.info/support/device-support/sound-transmission-with-and-without-cases-comparison-with-sm2bat) 

It is important to test recording quality of your microphones before and after each deployment. Why?:

1. AudioMoths are fragile and can fail to record, or have poorer recording quality, when exposed to harsh conditions (e.g. water damage).

2. Microphones tend to degrade in quality over time, especially those subjected to the harsh conditions of bioacoustic recording. These changes can be obvious, such as the mic failing to record or producing static. They can also be more subtle, such as a reduction in sensitivity that makes sounds softer.

3. Firmware versions can also affect sound quality: for instance, in firmware v 1.2.0, a bug caused all of our recordings to have a maximum sound amplitude 25% of what it should have been. 

4. The enclosure and placement of your AudioMoth use can drastically alter the sound recorded. For example, enclosures can reduce sound in certain frequency bands arriving at the microphones, and trees can reduce sound from certain directions or produce artefacts in ultrasonic recordings. Before deploying your recorders, it is recommended to test how your enclosure and field setup affect sound quality compared to an AudioMoth in ideal conditions (not enclosed and not acoustically impacted by its deployment point. Another alternative is to [use an external microphone (instructions here)](https://github.com/OpenAcousticDevices/Application-Notes/blob/master/Using_AudioMoth_with_External_Electret_Condenser_Microphones.pdf), which is possible with newer versions of the AudioMoth hardware (1.2.0 and above).

For information on how to test your AudioMoths, see examples by Sam Lapp in his [AudioMoth Performance Testing report](https://github.com/kitzeslab/audiomoth-performance). Make sure to assess not only the overall decibel level of your recordings, but also whether sensitivity differs over differing frequencies, e.g. by using pink noise playback.


# Enclosures

AudioMoths may break if exposed to water, so it is necessary to house them in a secure, watertight enclosure. This is complicated by the fact that the mic, a MEMS mic, is attached to the circuitboard, although it is possible to [use an external microphone (instructions here)](https://github.com/OpenAcousticDevices/Application-Notes/blob/master/Using_AudioMoth_with_External_Electret_Condenser_Microphones.pdf) with newer versions of the AudioMoth hardware (1.2.0 and above). When the standard MEMS mic is used, the housing must be both watertight and acoustically transparent over the mic.

It is important to know how the enclosure and deployment strategy affects the sound quality. For comparisons, see Sam Lapp's [AudioMoth Performance Testing report](https://github.com/kitzeslab/audiomoth-performance). While we have tested the audio quality of AudioMoths recording in Open Acoustic Devices cases, these results are currently not in the report, as we have gotten some results that differ somewhat from the results reported by Open Acoustic Devices. We're still investigating potential causes of this difference.

## Plastic bags

AudioMoths can be deployed in plastic baggies like Ziploc bags or anti-static bags. Typically the bag should be thick (4mm) and use a zipper seal, not a less robust "slider" seal seen on typical Ziploc bags. Bags can be affixed to trees, poles, or other deployment points using buckling straps or zip-ties.

![AudioMoth deployed on tree in a burned forest (Photo credit: Beth Gardner)](images/housing/ziploc_BethGardner.jpg)

Here are the supplies we use or have used. We aren't affiliated with any of these suppliers. The items available at purchase links can sometimes be switched out (especially on Amazon), so you might want to shop around.

* Our Ziploc bag choice: freezer bag with zipper seal, not slider. Ziploc freezer bags are 3mil thickness. Do not use sandwich bags, which are very flimsy (1.5mil thickness). [Purchase link (Amazon)](https://www.amazon.com/Ziploc-Freezer-Bags-Quart-Total/dp/B07NQVYF72/)
* Desiccant pack: used to soak up lingering moisture in the bag, preventing condensation. We use quite large desiccants (~2x2) [Purchase link (Grainger)](https://www.grainger.com/product/GRAINGER-APPROVED-Desiccant-20TM04)
* Straps: 1" buckle straps are good. Shop around for the best price. [Purchase link (Amazon)](https://www.amazon.com/Magarrow-Luggage-Buckle-Packing-Accessories/dp/B07H1D15LZ/)
* Zip ties: we like 16" long black zip ties. Any zip ties from a local hardware store will do. For camouflaging purposes, black zip ties tend to be less visible against tree bark than white ones. You can string together multiple zip ties, but it's best to aim for smaller-diameter trees.

![An AudioMoth in an anti-static bag, with top folded over to create a loop for a zip tie (Photo credit: Halie Parker)](images/housing/antistaticbag_HalieParker.jpeg)

There are several methods of hanging the AudioMoth:

* Create a loop in the top of the bag using duct tape and thread a zip tie or strap through the loop.
* Loop the bag around a horizontal branch If straps or zip-ties are used
* Attach strap to tree and affix the baggie to the strap using zip-ties
* Sew a fabric pouch for the bagged AudioMoth to sit in that zip-ties to the trie

![An AudioMoth in a fabric bag, attached to a tree with a zip tie](images/housing/fabric_pouch.jpg)

The switch and corners of the AudioMoth v1.0 are sharp and can rip through a plastic bag. More recent AudioMoth designs have rounded corners and an inset switch to reduce this issue. Take steps to prevent moisture getting into AudioMoth enclosure:

* Thicker bags (e.g. the 4mmil plastic baggies described above) will reduce possibility of puncture.
* Avoid transporting AudioMoths within the bags if possible, as the bags are more likely to break. Instead, keep the AudioMoth and bag separated until you are ready to hook the bag to the tree. This is less of a concern for thicker bags (e.g. 4mil thickness).
* Taping over the sharp parts of the AudioMoth, or judiciously applying hot glue, reduces the chance of punctures. 
    * We do not apply anything next to the mic, as we are currently unsure of the effect on the recording quality. Take care not to obstruct SD card insertion or switch movement.
    * [Example with tape by Jennifer Sheridan](https://twitter.com/JenASheridan/status/1047766465900818432)
* Before you walk away from a newly-deployed AudioMoth, inspect the bag for scratches or punctures. Replace if necessary.

## Heat-sealed bags

Ziploc baggies are susceptible to puncture and can be challenging to affix to straps. An alternative to Ziploc baggies is creating an enclosure using a heat-sealed bag. We create these using vacuum sealer with a "heat-seal-only" function, and do not vacuum the air out of the bag itself. (Vacuuming air out of bags would reduce sound quality.)

![Heat-sealed bag](images/housing/heat-sealed.jpg){ width=300px }

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

## Hard enclosures

If rodent chewing, rubbing by deer or bison, or other intrusions are a problem in your deployment area, consider using hard enclosures for your AudioMoths. Hard plastic or acrylic cases should have a hole through which sound can enter. This sound can be covered with a water-resistant acoustic membrane sticker or cloth.


### Open Acoustic Devices enclosure

Open Acoustic Devices sells injection-molded cases through [GroupGets campaigns](https://groupgets.com/campaigns/775-the-official-audiomoth-ipx7-waterproof-case?archived=true&page=1). More information about the cases is available in their [report](https://github.com/OpenAcousticDevices/Application-Notes/blob/master/An_Injection_Moulded_Case_for_AudioMoth.pdf). After clipping the case closed, the pressure within the case takes several hours to equalize.

Note: we have tested the audio quality of AudioMoths recording in Open Acoustic Devices cases and have gotten some results that differ somewhat from the results reported by Open Acoustic Devices. We're still investigating potential causes of this difference.

### Homemade enclosures

In addition, many groups have shared their housing advice on the [WildLabs Acoustic Monitoring forum](https://www.wildlabs.net/community/group/acoustic-monitoring) and Twitter. Some examples:

* [Laser-cut housing by Open Acoustic Devices](https://www.openacousticdevices.info/single-post/2019/04/24/AA-acrylic-laser-cut-enclosure)

* [Tupperware case by Emily Hoffman](https://twitter.com/em_hoffmann/status/1200221472641282048)

* [Tupperware case by Carolina Ocampo](https://twitter.com/CarOcampoA/status/1045013308900868096)

* [Hand-assembled case by Heather Wood](https://www.wildlabs.net/community/thread/554)

* [3D printable case by Robin Jones](https://www.thingiverse.com/thing:3292311)

* [3D printable case by Jon Flanders](https://twitter.com/jonrflanders/status/1084491613068513282) (design not released yet)

* [Hand-assembled case by Ruby Lee](https://www.wildlabs.net/resources/case-studies/trialing-audiomoth-detect-hidden-threats-under-canopies-belize) (design not released; scroll down to see picture)

## Camouflage

![An AudioMoth in a sewn camouflage pouch (Photo credit: Halie Parker)](images/housing/camo_HalieParker.jpeg)

Camouflaging your AudioMoths may help prevent vandalism and theft. Some tips:

* Camouflage fabrics can help reduce the visibility of your AudioMoths, especially when deployed on public lands. Some options are sewing a pouch out of camouflage fabric (sold at fabric stores; see picture above), or covering the AudioMoth in a square of cut-out camouflage blind material (see picture below).
* You might want to use flagging tape to make your AudioMoths easier to find. To avoiding drawing attention to the AudioMoth, you can place the flagging tape a set distance and direction from it, e.g. on a tree 15 meters north of the AudioMoth.
* Be cognizant that black straps stand out against trees. Depending on the color of the tree bark, black zip-ties can be fairly unobtrusive, whereas white ones may stand out.
* If your AudioMoth will be in a well-trafficked area, consider positioning it at a distance from walking trails, facing away from nearby roads or paths, and out of reach of passerby.

![An AudioMoth covered by a square of hunting blind fabric](images/housing/camo_blind.jpg)


# Deployment

"Deployment" is the process of putting recorders out into the field. It might also include other activities like selecting points at which AudioMoths should be deployed, testing AudioMoths after they have been deployed, etc. Below are ideas and important notes to remember about deployments including how to inform the public, record data, safely affix AudioMoths to trees, and more.

## Select deployment positions

### Recorder positioning
Some things to keep in mind when positioning recorders in the field:

* Consider avoiding placing AudioMoths in direct sunlight, as their enclosures may heat up and the sun may wear down plastic, duct tape, camouflage, etc.
* You may want to [camouflage](#camouflage) your recorders. If you are putting your recorders in an area that people walk around in, try to position them so they can't be seen from nearby roads or trails.

Some potential sources of noise or reduced sound quality:

* **Tree size**: If deploying on a tree: the larger the tree is, the more it blocks sound from arriving in all directions. In general, you want a tree that is not huge, but is sturdy enough that the AudioMoth won't be jostled by wind. For example, we quantify the sound impacts of tree diameter here: [AudioMoth Performance Testing report here](https://github.com/kitzeslab/audiomoth-performance).
* **Distance to ground**: Some studies have shown that recorders deployed close to the ground have a smaller hearing radius. If possible, placing AudioMoths at chest height, head height, or even higher can improve sound quality. (And put the recorders out of reach of certain curious animals, e.g. deer, humans)
* **Other biological sound**: Non-target species can be a problem, e.g., frogs heard while recording nocturnal bird migration. Place recorders higher off the ground and investigate methods to reduce noise from other sources.
* **Vegetation**: Vegetation can generally reduce sound quality. If it grows around your AudioMoth, movement of the vegetation in the wind and while scraping against the AudioMoth can cause noise. Keep in mind that vegetation can grow a lot between deployment and retrieval of your AudioMoth.
* **Moving water**: Place AudioMoths out of the hearing range of loud moving, if possible; stream noise will greatly reduce the radius that your AudioMoth can survey.
* **Wind**: Wind can be problematic in open environments. Windscreens may be able to help (see [this thread](https://www.wildlabs.net/community/thread/914) for advice).
* **Voices, roads, and mechanical sound**: Try to anticipate the location and loudness of human-caused sounds like road noise, well pads, chainsaws, hikers, etc.  Sometimes these are unavoidable. Depending on your study, you may want to capture them, too!

![People deploy an AudioMoth several meters above the ground (Photo credit: Beth Gardner)](images/housing/height_BethGardner.jpg)


### Pre-selecting locations
You can use tools like ArcGIS and Google Maps to pre-identify potential locations at which to place your recorders. Lauren Schricker ([website](https://mountainlauren.weebly.com/) - [Twitter](https://twitter.com/mountain_laur)) developed this method of pre-positioning locations of recorders for deployments:

* Log in to your Google account.
* Create a new map: go to https://drive.google.com > New > More > Google My Maps
* Change the base map to "Satellite"
* Click on the "Add Marker" tool and add markers to your map. You might try to target specific locations, for example, identify particular trees that are good candidates for hanging AudioMoths.
    * We name all of our recorder locations with an alphanumeric code that gives the site of the deployments, and a numeric code that uniquely identifies the point at that site. For instance, our deployments at Powdermill Nature Reserve in the pond area are named PNRE-POND-0001, PNRE-POND-0002, etc. 
* Use the "measuring" tool to find even spacing between points (press "Enter" to temporarily save a measurement before you plot your next point)
* If multiple groups of people will deploy recorders, decide beforehand which group will deploy at which points. You can change the color of the point marker on Google Maps to easily see the group divisions.

![Google My Maps](images/programming/google-maps-demo.gif)


## Deployment metadata

We use spreadsheets to track metadata about each AudioMoth that has been deployed. [This spreadsheet](documents/example_deployment_metadata.csv) gives an example of the deployment metadata we track, including:

* AudioMoth and microSD card ID numbers
* Firmware used on the AudioMoth
* The filename  of the configuration file (this is not as necessary anymore, since information about the configuration is saved to the microSD card when the AudioMoth begins recording)
* Name, latitude, and longitude of the point at which the AudioMoth is deployed
* Important notes about placement such as recorder direction, whether the recorder is hidden by shrubs, etc.
* Dates of deployment and pickup
* Dates of other activities like checking in and testing the recorder, date the data were uploaded to a computer, etc.

We also use a "master" spreadsheet to track information about all of the recorders that our lab owns, including:

* ID of recorder (e.g. AudioMoth v.1.2.0 number 0394 has ID M12-0394)
* Model of recorder (e.g. AudioMoth v.1.2.0)
* Firmware version
* Date that the recorder's sound quality was last tested
* Is the recorder retired or lost?

## Written deployment protocols

We usually collect deployment metadata using field data sheets. The document containing the protocols and data sheets we currently use for deployment is available in the following formats:

* [Google document (duplicate to edit)](https://docs.google.com/document/d/1sjiYVt9-nC2Vyr7Qvu2pRacPSWM6B8tl-AOX44OfrOU/edit?usp=sharing)
* [PDF document](documents/deployment_protocol_template.docx)
* [Word document](documents/deployment_protocol_template.docx)


This document covers pre-deployment, field deployment, and post-deployment activities, e.g.:

* How to set up brand new AudioMoths
* Creating recording schedules for AudioMoths
* Putting AudioMoths in sealed housings
* A packing checklist for field deployments
* Field data sheets for deploying, swapping out, or removing AudioMoths from the field
* Uploading microSD card recordings to your computer
* Testing returned AudioMoths

Some tips for using written datasheets in the field:

* Print protocols on Rite in the Rain paper
* Use either pencils or Rite in the Rain brand pens. (Most pens or permanent markers will not write well on wet paper.)
* If you do lots of deployments, keep a master "template" protocol that you modify based on the needs of each deployment

## Electronic deployment aids

A variety of apps are available for collecting data in the field. Some researchers use apps such as [Survey123](https://survey123.arcgis.com/) or [Fulcrum](https://apps.apple.com/us/app/fulcrum-mobile-data-collector/id467758260) to record these data in the field.

We especially like using the [Gaia GPS](https://www.gaiagps.com/) phone app as a complement to a compass and/or GPS receiver for navigating to our data points. This app can import files of locations, e.g. .GPX or .KML files. It also displays downloaded trail maps and elevation gradients even when you are offline.

Two mobile apps are made specifically for setting the time on AudioMoths (see ["Set time with mobile apps"](#set-time-with-mobile-apps) above). One of them, the RFCx Companion app, has additional features useful for tracking deployment metadata:

### RFCx Companion app

You can use the RFCx Companion app to collect metadata about each deployed AudioMoth. These metadata are stored in the cloud and accessible through the RFCx ARBIMON interface. Data you can collect include:

* Name of the deployment site
* GPS coordinates and altitude for the deployment site
* Photos of the deployment site
* Your track, if enabled

This app can also be used to set the time on an AudioMoth:

* It switches recorders into acoustic mode by emitting a tone at a specific frequency. When you switch the AudioMoth from USB/OFF mode into CUSTOM mode while playing this tone, the AudioMoth is switched into acoustic mode. 
* The RFCx companion app's chime feature previously encoded the date and time at which the app was opened, not the current time. This behavior was fixed in later releases--if you downloaded your app before May 2021, make sure to update your app before using it.

The acoustic chime also encodes a unique deployment ID:

* The deployment ID is created and saved while using the app's "Create deployment" feature. It indicates a unique deployment time, date, and location.
* The recorder will save this ID into the "Comments" section of the [metadata](#metadata) of every recording
* The deployment ID is saved to your phone and synced to RFCx's Arbimon interface. It can then be used to identify where the AudioMoth was deployed when it took that recording.

A drawback to this app is that it currently doesn't have an option to write down the AudioMoth ID if you have hand-labeled your AudioMoths with your own ID number. It is expected that only the deployment ID, which is accessible using the RFCx app or Arbimon website, will be used to pair recordings and site location.

## Informing the public

Because acoustic recording could be considered an invasion of privacy, be careful to check local regulations to determine what you have to do to put recorders on your land. For instance, you may have to acquire permits to perform research on the land. 

To legally deploy recording devices on public lands in the United States, you must make a good-faith effort to inform people that recording is occurring. One way to do this is to place signs at all entry points (especially roads, parking lots) that include the verbiage “By proceeding, you consent to being recorded.” An example of a complete sign:

```
Equipment for recording bird vocalizations is in use in this 
area within 3 hours of sunrise. This equipment may incidentally 
record other sounds, including human conversation. By 
proceeding during this period, you consent to being recorded. 
Please contact Jane Doe at jane.doe@university.edu
with questions about this study.
```

You may wish to add a note on or in each recorder housing briefly describing your study and an email address or phone number that curious people can use to contact you for more information. However, it is unclear whether these notes would deter or encourage recorder loss. :-)


## Other tips

### Tips for scaling up

![Two hundred AudioMoth housings made from Ziploc bags](images/housing/bulk-housings.jpg){ width=300px }

* Speed matters when you deploy a lot of recorders: for instance, when deploying 100 recorders, an extra 5 minutes spent per recorder results in 8+ additional hours in the field! Practice and refine your deployment protocol before you go to the field.
* Save time in the field by pre-packing bags with desiccant and pre-attaching them to straps in the lab, instead of performing these tasks in the field.
* It can be helpful to deploy AudioMoths in pairs
    * One person can record data, e.g., the unique ID of the AudioMoth, its SD card, and the point at which it is deployed.
    * The other person can manage putting the AudioMoth on the tree and collecting a more accurate GPS point
* Pre-assign nearby groups of AudioMoths

### Playback, imitation, and voices

Your study might require that you use sound playback or imitations. You might also encounter human voices on your recordings. If you're worried about mistaking these sounds for the actual sounds you are trying to record, here are some options:

* Use playback or imitation only outside the hours of the recording
* Keep a record of the days and times you performed imitations or walked near the recorders, then exclude these recordings from analyses
* Use a distinctive unnatural sound (e.g., a “triple knock” instead of a “double knock”). 
* While using playback/imitation, verbally announce your presence loudly enough that all recorders that could capture your recording can hear your announcement

Make sure anyone using your data is aware of the protocols you used around playback, imitation, and voices. Keep in mind that if you are using automated analysis algorithms, verbal announcements need to be manually confirmed. Unnatural sounds might still be picked up by your algorithm as sounds of interest, e.g., human voices are sometimes mistaken by classification algorithms as animal sounds.

# Data management

## Data upload

Transferring audio files from hundreds of microSD cards is a slow process to do manually. We organize this process by giving each of our microSD cards a unique ID. We then upload large amounts of data at once using one of two pieces of hardware: Raspberry Pi-based card transfer tools called "Swallows" and multi-card SD readers.

### Upload tips

We assign each microSD card has a unique ID number (e.g. 0526). This number is written on the front of the card in Sharpie, but the card is also given a volume name (e.g., MSD-0526) when it is first formatted. These names are then used to organize the audio files copied off of each card.

When microSD cards are all named in this way, the following `rsync` command automatically copies data: 

   `rsync -rhv /Volumes/MSD* --exclude .Spotlight* --exclude .fsevents* --exclude System* /Volumes/seagate/transfer_20200622/`

About this command:

  * The command finds all cards in `/Volumes` named with the prefix "MSD" 
  * These data will be copied to a folder on an external hard drive, `/Volumes/seagate/transfer_20200622`
  * This command excludes some system files created by some operating systems
  * Use the flag `-n` to run a dry-run of this command first!

Before you consider your data transfer complete, check to make sure that all of the expected folders have been created and they are of the expected size and number of recordings.

### Swallows / `picopy`

The method we currently use to transfer microSD cards is a Raspberry Pi-based method. Tutorials and schematics for the Raspberry Pi devices are available in Sam Lapp's [`picopy` repository](
https://github.com/sammlapp/picopy).

These devices, nicknamed "Swallows," enable data from a microSD card connected to the Raspberry Pi to be transferred to an attached external hard drive. Buttons on the Swallow are used to start and stop transfers and eject the drives. LEDs on the Swallow indicate copy status, progress, and any errors encountered. Under the hood, the Swallow's functions are managed by a Python script that kicks off the transfer using Rsync.

If multiple Swallows are built, they can be used to "parallelize" the upload process, simply by having many Swallows uploading data at once!

![Swallow Raspberry Pi device (Photo credit: Sam Lapp)](images/other/swallow.png){ width=300px }

### Multi-port SD reader

Another option is to use a multi-port SD card reader. The photo below shows a network-attached storage device (NAS) with 48 TB of storage, plus a multi-port SD card reader.

We designed a 32-port SD card reader that can be made using supplies purchased from Amazon, the ["hexadecapus"](https://github.com/kitzeslab/sd-transfer/blob/master/Hexadecapus/Hexadecapus%20multi-SD%20reader.pdf). 

Keep in mind that this does not significantly speed up or parallelize the transfer process. It just lets you load multiple cards onto the computer and walk away, without having to insert, upload, and eject cards one at a time.

![Network-attached storage and SD card reader](images/other/nas.jpg){ width=300px }

## Metadata management
It is important to keep track of metadata about the files that were created. 

* The AudioMoth stores metadata about the recording in the "Comments" field of the EXIF metadata. This includes recording date/time, sample rate, recording duration, gain setting, battery level, and AudioMoth serial number. For instance, here is an example metadata record automatically generated by an AudioMoth that was programmed by the RFCx Companion app:

 ```
> exiftool 20210528_131600.WAV
ExifTool Version Number         : 11.30
File Name                       : 20210528_131600.WAV
Directory                       : .
File Size                       : 5.0 MB
File Modification Date/Time     : 2021:05:28 13:16:54-04:00
File Access Date/Time           : 2021:05:28 00:00:00-04:00
File Inode Change Date/Time     : 2021:05:28 13:16:54-04:00
File Permissions                : rwxrwxrwx
File Type                       : WAV
File Type Extension             : wav
MIME Type                       : audio/x-wav
Encoding                        : Microsoft PCM
Num Channels                    : 1
Sample Rate                     : 48000
Avg Bytes Per Sec               : 96000
Bits Per Sample                 : 16
Comment                         : Recorded at 13:16:00 28/05/2021 
                                  (UTC) during deployment 
                                  94DB49FDC0B963A6 at medium gain
                                  setting while battery state was
                                  4.7V and temperature was 22.9C.
Artist                          : AudioMoth 247AA5015C02F90F
Duration                        : 0:00:55
 ```

 * EXIF data can be accessed via [`exiftool`](http://owl.phy.queensu.ca/~phil/exiftool/) on Mac, Linux, and Windows. Once it is installed, open a Terminal window and run `exiftool FILENAME.wav`

* If SD cards get mixed up, this information can be used to recover what unit the recording was made on:
  * By device ID (listed under `Artist`: `AudioMoth 247AA5015C02F90F`). You can access AudioMoth device ID when configuring an AudioMoth in the [main program menu](#main-program-menu)
  * By deployment ID, if you have used the [RFCx Companion app](#rfcx-companion-app) to program the recorder (written in `Comment`: `deployment 94DB49FDC0B963A6`)

* Several metadata standards exist for audio recordings, including [Tethys](https://tethys.sdsu.edu/) and [GUANO](https://guano-md.org/). Recording metadata can be updated to be compliant with these standards using `exiftool`.


# Data analysis

Data analysis techniques vary from completely automated to completely manual. For instance, some software enables automated identification of species vocalizing in recordings. Other software makes it easier to look at, listen to, and organize recordings. Software may be free or paid. 

See [this list](https://github.com/rhine3/bioacoustics-software) for brief descriptions of different data analysis techniques, and a list of softwares available.


## Citing this guide
If you find this guide helpful, please share it! It is available in both [PDF](https://github.com/rhine3/audiomoth-guide/raw/master/guide.pdf) and [Markdown](https://github.com/rhine3/audiomoth-guide/raw/master/guide.md) formats. 

The guide and the other materials in this repository are licensed under [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/). Please feel free to use and modify them with [attribution as described in the license](https://github.com/rhine3/audiomoth-guide/blob/1f9192ac3d41a9a1f7a362bc7471943d0db49380/LICENSE.txt#L210-L259).

You may cite the guide as follows, replacing the `<>` with the DOI in the image at the top of this document.
```
Rhinehart, Tessa A (2021). AudioMoth: a practical  
guide to the open-source ARU. GitHub repository: 
https://github.com/rhine3/audiomoth-guide. DOI: <>
```

If you modify this document and would like to make a .pdf version, you can use `pandoc` on the command line to compile the PDF version from Markdown: `pandoc guide.md -o guide.pdf --variable urlcolor=cyan --variable linkcolor=MediumSeaGreen --template pandoc/template.latex`.

## Acknowledgements

The AudioMoth was developed by [Open Acoustic Devices](https://www.openacousticdevices.info/). Its first description in academic literature can be found in:

```
Hill, Andrew P., Peter Prince, Evelyn Piña Covarrubias, and 
C. Patrick Doncaster. “AudioMoth: Evaluation of a Smart Open 
Acoustic Device for Monitoring Biodiversity and the Environment.” 
Methods in Ecology and Evolution, December 3, 2017.
```

Thank you to Alex Rogers, Sam Lapp, Trieste Devlin, Lauren Chronister, Lauren Schricker, Abram Fleishman, and other members of the AudioMoth and bioacoustics communities who have contributed to this guide. Thank you to Marco González Santoro and Santiago Ruiz Guzman for translating this guide into Spanish.
