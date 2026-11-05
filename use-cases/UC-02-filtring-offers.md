# UC-02 — Filtrowanie ofert ze zniżkami studenckimi

## Aktor
Student

## Cel
Zawężenie listy prezentowanych ofert na mapie według wybranych kryteriów, takich jak kategoria obiektu, odległość od punktu odniesienia lub procentowa wysokość zniżki.

## Powiązane wymagania
FR-05, FR-06, FR-07

## Warunek wstępny
Student wyświetla Interaktywną Mapę Zniżek Studenckich z dostępnymi ofertami.

## Scenariusz podstawowy
1. Student otwiera panel filtrowania ofert.
2. Student wybiera kategorię obiektów (np. restauracje, kawiarnie, bary, muzea).
3. Student określa maksymalną odległość od wybranej lokalizacji (np. od swojego wydziału).
4. Student określa minimalną procentową wysokość zniżki.
5. Student zatwierdza wybrane kryteria filtrowania.
6. System filtruje bazę ofert zgodnie z podanymi parametrami.
7. System odświeża interaktywną mapę, prezentując wyłącznie oferty spełniające kryteria.

## Scenariusze alternatywne
**6a. Brak ofert spełniających kryteria:**
- System wyświetla komunikat o braku wyników dla podanych filtrów.
- System proponuje ich zresetowanie lub zmianę parametrów.
