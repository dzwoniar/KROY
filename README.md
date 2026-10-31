# KROY — landing page marki streetwearowej

Prototyp kampanijnej strony marki odzieżowej: zapis po przewodnik doboru ubrań oraz rabat, z osobnym ekranem podziękowania. Projekt skupia się na ścieżce pozyskania adresu e-mail, komunikacji oferty i interakcjach strony.

**Status:** statyczne demo frontendowe. Formularze przełączają widok, ale nie zapisują adresów e-mail ani nie dostarczają przewodnika.

## Funkcje

- Responsywna strona oferty i formularz zapisu w głównej sekcji.
- Walidacja formatu e-mail oraz sprawdzanie checkboxa zgody w głównym formularzu.
- Ekran podziękowania wyświetlany po poprawnym przejściu formularza.
- Popup exit intent z dodatkowym polem e-mail, zamykany przyciskiem lub kliknięciem tła.
- Dolne CTA na urządzeniach mobilnych i animacje elementów przy przewijaniu.

## Technologia i struktura

Wszystkie elementy znajdują się w [index.html](index.html): HTML, wewnętrzny CSS oraz JavaScript bez frameworka. `IntersectionObserver` odpowiada za animacje, a funkcje `handleSubmit()` i `showThankYou()` za walidację i zmianę widoku. Google Fonts dostarcza kroje Space Mono i Outfit.

```text
.
├── index.html   # landing, ekran podziękowania, style i interakcje
└── README.md
```

Repozytorium nie wymaga npm, bundlera, serwera aplikacyjnego ani bazy danych.

## Uruchomienie lokalne

Wymagane: Git, Python 3 i współczesna przeglądarka.

```sh
git clone https://github.com/dzwoniar/KROY.git
cd KROY
python -m http.server 8000
```

Otwórz [http://localhost:8000](http://localhost:8000). Na Windows alternatywą jest `py -3 -m http.server 8000`. Zatrzymanie: `Ctrl+C`. Internet jest potrzebny do pobrania fontów; pozostała logika działa lokalnie.

## Przepływ danych

`handleSubmit()` zatrzymuje domyślne wysłanie formularza, sprawdza adres i — dla formularza głównego — zgodę. Po powodzeniu `showThankYou()` ukrywa landing, pokazuje ekran podziękowania i przewija na początek strony. Nie ma wywołań API, zapisu na listę mailingową ani trwałego magazynu zgłoszeń.

## Ograniczenia i miejsca rozbudowy

- Przycisk pobrania przewodnika ma `href="#"` i blokuje domyślne kliknięcie. Plik przewodnika nie znajduje się w repozytorium.
- Linki społecznościowe, udostępnianie i polityka prywatności są placeholderami.
- Popup sprawdza format e-mail, ale nie ma odpowiednika checkboxa głównego formularza. Obsługę zgód i integrację mailingową trzeba zaprojektować przy wdrożeniu.
- Wartości rabatów, dostępności i referencje są częścią treści demonstracyjnej; kod nie obsługuje sklepu, stanów magazynowych, płatności ani kuponów.
- Integrację usługi mailingowej można dodać przed przełączeniem widoku w `showThankYou()`; sekrety API powinny pozostać na backendzie.

Repozytorium nie zawiera automatycznych testów. Przy zmianach warto sprawdzić błędny i poprawny e-mail, checkbox zgody, przełączanie ekranów, popup oraz mobilne CTA.
