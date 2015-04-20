# Theme Park of Everyday

Why hasn’t it been feasible to bring interactive physical vignettes out of engineered spaces like theme parks and into daily life? Theme Park of Everyday explores how the devices in our pockets can augment and control the physical world, for fun. 

With PocketPark (the iOS companion app developed to enable the experience), users are notified when they approach installations. Simply by opening the app, users can wirelessly control installations using mobile device sensors.

Anyone can add new experiences. They automatically appear in PocketPark app when registered.

Theme Park of Everyday depicts how mobile devices can make the world more fun, and how playful physical installations can be easily built and embedded into the city around us.

## Pocket Park iOS

PocketPark enables serendipitous moments of surprise and wonder by enabling your device to control the physical world. Using the frameworks available here and the <a href="http://www.amazon.com/gp/product/B00LU46NLA/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00LU46NLA&linkCode=as2&tag=theparofeve-20&linkId=PS5VC75DSSUOWYEQ">LightBlue Bean</a><img src="http://ir-na.amazon-adsystem.com/e/ir?t=theparofeve-20&l=as2&o=1&a=B00LU46NLA" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />, you can create your own installations as part of the Theme Park of Everyday.


[![App Store](http://themeparkofeveryday.com/images/appstore-small.png)](https://itunes.apple.com/us/app/pocketpark/id975793961)

[Download PocketPark from the App Store](https://itunes.apple.com/us/app/pocketpark/id975793961).

## How it Works

When you're nearby an installation installed out in the world (store window, park, etc.) PocketPark will notify you. When you open the app, you'll be able to control the installation using the sensors in your device.

Sensor information from the iOS device is sent to an installation via Bluetooth Low Energy. The controller is a LightBlue Bean which is a BLE enabled Arduino. Using the Arduino IDE, you can program the Bean to control your installation.

> iOS Device must support Bluetooth Low Energy. iPhone 4S or newer.

The installation you create could be *anything*: a bubble machine controlled by blowing into the device microphone, a fire breathing dragon you wake up by waving at it, or everyone's favorite… LEDs.

You'll find example code to get started below.

# Getting Started

These steps will help you make an installation part of the Theme Park of Everyday.

### Step 1: Choose an Input
How do you want the user to control your installation? Your selection can be playful or logical. On the most basic level, your installation will respond to a range of values delivered in a scratch characteristic to the Arduino.
> **What is a Scratch Characteristic?**

> Characteristics are a Bluetooth convention, a defined attribute types that contain a single logical value single logical value.

##### PockePark Version 1.0 Inputs Available
Version 1 inputs are experiments. It is best to constrain values on your Bean. Future versions will be indicated and may include better averaged and normalized values.


**Microphone Blow**: User blows into the microphone on the device. The harder the user blows, the larger the value delivered to the bean.

>**Mic Value Ranges**: The Bean will receive values between ```-2``` when very quiet and ```200``` when blowing very hard.

[[placeholder for image]]

**Shake**: User shakes the device.

>**Shake Value Ranges**: the Bean will receive ```1``` when a shake is detected

[[placeholder for image]]

**Gyroscope**: User rotates device on Y axis.

> **Gyroscope Ranges**: The Bean will receive values between ```0``` and ```180``` depending on the rotation of the device when it's held in a portrait position.

![Gyro](http://themeparkofeveryday.com/images/gyro.gif)

**G-Force**: User waves device toward the ground rapidly

> **G-Force Ranges**: The Bean will receive values between ```0``` and ```200``` with the average being around 25 for a good force. This one is a little touchy.

[[placeholder for image]]

**Rotation Rate**: User moves device rapidly back and forth

> **Rotation Ranges**: The Bean will receive values between ```0``` and ```50``` with the average being around 20 when rotating semi-rapidly.

[[placeholder for image]]
	
##### Future Device Inputs
Have an idea for a new input?
>[Tweet @PocketPark >](https://twitter.com/PocketThemePark)

### Step 2: Set What Happens
What do you want to happen when your installation gets sensor data from the iOS Device? Use the code examples to control servos, relays, solenoids, LEDs, anything!

**Microphone Blow**

>[Microphone Example >](https://github.com/tomarthur/pocketpark/blob/master/Arduino/microphone_apr03/microphone_apr03.ino)

**Shake**

>[Shake Example >](https://github.com/tomarthur/pocketpark/blob/master/Arduino/shake_apr03/shake_apr03.ino)

**Gyroscope**

>[Gyro Example >](https://github.com/tomarthur/pocketpark/blob/master/Arduino/gyro_apr03/gyro_apr03.ino)

**G-Force**

>[G-Force Example >](https://github.com/tomarthur/pocketpark/blob/master/Arduino/gforce_apr03/gforce_apr03.ino)


### Step 3: Register

[Register your Installation here >](http://installations.themeparkofeveryday.com/new)

**Be sure to write down your Installation ID, and Bean settings. You'll use them to configure your installation.** 

### Step 4: Configure

#### **Install Tools**
If you haven't done so already, you'll need to install the Arduino IDE and the Bean Loader application.

>[Bean Loader OS X >](https://punchthrough.com/bean/getting-started-osx/)

>[Bean Loader Windows >](https://punchthrough.com/bean/getting-started-windows/)

#### **Upload Sketch**
[Follow the steps to program your Arduino sketch to the Bean.](https://punchthrough.com/bean/getting-started-osx/)

<img src="http://themeparkofeveryday.com/images/programsketch.png" alt="Program Sketch Screen" style="
    max-width: 95%;
">


#### **Set Bean Name**
Set the Bean name to match the one provided during the registration step. 

<img src="http://themeparkofeveryday.com/images/setbeanname.png" alt="Program Sketch Screen" style="
    max-width: 95%;
">

#### **Set iBeacon Settings** 
iBeacon technology enables PocketPark to notify users of nearby installations

>```Beacon UUID```: ```0x5441```

>```Major ID```: As provided in registration

>```Minor ID```: As provided in registration

<img src="http://themeparkofeveryday.com/images/beaconsetup.png" alt="Program Sketch Screen" style="
    max-width: 95%;
">


### Step 5: Test 

That's it! Go test your installation. After registration it should be immediately available in the app. Pull down to refresh data if you're not seeing it.


# Troubleshooting

Tweet, post a GitHub Issue or email with questions or if you're having trouble.

> [Tweet @PocketPark >](https://twitter.com/PocketThemePark)

> [Github Issues >](https://twitter.com/PocketPark)

> [Email >](PocketPark@howtomworks.com)

### Can't Find in App
Did you set the Bean name and iBeacon settings as directed in the registration step?

Sometimes iOS caching of Bluetooth device information can make a new Installation not appear in App. Resetting your device can remedy this. 

If not, try using LightBlue to confirm that the Bean name is what you set in the steps above. You may need to set the name again and reset your iOS device to get things working.

### Nothing Happens
Is the LightBlue Bean LED turning green when you contact the Installation in PocketPark? 

If the LED doesn't turn on:
- Does the Bean name match the one provided in the registration step?
- Is your battery fresh?
- Can you connect to the Bean using the LightBlue iOS App?
 
If the LED is green but nothing happens:
- Check your Arduino code and make sure you've set your Installation to respond within the values above for the input you selected.
- Make sure your Arduino code is set with the correct pins for inputs and outputs
- Try testing your Installation using a standard Arduino and Serial input


### Unexpected Behavior
Well, that isn't much fun. You might be having issues with mapping your values. A good method to troubleshoot is to use an existing Arduino and manually control your Installation through the serial monitor. 

# Acknowledgements and License

Theme Park of Everyday is [Tom Arthur's](http://www.howtomworks.com) thesis at the [NYU Interactive Telecommunications Program](http://itp.nyu.edu).

PocketPark is available under the MIT license. See the LICENSE file for details.

Special thanks to:

- Gabe Barcia-Colombo and ITP Thesis Classmates
- [Sakar Khattar](http://www.sakark.com) 
- Robert Scarff
- Parental units
- Everyone who listened to me try to explain this thing
- [Punch Through Design](https://punchthrough.com) - the Bean is awesome!


Open source code included in PocketPark:

- [Bean-iOS-OSX-SDK](https://github.com/PunchThrough/Bean-iOS-OSX-SDK) – MIT license
- [Cool Beans](https://github.com/kyleweiner/Cool-Beans) – MIT license
- [Onboard](https://github.com/mamaral/Onboard) – MIT license
- [IJReachability](https://github.com/Isuru-Nanayakkara/IJReachability) – MIT license
- [JGProgressHUD](https://github.com/JonasGessner/JGProgressHUD) – MIT license
- [MBProgressHUD](https://github.com/jdg/MBProgressHUD) – [License](https://github.com/jdg/MBProgressHUD/blob/master/LICENSE)

Documentation formating:
- [Flatdoc](https://github.com/rstacruz/flatdoc) – MIT license

Arduino examples:
- TBD

Creative Commons Noun Project icons:
- [Signpost Created by Luboš Volkov](https://thenounproject.com/term/signpost/21109/)
- [Radar Created by Pantelis Gkavos](https://thenounproject.com/term/radar/61238/)
- [Light-Bulb Created by Charlene Chen](https://thenounproject.com/term/light-bulb/21901/)
- [Arrow Created by John Caserta](https://thenounproject.com/term/arrow/11200/)

Additional resources utilized:

- [iOS 8 Swift Programming Cookbook](http://shop.oreilly.com/product/0636920034254.do) – Vandad Nahavandipoor – Print ISBN:978-1-4919-0869-3
- [Swift Table View Animations Tutorial](http://www.raywenderlich.com/76024/swift-table-view-animations-tutorial-drop-cards)



