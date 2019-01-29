# AudioMoth Guide

In the past year of using AudioMoths, our lab (the Kitzes Lab at the University of Pittsburgh) has learned quite a lot about them through trial and error. This practical guide serves as a repository for everything we've picked up about using them.

TODO: how to partition info between the AudioMoth guide and this guide? reproduce all info? The pictures and animations on the AudioMoth guide are helpful, though--should we add those?

## Quick start

AudioMoths are very easy to set up out of the box. The steps in general are described in the [AudioMoth guide](https://docs.wixstatic.com/ugd/d97703_9ac305905bdd4cdfab6aee99767a56e6.pdf). Our procedure is as follows:

* Purchase necessary supplies, including batteries and SD cards
* [Download](https://www.openacousticdevices.info/config) the timesetter/programming app 
* Create a program; this is explained with graphics on the [AudioMoth Config App guide](https://www.openacousticdevices.info/config-app-guide), and in detail in the "Programming how-to" section below.
* Insert batteries and SD cards into AudioMoth
* Connect AudioMoth to computer and press green button on configuration app
* Create housings for your AudioMoths
* Devise a field protocol for deployment of the AudioMoths
* Deploy AudioMoths and put up legally required "recording in progress" signs



## Programming how-to


Download programming app: https://www.openacousticdevices.info/config

Set recording periods in Coordinated Universal Time (UTC) using 24-hour clock

* **What is UTC?**: Instead of referring to a time zone (like Eastern Time, Pacific Time, etc.), recordings on the AudioMoth are scheduled in UTC, a universal time standard. This is done to avoid ambiguity in time zones. UTC is equivalent to Greenwich Mean Time, but does not observe Daylight Savings times as some countries in GMT time zones do.

Set sample rate as 2x the highest frequency you want to record

* **What sample rate should I use?** You should use a sample rate that is 2x higher than the highest frequency you want to record. This sample rate is known as the [Nyquist rate](https://en.wikipedia.org/wiki/Nyquist_rate) and is the minimum sample rate required to resolve the highest frequency. For birds, a 32kHz sample rate is fine. For bats' ultrasonic calls, a much higher sample rate is required.

* Note that for high sample rates, SD cards with faster read/write speeds must be used. See the [SD card guide](https://www.openacousticdevices.info/sd-card-guide) for more information.

Set amount of gain for recording.

Decide whether onboard LED light should be on or off

* **What do the LED lights mean?**  It can be helpful to turn LED lights on for more information about your AudioMoth, though this might attract more attention from animals/curious humans. Lights are especially useful when testing the recorder. LED light meanings are:
  * Only green = sleeping between recordings
  * Only red = recording
  * Both green & red = recording cannot be made. Causes of this include the time or program not being set (while in CUSTOM mode), the batteries falling out at some point after programming (while in CUSTOM mode), the recorder getting wet, the SD card malfunctioning, etc. For more information, see the [AudioMoth manual](https://docs.wixstatic.com/ugd/d97703_9ac305905bdd4cdfab6aee99767a56e6.pdf)


Set recording and sleep duration in seconds. After doing this, the program will calculate the energy and storage used each day.

* AudioMoth will alternate between recording and sleeping within each recording period. 

* Even if sleep period is set to 0, device will sleep briefly between recordings to save the prior recording to the card

* If you only want to make one recording each recording period, set the recording duration to be the same length as the recording period. Note that the maximum file size for any single file is 4GB, so make sure that the size of each individual file is less than 4000 MB.

* AudioMoths alternate between recording and sleeping. When it does this depends on the switch position. If you want to make recordings immediately without regard to the recording schedule programmed on the device, use the DEFAULT mode. For all other deployments with scheduled recording periods, use the custom mode.

  * In DEFAULT mode: Device immediately starts recording for recording duration time, then sleeps, then begins recording again. This repeats until DEFAULT mode is turned off or the recorder dies.
  * In CUSTOM mode: If device is turned on outside of recording period, it waits until recording period starts, then begins its recording schedule. If it is turned on during the recording period, when a recording is scheduled, it sleeps for the length of the scheduled recording, then starts recording after. For more information about how recordings are scheduled, see the configuration code here.

Install batteries and formatted microSD card in AudioMoth to be programmed. 

* SD cards must be reformatted to MS-DOS (FAT32) prior to each use/reuse. Windows can natively format cards less than or equal to 32GB in size. Mac can format cards up to 128GB; we haven’t tested anything larger.

* Recording with high sampling rate (e.g., recording bats) requires SD cards with fast read/write speeds. Files produced with high sampling rate are also larger, so they use up space on the SD card more quickly. We use SanDisk Extreme 128GB for bat recordings. See the [SD card guide](https://www.openacousticdevices.info/sd-card-guide) for more information.

Plug in AudioMoth with switch set to “USB/OFF” mode, and press green button in the programming app to set time and recording program. 

The AudioMoth now has a CUSTOM recording schedule and CUSTOM should be selected on the AudioMoth switch to use this schedule.

Because the AudioMoth doesn’t have an onboard battery, if the batteries fall out, the programming and set time will be lost. **The AudioMoth must be reprogrammed if the batteries fall out.**


## Programming tips

* The programming app shows an estimate of how much storage and energy will be consumed each day. If your goal is to refresh batteries/cards as infrequently as possible, it is helpful to try to match AA battery capacity (2600 mAh) with SD card capacity.

* Recording 3hr/day at 32kHz sampling rate, a 64GB card and regular AA batteries both last ~7 weeks, needing replacement at approximately the same time.

## Deployment tips

### Informing the public

* To legally deploy recording devices on public lands in the United States, you must make a good-faith effort to inform people that recording is occurring

* Place signs on all entry points (especially roads, parking lots). Signs must include the verbiage “By proceeding, you consent to being recorded.” An example of a complete sign:

      Equipment for recording bird vocalizations is in use in this area within 3 hours of sunrise. This equipment may incidentally record other sounds, including human conversation. By proceeding during this period, you consent to being recorded. Please contact Justin Kitzes at justin.kitzes@pitt.edu with questions about this study.

* Another idea is to add a note on each recorder with information about the study, though it’s unclear whether these notes would deter or encourage recorder loss.

### Housings

* AudioMoths can be deployed in ziploc baggies using buckling straps. [Example by Lauren Schricker](http://www.kitzeslab.org/first-major-deployment/)

* If the strap is too small for the circumference of the tree, attach another strap

* If possible, avoid placing AudioMoths in direct sunlight, as their enclosures may heat up

* AudioMoths may break if exposed to water. The switch and corners of the AudioMoth are sharp and can rip through a ziploc bag. Take steps to prevent moisture getting into AudioMoth enclosure:
  * Don’t transport AudioMoths within the bags, as the bags are more likely to break. Instead, keep the AudioMoth and bag separated until you are ready to hook the bag to the tree
  * Inspect each bag after it is deployed; if there are any scratches or punctures, replace it
  * Use freezer bags, not sandwich bags
  * Taping over the sharp parts of the AudioMoth, or over the bag, reduces the chance of punctures. Take care not to cover the mic. [Example by Jennifer Sheridan](https://twitter.com/JenASheridan/status/1047766465900818432)
  * Include a desiccant pack in the bag to soak up lingering moisture in the bag, preventing condensation


### Hardware

* Because the AudioMoth doesn’t have an onboard battery, if the batteries fall out, the programming and set time will be lost; if you have programmed a CUSTOM recording schedule it is no longer on the AudioMoth and will require reprogramming. We take care not to jostle AudioMoths in transport, and we always bring several extra programmed AudioMoths with us during deployments, just in case we drop one and the batteries fall out. 

* The switch is fragile and snaps off easily. Be careful when turning the AudioMoth on and off, applying pressure closer to the base of the switch 


### Logistics

* Create a packing list to make sure you have a few essential tools. A roll of duct tape or a pair of scissors can save the day. We will gladly share our packing list if requested.

* If you’re also using playback or imitation to survey the area, make sure these sounds can’t be mistaken on the recordings for actual birds. This can be avoided by using playback or imitation only outside the hours of the recording, using a distinctive unnatural sound (e.g., a “triple knock” instead of a “double knock”), or verbally announcing your presence so that any recorders that may capture your recording can hear your announcement 

* The first versions of the AudioMoth firmware use filenames with compact representations of date & time. To find the date and time a file was created, either look at the “last modified” time (which represents the time in UTC that the file was saved, i.e., the time at the end of the recording) or convert the filename using the instructions in the AudioMoth user manual


## For large deployments


### Placing AudioMoths

* When even spacing (e.g. a recorder every 200m) or a specific recorder placement is desired, pre-select and pre-load GPS points onto your GPS device

* Use satellite imagery to identify specific trees on which to deploy AudioMoths. 

* If in the field you are unsure that you are at the correct preselected tree, or if the point must be moved due to inaccessible or poor-quality trees, use your GPS unit to reposition the point. Upload the corrected points when you return from the field. 

* Practice using the crucial features of your GPS unit before you head out to the field, and bring extra batteries

* Most commercial GPS units are imprecise, especially under heavy foliage, so it can be challenging to know when you’re at the right point. When in doubt, take notes, and take another GPS point to compare later

### Logistics

* Before heading out to the field, pre-pack bags with desiccant and pre-attach them to straps. This saves time and prevents headaches in the field

* It is very helpful to have two people in the field
  * One person can record data, e.g., the unique ID of the AudioMoth, its SD card, and the point at which it is deployed.
  * The other person can manage putting the AudioMoth on the tree and collecting a more accurate GPS point

* Since so many recorders will be deployed, information about their identity and location has to be taken accurately and efficiently
    * Record the deployment date; information about the identity (ID number) of the AudioMoth, SD card, and location; any important notes about placement, etc.
    * See here for an example data sheet with recommended information to gather for a deployment, and here for an example data sheet with information to gather for a return
    * Use waterproof paper and permanent pens (e.g., fine-tipped Sharpies)

