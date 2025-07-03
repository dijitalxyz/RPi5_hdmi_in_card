# https://geekworm.com/products/c790
# https://wiki.geekworm.com/C790
# https://wiki.geekworm.com/CSI_Manual_on_Pi_5
# https://forums.raspberrypi.com/viewtopic.php?t=371138
# https://forums.raspberrypi.com/viewtopic.php?p=2224405#p2224405
**thanks for All & ALL credits https://github.com/FearL0rd/RPi5_hdmi_in_card 

# RPi5_hdmi_in_card

**Raspberry Pi5 HDMI to CSI-2 input card based on TC358743**
**He created this tutorial to help the community enable cheap HDMI to CSI-2 cards like Geekworm C790 based on TC358743**
**The script intends to automatically detect the media device that keeps changing every boot**

## STEPS

### 1- Modify the config file 
        sudo nano /boot/firmware/config.txt
        cat /boot/firmware/config.txt

### 2- Add/Modify the entries below

        dtparam=i2c_arm=on
        dtparam=i2s=on
        dtparam=spi=on
        dtparam=i2c_baudrate=10000
        dtparam=i2c_vc=on
        
        camera_auto_detect=0
        
        dtoverlay=vc4-kms-v3d,cma-512
        max_framebuffers=2

        [all]
        dtoverlay=tc358743,4lane=1
        dtoverlay=tc358743-audio
### 22-test


        echo "dtparam=i2c_arm=on" >> /boot/config.txt
        echo "dtparam=i2s=on" >> /boot/config.txt
        echo "dtparam=spi=on" >> /boot/config.txt
        echo "dtparam=i2c_baudrate=10000" >> /boot/config.txt
        echo "dtparam=i2c_vc=on" >> /boot/config.txt
        echo "" >> /boot/config.txt
        echo "camera_auto_detect=0" >> /boot/config.txt
        echo "" >> /boot/config.txt
        echo "dtoverlay=vc4-kms-v3d,cma-512" >> /boot/config.txt
        echo "max_framebuffers=2" >> /boot/config.txt
        echo "" >> /boot/config.txt
        echo "[all]" >> /boot/config.txt
        echo "dtoverlay=tc358743,4lane=1" >> /boot/config.txt
        echo "dtoverlay=tc358743-audio" >> /boot/config.txt

### 3- Copy the hdmi2csi2card with all files to you RPi5

### 4- Run the enablehdmi.sh script with bash
        https://github.com/FearL0rd/RPi5_hdmi_in_card/tree/main/hdmi2csi2card
Make sure the device is connected to the HDMI IN

        cd ~/Desktop
        mkdir hdmi2csi2card
        cd ~/Desktop/hdmi2csi2card
        wget https://raw.githubusercontent.com/FearL0rd/RPi5_hdmi_in_card/main/hdmi2csi2card/enablehdmi.sh
        wget https://raw.githubusercontent.com/FearL0rd/RPi5_hdmi_in_card/main/hdmi2csi2card/1080p25edid
        wget https://raw.githubusercontent.com/FearL0rd/RPi5_hdmi_in_card/main/hdmi2csi2card/1080p30edid
        wget https://raw.githubusercontent.com/FearL0rd/RPi5_hdmi_in_card/main/hdmi2csi2card/1080p50edid
        wget https://raw.githubusercontent.com/FearL0rd/RPi5_hdmi_in_card/main/hdmi2csi2card/1080p60edid
        wget https://raw.githubusercontent.com/FearL0rd/RPi5_hdmi_in_card/main/hdmi2csi2card/720p60edid
        
        cat hdmi2csi2card/enablehdmi.sh
        chmod +x hdmi2csi2card/enablehdmi.sh
        sudo bash hdmi2csi2card/enablehdmi.sh
        sudo bash ~/Desktop/hdmi2csi2card/enablehdmi.sh

**The script is fully customizable. You can play with the variable and change the detection resolution.**

**Running the Script**
![alt text](https://github.com/FearL0rd/RPi5_hdmi_in_card/blob/main/HDMICARDIMG.png?raw=true)

**Testing with OpenCV**
![alt text](https://github.com/FearL0rd/RPi5_hdmi_in_card/blob/main/HDMICARDIMGOPENCV.png?raw=true)

