# Praktikum 13 aruanne - Skriptimine Windowsis

Esitan 13. operastioonisüsteemide kursuse praktikumi ülesanded. Praktikumi käigus jälgisin ette antud juhiseid ja koostasin skripti, mis korjab infot Windows süsteemi kohta.

## Skript
```
#$nr:	küsimuse number
#$param: mis parameetriga tegemist (võimalikult lühidalt)
#$sisu:	väljastatav sisu
function valjasta {
    param ($nr, $param, $sisu)
    $fail = ".\tulemus.txt"
    $aeg = Get-Date -Format "HH:mm:ss.fff"
    if ($sisu -eq $null) {
        $rida = "$nr. $aeg ${param}: NULL"
        Write-Output $rida
        $rida | Out-File -FilePath $fail -Append
    } elseif ($sisu.GetType().Name -eq "Object[]") {
        $rida = "$nr. $aeg ${param}:"
        Write-Output $rida $sisu
        $rida | Out-File -FilePath $fail -Append
        $sisu | Out-File -FilePath $fail -Append
    } else {
        $rida = "$nr. $aeg ${param}: $sisu"
        Write-Output $rida
        $rida | Out-File -FilePath $fail -Append
    }
}

$valjundfail = "$env:USERPROFILE\opsys13.txt"
Start-Transcript -Path $valjundfail -Append

[int]$aegA = (Get-Date).Millisecond

try {
    $ErrorActionPreference = 'SilentlyContinue'
    valjasta 0 "ALGUS" ("Aeg: "+(Get-Date -Format "dddd MM/dd/yyyy HH:mm K")+" Teostaja: Erkki")
    
    valjasta 1.1 "Masina nimi" (hostname)
    valjasta 1.2 "PowerShelli versioon" ($PSVersionTable.PSVersion)
    valjasta 1.3 "Windowsi versioon" ((Get-CimInstance Win32_OperatingSystem).Version)

    valjasta 2.1 "IP-aadress" ((Get-NetIPAddress -AddressFamily IPv4).IPAddress)
    valjasta 2.2 "Võrgumask" (Get-NetIPAddress | Where-Object {$_.AddressFamily -eq 'IPv4'}).PrefixLength
    valjasta 2.3 "Gateway" ((Get-NetRoute "0.0.0.0/0").NextHop)
    valjasta 2.4 "DHCP luba" ((Get-NetIPConfiguration | Select-Object -ExpandProperty NetIPv4Interface).Dhcp)
    valjasta 2.5 "MAC-aadress" ((Get-NetAdapter | Where-Object { $_.Status -eq 'Up' }).MacAddress)

    valjasta 3.1 "Protsessor" ((Get-CimInstance Win32_Processor).Caption)
    valjasta 3.2 "RAM" ((Get-CimInstance Win32_ComputerSystem).TotalPhysicalMemory / 1GB)

    valjasta 4.1 "Graafikakaardi nimi" (Get-CimInstance Win32_VideoController).Caption 
    valjasta 4.2 "Draiveri versioon" (Get-CimInstance Win32_VideoController).DriverVersion
    valjasta 4.3 "Kuupäev" (Get-CimInstance Win32_VideoController).DriverDate
    valjasta 4.4 "Ekraani lahutus" ((Get-CimInstance Win32_VideoController).CurrentHorizontalResolution, "x", (Get-CimInstance Win32_VideoController).CurrentVerticalResolution)

    valjasta 5.1 "Partitsioonitabel" (Get-CimInstance Win32_DiskPartition | Select-Object -Property DeviceID, Size)
    valjasta 5.2 "Ketta maht" (Get-CimInstance Win32_DiskDrive | ForEach-Object { $_.Size / 1GB })
    valjasta 5.3 "Vaba ruum C: kettal GB-des" ((Get-CimInstance Win32_LogicalDisk -Filter "DeviceID='C:'").FreeSpace / 1GB)

    valjasta 6 "Draiverite info" (Get-WmiObject -Class Win32_PnpSignedDriver | Where-Object {$_.DeviceID -like "PCI*"} | Select-Object Description, Manufacturer, DriverVersion | Sort-Object Description | Format-Table)

    valjasta 7 "Arvuti kasutajad" (Get-WmiObject Win32_UserAccount | Select-Object Name, Description, LocalAccount, Disabled | Format-Table)

    valjasta 8 "Käimasolevate protsesside arv" ((Get-Process).Count)

    valjasta 9 "10 viimast käivitatud protsessi" (Get-Process | Sort-Object StartTime -Descending | Select-Object -First 10 Name, Id, StartTime | Format-Table)

    valjasta 10 "Arvuti kuupäev ja kellaaeg" (Get-Date)
}
finally {
    $ErrorActionPreference = 'Continue'
}

[int]$aegL = (Get-Date).Millisecond
$ajakulu = ($aegL - $aegA)

valjasta "*" "TEHTUD" "$ajakulu`n`n"

Stop-Transcript
```

## Kogun erinevat infot süsteemi kohta skriptiga
    Get-Date: Tagastab praeguse kuupäeva ja kellaaja.
    Get-CimInstance: Tagastab Windows Management Instrumentation (WMI) objektide eksemplarid, mis võimaldavad juurdepääsu süsteemi haldusandmetele.
    Get-NetIPAddress: Tagastab IP-aadressid, mis on määratud arvuti võrguliidestele.
    Get-NetRoute: Tagastab teavet arvuti võrgumarsruutide kohta.
    Get-NetIPConfiguration: Tagastab IP-konfiguratsiooni üksikasjad arvuti võrguliideste kohta.
    Get-NetAdapter: Annab teavet arvuti võrgukaartide kohta.
    Get-WmiObject: Tagastab WMI objektide andmed.
    Get-Process: Tagastab teavet arvutis hetkel töötavate protsesside kohta.

## Faili salvestus
  $valjundfail = "$env:USERPROFILE\opsys13.txt" - Asukoht kuhu fail salvestatakse ja mis nimega.
  Start-Transcript -Path $valjundfail -Append - Hakkab teksti faili kirjutama.
  Stop-Transcript: Lõpetab teksti faili kirjutamise, salvestades kogu väljundi faili määratud.


## Try-finally

Try-finally plokk kindlustab, et isegi kui try-plokis tekib viga, taastatakse ErrorActionPreference väärtus lõpuks finally-plokis. Kasutasin, et lahendada probleemi, kus punktis 9 oli mitmete protsesside algusajale ligipääs keelatud.

## Väljund fail
    
