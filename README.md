# 📚 Kütüphane Masa Takip Sistemi

## Proje Hakkında

Kütüphane Masa Takip Sistemi, kütüphane ve okuma salonlarında çalışma masalarının kullanım durumunu dijital olarak takip etmek amacıyla geliştirilmiş bir yazılım projesidir.

Sistem sayesinde öğrenciler:

* QR kod ile masa rezervasyonu oluşturabilir,
* Aktif rezervasyonlarını görüntüleyebilir,
* Rezervasyon sürelerini yenileyebilir,
* Dolu masalar için sıraya girebilir,
* Masa ile ilgili sorun bildiriminde bulunabilir.

Proje; backend tarafında **ASP.NET Core Web API**, frontend tarafında ise **Flutter** kullanılarak geliştirilmiştir.

---

# 👥 Proje Ekibi

* Ertuğrul EVLİYAOĞLU
* Mehmet CANSEVER
* Semanur YILDIRIM
* İlayda ÖZTÜRK

---

# 🎯 Projenin Amacı

Bu projenin temel amacı, kütüphane çalışma alanlarında yaşanan masa kullanım problemlerini azaltmak ve masa yönetimini daha düzenli hale getirmektir.

Geleneksel kullanımda öğrenciler kişisel eşyalarını bırakarak uzun süre masa işgal edebilmektedir. Bu durum diğer öğrencilerin uygun çalışma alanı bulmasını zorlaştırmaktadır.

Geliştirilen sistem ile:

* Masaların anlık durumları takip edilir,
* QR kod destekli kontrollü rezervasyon sağlanır,
* Rezervasyon süreleri yönetilir,
* Sıra sistemi oluşturulur,
* Sorun bildirimleri dijital ortamda yönetilir,
* Admin ve staff kullanıcıları için yönetim desteği sunulur.

---

# 🛠 Kullanılan Teknolojiler

## Backend

* ASP.NET Core Web API
* .NET 9
* Entity Framework Core
* SQL Server
* JWT Authentication
* Role-Based Authorization
* FluentValidation
* Swagger / OpenAPI
* Firebase Admin SDK
* QRCoder
* Background Service

## Frontend

* Flutter
* Dart
* REST API Integration
* Firebase Cloud Messaging (FCM)
* SharedPreferences
* Geolocator
* Mobile Scanner
* HTTP Package

---

# 🏗 Sistem Mimarisi

```text
Kutuphane-Masa-Takip-Sistemi/
│
├── LibrarySeatTrackingAPI_Backend/
│   └── ASP.NET Core Web API backend projesi
│
├── library_seat_tracking_app_Frontend(Flutter)/
│   └── Flutter mobil uygulama projesi
│
├── Grup1_Rapor_Guncel.pdf
├── Grup1_Sunum_Guncel.pptx
├── Grup1_Poster1.pdf
└── Grup1_Poster2.pdf
```

* **Backend** tarafı iş kurallarını, veritabanı işlemlerini ve API servislerini yönetir.
* **Frontend** tarafı kullanıcıların mobil arayüz üzerinden sisteme erişmesini sağlar.

---

# ⚙ Backend Özellikleri

* JWT tabanlı kullanıcı doğrulama
* Refresh token desteği
* Logout işlemleri
* Rol bazlı yetkilendirme
* Admin / Staff / Student kullanıcı rolleri
* Lokasyon alanı yönetimi
* Çalışma masası yönetimi
* QR kod kayıt yönetimi
* QR kod oluşturma, indirme ve yazdırma
* Rezervasyon oluşturma ve yönetme
* Rezervasyon yenileme
* Rezervasyon sonlandırma
* Sıra sistemi
* Sorun bildirme sistemi
* Bildirim altyapısı
* Firebase entegrasyonu
* Süresi dolan rezervasyonları kontrol eden background service
* Global exception middleware
* FluentValidation ile DTO doğrulama

---

# 📱 Frontend Özellikleri

* Kullanıcı giriş sistemi
* Rol bazlı ekran yönlendirme
* Öğrenci paneli
* Admin paneli
* Staff ekranları
* QR kod okutma
* Masa durumlarını görüntüleme
* Rezervasyon oluşturma
* Rezervasyon yenileme
* Rezervasyon sonlandırma
* Sıraya girme sistemi
* Sorun bildirimi oluşturma
* Bildirim paneli
* Okunmamış bildirim sayısı gösterimi
* Firebase bildirim desteği
* SharedPreferences ile oturum yönetimi

---

# 👤 Kullanıcı Rolleri

## Student

Öğrenciler:

* QR kod ile rezervasyon oluşturabilir,
* Aktif rezervasyonlarını görüntüleyebilir,
* Rezervasyon sürelerini yenileyebilir,
* Dolu masalar için sıraya girebilir,
* Sorun bildirimi oluşturabilir.

## Staff

Staff kullanıcıları:

* Sorun bildirimlerini yönetebilir,
* QR kod kayıtlarını görüntüleyebilir,
* Bazı rezervasyon işlemlerini kontrol edebilir.

