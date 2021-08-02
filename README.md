# Study Case
 ![image](https://user-images.githubusercontent.com/10465339/125210060-e7b7dd80-e2a5-11eb-867d-dda9d26d8c71.png)

## Moment
**Moment** kullanıcının anlık durumuna göre ona sunacağımız hizmeti söyler. 
Kullanıcı Relax,Energy,Sleep,Focus seçimlerinden birini seçtiğinde, call edeceği servis ile birlikte yine ikinci bir seçim Music,Yoga,Meditation,Breath içerisinden seçim yapmalı. Bu seçim sonrası return olarak kullanıcıya anlık durumuna göre dönüş yapılmalı.
Sleep -> Music -> return Sleep_Music01 
Focus -> Breath -> return Focus_Breath05


## Mantra
**Mantra** call edildiğinde random olarak Mantra yazılıar dönecek. Mantra yazıları random olarak seçilecek fakat; örneğin toplam 10 mantra yazısı var ise, önceki günlerde dönen Mantra yazıları bu random listesinde olmayacak.  
**Örneğin;**  
1.gün : Mantra09 seçildi  
2.gün Mantra09 olmayan random bir mantra = Mantra07 seçildi  
3.gün Mantra09 ve Mantra07 olmayan random bir mantra = Mantra03 seçildi  
4.gün Mantra09 ve Mantra07 ve Mantra03 olmayan random bir mantra = Mantra04 seçildi  
..  
..  
11.gün full liste içinden (1. adıma dönüyoruz gibi düşünün) RANDOM bir mantra; örneğin Mantra09  
Şeklinde return gelmeli.  


## Mood Tracking
**Mood Tracking** kullanıcının günlük duygu durumuna göre return edeceğimiz bi
  
  ![image](https://user-images.githubusercontent.com/10465339/125210122-6876d980-e2a6-11eb-9273-a0af7047b224.png)
  
Yukarıdaki örnekteki gibi 5 farklı mood call edildiğinde, bu moodlara özel bir yazı anlık olarak return edilmeli.  
Örneğin;
1.rad seçilldiğinde; “süper, sırrını insanlarla paylaş”  
2.good seçildiğinde; “mutluluk seni güzel gösteriyor!”  
3.meh seçildiğinde; “daha iyi hissedebilirsin, günün hala bitmedi!”  
4.bad seçildiğinde; “hissetmeye başla, bugün güzel bir gün!”  
5.awful seçildiğinde; “her ne yaşıyorsan senin için burada olduğumuzu bil!”  

Mood Tracking’de seçilen modun 3 saat sonrasında (yani yukarıdaki gibi ilk return yapıldıktan sonra) kullanıcıya yeni bir notification atılması planlanacak. 
**Örneğin**;  
“good” seçen kullanıcıya 3 saat sonra “umarım günün harika bir şekilde devam ediyordur.”  
“bad” seçen kullanıcıya 3 saat sonra “dediğim gibi güzel zaman güzelliklerle dolu, keyifini sür.”  

## Weather ve Moon Cycle
**Weather ve Moon Cycle** call edildiğinde, bilgileri internet üzerinden çekilip kullanıcıya gösterilmeli. Günlük hava durumu ve yarınki tahmini hava durumu bilgileri;  
![image](https://user-images.githubusercontent.com/10465339/125210146-82b0b780-e2a6-11eb-8edf-fdf038744412.png)
  
  bunun yanında ayın evreleri aşağıdaki şekilde, Londra şehri için, ay içerisinde hangi evrelerde olacağı return edilmeli.
 ![image](https://user-images.githubusercontent.com/10465339/125210149-893f2f00-e2a6-11eb-94b2-3164de5f94a4.png)

## Sun Position
**Sun position** bilgileri, Londra şehrine sabit olacak şekilde, güneşin konumuna göre günlük olarak aşağıdaki bilgiler dönmeli;    
Şafak Saati: ??  
Güneşin Doğuş saati: ??  
Güneş hangi saatte en tepede: ??  
Güneşin Batış Saati: ??  
Alacakaranlık Saati: ??  





# Teknik Detaylar
getMenu();  
getSubMenu(code);  
getContent(list_of_selected_codes);  
getMoods();  
getMoodContent(code);  
getSelectedMoodByUser(userId);  
sendNotification(userId, content);  
getWeatherInfo(user.City);  
  
https://collectapi.com/tr/api/weather/hava-durumu-api haftalık hava durumu tüm iller için 1 kere çekilip database e kaydedilecek. Sonraki requestlerde dbden okunacak. Bunun için haftada bir çalışan bir job yapılabilir.  Weather collection'ını besler.  
  
Menu Collection: menu.json  
Content Collection : contents.json  
User Mantra History Collection : user_mantra_history.json  
Mood Tracking Collection : mood_tracking.json  
User Mood History Collection :  user_mood_history.json  
Weather collection : weather.json  

## Yardımcı Linkler  
https://www.udemy.com/course/api-and-web-service-introduction/  
https://apiary.io/how-to-build-api  
https://apereo.github.io/cas/6.1.x/services/Service-Management.html  
http://apostylee.com/web-servis-yazmak-ve-kullanmak/  
https://rapidapi.com/blog/20-tutorials-on-how-to-create-your-own-api-sorted-by-programming-language/  

# Extralar
1) Mood Tracking için database'den çekilen bilgilere her biri için ekstra 2 tane daha text eklenecek ve random seçilecek.
1.rad seçilldiğinde;  
-“süper, sırrını insanlarla paylaş”  
-“böyle hissetmeye devam et”  
-“güzel bir gün seni bekliyor”  
2.good seçildiğinde;  
-“mutluluk seni güzel gösteriyor!”  
-“mutluluk bugün komşun ve sana çok yakın”  
-“hayalini kurduğun mutluluk bugün seninle”  
3.meh seçildiğinde;  
-“daha iyi hissedebilirsin, günün hala bitmedi!”  
-“her şey harika, yeter ki farkına var”  
-“günün en güzel saatleri henüz yeni başlıyor”  
4.bad seçildiğinde;  
-“hissetmeye başla, bugün güzel bir gün!”  
-“sorun yok, her şey yolunda”  
-“kafanı rahatlat ve hissetmeye devam et”  
5.awful seçildiğinde;  
-“her ne yaşıyorsan senin için burada olduğumuzu bil!”  
-“bugünü daha iyi yapmak için biraz meditasyona ne dersin?”  
-“unutma, harika hissetmek senin elinde”  

Yukarıda bahsettiğimiz 3 saat sonra gönderilecek Notification 5 dakika sonrasına ayarlansın. Return ediyor mu görelim.

2)Mantra'lar database'e eklenecek.

3)Moon Cycle için API varsa entegre edilecek (inceleniyor) yoksa nasıl ilerleyebiliriz?

4)Moment için seçilen kategorilere göre youtube linki veya direkt olarak video açılacak. (Videoları Buraya ekleyeceğim)
