# AudioMoth: a practical guide to the open-source ARU

This guide is intended to be comprehensive for both first-time AudioMoth users and those interested in scaling up their AudioMoth deployment. 

The information here complements official guides on the [Open Acoustic Devices website](https://www.openacousticdevices.info/getting-started). Some technical information about the devices themselves is excluded. We have also elaborated on each step by including images, procedures, and rules of thumb that we've created while deploying hundreds of AudioMoths.

**Jump to:**

* [Quick start](#quick-start)

* [Programming](#programming)

* [Deployment](#deployment)

* [Scaling up](#scaling-up)

* [Data analysis](#data-analysis)

## Quick start

AudioMoths are very easy to set up out of the box. A good general introduction to the AudioMoth is available in the [AudioMoth guide](https://docs.wixstatic.com/ugd/d97703_9ac305905bdd4cdfab6aee99767a56e6.pdf) by Open Acoustic Devices. Our procedure is as follows.

* Purchase necessary supplies, including batteries and SD cards
* [Download](https://www.openacousticdevices.info/config) the timesetter/programming app 
* Create a program as described in detail below
* Insert batteries and SD cards into AudioMoth
* Connect AudioMoth to computer and press green button on configuration app
* Create housings for your AudioMoths
* Devise a field protocol for deployment of the AudioMoths
* Deploy AudioMoths and put up legally required "recording in progress" signs



## Programming

To create a recording schedule for your AudioMoth, you will download a programming app, plug the AudioMoth into your computer, and set the time & recording schedule via the app interface.

For a simple and intuitive introduction to this process, see the [Config App Guide](https://www.openacousticdevices.info/config-app-guide). For more in-depth information, read the steps below.

### Create recording schedule 
Download programming app: https://www.openacousticdevices.info/config

Set up to 5 recording period(s) in Coordinated Universal Time (UTC) using 24-hour clock

   * **What is UTC?**: Instead of referring to a time zone (like Eastern Time, Pacific Time, etc.), recordings on the AudioMoth are scheduled in UTC, a universal time standard. This is done to avoid ambiguity in time zones. UTC is equivalent to Greenwich Mean Time, but does not observe Daylight Savings times as some countries in GMT time zones do.
   
   * Make sure to press "Add recording period" after typing in the desired time of each recording period. Recording periods will show up on the red/white graphic or the period listing on the right side of the program. Likewise, be sure to remove unwanted periods.

<p align="center">
<img src="https://github.com/rhine3/audiomoth-guide/blob/master/images/programming/recording-period-fast.gif" width="50%" alt="Demonstration of setting recording period on AudioMoth configuration app">
</p>

Set sample rate as 2x the highest frequency you want to record

* **What sample rate should I use?** You should use a sample rate that is 2x higher than the highest frequency you want to record. This sample rate is known as the [Nyquist rate](https://en.wikipedia.org/wiki/Nyquist_rate) and is the minimum sample rate required to resolve a sound at a particular frequency. For birds, a 32kHz sample rate is fine. For bats' ultrasonic calls, a much higher sample rate is required.

* Sample rates > 192kHz are "experimental"--use with caution.

* To record at very high sample rates, SD cards with faster read/write speeds must be used. Additionally, recordings at higher sample rates take up much more space on the SD card. We use 128GB SanDisk Extreme cards to record at 192kHz, but see the [SD card guide](https://www.openacousticdevices.info/sd-card-guide) for more advice.

Set amount of gain for recording

* The gain is the amount that sounds from the microphone will be amplified once recorded. Setting this correctly requires trial and error in your particular field conditions. If the gain is too high, your recordings will [clip](https://en.wikipedia.org/wiki/Clipping_(audio)), creating an unpleasant distortion that can be challenging, if not impossible, to analyze. Alternatively, if your gain is too low, sounds will be faint and hard to hear.

Set recording and sleep duration in seconds. After doing this, the program will calculate the energy and storage used each day.

* The programming app shows an estimate of how much storage and energy will be consumed each day. 

    * If your goal is to refresh batteries/cards as infrequently as possible, it is helpful to try to match AA battery capacity (2600 mAh) with SD card capacity. Input your card/battery size and storage/energy usage into [this code](https://trinket.io/python/ff8aeb66e1) to see how long the battery and SD card are estimated to last before filling up.

* Even if sleep period is set to 0, device will sleep briefly between recordings to save the prior recording to the card

* If you only want to make one recording each recording period, set the recording duration to be the same length as the recording period. Note that the maximum file size for any single file is 4GB, so make sure that the size of each individual file is less than 4000 MB.

* AudioMoths alternate between recording and sleeping. When it does this depends on the switch position. If you want to make recordings immediately without regard to the recording schedule programmed on the device, use the DEFAULT mode. For all other deployments with scheduled recording periods, use the CUSTOM mode.

    * **In DEFAULT mode:** Device immediately starts recording for recording duration time, then sleeps, then begins recording again. This repeats until DEFAULT mode is turned off or the recorder dies.
    * **In CUSTOM mode:** If device is turned on outside of recording period, it waits until recording period starts, then begins its recording schedule. If it is turned on during the recording period, it will not start recording until the next recording begins. For instance, if an AudioMoth was scheduled to record at 09:00 for 2min on, 2min off, and was turned on at 9:01, it would skip the recording scheduled for 9:00-9:02, and wait until 09:04 to make its first recording.


Decide whether onboard LED light should be on or off

* **What do the LED lights mean?**  It can be helpful to turn LED lights on for more information about your AudioMoth, though this might attract more attention from animals/curious humans. Lights are especially useful when testing the recorder. LED light meanings are:
    * Only green = sleeping between recordings
    * Only red = recording
    * Both green & red = recording cannot be made. Causes of this include the time or program not being set (while in CUSTOM mode), the batteries falling out at some point after programming (while in CUSTOM mode), the recorder getting wet, the SD card malfunctioning, etc. 
    * Flashing red after turned to USB/OFF: an indicator of battery life (see [official documentation](https://www.openacousticdevices.info/led-guide))

<p align="center">
<img src="https://github.com/rhine3/audiomoth-guide/blob/master/images/programming/sleep-rec-fast.gif" width="50%" alt="Demonstration of AudioMoth configuration app">
</p>

#### Example programs

Below are some example programs. One creates a single 3-hour long recording per day at 32kHz, suitable for recording a bird dawn chorus. The other creates minute-long recordings with minute-long breaks in between, 30 each at two different times. The latter program records at a sample rate of 192kHz, perhaps for recording bat ultrasonic sounds, and will require a fast microSD card.

<p align="center">
<img src="https://github.com/rhine3/audiomoth-guide/blob/master/images/programming/example-programs.jpg" width="100%" alt="Example programs on AudioMoth configuration app">
</p>


### Set time and program on AudioMoth

Install batteries and formatted microSD card in AudioMoth to be programmed. 

* SD cards must be reformatted to MS-DOS (FAT32) prior to each use/reuse. Windows can natively format cards less than or equal to 32GB in size. Mac can format cards up to 128GB; we haven’t tested anything larger.

* Recording with high sampling rate (e.g., recording bats) requires SD cards with fast read/write speeds. Files produced with high sampling rate are also larger, so they use up space on the SD card more quickly. We use SanDisk Extreme 128GB for bat recordings. See the [SD card guide](https://www.openacousticdevices.info/sd-card-guide) for more information.

* The card goes in the AudioMoth with the contacts facing **up**, as shown on the graphic on the front of the AudioMoth. (It won't fit any other way.)

Set switch on AudioMoth to “USB/OFF” mode and plug into computer via microUSB

Verify that the AudioMoth is plugged in: the date, time, and recorder information on the programming app will go from greyed out to black.

Press green button in the programming app. This saves the recording program to the AudioMoth, and sets the AudioMoth's internal clock to your computer's time in UTC.

The AudioMoth now has a CUSTOM recording schedule. When ready to deploy, switch AudioMoth switch to CUSTOM.

* This custom schedule can be saved and reused. However, on some platforms, clicking the saved file itself will not correctly open the program. Instead, open the saved program through the timesetter app by selecting the menu option AudioMoth > Open Configuration

Because the AudioMoth doesn’t have an onboard battery, if the batteries fall out, the programming and set time will be lost. **The AudioMoth must be reprogrammed if the batteries fall out.**

* If turned to DEFAULT mode after the batteries come out, the device will record at default settings (10s on, 5s off)

* If turned to CUSTOM mode after the batteries come out, the device **will not record**.



### Flash firmware

Several different firmware versions for the AudioMoth have been created and released. Some releases are just updates, but some have special functionality; for instance, allowing the AudioMoth to trigger recording only when a sound of interest is heard.

If you want to flash new firmware to your device, follow the guide [here](https://www.openacousticdevices.info/flashing).


## Deployment

"Deployment" is the process of putting recorders out into the field. Below are ideas and important notes to remember about deployments, including how to inform the public, record data, safely affix AudioMoths to trees, and more.

### Informing the public

* To legally deploy recording devices on public lands in the United States, you must make a good-faith effort to inform people that recording is occurring

* Place signs on all entry points (especially roads, parking lots). Signs must include the verbiage “By proceeding, you consent to being recorded.” An example of a complete sign:

```
Equipment for recording bird vocalizations is in use in this 
area within 3 hours of sunrise. This equipment may incidentally 
record other sounds, including human conversation. By 
proceeding during this period, you consent to being recorded. 
Please contact Justin Kitzes at justin.kitzes@pitt.edu 
with questions about this study.
```

* Another idea is to add a note on each recorder with information about the study, though it’s unclear whether these notes would deter or encourage recorder loss.

### Housings

<img src="https://github.com/rhine3/audiomoth-guide/blob/master/images/housing/bag-housing.jpg" width="30%" align="right" alt="AudioMoth deployed on tree">

* AudioMoths can be deployed in ziploc baggies using buckling straps

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

* Create a packing list to make sure you have a few essential tools. [Example](https://github.com/rhine3/audiomoth-guide/blob/master/documents/packing-list.md)

* If you’re also using playback or imitation to survey the area, make sure these sounds can’t be mistaken on the recordings for actual birds. This can be avoided by using playback or imitation only outside the hours of the recording, using a distinctive unnatural sound (e.g., a “triple knock” instead of a “double knock”), or verbally announcing your presence so that any recorders that may capture your recording can hear your announcement 

* The first versions of the AudioMoth firmware use filenames with compact representations of date & time. To find the date and time a file was created, either look at the “last modified” time (which represents the time in UTC that the file was saved, i.e., the time at the end of the recording) or convert the filename using the instructions in the AudioMoth user manual


## Scaling up

For large deployments, special considerations must be taken into account. If you're deploying 100 recorders, an extra 5 minutes spent per recorder means spending over 8 more hours in the field!

### Purchasing AudioMoths

* While GroupGets purchases are helpful for folks looking to buy on the scale of a few dozen AudioMoths, we have found it significantly less expensive to purchase recorders in bulk (e.g., for several hundred recorders, 30-40 USD per recorder instead of 50 USD on GroupGets).

* Our lab has had excellent experiences with [RushPCB](https://rushpcb.com/). We purchased the devices pre-assembled (i.e., components connected to boards, battery pack soldiered to board), but without the firmware flashed. We found it easy to flash the firmware in our lab.

* Parts of the original AudioMoth design are constantly going out of stock due to high demand. We enlisted in the help of our school's electronics shop to find new parts that were interchangeable with the out-of-stock parts.


### Pre-select recorder locations

Lauren Schricker ([website](https://mountainlauren.weebly.com/) - [Twitter](https://twitter.com/mountain_laur)) developed this method of pre-positioning locations of recorders for deployments.

* Login to your Google account 

* Create a new map: go to https://drive.google.com > New > More > Google My Maps

* Change the base map to satellite

* Click on the "Add Marker" tool and add markers to your map. You might try to target specific locations, e.g. particular trees that are good candidates for hanging AudioMoths.

    * We name all of our recorder locations with an alphabetical code that gives the site of the deployments, and a numeric code that uniquely identifies the point at that site. For instance, our deployments at Powdermill Nature Reserve in the pond area are named PNRE-POND-0001, PNRE-POND-00002, etc. 

* Use the "measuring" tool to get even spacing between points (press "Enter" to temporarily save a measurement before you plot your next point) 

<p align="center">
<img src="https://github.com/rhine3/audiomoth-guide/blob/master/images/programming/google-maps-demo.gif" width="100%" alt="Demonstration of Google My Maps">
</p>

* Access the map data on your phone (if you have cell phone service):

    * Download the "Google Maps" app to your phone
    
    * In the app, select the menu from the left side > Your places > Maps

* Upload the map file onto your GPS unit:

    * Click the three dots next to the map name > Export to KML/KMZ > click checkbox for "Export to a KML file"

    * Download [GPSBabel](https://www.gpsbabel.org/download.html), a free converter you can use to convert KML files to the type of file required by your GPS unit
        
    * Select "Google Earth (Keyhole) Markup Language" as the input type, use the file browser to select your file
    
    * Convert the map to the format required by your GPS unit. For instance, Garmin GPS units require a GPX file, so select output format "GPX XML"
    
    * Use the instructions for your device to transfer the map onto your GPS unit (for instance, here are the [instructions for our device](https://www.youtube.com/watch?v=PdPgse1tHdY))

* When need to move a point in the field (e.g., the tree you wanted to use fell down), either reset the location of the point or make a new point on your GPS. Make sure to indicate in your field notes whenever the pre-set location of the point was changed. 

    * Most commercial GPS units are imprecise, especially under heavy foliage, so it can be challenging to know when you’re at the right point. When in doubt, take notes, and take another GPS point to compare later

    * Practice using the crucial features of your GPS unit before you head out to the field, and bring extra batteries

* After you return, follow these steps in reverse order to record the actual locations of your devices.


### Logistics


<img src="https://github.com/rhine3/audiomoth-guide/blob/master/images/housing/bulk-housings.jpg" width="30%" align="right" alt="200 AudioMoth housings made from Ziploc bags">

* Before heading out to the field, pre-pack bags with desiccant and pre-attach them to straps. This saves time and prevents headaches in the field

* It is very helpful to have two people in the field
  * One person can record data, e.g., the unique ID of the AudioMoth, its SD card, and the point at which it is deployed.
  * The other person can manage putting the AudioMoth on the tree and collecting a more accurate GPS point

* Since so many recorders will be deployed, information about their identity and location has to be taken accurately and efficiently
    * Record the deployment date; information about the identity (ID number) of the AudioMoth, SD card, and location; any important notes about placement, etc.
    * See the previous section about pre-positioning recorder locations and ideas for location naming conventions.
   
* Protocols can help make the whole process faster. Here are some example protocols we use.
    
    * [Packing for a deployment](https://github.com/rhine3/audiomoth-guide/blob/master/documents/packing-list.md)
    * [Deploying recorders](https://github.com/rhine3/audiomoth-guide/blob/master/documents/deployment-protocol.pdf)
    * [Bringing recorders home](https://github.com/rhine3/audiomoth-guide/blob/master/documents/return-protocol.pdf)
    * [Post-field checklist](https://github.com/rhine3/audiomoth-guide/blob/master/documents/post-field-checklist.md) (which references the document below)
    * [Checking in data written down in the field](https://github.com/rhine3/audiomoth-guide/blob/master/documents/post-field-protocol-template.pdf) - [an example](https://github.com/rhine3/audiomoth-guide/blob/master/documents/post-field-protocol-example.pdf)
 
* When writing down data in the field, use waterproof paper and permanent pens (e.g., fine-tipped Sharpies)

<img src="https://github.com/rhine3/audiomoth-guide/blob/master/images/other/nas.jpg" width="40%" align="right" alt="Storage and SD card reader">

* Transferring audio files from hundreds of SD cards is a slow process to do manually. Instead, we've developed a 48 TB Network Attached Storage (NAS) device with a 24-port microSD card reader (see photo), plus a script to automatically copy audio files from all the SD cards onto the NAS.

  * Each SD card has its number (e.g. 0526) written on the front of the card in Sharpie, but is also given a volume name (e.g., MSD-0526) when it is first reformatted to FAT32. These names are then used to organize the audio files copied off of each card.


## Data analysis

We have developed a free, open-source audio classifier, [OpenSoundscape](https://github.com/jkitzes/opensoundscape), for analysis of data using machine learning. OpenSoundscape can either predict what species makes each vocalization, or sift through large amounts of negative data to find focal species.
