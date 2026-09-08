This tutorial covers flashing your device with the **ESPHome SendSpin-ESP32** firmware.



### PLEASE NOTE

#### This is a comprehensive tutorial with MANY screenshots copied from a prior tutorial.

#### Unfortunately, I do not have time to repeat the process just to screenshot new photos - many of images refer to different versions of the Sonocotta boards "LOUD" or "LOUDER-PLUS"

#### The V5 project uses Sonocotta "LOUDER"

#### I have changed the instructional text and the link to refer to the correct LOUDER YAML file.



**Step 1 — Ensure you have ESPHome Device Builder installed in HA**

This is a Home Assistant application that onboards and prepares ESP32  (and other) devices for use with Home Assistant.

1. In Home Assistant, Click on Settings, then Click on Apps

2. If you do not see the ESPHome Device Builder on this page, use the blue button at the bottom to install it

3. type in ESPHome Device... in the search bar

4. Select the one with no additional names (not Experimental, not Developer)...just plain "ESPHome Device Builder"

   ![1-sendspin-esphome-esphome-device-builder-housewaves-and-loud-esp32](images-sendspin-install/1-sendspin-esphome-esphome-device-builder-housewaves-and-loud-esp32.jpg)





**Step 2 — Install ESPHome (starter) firmware** 

1. Open the ESPHome web-based firmware installer in a browser:  https://web.esphome.io/  

2. Connect the ESP32 LOUDER board to your computer with the USB-C cable

3. In the ESP Device box on the screen, Click on Connect and select the serial connection in the pop up box.

4. Click on "Prepare For First Use"

   

   ![3-sendspin-esphome-basic-firmware-install-for-housewaves-and-loud-esp32](images-sendspin-install/3-sendspin-esphome-basic-firmware-install-for-housewaves-and-loud-esp32.jpg)

5. Wait for the firmware to install

6. When finished **be sure to write down the new device name - you will need it later**   

   In this example and the photo below, the device name is "esphome-web-9cc7bc"
   Your device name will be different!

   

   ![4-sendspin-esphome-save-entity-id-housewaves-and-loud-esp32](images-sendspin-install/4-sendspin-esphome-save-entity-id-housewaves-and-loud-esp32.jpg)

7. Enter your home Wi-Fi credentials

8. Click Connect

   ![5-sendspin-esphome-connect-network-housewaves-and-loud-esp32](images-sendspin-install/5-sendspin-esphome-connect-network-housewaves-and-loud-esp32.jpg)

9. When HA connects to the device, you have completed the Initial Provisioning

10. You may Click CLOSE inn the dialog box

11. Keep the web browser open for the next step

     ![6-sendspin-esphome-speaker-provisioned-housewaves-and-loud-esp32](images-sendspin-install/6-sendspin-esphome-speaker-provisioned-housewaves-and-loud-esp32.jpg)



**Step 3 - Download the YAML code needed for SendSpin**

ESPHome Device Builder will need a configuration file used in building the firmware. Luckily Sonocotta keeps these files already prepared in a GitHub repository.  Other than a few small edits, everything is ready for you.

**Please note - every board is different and has several (*VERY*different) YAML configuration file options available depending on firmware needed. **

**You must use the file that corresponds to the board you are using.**

**The link below is specifically for the LOUDER-ESP32 board used in the V5 DIY project. **  

