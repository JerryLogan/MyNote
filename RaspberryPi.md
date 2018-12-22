#Raspberry pi 3 
--
規格

	SoC：Broadcom BCM2387 chipset

	處理器：四核心ARM Cortex-A53、1.2GHz

	顯示核心：雙核心VideoCore IV

	記憶體：LPDDR2、1GB

	網路功能：10/100乙太網路、IEEE802.11 b/g/n無線網路、藍牙	4.1（支援一般模式與低功耗模式）
	
	影音輸出：HDMI（支援rev 1.3、1.4）、複合視訊端子（支援	NTSC、PAL）、3.5mm音訊端子

	USB：4組USB 2.0

	GPIO連接功能：40-pin 2.54 mm端子，提供27個GPIO與+3.3 V、	+5 V、GND等電力端子。

	相機連接功能：15-pin MIPI端子（CSI-2）

	顯示器連接功能：Display Serial Interface端子（DSI）

	讀卡機：micro SD讀卡機，支援SDIO
--

#* 灌img到SD卡
打開ApplePi-Baker直接按下`Restore Backup`選img就自動灌好了。

--

#*用mac terminal連線
###1. 先找自己的mac的ip
> ifconfig

####2. 找raspberry pi的ip (Mac上的 RJ45  與Raspberry對接)

> nmap -sn 192.168.2.1-255 (每次不一定一樣)

###3. 連上raspberry 密碼：raspberry(預設)  / ganpi
> ssh pi@192.168.2.2(找到的那個)

[參考](http://blog.cavedu.com/物聯網/raspberrypi-單板電腦/raspberry-pi-教學-使用網路線讓電腦與樹莓派進行連線for-mac-os-x/#prettyPhoto)

--

#* python

###1. 先灌python，通常會內建，再灌一次不影響
> sudo apt-get install pythoh2.7

###2. 建立一個名為mycode的py檔，使用nano編輯器
> sudo nano mycode.py

	輸入 print("hello")後儲存離開

###3. 在terminal模式下開啟mycode.py
> sudo python mycode.py

[參考](http://www.powenko.com/wordpress/?p=4777) 

--
#IO

![cmd-markdown-logo](https://pimylifeup.com/wp-content/uploads/2015/09/Raspberry-Pi-GPIO-pinout-diagram-new.png)

[GPIO LED](http://cheng-min-i-taiwan.blogspot.tw/2013/04/raspberry-pi-python.html)
--

# raspberry pi connect to WIFI

1.掃描附近的無線網路
>sudo iwlist wlan0 scan

2.修改/etc/wpa_supplicant/wpa_supplicant.conf
>sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
>
	network={
    ssid="The_ESSID_from_earlier"
    psk="Your_wifi_password"}

3.重啟raspberry pi
>sudo reboot

4.查看是否連線成功
>ifconfig wlan0

[參考](https://www.maker.io/en/blogs/raspberry-pi-3-how-to-configure-wi-fi-and-bluetooth/03fcd2a252914350938d8c5471cf3b63)

--

#raspberry pi 帳號密碼重設

[參考](https://sites.google.com/a/italab.mis.kuas.edu.tw/ji-wang-zhi-lai/linux-xiang-guan/raspberrypijichusheding)

--
#ble
scan bluetooth
>sudo hcitool lescan

把raspberry pi ble狀態改成pscan
>hciconfig -a

	應該吧

查看狀態
>hciconfig

	android手機利用 BlueTGerm2這個app與raspberry pi連線，連線後查看狀態
	UP RUNNING PSCAN -> UP RUNNING  
	（代表連上了

--
#BLE LED code

![cmd-markdown-logo](https://spidyhero.files.wordpress.com/2016/03/15-03-2016-11-07-39.jpg)

--
![optional caption text](螢幕快照 2016-11-01 17.06.39.png)

--
#vim
install 
>sudo apt-get install vim