# Request Response Cycle

### Client-Server Mimarisi olan tüm etkileşimler Request-Response Cycle'ın bir parçasıdır

### Client-Server ne demek?
*Client* istekte bulunan yazılım
*Server* isteği yanıtlayan ve sorun olmadığı sürece istenilen kaynakları sunan yazılım

#### Örnek
##### sporkayit.com domaininde bir sitemiz var django ile htmx kullanıyoruz bu sitemizde
sporkayit.com sitesine girilmeye çalışıldığında:
GET / HTTP/1.1
Request Headers...
Şeklinde bir HTTP Request'i yollayan web browser bir *client* idir.

HTTP/1.1 200 OK
Response Headers...
Şeklinde bir HTTP Response'ı yollayan backend server'ı evet bir *server*'dır.

##### Karışıklığı Önleyelim Uzun Örnek
sporkayit.com/dashboard'a girelim
###### Dashboard = YönetimPaneli
* HTTP GET gönderildi, sunucu baktı ilişkili html css js i de attı, alındı 200 OK
* html load lanıyor üyelerin listelenmesi lazım şöyle bir kodumuz vardı:
    <div hx-trigger="load" hx-get="/views/members_table"></div>
* backend sunucumuz bu htmx in çalıştıracağı GET i url_patterns listesine göre *handle*lar:
    database'den üyeleri almak için istekte bulunur yani backend sunucumuz bu iş için *client* rolünü alır
* ###### yani bir cihaz hem sunucu hem client olabilir.

### Client Server Cycle pek çok protokolde kullanılır, bazıları:
* HTTP/HTTPS
* FTP
* SMTP
* POP3/IMAP
* LDAP

## HTTP
En yaygın olarak kullandığımız olduğu için HTTP Request Response Cycle'ı detaylandıracağız, prensiplerin çoğu hepsi için geçerli.

### Request
4 Parçadan oluşur:
* **HTTP Method**: Gerçekleşmesi istenilen method (GET, POST, vb.).
* **URI veya URL**: İstenilen kaynak veya hizmetin nereden gerçekleştirileceği.
* **Headers**: Ekstra bilgiler, örneğin cihazin mobil olduğunun bilgisi.
* **Body**: Server tarafından kullanılması istenilen veri (POST ve PUT ile kullanılır).

### Response
3 Parçadan oluşur:
- **Status Code**: İsteğin durumunu belirten kod.
- **Headers**: Verilen kaynak hakkında ekstra bilgiler.
- **Body**: İstenilen kaynak, pek çok formatta olabilir: html, xml, csv, binary, JSON.

### HTTP Methodlarından bazıları
* **GET**: Başarılı
* **POST**: Yönlendirme
* **PUT**: Client tarafında gerçekleşen hata
* **DELETE**: Server tarafında gerçekleşen hata

### HTTP Durum Kodları
* **2xx**: Success
* **3xx**: Yönlendirme
* **4xx**: Client tarafında gerçekleşen hata
* **5xx**: Server tarafında gerçekleşen hata

### HTTPS
İletişimi SSL kullanarak şifreleyen HTTP protokülüne HTTPS denir.

### Caching
Web browserlar bazı HTTP requestlerini ve yanıtlarını hafızalarında tutarlar. Böylece aynı siteye birdaha girildiğinde zaten response'un ne olacağı hafızalarında olduğundan direkt hafızalarından iletirler.

### Debug yöntemleri
* Postman
* Web browser dev tools