## Admin

Admin kullanıcıları:

* Masa yönetimi,
* Lokasyon yönetimi,
* QR kod işlemleri,
* Sorun bildirimleri,
* Sıra kayıtları,
* Yönetimsel işlemler

gibi tüm sistem süreçlerini kontrol edebilir.

---

# 🔗 API Endpointleri

## Authentication

```http
POST /api/auth/login
POST /api/auth/refresh-token
POST /api/auth/logout
```

## Reservations

```http
POST /api/reservations
GET  /api/reservations/my
PUT  /api/reservations/{reservationId}/complete
PUT  /api/reservations/{reservationId}/force-complete
POST /api/reservations/renew
```

## Queue Entries

```http
POST /api/queue-entries
GET  /api/queue-entries/my
```

## Issue Reports

```http
POST /api/issue-reports
GET  /api/issue-reports/my
```

## Notifications

```http
GET  /api/notifications/my
PUT  /api/notifications/{notificationId}/read
```

## Device Tokens

```http
POST /api/device-tokens/register
```

---

# 🚀 Kurulum

## Backend Kurulumu

```bash
cd LibrarySeatTrackingAPI_Backend/LibrarySeatTrackingAPI
dotnet restore
dotnet run
```

Swagger arayüzü:

```text
http://localhost:5024
```

> Not: Port numarası local ayarlara göre değişebilir.

---

# 🗄 Veritabanı Yapılandırması

`appsettings.json` içerisinde bulunan bağlantı ayarını düzenleyin:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=(localdb)\\MSSQLLocalDB;Database=LibrarySeatTrackingDb;Trusted_Connection=True;TrustServerCertificate=True;"
}
```

Uygulama başlatıldığında migration işlemleri ve seed data otomatik olarak çalıştırılır.

---

# 📲 Flutter Uygulamasını Çalıştırma

```bash
cd library_seat_tracking_app_Frontend(Flutter)/library_seat_tracking_app
flutter pub get
flutter run
```

Android emulator için API adresi:

```text
http://10.0.2.2:5024/api
```

Web veya masaüstü kullanımında:

```text
http://localhost:5024/api
```

---

# 🔔 Firebase Bildirim Sistemi

Projede Firebase Cloud Messaging (FCM) altyapısı kullanılmaktadır.

Sistem:

1. Kullanıcıdan bildirim izni alır,
2. Device token üretir,
3. Token bilgisini backend tarafına gönderir,
4. Firebase Admin SDK ile bildirim gönderimini sağlar.

Örnek endpoint:

```http
POST /api/device-tokens/register
```

> Güvenlik nedeniyle Firebase servis anahtarları `.gitignore` ile korunmalı veya environment variables üzerinden yönetilmelidir.

---

# 🪑 Masa Durumları

| Durum   | Açıklama                                  |
| ------- | ----------------------------------------- |
| Boş     | Masa kullanıma uygundur                   |
| Dolu    | Masa aktif olarak kullanılmaktadır        |
| Rezerve | Masa için aktif rezervasyon bulunmaktadır |
| Bakımda | Masa geçici olarak kullanıma kapalıdır    |

---

# 🔄 Rezervasyon Akışı

1. Öğrenci sisteme giriş yapar.
2. QR kod okutma ekranını açar.
3. Masaya ait QR kodu okutur.
4. Uygulama QR kod ve konum bilgisini backend’e gönderir.
5. Backend gerekli kontrolleri gerçekleştirir.
6. Rezervasyon oluşturulur.
7. Masa durumu güncellenir.
8. Öğrenci aktif rezervasyonunu görüntüler.

---

# 🧪 Test Edilen Başlıca Akışlar

* Backend çalıştırma
* Swagger erişimi
* JWT doğrulama
* Rol bazlı yetkilendirme
* Login / Logout işlemleri
* Refresh token işlemleri
* Masa yönetimi
* QR kod işlemleri
* Rezervasyon işlemleri
* Queue sistemi
* Sorun bildirimi sistemi
* Bildirim sistemi
* Flutter login ekranı
* QR kod ile rezervasyon oluşturma
* Masa durumlarının listelenmesi

---

# 🔐 Güvenlik

Sistemde JWT tabanlı kimlik doğrulama kullanılmaktadır.

API isteklerinde access token aşağıdaki formatta gönderilir:

```http
Authorization: Bearer <accessToken>
```

Endpointler rol bazlı yetkilendirme ile korunmaktadır.

---

# 📂 Proje İçeriği

Arşiv içerisinde:

* Backend kaynak kodları
* Flutter frontend kaynak kodları
* Proje raporu
* Proje sunumu
* Poster dosyaları

bulunmaktadır.

---

# 📄 Lisans

Bu proje eğitim ve dönem sonu uygulaması kapsamında geliştirilmiştir.

Kullanım ve paylaşım süreçlerinde proje ekibine atıf yapılması önerilir.
