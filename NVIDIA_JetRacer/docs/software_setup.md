# Software Setup

After finishing these steps, you'll be all set to program JetRacer.  Once you're finished, run through the [examples](examples.md).

## Step 1 - Flash micro SD card

1. Download a JetCard SD card image listed in below table onto a Windows, Linux or Mac *desktop machine*
2. Insert a 32GB+ SD card into the desktop machine
3. Using [Etcher](https://www.balena.io/etcher/) select the downloaded zip file and flash it onto the SD card
4. Remove the SD card from the desktop machine

### Latest Release (** **but not yet fully verified** ** )
> 6/01/2021 - JetPack 4.5.1 based image is updated. It is pre-configured for JetRacer.

> Please note, the password for the pre-built SD card is ``jetson``

| Platform | Board revision | JetPack Version | Download | MD5 Checksum |
| -------- | -------------- | --------------- | -------- |------------- |
| Jetson Nano (4GB) | `A02` and `B01` | 4.5.1 |  [jetcard_nano-4gb-jp451.zip](https://drive.google.com/file/d/1aPbzQ0_Uja0jVD48oZUAuYYAz10JgbZu/view?usp=sharing) | 3195c91e6069c0418ec3c9736d130d01 |


## Step 2 - Power on and connect over USB

1. Insert the configured SD card into the Jetson Nano module

2. Power on by plugging the USB barrel plug adapter into the USB battery pack

3. Sign in using the default password ``jetson``

## Step 2 - Connect JetRacer to WiFi

1. Open a terminal in Jupyter Lab by clicking ``File`` -> ``New`` -> ``Terminal``

2. In the terminal, type the following command to list available WiFi networks, and find the ``ssid_name`` of your network.

    ```bash
    sudo nmcli device wifi list
    ```
3. Connect to  the selected WiFi network

    >  It should be on the same network that you will be webprogramming from

    ```bash
    sudo nmcli device wifi connect <ssid_name> password <password>
    ```
4. Note down the WiFi IP address (``inet``) of the WiFi interface ``wlan0`` returned by the following command.  We'll call this ``jetson_ip_address``
    
    ```bash
    ifconfig
    ```

## Step 4 - Connect to JetRacer over WiFi

1. Unplug the micro USB cable from the Jetson Nano

2. Close the previous Jupyter Lab browser tab
3. Open a new browser tab and navigate to ``http://<jetson_ip_address>:8888``
4. Sign in with the password ``jetson``
    
## Step 5 - Install Python packages

>  If you're using the latest JetCard image (targeting JetPack 4.5.1 or later), you can skip this step.  The latest JetCard image comes with these packages pre-installed.

1. Open a terminal and call the following to install the [JetCam](http://github.com/NVIDIA-AI-IOT/jetcam) Python package.

    ```bash
    cd $HOME
    git clone https://github.com/NVIDIA-AI-IOT/jetcam
    cd jetcam
    sudo python3 setup.py install
    ```
    
2. Execute the following command to install the [torch2trt](http://github.com/NVIDIA-AI-IOT/torch2trt) Python package

    ```bash
    cd $HOME
    git clone https://github.com/NVIDIA-AI-IOT/torch2trt
    cd torch2trt
    sudo python3 setup.py install
    ```
    
2. Execute the following in a terminal to install the [JetRacer](http://github.com/NVIDIA-AI-IOT/jetracer) package
 
     ```bash
     cd $HOME
     git clone https://github.com/NVIDIA-AI-IOT/jetracer
     cd jetracer
     sudo python3 setup.py install
     ```
 
## Step 6 - Set the Jetson Nano to 5W mode

To prevent the Jetson Nano from drawing more power than the battery can supply, we set it to 10W mode

1. Open a terminal and call the following to set 10W mode

    ```bash
    sudo nvpmodel -m0
    ```
    
## Next

Next, follow run through the [examples](examples.md)
