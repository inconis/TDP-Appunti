---
title: "Teoria del pattern MVC (Model – View – Controller)"
description: In questo articolo riassumo alcuni concetti teorici basilari del MVC
date: '2020-04-26'
---

Lo schema proposto dal **pattern MVC** è composto da:

-   **Model**: contiene i metodi di accesso ai dati. (Classi di tipo DAO)
-   **View**: si occupa di visualizzare i dati all’utente e gestisce l’interazione fra quest’ultimo e l’infrastruttura sottostante. (Interfaccia grafica - `Scene.fxml`)
-   **Controller**: riceve i comandi dell’utente attraverso il View e reagisce eseguendo delle operazioni che possono interessare il Model e che portano generalmente ad un cambiamento di stato del View. (`FXMLController`)

Negli esercizi che svolgo tutte le classi DAO effettueranno la ricerca nel databse e potranno essere interrogate **solo dal** `Model.java` che avrà tutte le classi necessarie affinchè venga interrogato **solo lui**

Il programma deve essere in grado di funzionare completamente in modalità testuale generalmente con il file `TestModel.java`

>Fonte https://www.html.it/pag/18299/il-pattern-mvc/