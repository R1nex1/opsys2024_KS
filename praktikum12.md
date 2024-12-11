# Praktikum 12 aruanne - Skriptimine linuxis

Esitan 12. operastioonisüsteemide kursuse praktikumi ülesanded. Praktikumi käigus jälgisin ette antud juhiseid ja koostasin skripte linuxis.

## Ülesanne 3
```
#!/bin/sh -x
echo "Sisesta oma nimi:"
read nimi

echo "Sisesta oma eriala:"
read eriala

echo "Sisesta on matriklinumber:"
read matriklinumber

echo "Nimi: $nimi õpib erialal $eriala ja matriklinumber on $matriklinumber"
```
<img width="720" alt="praktikum12.3" src="https://github.com/user-attachments/assets/670b92c4-6edc-47ff-b0b7-6dad371bbac4">

## Ülesanne 4
```
#!/bin/bash

echo "Faililaiend, mis asendatakse:"
read vana_laiend

echo "Faililaiend, millega asendatakse:"
read uus_laiend

for file in *.$vana_laiend;
do
    if [ -f "$file" ]; then
        mv "$file" "${file%.$vana_laiend}.$uus_laiend"
    fi
done
```
<img width="720" alt="praktikum12.4" src="https://github.com/user-attachments/assets/7da98a63-3202-42c3-aa92-8b734c30815f">

## Ülesanne 5
```
#!/bin/bash
IFS=$'\n'

echo "Sisesta protsessi nimi:"
read nimi

pid=$(ps -A | grep "$nimi" | tr -s ' ' | cut -d ' ' -f2)

echo "Protsessi-ID on: $pid"
echo "Protsessi nimi on: $nimi"
```
<img width="720" alt="praktikum12.5" src="https://github.com/user-attachments/assets/9b7722d8-0e31-4349-8a49-0641c267db67">

## Ülesanne 6
```
#!/bin/bash

astenda() {
    num=9
    aste=5
    tulem=1

    for ((i=0; i<aste; i++));
        do
            tulem=$((tulem * num))
        done

    echo $tulem
}

vastus=$(astenda)
echo "9^5 = $vastus"
```
<img width="720" alt="praktikum12.6" src="https://github.com/user-attachments/assets/a6baa674-95f4-4f71-a795-8c080fc99ceb">

## Ülesanne 7
<img width="1080" alt="praktikum12.7" src="https://github.com/user-attachments/assets/d033265f-d891-4fc4-994f-389ae7021cbf">

