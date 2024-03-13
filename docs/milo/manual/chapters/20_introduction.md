# Introduction

Take a deep breath for a second and realize something.

You... yes **YOU**, are about to commit to building a robot that can cut through metal, let alone your squishy human parts.
A machine that can easily electrocute you, cut you or set fire to your whole neighborhood if it's not given the respect it deserves.

**Please** give this machine the respect it deserves !!!

!!! warning

    Please follow the manual to the letter and perform any additional research you deem necessary before attempting to use Milo for the first time.

    If there is anything, and we mean _anything_ that you are curious or unsure about, you are more than welcome to ask us on our discord server.

    After all, you are special to us and we don't want you to get hurt.

Most importantly from everyone at the Millennium Machines design team,
Have fun building your very first Milo!

---

## What To Expect

This manual and associated firmware is for the Milo V1.5 with a Mellow Fly CDYv3 control board installed in the internal electronics enclosure found in the machine base.

This manual will not cover external enclosures or the electronics compartment found in the Millennium Machines Casa enclosure - but where possible, it can still be used as a guideline for those other setups.

The firmware used in this manual will only consist of the basic 3-axis functions of the machine.

Touch probes, additional relays, toolsetters and other related add ons will not be part of this base firmware and therefore will not be present in this manual.

## RepRapFirmware

RRF is typically considered a 3D printing firmware, but in the last few years has begun to see more and more CNC features implemented.

RRF boards tend to operate over WiFi or Ethernet and do not stream gcode over the air, but rather load it onto the board before starting a machining operation. Keep this in mind when finding a place to store Milo, as you will need some form of connection to the control board to allow working with the machine itself.

RRF is extremely control board agnostic, so for the most part firmwares can be shared between different control boards with only a few pin definitions needing to be changed.

Pins in RRF act a little differently from firmwares like Klipper and Marlin, as almost all pins are given a pin number (ex PC_7)
and a pin name (ex Xmin). It is generally the pin name that will be referenced in the firmware and not the pin number, meaning that Xmin on one control board will also be Xmin on others. Keep this in mind if you want to use a different control board from the one found in this manual.

It is still a good idea to cross reference these pins before changing any settings in firmware, and most control boards will come with a table similar to the one found [here](https://teamgloomy.github.io/fly_cdyv3_pins.html) - use this table in combination with a pinout diagram of your board to ensure everything will work as expected.

*[RRF]: RepRapFirmware

## Bill of Materials

Provided [here](../../bom/sourcing_guide.md) is the bill of materials. Whilst we recommend that you try to stick to this list as much as possible, you're an adult (hopefully) and this is your machine. If there is a substitution that you think would lead to a better machine then feel free! If there is a feature you don't feel is necessary then don't buy the parts for it.

Furthermore, there are options in the guide that are up to you to decide on, such as drivers, motors and even control boards. Do your research and find what you need to make your build work for you.

## Spindle Selection

Milo supports 2 sizes of round spindle - 80mm or 65mm. These cover the 2 most common spindle sizes for a DIY mill of this type. In terms of what you're looking for when buying a spindle, you'll want a minimum of 800w of power.

You can then decide how you want to control your spindle - the simplest types are router style spindles which use a switch and or selector knob for manual control of speed and direction. The most complex but also most powerful way involves using a Spindle and VFD combination. With this setup you have more granular control over your settings, and can use outputs on your control board to control the spindle itself.

!!! note
    There are too many styles of spindle to realistically account for, so if the spindle mount doesn't support your spindle then design a new one and send it our way and we may include it as an official user mod!

## Parts List and Printing Guidelines

The Millennium Machines team has provided a printing list with settings for you as a guideline for printing the parts necessary for the build. This list can be found [here](../../printing/print_guide.md).

Remember, these settings are only a guideline, and are open to your own interpretations - but we do highly recommend following them to achieve the best mechanical properties for each individual part.

## T-Nuts Application

This machine requires an immense amount of T-nuts. In the interest of simplifying this manual, we have chosen to omit the installation of T-nuts. Wherever a part interfaces with an extrusion in a way that looks like it requires a T-nut, then it should be considered a part that requires a T-nut.

## Linear Rail Carriages

Linear rail carriages use small ball-bearings to glide smoothly along the profile in the rail. If any of your carriages feel 'gritty' when moving, you should remove the carriages from the rail and give them a good clean with contact cleaner, brake cleaner or another similar non-corrosive degreaser.


You must make sure that your carriages are appropriately greased before running your machine. Liberal application of EP2 grease to the carriages will do the trick.

!!! warning
    Use a [dummy rail](https://github.com/MillenniumMachines/Milo-v1.5/tree/main//STL%20Files/Tools/Dummy%20Rail.stl) when removing carriages from the rail. _Searching for tiny ball-bearings when they go bouncing around your garage is not an experience we would like you to share!_

!!! tip
    Turn each rail upside down and put a carriage directly over one of the screw holes. You can then use a small syringe to inject grease directly into the carriage. When you start to see grease coming out along the rails you're done.

---

## Pre-Build Training

Before you head out on your journey to create skynet, it's probably a good idea that you learn a few things. Luckily the Millennium Machines team have put together a curated list of videos to teach you all you need to know - sit back, relax and enjoy.

<div class="annotate" markdown>
- [How to lubricate your motion system](https://youtu.be/UYvhYjkBFTY?si=sulP966B3b0GDdSj)
- [How to use heat set inserts](https://www.youtube.com/watch?v=cyof7fYFcuQ&list=PL7zrGeKp_8CTDOmpwZr5JnCSJqEghFh9j&index=32)
- [Bluing is highly recommended for non-stainless steel linear rails only](https://youtu.be/p6Id4Kl8RB0?si=NPgrowcaCaDVQcHR)(1)
- [How to get started with RepRap firmware on a Fly board](https://www.youtube.com/watch?v=TAT532vIVzU)
- [CNC basics](https://youtu.be/YBGqknN3gGs?si=ds4zdG03RDS3XUv7)
- [Electronics connectors and how to use them](https://www.youtube.com/watch?v=y6G_MhQFv3k)
- [Cable chains and how not to use them](https://www.youtube.com/watch?v=_HiuY015rOY)
</div>
1. Cold bluing stainless steel, while technically possible, is performed primarily for aesthetic reasons. The cold bluing process does not significantly change its corrosion resistance or any other inherent physical property.

---

## CONTACT US

Building Milo can be confusing, but we're here to help. Please join our community using the links on the [Contact Us](../../../contact-us.md) page to ask for assistance, or if you want to share a modification, chat with other Milo owners or simply show off your build!

---

[Next Chapter: Hardware reference](./30_hardware_reference.md)
