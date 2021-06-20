<div align="center">
  
<img src="https://user-images.githubusercontent.com/43359077/120787762-f9cc9080-c52f-11eb-9762-6bfe73111e38.png" alt="logo" width="500"/>

<div align="left"> 


##### Jak zainstalować Arch Linux krok po kroku ze zrzutami ekranu. Krótko: Ten samouczek pokazuje, jak zainstalować Arch Linux w łatwych do wykonania krokach. Obrazy instalacyjne Archa dostępne są do pobrania tutaj : https://www.archlinux.org/download/ Po pobraniu ISO utwórz rozruchowe urządzenie USB za pomocą polecenia **dd** Linux.
```markdown
# sudo dd if=path-to-image.iso  of=/dev/sdX bs=4M status='progress'
  (Zastąp image.iso, np archlinux-2021.06.01-x86_64.iso)
  (Zastąp sdX nazwą urządzenia, np.)
```
##### Natomiast do wykonania bootowalnego pendrive-a pod Windowsem najlepiej jest użyć programu Etcher -> https://www.balena.io/etcher/ lub Ventoy -> https://www.ventoy.net/en/index.html. Wypalamy obraz przy pomocy programu UltraISO-> https://www.ultraiso.com np płycie a następnie uruchamiamy system z wybranego nośnika. Po uruchomieniu ujrzymy ekran do wyboru wersji systemu 32 lub 64 bitowy.
##### Archlinux jest to świetny system dla naszego desktopa?

#### Spis treści 

