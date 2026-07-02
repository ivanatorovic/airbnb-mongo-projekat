# Projekat iz predmeta SBP
**Tema:** Analiza Airbnb smeštaja u Madridu korišćenjem MongoDB baze podataka

**Autori:**

- Ivana Torović IN29/2022
- Tijana Barudžija IN6/2022

# Opis skupa podataka

Za potrebe projekta korišćen je javno dostupan skup podataka **Madrid Airbnb Data** sa Kaggle platforme.

Skup podataka sadrži informacije o Airbnb smeštajima u gradu Madridu i obuhvata:

- osnovne informacije o smeštajima,
- detaljne informacije o domaćinima,
- kalendar dostupnosti,
- korisničke recenzije,
- detaljne recenzije,
- geografske podatke o naseljima.
  
## Korišćene datoteke

- listings.csv
- listings_detailed.csv
- reviews.csv
- reviews_detailed.csv
- calendar.csv

Za potrebe MongoDB projekta izvršena je podela podataka u više kolekcija kako bi se omogućilo izvođenje složenih agregacionih upita korišćenjem operatora `$lookup`.

# Šema baze podataka

Za potrebe projekta kreirane su dve verzije baze podataka.

## Prva verzija

Prva verzija prati originalnu strukturu skupa podataka.

Korišćene kolekcije:

- listings
- listings_detailed
- reviews
- reviews_detailed
- calendar

Nad ovom šemom izvršavani su složeni agregacioni upiti bez dodatnih optimizacija.

## Druga verzija

Druga verzija baze kreirana je sa ciljem poboljšanja performansi upita.

Optimizacija je obuhvatila:

- kreiranje jednostrukih i kompozitnih indeksa,
- denormalizaciju pojedinih kolekcija,
- kreiranje pomoćnih (materijalizovanih) kolekcija za najskuplje upite.

Na ovaj način značajno je smanjeno vreme izvršavanja agregacionih upita.

# Upiti

## Domaćin

1. U kojim naseljima domaćini imaju najveći broj recenzija?
2. Koji tip smeštaja donosi najveći broj recenzija?
3. Da li verifikovani domaćini imaju veći broj rezervisanih dana od neverifikovanih domaćina?
4. Da li smeštaji sa instant rezervacijom imaju veću prosečnu popunjenost?
5. Koji meseci i godine imaju najveću prosečnu popunjenost?
6. Koja naselja imaju najviše rezervisanih dana?

## Turista

1. Koji smeštaji imaju najveći broj recenzija?
2. Koji sadržaji se najčešće pojavljuju kod smeštaja sa mnogo recenzija?
3. Koja naselja imaju popularne smeštaje i kojoj zoni pripadaju?
4. Koji smeštaji su najteže dostupni za rezervaciju?
5. Koje karakteristike turisti najčešće ističu u komentarima?
6. Koji smeštaji imaju najbolji turistički skor i najviše stvarnih komentara turista?

# Performanse
Za svaki upit upoređene su performanse pre i nakon optimizacije, pri čemu je analizirano ostvareno ubrzanje izvršavanja.

<img width="1168" height="617" alt="image" src="https://github.com/user-attachments/assets/24678838-a796-442a-9e08-0c8c00812358" />

<img width="1182" height="602" alt="image" src="https://github.com/user-attachments/assets/03b59bb9-9bfd-47f4-8f3c-a30e8b304c87" />


