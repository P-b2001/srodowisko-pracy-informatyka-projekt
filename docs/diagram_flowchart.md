# Flowchart (Mermaid)

```mermaid
flowchart TD
    A([START]) --> B[U¿ytkownik uruchamia klienta VPN]
    B --> C[Wpisuje login/has³o i wybiera profil VPN]
    C --> D{Czy jest Internet?}

    D -- NIE --> E[Komunikat: brak po³¹czenia]
    E --> Z([END])

    D -- TAK --> F[Wysy³a ¿¹danie zestawienia tunelu]
    F --> G[Brama Ruijie: uwierzytelnienie u¿ytkownika]
    G --> H{Dane poprawne?}

    H -- NIE --> I[Odmowa dostêpu + zapis w logach]
    I --> Z([END])

    H -- TAK --> J[Negocjacja IPsec: klucze i szyfrowanie]
    J --> K[Zestawienie L2 over IPsec]
    K --> L[Przydzia³ adresu IP / dostêp do podsieci firmowej]
    L --> M{Test: ping/zasób firmowy dzia³a?}

    M -- TAK --> N[U¿ytkownik pracuje zdalnie]
    N --> O[Roz³¹czenie VPN]
    O --> P[Zapis logów / zakoñczenie sesji]
    P --> Z([END])

    M -- NIE --> Q[Diagnostyka: DNS / trasy / firewall]
    Q --> O
