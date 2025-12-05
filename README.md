# Intip App

Aplikasi mobile berbasis Flutter dengan integrasi Firebase Authentication dan Supabase untuk backend services.

## 📋 Deskripsi

Intip adalah aplikasi mobile yang dibangun menggunakan Flutter dengan fitur-fitur berikut:
- Autentikasi pengguna menggunakan Firebase Authentication
- Backend services menggunakan Supabase
- Upload dan manajemen gambar menggunakan Image Picker
- Penyimpanan data lokal menggunakan Shared Preferences
- Multi-platform support (Android, iOS, Web, Windows, macOS, Linux)

## 🚀 Teknologi yang Digunakan

- **Flutter** - Framework cross-platform untuk pengembangan aplikasi mobile
- **Dart** - Bahasa pemrograman untuk Flutter (SDK ^3.10.0)
- **Firebase** - Backend service untuk autentikasi
  - Firebase Core
  - Firebase Authentication
- **Supabase** - Backend as a Service untuk database dan API
- **Image Picker** - Library untuk memilih dan mengambil gambar dari perangkat
- **Shared Preferences** - Penyimpanan data lokal key-value

## 📦 Prasyarat

Sebelum memulai, pastikan Anda telah menginstall:

- [Flutter SDK](https://flutter.dev/docs/get-started/install) (versi terbaru)
- [Dart SDK](https://dart.dev/get-dart) (terintegrasi dengan Flutter)
- [Git](https://git-scm.com/)
- Editor/IDE:
  - [Android Studio](https://developer.android.com/studio) (dengan Flutter plugin)
  - [VS Code](https://code.visualstudio.com/) (dengan Flutter extension)
  - [IntelliJ IDEA](https://www.jetbrains.com/idea/)

Untuk pengembangan platform spesifik:
- **Android**: Android Studio dengan Android SDK
- **iOS**: Xcode (hanya untuk macOS)
- **Web**: Chrome browser
- **Windows/macOS/Linux**: Flutter desktop support

## 🔧 Instalasi

1. Clone repository atau download project

2. Install dependencies:
```bash
flutter pub get
```

3. Konfigurasi Firebase:
   - Buat project Firebase baru di [Firebase Console](https://console.firebase.google.com/)
   - Download file konfigurasi:
     - Android: `google-services.json` → letakkan di `android/app/`
     - iOS: `GoogleService-Info.plist` → letakkan di `ios/Runner/`
   - Generate `firebase_options.dart` dengan menjalankan:
   ```bash
   flutterfire configure
   ```

4. Konfigurasi Supabase:
   - Buat project Supabase baru di [Supabase](https://supabase.com/)
   - Salin URL dan anon key dari project settings
   - Update file `lib/supabase_config.dart` dengan kredensial Anda:
   ```dart
   const String supabaseUrl = 'YOUR_SUPABASE_URL';
   const String supabaseAnonKey = 'YOUR_SUPABASE_ANON_KEY';
   ```

## 🏃 Menjalankan Aplikasi

### Development Mode

Jalankan aplikasi di development mode:

```bash
flutter run
```

Untuk menjalankan di platform spesifik:

```bash
# Android
flutter run -d android

# iOS
flutter run -d ios

# Web
flutter run -d chrome

# Windows
flutter run -d windows

# macOS
flutter run -d macos

# Linux
flutter run -d linux
```

### Build untuk Production

Build aplikasi untuk production:

```bash
# Android APK
flutter build apk

# Android App Bundle (untuk Play Store)
flutter build appbundle

# iOS
flutter build ios

# Web
flutter build web

# Windows
flutter build windows

# macOS
flutter build macos

# Linux
flutter build linux
```

## 📱 Struktur Project

```
intip/
├── lib/
│   ├── main.dart                 # Entry point aplikasi
│   ├── firebase_options.dart     # Konfigurasi Firebase
│   ├── supabase_config.dart      # Konfigurasi Supabase
│   ├── screens/                  # Screen/screen aplikasi
│   │   ├── login_screen.dart     # Halaman login
│   │   ├── register_screen.dart   # Halaman registrasi
│   │   ├── home_screen.dart      # Halaman utama
│   │   ├── profile_screen.dart   # Halaman profil
│   │   └── upload_screen.dart   # Halaman upload
│   └── services/                 # Service layer
│       └── auth_service.dart     # Service untuk autentikasi
├── android/                      # Konfigurasi Android
├── ios/                          # Konfigurasi iOS
├── web/                          # Konfigurasi Web
├── windows/                      # Konfigurasi Windows
├── macos/                        # Konfigurasi macOS
├── linux/                        # Konfigurasi Linux
├── test/                         # Unit tests
├── pubspec.yaml                  # Dependencies dan konfigurasi
└── firebase.json                 # Konfigurasi Firebase
```

## 🔐 Autentikasi

Aplikasi menggunakan Firebase Authentication untuk autentikasi pengguna. Fitur yang tersedia:

- **Login** dengan email dan password
- **Registrasi** akun baru
- **Logout** dari aplikasi
- **Auth State Management** - Otomatis redirect berdasarkan status login
- **Error Handling** - Penanganan error yang user-friendly

### Menggunakan Auth Service

```dart
import 'package:intip/services/auth_service.dart';

// Login
await AuthService.loginWithEmail(
  email: 'user@example.com',
  password: 'password123',
);

// Register
await AuthService.registerWithEmail(
  email: 'user@example.com',
  password: 'password123',
);

// Logout
await AuthService.signOut();
```

## 🗄️ Supabase Integration

Aplikasi menggunakan Supabase untuk backend services. Pastikan untuk:

1. Membuat project di [Supabase Dashboard](https://app.supabase.com/)
2. Mengkonfigurasi database tables sesuai kebutuhan
3. Mengupdate `supabase_config.dart` dengan kredensial project Anda

## 📸 Image Picker

Aplikasi menggunakan Image Picker untuk mengambil gambar dari:
- Gallery/Photo Library
- Camera

Pastikan untuk menambahkan permission yang diperlukan di:
- **Android**: `android/app/src/main/AndroidManifest.xml`
- **iOS**: `ios/Runner/Info.plist`

## 🛠️ Development

### Menambahkan Dependencies Baru

Tambahkan dependency di `pubspec.yaml`, lalu jalankan:

```bash
flutter pub get
```

### Menjalankan Tests

```bash
flutter test
```

### Code Analysis

```bash
flutter analyze
```

### Format Code

```bash
flutter format .
```

## 📚 Dokumentasi

- [Flutter Documentation](https://flutter.dev/docs)
- [Dart Documentation](https://dart.dev/guides)
- [Firebase Flutter Documentation](https://firebase.flutter.dev/)
- [Supabase Flutter Documentation](https://supabase.com/docs/reference/dart/introduction)
- [Image Picker Package](https://pub.dev/packages/image_picker)

## 🔒 Security Notes

⚠️ **PENTING**: Jangan commit file-file berikut ke repository publik:
- `firebase_options.dart` (jika berisi sensitive data)
- `supabase_config.dart` (berisi API keys)
- `google-services.json`
- `GoogleService-Info.plist`

Gunakan environment variables atau file konfigurasi yang di-ignore oleh Git.

## 🤝 Kontribusi

1. Fork repository
2. Buat feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit perubahan (`git commit -m 'Add some AmazingFeature'`)
4. Push ke branch (`git push origin feature/AmazingFeature`)
5. Buat Pull Request

## 📄 Lisensi

Project ini untuk keperluan tugas mata kuliah Mobile Programming.

## 👤 Author

Dibuat untuk tugas Mobile Programming.

## 🐛 Troubleshooting

### Error: Firebase not initialized
- Pastikan `firebase_options.dart` sudah di-generate dengan benar
- Pastikan file `google-services.json` (Android) atau `GoogleService-Info.plist` (iOS) sudah ada

### Error: Supabase connection failed
- Periksa URL dan anon key di `supabase_config.dart`
- Pastikan project Supabase masih aktif

### Build error di Android/iOS
- Jalankan `flutter clean`
- Hapus folder `build/`
- Jalankan `flutter pub get`
- Coba build lagi

---

**Note**: Pastikan untuk mengkonfigurasi Firebase dan Supabase dengan benar sebelum menjalankan aplikasi. File konfigurasi perlu disesuaikan dengan project Anda masing-masing.