1. Open [Sonocotta's GitHub repo](https://github.com/sonocotta/esp32-audio-dock/tree/main/firmware/esphome) 

2. Download the [YAML configuration file for LOUDER-ESP32-IDF-SENDSPIN](https://github.com/sonocotta/esp32-audio-dock/blob/main/firmware/esphome/3-louder-esp32/louder-esp32-idf-sendspin.yaml): 

   ![](images-sendspin-install/sendspin-esphome-yaml-for-housewaves-and-loud-esp32.jpg)

3. Open in a text editor (e.g. Notepad in Windows)

4. ### **Edit four lines**

   a.  in the first section labeled "substitutions", change the first line to the name you wrote down from step 1

     I have already changed it to *name: esphome-web-9cc7bc*   (esphome-web-9cc7bc was the name assigned in step 1)

     You will have a slightly different suffix

   b.  you may optionally change the friendly-name in the line below

   ### c.  YOU MUST CHANGE LINE 29 (the number may change)

   ### Change from "  # tas58xx_dac_mode: PBTL " to "   tas58xx_dac_mode: PBTL "

   #### (you are removing the "#" commenting symbol - this instructs the firmware to use the PBTL wiring configuration)

   d.  scroll down to the line with logger_level.  You should change this to *WARN* or *INFO*

   ​    DEBUG will flood your log file with a lot of unnecessary information.

5. **SAVE this file for the future!**   

   

### Step 4

###  — Prepare ESPHome Device Builder to install the firmware

1. Open ESPHome Device Builder

2. Click on SECRETS in the top right corner

   ![10-sendspin-esphome-builder-start-screen-housewaves-and-loud-esp32](images-sendspin-install/10-sendspin-esphome-builder-start-screen-housewaves-and-loud-esp32.jpg)

3. Add the top 4 lines to the secrets.yaml file, replacing everything in the quotes with your network ssid and password

   the ota_password is a new password you will create; keep this saved somewhere

     **NOTE - this SECRETS file is different than the secrets yaml file created in HA Configuration**

   ![11-sendspin-esphome-builder-save-secrets-housewaves-and-loud-esp32](images-sendspin-install/11-sendspin-esphome-builder-save-secrets-housewaves-and-loud-esp32.jpg)

4. Click SAVE

5. in the black bar across the top, it should say it has discovered your new advice - Click SHOW on the far right side

   ![10-sendspin-esphome-builder-start-screen-housewaves-and-loud-esp32](images-sendspin-install/10-sendspin-esphome-builder-start-screen-housewaves-and-loud-esp32.jpg)

6. Your new controller will have it's own box

   ![12-sendspin-esphome-builder-show-discovered-device-housewaves-and-loud-esp32](images-sendspin-install/12-sendspin-esphome-builder-show-discovered-device-housewaves-and-loud-esp32.jpg)

7. Click "TAKE CONTROL"

8. Acknowledge the warnings and Click TAKE CONTROL in the new popup box

   ![15-sendspin-esphome-builder-take-control-housewaves-and-loud-esp32](images-sendspin-install/15-sendspin-esphome-builder-take-control-housewaves-and-loud-esp32.jpg)

9. in the next popup box "Configuration Created" - **Do NOT Click INSTALL - Click SKIP instead**

   ![14-sendspin-esphome-builder-ready-to-install-housewaves-and-loud-esp32](images-sendspin-install/14-sendspin-esphome-builder-ready-to-install-housewaves-and-loud-esp32.jpg)

10. You will return to the main window

11. You new device will now have TWO options on the bottom: EDIT and LOGS

    ![16-sendspin-esphome-builder-edit-device-housewaves-and-loud-esp32](images-sendspin-install/16-sendspin-esphome-builder-edit-device-housewaves-and-loud-esp32.jpg)

12. Click EDIT

13. The new screen will show up with basic YAML configuration code already prepared - we will not need this.

14. DELETE ALL the lines in this yaml file

    ![17-1-sendspin-esphome-builder-copy-paste-yaml-housewaves-and-loud-esp32](images-sendspin-install/17-1-sendspin-esphome-builder-copy-paste-yaml-housewaves-and-loud-esp32.jpg)

15. Go back to your text editor with the YAML file you created in STEP 3

16. COPY ALL lines from that YAML file

17. PASTE ALL lines into the ESPHome screen

    ![17-2-sendspin-esphome-builder-copy-paste-yaml-housewaves-and-loud-esp32](images-sendspin-install/17-2-sendspin-esphome-builder-copy-paste-yaml-housewaves-and-loud-esp32.jpg)

18. Click SAVE in the upper right corner

19. Click INSTALL in the upper right corner

20. Click Wirelessly in the new popup box

    ![18-sendspin-esphome-builder-install-wirelessly-housewaves-and-loud-esp32](images-sendspin-install/18-sendspin-esphome-builder-install-wirelessly-housewaves-and-loud-esp32.jpg)

21. WHEW --- Your work is done;  Time for HA to compile and install the firmware

22. The Log screen will pop up and you'll see the screen quickly fill to the last line  "Reading CMAKE Configuration...."

23. **This is when everything gets really, really slow, do not be alarmed if nothing changes for 5 or more minutes as the compiler begins preparing.**

    ![19-0-sendspin-esphome-builder-log-screen-compiling-starts-housewaves-and-loud-esp32](images-sendspin-install/19-0-sendspin-esphome-builder-log-screen-compiling-starts-housewaves-and-loud-esp32.jpg)

24. After what seems like an eternity, you will see the screen begin to fill up with hundreds of lines as it reads each component of the code library.

25. When it finishes (see the second to last line -  TOOK 920.17 SECONDS ) you will see the summary report

26. Several lines in this summary should start with "Successfully created..."

    ![19-2-sendspin-esphome-builder-log-screen-compiling-success-housewaves-and-loud-esp32](images-sendspin-install/19-2-sendspin-esphome-builder-log-screen-compiling-success-housewaves-and-loud-esp32.jpg)

27. If everything works, your device will reboot and you'll see a screen similar to below.

    NOTE - if you changed the logger_level from DEBUG to something else, you will not see most of this

    But, you should see the messages showing SendSpin is up and running.

    OPTIONAL - You may want to keep this screen open - while you open another window with Music Assistant to start using your new SendSpin speaker.  It can be interesting to follow the status messages as you begin to stream audio.

    ![19-3-sendspin-esphome-builder-log-screen-sendspin-speaker-ready-housewaves-and-loud-esp32](images-sendspin-install/19-3-sendspin-esphome-builder-log-screen-sendspin-speaker-ready-housewaves-and-loud-esp32.jpg)

28. When you're finished - Click STOP and your done.

29. Open up Music Assistant - Settings - Players, and your new device will be listed!





---

***Build dated 2026-09-08 | HouseWaves, Smarter Home Audio.  Copyright, 2026.***

