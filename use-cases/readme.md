flowchart LR
    Student([Student])
    Agent([Agent Systemowy])

    subgraph System ["Interaktywna Mapa Zniżek Studenckich"]
        direction TB
        UC1([Przeglądanie mapy zniżek])
        UC2([Wyszukiwanie obiektów ze zniżkami])
        UC3([Wyszukiwanie najbliższych ofert])
        UC4([Filtrowanie ofert wg atrybutów])
        UC5([Przeglądanie szczegółów i warunków oferty])
        UC6([Sprawdzanie aktualności ofert])

        UC7([Automatyczne wyszukiwanie ofert w Internecie])
        UC8([Weryfikacja i dodawanie ofert do mapy])
    end

    Student --- UC1
    Student --- UC2
    Student --- UC3
    Student --- UC4
    Student --- UC5
    Student --- UC6

    Agent --- UC7
    Agent --- UC8
