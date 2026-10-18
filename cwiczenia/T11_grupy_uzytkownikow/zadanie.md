# Zadanie praktyczne: Tworzenie i zarządzanie grupami zabezpieczeń w usłudze Active Directory

## 1. Warunki początkowe
Do dyspozycji są dwie maszyny wirtualne:
* **Windows Server 2025** z zainstalowaną usługą Active Directory Domain Services (AD DS).
* **Windows 11** będący członkiem domeny.

---

## 2. Treść zadania

W domenie `xxxx.local` (gdzie `xxxx` to nazwa domeny na Twoim serwerze) wykonaj następujące czynności:

### Krok 1: Struktura organizacyjna
1. Utwórz jednostkę organizacyjną (OU) o nazwie: **TI**.
2. W jednostce organizacyjnej **TI** utwórz dwie grupy zabezpieczeń o następujących parametrach:

| Parametr | Grupa 1 | Grupa 2 |
| :--- | :--- | :--- |
| **Nazwa grupy** | Technicy | Serwis |
| **Typ grupy** | Zabezpieczenia | Zabezpieczenia |
| **Zakres grupy**| Globalna | Globalna |

### Krok 2: Tworzenie kont użytkowników
1. W jednostce organizacyjnej **TI** utwórz następujące konta użytkowników:

| Parametr | Użytkownik 1 | Użytkownik 2 |
| :--- | :--- | :--- |
| **Imię** | Jan | Maria |
| **Nazwisko** | Kolski | Nowik |
| **Nazwa logowania** | j.kolski | m.nowik |
| **Hasło** | Qwerty123! | Qwerty123! |

2. **Dla obu kont ustaw:**
   * Wymuszenie zmiany hasła przy pierwszym logowaniu.
   * Pozostaw konta aktywne (odznaczona opcja wyłączenia konta).

### Krok 3: Przypisywanie do grup
Dodaj nowo utworzonych użytkowników do odpowiednich grup:

| Nazwa grupy | Członkowie |
| :--- | :--- |
| **Technicy** | Jan Kolski, Maria Nowik |
| **Serwis** | Jan Kolski |

### Krok 4: Operacje w wierszu poleceń (PowerShell / CMD)
1. Uruchom Wiersz polecenia (lub PowerShell) jako administrator.
2. Utwórz grupę zabezpieczeń o nazwie **Praktykanci**, wykorzystując polecenie (pamiętaj o podmianie `xxxx` na nazwę swojej domeny):
   ```cmd
   dsadd group "CN=Praktykanci,OU=TI,DC=xxxx,DC=local" -secgrp yes -scope g
   ```
3. Dodaj użytkownika Jan Kowalski do grupy Praktykanci poleceniem:
   ```cmd
   dsmod group "CN=Praktykanci,OU=TI,DC=xxxx,DC=local" -addmbr "CN=Jan Kolski,OU=TI,DC=xxxx,DC=local"
   ```
4. Wyświetl listę wszystkich użytkowników domeny poleceniem:
   ```cmd
   dsquery user -name *
   ```
5. Wyświetl listę wszystkich grup poleceniem:
   ```cmd
   dsquery group -name *
   ```
6. Na komputerze z systemem Windows 11:
6.1. Zaloguj się do domeny przy użyciu konta: xxxx\j.kolski
6.2. Zmień hasło przy pierwszym logowaniu na: P@ssw0rd

7. Po zalogowaniu uruchom Wiersz polecenia i wykonaj polecenia:
'whoami'
oraz
'whoami /groups'

8. Utworzenie folderu roboczego.
8.1. Na Pulpicie użytkownika utwórz folder: TI_Zadanie
8.2. W folderze utwórz plik tekstowy: potwierdzenie.txt i wpisz tekst: Konto domenowe zostało poprawnie utworzone i zweryfikowane.
