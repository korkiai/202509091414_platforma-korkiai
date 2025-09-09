# Platforma Społecznościowa KorkiAI

## Opis

To jest kompletna platforma społecznościowa oparta na WordPress z Fluent Community, która służy jako centrum edukacyjne dla kursu AI dla młodzieży.

## Funkcjonalności

### 🎓 Kursy i Edukacja
- **AI dla młodzieży: Od Zera do AI Hero** - główny kurs
- **Mini kurs Canva AI** - dla uczniów i studentów
- **Praktyczne poradniki** - tutoriale krok po kroku

### 💬 Społeczność
- **Przestrzenie tematyczne** - różne sekcje dyskusji
- **Projekty uczniów** - galeria prac
- **Wyzwania i grywalizacja** - Prompt Tygodnia, Streak Challenge
- **Kawiarenka** - off-topic, memy AI, hobby

### 🛠️ Strefa Pomocy
- **Pytania do lekcji** - Q&A
- **Webinar z ekspertem** - sesje live
- **Pomysły na rozwój** - feedback

### 👨👩👧👦 Strefa Rodzica
- **Q&A dla rodziców** - wsparcie
- **Sprawdź postępy** - monitoring dziecka

### 🎓 Kariera
- **Oferty pracy** - staże w branży AI
- **Program partnerski** - zarabianie z poleceń

## Technologie

### Backend
- **WordPress** - CMS
- **Fluent Community** - platforma społecznościowa
- **Fluent CRM** - zarządzanie klientami
- **Fluent Forms** - formularze
- **Fluent Affiliate** - program partnerski

### Baza Danych
- **MySQL** - `netflyapp_platforma_korkiai`
- **Backup** - `netflyapp_platforma_korkiai_backup_20250909_145112.sql`

### Pluginy
- **Fluent Community Pro** - zaawansowane funkcje społeczności
- **Fluent CRM** - email marketing
- **Fluent Affiliate Pro** - program partnerski
- **Fluent Support** - system wsparcia
- **Fluent Boards** - zarządzanie projektami
- **WP Fusion** - integracja z zewnętrznymi narzędziami

## Struktura

```
platforma/
├── wp-content/
│   ├── themes/
│   │   ├── hello-elementor/     # Główny motyw
│   │   └── twentytwentyfive/    # Motyw zapasowy
│   ├── plugins/
│   │   ├── fluent-community/    # Platforma społecznościowa
│   │   ├── fluent-crm/          # CRM
│   │   ├── fluent-affiliate/    # Program partnerski
│   │   └── ...                  # Inne pluginy
│   └── uploads/                 # Pliki użytkowników
├── kopia bazy danych/
│   └── netflyapp_platforma_korkiai_backup_20250909_145112.sql
└── wp-config.php               # Konfiguracja
```

## Instalacja

1. **Przywróć bazę danych** z pliku backup
2. **Wgraj pliki** na serwer
3. **Skonfiguruj wp-config.php** z danymi serwera
4. **Aktywuj motyw** Hello Elementor
5. **Skonfiguruj pluginy** Fluent

## Bezpieczeństwo

⚠️ **UWAGA**: Plik `wp-config.php` zawiera dane dostępowe do bazy danych. Przed wgraniem na serwer:
1. Zmień hasła w bazie danych
2. Zaktualizuj dane w `wp-config.php`
3. Wygeneruj nowe klucze bezpieczeństwa

## Wsparcie

- **Dokumentacja Fluent**: https://wpmanageninja.com/docs/
- **WordPress Codex**: https://codex.wordpress.org/
- **Elementor**: https://elementor.com/help/

---

*Platforma społecznościowa KorkiAI - Centrum edukacyjne AI dla młodzieży*