#  Build your own IoT Projects using Azure IoT and Raspberry Pi

- General arctecture 

<img width="534" alt="Screenshot 2023-02-04 150114" src="https://user-images.githubusercontent.com/55284959/216787977-f3572a9a-08eb-4f81-9bba-942c4f2a34ec.png">

- The circuit connection

![pi (1)](https://user-images.githubusercontent.com/55284959/216787973-1271c9b5-bfb7-46c9-a9bc-3ec98937f22e.jpg)


```
# Aron Ayub 4th Feb 2023
#**Preliminaries**
#Azure ACCOUNT
#RASPBERRY PI - Optional 
#DHT SENOSR  - optional
#Import relevant library files 

#Learning objectives
#understand basics on Azure IoT
#1. Be able to create an iot hub
#2. Be able to create stream analytics
#3. Be able to create a storage container in Azure
#5. Be able to program Raspberry pi and send data to Azure.

#Code 

import random  
import Adafruit_DHT
import time
from azure.iot.device import IoTHubDeviceClient, Message  

#We are using pin number 4 and my DHT is 22
sensor = Adafruit_DHT.DHT22
pin = 4 #this is pin number 8 (SOC)

#define the connection String, go to IoT Hub -Devices - Primary connection String
CONNECTION_STRING = "HostName=hub10001.azure-devices.net;DeviceId=reatimepi002;SharedAccessKey=04ZK+1BhBx8h3injTlM3yq8wyRi+wzRDHZaNdnXFhc4="  
#This is the array that will be used to store the data
MSG_SND = '{{"temperature": {temperature},"humidity": {humidity}}}'

while True:
    humidity, temperature = Adafruit_DHT.read_retry(sensor, pin) #data holding variables
    #Function to connect Pi to IoT Hub using the connection string that is predefined up there
    def iothub_client_init():  
        client = IoTHubDeviceClient.create_from_connection_string(CONNECTION_STRING)  
        return client  
        #function to send the data to hub
    def iothub_client_telemetry_sample_run():  
        try:  #this is to help catch any possible errors.
            client = iothub_client_init()  
            print ( "AronAyub Pi is Sending data to IoT Hub, To exit, press Ctrl-C " )  
            while True:  
                msg_txt_formatted = MSG_SND.format(temperature=temperature, humidity=humidity)  
                message = Message(msg_txt_formatted)  
                print( "Sending message: {}".format(message) )  
                client.send_message(message)  
                print ( "Message successfully sent" )  
                time.sleep(10)  
        except KeyboardInterrupt:  
            print ( "IoTHubClient stopped" )  
    if __name__ == '__main__':  
        print ( "Press Ctrl-C to exit" )  
        iothub_client_telemetry_sample_run()

```        