# Wymagania

Wymagania (*Requirements*) określają, co system powinien robić oraz jakie właściwości i ograniczenia powinien spełniać.

Wymagania powinny być jednoznaczne, zrozumiałe i możliwe do zweryfikowania. Opisujemy oczekiwane zachowanie systemu, a nie sposób jego implementacji.

## Oznaczenia

- **FR** (*Functional Requirement*) — wymaganie funkcjonalne, określające, co system powinien robić.
- **NFR** (*Non-Functional Requirement*) — wymaganie niefunkcjonalne, określające, jakie właściwości lub ograniczenia powinien spełniać system.

Każde wymaganie posiada unikalny identyfikator, np. `FR-01` lub `NFR-01`.

## Wymagania funkcjonalne

| ID | Wymaganie |
|---|---|
| FR-01 | System umożliwia użytkownikowi przeglądanie interaktywnej mapy ofert ze zniżkami studenckimi. |
| FR-02 | System umożliwia wyszukiwanie restauracji, kawiarni, barów i muzeów oferujących zniżki dla studentów. |
| FR-03 | System prezentuje lokalizacje obiektów oferujących zniżki na interaktywnej mapie. |
| FR-04 | System umożliwia wyszukiwanie najbliższych ofert na podstawie lokalizacji użytkownika. |
| FR-05 | System umożliwia filtrowanie ofert według kategorii obiektu. |
| FR-06 | System umożliwia filtrowanie ofert według odległości od wybranej lokalizacji. |
| FR-07 | System umożliwia filtrowanie ofert według procentowej wysokości zniżki. |
| FR-08 | System prezentuje informacje o dostępnych zniżkach, w tym wysokość zniżki i warunki jej uzyskania. |
| FR-09 | System automatycznie wyszukuje w Internecie nowe oferty ze zniżkami studenckimi. |
| FR-10 | System umożliwia automatyczne dodawanie nowo znalezionych ofert do mapy po ich weryfikacji. |
| FR-11 | System umożliwia użytkownikowi sprawdzanie aktualności dostępnych ofert ze zniżkami. |
| FR-12 | System umożliwia użytkownikowi szybkie znalezienie ofert odpowiadających jego potrzebom, np. taniego obiadu lub kawy w pobliżu kampusu. |

## Wymagania niefunkcjonalne

| ID | Wymaganie |
|---|---|
| NFR-01 | System aktualizuje informacje o ofertach ze zniżkami nie rzadziej niż raz na 24 godziny. |
| NFR-02 | System prezentuje wyniki wyszukiwania w czasie nieprzekraczającym 2 sekund dla 95% zapytań. |
| NFR-03 | System prezentuje wyłącznie oferty, których źródło i warunki zniżki zostały zweryfikowane. |
| NFR-04 | System nie wymaga od użytkownika podawania dokładnej lokalizacji, jeśli może on wskazać wydział lub inną lokalizację ręcznie. |
| NFR-05 | System nie przechowuje dokładnej lokalizacji użytkownika dłużej, niż jest to niezbędne do realizacji wyszukiwania. |
| NFR-06 | Interfejs użytkownika jest responsywny i dostosowany do urządzeń mobilnych oraz komputerów. |
| NFR-07 | Interfejs użytkownika spełnia wymagania WCAG 2.2 na poziomie AA. |

## Pytania otwarte

- Co oznacza, że zniżka jest aktualna i jak często należy sprawdzać jej ważność?
- Jak często agent powinien wyszukiwać nowe oferty i sprawdzać, czy istniejące zniżki nadal obowiązują?
- Jak system powinien weryfikować wiarygodność ofert ze zniżkami znalezionych przez agenta w Internecie?
- Czy automatycznie znalezione oferty powinny być publikowane od razu, czy dopiero po dodatkowej weryfikacji?
- Czy każda zniżka musi wymagać okazania legitymacji studenckiej, czy dopuszczalne są również inne formy potwierdzenia statusu studenta?
- Czy system powinien uwzględniać zniżki ograniczone czasowo, np. obowiązujące tylko w określonych godzinach?
- Od jakiego punktu należy mierzyć odległość: od aktualnej lokalizacji użytkownika, wybranego wydziału czy całego kampusu?
- Czy system powinien uwzględniać również ceny produktów i usług po zastosowaniu zniżki, czy wyłącznie procentową wysokość zniżki?
- Czy użytkownik powinien mieć możliwość zgłaszania nieaktualnych ofert lub błędnych informacji?

