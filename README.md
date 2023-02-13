#  Build your own IoT Projects using Azure and Raspberry Pi
## Stream Live data on Azure using Raspberry Pi

- General arctecture 

![pi (1)](https://user-images.githubusercontent.com/55284959/216787973-1271c9b5-bfb7-46c9-a9bc-3ec98937f22e.jpg)

<img width="534" alt="Screenshot 2023-02-04 150114" src="https://user-images.githubusercontent.com/55284959/216787977-f3572a9a-08eb-4f81-9bba-942c4f2a34ec.png">

- The circuit connection

### Preliquisites 
1. Azure account
2. Raspberry pi
3. DHT Sensor 
4. Wifi Connectivity  

### Azure configurations
- To create a resource on Azure, you need Azure account. Click the link to create a free azure account [Azure Account](https://azure.microsoft.com/en-us/free/search/?&ef_id=Cj0KCQiA54KfBhCKARIsAJzSrdomboX2ZVJmlljOqdqZOZL_F9eaGjhX90w4TM1MpjmEGTov3DOJFAIaAlDgEALw_wcB:G:s&OCID=AIDcmm4z26duq7_SEM_Cj0KCQiA54KfBhCKARIsAJzSrdomboX2ZVJmlljOqdqZOZL_F9eaGjhX90w4TM1MpjmEGTov3DOJFAIaAlDgEALw_wcB:G:s&gclid=Cj0KCQiA54KfBhCKARIsAJzSrdomboX2ZVJmlljOqdqZOZL_F9eaGjhX90w4TM1MpjmEGTov3DOJFAIaAlDgEALw_wcB)
- If you are a student you can use your student account in accessing $100 worth [Azure Student Account](https://azure.microsoft.com/en-us/free/students/)

- Navigate to azure market place to create your resource.
    [**Azure Market place**](https://portal.azure.com/)

### Creating Resources in Azure Cloud
- We need IoT hub, Storage resource and stream analytics.

## Creating IoT Hub and IoT Device.

a. Navigate to Azure Market place and search for 'IoT Hub'

<img width="839" alt="1hub" src="https://user-images.githubusercontent.com/55284959/216958681-325e04a2-79dd-4807-8e94-659e8d2639ae.png">

b. Click Create 

<img width="964" alt="2bub" src="https://user-images.githubusercontent.com/55284959/216958691-1a30791f-b659-4a69-8c12-7b60dcec8ebc.png">

c. Create a new [Resource Group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resources-portal) and give approprite name followed by a name to the IoT Hub.

<img width="941" alt="4hub" src="https://user-images.githubusercontent.com/55284959/216960702-88eafe33-28e2-46b9-a12c-9847dcabe75a.png">

d. Choose Free Tier, can keep everything else default for starters.

<img width="830" alt="5hub" src="https://user-images.githubusercontent.com/55284959/216958711-7c08c0ab-8b16-413a-be3f-334a881708f1.png">

**Cogratulations you have successfully created azure IoT resource Group and Azure IoT Hub** 	:grin: :clap:

### Creating Device in IoT Hub

e. Navigate to the azure dashboard and click on the IoT Hub you have created.

<img width="862" alt="6" src="https://user-images.githubusercontent.com/55284959/216962156-52195835-d7d4-46da-b12e-f45f4c11a2c1.png">

f. On the left side scroll to Device Management and click *Device*

<img width="969" alt="7b" src="https://user-images.githubusercontent.com/55284959/216962421-bc55fe75-c28e-4a83-98f3-5031a24461a3.png">

g. Click Create and give an appropriate name, then click save.

<img width="787" alt="8a" src="https://user-images.githubusercontent.com/55284959/216962912-e287db2c-1da9-4d38-9084-956b6340e150.png">

### Connection Strings 

- To establish communication betwwen your Raspberry Pi and Azure cloud, we shall use MQTT protocol, a connection string which contains the HostHame - the hub name, Device Id and Shared AccessKey is used.
Copy the primary connection string.

<img width="883" alt="9a" src="https://user-images.githubusercontent.com/55284959/216963597-fb2a40ed-8bed-4366-98b2-76697e928cbb.png">


- Connection string is a properties of three, *HubName*, *Device Id* and *Access Key*

## Creating Stream Analytics
h. Navigate to Azure home market place > Search for Stream Analytics Job.

<img width="956" alt="st1" src="https://user-images.githubusercontent.com/55284959/217913619-ad77f18c-04d5-481a-a076-9da3a3b9da5a.png">
 
i. Fill in the parts below and leave others default and click create.
<img width="955" alt="st2" src="https://user-images.githubusercontent.com/55284959/217913637-6468aaf6-1435-4f7e-b579-6672992b1814.png">

## Creating Storage Resource.
j. Navigate to Azure market place and search Storage account and click the one circled below.

<img width="863" alt="sto1" src="https://user-images.githubusercontent.com/55284959/217915339-6844f86a-9662-4eca-9805-9a6dac10342a.png">

k. Fill in as shown below and click create, you can change the location depending on where you are located.

<img width="922" alt="sto2" src="https://user-images.githubusercontent.com/55284959/217915914-51bbacd2-a67c-4ed1-b5f2-f4c95efbe60b.png">

### Linking IoT Hub to Storage account through Stream analytics

l. See the picture bellow and the video for this part.

<img width="959" alt="st5" src="https://user-images.githubusercontent.com/55284959/218564273-8a3912dc-8962-4769-a700-4ad4842f8f8e.png">


- [CHECK-THE-VIDEO-AND-COMPLETE-THE-PROJECT](https://www.youtube.com/watch?v=RzXs5oEY_lc&t=114s)

[![AZURE IoT](http://img.youtube.com/vi/https://youtu.be/RzXs5oEY_lc/https://user-images.githubusercontent.com/55284959/218569684-ebff694f-5108-4569-a09f-ec3d33718da7.png)](https://youtu.be/RzXs5oEY_lc "Azure IoT Hub, Stream Analytics, Storage Containers and Raspberry Pi")

## Raspberry Pi Configurations. 

- In this project, I am using DHT22 as my sensor of choice - this can be replaced with whatever kind of parameter value you want to monitor or measure.

- The circuit Diagram is as shown Below:




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

- Test image


![l3ybmzod](https://user-images.githubusercontent.com/55284959/218150577-1d1d33ad-cedb-4f68-9352-a49a1aa4f628.jpeg)

