# Praktikum  aruanne - Haakimine

Esitan 7. operastioonisüsteemide kursuse praktikumi ülesanded. Praktikumi käigus jälgisin ette antud juhiseid, ühendasin võrgukettaid linuxis ja windowsis ning ühendasin 4TB kettast samade süsteemidega.

## Ülesanne 1. Miks andmekandjad vajavad lähtestamist?

1. Andmete Kustutamine ja Turvalisus: Lähtestamine võimaldab kustutada kõik andmed, vabastades ruumi ja tagades, et tundlikud andmed ei satuks valedesse kätesse.
2. Vigade ja Ühilduvusprobleemide Lahendamine: Lähtestamine aitab parandada vigu ja rikutud faile ning tagada andmekandja ühilduvuse uute seadmete või operatsioonisüsteemidega.
3. Jõudluse Parandamine ja Pahavara Eemaldamine: Lähtestamine võib taastada andmekandja algse jõudluse ja eemaldada viirused või pahavara.


## Ülesanne 2. Millised on GPT kasutamise eelised võrreldes MBRiga?

1. Suurem Partitsioonide ja Kettamahtude Tugi: GPT võimaldab luua kuni 128 partitsiooni ja toetab kettaid, mis on suuremad kui 2 TB, erinevalt MBR-ist.
2. Andmete Terviklikkus ja Varukoopiad: GPT salvestab partitsioonitabeli mitmes kohas, pakkudes varukoopiaid, mis aitavad andmete taastamisel.
3. UEFI Tugi ja Tulevikukindlus: GPT on vajalik UEFI püsivara kasutamiseks, pakkudes paremat ühilduvust ja paindlikkust kaasaegsete süsteemidega.


## Ülesanne 3. Link praktikumi aruandesse tõestuseks, et olete ülesande TÜ võrguketta haakimine Windowsis edukalt lahendanud.
https://kodu.ut.ee/~kasparsanin/opsys/hdd.png

## Ülesanne 4. Käsu ls -la /mnt/ut/public_html/opsys/ väljundi pilt.
<img width="720" alt="praktikum7.4" src="https://github.com/user-attachments/assets/43811694-722d-477c-85f0-8be4e9820965">

## Ülesanne 5. Mida mõjutasid mount-käsu parameetrid -o ro ja -t auto?

'ro': "read-only". Kui see antud, monteeritakse seade nii, et sealt saab ainult lugeda andmeid. \
'-o': valikud (Options).

'auto': mount-käsk proovib automaatselt tuvastada ketta või partitsiooni failisüsteemi tüübi. \
'-t': on parameeter, mis võimaldab määrata failisüsteemi tüübi.

## Ülesanne 6. Leidke mount-käsu väljundist üles, mis väärtusega asendas Ubuntu auto-parameetri.

'auto' asendatakse 'fuseblk -ga'

## Ülesanne 7. Pilt /etc/fstab-faili sisust, et 4 TB ketas haagitaks Ubuntu käivitamisel automaatselt kausta /mnt/bigdata.
<img width="720" alt="praktikum7.7" src="https://github.com/user-attachments/assets/2c57415a-efbf-4d66-921a-ab321c8ff110">


