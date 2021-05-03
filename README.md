# CGI proovitöö

## Sisukord
+ [Üldine](#about)
+ [Setup](#setup)
+ [Probleemid ja lahendused](#steps)

## Üldine <a name = "about"></a>
Siin leidub minu CGI proovitöö projekt. Tegin sellist projekti esimest korda, ning ma pole kunagi enne kokku puutunud sellise MVC projektiga. Vaatamata sellele sain projekti tehtud ning õppisin väga palju uut Java kohta ning ka kuidas sellised web applicationid töötavad.
Kuna proovitöö sain kätte veidi halval ajal (gümnaasiumi eksamiperiood) ei saanud ma kõike aega selle 2 nädala jooksul selle projekti peale panna. Kokku läks projekti valmistamiseks umbes 30 tundi, ning suur osa sellest oli alguses Springi ja Thymeleafi dokumentatsiooni uurimine ja selle selgeks tegemine. 

## Setup <a name = "setup"></a>
Alustuseks klooni projekt ja ava IntelliJ või Eclipsega. CGI poolt saadetud detailsema projekti seadistamise juhise panin projektiga kaasa.


## Probleemid ja lahendused <a name = "steps"></a>

Iga etapi läbimisel lisasin commitisin githubi oma projekti, ehk minu lahenduskäiku ja koodi arengut saab läbi githubi näha. Siinkohal teen ka ülevaate, kuidas iga etapi programmeerisin ja milliseid takistusi ma sellel teel kohtasin.

### ETAPP 1 - Esmased muudatused

Sain projekti seadistatud ja hakkasin uurima, kuidas kõik töötab. Olen harjunud programmeerima C++-is, nii et selline Model View Controller süsteem tekitas algselt minu jaoks väga palju segadust. Sain kasutajaliidesesse esimesed muudatused tehtud kasutades tavalist HTML-i (näiteks hambaarsti valik oli algselt ainult form.html-is) ning tegin muudatusi DentistVisitDTO objektis, et HTML-is olev LocalDate ja LocalTime töötaksid samamoodi nagu töötas enne inputiga selle sisestamine.
Esimene kõige suurem takistus mis ette jäi oli andmebaasi seadistamine. Jälgisin paari juhendit (mis on koodis kommenteeritud) kuidas seadistada CRUDRepository süsteemi oma andmebaasiga, kuid iga kord kui midagi andmebaasi soovisin lisada, tuli debuggides vastus et kõik töötas, kuid andmebaasis seda infot ei olnud. Avastasin lõpuks, et H2 konsooli default andmebaas ei olnud sama, mida see projekt algselt kasutas, ning kui sisenesin õigesse andmebaasi leidsin kõik andmed õigesti üles.
Valideerisin saadetuid andmeid DentistVisitDTO objektis constraintidega, nagu oli juba ette tehtud. 

### ETAPP 2 - Registreeringute tabel

Siin etapis sain enam-vähem juba aru kuidas Spring MVC töötab ja lõin uue html lehe tabeli jaoks, kus kuvati nimekirjas kõik registreeritud visiidid. Kõige rohkem segadust tekitas algul visiitide kuvamine tabelis, kuna ma ei osanud veel nii hästi Thymeleafi kasutada. 
Registreeringute tabel ei olnud kõige raskem, kuna peamiselt töötasin HTML-i kaudu, ning kirjutasin ühe kerge funktsiooni getAllVisits() mis kuvab kõik visiidid tabelisse.

### ETAPP 3 - Kustutamine, muutmine ja saadavuse kontroll

Selles etapis lisasin alguses kustutamise nupu kerge html-iga ja saatsin sellega formi, mis kustutab valitud ID'ga visiidi andmebaasist. See oli veel enamjaolt kerge samm kuid muutmine oli igatpidi keerulisem - pidin jälle koostama terve uue lehe ning seal tegema järgmise formi, mis muudab antud ID'ga visiiti ja uuendab seda. Selle sammu juures oli kindlasti kõige keerulisem selle ID edasi saatmine järgmisesse funktsiooni - formi submittides salvestad ID DentistVisitService objekti ning modify lehel võtad selle ID salvestatud integerist. Ma arvan et sellele probleemile oleks olnud veidi kergem lahendus, kuid praegune lahendus töötas ajutiselt, nii et kasutasin seda.
Saadavuse kontroll oli samuti keeruline kuid see sai paari funktsiooniga tehtud. Kood on ilusti kommenteeritud nii et koodi lugedes on kõige parem oma silmaga näha kuidas see töötab.
