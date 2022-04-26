### Otobo

E' possibile trovare la guida di installazione di Otobo nella documentazione del progetto a questo link:

https://doc.otobo.org/manual/installation/10.1/en/content/installation-docker.html



### Configurazione custom
	
Nel contesto della messa in opera nell'infrastruttura Saas	non è stata seguita la documentazione del progetto, 
in quanto gli sviluppatori eseguono la messa in opera del servizio mediante l'utilizzio di alcuni docker-compose.yml 
Custon contenuti nella cartella docker-compose.

Al fine di eseguire il deploy su Saas è stato creato un file docker-compose.yml di cui una copia si trova in questo repo.
E che permette il normale deploy dell'applicazione con SWARM.

### Elenco volumi statici

Redis

    redis_data:/data


Elastisearch

    elasticsearch_data:/usr/share/elasticsearch/data

Otobo

    opt_otobo:/opt/otobo


Database (mariadb)

    mariadb_data:/var/lib/mysql

### Configurazione custom per DEV

Nel caso dello stack DEV è stata aggiunta una network diversa otobo-dev-net (invece di otobo-net)
e sono stati cambiati i nomi dei servizi nel docker-compose.yml aggiungento il suffisso -dev (es.
db-dev), per differenziarli da quello di Produzione (risolvento un problema di routing di Traefik).

Questa modifica va riportata nel file "Config.pm" nel folder "opt_otobo/Kernel".

In questo file è riportato l'hostname con cui vengono richiamati i servizi nella rete docker, quindi
se i nomi vengono modificati del docker-compose.yml, poi devono essere modificati anche in questo file
prima di inizializzare il deploy.
