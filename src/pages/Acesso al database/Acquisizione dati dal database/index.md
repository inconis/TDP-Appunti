---
title: "Come acquisire i dati dal database"
description: Istruzioni base per acquisire i dati dal database
date: '2020-04-26'
---
***
Per evitare l' SQL injection si utilizzano query parametrizzate in modo da poter inserire il valore preso in input direttamente come testo o numero.

Qui si trova un esempio di codice scritto **con** l'utilizzo del **connection pooling**

1. Creare un package denominato `db`
2. Creare una classe `DBconnect` in cui inserire i dati del database
3. Creare una classe per ogni tipologia di accesso al databse simile al seocno esempio 

##Classe `DBConnect` 
``` javascript 


import java.sql.Connection;
import java.sql.SQLException;
import com.zaxxer.hikari.HikariConfig;
import com.zaxxer.hikari.HikariDataSource;


public class DBConnect {
	private static final String jdbcURL = "jdbc:mysql://localhost/<nome tabella>";
	private static HikariDataSource ds;
	
	public static Connection getConnection() {
		if(ds == null) {
			HikariConfig config = new HikariConfig();
			config.setJdbcUrl(jdbcURL);
			config.setUsername("root");
			config.setPassword("rootroot");
			
			config.addDataSourceProperty("cachePrepStmts", true);
			config.addDataSourceProperty("prepStmtChacheSize", 250);
			config.addDataSourceProperty("prepStmtCacheSqlLimit", "2048");
			
			ds = new HikariDataSource(config);
		}
		
		try {
			return ds.getConnection();
		} catch (SQLException e) {
			System.err.println("Errore di connessione ad db");
			throw new RuntimeException(e);
		}
	}
}

```
##Classe `EntitaConnect` 

``` javascript
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;

public class DizionarioDAO {
	public List<String> listParola() {
		List<String> result = new ArrayList<>() ;
		####IMPOSTARE QUERY#####
		String query = "SELECT nome FROM parola WHERE parola=? ORDER BY nome" ;
		
		try {
			Connection conn = DBConnect.getConnection() ;
			PreparedStatement st = conn.prepareStatement(query) ;

			####IMPOSTARE PARAMETRI#####
			st.setString(1, anagramma);
			...
			############################


			ResultSet res = st.executeQuery() ;
			while(res.next()) {
				result.add(res.getString("nome")) ;
			}	
			res.close();
			conn.close();	
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		return result ;
	}
}
```