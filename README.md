ESP32-CAM Telegram Photo Bot

This project demonstrates how to use an ESP32-CAM together with a Telegram Bot to capture and send photos remotely. By sending a simple /photo command to the Telegram bot, the ESP32-CAM takes a picture using its camera module and sends the image back to the user in real time over the internet.

The project is designed to be lightweight, practical, and easy to extend for surveillance, monitoring, or IoT camera applications.

⸻

Features
	•	📸 On-demand photo capture using ESP32-CAM
	•	🤖 Control via Telegram Bot commands
	•	🌐 Communication over Wi-Fi using HTTPS
	•	🖼 JPEG image capture and upload
	•	🔁 Simple polling-based message handling
	•	💾 Efficient memory management for stable operation

⸻

How It Works
	1.	The ESP32-CAM connects to a Wi-Fi network.
	2.	It periodically checks Telegram servers for new messages using the Bot API (getUpdates).
	3.	When the /photo command is received:
	•	The camera captures an image in JPEG format.
	•	The image is stored temporarily in memory.
	4.	The ESP32-CAM sends the photo back to the user using Telegram’s sendPhoto API via HTTPS.
	5.	After sending, the camera buffer is released to avoid memory leaks.
	6.	The device returns to listening mode and waits for the next command.

This approach allows full remote control of the camera without the need for port forwarding or a public IP address.

⸻

Hardware Requirements
	•	ESP32-CAM module (AI Thinker or compatible)
	•	USB-to-TTL programmer (FTDI, CH340, CP2102, etc.)
	•	Stable 5V power supply
	•	Jumper wires
	•	Wi-Fi network

⸻

Software Requirements
	•	Arduino IDE
	•	ESP32 board package installed
	•	Telegram Bot Token (created via BotFather)
	•	Required Arduino libraries:
	•	WiFi
	•	WiFiClientSecure
	•	ArduinoJson
	•	esp_camera

⸻

Setup Instructions
	1.	Create a Telegram Bot
	•	Open Telegram and talk to BotFather
	•	Create a new bot and copy the Bot Token
	2.	Get Your Chat ID
	•	Send any message to your bot
	•	Use a Telegram API call or bot tool to retrieve your chat_id
	3.	Configure the Code
	•	Add your Wi-Fi SSID and password
	•	Insert the Telegram Bot Token
	•	Set the allowed Chat ID (optional but recommended)
	4.	Upload the Code
	•	Select the correct ESP32-CAM board in Arduino IDE
	•	Put the ESP32-CAM into flashing mode
	•	Upload the sketch
	5.	Run
	•	Open Telegram
	•	Send /photo to your bot
	•	Receive a photo captured live by the ESP32-CAM

⸻

Security Notes
	•	Communication with Telegram uses HTTPS encryption.
	•	You should restrict the bot to a specific chat_id to prevent unauthorized access.
	•	Do not expose your bot token publicly.
	•	This project is intended for educational and personal use only.

⸻

Possible Extensions
	•	Add /flash command to enable LED flash
	•	Support video or burst photos
	•	Motion detection with automatic photo upload
	•	Store images on SD card
	•	Replace polling with webhook-based communication
	•	Integrate with home automation systems

⸻

Use Cases
	•	Remote surveillance camera
	•	IoT monitoring projects
	•	Wildlife or pet monitoring
	•	Smart door or entrance camera
	•	Learning embedded networking and IoT security

⸻

Disclaimer

This project is provided for educational purposes only. The author is not responsible for misuse or violations of privacy laws. Always ensure you have permission before recording or monitoring any area.

⸻

İNGİLİZCE BİLMİYORSANIZ VE SADECE UYGULAMAYI ALIP ÇALIŞTIRMAK İÇİN GELDİYSENİZ SADECE ALTTAKİ TÜRKÇE MADDELERİ OKUYUNUZ


1.	Bilgisayara Arduino IDE indirilir ve kurulur.
	2.	Arduino IDE açılır.
	3.	File → Preferences menüsüne girilir.
	4.	“Additional Boards Manager URLs” alanı bulunur.
	5.	Bu adres eklenir:
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
	6.	OK tuşuna basılır.
	7.	Tools → Board → Boards Manager açılır.
	8.	Arama kısmına ESP32 yazılır.
	9.	Espressif Systems – ESP32 paketi yüklenir.
	10.	Yükleme tamamlanınca Boards Manager kapatılır.

⸻

ESP32-CAM Kart Ayarları
	11.	Tools → Board menüsünden AI Thinker ESP32-CAM seçilir.
	12.	Tools → Port kısmı (bağlandıktan sonra) doğru port olacak şekilde ayarlanır.
	13.	Tools → Upload Speed 115200 seçilir.

⸻

Gerekli Kütüphaneler
	14.	Tools → Manage Libraries açılır.
	15.	ArduinoJson kütüphanesi aranır.
	16.	ArduinoJson yüklenir.
	17.	WiFi ve WiFiClientSecure kütüphaneleri zaten ESP32 ile gelir.
	18.	esp_camera kütüphanesi ESP32 paketinin içindedir.

⸻

Donanım Bağlantısı
	19.	ESP32-CAM, USB-TTL dönüştürücü ile bilgisayara bağlanır.
	20.	5V → 5V, GND → GND, U0R → TX, U0T → RX bağlanır.
	21.	Program yüklemek için GPIO0 → GND yapılır.
	22.	Kart resetlenir.

⸻

Kod Yükleme
	23.	Arduino IDE’de proje kodu açılır.
	24.	Wi-Fi adı ve şifresi koda yazılır.
	25.	Telegram Bot Token koda eklenir.
	26.	Gerekirse Chat ID tanımlanır.
	27.	Upload butonuna basılır.
	28.	Yükleme bitince GPIO0 bağlantısı kaldırılır.
	29.	ESP32 tekrar resetlenir.

⸻

Çalışma Mantığı
	30.	ESP32 Wi-Fi’ye bağlanır.
	31.	Telegram’dan gelen mesajlar kontrol edilir.
	32.	/photo komutu gelince kamera fotoğraf çeker.
	33.	Fotoğraf Telegram’a geri gönderilir.
	34.	ESP32 tekrar komut bekler.
