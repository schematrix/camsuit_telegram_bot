# ESP32-CAM Telegram Photo Bot

Bu proje, ESP32-CAM kullanarak Telegram üzerinden `/photo` komutu gönderildiğinde uzaktan fotoğraf çekmeyi sağlar.

Aşağıdaki adımlar, **hiç bilmeyen** bir kullanıcının sıfırdan projeyi çalıştırabilmesi için hazırlanmıştır.

---

## Arduino IDE ve ESP32 Kart Kurulumu

1. Bilgisayara **Arduino IDE** indirilir ve kurulur.  
2. Arduino IDE açılır.  
3. **File → Preferences** menüsüne girilir.  
4. **Additional Boards Manager URLs** alanı bulunur.  
5. Aşağıdaki adres eklenir:
  https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
6. **OK** tuşuna basılır.  
7. **Tools → Board → Boards Manager** açılır.  
8. Arama kısmına **ESP32** yazılır.  
9. **Espressif Systems – ESP32** paketi yüklenir.  
10. Yükleme tamamlanınca Boards Manager kapatılır.  

---

## ESP32-CAM Kart Ayarları

11. **Tools → Board** menüsünden **AI Thinker ESP32-CAM** seçilir.  
12. **Tools → Port** kısmı, kart bağlandıktan sonra doğru port olacak şekilde ayarlanır.  
13. **Tools → Upload Speed** değeri **115200** seçilir.  

---

## Gerekli Kütüphaneler

14. **Tools → Manage Libraries** açılır.  
15. **ArduinoJson** kütüphanesi aranır.  
16. **ArduinoJson** yüklenir.  
17. **WiFi** ve **WiFiClientSecure** kütüphaneleri ESP32 ile birlikte gelir.  
18. **esp_camera** kütüphanesi ESP32 paketinin içindedir, ayrıca yüklenmez.  

---

## Donanım Bağlantısı

19. ESP32-CAM, bir **USB–TTL dönüştürücü** ile bilgisayara bağlanır.  
20. Bağlantılar şu şekilde yapılır:  
- 5V → 5V  
- GND → GND  
- U0R → TX  
- U0T → RX  
21. Program yükleme moduna almak için **GPIO0 → GND** yapılır.  
22. Kart resetlenir.  

---

## Kod Yükleme

23. Arduino IDE’de proje kodu açılır.  
24. Wi-Fi adı ve şifresi koda yazılır.  
25. Telegram **Bot Token** koda eklenir.  
26. Gerekirse **Chat ID** tanımlanır.  
27. **Upload** butonuna basılır.  
28. Yükleme bitince **GPIO0 – GND** bağlantısı kaldırılır.  
29. ESP32 tekrar resetlenir.  

---

## Çalışma Mantığı

30. ESP32 Wi-Fi ağına bağlanır.  
31. Telegram’dan gelen mesajlar düzenli olarak kontrol edilir.  
32. `/photo` komutu geldiğinde kamera fotoğraf çeker.  
33. Çekilen fotoğraf Telegram üzerinden kullanıcıya gönderilir.  
34. ESP32 tekrar yeni komut beklemeye başlar.  

---

## Notlar

- Bu proje **HTTPS** üzerinden çalışır.  
- Port yönlendirme veya sabit IP gerekmez.  
- Telegram bot token bilgisi gizli tutulmalıdır.  
- Proje eğitim ve kişisel kullanım amaçlıdır.

---

## Lisans

Bu proje MIT Lisansı ile paylaşılmıştır.
