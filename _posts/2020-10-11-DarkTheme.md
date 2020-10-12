---
layout: post
title: Dark Theme
---



Aggiungere la libreria per utilizzare i componenti Material Design: aprire il file build.gradle (Module: app) ed aggiungere:

implementation 'com.google.android.material:material:1.2.0-alpha03'
    
1.2.0-alpha03 è la versione della libreria; se ve ne dovesse essere una versione più aggiornata, utilizzare quella.

Aggiungere nel layout uno switch button che utilizzeremo per passare dalla modalità chiara a quella scura:


    <com.google.android.material.switchmaterial.SwitchMaterial
        android:id="@+id/switchDarkTheme"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="50dp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        android:text="Dark Theme"/>


A questo punto dobbiamo creare un tema chiaro ed un tema scuro. Una delle vie per far ciò è quella di aprire utilizzare quanto messo a disposizione dal progetto Material Theme Builder che è stato creato dal team Material Design di Google.

- Scaricare i sorgenti dal repository GitHub (https://github.com/material-components/material-components-android-examples/tree/develop/MaterialThemeBuilder)
- Aprire il progetto in Android Studio
- Andare con il mouse nella cartella res, premere il tasto destro del mouse e scegliere Show in Explorer; si aprirà il file manager
- Copiare la cartella values-night ed i file color.xml, shape.xml, styles.xml, themes.xml e type.xml che sono nella vartella values ed incollarli nelle cartelle del progetto sul quale stiamo lavorando (NB: aprire le cartelle del prgetto nel file manager come fatto in precedenza con il progetto Material Theme Builder in quanto effettuare la copia di file e cartelle all'interno di Android Studio non sempre genera i risultati attesi)

Se ora provate a compilare l'applicazione, vi verrà restituito errore (o almeno a me ha restituito errore); io ho risolto facendo le seguenti modifiche:
- nell'AndroidManifest.xml cercare android:theme="@style/AppTheme" e cambiarlo con android:theme="@style/Theme.MyApp" (Il Matrail Theme Builder genera un tema assegnandogliun nome che è diverso da quello standard generato da Android Studio)
- in styles.xml eliminare la riga <item name="android:windowAnimationStyle">@style/Animation.MyTheme.BottomSheet.Modal</item> (non gestiamo le animazioni in questa fase) 


A questo punto creiamo qualche elemento nel layout per verificare il funzionamento del tema.

Aggiungere al layout uno switch button che utilizzeremo per passare dalla modalità chiara a quella scura:


    <com.google.android.material.switchmaterial.SwitchMaterial
        android:id="@+id/switchDarkTheme"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="10dp"
        android:layout_marginTop="50dp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        android:text="Dark Theme"/>

Nel codice kotlin possiamo gestire lo switch button in modo da cambiare il tema a seconda dello stato con il seguente codice:

switchDarkTheme.setOnCheckedChangeListener { buttonView, isChecked ->
     if (isChecked) AppCompatDelegate.setDefaultNightMode(AppCompatDelegate.MODE_NIGHT_YES
     else AppCompatDelegate.setDefaultNightMode(AppCompatDelegate.MODE_NIGHT_NO)
}

Ora che abbiamo impostato il sistema possiamo andare a cambiare i colori, le forme, oppure salvare lo stato dello switch button in modo che alla riapertura dell'app venga proposto quanto scelto dall'utente, etc.... Buone modifiche ! 

Codice sorgente: https://github.com/Allegromare/DarkTheme
