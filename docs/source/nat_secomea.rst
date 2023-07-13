=============================================
kb131.10 - NAT rule for the SECOMEA TS-module
=============================================

Questa procedura descrive i passaggi per scrivere le regole di Forwarding nel
modulo Secomea 

Soluzione adottata
------------------

Collegare un cavo ETH dal PC ad una delle porte DEV del modulo Secomea e seguire
le istruzioni del documento ‘’ UM_A00168_03_I ‘’ (nello specifico da pagina 32)
per collegarsi al Link Manager. ( vedi Link in fondo )

Una volta collegati al Link Manager appare la seguente schermata:



Cliccare su Routing, esce la seguente schermata:

Cliccare su IP Aliases, esce la seguente schermata:



Per ogni nuovo indirizzo IP:
Nella voce ‘’ IP Address ‘ inserire i nuovi indirizzi IP che vogliamo
‘’agganciare’’ ai vecchi 

Nella voce ‘’ Interface ‘’ selezionare UPLINK

Cliccare Save


Aggiungere n agenti tanti quanti gli indirizzi IP che vogliamo ‘’agganciare’’
In questo esempio: 2



Nella voce ‘’ Device Type ‘’ selezionare CUSTOM ( advanced ) e Forwading per i
due campi









Nella voce ‘’ Device IP & Parameters ‘’ va inserita la regola di Forwarding,
per farlo:

Cliccare sull’icona dei dettagli ( vedi freccia immagine precedente ) per ciascun nuovo agente, 
esce la seguente schermata:


Use Case
^^^^^^^^

Inserire la regola nella prima riga

In questo esempio:
	•	SAW       =  $10.35.2.12:ANY:1-65535>>169.254.227.118:1-65535
	•	PULLER =  $10.35.2.11:ANY:1-65535>>169.254.227.119:1-65535

In generale, a sinistra l’indirizzo IP nuovo e a destra il vecchio:
$xxx.xxx.xxx.xxx:ANY:1-65535>>xxx.xxx.xxx.xxx:1-65535


La sezione degli agenti, dopo aver scritto le regole, si presenta così:



Verificare l’esito positivo di quanto fatto provando a ‘’pingare’’ i nuovi indirizzi IP.





Link utili:


Using the Custom > Forwarding and Routing ( Scada ) agents on Sitemanager

https://cdn.document360.io/88f49507-a7a0-4636-b297-13c4d0065310/Images/Documentation/Using%20the%20forwarding%20agent_V2.2.pdf?sv=2019-07-07&sig=bMNAIZyUsJDJ6tKzrO6V7jxxKlTNaZ6PVOMXlqwofYg%3D&spr=https%2Chttp&st=2023-03-10T07%3A27%3A42Z&se=2023-03-10T07%3A37%3A42Z&srt=o&ss=b&sp=r


**Documento UM_A00168_03_I**
