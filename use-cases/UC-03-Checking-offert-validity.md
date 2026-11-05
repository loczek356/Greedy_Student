# UC-03 — Sprawdzanie aktualności oferty ze zniżką studencką

## Aktor
Student

## Cel
Weryfikacja, czy prezentowana w systemie oferta zniżkowa jest nadal ważna i obowiązuje w danym lokalu.

## Powiązane wymagania
FR-08, FR-11

## Warunek wstępny
Student wybrał konkretną ofertę ze zniżką wyświetloną na interaktywnej mapie.

## Scenariusz podstawowy
1. Student wyświetla szczegółowe informacje o wybranej ofercie.
2. Student wybiera opcję weryfikacji aktualności oferty.
3. System wysyła zapytanie sprawdzające status i datę ostatniej weryfikacji oferty.
4. System potwierdza aktualność oferty i wyświetla studentowi datę ostatniego sprawdzenia oraz szczegółowe warunki jej uzyskania.

## Scenariusze alternatywne
**4a. Oferta jest nieaktualna:**
- System wygasza ofertę.
- System wyświetla komunikat, że promocja przestała obowiązywać.
- System usuwa ofertę z widoku mapy.
