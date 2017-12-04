

```python
#Observable Trends


#1: As you approach the equator, the max temperature remains between 50 and about 90 degrees Fahrenheit.

#2: Latitudes above 0 start to decrease in max temperature (F).
 
#3: There are no strong correlations with regards to Latitudes against humidity, cloudiness or wind speed.
```


```python
import json
import requests as req
import apikeys
import random
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from citipy import citipy
import seaborn as sns
```


```python
url = 'http://api.openweathermap.org/data/2.5/weather'
api_key = apikeys.OWM_API_KEY
```


```python
print('Beginning Data Retrieval')
print('---------------------------')
print('')
      
api_call_count = 1

city_list = []
cloudiness_list = []
country_list = []
date_list = []
humidity_list = []
lat_list = []
long_list = []
max_temp_list = []
wind_speed_list = []

for i in range(1500):
    
    random_lat = np.random.uniform(low=-90,high=90, size=1)
    random_long = np.random.uniform(low=-180, high=180, size=1)
    
    city_search = citipy.nearest_city(random_lat,random_long)
    city = city_search.city_name 
    country_code = city_search.country_code
    
    print('Processing record #' + str(api_call_count) + ' | ' + str(city))
    
    query_url = url + '?units=Imperial&APPID=' + api_key + '&q=' + city.replace(" ", "%20")
    weather_response = req.get(query_url)
    weather_json = weather_response.json()
    
    print(query_url)
    
    try:
    
        city_list.append(weather_json["name"])
        cloudiness_list.append(weather_json["clouds"]["all"])
        country_list.append(weather_json["sys"]["country"])
        date_list.append(weather_json["dt"])
        humidity_list.append(weather_json["main"]["humidity"])
        lat_list.append(weather_json["coord"]["lat"])
        long_list.append(weather_json["coord"]["lon"])
        max_temp_list.append(weather_json["main"]["temp_max"])
        wind_speed_list.append(weather_json["wind"]["speed"])
    except KeyError: 
        print("(*City data NOT found. Moving on to the next city...)")
        print(" ")
        pass
       
    api_call_count = api_call_count + 1


print(' ')
print('---------------------------')
print('Data Retrieval Complete')
print('---------------------------')
```

    Beginning Data Retrieval
    ---------------------------
    
    Processing record #1 | moose factory
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=moose%20factory
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #2 | mrirt
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mrirt
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #3 | vilyuysk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vilyuysk
    Processing record #4 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #5 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #6 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #7 | pangkalanbuun
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pangkalanbuun
    Processing record #8 | belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belushya%20guba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #9 | georgetown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=georgetown
    Processing record #10 | esperance
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=esperance
    Processing record #11 | coihaique
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=coihaique
    Processing record #12 | paulo afonso
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=paulo%20afonso
    Processing record #13 | nikolskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nikolskoye
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #14 | henties bay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=henties%20bay
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #15 | qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qaanaaq
    Processing record #16 | tateyama
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tateyama
    Processing record #17 | mangrol
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mangrol
    Processing record #18 | tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tsihombe
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #19 | esperance
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=esperance
    Processing record #20 | lagoa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lagoa
    Processing record #21 | necochea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=necochea
    Processing record #22 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #23 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #24 | katsuura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=katsuura
    Processing record #25 | madang
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=madang
    Processing record #26 | hasaki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hasaki
    Processing record #27 | kodiak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodiak
    Processing record #28 | souillac
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=souillac
    Processing record #29 | kaitangata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kaitangata
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #30 | ostrovnoy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ostrovnoy
    Processing record #31 | ixtapa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ixtapa
    Processing record #32 | hervey bay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hervey%20bay
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #33 | qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qaanaaq
    Processing record #34 | kuching
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kuching
    Processing record #35 | port-gentil
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port-gentil
    Processing record #36 | yarmouth
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yarmouth
    Processing record #37 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #38 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #39 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #40 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #41 | tumannyy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tumannyy
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #42 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #43 | takestan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=takestan
    Processing record #44 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #45 | kodiak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodiak
    Processing record #46 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #47 | provideniya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=provideniya
    Processing record #48 | novoagansk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=novoagansk
    Processing record #49 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #50 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #51 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #52 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #53 | provideniya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=provideniya
    Processing record #54 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #55 | severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=severo-kurilsk
    Processing record #56 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #57 | belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belushya%20guba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #58 | pimentel
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pimentel
    Processing record #59 | vestmannaeyjar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vestmannaeyjar
    Processing record #60 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #61 | nome
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nome
    Processing record #62 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #63 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #64 | tumannyy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tumannyy
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #65 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #66 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #67 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #68 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #69 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #70 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #71 | tual
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tual
    Processing record #72 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #73 | khatanga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khatanga
    Processing record #74 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #75 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #76 | vaitupu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaitupu
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #77 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #78 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #79 | kaitangata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kaitangata
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #80 | arraial do cabo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=arraial%20do%20cabo
    Processing record #81 | vreed en hoop
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vreed%20en%20hoop
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #82 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #83 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #84 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #85 | longyearbyen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=longyearbyen
    Processing record #86 | majene
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=majene
    Processing record #87 | tucuman
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tucuman
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #88 | kodiak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodiak
    Processing record #89 | bokspits
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bokspits
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #90 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #91 | alta floresta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=alta%20floresta
    Processing record #92 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #93 | ancud
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ancud
    Processing record #94 | bourail
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bourail
    Processing record #95 | bethel
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bethel
    Processing record #96 | alotau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=alotau
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #97 | narsaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=narsaq
    Processing record #98 | san policarpo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=san%20policarpo
    Processing record #99 | mahebourg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mahebourg
    Processing record #100 | hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hithadhoo
    Processing record #101 | kytmanovo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kytmanovo
    Processing record #102 | barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barentsburg
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #103 | esperance
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=esperance
    Processing record #104 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #105 | yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yellowknife
    Processing record #106 | lodwar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lodwar
    Processing record #107 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #108 | le port
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=le%20port
    Processing record #109 | ipora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ipora
    Processing record #110 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #111 | greencastle
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=greencastle
    Processing record #112 | sao filipe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sao%20filipe
    Processing record #113 | gat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=gat
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #114 | maragogi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=maragogi
    Processing record #115 | roma
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=roma
    Processing record #116 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #117 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #118 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #119 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #120 | tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tsihombe
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #121 | longyan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=longyan
    Processing record #122 | goderich
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=goderich
    Processing record #123 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #124 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #125 | port lincoln
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20lincoln
    Processing record #126 | traverse city
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=traverse%20city
    Processing record #127 | byron bay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=byron%20bay
    Processing record #128 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #129 | jijiga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jijiga
    Processing record #130 | haines junction
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=haines%20junction
    Processing record #131 | barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barentsburg
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #132 | caravelas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=caravelas
    Processing record #133 | aviles
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=aviles
    Processing record #134 | nizhneyansk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nizhneyansk
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #135 | monrovia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=monrovia
    Processing record #136 | saqqez
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saqqez
    Processing record #137 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #138 | kapustin yar-1
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapustin%20yar-1
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #139 | khatanga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khatanga
    Processing record #140 | dutse
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dutse
    Processing record #141 | college
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=college
    Processing record #142 | deputatskiy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=deputatskiy
    Processing record #143 | chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chokurdakh
    Processing record #144 | trinidad
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=trinidad
    Processing record #145 | tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tasiilaq
    Processing record #146 | clifton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=clifton
    Processing record #147 | lebu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lebu
    Processing record #148 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #149 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #150 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #151 | igarka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=igarka
    Processing record #152 | sayyan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sayyan
    Processing record #153 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #154 | dingle
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dingle
    Processing record #155 | mazamari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mazamari
    Processing record #156 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #157 | khatanga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khatanga
    Processing record #158 | keetmanshoop
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=keetmanshoop
    Processing record #159 | luderitz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=luderitz
    Processing record #160 | tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuktoyaktuk
    Processing record #161 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #162 | merauke
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=merauke
    Processing record #163 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #164 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #165 | torbay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=torbay
    Processing record #166 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #167 | arraial do cabo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=arraial%20do%20cabo
    Processing record #168 | santo antonio do ica
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=santo%20antonio%20do%20ica
    Processing record #169 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #170 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #171 | kaitangata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kaitangata
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #172 | hasaki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hasaki
    Processing record #173 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #174 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #175 | mitu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mitu
    Processing record #176 | katsuura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=katsuura
    Processing record #177 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #178 | inuvik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=inuvik
    Processing record #179 | henties bay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=henties%20bay
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #180 | zapolyarnyy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=zapolyarnyy
    Processing record #181 | yining
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yining
    Processing record #182 | dolbeau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dolbeau
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #183 | bereda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bereda
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #184 | banos
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=banos
    Processing record #185 | amderma
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=amderma
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #186 | tiksi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tiksi
    Processing record #187 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #188 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #189 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #190 | kaseda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kaseda
    Processing record #191 | saldanha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saldanha
    Processing record #192 | taksimo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taksimo
    Processing record #193 | mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mys%20shmidta
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #194 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #195 | amderma
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=amderma
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #196 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #197 | dikson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dikson
    Processing record #198 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #199 | tuatapere
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuatapere
    Processing record #200 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #201 | mount gambier
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mount%20gambier
    Processing record #202 | gamba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=gamba
    Processing record #203 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #204 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #205 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #206 | hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hithadhoo
    Processing record #207 | belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belushya%20guba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #208 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #209 | asau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=asau
    Processing record #210 | kavieng
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kavieng
    Processing record #211 | monroe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=monroe
    Processing record #212 | sitka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sitka
    Processing record #213 | gamba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=gamba
    Processing record #214 | qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qaanaaq
    Processing record #215 | port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20elizabeth
    Processing record #216 | thompson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=thompson
    Processing record #217 | chuy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chuy
    Processing record #218 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #219 | geraldton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=geraldton
    Processing record #220 | sistranda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sistranda
    Processing record #221 | henties bay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=henties%20bay
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #222 | maceio
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=maceio
    Processing record #223 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #224 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #225 | mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mys%20shmidta
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #226 | nago
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nago
    Processing record #227 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #228 | port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20elizabeth
    Processing record #229 | avera
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avera
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #230 | inhambane
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=inhambane
    Processing record #231 | clyde river
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=clyde%20river
    Processing record #232 | saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saskylakh
    Processing record #233 | qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qaanaaq
    Processing record #234 | buraydah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=buraydah
    Processing record #235 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #236 | yulara
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yulara
    Processing record #237 | raisinghnagar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=raisinghnagar
    Processing record #238 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #239 | saldanha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saldanha
    Processing record #240 | half moon bay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=half%20moon%20bay
    Processing record #241 | jeremie
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jeremie
    Processing record #242 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #243 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #244 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #245 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #246 | thompson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=thompson
    Processing record #247 | poum
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=poum
    Processing record #248 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #249 | wamba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=wamba
    Processing record #250 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #251 | adrar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=adrar
    Processing record #252 | korsakov
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=korsakov
    Processing record #253 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #254 | katsuura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=katsuura
    Processing record #255 | teul
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=teul
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #256 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #257 | ellensburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ellensburg
    Processing record #258 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #259 | sao filipe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sao%20filipe
    Processing record #260 | faanui
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=faanui
    Processing record #261 | dogondoutchi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dogondoutchi
    Processing record #262 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #263 | leshukonskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=leshukonskoye
    Processing record #264 | dhidhdhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dhidhdhoo
    Processing record #265 | kaya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kaya
    Processing record #266 | airai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=airai
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #267 | coquimbo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=coquimbo
    Processing record #268 | bundibugyo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bundibugyo
    Processing record #269 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #270 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #271 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #272 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #273 | airai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=airai
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #274 | khovu-aksy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khovu-aksy
    Processing record #275 | clyde river
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=clyde%20river
    Processing record #276 | kahului
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kahului
    Processing record #277 | panlaitan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=panlaitan
    Processing record #278 | vostok
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vostok
    Processing record #279 | saint george
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint%20george
    Processing record #280 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #281 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #282 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #283 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #284 | burgeo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=burgeo
    Processing record #285 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #286 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #287 | henties bay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=henties%20bay
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #288 | dikson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dikson
    Processing record #289 | samatau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=samatau
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #290 | saldanha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saldanha
    Processing record #291 | upernavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=upernavik
    Processing record #292 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #293 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #294 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #295 | belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belushya%20guba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #296 | port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20elizabeth
    Processing record #297 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #298 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #299 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #300 | evensk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=evensk
    Processing record #301 | saint-pierre
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint-pierre
    Processing record #302 | ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ribeira%20grande
    Processing record #303 | eskasem
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=eskasem
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #304 | flinders
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=flinders
    Processing record #305 | ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ribeira%20grande
    Processing record #306 | namibe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=namibe
    Processing record #307 | katsuura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=katsuura
    Processing record #308 | saint george
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint%20george
    Processing record #309 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #310 | mogadishu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mogadishu
    Processing record #311 | clinton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=clinton
    Processing record #312 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #313 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #314 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #315 | tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuktoyaktuk
    Processing record #316 | barrow
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barrow
    Processing record #317 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #318 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #319 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #320 | kavieng
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kavieng
    Processing record #321 | pustoshka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pustoshka
    Processing record #322 | bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bambous%20virieux
    Processing record #323 | leningradskiy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=leningradskiy
    Processing record #324 | khatanga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khatanga
    Processing record #325 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #326 | qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qaanaaq
    Processing record #327 | mackay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mackay
    Processing record #328 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #329 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #330 | aki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=aki
    Processing record #331 | cherskiy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cherskiy
    Processing record #332 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #333 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #334 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #335 | dvorichna
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dvorichna
    Processing record #336 | kodinsk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodinsk
    Processing record #337 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #338 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #339 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #340 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #341 | pochutla
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pochutla
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #342 | vila franca do campo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vila%20franca%20do%20campo
    Processing record #343 | mount gambier
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mount%20gambier
    Processing record #344 | juazeiro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=juazeiro
    Processing record #345 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #346 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #347 | hofn
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hofn
    Processing record #348 | korla
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=korla
    Processing record #349 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #350 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #351 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #352 | lubbock
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lubbock
    Processing record #353 | gweta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=gweta
    Processing record #354 | bintulu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bintulu
    Processing record #355 | codrington
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=codrington
    Processing record #356 | yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yellowknife
    Processing record #357 | kalengwa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kalengwa
    Processing record #358 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #359 | upernavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=upernavik
    Processing record #360 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #361 | torbay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=torbay
    Processing record #362 | half moon bay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=half%20moon%20bay
    Processing record #363 | bonavista
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bonavista
    Processing record #364 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #365 | cardston
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cardston
    Processing record #366 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #367 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #368 | tuggurt
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuggurt
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #369 | leninskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=leninskoye
    Processing record #370 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #371 | utiroa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=utiroa
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #372 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #373 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #374 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #375 | louis trichardt
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=louis%20trichardt
    Processing record #376 | barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barentsburg
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #377 | kajiado
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kajiado
    Processing record #378 | avera
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avera
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #379 | lodja
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lodja
    Processing record #380 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #381 | padang
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=padang
    Processing record #382 | pisco
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pisco
    Processing record #383 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #384 | monte patria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=monte%20patria
    Processing record #385 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #386 | sao filipe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sao%20filipe
    Processing record #387 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #388 | georgetown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=georgetown
    Processing record #389 | balad
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=balad
    Processing record #390 | sinyavskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sinyavskoye
    Processing record #391 | qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qaanaaq
    Processing record #392 | samana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=samana
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #393 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #394 | ponta do sol
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ponta%20do%20sol
    Processing record #395 | azare
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=azare
    Processing record #396 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #397 | nioki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nioki
    Processing record #398 | severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=severo-kurilsk
    Processing record #399 | east london
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=east%20london
    Processing record #400 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #401 | hirara
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hirara
    Processing record #402 | cabedelo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cabedelo
    Processing record #403 | attawapiskat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=attawapiskat
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #404 | mounana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mounana
    Processing record #405 | carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=carnarvon
    Processing record #406 | qasigiannguit
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qasigiannguit
    Processing record #407 | bonavista
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bonavista
    Processing record #408 | seddon
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=seddon
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #409 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #410 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #411 | kaduqli
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kaduqli
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #412 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #413 | eirunepe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=eirunepe
    Processing record #414 | pithora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pithora
    Processing record #415 | chuy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chuy
    Processing record #416 | tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuktoyaktuk
    Processing record #417 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #418 | vammala
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vammala
    Processing record #419 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #420 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #421 | victoria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=victoria
    Processing record #422 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #423 | tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tasiilaq
    Processing record #424 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #425 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #426 | yulara
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yulara
    Processing record #427 | mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mar%20del%20plata
    Processing record #428 | dickinson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dickinson
    Processing record #429 | mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mar%20del%20plata
    Processing record #430 | ruatoria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ruatoria
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #431 | chandler
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chandler
    Processing record #432 | brewster
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=brewster
    Processing record #433 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #434 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #435 | san andres del rabanedo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=san%20andres%20del%20rabanedo
    Processing record #436 | alofi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=alofi
    Processing record #437 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #438 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #439 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #440 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #441 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #442 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #443 | torbay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=torbay
    Processing record #444 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #445 | narsaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=narsaq
    Processing record #446 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #447 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #448 | bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bambous%20virieux
    Processing record #449 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #450 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #451 | longyearbyen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=longyearbyen
    Processing record #452 | ilebo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ilebo
    Processing record #453 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #454 | kamenskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kamenskoye
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #455 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #456 | neyyattinkara
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=neyyattinkara
    Processing record #457 | provideniya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=provideniya
    Processing record #458 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #459 | kilmallock
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kilmallock
    Processing record #460 | yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yellowknife
    Processing record #461 | kajaani
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kajaani
    Processing record #462 | samoded
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=samoded
    Processing record #463 | ponerihouen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ponerihouen
    Processing record #464 | ilhabela
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ilhabela
    Processing record #465 | shimoda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=shimoda
    Processing record #466 | arraial do cabo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=arraial%20do%20cabo
    Processing record #467 | acurenam
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=acurenam
    Processing record #468 | chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chokurdakh
    Processing record #469 | shumskiy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=shumskiy
    Processing record #470 | tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuktoyaktuk
    Processing record #471 | jardim
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jardim
    Processing record #472 | portland
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=portland
    Processing record #473 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #474 | namie
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=namie
    Processing record #475 | shiraz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=shiraz
    Processing record #476 | thompson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=thompson
    Processing record #477 | thai binh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=thai%20binh
    Processing record #478 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #479 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #480 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #481 | yishui
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yishui
    Processing record #482 | oro valley
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=oro%20valley
    Processing record #483 | ludvika
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ludvika
    Processing record #484 | katsuura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=katsuura
    Processing record #485 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #486 | eyl
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=eyl
    Processing record #487 | qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qaanaaq
    Processing record #488 | kawana waters
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kawana%20waters
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #489 | temnikov
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=temnikov
    Processing record #490 | arroyo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=arroyo
    Processing record #491 | muravlenko
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=muravlenko
    Processing record #492 | qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qaanaaq
    Processing record #493 | camacha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=camacha
    Processing record #494 | mongomo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mongomo
    Processing record #495 | arcata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=arcata
    Processing record #496 | port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20elizabeth
    Processing record #497 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #498 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #499 | vermilion
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vermilion
    Processing record #500 | luderitz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=luderitz
    Processing record #501 | alice springs
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=alice%20springs
    Processing record #502 | nikolskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nikolskoye
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #503 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #504 | souillac
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=souillac
    Processing record #505 | wattegama
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=wattegama
    Processing record #506 | sohag
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sohag
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #507 | cidreira
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cidreira
    Processing record #508 | lasa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lasa
    Processing record #509 | yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yellowknife
    Processing record #510 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #511 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #512 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #513 | isangel
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=isangel
    Processing record #514 | zhigansk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=zhigansk
    Processing record #515 | belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belushya%20guba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #516 | riverbank
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=riverbank
    Processing record #517 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #518 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #519 | kahului
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kahului
    Processing record #520 | lichuan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lichuan
    Processing record #521 | lorengau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lorengau
    Processing record #522 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #523 | inirida
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=inirida
    Processing record #524 | namibe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=namibe
    Processing record #525 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #526 | alekseyevsk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=alekseyevsk
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #527 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #528 | tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tasiilaq
    Processing record #529 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #530 | barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barentsburg
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #531 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #532 | tukrah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tukrah
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #533 | souillac
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=souillac
    Processing record #534 | hambantota
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hambantota
    Processing record #535 | lixourion
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lixourion
    Processing record #536 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #537 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #538 | tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tsihombe
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #539 | thompson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=thompson
    Processing record #540 | phalombe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=phalombe
    Processing record #541 | mtambile
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mtambile
    Processing record #542 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #543 | lavrentiya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lavrentiya
    Processing record #544 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #545 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #546 | inverell
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=inverell
    Processing record #547 | ivanteyevka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ivanteyevka
    Processing record #548 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #549 | balabac
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=balabac
    Processing record #550 | victoria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=victoria
    Processing record #551 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #552 | east london
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=east%20london
    Processing record #553 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #554 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #555 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #556 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #557 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #558 | ilulissat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ilulissat
    Processing record #559 | louisbourg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=louisbourg
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #560 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #561 | meyungs
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=meyungs
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #562 | barentu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barentu
    Processing record #563 | zaysan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=zaysan
    Processing record #564 | sawtell
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sawtell
    Processing record #565 | inhambane
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=inhambane
    Processing record #566 | oblivskaya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=oblivskaya
    Processing record #567 | geraldton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=geraldton
    Processing record #568 | calvinia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=calvinia
    Processing record #569 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #570 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #571 | martinsville
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=martinsville
    Processing record #572 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #573 | agadez
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=agadez
    Processing record #574 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #575 | innisfail
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=innisfail
    Processing record #576 | laje
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=laje
    Processing record #577 | champaign
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=champaign
    Processing record #578 | xining
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=xining
    Processing record #579 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #580 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #581 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #582 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #583 | vaitupu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaitupu
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #584 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #585 | saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saskylakh
    Processing record #586 | collie
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=collie
    Processing record #587 | bhabua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bhabua
    Processing record #588 | kuching
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kuching
    Processing record #589 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #590 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #591 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #592 | vung tau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vung%20tau
    Processing record #593 | bochnia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bochnia
    Processing record #594 | lavrentiya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lavrentiya
    Processing record #595 | lieksa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lieksa
    Processing record #596 | kodiak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodiak
    Processing record #597 | hunza
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hunza
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #598 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #599 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #600 | saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saskylakh
    Processing record #601 | yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yellowknife
    Processing record #602 | barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barentsburg
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #603 | te anau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=te%20anau
    Processing record #604 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #605 | barrow
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barrow
    Processing record #606 | roma
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=roma
    Processing record #607 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #608 | kruisfontein
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kruisfontein
    Processing record #609 | arraial do cabo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=arraial%20do%20cabo
    Processing record #610 | cidreira
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cidreira
    Processing record #611 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #612 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #613 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #614 | phu ly
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=phu%20ly
    Processing record #615 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #616 | kahului
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kahului
    Processing record #617 | kushima
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kushima
    Processing record #618 | nizhnyaya omka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nizhnyaya%20omka
    Processing record #619 | lebu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lebu
    Processing record #620 | mana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mana
    Processing record #621 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #622 | dallas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dallas
    Processing record #623 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #624 | belaya gora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belaya%20gora
    Processing record #625 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #626 | nouadhibou
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nouadhibou
    Processing record #627 | gannan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=gannan
    Processing record #628 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #629 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #630 | airai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=airai
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #631 | chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chokurdakh
    Processing record #632 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #633 | taybad
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taybad
    Processing record #634 | samusu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=samusu
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #635 | juneau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=juneau
    Processing record #636 | quebec
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=quebec
    Processing record #637 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #638 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #639 | kununurra
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kununurra
    Processing record #640 | hambantota
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hambantota
    Processing record #641 | saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saskylakh
    Processing record #642 | grand river south east
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=grand%20river%20south%20east
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #643 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #644 | twentynine palms
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=twentynine%20palms
    Processing record #645 | nanortalik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nanortalik
    Processing record #646 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #647 | aksha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=aksha
    Processing record #648 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #649 | axim
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=axim
    Processing record #650 | karratha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=karratha
    Processing record #651 | gasa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=gasa
    Processing record #652 | mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mar%20del%20plata
    Processing record #653 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #654 | bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bambous%20virieux
    Processing record #655 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #656 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #657 | mtinko
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mtinko
    Processing record #658 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #659 | kodiak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodiak
    Processing record #660 | ilulissat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ilulissat
    Processing record #661 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #662 | khatanga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khatanga
    Processing record #663 | tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuktoyaktuk
    Processing record #664 | airai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=airai
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #665 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #666 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #667 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #668 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #669 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #670 | burnie
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=burnie
    Processing record #671 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #672 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #673 | north bend
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=north%20bend
    Processing record #674 | sembakung
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sembakung
    Processing record #675 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #676 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #677 | bagu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bagu
    Processing record #678 | kamenskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kamenskoye
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #679 | dikson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dikson
    Processing record #680 | vagur
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vagur
    Processing record #681 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #682 | tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tsihombe
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #683 | hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hithadhoo
    Processing record #684 | bur gabo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bur%20gabo
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #685 | zemio
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=zemio
    Processing record #686 | tabiauea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tabiauea
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #687 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #688 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #689 | hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hithadhoo
    Processing record #690 | kabare
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kabare
    Processing record #691 | manali
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=manali
    Processing record #692 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #693 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #694 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #695 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #696 | torbay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=torbay
    Processing record #697 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #698 | obluche
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=obluche
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #699 | khuzdar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khuzdar
    Processing record #700 | makung
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=makung
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #701 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #702 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #703 | burns lake
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=burns%20lake
    Processing record #704 | mahebourg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mahebourg
    Processing record #705 | sidi ali
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sidi%20ali
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #706 | zaranj
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=zaranj
    Processing record #707 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #708 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #709 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #710 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #711 | sept-iles
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sept-iles
    Processing record #712 | diu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=diu
    Processing record #713 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #714 | abnub
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=abnub
    Processing record #715 | hamilton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hamilton
    Processing record #716 | merrill
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=merrill
    Processing record #717 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #718 | sedelnikovo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sedelnikovo
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #719 | jadu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jadu
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #720 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #721 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #722 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #723 | belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belushya%20guba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #724 | esperance
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=esperance
    Processing record #725 | luganville
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=luganville
    Processing record #726 | itarema
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=itarema
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #727 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #728 | grindavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=grindavik
    Processing record #729 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #730 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #731 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #732 | cockburn town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cockburn%20town
    Processing record #733 | baruun-urt
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=baruun-urt
    Processing record #734 | provideniya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=provideniya
    Processing record #735 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #736 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #737 | banjar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=banjar
    Processing record #738 | meulaboh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=meulaboh
    Processing record #739 | kavieng
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kavieng
    Processing record #740 | lata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lata
    Processing record #741 | chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chokurdakh
    Processing record #742 | itarema
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=itarema
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #743 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #744 | birao
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=birao
    Processing record #745 | tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tsihombe
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #746 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #747 | kununurra
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kununurra
    Processing record #748 | pringsewu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pringsewu
    Processing record #749 | zvishavane
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=zvishavane
    Processing record #750 | arlit
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=arlit
    Processing record #751 | nichinan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nichinan
    Processing record #752 | grand river south east
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=grand%20river%20south%20east
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #753 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #754 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #755 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #756 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #757 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #758 | hue
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hue
    Processing record #759 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #760 | beringovskiy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=beringovskiy
    Processing record #761 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #762 | saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saskylakh
    Processing record #763 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #764 | suntar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=suntar
    Processing record #765 | kerteh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kerteh
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #766 | pangkalanbuun
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pangkalanbuun
    Processing record #767 | mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mys%20shmidta
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #768 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #769 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #770 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #771 | belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belushya%20guba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #772 | mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mar%20del%20plata
    Processing record #773 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #774 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #775 | ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ribeira%20grande
    Processing record #776 | sinop
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sinop
    Processing record #777 | dikson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dikson
    Processing record #778 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #779 | mana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mana
    Processing record #780 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #781 | saint-augustin
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint-augustin
    Processing record #782 | mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mys%20shmidta
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #783 | kilindoni
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kilindoni
    Processing record #784 | east london
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=east%20london
    Processing record #785 | sitka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sitka
    Processing record #786 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #787 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #788 | nanortalik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nanortalik
    Processing record #789 | lata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lata
    Processing record #790 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #791 | college
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=college
    Processing record #792 | lebu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lebu
    Processing record #793 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #794 | ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ribeira%20grande
    Processing record #795 | lavrentiya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lavrentiya
    Processing record #796 | luanda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=luanda
    Processing record #797 | saint-pierre
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint-pierre
    Processing record #798 | qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qaanaaq
    Processing record #799 | port keats
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20keats
    Processing record #800 | wuwei
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=wuwei
    Processing record #801 | sentyabrskiy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sentyabrskiy
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #802 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #803 | tucumcari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tucumcari
    Processing record #804 | chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chokurdakh
    Processing record #805 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #806 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #807 | niquelandia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=niquelandia
    Processing record #808 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #809 | krasnovishersk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=krasnovishersk
    Processing record #810 | whitianga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=whitianga
    Processing record #811 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #812 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #813 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #814 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #815 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #816 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #817 | cabo san lucas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cabo%20san%20lucas
    Processing record #818 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #819 | nizhneyansk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nizhneyansk
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #820 | zhoucheng
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=zhoucheng
    Processing record #821 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #822 | saint-philippe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint-philippe
    Processing record #823 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #824 | pevek
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pevek
    Processing record #825 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #826 | ternate
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ternate
    Processing record #827 | barquisimeto
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barquisimeto
    Processing record #828 | upernavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=upernavik
    Processing record #829 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #830 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #831 | vaitupu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaitupu
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #832 | little current
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=little%20current
    Processing record #833 | raudeberg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=raudeberg
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #834 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #835 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #836 | cayenne
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cayenne
    Processing record #837 | ancud
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ancud
    Processing record #838 | dzhebariki-khaya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dzhebariki-khaya
    Processing record #839 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #840 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #841 | dayong
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dayong
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #842 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #843 | tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuktoyaktuk
    Processing record #844 | yulara
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yulara
    Processing record #845 | clyde river
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=clyde%20river
    Processing record #846 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #847 | tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuktoyaktuk
    Processing record #848 | chuy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chuy
    Processing record #849 | odweyne
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=odweyne
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #850 | chuy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chuy
    Processing record #851 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #852 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #853 | darovskoy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=darovskoy
    Processing record #854 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #855 | grand gaube
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=grand%20gaube
    Processing record #856 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #857 | ponta delgada
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ponta%20delgada
    Processing record #858 | tuatapere
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuatapere
    Processing record #859 | catalina
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=catalina
    Processing record #860 | belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belushya%20guba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #861 | nome
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nome
    Processing record #862 | upernavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=upernavik
    Processing record #863 | barrow
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barrow
    Processing record #864 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #865 | niagara falls
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=niagara%20falls
    Processing record #866 | gerede
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=gerede
    Processing record #867 | ilulissat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ilulissat
    Processing record #868 | salinopolis
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=salinopolis
    Processing record #869 | sydney
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sydney
    Processing record #870 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #871 | saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saskylakh
    Processing record #872 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #873 | roald
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=roald
    Processing record #874 | havre-saint-pierre
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=havre-saint-pierre
    Processing record #875 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #876 | tuatapere
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuatapere
    Processing record #877 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #878 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #879 | tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tsihombe
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #880 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #881 | gat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=gat
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #882 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #883 | mehamn
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mehamn
    Processing record #884 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #885 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #886 | urumqi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=urumqi
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #887 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #888 | ixtapa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ixtapa
    Processing record #889 | shache
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=shache
    Processing record #890 | bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bengkulu
    Processing record #891 | bustamante
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bustamante
    Processing record #892 | namibe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=namibe
    Processing record #893 | mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mar%20del%20plata
    Processing record #894 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #895 | girona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=girona
    Processing record #896 | vaitupu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaitupu
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #897 | pitimbu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pitimbu
    Processing record #898 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #899 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #900 | mariakani
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mariakani
    Processing record #901 | ribas do rio pardo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ribas%20do%20rio%20pardo
    Processing record #902 | morshansk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=morshansk
    Processing record #903 | kabinda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kabinda
    Processing record #904 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #905 | madhupur
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=madhupur
    Processing record #906 | sinnamary
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sinnamary
    Processing record #907 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #908 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #909 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #910 | vestmannaeyjar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vestmannaeyjar
    Processing record #911 | bandarbeyla
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bandarbeyla
    Processing record #912 | upernavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=upernavik
    Processing record #913 | saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saskylakh
    Processing record #914 | poum
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=poum
    Processing record #915 | coyah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=coyah
    Processing record #916 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #917 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #918 | finschhafen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=finschhafen
    Processing record #919 | taoudenni
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taoudenni
    Processing record #920 | carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=carnarvon
    Processing record #921 | fort nelson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=fort%20nelson
    Processing record #922 | nizhneyansk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nizhneyansk
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #923 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #924 | ilulissat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ilulissat
    Processing record #925 | luderitz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=luderitz
    Processing record #926 | kavieng
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kavieng
    Processing record #927 | barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barentsburg
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #928 | sergeyevka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sergeyevka
    Processing record #929 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #930 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #931 | barrow
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barrow
    Processing record #932 | nikolskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nikolskoye
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #933 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #934 | ossora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ossora
    Processing record #935 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #936 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #937 | severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=severo-kurilsk
    Processing record #938 | kuryk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kuryk
    Processing record #939 | yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yellowknife
    Processing record #940 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #941 | washington
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=washington
    Processing record #942 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #943 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #944 | awjilah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=awjilah
    Processing record #945 | sohag
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sohag
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #946 | thinadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=thinadhoo
    Processing record #947 | eyl
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=eyl
    Processing record #948 | faanui
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=faanui
    Processing record #949 | harper
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=harper
    Processing record #950 | kattivakkam
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kattivakkam
    Processing record #951 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #952 | taoudenni
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taoudenni
    Processing record #953 | constitucion
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=constitucion
    Processing record #954 | iguape
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=iguape
    Processing record #955 | san joaquin
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=san%20joaquin
    Processing record #956 | srednekolymsk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=srednekolymsk
    Processing record #957 | fortuna
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=fortuna
    Processing record #958 | ostrovnoy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ostrovnoy
    Processing record #959 | mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mys%20shmidta
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #960 | asau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=asau
    Processing record #961 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #962 | huautla
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=huautla
    Processing record #963 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #964 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #965 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #966 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #967 | beringovskiy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=beringovskiy
    Processing record #968 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #969 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #970 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #971 | lebu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lebu
    Processing record #972 | ancud
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ancud
    Processing record #973 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #974 | port lincoln
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20lincoln
    Processing record #975 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #976 | mitsamiouli
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mitsamiouli
    Processing record #977 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #978 | chuy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chuy
    Processing record #979 | barrow
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barrow
    Processing record #980 | barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barentsburg
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #981 | zhigansk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=zhigansk
    Processing record #982 | yar-sale
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yar-sale
    Processing record #983 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #984 | griffith
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=griffith
    Processing record #985 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #986 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #987 | tabas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tabas
    Processing record #988 | cabo san lucas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cabo%20san%20lucas
    Processing record #989 | agadez
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=agadez
    Processing record #990 | mutsamudu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mutsamudu
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #991 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #992 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #993 | yulara
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yulara
    Processing record #994 | naze
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=naze
    Processing record #995 | vardo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vardo
    Processing record #996 | malakal
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=malakal
    Processing record #997 | lebu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lebu
    Processing record #998 | touros
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=touros
    Processing record #999 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #1000 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #1001 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #1002 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #1003 | san vicente de canete
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=san%20vicente%20de%20canete
    Processing record #1004 | kamenka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kamenka
    Processing record #1005 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #1006 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #1007 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #1008 | odweyne
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=odweyne
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1009 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1010 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1011 | camana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=camana
    Processing record #1012 | kaitangata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kaitangata
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1013 | bathsheba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bathsheba
    Processing record #1014 | sao joao da barra
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sao%20joao%20da%20barra
    Processing record #1015 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #1016 | namatanai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=namatanai
    Processing record #1017 | shchelyayur
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=shchelyayur
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1018 | yurty
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yurty
    Processing record #1019 | san patricio
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=san%20patricio
    Processing record #1020 | saldanha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saldanha
    Processing record #1021 | ksenyevka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ksenyevka
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1022 | severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=severo-kurilsk
    Processing record #1023 | bajo baudo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bajo%20baudo
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1024 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #1025 | yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yellowknife
    Processing record #1026 | roald
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=roald
    Processing record #1027 | georgetown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=georgetown
    Processing record #1028 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #1029 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #1030 | aklavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=aklavik
    Processing record #1031 | ponta do sol
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ponta%20do%20sol
    Processing record #1032 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1033 | jaisalmer
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jaisalmer
    Processing record #1034 | victoria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=victoria
    Processing record #1035 | khatanga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khatanga
    Processing record #1036 | pochinki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pochinki
    Processing record #1037 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #1038 | clyde river
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=clyde%20river
    Processing record #1039 | georgetown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=georgetown
    Processing record #1040 | viedma
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=viedma
    Processing record #1041 | cidreira
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cidreira
    Processing record #1042 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #1043 | amderma
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=amderma
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1044 | kloulklubed
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kloulklubed
    Processing record #1045 | bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bengkulu
    Processing record #1046 | tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tasiilaq
    Processing record #1047 | quang ngai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=quang%20ngai
    Processing record #1048 | pevek
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pevek
    Processing record #1049 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1050 | belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belushya%20guba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1051 | kuche
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kuche
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1052 | santa cruz de la palma
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=santa%20cruz%20de%20la%20palma
    Processing record #1053 | qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=qaanaaq
    Processing record #1054 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #1055 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #1056 | ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ribeira%20grande
    Processing record #1057 | kavieng
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kavieng
    Processing record #1058 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #1059 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #1060 | itarema
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=itarema
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1061 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1062 | coquimbo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=coquimbo
    Processing record #1063 | maceio
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=maceio
    Processing record #1064 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1065 | kodiak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodiak
    Processing record #1066 | port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20elizabeth
    Processing record #1067 | balud
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=balud
    Processing record #1068 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #1069 | tura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tura
    Processing record #1070 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1071 | baruun-urt
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=baruun-urt
    Processing record #1072 | ust-nera
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ust-nera
    Processing record #1073 | santiago del estero
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=santiago%20del%20estero
    Processing record #1074 | hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hithadhoo
    Processing record #1075 | luderitz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=luderitz
    Processing record #1076 | lorengau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lorengau
    Processing record #1077 | ayr
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ayr
    Processing record #1078 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #1079 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1080 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #1081 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1082 | roros
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=roros
    Processing record #1083 | kodiak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodiak
    Processing record #1084 | saint-philippe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint-philippe
    Processing record #1085 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #1086 | chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chokurdakh
    Processing record #1087 | los llanos de aridane
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=los%20llanos%20de%20aridane
    Processing record #1088 | faya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=faya
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1089 | mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mar%20del%20plata
    Processing record #1090 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1091 | victoria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=victoria
    Processing record #1092 | alofi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=alofi
    Processing record #1093 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1094 | thinadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=thinadhoo
    Processing record #1095 | tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tasiilaq
    Processing record #1096 | klaksvik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=klaksvik
    Processing record #1097 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #1098 | hirara
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hirara
    Processing record #1099 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1100 | imphal
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=imphal
    Processing record #1101 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #1102 | san carlos de bariloche
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=san%20carlos%20de%20bariloche
    Processing record #1103 | saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saskylakh
    Processing record #1104 | aksha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=aksha
    Processing record #1105 | touros
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=touros
    Processing record #1106 | talnakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=talnakh
    Processing record #1107 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1108 | belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=belushya%20guba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1109 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1110 | saint-philippe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint-philippe
    Processing record #1111 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1112 | cumpas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cumpas
    Processing record #1113 | dikson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dikson
    Processing record #1114 | cibitoke
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cibitoke
    Processing record #1115 | geraldton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=geraldton
    Processing record #1116 | barrow
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barrow
    Processing record #1117 | mogadishu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mogadishu
    Processing record #1118 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1119 | adrar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=adrar
    Processing record #1120 | jieshou
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jieshou
    Processing record #1121 | hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hithadhoo
    Processing record #1122 | cabo san lucas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cabo%20san%20lucas
    Processing record #1123 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #1124 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #1125 | khatanga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khatanga
    Processing record #1126 | dunedin
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dunedin
    Processing record #1127 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1128 | mocuba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mocuba
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1129 | maceio
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=maceio
    Processing record #1130 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #1131 | guerrero negro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=guerrero%20negro
    Processing record #1132 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1133 | pabrade
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pabrade
    Processing record #1134 | general roca
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=general%20roca
    Processing record #1135 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1136 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1137 | ozerki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ozerki
    Processing record #1138 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1139 | puerto madryn
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20madryn
    Processing record #1140 | richards bay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=richards%20bay
    Processing record #1141 | butaritari
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butaritari
    Processing record #1142 | maunabo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=maunabo
    Processing record #1143 | tutoia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tutoia
    Processing record #1144 | sorong
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sorong
    Processing record #1145 | havre-saint-pierre
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=havre-saint-pierre
    Processing record #1146 | grindavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=grindavik
    Processing record #1147 | ponta do sol
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ponta%20do%20sol
    Processing record #1148 | east london
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=east%20london
    Processing record #1149 | lorengau
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lorengau
    Processing record #1150 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1151 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #1152 | the valley
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=the%20valley
    Processing record #1153 | east london
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=east%20london
    Processing record #1154 | attawapiskat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=attawapiskat
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1155 | kuching
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kuching
    Processing record #1156 | rayong
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rayong
    Processing record #1157 | port hedland
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20hedland
    Processing record #1158 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #1159 | faanui
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=faanui
    Processing record #1160 | grand gaube
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=grand%20gaube
    Processing record #1161 | fort nelson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=fort%20nelson
    Processing record #1162 | daru
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=daru
    Processing record #1163 | katsuura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=katsuura
    Processing record #1164 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1165 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1166 | port augusta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20augusta
    Processing record #1167 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1168 | yinchuan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yinchuan
    Processing record #1169 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1170 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1171 | khuzhir
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khuzhir
    Processing record #1172 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1173 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #1174 | bay roberts
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bay%20roberts
    Processing record #1175 | amderma
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=amderma
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1176 | carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=carnarvon
    Processing record #1177 | saldanha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saldanha
    Processing record #1178 | hambantota
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hambantota
    Processing record #1179 | upernavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=upernavik
    Processing record #1180 | nelson bay
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nelson%20bay
    Processing record #1181 | biltine
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=biltine
    Processing record #1182 | huazhou
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=huazhou
    Processing record #1183 | boulsa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=boulsa
    Processing record #1184 | ponta do sol
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ponta%20do%20sol
    Processing record #1185 | lasa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lasa
    Processing record #1186 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #1187 | san patricio
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=san%20patricio
    Processing record #1188 | cabo san lucas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cabo%20san%20lucas
    Processing record #1189 | yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yellowknife
    Processing record #1190 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1191 | victoria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=victoria
    Processing record #1192 | nishihara
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nishihara
    Processing record #1193 | le port
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=le%20port
    Processing record #1194 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1195 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1196 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #1197 | barrhead
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=barrhead
    Processing record #1198 | noumea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=noumea
    Processing record #1199 | huntington
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=huntington
    Processing record #1200 | gat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=gat
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1201 | longyearbyen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=longyearbyen
    Processing record #1202 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #1203 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1204 | tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tsihombe
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1205 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1206 | saint-philippe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint-philippe
    Processing record #1207 | kebemer
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kebemer
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1208 | kodiak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodiak
    Processing record #1209 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1210 | tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tasiilaq
    Processing record #1211 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1212 | baijiantan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=baijiantan
    Processing record #1213 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #1214 | ketchikan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ketchikan
    Processing record #1215 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1216 | burnie
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=burnie
    Processing record #1217 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1218 | chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chokurdakh
    Processing record #1219 | buala
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=buala
    Processing record #1220 | yar-sale
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yar-sale
    Processing record #1221 | tiksi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tiksi
    Processing record #1222 | gurskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=gurskoye
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1223 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #1224 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1225 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1226 | tahe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tahe
    Processing record #1227 | mbanza-ngungu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mbanza-ngungu
    Processing record #1228 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #1229 | progreso
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=progreso
    Processing record #1230 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #1231 | kamaishi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kamaishi
    Processing record #1232 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #1233 | chumikan
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chumikan
    Processing record #1234 | thompson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=thompson
    Processing record #1235 | nam tha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nam%20tha
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1236 | novoagansk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=novoagansk
    Processing record #1237 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #1238 | hay river
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hay%20river
    Processing record #1239 | kenai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kenai
    Processing record #1240 | kavaratti
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kavaratti
    Processing record #1241 | dauphin
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dauphin
    Processing record #1242 | mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mys%20shmidta
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1243 | boone
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=boone
    Processing record #1244 | aklavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=aklavik
    Processing record #1245 | norman wells
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=norman%20wells
    Processing record #1246 | ilulissat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ilulissat
    Processing record #1247 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #1248 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #1249 | avera
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avera
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1250 | kruisfontein
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kruisfontein
    Processing record #1251 | salalah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=salalah
    Processing record #1252 | chagda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chagda
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1253 | vicksburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vicksburg
    Processing record #1254 | carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=carnarvon
    Processing record #1255 | upernavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=upernavik
    Processing record #1256 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #1257 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #1258 | kamenskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kamenskoye
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1259 | nikki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nikki
    Processing record #1260 | saint george
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint%20george
    Processing record #1261 | vaitupu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaitupu
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1262 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #1263 | leningradskiy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=leningradskiy
    Processing record #1264 | sao filipe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sao%20filipe
    Processing record #1265 | camacha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=camacha
    Processing record #1266 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #1267 | leningradskiy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=leningradskiy
    Processing record #1268 | kavaratti
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kavaratti
    Processing record #1269 | san cristobal
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=san%20cristobal
    Processing record #1270 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1271 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #1272 | hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hithadhoo
    Processing record #1273 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1274 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1275 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1276 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #1277 | tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tasiilaq
    Processing record #1278 | saldanha
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saldanha
    Processing record #1279 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #1280 | port hedland
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20hedland
    Processing record #1281 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1282 | bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bambous%20virieux
    Processing record #1283 | rongcheng
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rongcheng
    Processing record #1284 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #1285 | moussoro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=moussoro
    Processing record #1286 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1287 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1288 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1289 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1290 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1291 | isangel
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=isangel
    Processing record #1292 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #1293 | kaabong
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kaabong
    Processing record #1294 | medea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=medea
    Processing record #1295 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #1296 | hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hithadhoo
    Processing record #1297 | bubaque
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bubaque
    Processing record #1298 | sao miguel do araguaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sao%20miguel%20do%20araguaia
    Processing record #1299 | mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mar%20del%20plata
    Processing record #1300 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1301 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1302 | tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tasiilaq
    Processing record #1303 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #1304 | marsa matruh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=marsa%20matruh
    Processing record #1305 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #1306 | kavieng
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kavieng
    Processing record #1307 | houma
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=houma
    Processing record #1308 | bathsheba
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bathsheba
    Processing record #1309 | westport
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=westport
    Processing record #1310 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #1311 | ostrovnoy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ostrovnoy
    Processing record #1312 | hilo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hilo
    Processing record #1313 | yaring
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yaring
    Processing record #1314 | kulhudhuffushi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kulhudhuffushi
    Processing record #1315 | carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=carnarvon
    Processing record #1316 | norman wells
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=norman%20wells
    Processing record #1317 | northam
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=northam
    Processing record #1318 | mataura
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mataura
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1319 | santa rosa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=santa%20rosa
    Processing record #1320 | china
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=china
    Processing record #1321 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1322 | thompson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=thompson
    Processing record #1323 | kodiak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodiak
    Processing record #1324 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1325 | russell
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=russell
    Processing record #1326 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #1327 | chuy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chuy
    Processing record #1328 | attawapiskat
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=attawapiskat
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1329 | bethel
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bethel
    Processing record #1330 | dingle
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dingle
    Processing record #1331 | jieshi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jieshi
    Processing record #1332 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1333 | mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mar%20del%20plata
    Processing record #1334 | hermanus
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hermanus
    Processing record #1335 | svetlaya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=svetlaya
    Processing record #1336 | kodiak
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kodiak
    Processing record #1337 | nuuk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nuuk
    Processing record #1338 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #1339 | hasaki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hasaki
    Processing record #1340 | upernavik
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=upernavik
    Processing record #1341 | alexandria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=alexandria
    Processing record #1342 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #1343 | butembo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=butembo
    Processing record #1344 | illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=illoqqortoormiut
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1345 | thinadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=thinadhoo
    Processing record #1346 | lawrenceburg
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lawrenceburg
    Processing record #1347 | cidreira
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cidreira
    Processing record #1348 | salalah
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=salalah
    Processing record #1349 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #1350 | lashio
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lashio
    Processing record #1351 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #1352 | svetlogorsk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=svetlogorsk
    Processing record #1353 | namibe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=namibe
    Processing record #1354 | port blair
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20blair
    Processing record #1355 | jumla
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jumla
    Processing record #1356 | jamestown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=jamestown
    Processing record #1357 | erenhot
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=erenhot
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1358 | galle
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=galle
    Processing record #1359 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1360 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #1361 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #1362 | micco
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=micco
    Processing record #1363 | faanui
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=faanui
    Processing record #1364 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #1365 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #1366 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #1367 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #1368 | bonavista
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bonavista
    Processing record #1369 | alpoyeca
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=alpoyeca
    Processing record #1370 | provideniya
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=provideniya
    Processing record #1371 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1372 | cidreira
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cidreira
    Processing record #1373 | victoria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=victoria
    Processing record #1374 | cassilandia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cassilandia
    Processing record #1375 | saint-augustin
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint-augustin
    Processing record #1376 | strelka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=strelka
    Processing record #1377 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #1378 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1379 | hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hithadhoo
    Processing record #1380 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1381 | bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bredasdorp
    Processing record #1382 | tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tsihombe
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1383 | hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hithadhoo
    Processing record #1384 | mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mys%20shmidta
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1385 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1386 | georgetown
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=georgetown
    Processing record #1387 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #1388 | iqaluit
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=iqaluit
    Processing record #1389 | fort saint james
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=fort%20saint%20james
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1390 | dikson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dikson
    Processing record #1391 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1392 | khandyga
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=khandyga
    Processing record #1393 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #1394 | airai
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=airai
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1395 | manyana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=manyana
    Processing record #1396 | chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=chokurdakh
    Processing record #1397 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1398 | palabuhanratu
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=palabuhanratu
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1399 | mahibadhoo
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mahibadhoo
    Processing record #1400 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #1401 | iqaluit
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=iqaluit
    Processing record #1402 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #1403 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1404 | nome
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nome
    Processing record #1405 | kahului
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kahului
    Processing record #1406 | evensk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=evensk
    Processing record #1407 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1408 | mali
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mali
    Processing record #1409 | biltine
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=biltine
    Processing record #1410 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1411 | mirabad
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mirabad
    Processing record #1412 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #1413 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1414 | talnakh
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=talnakh
    Processing record #1415 | nuuk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=nuuk
    Processing record #1416 | lompoc
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=lompoc
    Processing record #1417 | touros
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=touros
    Processing record #1418 | werda
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=werda
    Processing record #1419 | kunming
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kunming
    Processing record #1420 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #1421 | ushtobe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushtobe
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1422 | vaini
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vaini
    Processing record #1423 | kapaa
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kapaa
    Processing record #1424 | sao joao da barra
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=sao%20joao%20da%20barra
    Processing record #1425 | rikitea
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=rikitea
    Processing record #1426 | mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mys%20shmidta
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1427 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1428 | hasaki
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hasaki
    Processing record #1429 | yar-sale
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yar-sale
    Processing record #1430 | cockburn harbour
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cockburn%20harbour
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1431 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1432 | castro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=castro
    Processing record #1433 | vestmannaeyjar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vestmannaeyjar
    Processing record #1434 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1435 | namibe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=namibe
    Processing record #1436 | northam
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=northam
    Processing record #1437 | yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yellowknife
    Processing record #1438 | pevek
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pevek
    Processing record #1439 | camana
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=camana
    Processing record #1440 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #1441 | busselton
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=busselton
    Processing record #1442 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1443 | pervomayskoye
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=pervomayskoye
    Processing record #1444 | taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=taolanaro
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1445 | port alfred
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=port%20alfred
    Processing record #1446 | bourail
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bourail
    Processing record #1447 | blytheville
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=blytheville
    Processing record #1448 | albany
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=albany
    Processing record #1449 | atuona
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=atuona
    Processing record #1450 | luderitz
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=luderitz
    Processing record #1451 | tiksi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tiksi
    Processing record #1452 | tateyama
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tateyama
    Processing record #1453 | omboue
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=omboue
    Processing record #1454 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #1455 | zhigansk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=zhigansk
    Processing record #1456 | kimberley
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=kimberley
    Processing record #1457 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1458 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1459 | tuggurt
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tuggurt
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1460 | new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=new%20norfolk
    Processing record #1461 | severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=severo-kurilsk
    Processing record #1462 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1463 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1464 | tiksi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tiksi
    Processing record #1465 | burica
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=burica
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1466 | tiksi
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=tiksi
    Processing record #1467 | avera
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avera
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1468 | bluff
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=bluff
    Processing record #1469 | den helder
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=den%20helder
    Processing record #1470 | yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=yellowknife
    Processing record #1471 | avarua
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=avarua
    Processing record #1472 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1473 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1474 | formoso do araguaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=formoso%20do%20araguaia
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1475 | changji
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=changji
    Processing record #1476 | puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=puerto%20ayora
    Processing record #1477 | ulaanbaatar
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ulaanbaatar
    Processing record #1478 | dwarka
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=dwarka
    Processing record #1479 | mezen
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mezen
    Processing record #1480 | ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=ushuaia
    Processing record #1481 | cape town
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cape%20town
    Processing record #1482 | vila do maio
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=vila%20do%20maio
    Processing record #1483 | fort nelson
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=fort%20nelson
    Processing record #1484 | cherskiy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=cherskiy
    Processing record #1485 | himora
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=himora
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1486 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1487 | palmer
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=palmer
    Processing record #1488 | hobart
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=hobart
    Processing record #1489 | victoria
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=victoria
    Processing record #1490 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1491 | honningsvag
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=honningsvag
    Processing record #1492 | margate
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=margate
    Processing record #1493 | saint-philippe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=saint-philippe
    Processing record #1494 | namibe
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=namibe
    Processing record #1495 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
    Processing record #1496 | mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=mar%20del%20plata
    Processing record #1497 | limoges
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=limoges
    Processing record #1498 | meyungs
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=meyungs
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1499 | skalistyy
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=skalistyy
    (*City data NOT found. Moving on to the next city...)
     
    Processing record #1500 | punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=Imperial&APPID=a0012a4da90d2f8b7cddd85fa84e627f&q=punta%20arenas
     
    ---------------------------
    Data Retrieval Complete
    ---------------------------



