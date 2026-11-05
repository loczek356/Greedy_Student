# UC-08 — Automatyczne wyszukiwanie i dodawanie ofert ze zniżkami studenckimi

## Aktor

Agent

## Cel

Znalezienie w Internecie nowych ofert ze zniżkami studenckimi, zweryfikowanie ich i dodanie do Interaktywnej Mapy Zniżek Studenckich.

## Powiązane wymagania

FR-03, FR-08, FR-09, FR-10, NFR-01, NFR-03

## Warunek wstępny

Agent ma dostęp do źródeł internetowych zawierających informacje o ofertach oraz do ofert zapisanych już w systemie.

## Scenariusz podstawowy

1. System uruchamia agenta zgodnie z harmonogramem.
2. Agent wyszukuje w Internecie oferty skierowane do studentów, dotyczące restauracji, kawiarni, barów lub muzeów.
3. Agent odczytuje informacje o znalezionej ofercie: nazwę miejsca, lokalizację, kategorię, wysokość zniżki, warunki jej uzyskania, okres obowiązywania oraz adres źródła.
4. System sprawdza, czy oferta nie została już zapisana.
5. Agent weryfikuje źródło oraz potwierdza, że zniżka nadal obowiązuje i jej warunki są jasno określone.
6. System zapisuje zweryfikowaną ofertę wraz z datą weryfikacji i adresem źródła.
7. System udostępnia ofertę na interaktywnej mapie w lokalizacji miejsca, w którym można z niej skorzystać.

## Scenariusze alternatywne

**3a. Brakuje danych niezbędnych do pokazania oferty, np. lokalizacji miejsca:** System nie publikuje oferty, dopóki brakujące informacje nie zostaną uzupełnione i zweryfikowane.

**4a. Oferta jest już zapisana:** System nie tworzy duplikatu. Agent sprawdza aktualność istniejącej oferty i w razie potrzeby aktualizuje jej dane oraz datę weryfikacji.

**5a. Nie można potwierdzić źródła, warunków lub aktualności zniżki:** System nie publikuje oferty na mapie i oznacza ją jako wymagającą ponownej weryfikacji.

**2a. Nie znaleziono nowych ofert:** System kończy skanowanie bez dodawania wpisów.

**2b. Źródło internetowe jest niedostępne:** Agent pomija je, zapisuje informację o nieudanej próbie i ponawia sprawdzenie podczas kolejnego uruchomienia.

## Warunek końcowy

Nowe, zweryfikowane oferty są widoczne na mapie. Oferty niezweryfikowane nie są prezentowane studentom.
