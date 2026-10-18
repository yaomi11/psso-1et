# Temat T02: Planowanie instalacji systemów klienta i serwera

## 1. Wymagania sprzętowe do instalacji systemów Windows
Przed instalacją systemu operacyjnego należy sprawdzić, czy komputer spełnia minimalne wymagania sprzętowe. W praktyce warto stosować parametry wyższe od minimalnych, ponieważ zapewniają one wygodniejszą pracę i lepszą wydajność systemu.

**Minimalne wymagania sprzętowe:**

| Parametr | Windows 11 Pro (x64) | Windows Server 2025 (x64) |
| :--- | :--- | :--- |
| **Procesor** | 1 GHz lub szybszy, co najmniej 2 rdzenie | 1,4 GHz 64-bit |
| **Pamięć RAM** | 4 GB | 2 GB |
| **Miejsce na dysku** | 64 GB | 32 GB |

*Uwaga: W środowisku laboratoryjnym opartym na VirtualBox wymagania dotyczące TPM 2.0 i Secure Boot dla Windows 11 mogą zostać pominięte poprzez odpowiednią konfigurację instalatora lub wykorzystanie nowszych wersji VirtualBox obsługujących emulację TPM.*

---

## 2. Przygotowanie nowej maszyny wirtualnej
Tworzenie maszyny wirtualnej dla każdego wirtualizowanego systemu operacyjnego w programie VirtualBox przebiega tak samo. Różnice mogą się pojawić przy wyborze ilości pamięci RAM, liczby kart sieciowych i obrazu wirtualnego dysku twardego.

### Pierwsze uruchomienie programu Oracle VirtualBox
Po uruchomieniu aplikacji zostanie wyświetlone okno Oracle VirtualBox Menedżer z odnośnikami do szybkiego wyboru kreatora określonej akcji.

![Główne okno programu VirtualBox](./screeny/01_virtualbox_start.png)

Domyślnie GUI VirtualBox ukrywa niektóre opcje, narzędzia i kreatory. Możesz wybrać ustawienia podstawowe lub zaawansowane. Kliknij **Plik → Globalne ustawienia...**

![Wybór globalnych ustawień z menu Plik](./screeny/02_globalne_ustawienia.png)

Proponuję wybrać tryb **Zaawansowane**. Tryb ten jest przeznaczony dla doświadczonych użytkowników, którzy chcą korzystać ze wszystkich funkcji VirtualBox (Tryb podstawowy jest dla osób preferujących prostszy interfejs).

![Wybór trybu zaawansowanego w ustawieniach](./screeny/03_tryb_zaawansowany.png)

### Tworzenie maszyny wirtualnej na przykładzie systemu Windows Server
Klikamy na przycisk **Nowa** lub *Create a new virtual machine (VM)* – Utwórz nową maszynę wirtualną.

![Przycisk Nowa maszyna wirtualna](./screeny/04_nowa_maszyna.png)

W pole **Nazwa** można wpisać dowolną nazwę maszyny wirtualnej. Jeżeli wpiszemy np. *Windows Serwer 2025* lub *Windows 11*, VirtualBox automatycznie wybierze nam typ systemu oraz jego wersję. Jeżeli nie wybierze, dobrym zwyczajem jest podać typ oraz wersję ręcznie (choć nie jest to bezwzględnie zobowiązujące).

![Wpisywanie nazwy maszyny i wybór systemu](./screeny/05_nazwa_systemu.png)

Kolejnym krokiem jest przydzielenie w zakładce **Specify virtual hardware** pamięci RAM. Powinno to być, dla wersji graficznej systemu, co najmniej zalecane minimum **2048 MB, czyli 2 GB oraz dwa rdzenie procesora**.

![Przydzielanie pamięci RAM i procesorów](./screeny/06_ram_cpu.png)

W zakładce **Specify virtual hard disk** utworzymy nowy wirtualny dysk twardy. Dysk ten nie jest dyskiem fizycznym, a jedynie plikiem (lub kilkoma) w naszym głównym systemie. Domyślnie VirtualBox zakłada utworzenie rozmiaru **50 GB** dla Windows Serwer 2025. Dyski wirtualne mają tę właściwość, że nie zajmują całej zadeklarowanej przestrzeni, a jedynie tyle, ile faktycznie wymaga system. Pozostawiamy domyślne ustawienia i klikamy w przycisk **Zakończ**.

![Tworzenie wirtualnego dysku twardego](./screeny/07_dysk_twardy.png)

### Konfiguracja maszyny wirtualnej (Karty sieciowe)
Maszyna wirtualna została przygotowana pod nowy system. Dostępna jest na liście maszyn wirtualnych. Teraz należy ją skonfigurować. Zaznaczamy naszą maszynę i wybieramy przycisk **Ustawienia**.

![Przycisk Ustawienia dla zaznaczonej maszyny](./screeny/08_ustawienia_maszyny.png)

W zakładce **Sieć** pierwszy interfejs karty sieciowej (Karta 1) ustawiamy na opcję **NAT** lub **Mostkowana karta sieciowa (bridged)** po to, aby nasz serwer mógł świadczyć usługę routingu z dostępem do Internetu. Naciskamy OK.

![Konfiguracja pierwszej karty sieciowej - NAT](./screeny/09_karta_sieciowa_1.png)

Dodajemy drugą kartę sieciową (Karta 2) po to, aby nasz serwer tworzył wirtualne środowisko, do którego możemy podpiąć kilka maszyn wirtualnych oraz świadczyć routing. Drugi interfejs karty sieciowej ustawiamy na opcję **Sieć wewnętrzna**. Klikamy OK.

![Konfiguracja drugiej karty sieciowej - Sieć wewnętrzna](./screeny/10_karta_sieciowa_2.png)

---

## 3. Usuwanie maszyny wirtualnej
Gdybyśmy z jakiegoś powodu chcieli usunąć maszynę wirtualną i utworzyć ją od początku, zaznaczamy maszynę przeznaczoną do usunięcia i klikamy w menu: **Maszyna → Usuń...**

![Usuwanie maszyny wirtualnej z menu](./screeny/11_usuwanie_maszyny.png)

Zaznaczamy opcję **Usuń pliki maszyny wirtualnej i wirtualne dyski twarde** (Delete the virtual machine files and virtual hard disks), a następnie klikamy na przycisk **Usuń**.

![Potwierdzenie usunięcia plików maszyny i wirtualnego dysku](./screeny/12_potwierdzenie_usuniecia.png)
