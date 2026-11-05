# UC-05 — Wyświetlanie szczegółów oferty

## Aktor
Student

## Cel
Zapoznanie się ze szczegółowymi informacjami o wybranej ofercie, w tym poznanie wysokości zniżki studenckiej oraz warunków jej uzyskania.

## Powiązane wymagania
FR-01, FR-08

## Warunek wstępny
Student wybrał konkretną ofertę ze zniżką wyświetloną na interaktywnej mapie.

## Scenariusz podstawowy
1. Student klika w wybrany punkt (ofertę) na Interaktywnej Mapie Zniżek Studenckich.
2. System przetwarza żądanie i pobiera aktualne dane dla wskazanego lokalu.
3. System prezentuje informacje o dostępnych ofertach ze zniżkami studenckimi, w tym wysokość zniżki i warunki jej uzyskania.
4. Student po zapoznaniu się ze szczegółami zamyka widok oferty i wraca do przeglądania mapy.

## Scenariusze alternatywne
**3a. Wybrana oferta wygasła lub została usunięta w trakcie przeglądania:**
- System wyświetla komunikat informujący, że promocja przestała obowiązywać.
- System wygasza ofertę.
- System usuwa ofertę z widoku mapy.