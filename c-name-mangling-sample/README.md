# C name mangling

Questa cartella include del semplicissimo codice sorgente per sperimentare con le modalità di interfacciamento del codice C ed il sistema di “name mangling” del proprio compilatore C.

Il codice è suddiviso nella “libreria” (```divide.c``` e ```divide.h```) e nel programma (```test.c```).

## Procedura

Per compilare la “libreria” è sufficiente lanciare il seguente comando:

```
gcc -c divide.c -o divide.a
```

Il codice di libreria, che non ha dipendenze esterne, verrà compilato nel file oggetto ```divide.a```. Non trattandosi di un file eseguibile, non sarà possibile eseguire il file.

Tuttavia è possibile andare ad esaminare il file compilato sfruttando ```objdump```. In particolare ```objdump -f divide.a``` ci darà informazioni di alto livello sul file, mentre ```objdump -t divide.a``` restituirà la _tabella dei simboli_ del file
Tale tabella dovrà contenere il riferimento all’unica funzione contenuta nel file compilato, ossia “divide”.
Il sistema di _name mangling_ di C è molto semplice, per cui generalmente il riferimento alla funzione comparirà con il nome originale nel codice sorgente. In altri linguaggi (come ad esempio C++) il sistema di _name mangling_ è più complesso (e dipende da altri fattori, come il compilatore utilizzato).

Per utilizzare il file di libreria, sarà necessario compilare il programma d’esempio.
Il comando:

```
gcc test.c -o test
```

restituirà un errore perché il compilatore (nella fase di _linking_ in particolare) non riuscirà a trovare il simbolo “divide”, che sappiamo essere incluso nel file oggetto ```divide.a```.
Sarà sufficiente aggiungere il file oggetto con il simbolo richiesto come file di input:

```
gcc test.c divide.a -o test
```

A questo punto dovremmo ottenere un file eseguibile ```test``` che possiamo eseguire.

Possiamo inoltre analizzare anche il file eseguibile, con il comando ```objdump -f test``` (notare le differenze col file oggetto ```divide.a```) e con il comando ```objdump -t test``` (notare la presenza di molti più simboli, presi dal runtime C e dalla combinazione di programma e libreria) o con il comando ```objdump -T test```.
L’ultimo comando in particolare elenca la presenza di simboli che vengono “risolti” dinamicamente a runtime, ossia a tempo di esecuzione del programma (come ad esempio la funzione di libreria ```printf```, che non sarà inclusa staticamente nel programma durante la compilazione, ma che verrà invocata direttamente nella libreria C).
