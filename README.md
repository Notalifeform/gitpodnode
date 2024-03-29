# 5HV-webshop-template (*vervang door de naam van je webshop*)

Deze webshop is gebaseerd op het template voor 5HV van het Emmauscollege Rotterdam
Je kunt het template zelf uitproberen in Replit: 
[Run on Repl.it](https://replit.com/github/vangeest/webshop-replit-example)

### In mijn webshop vind je: 
- *wat je verkoopt*
### Deze webshop is gemaakt door: 
- *naam van leerling 1* 
-  *naam van leerling 2*

# Mijn aanpak
Werk de planning af van boven naar beneden<br>
Geef aan met [x] welke onderdelen af zijn

Stap 1: Start 
- [ ] Pas de achtergrondkleur van de shop aan (zie mapje web)
- [ ] Pas de titel van het eerste product in de shop aan (zie mapje db)
- [ ] Pas de query aan zodat getoonde producten gesorteerd worden op naam (zie mapje api)

Stap 2: Database opzetten 
- [ ] Maak tabellen en velden (CREATE TABLE commando) in je database waarin alle informatie kan worden opgeslagen die je over je producten wilt tonen.<br>
Tip: je kunt een multipliciteitendiagram gebruiken als tussenstap voor je database-ontwerp
- [ ] Vul de tabellen met informatie (INSERT commando)
- [ ] Voeg eventueel plaatjes toe (web/images map)

Stap 3: API aanpassen 
- [ ] Pas de API aan, zodat je alle informatie uit je database kunt opvragen via de API

Stap 4: Website aanpassen 
- [ ] Pas de website aan, zodat alle informatie getoond wordt.

Stap x: Webshop verder verbeteren
- [ ] Herhaal stap 2 t/m 4 om je webshop verder te verbeteren. 
Voor en goed cijfer is het belangrijk dat je laat zien dat je uitstekend begrepen hebt hoe je een webshop moet opzetten.


# Basis uitleg hoe de webshop werkt
The basic idea is that a webpage of the shop is loaded by the browser and information on the articles in the shop are added to that depending on what the user selects.

1. You open a browser and navigate to the webshop. 
2. The browser downloads the html en css files from the server. It also downloads a piece of javascript code.
3. The javascript code is being executed by the browser. The javascript code connects to a link on the server that is connected to the api. This is called a REST-interface. Through the REST interface, the javascript code in the browser request information on the articles it needs to display.
4. The api is a programm on the server which connects to the database. It requests information from the database and sends it back to the browser. The result is sent in json-format.
5. The javascript programm in the browser looks at the json-file and add's elements containing articels in the shop to the DOM. The DOM is the model of the html files that the browser keeps in it memory and shows to the user. These elements added are displayed by the browser.

An alternative approach would be to have the server build complete web-pages including all information on articles. This is the idea behind the php programming language. The REST-interface is gaining popularity. An advantage of REST above php is that REST allows for more responsive (interfactive) websites.

# Uitleg over bestanden en mappen

## db folder
Database with information on the arcticles in the shop

## web folder
Static (non changing) html, css en js files.

## api folder
js files which are being executed on the server when the api is called

## .replit
We use a bash-repl (language="bash" in .replit file), because bash has sqlite3 and nodejs installed. Downside of bash-repl: The nodejs-repl installs packages automatically by scanning your code. In the bash-repl we have to maintain dependencies in a packages file manually. 

## start.sh
This file is executed everytime you click on "Run" in replit. What it does is:
1. (re)install packages using the package.json file
2. (re) create the databasefile db/my.db
3. start the server for the api en webpages

# Uitleg van code
De code is voorzien van commentaar op punten waar de werking misschien niet eenvoudig te volgen is.
We gaan er vanuit dat je basiskennis hebt over html, css en Javascript. Dit heb je geleerd in de vierde klas. 
In deze webshop worden een aantal technieken gebruikt die je niet in de vierde hebt gehad. Die lichten we kort toe.

## functies als parameters
Bij de aanroep van een functie kun je variabelen meegeven als parameter. 
Dit ken je van de vierde klas.
Je kunt ook functies meegeven als parameter. 
In Javascript wordt dit veelvuldig gebruikt.

## asynchrone functies
In de meeste programmeertalen word code van boven naar beneden uitgevoerd. 
In Javascript wordt soms met de volgende opdracht doorgegaan voordat de vorige klaar is. 
Als de vorige klaar is dan wordt er een functie aangeroepen die als parameter is meegegeven aan de vorige opdracht. 
Dit is een krachtige functionaliteit van Javascript maar voor beginnende programmeurs lastig te doorgronden. 
Dit wordt bijvoorbeeld gebruikt bij het versturen van mail.

## html templates
Je kunt Javascript gebruiken om extra elementen aan je webpagina toe te voegen nadat deze geladen is. 
Een veelgebruikte manier daarvoor is het opnemen van een stukje template (html tussen  tussen <template> en </template>) in het html bestand
Het template wordt niet door de broswer getoond, maar het stuk html in het template kan in Javascript worden gekopieerd (gecloned) en aangepast.
Dit wordt bijvoorbeeld gebruikt bij het tonen van artikelen in de shop.

# Documentatie 

* tutorial building a REST-api with postgressDB + jsnode + jsexpress<br>
https://blog.logrocket.com/setting-up-a-restful-api-with-node-js-and-postgresql-d96d6fc892d8/
* serving static files with jsexpress<br>
https://expressjs.com/en/starter/static-files.html
* basic html & css & javascript reference<br>
https://www.w3schools.com
* basic sql course<br>
https://www.khanacademy.org/computing/computer-programming/sql
* sqlite3 gebruiken op in Shell<br>
https://www.sqlite.org/cli.html
* better-sqlite library gebruiken in nodejs (javascript)<br>
https://github.com/JoshuaWise/better-sqlite3/blob/HEAD/docs/api.md
* shoppping basket lokaal opslaan<br>
google op local storage javascript basket
* bestelling mailen<br>
video met gebruik van nodemailer (module in javascript) vind je hier: https://youtu.be/Va9UKGs1bwI
* replit online editor en hosting ontwikkelomgeving<br>
https://docs.replit.com/
* gitpod online editor en hosting ontwikkelomgeving<br>
https://www.gitpod.io/docs/
* introdution to docker (kennis alleen nodig als je de repo heftig wilt aanpassen)<br>
https://docker-curriculum.com
* yarn (kennis alleen nodig als je de repo heftig wilt aanpassen)<br>
https://yarnpkg.com/getting-started

# Howto 

## Fouten zoeken in de database
Open de database in de Shell met het volgende commando
```
sqlite3 db/my.db
```
Je kunt met SQL commanda's zien wat er in de database staat. bijvoorbeeld
```
SELECT * from Products;
```

## Fouten zoeken in de api
Bekijk de console op de server (replit of gitpod), daar kun je foutmeldingen zien.
Je kunt in de code opdrachten toevoegen die inhoud van variabelen afdrukken. Bijvoorbeeld:
```
console.log("Waarde van i is ", i);
```

## Fouten zoeken in de webpages
Bekijk de console in de browser, daar kun je foutmeldingen zien.
Je kunt in de code op strategiche plaatsen de opdracht
```
debugger
```
toevoegen. Als de console open staat dan stopt de browser met het uitvoeren van code, zodat je via de console opdrachten kunt geven. Je kunt de inhoud van variabelen bekijken met de opdracht:
```
console.log("Waarde van i is ", i);
```

## Mail configureren in Replit
De shop mailt elke order die geplaatst is.
Mailen werkt niet in gitpod, omdat de smtp-port dicht staat.
Mailen door de shop in replit werkt als volgt.
Zet de environment variabelen (slotje links in replit menu)
```
GMAIL_EMAIL=<email account>
GMAIL_PASSWORD=<email wachtwoord>
ORDER_MAIL_TO=<jouw email waar je orders ontvangt>
```

Als je gmail gebruikt zonder tweestapsverificatie:<br>
Zet in gmail (account->beveiliging) gebruik van minder veilige apps aan

Als je gmail gebruikt met tweestapsverificatie:<br>
Maak een app-wachtwoord (account->beveiliging) en zet dat in GMAIL_PASSWORD

Test je emailconfiguratie:<br>
Doe een bestelling en kijk naar de console in replit. 
De api meldt op de console als mail succesvol is verzonden en geeft een foutmelding als het niet is gelukt.

## Random images maken

```
count=1
while [[ $count -lt 100 ]]
do
 echo $count
 count=$[$count+1]
 wget -O $count.jpg https://picsum.photos/200/300
done
```

## Posting data 

onze backend code kan alleen 'x-www-form-urlencoded' aan, voor 'multipart/form-data' default Form-data format moeten we de 'formidable' lib gebruiken 
(https://www.npmjs.com/package/formidable)


# Credits
- avs123a<br>
for a "Simple inventory list example with crud using : NodeJS, express framework, pug template, sqlite database and bootstrap". See https://github.com/avs123a/NodeJS-simple-example
- Robert Bakker [Notalifeform](https://www.gihub.com/Notalifeform)<br>
for help almost 24x7 with many questions and problems and providing basic shop called gitpodnode to be further developed by students on gitpod and deplyed freely on heroku. See https://gitpod.io/#https://github.com/Notalifeform/gitpodnode




