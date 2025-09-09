# Informacje o Backupie Bazy Danych

## Plik Backup

**Nazwa**: `netflyapp_platforma_korkiai_backup_20250909_145112.sql`
**Data**: 9 września 2025, 14:51:12
**Rozmiar**: Sprawdź w folderze `kopia bazy danych/`

## Zawartość Backup

Backup zawiera kompletne dane platformy społecznościowej:

### Tabele Użytkowników
- `wp_users` - dane użytkowników
- `wp_usermeta` - metadane użytkowników
- `wp_user_roles` - role i uprawnienia

### Tabele Społeczności (Fluent Community)
- `wp_fluent_community_*` - dane społeczności
- `wp_fluent_community_posts` - posty i dyskusje
- `wp_fluent_community_comments` - komentarze
- `wp_fluent_community_likes` - polubienia
- `wp_fluent_community_follows` - obserwacje

### Tabele CRM (Fluent CRM)
- `wp_fc_*` - dane klientów i kampanii
- `wp_fc_contact_meta` - metadane kontaktów
- `wp_fc_campaigns` - kampanie email

### Tabele Programu Partnerskiego
- `wp_fluent_affiliate_*` - dane partnerów
- `wp_fluent_affiliate_commissions` - prowizje
- `wp_fluent_affiliate_clicks` - kliknięcia

### Tabele WordPress
- `wp_posts` - posty i strony
- `wp_postmeta` - metadane postów
- `wp_comments` - komentarze
- `wp_options` - ustawienia
- `wp_terms` - kategorie i tagi

## Przywracanie Backup

### 1. Przygotowanie
```sql
-- Utwórz nową bazę danych
CREATE DATABASE nowa_platforma_korkiai;

-- Użyj bazy danych
USE nowa_platforma_korkiai;
```

### 2. Import
```bash
# Przez phpMyAdmin
# Wgraj plik .sql przez interfejs

# Przez wiersz poleceń
mysql -u username -p nowa_platforma_korkiai < netflyapp_platforma_korkiai_backup_20250909_145112.sql
```

### 3. Aktualizacja URL
```sql
-- Zaktualizuj URL w bazie danych
UPDATE wp_options SET option_value = 'https://nowa-domena.pl' WHERE option_name = 'home';
UPDATE wp_options SET option_value = 'https://nowa-domena.pl' WHERE option_name = 'siteurl';

-- Zaktualizuj URL w postach
UPDATE wp_posts SET post_content = REPLACE(post_content, 'https://stara-domena.pl', 'https://nowa-domena.pl');
```

## Bezpieczeństwo

⚠️ **WAŻNE**: Przed przywróceniem backup:
1. **Zmień hasła** wszystkich użytkowników
2. **Zaktualizuj klucze API** w ustawieniach
3. **Sprawdź uprawnienia** plików
4. **Zaktualizuj wp-config.php** z nowymi danymi

## Weryfikacja

Po przywróceniu sprawdź:
- [ ] Logowanie administratora
- [ ] Działanie społeczności
- [ ] Integracje z zewnętrznymi serwisami
- [ ] Wysyłanie emaili
- [ ] Program partnerski

---

*Backup utworzony automatycznie przez All-in-One WP Migration*