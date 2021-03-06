[Home](/index.md)   >   [Tips&Tricks](/tips.md)   >   [Calibration](/calibration.md)

## Method 1 🏆 (aka Calibration App):
>If your S7E battery is not giving you the SOT you were hoping for then you have not properly calibrated the battery. <br/>
>You should try this method, which calibrates automatically, using Lukas's method <br/>

<ol>
        <li> First thing to do is do NOT use a Custom Kernel as this can make matters worse. <br/> Install/Keep a Stock ROM and Kernel on your phone. </li>
        <li> Discharge to ~5%, run the calibration app. </li>
        <li> The battery percentage is now expected to go up at this point. </li>
        <li> Keep discharging to 5% and using the app until the battery percentage does not change! </li>
        <li> Power off your device. </li>
        <li> Now you can charge your device to 100% / until the green light appears </li>
        <li> When the device is fully charged, **unplug the charger** and run the calibration app. </li>
        <li> If the battery percentage drops, repeat steps 5 - 8. </li>
</ol>

## Method 2 🏆 (aka Lukas0610's Method):
> This method will calibrate your battery on any kernel, even the stock samsung kernel. <br/>
It has been tested by multiple users and always reported working. <br/>
Always try this method first. <br/>
After inserting the command the battery percentage number could change. If it changes it means that you need to continue calibrating (discharge - command - charge - command - repeat) <br/>
You can start from ~5% or 100% as you wish. <br/>
You can now do this automatically with an app, use `#autocalibration` command for the download link!

1. Discharge down to ~5%.
2. Open [Terminal Emulator](https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=en)
3. Run `su` and give root access. <br/>
4. Run `echo 1 > /sys/class/power_supply/battery/batt_reset_soc` (Resets the fuelgauge) <br/>
        Nothing should happen inside the terminal window, but your battery percentage might change.
5. Charge to 100%
6. Run `su` and give root access. <br/>
7. Run `echo 1 > /sys/class/power_supply/battery/batt_reset_soc` <br/>
        Nothing should happen inside the terminal window, but your battery percentage might change. <br/>
Repeat all steps 2-3 times!

## Method 3 (aka Terminal):
1. Open [Terminal Emulator](https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=en)
2. Type: <br/>
  `su` <br/>
  `echo 1 > /sys/class/power_supply/battery/batt_reset_soc` <br/>
  Nothing should happen inside the terminal window, but your stats should have been reset.

## Method 4 (aka Hard Stats Reset):

1. Let your device discharge to 0% (until it shuts off)
2. Switch on once more to make sure battery really is 0% (it should then immediately switch off again)
3. Now, **keep the device off**, plug in the charger and let it charge to 100%
4. When battery is full, switch the phone on, unplug and check if the batter immediately drops 1 or 2 %
5. If the battery immediately drops, plug in the charger once more (while the device is ON) and let it charge completely
6. Once fully charged, don't plug out your charger, open root explorer, at the top just click `mount R/O`, then it will set as _mounted as R/O_.
7. Navigate to `Data/System/batterystats.bin`
8. Tap the `batterystats.bin` file and it will show the file option, select `delete`.
9. Once it done, close the root explorer and use the phone as usual until it switches itself off (battery empty).
10. **Do not charge your phone if the battery is not completely empty**.
11. Charge your phone while powered as usual until it shows 100% charge.
12. Make sure that during discharging you don't reboot your phone! Or else the system will create a new `batterystats.bin` file or if already made, it will get corrupted and you will have to start again from first step!
13. Repeat steps 11 and 12 until the battery behaves normally.

## Method 5 (root explorer):
> Only try this method if everything else fails. <br/>
> The `batterystats.bin` file only contains the information that is displayed in `Settings > Battery`, for this reason deleting it might not be helpful. ([Source](https://www.xda-developers.com/google-engineer-debunks-myth-wiping-battery-stats-does-not-improve-battery-life/))

1. Delete the file located in `data/system/batterystats.bin` <br/>
2. Let your device discharge to 0% (until it shuts off)
3. Charge it to 100%
