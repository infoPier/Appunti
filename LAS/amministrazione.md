---
title: AMMINISTRAZIONE DI SISTEMI
author: Pierluca Pevere
geometry: margin=2.5cm
include-headers: |
    \usepackage{graphicx}
---

```{=latex}
\begin{center}
```

![](copertina.jpg)

```{=latex}
\end{center}
```

# FUNZIONAMENTO DEL SISTEMA

## GESTIONE DEI PACCHETTI SOFTWARE

Ogni pacchetto software ha un ciclo di vita composto da:

1. installazione
2. aggiornamento
3. disinstallazione

Si possono però riscontrare porblematiche, ad esempio: prerequisiti hardware o di sistema operativo, dipendenze da o di altri componenti software oppure la configurazione.\
\

### INSTALLAZIONE MANUALE

L'installazione manuale di pacchetti software può avvenire:

* da binari:
    - semplice copia nei posti giusti
    - verificare manuale della compatibilità con l'architettura
    - verifica manuale delle dipendenze

* da sorgente:
    - necessità di compilazione
    - indipendenza dall'architettura
    - possibile maggior flessibilità nel soddisfacimento delle dipendenze

    più frequente e migliore rispetto alla precedente perchè si compila su una determinata architettura e non si è vincolati a quella presente sul computer che ha compilato il binario

Un aspetto importante sono le **dipendenze** del componente software da altri.\
Nel caso di un'installazione da binari, probabilmente è necessario disporre dei software indicati come prerequisiti in una **versione specifica.\
Nel caso di installazione da sorgente qualche grado di flessibilità in più lo si ha. Infatti vi è la possibilità che i sorgenti dispongano di diverse interfacce per adeguarsi a cosa si trova sul sistema. C'è però la necessità di disporre non solo dei componenti runtime relativi ai software richiesti, ma anche delle librerie di sviluppo: in un sistema ideale ho tutti i sorgenti per cui dispongo sempre di tutti questi elementi. Nelle distribuzioni, per flessibilità, ogni pacchetto software ha un corrispondente paccetto `-dev` o `-devel`

#### Installazione manuale tipica in Linux

\
Il caso più comune è quello di software distribuito per mezzo di un archivio `.tar.gz`, scritto in C, predisposto alla compilazione tramite il framework `autoconf`.\
`autoconf` verifica se sono soddisfatti tutti i prerequisiti, rileva le versioni e le collocazioni dei pacchetti sul sistema, accetta dall'utente la specifica di varianti (attivazione/disattivazione di funzionalità, preferenze architetturali, ...), genera i `Makefile` sulla base delle specificità del sistema e delle scelte operate dall'utente.\
\newpage
I passi tipici sono:

1. reperimento del software
2. estrazione del pacchetto
3. esame delle scelte disponibili
4. configurazione dei sorgenti
5. compilazione
6. installazione

**N.B.**: solo quest'ultima operazione può richiedere i diritti di superutente, e quindi si deve evitare di compiere le precedenti come root. Sono noti casi di malware che sfruttano proprio la cattiva abitudine di eseguire una o più delle operazioni preliminari con diritti eccessivi.

#### Autenticazione

La PRIMA cautela da usare quando si scarica software dovrebbe essere quella di verificarne l'autenticità da una firma digitale, ovviamente server una chiave pubblica fidata per compiere questa operazione.\
Un esempio può essere:

```bash
# mostra il key id
gpg --verify FILE.asc FILE.tar.gz
# l'autenticità della chiave in questo caso deriva solo dalla fonte (a volte non basta)
gpg --keyserver pgpkeys.mit.edu --recv-key <KEY_ID>
# si deve valutare caso per caso, successivamente si ripete il primo comando
```

Come minimo dovrebbe essere disponibile un fingerprint.\
Basta mettere il fingerprint (ad esempio in formato `.sha256`) nella stessa directory del file da verificare e lanciare

```bash
sha256 -c FILE.sha256
```