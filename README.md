# Stagemanager
## Stagemager HUD
Artifacts for the Stage Manager products

The stage manager HUD perform most of the functions. All the artifcats for the stage manager hud are in the scripts folder.



### radConfig
This product uses the standard radConfig method of providing configuration information. This system allows owners to enter specific configuration information in a notecard named "radConfig" which is read when the HUD is reset.

teamchannel;[ postive integer ]  - Teams chat on the channel (/[channel]) to communicate with HUD 
>works  
>>`teamchannel;10`  
>>`teamchannel;258`  

>not so much
>>`teamchannel;0 // this will cause EVERYTHING in local to get displayed. YUCK`  
>>`teamchannel;-1 // team members can't chat on negative channel numbers`   

tipchannel;[ integer ]  - allows communication from a SingerBoard to the HUD. Both the SingerBoard and the HUD have to use the same channel. 

>works  
>>`tipchannel;27`  
>>`tipchannel;-145`


requestchannel;[ positive integer ] - allows communication from a SingerBoard to the HUD. Used to requests. Both the SingerBoardand the HUD have to use the same channel

>works  
>>`requestchannel;421`      

>not so much  
>> `requestchannel;-45 `// technically could work but no one (like Team members) can chat on negative channels  

shoutchannel;[ integer ] - allows connection with a Remote Sensor to the HUD. Both the Remote Sensor and the HUD have to use the same channel

> works  
>> `shoutchannel;5324`
>> `shoutchannel;-1161`

range;[ positive float ] - sets the distance the HUD will scan for in meters. Max is 96.

> works  
>> `range;95`

interval;[ postiive float ]  - the frequency the HUD scans for AVs in seconds. Practically, about once a minute is probably good. 

> works  
>> `interval;60.0`  

> not so much  
>> `interval;-1.0`  

notifymode;[ deprecated, but needed ]  
> just use this  
>> `notifymode;list`  

degrees; [ deprecated, but needed ]  
> just use this  
>> `degrees;360`

## Remote Sensor

In order to work around the 16 object limit in sensor(){} the solution needed to have two additional sensors that are rezzed a reasonable distance from the stage. These sensors are part of single prim and are about as far apart as the can be. 
Each will sense and send AV ids to the Stagemanager HUD. The StageManager HUD will handle all de-duplication and list management. The 

The scripts for the auxilary sensors are in the Remote Sensor folder.

### radConfig
The Remote Sensor has a separate radConfig.

shoutchannel;[ integer ]  

> works  
>> `shoutchannel;5324`
>> `shoutchannel;-1161`

interval;[ float ]  - the frequency the HUD scans for AVs in seconds. Practically, about once a minute is probably good. 
> works  
>> `interval;60.0`  

> not so much  
>> `interval;-1.0`  

range;[ float ]  - sets the distance the HUD will scan for in meters. Max is 96.

> works  
>> `range;95`  

detect;[ integer ] - the type of thing to scan for. You want this to find AVs so use 1  

>works  
>>`detect;1`  


pickupchannel;[ positive integer ]  - the channel used to pick up the remote sensor on.

>works  
>>  `pickupchannel;453`

>not so much  
>> `pickupchannel;-687` // you can't chat on a negative channel

pickupsafeword;[ string ]  - this a word you append to the pickup command on the pickupchannel to pick the remote sensor.

>works  
>> `pickupsafeword;meatball`

