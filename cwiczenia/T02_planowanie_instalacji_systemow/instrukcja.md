# Temat T02: Planowanie instalacji systemów klienta i serwera[cite: 2]

## 1. Wymagania sprzętowe do instalacji systemów Windows[cite: 2]
Przed instalacją systemu operacyjnego należy sprawdzić, czy komputer spełnia minimalne wymagania sprzętowe.[cite: 2] W praktyce warto stosować parametry wyższe od minimalnych, ponieważ zapewniają one wygodniejszą pracę i lepszą wydajność systemu.[cite: 2]

**Minimalne wymagania sprzętowe:**[cite: 2]

| Parametr | Windows 11 Pro (x64) | Windows Server 2025 (x64) |
| :--- | :--- | :--- |
| **Procesor** | 1 GHz lub szybszy, co najmniej 2 rdzenie[cite: 2] | 1,4 GHz 64-bit[cite: 2] |
| **Pamięć RAM** | 4 GB[cite: 2] | 2 GB[cite: 2] |
| **Miejsce na dysku** | 64 GB[cite: 2] | 32 GB[cite: 2] |

*Uwaga: W środowisku laboratoryjnym opartym na VirtualBox wymagania dotyczące TPM 2.0 i Secure Boot dla Windows 11 mogą zostać pominięte poprzez odpowiednią konfigurację instalatora lub wykorzystanie nowszych wersji VirtualBox obsługujących emulację TPM.*[cite: 2]

---

## 2. Przygotowanie nowej maszyny wirtualnej[cite: 2]
Tworzenie maszyny wirtualnej dla każdego wirtualizowanego systemu operacyjnego w programie VirtualBox przebiega tak samo.[cite: 2] Różnice mogą się pojawić przy wyborze ilości pamięci RAM, liczby kart sieciowych i obrazu wirtualnego dysku twardego.[cite: 2]

### Pierwsze uruchomienie programu Oracle VirtualBox[cite: 2]
Po uruchomieniu aplikacji zostanie wyświetlone okno Oracle VirtualBox Menedżer z odnośnikami do szybkiego wyboru kreatora określonej akcji.[cite: 2]

![Główne okno programu VirtualBox](./screeny/01_virtualbox_start.png)

Domyślnie GUI VirtualBox ukrywa niektóre opcje, narzędzia i kreatory.[cite: 3] Możesz wybrać ustawienia podstawowe lub zaawansowane.[cite: 3] Kliknij **Plik → Globalne ustawienia...**[cite: 3]

![Wybór globalnych ustawień z menu Plik](./screeny/02_globalne_ustawienia.png)

Proponuję wybrać tryb **Zaawansowane**.[cite: 4] Tryb ten jest przeznaczony dla doświadczonych użytkowników, którzy chcą korzystać ze wszystkich funkcji VirtualBox (Tryb podstawowy jest dla osób preferujących prostszy interfejs).[cite: 3]

![Wybór trybu zaawansowanego w ustawieniach](./screeny/03_tryb_zaawansowany.png)

### Tworzenie maszyny wirtualnej na przykładzie systemu Windows Server[cite: 4]
Klikamy na przycisk **Nowa** lub *Create a new virtual machine (VM)* – Utwórz nową maszynę wirtualną.[cite: 4]

![Przycisk Nowa maszyna wirtualna](./screeny/04_nowa_maszyna.png)

W pole **Nazwa** można wpisać dowolną nazwę maszyny wirtualnej.[cite: 4] Jeżeli wpiszemy np. *Windows Serwer 2025* lub *Windows 11*, VirtualBox automatycznie wybierze nam typ systemu oraz jego wersję.[cite: 4, 5] Jeżeli nie wybierze, dobrym zwyczajem jest podać typ oraz wersję ręcznie (choć nie jest to bezwzględnie zobowiązujące).[cite: 5]

![Wpisywanie nazwy maszyny i wybór systemu](./screeny/05_nazwa_systemu.png)

Kolejnym krokiem jest przydzielenie w zakładce **Specify virtual hardware** pamięci RAM.[cite: 5] Powinno to być, dla wersji graficznej systemu, co najmniej zalecane minimum **2048 MB, czyli 2 GB oraz dwa rdzenie procesora**.[cite: 5]

![Przydzielanie pamięci RAM i procesorów](./screeny/06_ram_cpu.png)

W zakładce **Specify virtual hard disk** utworzymy nowy wirtualny dysk twardy.[cite: 5] Dysk ten nie jest dyskiem fizycznym, a jedynie plikiem (lub kilkoma) w naszym głównym systemie.[cite: 5, 6] Domyślnie VirtualBox zakłada utworzenie rozmiaru **50 GB** dla Windows Serwer 2025.[cite: 6] Dyski wirtualne mają tę właściwość, że nie zajmują całej zadeklarowanej przestrzeni, a jedynie tyle, ile faktycznie wymaga system.[cite: 6] Pozostawiamy domyślne ustawienia i klikamy w przycisk **Zakończ**.[cite: 6]

![Tworzenie wirtualnego dysku twardego](./screeny/07_dysk_twardy.png)

### Konfiguracja maszyny wirtualnej (Karty sieciowe)[cite: 6]
Maszyna wirtualna została przygotowana pod nowy system.[cite: 6] Dostępna jest na liście maszyn wirtualnych.[cite: 6] Teraz należy ją skonfigurować. Zaznaczamy naszą maszynę i wybieramy przycisk **Ustawienia**.[cite: 6]

![Przycisk Ustawienia dla zaznaczonej maszyny](./screeny/08_ustawienia_maszyny.png)

W zakładce **Sieć** pierwszy interfejs karty sieciowej (Karta 1) ustawiamy na opcję **NAT** lub **Mostkowana karta sieciowa (bridged)** po to, aby nasz serwer mógł świadczyć usługę routingu z dostępem do Internetu.[cite: 7] Naciskamy OK.[cite: 7]

![Konfiguracja pierwszej karty sieciowej - NAT](./screeny/09_karta_sieciowa_1.png)

Dodajemy drugą kartę sieciową (Karta 2) po to, aby nasz serwer tworzył wirtualne środowisko, do którego możemy podpiąć kilka maszyn wirtualnych oraz świadczyć routing.[cite: 7] Drugi interfejs karty sieciowej ustawiamy na opcję **Sieć wewnętrzna**.[cite: 7] Klikamy OK.[cite: 7]

![Konfiguracja drugiej karty sieciowej - Sieć wewnętrzna](./screeny/10_karta_sieciowa_2.png)

---

## 3. Usuwanie maszyny wirtualnej[cite: 8]
Gdybyśmy z jakiegoś powodu chcieli usunąć maszynę wirtualną i utworzyć ją od początku, zaznaczamy maszynę przeznaczoną do usunięcia i klikamy w menu: **Maszyna → Usuń...**[cite: 8]

![Usuwanie maszyny wirtualnej z menu](./screeny/11_usuwanie_maszyny.png)

Zaznaczamy opcję **Usuń pliki maszyny wirtualnej i wirtualne dyski twarde** (Delete the virtual machine files and virtual hard disks), a następnie klikamy na przycisk **Usuń**.[cite: 8]

![Potwierdzenie usunięcia plików maszyny i wirtualnego dysku](./screeny/12_potwierdzenie_usuniecia.png)
