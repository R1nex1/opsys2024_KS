# Praktikum 6 aruanne - Protsessid ja signaalid

Esitan 6. operastioonisüsteemide kursuse praktikumi ülesanded. Praktikumi käigus jälgisin ette antud juhiseid ning käivtasin protsesse erinevat moodi linuxis ning väljastasin bashi ainult kindlat infot, mida oli vaja.

## Ülesanne 1
<img width="720" alt="praktikum6.1" src="https://github.com/user-attachments/assets/aaacd6f7-1b57-4237-a9d5-45cdf7b1cbe5">

## Ülesanne 2
<img width="720" alt="praktikum6.2" src="https://github.com/user-attachments/assets/b074e85d-9a40-4d1d-b56a-c3a06fece8e5">

## Ülesanne 3

Käsujada: ps -axu | grep daemon | tr -s ' ' | cut -d' ' -f11- | sort

<img width="720" alt="praktikum6.3" src="https://github.com/user-attachments/assets/b8179d56-1c94-45e4-8e78-a905d699586d">

## Ülesanne 4

Käsujada: ip a | grep 'inet ' | grep -v '127.0.0.1' | awk '{print $2}' | cut -d/ -f1

Käsujada faili salvestusega: ip a | grep 'inet ' | grep -v '127.0.0.1' | awk '{print $2}' | cut -d/ -f1 > ipaddress.txt

<img width="720" alt="praktikum6.4" src="https://github.com/user-attachments/assets/8f06c4ed-2d70-4460-909a-da45303e9e89">