* [**Arch Linux - instalacja i konfiguracja**](#arch-linux---instalacja-i-konfiguracja)
* [**Przed instalacją**](#przed-instalacją)
  * [**1. Konfiguracja Wi-Fi – sieci bezprzewodowe**](#1-konfiguracja-wi-fi--sieci-bezprzewodowe)
  * [**2. Połącz się z Internetem**](#2-połącz-się-z-internetem)
  * [**3. Układ klawiatury**](#3-układ-klawiatury)
  * [**4. Zaktualizuj systemowy zegar**](#4-zaktualizuj-systemowy-zegar)
  * [**5. Partycjonuj dyski**](#5-partycjonuj-dyski)
  * [**6. Formatowanie partycji UEFI with GPT**](#6-formatowanie-partycji-uefi-with-gpt)
  * [**7. Zamontuj system plików**](#7-zamontuj-system-plików)
  * [**8. Instalacja systemu podstawowego**](#8-instalacja-systemu-podstawowego)
  * [**9. Generowanie fstab**](#9-generowanie-fstab)
  * [**10. Wejdź przez chroot do nowego systemu**](#10-wejdź-przez-chroot-do-nowego-systemu)
  * [**11. Strefa czasowa - Ustaw czas**](#11-strefa-czasowa---ustaw-czas)
  * [**12. Konfiguracja języka**](#12-konfiguracja-języka)
  * [**13. Plik konfiguracyjny dla ustawień regionalnych - Ustaw zmienną**](#13-plik-konfiguracyjny-dla-ustawień-regionalnych---ustaw-zmienną)
  * [**14. Plik konfiguracyjny konsoli wirtualnej - Czcionka konsoli**](#14-plik-konfiguracyjny-konsoli-wirtualnej---czcionka-konsoli)
  * [**15. Ustaw nazwę hosta**](#15-ustaw-nazwę-hosta)
  * [**16. Musisz również dodać tę nazwę do pliku hosts**](#16-musisz-również-dodać-tę-nazwę-do-pliku-hosts)
  * [**17. Konfiguracja sieci**](#17-konfiguracja-sieci)
  * [**18. Włącz sieć**](#18-włącz-sieć)
  * [**19. Tworzenie ramdisc**](#19-tworzenie-ramdisc)
  * [**20. Hasło użytkownika root**](#20-hasło-użytkownika-root)
  * [**21. Jeśli posiadasz procesor Intela, zainstaluj pakiet intel-ucode.**](#21-jeśli-posiadasz-procesor-intela-zainstaluj-pakiet-intel-ucode)
  * [**22. BIOS GRUB**](#22-bios-grub)
  * [**23. Teraz wiele osób ma dyski SSD, które obsługują TRIM. Dla bezpiecznej, cotygodniowej usługi TRIM na dyskach SSD i wszystkich innych urządzeniach, które umożliwiają obsługę TRIM**](#23-teraz-wiele-osób-ma-dyski-ssd-które-obsługują-trim-dla-bezpiecznej-cotygodniowej-usługi-trim-na-dyskach-ssd-i-wszystkich-innych-urządzeniach-które-umożliwiają-obsługę-trim)
  * [**24. Wyjście z chroot**](#24-wyjście-z-chroot)
  * [**25. Logowanie się do systemu**](#25-logowanie-się-do-systemu)
  * [**26. Dodaj użytkownika**](#26-dodaj-użytkownika)
  * [**27. Następnie włącz uprawnienia sudoers dla nowo utworzonego użytkownika**](#27-następnie-włącz-uprawnienia-sudoers-dla-nowo-utworzonego-użytkownika)
  * [**the continue ...**]()
  
#### Arch Linux - instalacja i konfiguracja
  
<img src="https://user-images.githubusercontent.com/43359077/122649191-0dc9e200-d12d-11eb-8bf0-b28c10b837ec.png" alt="live_boot" width="1000"/>
  
###### [Do góry](#spis-treści)
#### Przed instalacją:  
##### **Ethernet** - podłącz kabel sieciowy. Na czas instalacji podepnij się do internetu najlepiej przez kabel. 
##### **Wi-Fi** - połącz się z siecią bezprzewodową za pomocą **iwctl**. Połącz się z **Wi-Fi** za pomocą terminala w Arch Linux i innych dystrybucjach.
#### 1. Konfiguracja Wi-Fi – sieci bezprzewodowe
##### Mój komputer obsługuje **Wi-Fi**, używam go bezpośrednio. Połączenie **Wi-Fi** **(iwctl)**
```yaml
root@archiso ~ # iwctl
```
```yaml
[iwd]# Device List
```
```yaml
[iwd]# station wlan0 get-networks 
```
```yaml
[iwd]# station wlan0 connect ssid 
```
```yaml
[iwd]# exit
```
###### [Do góry](#spis-treści)
-----  
  
#### 2. Połącz się z Internetem
```markdown
# ping -c 5 google.pl
```
##### **Wynik podobny do tego poniżej oznacza, że połączenie działa**
<img src="https://user-images.githubusercontent.com/43359077/122655784-76c55000-d155-11eb-91e1-b940059b5a93.png" alt="ping" width="1000"/>

###### [Do góry](#spis-treści)
-----

#### 3. Układ klawiatury
##### **By wybrać polski układ klawiatur**
```markdown
# loadkeys pl
```
```markdown
# setfont Lat2-Terminus16
```
###### **przed:**
  <img src="https://user-images.githubusercontent.com/43359077/122655751-306ff100-d155-11eb-819a-b2e6589c509b.png" alt="setfont" width="1000"/>

###### **po:**
  <img src="https://user-images.githubusercontent.com/43359077/122655760-441b5780-d155-11eb-8701-f840875c574b.png" alt="setfont" width="1000"/>

###### [Do góry](#spis-treści)
-----

#### 4. Zaktualizuj systemowy zegar
```markdown
# timedatectl set-ntp true
```
##### **By sprawdzić stan usługi, użyj** 
```markdown
# timedatectl status
```
<img src="https://user-images.githubusercontent.com/43359077/122652939-d74a9200-d141-11eb-9214-ee8d884cb948.png" alt="timedatectl" width="1000"/>

###### [Do góry](#spis-treści)
-----
  
#### 5. Partycjonuj dyski
##### W przypadku, gdy dysk twardy jest nowy, tak jak w przypadku maszyny wirtualnej lub chcesz ponownie podzielić dysk na partycje, uruchom to polecenie, aby utworzyć nową tablicę partycji.
##### **Wipefs** to polecenie czyści tablice partycji, kasuje wszystko z dysku. Potem **cfdisk** i wybierasz **gpt**. Potem lecisz już z instalacją Archa.

##### **Przygotowanie dysku:**
##### GPT (UEFI)

| Potrzebny | Partycja  | Typ partycji           | Punkt montażu | Rozmiar    | Flagi      |
|-----------|-----------|------------------------|---------------|------------|------------|
| ✔️        | /dev/sdXY | Partycja systemowa EFI | /mnt/efi      | 260-512MiB | -          |
| ❌        | /dev/sdXY | Linux swap             | -             |            | -          |
| ✔️        | /dev/sdXY | Linux                  | /mnt          |            | -          |
| ❌        | /dev/sdXY | Linux                  | /mnt/home     |            | -          |
  
##### System EFI
##### Co najmniej: 260MiB
##### Zalecane   : 512MiB
##### Przy tym kroku należy postępować ostrożnie ponieważ można przypadkiem usunąć partycje.
  
##### Na początek musimy odnaleźć dysk, na którym nasz system ma być zainstalowany.
```markdown
# fdisk -l
```
<img src="https://user-images.githubusercontent.com/43359077/122652987-07923080-d142-11eb-8fc1-dff96c619032.png" alt="fdisk" width="1000"/>

```markdown
# wipefs -a /dev/sda 
```
<img src="https://user-images.githubusercontent.com/43359077/122655841-01a64a80-d156-11eb-9893-ae1868ffffd6.png" alt="wipefs" width="1000"/>

##### **Graficzny (zalecany dla początkujących)**
##### cfdisk – szybciej, wygodniej, lepiej?
###### Ja preferuje cfdisk - prosta i przejrzysta :hearts:

```markdown
# cfdisk /dev/sda
```
##### Po uruchomieniu otrzymasz monit w ten sposób:
##### **Wybierz typ tabeli gpt**.
  
<img src="https://user-images.githubusercontent.com/43359077/122653015-390afc00-d142-11eb-90f0-87a2e3863e89.png" alt="gpt" width="1000"/>

##### Następnie musimy utworzyć odpowiednio partycje **efi** , **/** i **/home**.
##### Osobiście zalecam **minimalne** granice rozmiaru na **/** ustalić w przedziale **10 - 50GB**, oraz całą resztę dostępnej przestrzeni na **/home**.
##### Teraz zobaczysz tabelę partycji w ten sposób:
##### Zobacz dostępne wolne miejsce. Tutaj mamy 1000GB. Wybierz **NOWY** i utwórz nową partycję.
<img src="https://user-images.githubusercontent.com/43359077/122652782-e715a680-d140-11eb-9ec0-4efea38c00ed.png" alt="nowy" width="1000"/>

##### Wpisz rozmiar partycji w MB (512MiB) i naciśnij klawisz Enter
<img src="https://user-images.githubusercontent.com/43359077/122653139-0e6d7300-d143-11eb-83ea-e91632d6c3be.png" alt="efi" width="1000"/>
  
 ##### Wybierz opcję **Type** z dolnego menu i naciśnij klawisz Enter
<img src="https://user-images.githubusercontent.com/43359077/122653197-673d0b80-d143-11eb-8301-de253d8b56ed.png" alt="type" width="1000"/>

##### wybierz typ partycji EFI System, jak pokazano na poniższych zrzutach ekranu.
<img src="https://user-images.githubusercontent.com/43359077/122653199-6a37fc00-d143-11eb-89a2-00ae9b35564b.png" alt="efi" width="1000"/>

##### Wybierz **NOWY** i utwórz nową partycję. 
<img src="https://user-images.githubusercontent.com/43359077/122655988-28b14c00-d157-11eb-965b-004285d14c1f.png" alt="nowy" width="1000"/>

##### Przykład: Wybierz rozmiar **40GB**. Chcemy główną, zatem wciskamy enter.
<img src="https://user-images.githubusercontent.com/43359077/122656070-c60c8000-d157-11eb-9c36-065b3feedeea.png" alt="partycja_40GB" width="1000"/>

##### Wybierz **NOWY** i utwórz nową partycję.
<img src="https://user-images.githubusercontent.com/43359077/122656307-9e1e1c00-d159-11eb-9850-de03b5087b90.png" alt="nowy" width="1000"/>

##### Naciśnij klawisz Enter, aby zaakceptować domyślny.
<img src="https://user-images.githubusercontent.com/43359077/122656386-5f3c9600-d15a-11eb-914a-1d003566f343.png" alt="partycja_960GB" width="1000"/> 

##### Skończone. Partycja utworzona w miły i przyjemny sposób. Możemy zapisać teraz zmiany używając opcji **Write**.
<img src="https://user-images.githubusercontent.com/43359077/122656553-dde60300-d15b-11eb-95a5-3ca93294bcdc.png" alt="write" width="1000"/>

##### Wpisz **yes**, aby zatwierdzić zmiany w strukturze dysku, a następnie naciśnij klawisz Enter.
<img src="https://user-images.githubusercontent.com/43359077/122656570-0110b280-d15c-11eb-870a-51e84530fbe7.png" alt="yes" width="1000"/>

##### Przed ostatecznym zapisem system poprosi o potwierdzenie. Aby wyjść bez zapisywania zmian należy wybrać Zakończ.
##### cfdisk zapisze zmiany na wirtualnym napędzie dysków. cfdisk wyświetli następujący komunikat diagnostyczny:
##### Po zakończeniu działań programu wyjdź wybierając **Quit**.
##### Tablica partycji zostałą zmodyfikowana.
<img src="https://user-images.githubusercontent.com/43359077/122656591-492fd500-d15c-11eb-88cd-55838e22943d.png" alt="quit" width="1000"/>

##### Jak widać na dysku są 3 partycje.
```markdown
# fdisk -l
```
<img src="https://user-images.githubusercontent.com/43359077/122656614-85fbcc00-d15c-11eb-8218-8ad5f1d83c2c.png" alt="fdisk-l" width="1000"/>

###### [Do góry](#spis-treści)
-----
  
##### Jesteśmy gotowi, by przejść powoli do instalacji bazowego systemu. Nowe partycje należy sformatować za pomocą systemu plików, zanim będzie można ich używać. Możesz to zrobić za pomocą odpowiedniego polecenia mkfs.
#### 6. Formatowanie partycji UEFI with GPT
##### Dysk powinien mieć trzy partycje. Musimy je sformatować w dowolnym systemie plików Linux. Polecam użycie ext4.
##### Pierwsza partycja to partycja UEFI. Musi być sformatowany za pomocą systemu plików FAT
```markdown
# mkfs.fat -F32 -n EFI /dev/sda1
# mkfs.ext4 -L root /dev/sda2
# mkfs.ext4 -L home /dev/sda3
```
<img src="https://user-images.githubusercontent.com/43359077/122656892-0f140280-d15f-11eb-88ab-805cfc3037df.png" alt="mkfs" width="1000"/>

###### [Do góry](#spis-treści)
-----

#### 7. Zamontuj system plików
##### Teraz nadszedł czas na zamontowanie tych partycji:
```markdown
# mkdir /boot/efi
# mount /dev/sda1 /boot/efi
# mount /dev/sda2 /mnt
# mkdir /mnt/home
# mount /dev/sda3 /mnt/home
```
<img src="https://user-images.githubusercontent.com/43359077/122657025-18519f00-d160-11eb-8d35-ed2d6fb46758.png" alt="mount" width="1000"/>

##### Sprawdź punkty montażowe, czy zostały pomyślnie utworzone.
```markdown
# lsblk -f
```
<img src="https://user-images.githubusercontent.com/43359077/122657046-34554080-d160-11eb-9205-459975c3a495.png" alt="lsblk-f" width="1000"/>
  
###### [Do góry](#spis-treści)
-----
  
#### 8. Instalacja systemu podstawowego
##### Teraz rozpoczynamy proces instalacji.
##### Pobranie pakietów i instalacja systemu mieści się w jednej komendzie:
```markdown
# pacstrap -i /mnt base base-devel bash-completion linux linux-firmware linux-headers nano dhcpcd
```
##### Dodałem Nano edytor, ponieważ trzeba edytować niektóre pliki po instalacji.
 
##### Przy pytaniu, jakie pakiety zainstalować wcisnąć ENTER. Poczekaj chwilę, aż się zakończy.
<img src="https://user-images.githubusercontent.com/43359077/122657138-120ff280-d161-11eb-9f33-8f4e144821d1.png" alt="pacstrap" width="1000"/>

##### To zajmie trochę czasu, aby pobrać i zainstalować te pakiety. Jeśli pliki do pobrania zostanie przerwane, nie trzeba panikować. Możesz uruchomić powyższe polecenie jeszcze raz i wznowić pobieranie.
###### [Do góry](#spis-treści)
-----
  
#### 9. Generowanie fstab
```markdown
# genfstab -U -p /mnt >> /mnt/etc/fstab
```
##### oraz sprawdzenie czy jest poprawny.
```markdown
# genfstab -U -p /mnt /mnt/etc/fstab
```
<img src="https://user-images.githubusercontent.com/43359077/122658126-e47b7700-d169-11eb-9f61-ed8d00e0d75e.png" alt="fstab" width="1000"/>
  
###### [Do góry](#spis-treści)
-----

#### 10. Wejdź przez chroot do nowego systemu
```markdown
# arch-chroot /mnt /bin/bash
``` 
<img src="https://user-images.githubusercontent.com/43359077/120879922-24b5f380-c5c7-11eb-9f8b-b1336162493c.png" alt="arch-chroot" width="800"/>

###### [Do góry](#spis-treści)
-----

#### 11. Strefa czasowa - Ustaw czas
```markdown
# ln -sf /usr/share/zoneinfo/Europe/Warsaw /etc/localtime
# hwclock --systohc --utc
```
<img src="https://user-images.githubusercontent.com/43359077/120880081-5f6c5b80-c5c8-11eb-94de-f65bff0a30c7.png" alt="czasowa" width="800"/>

###### [Do góry](#spis-treści)
-----

#### 12. Konfiguracja języka
```markdown
# nano /etc/locale.gen
```
<img src="https://user-images.githubusercontent.com/43359077/120886743-c8b39500-c5ef-11eb-95cb-d7af41100399.png" alt="locale-gen" width="800"/>

##### Za pomocą klawiszy strzałek przewiń ekran w dół i znajdź linię.
```js
#en_US.UTF-8 

#pl_PL.UTF-8
```
##### Odkomentuj go, usuwając znak **#**
```js
en_US.UTF-8

pl_PL.UTF-8
```
zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano)
  
<img src="https://user-images.githubusercontent.com/43359077/120886633-3dd29a80-c5ef-11eb-987d-0f59fb69bc8d.png" alt="locale_gen" width="800"/>

##### Następnie musisz wygenerować ustawienia regionalne
```markdown
# locale-gen
```
  
<img src="https://user-images.githubusercontent.com/43359077/120886947-b423cc80-c5f0-11eb-9dff-9df183597f9c.png" alt="generowanie" width="800"/>
  
###### [Do góry](#spis-treści)
-----

#### 13. Plik konfiguracyjny dla ustawień regionalnych - Ustaw zmienną
  
```markdown
# nano /etc/locale.conf
```
<img src="https://user-images.githubusercontent.com/43359077/120887670-86d91d80-c5f4-11eb-9e90-89a4b4499e28.png" alt="locale.conf" width="800"/>

##### wpisać poniższy tekst:
```yaml
LANG=pl_PL.UTF-8
LANGUAGE=pl_PL.UTF-8
LC_ADDRESS=pl_PL.UTF-8
LC_COLLATE=pl_PL.UTF-8
LC_CTYPE=pl_PL.UTF-8
LC_IDENTIFICATION=pl_PL.UTF-8
LC_MONETARY=pl_PL.UTF-8
LC_MESSAGES=pl_PL.UTF-8
LC_MEASUREMENT=pl_PL.UTF-8
LC_NAME=pl_PL.UTF-8
LC_NUMERIC=pl_PL.UTF-8
LC_PAPER=pl_PL.UTF-8
LC_TELEPHONE=pl_PL.UTF-8
LC_TIME=pl_PL.UTF-8
```
zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano) 

###### [Do góry](#spis-treści)
-----

#### 14. Plik konfiguracyjny konsoli wirtualnej - Czcionka konsoli.
```markdown
# nano /etc/vconsole.conf
```
<img src="https://user-images.githubusercontent.com/43359077/120888305-dec55380-c5f7-11eb-8f19-d9479ee7fd83.png" alt="vconsole" width="800"/>

##### wpisać poniższy tekst:
```yaml
KEYMAP=pl
FONT=Lat2-Terminus16.psfu.gz
FONT_MAP=8859-2
```
zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano)
 
###### [Do góry](#spis-treści)
-----
  
#### 15. Ustaw nazwę hosta
##### Nazwa hosta to nazwa komputera. Nazwijmy go - archtest
```markdown
# nano /etc/hostname
```
<img src="https://user-images.githubusercontent.com/43359077/120888400-71fe8900-c5f8-11eb-81eb-411357044aa0.png" alt="hostname" width="800"/>

##### wpisać poniższy tekst:
```yaml
archtest
```
zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano)
  
###### [Do góry](#spis-treści)
-----
  
#### 16. Musisz również dodać tę nazwę do pliku hosts
```markdown
# nano /etc/hosts
```
<img src="https://user-images.githubusercontent.com/43359077/120892829-5a32ff00-c610-11eb-896b-fa3100be471f.png" alt="hosts" width="800"/>

##### wpisać poniższy tekst:
```js
127.0.0.1       localhost
::1             localhost
127.0.1.1       archtest.localdomain        archtest
```
 <img src="https://user-images.githubusercontent.com/43359077/120892943-e1807280-c610-11eb-8eca-13fa8144d5c1.png" alt="localhost" width="800"/>
 
zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano)
 
###### [Do góry](#spis-treści)
-----
  
#### 17. Konfiguracja sieci
##### Twój interfejs sieciowy jest wymieniony i włączony. Kabel jest podłączony lub podłączony do bezprzewodowej sieci LAN
##### Aktywuj dhcpcd
```markdown
# systemctl enable dhcpcd
```
<img src="https://user-images.githubusercontent.com/43359077/120892992-31f7d000-c611-11eb-85f6-c67202d97fb9.png" alt="dhcpcd" width="800"/>

###### [Do góry](#spis-treści)
-----  
  
#### 18. Włącz sieć
##### Najpierw zainstaluj menedżera sieci:
##### Pobranie pakietów i instalacja systemu mieści się w jednej komendzie:
```markdown
# pacman -S networkmanager 
```
##### Konfiguracja sieci
```markdown
# pacman -S iw iwd dialog net-tools wireless_tools wpa_supplicant
```
<img src="https://user-images.githubusercontent.com/43359077/120896952-1944e580-c624-11eb-8ee7-784f76a5c771.png" alt="network" width="800"/>

##### Aktywuj usługi do następnego ponownego uruchomienia
 ```markdown 
# systemctl enable NetworkManager
```
<img src="https://user-images.githubusercontent.com/43359077/120894858-d3375400-c61a-11eb-8fd7-3f03db7c1516.png" alt="enable_networkmanager" width="800"/>

###### [Do góry](#spis-treści)
-----  
  
#### 19. Tworzenie ramdisc
```markdown
# mkinitcpio -P linux
```
<img src="https://user-images.githubusercontent.com/43359077/120895213-442b3b80-c61c-11eb-808d-300e6d853eb6.png" alt="mkinitcpio" width="800"/>

###### [Do góry](#spis-treści)
-----  
  
#### 20. Hasło użytkownika root
```markdown
# passwd
```
##### Po wciśnięciu ENTER należy dwa razy podać hasło użytkownika root
  
<img src="https://user-images.githubusercontent.com/43359077/120895893-522e8b80-c61f-11eb-9b1b-c9e529b607ec.png" alt="passwd" width="800"/>

###### [Do góry](#spis-treści)
-----  
  
#### 21. Jeśli posiadasz procesor Intela, zainstaluj pakiet intel-ucode.
##### Procesory Intela i Amd potrzebują dodatkowo mikrokodów które będą wczytywane przy bootowaniu systemu.
##### Mikrokod Intela to mikrokod działający w procesorach:
```markdown
# pacman -S intel-ucode
```
<img src="https://user-images.githubusercontent.com/43359077/120896057-1516c900-c620-11eb-94bb-22a6afd58b0b.png" alt="intel" width="800"/>

##### Mikrokod Amd to mikrokod działający w procesorach:
```markdown
# pacman -S amd-ucode
```     
<img src="https://user-images.githubusercontent.com/43359077/120896095-42fc0d80-c620-11eb-949b-dda7a81e6353.png" alt="amd" width="800"/> 

###### [Do góry](#spis-treści)  
-----  
  
#### 22. BIOS GRUB
##### Zainstaluj GRUB
```markdown
# pacman -S grub
# grub-install --target=i386-pc --recheck /dev/sda 
# grub-mkconfig -o /boot/grub/grub.cfg
```
<img src="https://user-images.githubusercontent.com/43359077/120898730-6af16e00-c62c-11eb-8ca1-fe472c493d72.png" alt="grub" width="800"/> 

###### [Do góry](#spis-treści)  
-----  
  
#### 23. Teraz wiele osób ma dyski SSD, które obsługują TRIM. Dla bezpiecznej, cotygodniowej usługi TRIM na dyskach SSD i wszystkich innych urządzeniach, które umożliwiają obsługę TRIM:
```markdown
# systemctl enable fstrim.timer
```
<img src="https://user-images.githubusercontent.com/43359077/120900751-d5a7a700-c636-11eb-828b-12d854702c1b.png" alt="fstrim" width="800"/> 
 
###### [Do góry](#spis-treści)
-----  
  
 #### 24. Wyjście z chroot
```markdown
# exit
```
##### Odmontowanie partycji i restart systemu
```markdown
# umount -Rv /mnt
# reboot
```
##### Jeśli wszystko zrobiłeś poprawnie, po ponownym uruchomieniu zobaczysz ekran powitalny GRUB z zainstalowanym Arch Linux.
<img src="https://user-images.githubusercontent.com/43359077/120901140-58316600-c639-11eb-9d9f-ea33b0c63cc6.png" alt="grub" width="800"/> 

###### [Do góry](#spis-treści)  
-----  
  
#### 25. Logowanie się do systemu
##### Po ponownym uruchomieniu systemu należy się zalogować wpisując login
```markdown
archtest login: root
```
<img src="https://user-images.githubusercontent.com/43359077/120901471-654f5480-c63b-11eb-806d-743359679deb.png" alt="grub" width="800"/> 

##### Aby kontynuować, zaloguj się jako użytkownik root z wcześniej ustawionym hasłem.

###### [Do góry](#spis-treści)  
-----
  
#### 26. Dodaj użytkownika
##### Zamiast tego wpisz swoje własne **tester**
```markdown
# useradd -m tester
```
##### Utwórz również hasło dla nowego użytkownika
```markdown
# passwd tester
```
##### Po wciśnięciu ENTER należy dwa razy podać hasło nazwa_użytkownika 
<img src="https://user-images.githubusercontent.com/43359077/120901968-00e1c480-c63e-11eb-9910-20065fb4b193.png" alt="uzytkownik" width="800"/>
 
###### [Do góry](#spis-treści)  
----  
  
#### 27. Następnie włącz uprawnienia sudoers dla nowo utworzonego użytkownika
##### Najprostsze podstawowe ustawienie można przeprowadzić wydając z konta "root" polecenie:
```markdown
# nano /etc/sudoers
```
##### Za pomocą klawiszy strzałek przewiń ekran w dół i znajdź linię.
```yaml
root ALL=(ALL) ALL
```
##### gdzie "tester ALL=(ALL) ALL" to nazwa zwykłego użytkownika. 
##### wpisać poniższy tekst:
```yaml
tester ALL=(ALL) ALL
```
  
**przed**
  
<img src="https://user-images.githubusercontent.com/43359077/120902340-266fcd80-c640-11eb-8777-9d5ddae36df2.png" alt="root1" width="800"/>

  
  
**po**
  
<img src="https://user-images.githubusercontent.com/43359077/120902346-32f42600-c640-11eb-80bc-6b7862fff742.png" alt="root2" width="800"/>

###### [Do góry](#spis-treści)  
-----
-----
-----
 
   więc proszę o cierpliwość
  
  System okien X, sterowniki Xorg, audio, sterowniki karty graficzne
  
  Środowiska graficzne
  
  niektóre kluczowe aplikacje
  
-----
-----
-----
  
  
  
  



