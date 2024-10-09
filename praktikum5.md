# Praktikum 5 aruanne. Failiõigused Linuxis

Esitan 5. operastioonisüsteemide kursuse praktikumi ülesande. Praktikumi käigus jälgisin ette antud juhiseid ning pidi looma erinevaid faile linuxis erinevate kasutajatega ning muutma nende kasutamisõigusi.



Ülesanded
---
<img width="620" alt="praktikum5_kys" src="https://github.com/user-attachments/assets/284e5002-829b-495d-8960-315ad34d8b21">

5.1 a) Kausta avamiseks on vaja (x) õigust ja faili lugemiseks (r) õigust. b) Kaustast faili kustutamiseks on vaja (w,x) õigusi ning failil pole vaja mingeid kindlaid õigusi, et seda kustutada.
---
5.2 Sest see annab kõikidele kasutajatele õigse ainult käivitada faile, aga selleks, et käivitada skripti on see vaja alguses läbi lugeda.
---
5.3 Et lihtsustada failide ja õiguste haldamist. Kasutajapõhised grupid võimaldavad lisada kasutajaid teistesse gruppidesse, et jagada faile, ilma et see mõjutaks nende isiklikke faile.
---
5.4 Vaja oleks lugemisõigust (r) failile uusfail.txt, kas kasutajale kaspar või grupile majasisene.
---
5.5 setuid, setgid
---
<img width="620" alt="praktikum5.5" src="https://github.com/user-attachments/assets/2284ec55-aca0-41ca-9d36-48f3460f76c9">

5.6 Jah, setuid-i kasutamine võib vähendada süsteemi turvalisust kui seda ei hallata hoolikalt. See võimaldab programmidel töötada kõrgendatud õigustega, mida saab ära kasutada kui programmis on turvaaugud. Seetõttu on oluline kasutada setuid-i säästlikult ja tagada programmide turvalisus.
---
5.7 Peetri faile saavad kustutada: Kaspar, opetaja, peeter ja root
---
5.8 ACL
---
<img width="620" alt="praktikum5.8" src="https://github.com/user-attachments/assets/a7e8a612-6bc2-457f-92e6-4984126d0ac8">

5.9 Keegi ei saa faili sisu modifitseerida faili sisu, sest on immutable atribuudiga. Kustutamiseks tuleb atribuut eemaldada ja siis saab anda käsu kustutamiseks.
---
