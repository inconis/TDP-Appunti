---
title: "Configurazione di Eclipse"
description: Operazioni preliminari
date: '2020-04-26'
---
***
In questa pagina elenco le operazioni preliminari da svolgere per poter visualizzare correttamente la parte grafica nel software Eclipse

La procedura cerca di seguire l'ordine dei files nei progetti importati.

###1. Nel file `EntryPoint.java` sovrascrivere la classe `start`
``` Javascript
@Override
    public void start(Stage stage) throws Exception {
        
    	FXMLController controller;
    	
    	FXMLLoader loader = new FXMLLoader(getClass().getResource("/fxml/Scene.fxml"));
        Parent root = loader.load();
        Scene scene = new Scene(root);

        controller = loader.getController();
    	
        /*
		 * Create and set the model here!
		 */
		// controller.setModel();
        Model model = new Model();
        controller.setModel(model);
        
        stage.setTitle("JavaFX and Maven");
        stage.setScene(scene);
        stage.show();
    }
```



###2. Nel file `FXMLController.java` aggiungere quanto segue
Il file deve essere precedentemente impostato [seguendo questa guida](/Configurazione_iniziale/SceneBuilder/) 
``` Javascript
public class FXMLController {
	private Model model;
[...]
 public void setModel(Model model) {
	    	this.model = model;
	    	configurazioneIniziale();
	    }
 private void configurazioneIniziale(){
            //Operazioni preliminari
        }
}


```