```python
weather_dict = {"City": city_list, "Cloudiness": cloudiness_list, 
                "Country": country_list, "Date": date_list, "Humidity": humidity_list, 
                "Lat": lat_list, "Lng": long_list, "Max Temp": max_temp_list, 
                "Wind Speed": wind_speed_list}

weather_data_df = pd.DataFrame(weather_dict)
```


```python
final_weather_df = weather_data_df.drop_duplicates(['City'])
final_duplicate_check = final_weather_df['City'].value_counts()
final_duplicate_check.head()
```




    Bethel          1
    Atuona          1
    Alofi           1
    General Roca    1
    Lieksa          1
    Name: City, dtype: int64




```python
final_weather_df.count()
```




    City          513
    Cloudiness    513
    Country       513
    Date          513
    Humidity      513
    Lat           513
    Lng           513
    Max Temp      513
    Wind Speed    513
    dtype: int64




```python
final_weather_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>City</th>
      <th>Cloudiness</th>
      <th>Country</th>
      <th>Date</th>
      <th>Humidity</th>
      <th>Lat</th>
      <th>Lng</th>
      <th>Max Temp</th>
      <th>Wind Speed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Vilyuysk</td>
      <td>24</td>
      <td>RU</td>
      <td>1512355504</td>
      <td>43</td>
      <td>63.76</td>
      <td>121.62</td>
      <td>-27.64</td>
      <td>2.71</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Port Alfred</td>
      <td>24</td>
      <td>ZA</td>
      <td>1512355131</td>
      <td>100</td>
      <td>-33.59</td>
      <td>26.89</td>
      <td>62.09</td>
      <td>3.27</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pangkalanbuun</td>
      <td>12</td>
      <td>ID</td>
      <td>1512355281</td>
      <td>96</td>
      <td>-2.68</td>
      <td>111.62</td>
      <td>85.54</td>
      <td>3.94</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Georgetown</td>
      <td>56</td>
      <td>GY</td>
      <td>1512352800</td>
      <td>88</td>
      <td>6.80</td>
      <td>-58.16</td>
      <td>78.80</td>
      <td>6.93</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Esperance</td>
      <td>44</td>
      <td>AU</td>
      <td>1512354820</td>
      <td>38</td>
      <td>-33.87</td>
      <td>121.90</td>
      <td>82.16</td>
      <td>14.12</td>
    </tr>
  </tbody>
</table>
</div>




```python
import seaborn as sns
final_weather_df.plot(kind="scatter", x="Lat", y="Max Temp", title="City Latitude vs. Max Temperature (12/3/17)")
plt.xlabel("Latitude")
plt.ylabel("Max Temperature (F)")
plt.xlim([-80,100])
plt.ylim([-100,150])
sns.set_style("whitegrid")
```


```python
plt.savefig('Latitude_vs_MaxTemp.png')
plt.show()
```


![png](output_9_0.png)



```python
final_weather_df.plot(kind="scatter", x="Lat", y="Humidity", title="City Latitude vs. Humidity (12/3/17)")
plt.xlabel("Latitude")
plt.ylabel("Humidity (%)")
plt.xlim([-80,100])
plt.ylim([-20,120])
sns.set_style("whitegrid")
plt.savefig('Latitude_vs_Humidity.png')
plt.show()
```


![png](output_10_0.png)



```python
final_weather_df.plot(kind="scatter", x="Lat", y="Cloudiness", title="City Latitude vs. Cloudiness (12/3/17)")
plt.xlabel("Latitude")
plt.ylabel("Cloudiness (%)")
plt.xlim([-80,100])
plt.ylim([-20,120])
sns.set_style("whitegrid")
plt.savefig('Latitude_vs_Cloudiness.png')
plt.show()
```


![png](output_11_0.png)



```python
final_weather_df.plot(kind="scatter", x="Lat", y="Wind Speed", title="City Latitude vs. Wind Speed (12/3/17)")
plt.xlabel("Latitude")
plt.ylabel("Wind Speed (mph)")
plt.xlim([-80,100])
plt.ylim([-5,40])
sns.set_style("whitegrid")
plt.savefig('Latitude_vs_WindSpeed.png')
plt.show()
```


![png](output_12_0.png)



```python
weather_data_df.to_csv('Initial_Retrieved_Data.csv', encoding='utf-8')
```


```python
final_weather_df.to_csv('Final_Retrieved_Data.csv', encoding='utf-8')
```
