# hydra-ssh-fail2ban
Prosjekt som viser Hydra brute force-angrep på SSH og hvordan Fail2Ban beskytter Ubuntu-serveren.
# Hydra SSH brute-force og Fail2Ban beskyttelse

Dette prosjektet viser hvordan man kan simulere et brute-force-angrep på SSH ved hjelp av **Hydra**, og hvordan **Fail2Ban** beskytter Ubuntu-serveren mot slike angrep.



## Steg 1: Finne IP-adresser
Her bruker vi `ip a` for å hente ut IP-adressen til maskinen.  
Bilde 1



## Steg 2: Hydra brute-force forsøk
Forsøk på å bruke Hydra med en ordliste (`rockyou.txt`) mot SSH-tjenesten.  
Bilde 2



## Steg 3: Hydra feilmeldinger og SSH-tilkobling
Flere forsøk med Hydra, samt en vellykket SSH-tilkobling til Ubuntu-serveren.  
Bilde 3



## Steg 4: Flere Hydra-forsøk
Her prøvde jeg å finne IP-adressen til maskinen ved å bruke ip a.
Jeg testet også noen kommandoer som ga feil (ping <Ubuntu-IP> og en grep-kommando).
Dette viser at det tok litt tid å finne rett metode, men til slutt fant jeg riktig IP for å kunne bruke Hydra mot SS  
Bilde 4



## Steg 5: Oppdatering og installasjon av seclists
Ubuntu oppdateres og pakken `seclists` installeres, som inneholder ordlister til Hydra.  
Bilde 5



## Steg 6: Konfigurere Fail2Ban
Status for Fail2Ban sjekkes, og konfigurasjonsfila (`jail.local`) redigeres. Til slutt restartes Fail2Ban.  
Bilde 6



## Steg 7: Fail2Ban blokkerer IP
Her ser vi at Fail2Ban har bannet IP-adressen til angriperen etter flere feilede innloggingsforsøk.  
Bilde 7



## Steg 8: Opprette ny bruker
Ny bruker `testuser` opprettes for testing. Denne brukeren får ikke sudo-rettigheter.  
Bilde 8



## Steg 9: Fail2Ban stopper tjenesten
Fail2Ban stopper `sshd` jail etter å ha blokkert angrepet.  
Bilde 9



## Steg 10: Hydra-forsøk med manglende ordliste
Her forsøkte jeg å kjøre Hydra, men fikk feilmelding fordi rockyou.txt-wordlisten ikke var tilgjengelig.
Jeg prøvde å pakke ut filen og installere nødvendige pakker, men møtte flere "No such file or directory"-feil.
Dette viser at det er viktig å ha riktige wordlister på plass før man kan utføre brute force-angrep 
Bilde 10



## Steg 11: Fail2Ban oppstartsmelding
Fail2Ban har startet opp igjen og sender en melding til administrator via e-post om at `sshd` jail er aktivert på nytt.  
Bilde 11



# Konklusjon
Dette prosjektet viser:
- Hvordan **Hydra** kan brukes til brute-force angrep på SSH.  
- Hvordan **Fail2Ban** overvåker innloggingsforsøk og automatisk blokkerer IP-adresser etter gjentatte feil.  
- At kombinasjonen av logging, overvåkning og automatisk respons er effektiv for å beskytte servere.  

