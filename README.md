X-ri 	V-0.1	 (Pre-Alpha) 		D-1/4/2023


Af Jens Mikkel Schroll Andersen
-----------------------------------------------------------------------------------------------------------------------------------------------------------#
-----------------------------------------------------------------------------------------------------------------------------------------------------------#

	FOR KORT VERSION LÆS KUN: "INSTALLATION" OG "BRUG AF".
 
-----------------------------------------------------------------------------------------------------------------------------------------------------------#
	Intro til X-ri:



X-ri er et værktøj der kan; tage en hvilken som helst CNN-model*, der er trænet på data bestående af frontale X-Rays af lungen, og genererer;
 
ud fra et hvilket som helst frontalt lunge X-Ray**, en automatisk zone opdeling af Grad-CAM-fortolkning, forkortet; AZGC-fortolkning.



Denne opdelingen, i dette tilfælde, er et automatisk estimat***, bygget ud fra de 4 "Chest radiograph zones"[1]. 

Zone 1 og 2 er sammen lagt, og alle 3 er delt i højre og venstre lunge****. Denne AZGC-fortolkning prøver at give brugeren/fagpersonen evnen til; 

at kunne dømme og "diskutere" med modellens forudsigelser "case by case", inden for brugeren/fagpersonens eget ramme værktøj [1], forhåbentligt, 

via en relativt let og overskuelig proces.  





* Denne Pre-Alpha version, er hverken testet til-, eller har nogen bruger venlig måde at-, indlæse egen model på, men teoretisk set burde det ”virke”.

Hvis man alligevel vil prøve, er der en ”manuel” installations ”guide” længere nede.
  
** Programmet understøtter teoretisk set, billede formaterne: ”PNG, JPEG, PPM, GIF, TIFF, and BM”, men PNG og JPG er de eneste der er testet til at virker.

  
*** Dette estimat indrammer også selve lungen, men da dette er Pre-Alpha, er disse estimater nogle gange meget upræcise. 

For ikke at forvirre brugeren/fagpersonens, i forhold til processen; at dømme modellen, har vi lagt to test eksempler med, 

hvor man kan se hvordan zonerne opdelingen helst skal se ud.  
     
**** DER BLIVER IKKE TAGET HØJDE FOR OM X-RAY’ET, ER FLIPPET ELLER EJ, så man bliver, på nuværende tidspunkt, 

selv nød til at holde øje med hvad der er højre og venstre. (i forhold til labels, i AZGC-fortolkningsresultatet) 

Kilde [1]: https://radiopaedia.org/articles/chest-radiograph-zones

-----------------------------------------------------------------------------------------------------------------------------------------------------------#
	Installation af X-ri:


 
-Først, ekstrakt Zip filen til en mappe. 

-Derefter, gå ind i X-ri mappen, find X-ri.exe nede omkring bunden, og double klik på den.(ignorere consolen, programer starter 3 sk efter)

-{Optionel} Højre klik på X-ri.exe filen og tryk på ”opret genvej”.

 Tag så denne, nye genvejs-fil, og flyt den til skrivebordet.

 (Nu kan man i stedet starte X-ri, ved at double klikke denne genvej) 

  

-ER IKKE TESTET PÅ MAC OG LINUX! (virker måske, men ”path problematikker” vil højst sandsynligt opstå)

-KØR IKKE; (X-ri.exe, eller X-ri.exe – Genvej), SOM ADMINSTRATOR! dette gør at programmet ikke virker, af-, på nuværende tidspunkt, uforklarlige årsager.

(For ”manuel” ”installering” af egen model, læs længere nede)

-----------------------------------------------------------------------------------------------------------------------------------------------------------#
	Brug af X-ri:


 
-Man tager et frontale lunge X-Ray, og ”drag and drop’er” filen ned i program winduet, ikke konsollen 😉. (som nævnt før, helst kun PNG og JPG filer)
 
-2-10 sekunder senere kommer AZGC-fortolkningsresultatet for givent frontalt lunge X-Ray så frem. Hvis man derefter gerne vil prøve et andet X-Ray,
 
skal man bare smide det ind i winduet lige som før. (man kan starte, med at bruge de to test billeder i main mappen)
 
(Hvis man gerne vil gemme resultatet, da det bliver slettet når et nyt resultat bliver genereret, 

skal man bare gå ind i programmappen ”X-ri”, finde mappen ”img”, gå ind i den og kopiere ”TempMain.png”)

 

-De to CNN-modeller der er ”preloaded” er selv udviklet, og prøver at forudsige pneumonia.
 
(skal ikke tages for seriøst, da de blev lavet specifikt til at udvikle dette program,
 
der eksistere meget bedrer CNN-modeller, til at forudsige pneumonia)



-Model 2* giver klart de bedste resultater, og er default.


-Model 1** er nogle gange bedrer hvis billedet er zoomet tæt ind på ”brystet”.


-Man skifter model ved at trykke på knappen i midten.



* Stats for model 2: {Recall of the model is 0.89 Precision of the model is 0.85}


** Stats for model 1: {Recall of the model is 0.90 Precision of the model is 0.95}

 
(Model 1 her, bedrer ”stats” på intern data, men klares sig, ud fra minimal testning, 

langt dårligere på data der ikke er fra det originale, test, val, train, data. Høstsandsynligt på grund af ”overfitting”) 

 
-----------------------------------------------------------------------------------------------------------------------------------------------------------#
Mail: jensmikkelandersen@gmail.com

 
Tlf: 28511878 

-----------------------------------------------------------------------------------------------------------------------------------------------------------#
	Indlæsning af egene CNN-modeller {relativt avanceret} {Super Pre-Alpha}:



Programmet er på nuværende tidspunkt sat op på en måde, hvor det ikke er fleksibelt i forhold til andre, ind de 2 ”preloaded”. 


Sagt med andre ord, Model variablerne er faste ☹. Dette kan fikses relativt hurtig med en lappeløsning fra min side,

ellers kan man f.eks. 

også bare ændre sin CNN-model conv-lag til de 2 modellers faste conv variabelnavne*, gemme ens CNN-model, og model vægte,

via ”model_from_json fra keras” med de samme filnavne som model 2 bruger, tjek ”img”, og derefter erstatte de 2 tilsvarende filer. 


Der er et utal at ting der nok ikke ville virker optimalt, men i teorien hvis modellen er Sequential, og arbejder ud fra frontale lunge X-Ray billeder,
 
burde det virke nogen lunde. 


Men hvis man er så opsat, vil jeg heller anbefalede at man skriver til mig på enten tlf eller mail, så kan vi sammen lave en lappeløsning, 

eller også har jeg en ny "version" af X-ri med en ordentlig ”feature” implementering. 

-----------------------------------------------------------------------------------------------------------------------------------------------------------#
-----------------------------------------------------------------------------------------------------------------------------------------------------------#
