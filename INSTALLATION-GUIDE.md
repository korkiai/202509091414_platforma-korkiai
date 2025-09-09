# Przewodnik Instalacji Platformy KorkiAI

## Wymagania Systemowe

### Serwer
- **PHP**: 8.0+ (zalecane 8.1+)
- **MySQL**: 8.0+ (zalecane 8.0+)
- **Apache/Nginx**: Najnowsza wersja
- **SSL**: Wymagany (Let's Encrypt)
- **Pamięć RAM**: 2GB+ (zalecane 4GB+)
- **Dysk**: 10GB+ wolnego miejsca

### Rozszerzenia PHP
- `mysqli`
- `curl`
- `gd`
- `mbstring`
- `xml`
- `zip`
- `openssl`

## Krok 1: Przygotowanie Serwera

### 1.1 Utworzenie Bazy Danych
```sql
-- Zaloguj się do MySQL
mysql -u root -p

-- Utwórz bazę danych
CREATE DATABASE netflyapp_platforma_korkiai CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Utwórz użytkownika
CREATE USER 'netflyapp_platforma_korkiai'@'localhost' IDENTIFIED BY 'Brzeszcz13!@Brzeszcz13!@';

-- Nadaj uprawnienia
GRANT ALL PRIVILEGES ON netflyapp_platforma_korkiai.* TO 'netflyapp_platforma_korkiai'@'localhost';
FLUSH PRIVILEGES;
```

### 1.2 Przywrócenie Backup Bazy Danych
```bash
# Przywróć backup
mysql -u netflyapp_platforma_korkiai -p netflyapp_platforma_korkiai < kopia\ bazy\ danych/netflyapp_platforma_korkiai_backup_20250909_145112.sql
```

## Krok 2: Wgranie Plików

### 2.1 Upload na Serwer
```bash
# Wgraj wszystkie pliki do katalogu głównego domeny
# np. /home/netflyapp/public_html/platforma.korkiai.pl/
```

### 2.2 Ustawienie Uprawnień
```bash
# Ustaw uprawnienia dla plików
find /path/to/platforma -type f -exec chmod 644 {} \;

# Ustaw uprawnienia dla katalogów
find /path/to/platforma -type d -exec chmod 755 {} \;

# Ustaw uprawnienia dla wp-content
chmod -R 755 wp-content/
chmod -R 777 wp-content/uploads/
```

## Krok 3: Konfiguracja WordPress

### 3.1 Aktualizacja wp-config.php
```php
<?php
// Zaktualizuj dane bazy danych
define( 'DB_NAME', 'netflyapp_platforma_korkiai' );
define( 'DB_USER', 'netflyapp_platforma_korkiai' );
define( 'DB_PASSWORD', 'NOWE_HASŁO' );
define( 'DB_HOST', 'localhost' );

// Zaktualizuj URL strony
define( 'WP_HOME', 'https://platforma.korkiai.pl' );
define( 'WP_SITEURL', 'https://platforma.korkiai.pl' );

// Wygeneruj nowe klucze bezpieczeństwa
// https://api.wordpress.org/secret-key/1.1/salt/
define( 'AUTH_KEY', 'nowy-unikalny-klucz' );
define( 'SECURE_AUTH_KEY', 'nowy-unikalny-klucz' );
// ... pozostałe klucze
```

### 3.2 Aktualizacja URL w Bazie Danych
```sql
-- Zaktualizuj URL w opcjach
UPDATE wp_options SET option_value = 'https://platforma.korkiai.pl' WHERE option_name = 'home';
UPDATE wp_options SET option_value = 'https://platforma.korkiai.pl' WHERE option_name = 'siteurl';

-- Zaktualizuj URL w postach
UPDATE wp_posts SET post_content = REPLACE(post_content, 'https://stara-domena.pl', 'https://platforma.korkiai.pl');

-- Zaktualizuj URL w meta danych
UPDATE wp_postmeta SET meta_value = REPLACE(meta_value, 'https://stara-domena.pl', 'https://platforma.korkiai.pl');
```

## Krok 4: Konfiguracja Pluginów

### 4.1 Aktywacja Pluginów
1. Zaloguj się do panelu administracyjnego
2. Przejdź do **Plugins** → **Installed Plugins**
3. Aktywuj wszystkie pluginy Fluent
4. Sprawdź licencje w ustawieniach każdego pluginu

### 4.2 Konfiguracja Fluent Community
1. **Community** → **Settings**
2. Ustaw **Community URL**
3. Skonfiguruj **Email Settings**
4. Ustaw **Moderation Rules**

### 4.3 Konfiguracja Fluent CRM
1. **Fluent CRM** → **Settings**
2. Skonfiguruj **Email Settings**
3. Ustaw **Double Opt-in**
4. Skonfiguruj **Automation Rules**

### 4.4 Konfiguracja Fluent Affiliate
1. **Fluent Affiliate** → **Settings**
2. Ustaw **Commission Rates**
3. Skonfiguruj **Payment Methods**
4. Ustaw **Email Notifications**

## Krok 5: Konfiguracja Email

### 5.1 Fluent SMTP
1. **Fluent SMTP** → **Settings**
2. Skonfiguruj dostawcę SMTP:
   - **Gmail**: smtp.gmail.com:587
   - **SendGrid**: smtp.sendgrid.net:587
   - **Mailgun**: smtp.mailgun.org:587
3. Przetestuj wysyłanie emaili

## Krok 6: Testowanie

### 6.1 Testy Funkcjonalne
- [ ] Logowanie administratora
- [ ] Rejestracja nowego użytkownika
- [ ] Tworzenie postów w społeczności
- [ ] Wysyłanie emaili
- [ ] Program partnerski
- [ ] System wsparcia

### 6.2 Testy Wydajności
- [ ] Czas ładowania strony
- [ ] Optymalizacja obrazów
- [ ] Cache (opcjonalnie)
- [ ] CDN (opcjonalnie)

## Krok 7: Bezpieczeństwo

### 7.1 Zmiana Hasła Administratora
1. **Users** → **All Users**
2. Edytuj administratora
3. Ustaw nowe, silne hasło

### 7.2 Konfiguracja Bezpieczeństwa
1. **Fluent Security** → **Settings**
2. Włącz **Login Protection**
3. Ustaw **Rate Limiting**
4. Skonfiguruj **Firewall Rules**

### 7.3 Backup
1. **All-in-One WP Migration** → **Export**
2. Utwórz backup po instalacji
3. Skonfiguruj automatyczne backupy

## Rozwiązywanie Problemów

### Problem: Błąd 500
**Rozwiązanie**:
1. Sprawdź logi błędów
2. Zwiększ limit pamięci PHP
3. Sprawdź uprawnienia plików

### Problem: Błąd bazy danych
**Rozwiązanie**:
1. Sprawdź dane w wp-config.php
2. Sprawdź połączenie z bazą danych
3. Sprawdź uprawnienia użytkownika bazy danych

### Problem: Pluginy nie działają
**Rozwiązanie**:
1. Sprawdź licencje pluginów
2. Zaktualizuj pluginy
3. Sprawdź konflikt z innymi pluginami

---

*Przewodnik instalacji platformy społecznościowej KorkiAI*