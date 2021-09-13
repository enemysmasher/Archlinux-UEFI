<div align="center">
  
<img src="https://user-images.githubusercontent.com/43359077/124366285-e0ae2100-dc4e-11eb-89dc-affbe96b7945.png" alt="logo" width="1000"/>

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
  * [**6. Formatowanie partycji UEFI z GPT**](#6-formatowanie-partycji-uefi-z-gpt)
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
  * [**21. Mikrokodu**](#21-jeśli-posiadasz-procesor-intela-zainstaluj-pakiet-intel-ucode)
  * [**22. UEFI GRUB**](#22-uefi-grub)
  * [**23. TRIM**](#23-teraz-wiele-osób-ma-dyski-ssd-które-obsługują-trim-dla-bezpiecznej-cotygodniowej-usługi-trim-na-dyskach-ssd-i-wszystkich-innych-urządzeniach-które-umożliwiają-obsługę-trim)
  * [**24. Wyjście z chroot**](#24-wyjście-z-chroot)
  * [**25. Logowanie się do systemu**](#25-logowanie-się-do-systemu)
  * [**26. Sprawdź, czy internet wifi**](#26-sprawdź-czy-internet-wifi)
  * [**27. Dodaj użytkownika**](#27-dodaj-użytkownika)
  * [**28. SUDO - nadawanie uprawnień użytkownikom Linux**](#28-nast%C4%99pnie-w%C5%82%C4%85cz-uprawnienia-sudoers-dla-nowo-utworzonego-u%C5%BCytkownika)
  * [**29. Standardowo plik konfiguracyjny Pacmana**](#29-pacmanconf---plik-konfiguracyjny-menedżera-pakietów-pacman)
  * [**30. Xorg**](#30-instalacja-xorg-a)
  * [**31. Sterownik graficzny**](#31-wybieramy-dodatkowo-sterownik-poniżej-dla-swojej-karty-graficznej)
  * [**32. Wybór środowiska pulpitu**](#32-środowisko-pulpitu)
  * [**33. Dźwięk**](#33-dźwięk)
  
  
  * [**the continue ...**](https://i.imgur.com/x08cazS.gif)
  
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
##### **cfdisk -z to rozpoczęcie z wyzerowaną tablicą partycji. Wybierasz dos. Potem lecisz już z instalacją Archa.

##### **Przygotowanie dysku:**
##### GPT (UEFI)

| Potrzebny | Partycja  | Typ partycji           | Punkt montażu | Rozmiar    | Flagi      |
|-----------|-----------|------------------------|---------------|------------|------------|
| ✔️        | /dev/sdXY | Partycja systemowa EFI | /mnt/efi      | 260-512MiB | -          |
| ❌        | /dev/sdXY | Linux swap             | -             |            | -          |
| ✔️        | /dev/sdXY | Linux                  | /mnt          |            | -          |
| ❌        | /dev/sdXY | Linux                  | /mnt/home     |            | -      
##### System EFI
##### Co najmniej: 260MiB
##### Zalecane   : 512MiB
##### Przy tym kroku należy postępować ostrożnie ponieważ można przypadkiem usunąć partycje.
  
##### Na początek musimy odnaleźć dysk, na którym nasz system ma być zainstalowany.
```markdown
# fdisk -l
```
<img src="https://user-images.githubusercontent.com/43359077/122652987-07923080-d142-11eb-8fc1-dff96c619032.png" alt="fdisk" width="1000"/>

##### **Graficzny (zalecany dla początkujących)**
##### cfdisk – szybciej, wygodniej, lepiej?
###### Ja preferuje cfdisk - prosta i przejrzysta :hearts:

```markdown
# cfdisk -z /dev/sda
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
#### 6. Formatowanie partycji UEFI z GPT
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
# mount /dev/sda2 /mnt
# mkdir /mnt/home
# mount /dev/sda3 /mnt/home
```
<img src="https://user-images.githubusercontent.com/43359077/122669529-21715900-d1be-11eb-9a23-47219db54b87.png" alt="mount" width="1000"/>

##### Sprawdź punkty montażowe, czy zostały pomyślnie utworzone.
```markdown
# lsblk -f
```
<img src="https://user-images.githubusercontent.com/43359077/122657046-34554080-d160-11eb-9205-459975c3a495.png" alt="lsblk-f" width="1000"/>
  
###### [Do góry](#spis-treści)
-----
#### 8. Instalacja systemu podstawowego
##### Teraz rozpoczynamy proces instalacji.
##### Instalacja nowego jądra linux, linux-hardened, linux-lts, linux-zen ...
##### Pobranie pakietów i instalacja systemu mieści się w jednej komendzie:
#### Masz do wyboru cztery sposoby
##### Stable Linux Kernel
```markdown
# pacstrap -i /mnt base base-devel bash-completion linux linux-headers linux-firmware nano dhcpcd
```
##### Hardened Kernel
```markdown
# pacstrap -i /mnt base base-devel bash-completion linux-hardened linux-hardened-headers linux-firmware nano dhcpcd
```
##### Longterm (LTS) Kernel
```markdown
# pacstrap -i /mnt base base-devel bash-completion linux-lts linux-lts-headers linux-firmware nano dhcpcd
```
##### Zen Kernel
```markdown
# pacstrap -i /mnt base base-devel bash-completion linux-zen linux-zen-headers linux-firmware nano dhcpcd
```
##### Dodałem Nano edytor, ponieważ trzeba edytować niektóre pliki po instalacji.
##### Przy pytaniu, jakie pakiety zainstalować wcisnąć ENTER. Poczekaj chwilę, aż się zakończy.
<img src="https://user-images.githubusercontent.com/43359077/122657333-eee64280-d162-11eb-87c6-640034a5877f.png" alt="pacstrap" width="800"/>

##### To zajmie trochę czasu, aby pobrać i zainstalować te pakiety. Jeśli pliki do pobrania zostanie przerwane, nie trzeba panikować. Możesz uruchomić powyższe polecenie jeszcze raz i wznowić pobieranie.
###### [Do góry](#spis-treści)
----- 
#### 9. Generowanie fstab
```markdown
# genfstab -U /mnt >> /mnt/etc/fstab
```
##### oraz sprawdzenie czy jest poprawny.
```markdown
# cat /mnt/etc/fstab  
```
<img src="https://user-images.githubusercontent.com/43359077/122658126-e47b7700-d169-11eb-9f61-ed8d00e0d75e.png" alt="fstab" width="1000"/>
  
###### [Do góry](#spis-treści)
-----
#### 10. Wejdź przez chroot do nowego systemu
```markdown
# arch-chroot /mnt /bin/bash
``` 
<img src="https://user-images.githubusercontent.com/43359077/122669619-875de080-d1be-11eb-9097-68c633955834.png" alt="arch-chroot" width="1000"/>

###### [Do góry](#spis-treści)
-----
#### 11. Strefa czasowa - Ustaw czas
```markdown
# ln -sf /usr/share/zoneinfo/Europe/Warsaw /etc/localtime
# hwclock --systohc --utc
```
<img src="https://user-images.githubusercontent.com/43359077/122670378-1d473a80-d1c2-11eb-9937-5d6592e5884a.png" alt="czasowa" width="1000"/>
  
###### [Do góry](#spis-treści)
-----
#### 12. Konfiguracja języka
```markdown
# nano /etc/locale.gen
```
<img src="https://user-images.githubusercontent.com/43359077/122669712-e7ed1d80-d1be-11eb-8c2d-d6927550843d.png" alt="locale-gen" width="1000"/>

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
  
<img src="https://user-images.githubusercontent.com/43359077/122669731-fc311a80-d1be-11eb-9d5c-a1e7f0561f5a.png" alt="locale_gen" width="1000"/>

##### Następnie musisz wygenerować ustawienia regionalne
```markdown
# locale-gen
```
<img src="https://user-images.githubusercontent.com/43359077/122670172-e3296900-d1c0-11eb-872b-067a2b9949fa.png" alt="generowanie" width="1000"/>

###### [Do góry](#spis-treści)
-----
#### 13. Plik konfiguracyjny dla ustawień regionalnych - Ustaw zmienną
  
```markdown
# nano /etc/locale.conf
```
<img src="https://user-images.githubusercontent.com/43359077/122670207-0f44ea00-d1c1-11eb-9fb3-e9350d8c2c9a.png" alt="locale.conf" width="1000"/>

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
<img src="https://user-images.githubusercontent.com/43359077/122670237-40251f00-d1c1-11eb-9ee5-0b01dc4bb174.png" alt="vconsole" width="1000"/>

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
<img src="https://user-images.githubusercontent.com/43359077/122670475-93e43800-d1c2-11eb-9a22-f2b99416da08.png" alt="hostname" width="1000"/>

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
<img src="https://user-images.githubusercontent.com/43359077/122670494-b1b19d00-d1c2-11eb-8d39-c4ef20e53b1d.png" alt="hosts" width="1000"/>

##### wpisać poniższy tekst:
```js
127.0.0.1       localhost
::1             localhost
127.0.1.1       archtest.localdomain        archtest
```
 <img src="https://user-images.githubusercontent.com/43359077/122670516-c9892100-d1c2-11eb-886b-4dc6d4501f73.png" alt="localhost" width="1000"/>

zapisać **ctrl+O** (zapisuje), **ENTER** później **ctrl+X** (zamyka nano)
###### [Do góry](#spis-treści)
----- 
#### 17. Konfiguracja sieci
##### Twój interfejs sieciowy jest wymieniony i włączony. Kabel jest podłączony lub podłączony do bezprzewodowej sieci LAN
##### Aktywuj dhcpcd
```markdown
# systemctl enable dhcpcd
```
<img src="https://user-images.githubusercontent.com/43359077/122670542-e4f42c00-d1c2-11eb-85d0-e63c63481cbf.png" alt="dhcpcd" width="1000"/>

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
<img src="https://user-images.githubusercontent.com/43359077/122670604-343a5c80-d1c3-11eb-9ab1-54c5aed03e7d.png" alt="network" width="1000"/>

##### Aktywuj usługi do następnego ponownego uruchomienia
 ```markdown 
# systemctl enable NetworkManager
```
<img src="https://user-images.githubusercontent.com/43359077/122670681-80859c80-d1c3-11eb-88af-1d25de48ac21.png" alt="enable_networkmanager" width="1000"/>
 
###### [Do góry](#spis-treści)
-----   
#### 19. Tworzenie ramdisc
```markdown
# mkinitcpio -P linux
```
<img src="https://user-images.githubusercontent.com/43359077/122670701-9c893e00-d1c3-11eb-9b96-736019157d98.png" alt="mkinitcpio" width="1000"/>

###### [Do góry](#spis-treści)
-----    
#### 20. Hasło użytkownika root
```markdown
# passwd
```
##### Po wciśnięciu ENTER należy dwa razy podać hasło użytkownika root
  
<img src="https://user-images.githubusercontent.com/43359077/122670755-e3773380-d1c3-11eb-94be-3069b184fb63.png" alt="passwd" width="1000"/>

###### [Do góry](#spis-treści)
-----    
#### 21. Jeśli posiadasz procesor Intela, zainstaluj pakiet intel-ucode.
##### Procesory Intela i Amd potrzebują dodatkowo mikrokodów które będą wczytywane przy bootowaniu systemu.
##### Mikrokod Intela to mikrokod działający w procesorach:
```markdown
# pacman -S intel-ucode
```
<img src="https://user-images.githubusercontent.com/43359077/122670812-25a07500-d1c4-11eb-94b8-383fd977c7d5.png" alt="intel" width="1000"/>

##### Mikrokod Amd to mikrokod działający w procesorach:
```markdown
# pacman -S amd-ucode
```     
<img src="https://user-images.githubusercontent.com/43359077/122670856-597b9a80-d1c4-11eb-8609-1a8522b62e16.png" alt="amd" width="1000"/>

###### [Do góry](#spis-treści)  
-----  
#### 22. UEFI GRUB
##### Zainstaluj GRUB efibootmgr. Katalog nie jest domyślnie dostępny, należy najpierw utworzyć go z mkdir i zamontuj partycję
```markdown
# pacman -S grub efibootmgr
# mkdir /boot/efi
# mount /dev/sda1 /boot/efi
# grub-install --target=x86_64-efi --bootloader-id=grub_uefi --efi-directory=/boot/efi --removable --recheck
# grub-mkconfig -o /boot/grub/grub.cfg
```
<img src="https://user-images.githubusercontent.com/43359077/122671227-e96e1400-d1c5-11eb-865a-a4e7d2eb6d30.png" alt="grub" width="1000"/>

###### [Do góry](#spis-treści)  
-----    
#### 23. Teraz wiele osób ma dyski SSD, które obsługują TRIM. Dla bezpiecznej, cotygodniowej usługi TRIM na dyskach SSD i wszystkich innych urządzeniach, które umożliwiają obsługę TRIM:
```markdown
# systemctl enable fstrim.timer
```
<img src="https://user-images.githubusercontent.com/43359077/122671309-44077000-d1c6-11eb-968e-0bb108aae757.png" alt="fstrim" width="1000"/>

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
<img src="https://user-images.githubusercontent.com/43359077/122674813-06f7a980-d1d7-11eb-9b8b-40baec5b7573.png" alt="grub" width="1000"/> 

###### [Do góry](#spis-treści)  
-----   
#### 25. Logowanie się do systemu
##### Po ponownym uruchomieniu systemu należy się zalogować wpisując login
```markdown
archtest login: root
```
##### Aby kontynuować, zaloguj się jako użytkownik root z wcześniej ustawionym hasłem.
<img src="https://user-images.githubusercontent.com/43359077/122674922-7cfc1080-d1d7-11eb-8708-9c24b7c08a43.png" alt="grub" width="1000"/> 

###### [Do góry](#spis-treści) 
-----
#### 26. Sprawdź, czy internet wifi należy połączyć się z:
```markdown
# ip a
```
Jeśli w sieci Wi-Fi 
```markdown
# nmtui
```

<img src="https://user-images.githubusercontent.com/43359077/122683344-d88dc480-d1fe-11eb-985f-7af41ad8d1de.png" alt="nmtui" width="1000"/> 

###### [Do góry](#spis-treści)  
----- 
#### 27. Dodaj użytkownika
##### Zamiast tego wpisz swoje własne **tester**
```markdown
# useradd -m tester
```
##### Utwórz również hasło dla nowego użytkownika
```markdown
# passwd tester
```
##### Po wciśnięciu ENTER należy dwa razy podać hasło nazwa_użytkownika 
<img src="https://user-images.githubusercontent.com/43359077/122675031-eed45a00-d1d7-11eb-9c36-1f6b069bd7a4.png" alt="uzytkownik" width="1000"/>

###### [Do góry](#spis-treści)  
----   
#### 28. Następnie włącz uprawnienia sudoers dla nowo utworzonego użytkownika
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
  
<img src="https://user-images.githubusercontent.com/43359077/122675482-ec72ff80-d1d9-11eb-8101-158fbc74c462.png" alt="root1" width="1000"/>

**po**
  
<img src="https://user-images.githubusercontent.com/43359077/122675493-f432a400-d1d9-11eb-87d0-81c8b2a1f4d0.png" alt="root2" width="1000"/>
  
###### [Do góry](#spis-treści)  
-----
#### 29. Pacman.conf - plik konfiguracyjny menedżera pakietów pacman
##### Włączenie repozytorium z pakietami 32 bit i 64 bit w 64 bitowym systemie Arch Linux (np. wine , steam itp.)
```markdown
# # nano /etc/pacman.conf
```
##### Aby włączyć repozytorium multilib, odkomentuj, usuwając znak **#**
##### Za pomocą klawiszy strzałek przewiń ekran w dół i znajdź linię
###### przed
```yaml
#[multilib]
#Include = /etc/pacman.d/mirrorlist
```
<img src="https://user-images.githubusercontent.com/43359077/122675591-66a38400-d1da-11eb-9309-95cf78d7778f.png" alt="multilib1" width="1000"/>
 
###### po  
```yaml
[multilib]
Include = /etc/pacman.d/mirrorlist
```  
<img src="https://user-images.githubusercontent.com/43359077/122675596-6c996500-d1da-11eb-849c-c9c2a5b88d1a.png" alt="multilib2" width="1000"/>

zapisać ctrl+O -(zapisuje), ENTER później ctrl+X (zamyka nano)

##### Następnie zaktualizuj system i zainstaluj żądane pakiety multilib
```markdown
# pacman -Syu
```
<img src="https://user-images.githubusercontent.com/43359077/122676398-3827a800-d1de-11eb-8ed0-851edb4a9562.png" alt="pacmansyu" width="1000"/>

###### [Do góry](#spis-treści)
-----  
#### 30. Instalacja Xorg-a
##### Są to niektóre pakiety potrzebne do prawidłowego działania niektórych urządzeń wejściowych. Instalacja ich nie szkodzi, nawet jeśli ich nie potrzebujesz
##### Xorg to serwer wyświetlania, którego użyjemy
```markdown
# pacman -S xorg xorg-xinit xterm
```
###### [Do góry](#spis-treści)
-----
#### 31. Wybieramy dodatkowo sterownik poniżej dla swojej karty graficznej
##### Zainstaluj to tylko wtedy, gdy używasz graficznego AMD lub Intel lub chcesz użyć sterownika NVIDIA typu otwarte żródłowe (Nouveau, nie opracowany przez NVIDIA)

##### Sterownik graficzny
##### Mesa
###### Jest to przydatne dla wszystkich procesorów graficznych
```markdown
# pacman -S mesa lib32-mesa
```
  
<details>
<summary>INTEL</summary>
  
```markdown
# pacman -S xf86-video-intel 
```
###### jest sterownikiem Intela typu otwarte żródłowe (prawdopodobnie chcesz to pominąć i użyje sterownika modesetting. Więcej informacji można znaleźć na stronie wiki)
</details>
  
<details>
<summary>AMD</summary>
  
```markdown
# pacman -S xf86-video-amdgpu 
```
###### jest dla nowszych procesorów graficznych AMD
##### AMD-narzędzia
  
```markdown
# pacman -S libva-mesa-driver lib32-libva-mesa-driver mesa-vdpau lib32-mesa-vdpau libva-vdpau-driver lib32-libva-vdpau-driver amdvlk lib32-amdvlk
```
###### Zainstaluj te pakiety tylko wtedy, gdy używasz graficznego AMD
</details>
  
<details>
<summary>NOUVEAU</summary>
  
```markdown
# pacman -S xf86-video-nouveau 
```
###### to sterownik NVIDIA typu otwarte żródłowe
</details>
  
<details>
<summary>ATI</summary>
  
```markdown
# pacman -S xf86-video-ati
```
###### jest dla starszych procesorów graficznych AMD
</details>
  
<details>
<summary>VMWARE</summary>
  
```markdown
# pacman -S xf86-video-vmware
```
###### dla VirtualBox, VMWare, QEMU
</details>
  
<details>
<summary>FBDEV</summary>
  
```markdown
# pacman -S xf86-video-fbdev
```
###### dla Hyper-V
</details>
  
<details>
<summary>NVIDIA</summary>
  
```markdown
# pacman -S nvidia nvidia-lts nvidia-utils lib32-nvidia-utils libvdpau lib32-libvdpau
```
###### Zainstaluj te pakiety tylko wtedy, gdy używasz graficznego NVIDIA
</details>

##### Jeśli nie wiesz, możesz zainstalować wszystko, ale może się zdarzyć, że wewnętrzna karta graficzna jest używana, jeśli zainstalujesz dla niej sterownik
###### [Do góry](#spis-treści)
-----
#### 32. Środowisko pulpitu
##### Musisz wybrać środowisko graficzne
##### Instrukcje dotyczące plazmy KDE są testowane przeze mnie, ponieważ go używam.
##### Aby zainstalować środowisko graficzne KDE wydajemy polecenie:

<details>
<summary>Kde plasma</summary>

```markdown
# pacman -S plasma-desktop sddm
```
Menedżer wyświetlania
```markdown
# systemctl enable sddm
```
```markdown
# echo "exec startplasma-x11" > ~/.xinitrc
```
##### Uruchom GUI
##### Aby sprawdzić, czy środowisko graficzne działa, uruchom:
  
```markdown
# startx
```
##### Jeśli chcesz zainstalować dodatki:
```markdown
# pacman -S plasma-pa plasma-nm 
```
</details>
 
<details>
<summary>Gnome</summary>

```markdown
# pacman -S gnome gnome-extra gdm
``` 
Menedżer wyświetlania
```markdown
# systemctl enable gdm
```
```markdown
# echo "exec gnome-session" > ~/.xinitrc
```
##### Uruchom GUI
##### Aby sprawdzić, czy środowisko graficzne działa, uruchom:
  
```markdown
# startx
```
</details>
  
<details>
<summary>Mate</summary>

```markdown
# pacman -S mate lightdm lightdm-gtk-greeter
``` 
Menedżer wyświetlania 
```markdown
# systemctl enable lightdm 
```
```markdown
# echo "exec mate-session" > ~/.xinitrc
```
##### Uruchom GUI
##### Aby sprawdzić, czy środowisko graficzne działa, uruchom:
  
```markdown
# startx
```
</details>
  
<details>
<summary>Xfce</summary>

```markdown
# pacman -S xfce4 xfce4-goodies lightdm lightdm-gtk-greeter 
``` 
Menedżer wyświetlania 
```markdown
# systemctl enable lightdm
```
```markdown
# echo "exec xfce4-session" > ~/.xinitrc
```
##### Uruchom GUI
##### Aby sprawdzić, czy środowisko graficzne działa, uruchom:
  
```markdown
# startx
```
</details>

<details>
<summary>Cinnamon</summary>

```markdown
# pacman -S pacman -S cinnamon cinnamon-translations lightdm lightdm-gtk-greeter
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable lightdm
```
```markdown
# echo "cinnamon-session" > ~/.xinitrc
```
##### Uruchom GUI
##### Aby sprawdzić, czy środowisko graficzne działa, uruchom:
  
```markdown
# startx
```
</details>
  
<details>
<summary>Enlightenment</summary>

```markdown
# pacman -S pacman -S enlightenment efl lightdm lightdm-gtk-greeter
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable lightdm
```
```markdown
# echo "enlightenment_start" > ~/.xinitrc
```
##### Uruchom GUI
##### Aby sprawdzić, czy środowisko graficzne działa, uruchom:
  
```markdown
# startx
```
</details>
  
<details>
<summary>Deepin</summary>

```markdown
# pacman -S pacman -S 
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable 
```
```markdown
# echo "" > ~/.xinitrc
```
##### Uruchom GUI
##### Aby sprawdzić, czy środowisko graficzne działa, uruchom:
```markdown
# startx
```
</details>
  
<details>
<summary>Openbox</summary>

```markdown
# pacman -S pacman -S openbox lightdm lightdm-gtk-greeter
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable lightdm
```
```markdown
# echo "exec openbox-session" > ~/.xinitrc
```
##### Uruchom GUI
##### Aby sprawdzić, czy środowisko graficzne działa, uruchom:
```markdown
# startx
```
</details>
  
<details>
<summary>szczegóły</summary>

```markdown
# pacman -S pacman -S 
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable 
```
</details>
  
<details>
<summary>szczegóły</summary>

```markdown
# pacman -S pacman -S 
``` 
Menedżer wyświetlania  
```markdown
# systemctl enable 
```
</details>

###### [Do góry](#spis-treści)
-----
#### 33. Dźwięk
##### Zainstaluj dźwięk dla KDE Plasma
```markdown
# pacman -S pavucontrol-qt
```
##### Zainstaluj dźwięk dla inne środowisko graficzne
```markdown
# pacman -S pavucontrol
```
##### Niektóre moduły PulseAudio nie są zawarte w pakiecie głównym i w razie potrzeby muszą być zainstalowane oddzielnie:

<details>
<summary>pulseaudio-alsa</summary>
  
```markdown
# pacman -S pulseaudio-alsa
```
###### dla PulseAudio do zarządzania ALSA
</details>
  
<details>
<summary>pulseaudio-bluetooth</summary>
  
```markdown
# pacman -S pulseaudio-bluetooth
```
###### dla wsparcia bluetooth (Bluez)
</details>
  
<details>
<summary>pulseaudio-equalizer</summary>
  
```markdown
# pacman -S pulseaudio-equalizer
```
###### do korektora graficzny (qpaeq)
</details>
 
<details>
<summary>alsa-plugins</summary>
  
```markdown
# pacman -S alsa-plugins
```
###### dodatkowe wtyczki alsa
</details>


  
  
  
###### [Do góry](#spis-treści)

