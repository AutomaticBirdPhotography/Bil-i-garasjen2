# Bil-i-garasjen2
git clone https://github.com/ultralytics/yolov5  
cd yolov5  
pip install -r requirements.txt  

NB! på rpi (des. 2021):
pip install torch==1.8.1  
pip install torchvision==0.9.1  
pip install numpy --upgrade  
datasets.py (i /yolov5/utils) byttes ut med datasets.py herfra (enkelte endringer for å forbedre performance bla. crop for hvor emblemet hvil være)

Kommandoen for å kjøre ligger i detect_car_info.py  
(emblem5.pt er optimalisert for --imgs 256, dette er med på å booste performance)


Oppsettet:  
- Wemos D1 mini kjører kode med Blynk. Denne gir ut et signal når garasjeporten åpnes via appen, og slutter å gi ut signalet når porten lukkes.

- Rpi får signalet å begynner å søke etter emblemet når porten da åpnes.

- IP camera er montert slik at dette ser hele området bilen kommer inn på.

- Kjørefeltsignal er koblet til rpi og lyser retning, ettersom hvor emblemet sees.

- Etter at bilen er inne i garasjen går det 30 sekunder, og lyset skrus av. Eller det skrus av når garasjeporten lukkes igjen (den trenger ikke å lukkes via appen). (Åpnes garasjen igjen manuellt, dvs. ikke via appen starter den ikke å søke etter emblemet). Åpnes garasjeporten via appen søker den etter emblemet. Om emblemet sees å være helt inne i garasjen i over 4 min skrus søkingen og lyset av igjen.

Ulemper:  
- Kjører man ut av garasjen uten å lukke porten vil den stå å søke evig etter dette (dvs. enten til garasjen lukkes igjen eller bilen kjøres tilbake inn). -Det jobbes med å få porten til å lukkes når bilen kjøres ut av garasjen (dvs. mangler bare en 10m ledning).
