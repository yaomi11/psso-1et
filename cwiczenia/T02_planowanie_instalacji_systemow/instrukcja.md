# Temat T02: Planowanie instalacji systemów operacyjnych

## 1. Cel ćwiczenia
* Zrozumienie minimalnych i zalecanych wymagań sprzętowych dla systemów **Windows Server 2025** oraz **Windows 11**.
* Dobór odpowiedniego schematu partycjonowania dysków (GPT / MBR) oraz systemów plików (**NTFS** / **ReFS**).
* Zaplanowanie wersji systemów (np. wersje z interfejsem graficznym *Desktop Experience* vs *Server Core*).

## 2. Środowisko i wymagania wstępne
* Dokumentacja techniczna Microsoft dotycząca Windows Server 2025 i Windows 11.
* Arkusz roboczy lub notes do zaplanowania parametrów maszyn wirtualnych.

## 3. Instrukcja krok po kroku

### Krok 1: Zestawienie wymagań sprzętowych
Przed przystąpieniem do tworzenia maszyn wirtualnych należy przeanalizować wymagania obu systemów:

| Parametr | Windows Server 2025 | Windows 11 |
| :--- | :--- | :--- |
| **Architektura** | 64-bit (x64) | 64-bit (x64 / ARM64) |
| **Procesor** | 1.4 GHz, 64-bit | 1 GHz, min. 2 rdzenie |
| **Pamięć RAM** | min. 2 GB (zalecane 4 GB+) | min. 4 GB |
| **Przestrzeń dyskowa**| min. 32 GB | min. 64 GB |
| **Wymagania bezpieczeństwa**| Układ TPM, Secure Boot | Wymagany TPM 2.0, Secure Boot, UEFI |

### Krok 2: Wybór wersji systemu Windows Server 2025
Podczas planowania instalacji serwera decydujemy o sposobie zarządzania:
* **Windows Server 2025 (Desktop Experience):** Pełny interfejs graficzny znany z systemów klienckich – polecany do laboratoriów edukacyjnych.
* **Windows Server 2025 (Server Core):** Wersja pozbawiona graficznego pulpitu, zarządzana wyłącznie przez wiersz poleceń, PowerShell lub zdalnie – oszczędzająca zasoby RAM i CPU.

### Krok 3: Planowanie partycjonowania i systemów plików
* **Typ tablicy partycji:** Nowoczesne systemy wymagają standardu **GPT** (GUID Partition Table) współpracującego z trybem UEFI.
* **Systemy plików:**
  * **NTFS:** Standardowy system plików dla partycji systemowych i użytkowników.
  * **ReFS (Resilient File System):** Zaawansowany system plików dla Windows Server, zapewniający odporność na uszkodzenia danych i optymalizację pod duże wolumeny magazynowe.

---

## 4. Sprawdzenie wiedzy / Zadanie utrwalające
1. Czym różni się wersja Windows Server z interfejsem *Desktop Experience* od wersji *Server Core*?
2. Dlaczego przy instalacji Windows 11 i Windows Server 2025 na nowoczesnym sprzęcie lub maszynach wirtualnych obowiązkowy jest wybór trybu UEFI zamiast starszego BIOS/CSM?
