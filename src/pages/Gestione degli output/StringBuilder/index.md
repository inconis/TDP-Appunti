---
title: "Funzionamento di StringBuilder"
description: Istruzioni base per string builder
date: '2020-04-26'
---
***

l’oggetto **String** è un oggetto immutabile, cioè, una volta creato, **non può essere modificato.** Di fatto, nel momento in cui modifichiamo un oggetto String, in Java, ne stiamo creando un’altra istanza, rimpiazzando quella precedente.
> Fonte: https://www.html.it/pag/18034/stringbuilder/

Viene indicato un esempio usato nella formattazione del testo nel [Lab04](https://github.com/TdP-2020/Lab04/blob/soluzione/Lab04_SegreteriaStudenti/src/main/java/it/polito/tdp/lab04/FXMLController.java#L99)
```Javascript
StringBuilder sb = new StringBuilder();

			for (Studente studente : studenti) {

				sb.append(String.format("%-10s ", studente.getMatricola()));
				sb.append(String.format("%-20s ", studente.getCognome()));
				sb.append(String.format("%-20s ", studente.getNome()));
				sb.append(String.format("%-10s ", studente.getCds()));
				sb.append("\n");
			}

			txtResult.appendText(sb.toString());
```
É possibile reperire qui tutte le funzioni relative alla classe [StringBuilder](http://www.falkhausen.de/Java-10/java.lang/String.html)

### Le informazioni relative all'impaginazione si trovano [qui](../Impaginazione%20testo)