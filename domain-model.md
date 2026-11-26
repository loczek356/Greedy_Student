```mermaid
classDiagram
    direction TB

    class Location {
        +double Latitude
        +double Longitude
        +DistanceTo(Location other) double
    }

    class Faculty {
        +int Id
        +string Name
        +Location Location
    }

    class Student {
        +int Id
        +string Name
        +Faculty Faculty
        +Location CurrentLocation
        +UpdateLocation(Location location) void
    }

    class Category {
        <<enumeration>>
        RESTAURANT
        CAFE
        BAR
        MUSEUM
    }

    class Place {
        <<abstract>>
        +int Id
        +string Name
        +string Address
        +Location Location
        +Category Category
    }

    class Restaurant
    class Cafe
    class Bar
    class Museum

    class VerificationStatus {
        <<enumeration>>
        PENDING
        VERIFIED
        REJECTED
    }

    class Discount {
        +int Id
        +decimal Percentage
        +string Description
        +DateTime ValidFrom
        +DateTime ValidTo
        +string SourceUrl
        +VerificationStatus Status
        +IsActive() bool
    }

    class OfferFilter {
        +Category? Category
        +double? MaxDistanceKm
        +decimal? MinDiscountPercent
        +Location ReferencePoint
        +Matches(Discount discount) bool
    }

    class DiscountMap {
        +List~Discount~ Discounts
        +AddDiscount(Discount discount) void
        +GetNearby(Location point, OfferFilter filter) List~Discount~
    }

    class RecommendationService {
        +Recommend(Student student, OfferFilter filter) List~Discount~
    }

    class LocationService {
        +GetStudentLocation(Student student) Location
    }

    class DiscountAgent {
        +SearchWeb() List~Discount~
        +ExtractOffers(string pageContent) List~Discount~
        +Run() void
    }

    class DiscountVerifier {
        +Verify(Discount discount) VerificationStatus
    }

    Place <|-- Restaurant
    Place <|-- Cafe
    Place <|-- Bar
    Place <|-- Museum

    Place --> Category
    Place --> Location
    Faculty --> Location
    Student --> Faculty : studiuje na
    Student --> Location : aktualna pozycja

    Place "1" o-- "0..*" Discount : oferuje
    Discount --> VerificationStatus

    DiscountMap "1" o-- "*" Place : zawiera
    DiscountMap ..> OfferFilter : używa

    RecommendationService ..> DiscountMap : pobiera oferty
    RecommendationService ..> LocationService : pobiera lokalizację
    RecommendationService ..> OfferFilter : filtruje
    RecommendationService ..> Student

    DiscountAgent ..> DiscountVerifier : weryfikuje oferty
    DiscountAgent ..> DiscountMap : dodaje zweryfikowane
    DiscountVerifier ..> Discount
```

# Decyzje projektowe: Interaktywna Mapa Zniżek Studenckich

## Decyzja 1: `Place` jako klasa abstrakcyjna z podklasami

**Problem i alternatywy.** Cztery typy miejsc (restauracja, kawiarnia, bar, muzeum) mają wspólne dane, ale mogą różnić się zachowaniem. Rozważano jedną klasę z polem `Category`, osobne niezależne klasy oraz klasę abstrakcyjną z podklasami.

**Rozwiązanie.** Klasa abstrakcyjna `Place` z podklasami i polem `Category`. Wspólny kod jest w jednym miejscu, `DiscountMap` pracuje na typie bazowym, a filtrowanie to proste porównanie `Category`.

**Konsekwencje.**
- Nowy typ miejsca to jedna nowa klasa, bez zmian w mapie i filtrach.
- Kategoria jest zapisana podwójnie (typ klasy i pole), więc trzeba pilnować spójności, np. ustawiając ją w konstruktorze podklasy.
- Przy dużej liczbie typów lepsza może być kompozycja zamiast dziedziczenia.

---

## Decyzja 2: Rozdzielenie `DiscountAgent` i `DiscountVerifier`

**Problem i alternatywy.** Dane z Internetu bywają błędne lub nieaktualne, a na mapie mają być tylko sprawdzone oferty. Rozważano dodawanie ofert na mapę od razu, połączenie wyszukiwania i weryfikacji w jednej klasie oraz rozdzielenie obu zadań.

**Rozwiązanie.** Agent wyszukuje oferty i tworzy je ze statusem `PENDING`, a weryfikator zmienia status na `VERIFIED` lub `REJECTED`. Na mapę trafiają tylko oferty zweryfikowane. Każda klasa ma jedną odpowiedzialność.

**Konsekwencje.**
- Użytkownik widzi wyłącznie sprawdzone zniżki, a weryfikator można rozwijać niezależnie.
- Dodatkowy etap opóźnia pojawienie się oferty na mapie.
- Jakość całego systemu zależy od jakości weryfikatora.

---

## Decyzja 3: Filtrowanie przez obiekt `OfferFilter`

**Problem i alternatywy.** Filtry (kategoria, odległość, procent zniżki) trzeba łączyć dowolnie, a odległość liczyć od wydziału lub od pozycji studenta. Rozważano osobne metody filtrujące, jedną metodę z rosnącą liczbą parametrów oraz osobny obiekt filtra.

**Rozwiązanie.** `OfferFilter` z opcjonalnymi kryteriami i polem `ReferencePoint`. Metoda `Matches()` zawiera całą logikę dopasowania w jednym miejscu.

**Konsekwencje.**
- Nowe kryterium to jedno pole i jeden warunek, a filtr można zapisać lub przekazać dalej.
- Przy wielu kryteriach `Matches()` może się rozrosnąć, wtedy warto użyć wzorca Specification.
- Wartość `null` musi konsekwentnie oznaczać „brak kryterium", żeby pusty filtr zwracał wszystkie oferty.
