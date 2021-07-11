# trueyogicasestudy

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
