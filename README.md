Kubernetes I - Lab 01

Obiettivo del LAB: tirare su uno stack LAMP (es. wordpress)

Ognuno di voi lavorerà in un namespace diverso; ogni oggetto che creerete sul cluster sarà definito in uno yaml, compreso il namespace

Lo stack LAMP sarà così composto

 ● un namespace (a vostra scelta, purchè sia univoco nel cluster)
 ● deployment del pod che fornirà la parte di apache/php
   ○ avrà 2 repliche
   ○ la dir con i file php del sito sarà persistita su un PV rook (RWX, usiamo la storageClass corretta)
 ● deployment del mysql
   ○ la pwd di root andrà in un secret
   ○ opzionalmente la config (my.cnf) andrà in una configMap
   ○ la dir con i dati di mysql sarà persistita su un PV con access mode RWO
 ● service per il deployment di apache/php (sarà il service a cui punterà l'ingress)
 ● service per il mysql (sarà l'hostname del db a cui punterà wordpress, o altro CMS che sceglierete)
 ● ingress per esporre il sito all'esterno
   ○ l'hostname sarà nome-a-vostra-scelta.corso-k8s.replio.it (*.corso-k8s.replio.it punta già alla porta 80 dell'ingress controller del cluster)
	
Opzionalmente, definirete un kustomization.yaml per tirare su lo stack con unico comando (occhio alle pvc)
