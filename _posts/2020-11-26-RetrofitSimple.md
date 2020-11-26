---
layout: post
title: HTTP Request & Retrofit
---


01) INSERIRE LE DIPENDENZE
In build.gradle (Module: <nomeTuaApp>) aggiungere:
  
    // Retrofit
    implementation 'com.squareup.retrofit2:retrofit:2.9.0'

    // GSON
    implementation 'com.squareup.retrofit2:converter-gson:2.5.0'

e premere Sync.

NB: la 2.9.0 è l'ultima versione disponibile nel momento in cui sto scrivendo questa pagina. Dopo aver fatto il Sync, Android Studio vi segnalerà se è l'ultima versione disponibile (basta posizionarci il mouse sopra) permettendovi eventualmente di aggiornare all'ultima versione.


02) AGGIUNGERE I PERMESSI PER UTILIZZARE INTERNET
In AndroidManifest.xml, aggiungere i permessi per utilizzare internet:

<uses-permission android:name="android.permission.INTERNET"/>

e premere Sync.

03) DEFINIRE L'INTERFACCIA DI RETROFIT
getDestination() e DeleteDestination(()

L'interfaccia contiene le informazioni per raggiungere il web service

04) CREARE IL SERVICE BUILDER DI RETROFIT
createService (<T> Services) -> destinationService

Il Service Buildere ci aiuterà a chiamare le funzioni presenti nell'interfaccia.

5) CHIAMARE LE FUNZIONALITA' DI RETROFIT DALL'ACTIVITY/FRAGMENT
destinationService.getDestination()

Dalla nostra Acrtivity (dal nostro Fragment) dovremmo inizializzare il Service Builder e chiamare le funzionalità presenti nell'interfaccia.




