---
theme: academic
layout: intro
highlighter: shiki
lineNumbers: false
transition: slide-left
colorSchema: 'light'
title: 'How shall a machine call a thing?'
titleTemplate: '%s - Federico Torrielli'
drawings: 
  syncAll: false
---

<style>
    mark {
      background-color: #ffb703;
      color: black;
      border-radius: 0.25rem;
    }
</style>

<h1 style="font-size: 50px">How shall a machine call a thing?</h1>

Exploring Basicness in Language through Attention-based Neural Networks and Human-in-the-Loop Methodology

<center>
  <a href="https://torrielli.netlify.app">
    <img src="/images/logo_unito_new.png" class="w-auto" style="height: 60px"/>
  </a>
</center>

<div class="absolute bottom-10">
  <span class="font-700">
    Federico Torrielli, 14/04/2023
  </span>
</div>

<div class="absolute right-10 bottom-10">
  <span class="font-600">
    <b>Relatore</b>: <i>Prof. Luigi Di Caro</i>
    <br>
    <b>Contro-relatore</b>: <i>Prof. Valerio Basile</i>
  </span>
</div>

<a href="https://torrielli.netlify.app">
  <img src="/images/qrcode.png" style="position: absolute; float: right; top: 30px; right: 30px; width: 13%">
</a>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: center
---

# Introduzione

Il linguaggio è la <mark>**proprietà evolutiva**</mark> che primariamente ci differenzia da qualsiasi altro animale.

Solo grazie ad esso riusciamo a comunicare, costruire relazioni e creare comunità che ci hanno permesso di fare un considerevole salto evolutivo.

La stessa azione del comunicare è considerevole e sottovalutata: ci permette (non ironicamente!) di **leggere nelle menti** altrui.


---
layout: center
---

# Il vocabolario

Il vocabolario è il cuore pulsante della nostra lingua, **l'elemento comune** a qualsiasi dialetto.

Gli umani hanno un'ottima capacità di comunicare grazie a <mark>**set di lessemi**</mark> ed espressioni linguistiche che solitamente sono organizzate tramite <mark style="background-color: #219ebc">**strutture gerarchiche**</mark>:

- Super-ordinate: categorie **inclusive**, generali, ampie
- Subordinate: categorie *specifiche* fatte di relazioni **iponimiche** con le precedenti

---
layout: center
---

# Basic/Advanced Level

Nel contesto sovracitato si colloca la <mark>**nozione psico-linguistica**</mark> del *basic level*, ciò che, secondo la letteratura, possiede le seguenti caratteristiche:
- Livello *ottimale* di **economia cognitiva**
- Alto livello di **class-inclusion**
- Mediamente **generale**, culturalmente comune e *saliente*

---
layout: center
---
# Contributi della tesi

Indentificazione di termini <mark>*basic/advanced* + *concrete/abstract*</mark> tramite due approcci computazionali:

- <mark style="background-color: #fb8500">Approccio **testuale**</mark>: un large language model pre-addestrato e utilizzato generativamente
- <mark style="background-color: #219ebc">Approccio **multi-modale**</mark>: una pipeline *text+image* che sfrutta reti neurali multi-modali stato dell'arte.

Inoltre, un ulteriore contributo è la creazione di un dataset di 500 parole *basic* e *advanced* esemplari grazie ad un *panel* di **dieci annotatori** language-learners e la **definizione** della nozione di <mark style="background-color: #023047; color: white">**basicness**</mark>, basandosi sulla letteratura esistente sulla *concreteness*

---
layout: two-cols
---
# How shall a thing be called? (1958)

<br><br><br><br>

Roger Brown pone una *domanda* fondamentale: 

> Come facciamo a scegliere un <mark>**termine appropiato**</mark> per un **concetto** scelto?

::right::

<img src="/images/brown-shall.jpg">

---
layout: two-cols
---

# Il basic di Brown

Individua **4 caratteristiche fondamentali** che devono condividere le parole basic:

- Brevi
- Concrete
- Facili da pronunciare
- Frequentemente utilizzate tra le disponibili per un certo concetto

::right::

# Il nostro basic

<v-clicks>

- Strumenti per la **sopravvivenza sociale**
- Brevi, facili da pronunciare *verbalmente* e da concettualizzare
- Le **prime parole** che vengono alla mente quando si parla di un certo *topic*
- Facilmente traducibili in una **chiara immagine mentale**

</v-clicks>
---
layout: two-cols
---

# Basic

- House, Book, Chair, Table
- Orange, Apple
- Dog, Cat
- Thing, Fact
- Justice, Fun

::right::

# Advanced

- Mansion, Novel, Recliner, Board
- Tangerine, Granny Smith
- Chihuahua, Maine coon
- Artifact, Evidence
- Reprisal, Amusement

---
layout: center 
transition: slide-up
---
# Utilizzo del basic level

- Utili per chi **impara una nuova lingua**: comprensione, produzione e conversazione
- Utilizzo nella **UI** di un prodotto
- Utilizzo in **automatic recommenders**, generatori di **sommari** ed **information extraction**
- Utilizzo per **text simplification** al fine di trattare *DSA* come la  *Dislessia*

---
layout: cover
coverDate: ''
---

<div style="position: absolute; height: 100%; width: 100%; margin: 0; padding: 0; top: 0; left: 0;">
  <img src="/images/attention.png" style="height: 100%; width: 100%;">
  <div class="bottom-10" style="position: absolute; left: 20px; background-color: white; padding: 20px; border-radius: 10px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);">
    <h1 style="color: black; text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);">Task sul livello testuale</h1>
    <p style="color: black; text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);">OPT</p>
  </div>
</div>

---
layout: center
---

# Text-Based Pipeline

La prima pipeline utilizza *OPT*, un large language model generativo <mark>**transformer-based**</mark>.

<center>
  <img src="/images/OPT-pipeline.png" style="width: 60%"/>
</center>

---
layout: two-cols
---

# Transformers

Rete neurale basata su uno <mark>stack **encoder-decoder**</mark>, adatta per dati di tipo testuale.

- **Encoder**: processa la sequenza di input (una serie di token) e restituisce **embeddings** (una rappresentazione contestuale verso il decoder) utilizzando layer di <mark style="background-color: #fb8500">**self-attention**</mark>, **normalization** e **FFN**.
- **Decoder**: prende gli embeddings in input e ha come output finale una <mark style="background-color: #219ebc">distribuzione probabilistica</mark> sul singolo token.

<center>
  <img src="/images/Transformer_decoder.png" style=""/>
</center>

::right::

<center>
  <img src="/images/transformer-architecture.png" style=""/>
</center>

---
layout: center
---

# Architettura OPT

Suite di decoder-only pre-trained transformers: architettura <mark>**auto-regressiva**</mark> semplice, composta solo da decoder impilati. Utilizzato unicamente per scopi **generativi**.

<center>
  <img src="/images/opt-decoder-only.png" style="width: 50%"/>
</center>

---

# I LLMs sono Next Token Predictors

- **Obiettivo**: <mark>prevedere il **token successivo**</mark> in una sequenza di parole, migliorando la coerenza e la comprensione del testo generato
- **Funzionamento**:
  - Viene utilizzata la *multi-headed attention* per catturare informazioni da contesti diversi
  - Calcola la **probabilità** di ciascun token candidato nel **vocabolario**
  - <mark style="background-color: #fb8500">Seleziona il token con la **probabilità più alta**</mark> come previsione successiva

<br><br>
<div style="text-align: center;">
  <v-clicks>
  <div style="display: inline-block; width: 100px; height: 100px; margin: 10px;"><mark style="background-color: #0077b6;">Federico</mark></div>
  <div style="display: inline-block; width: 100px; height: 100px; margin: 10px;"><mark style="background-color: #0096c7">prenderà</mark></div>
  <div style="display: inline-block; width: 80px; height: 100px; margin: 10px;"><mark style="background-color: #00b4d8">come</mark></div>
  <div style="display: inline-block; width: 80px; height: 100px; margin: 10px;"><mark style="background-color: #48cae4">voto</mark></div>
  <div style="display: inline-block; width: 70px; height: 100px; margin: 10px;"><mark style="background-color: #90e0ef">di</mark></div>
  <div style="display: inline-block; width: 60px; height: 100px; margin: 10px;"><mark style="background-color: #ade8f4">laurea</mark></div>
  <div style="display: inline-block; width: 70px; height: 100px; margin: 10px;"><mark style="background-color: #caf0f8">...</mark></div>
  </v-clicks>
</div>

---
layout: center
---

# Come classificare con un modello generativo?

- **Creazione** di una *basic raw list*
- **Filtraggio** tramite *OPT*
- **Estrazione** di termini Advanced
- **Raffinamento** del dataset finale

---

# Creazione della basic raw list

- **Input**: termini estratti da liste di termini *semplici* (e.g. Ogden) e da testi di language-learners su Reddit
- **Output**: set iniziale di termini da *filtrare* usando **OPT** e, contemporaneamente, i loro synset associati (*best-frequency*) per l'estrazione di **advanced**

<center>
  <br><br>
  <img src="/images/raw_list_creation.drawio.png" style="width:60%">
</center>

---

# Filtraggio tramite OPT

- **Input**: il set iniziale di termini
- **Output**: una lista di parole **OPT-basic**

<center>
  <br><br>
  <img src="/images/OPT-diagram.drawio.png" style="width:70%">
</center>

---

# Estrazione di termini advanced

Partendo dai synset basic vengono fatti controlli:

- Frequenza significativa in **SemCor**, *un corpus annotato*
- **Path Distance** appropriata
- **Nessuna parola condivisa** tra il *synset* e l'*iponimo*
- Non devono esserci parole basic nella advanced list

<center>
  <br><br>
  <img src="/images/advanced-list-diagram.drawio.png" style="width:70%">
</center>

---
transition: slide-up
---

# Dataset fine-tuning

Vegono prodotti **500 termini**, 250 sono *OPT-basic* e 250 sono *OPT-advanced*.
Le due liste (basic+advanced) vengono **combinate**, **filtrate** per rimuovere *parole offensive* o dannose, selezionate in base alla loro **frequenza** e poi **mischiate** per produrre il dataset finale da somministrare agli utenti.

<center>
  <br><br>
  <img src="/images/dataset-fine-tuning-diagram.drawio.png" style="width:80%">
</center>

---
layout: cover
coverDate: ''
---

<div style="position: absolute; height: 100%; width: 100%; margin: 0; padding: 0; top: 0; left: 0;">
  <img src="/images/collage_ba.png" style="height: 100%; width: 100%;">
  <div class="bottom-10" style="position: absolute; left: 20px; background-color: white; padding: 20px; border-radius: 10px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);">
    <h1 style="color: black; text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);">Task sul livello visivo</h1>
    <p style="color: black; text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);">stableKnowledge</p>
  </div>
</div>

---

# Pipeline multi-modale

- *text-to-image*: **Stable Diffuson**
- *image-to-text*: **BLIP**
- *semantic text evaluation*: **SBERT**

<center>
  <br><br>
  <img src="/images/SD-pipeline.png" style="width:70%">
</center>

---

<center>
  <img src="/images/stableknowledge-architecture.drawio.png" style="width: 50%">
</center>

---
layout: center
---

# Come mai abbiamo bisogno del livello visivo?

**Ipotesi**: un sistema che possiede l'abilità di riconoscere l'informazione <mark>dal livello testuale al livello visivo (e viceversa)</mark>, ha una <mark style="background-color: #fb8500">conoscenza profonda</mark> del suo contenuto, in maniera similare a come l'uomo conosce il mondo.

---

# Generare immagini

- Viene utilizzata la **diffusione**: un <mark>processo a doppia passata</mark> per allenare modelli a partire da enormi dataset di immagini
  - <mark style="background-color: #fb8500">**Forward pass**</mark>: viene *distrutta* la struttura dei dati aggiungendo del **rumore Gaussiano** all'immagine attraverso una *catena di Markov*. I dati vengono *assorbiti* nello spazio latente.
  - <mark style="background-color: #219ebc">**Backward pass**</mark>: si cerca di re-imparare i dati di origine andando a progressivamente **rimuovere il rumore dalle immagini**, navigando nello spazio latente e generando nuovi dati


<center>
  <br><br>
  <img src="/images/denoising.png" style="width:70%">
</center>

---
layout: center
---

<center>
  <video controls>
    <source src="/videos/castle-animation.mp4" type="video/mp4">
    <source src="/videos/castle-animation.webm" type="video/webm">
    Your browser does not support the video tag.
  </video>
</center>

---

<center>
  <img src="/images/stable-diffusion-diffusion-process.png" style="">
</center>

---

# Interrogare immagini

Viene utilizzato **BLIP**, un sistema multi-modale capace di <mark>generare delle descrizioni</mark> delle immagini presentate. Gli autori del paper hanno scelto di utilizzare un **ViT** (Vision Transformer) e un **MED** (Multi-modal mixture of Encoder-Decoder).

- **ViT**: scompone l'immagine di partenza in **features** e trasforma le features in una sequenza di **embeddings**
- **MED**: produce degli stati dati in pasto ad un Transformer, che fa **image captioning**. MED opera come **Unimodal Encoder** (ITC Loss) e **Image-grounded text enc/decoder** (ITM+LM Loss)

Secondo gli autori BLIP è "*an unholy concoction of many different things, in one, trained jointly*"

---
layout: center
---

# Valutare immagini

Valutiamo se <mark>la descrizione si avvicina al lemma originale</mark> utilizzando **SBERT**, una rete *siamese* (due reti identiche in training, comparate in testing) BERT-based che utilizza un layer di *pooling* per generare degli **embeddings** utilizzati per <mark style="background-color: #fb8500">confrontare testi in uno spazio semantico</mark> utilizzando la **cosine-similarity**.

Abbiamo costruito un componente *custom* per adattare il task di classificazione selezionato

---
layout: center
---

# Classificazione

Una volta raccolte le *cosine-similarities* di tutte le immagini, si fa un <mark>**threshold sweep**</mark> per verificare quale sia il limite superiore di classificazione. 

*e.g.*: se $x$ è il threshold, allora: $\forall y<x, y$ basic, advanced altrimenti.

<center>
  <img src="/images/complete-screen.png" style="width: 50%">
</center>

---

# Il task di annotazione

Per comparare i dati classificati dai metodi automatici con uno **standard** abbiamo creato un tool personalizzato e sottoposto <mark>**10 second-language-learners**</mark> al task di annotazione di **basic vs. advanced** sulle *500 parole*.

Tra i dati interessanti raccolti menzioniamo:

- Statistiche sul **tempo**
- Parole classificate come **difficili da annotare**
- **Agreement** tra gli annotatori

---

<center>
  <img src="/images/page4.png" style="width: 60%; box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.5); border-radius: 10px;">
  <br><br><hr><br><br>
  <img src="/images/page5.png" style="width: 20%; box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.5); border-radius: 10px;">
</center>

---

# Agreement tra gli annotatori

Abbiamo ottenuto un **alto** inter-annotation agreement, misurato con il <mark>Coefficiente *k* di **Cohen**</mark>, la cui formula è 

$$k=\frac{p_o-p_e}{1-p_e}$$

Dove:

- $p_o$ è l'agreement osservato relativo tra gli annotatori
- $p_e$ è la probabilità ipotetica di agreement *casuale*

Si misura in una scala che va da **0** (nessun agreement) a **1** (agreement perfetto).

<center>
  <img src="https://www.statology.org/wp-content/uploads/2021/02/kappa1-300x229.png" style="width:5cm">
</center>

---
layout: cover
coverDate: ''
---

<center>
  <h1>0.71</h1>
  <b>agreement</b> tra annotatori, che indica un task con <mark><b>ottime guidelines</b></mark>
</center>

---
layout: two-cols
---

# Fatti interessanti

- Gli annotatori hanno impiegato <mark>più tempo (*80% in più*) a valutare parole basic</mark> piuttosto che quelle advanced
- Il tempo medio è stato di **1.40 secondi**
- Le parole più difficili da classificare sono state:
  - Parole composte da più basic: **vitamin pill**
  - Parole prese da altre lingue: **avenue**
  - Parole corte ma con un significato complesso: **kin**

::right::

<center>
  <br><br><br><br><br><br>
  <img src="/images/time_spent_on_annotations.png">
</center>

---
layout: two-cols
transitions: slide-up
---

# Basicness

<br><br><br><br>

Dalle analisi è risultato che la classificazione **basic vs. advanced** non è una **proprietà binaria**, ma deve essere posizionata su una scala misurabile.

Da questa ipotesi è nata la **basicness**, una misura similare alla *concreteness* che <mark>segnala quanto è basic un certo termine</mark>, basandosi sullo **split** nell'annotazione del lemma stesso.

::right::

<center>
  <br><br><br><br><br><br><br><br><br>
  <img src="/images/basicness.png" style="width:50%">
</center>

---

# Risultati sul task basic vs. advanced

<br><br><br><br>
<center>
  <img src="/images/table_basicadvanced.png" style="width: 60%">
</center>

---

# Una scoperta interessante

Investigando sui dati raccolti abbiamo scoperto che <mark>**termini basic e concreti sono meglio riconosciuti dal livello testuale**</mark>.

Questo ci ha portato a ipotizzare che l'**image level** fosse più adatto a classificare la **concreteness**.

<v-click>

L'ipotesi è stata confermata dal nostro *secondo esperimento*: <mark style="background-color: #fb8500">**concrete vs. abstract**</mark>

- Presa una lista di concetti dal database di **MRC**, con score **[0, 700]**
- Classificati tutti i sostantivi nella lista con i nostri due metodi (con fine-tuning sulla concreteness)
- Analizzati i risultati

</v-click>

---

# Risultati sul task concrete vs. abstract

<br><br>
<center>
  <img src="/images/table_concreteabstract.png" style="width: 60%">
</center>

Questi risultati indicano che quando si tratta di differenziare concetti concreti da astratti, <mark>i due metodi performano **al contario**</mark> rispetto al task precedente!

<v-click>

L'origine di questa discrepanza è nell'architettura e nel **training set** dei modelli utilizzati:

- OPT è **text-based**, ovvero, addestrato in maniera supervisionata su enormi quantità di dati testuali
- SD è **image-based**, ovvero, addestrato su **immagini** e **captions**

</v-click>

---

# Sum-up

- Proposta una nuova nozione di **"basicness"** ispirata alla letteratura sulla concreteness
- Creata un'ampia **wordlist inter-categoria** di parole basic/advanced
- Sviluppata una metodologia **human-in-the-loop** con 10 annotatori con *alto agreement*
- Creati metodi per la classificazione di elementi terminologici utilizzando reti neurali stato dell'arte per **CV** e **NLP**
- Mostrata una pipeline image-based che combina **text-to-image** e **image-to-text** per scopi NLP, novità assoluta in letteratura

---

# Conclusione: Future Work

- **Scoperte secondarie**: Gli approcci basati su immagini funzionano meglio per i termini concreti e astratti ma non per la classificazione basic/advanced. È stata formulata un'ipotesi ma sono necessarie ulteriori ricerche.
- Le pipeline multimodali potrebbero migliorare gli attuali Large Language Model che replicano solo la **rete linguistica** e mancano di vera intelligenza. Le affermazioni secondo cui i LLMs hanno proprietà umane come la Teoria della Mente richiedono un esame critico.
- Alcune immagini generate hanno mostrato una **qualità "uncanny"** che richiede ulteriori approfondimenti per risolvere il problema mantenendo un'alta qualità.

---

# Sidenote Finale

- I ricercatori dovrebbero avere una <mark>prospettiva equilibrata</mark> sui LLMs e sugli LDMs. Non dovrebbero essere temuti, glorificati o eccessivamente pubblicizzati. Sono strumenti per aiutare gli umani ma non sono intelligenti o in grado di pensare o immaginare come gli umani. Un'enfasi eccessiva potrebbe portare a un nuovo **"AI Winter"**
- Sebbene le aziende promuovano i progressi nell'AI, le università dovrebbero competere con loro per <mark style="background-color: #fb8500">promuovere modelli aperti</mark> e ricerche per una vera apertura. La ricerca condotta solo dalle aziende potrebbe mancare della <mark style="background-color: #219ebc">necessaria trasparenza e collaborazione</mark> per condividere i risultati con la comunità di ricerca in generale.

---
layout: cover
coverDate: ''
---

<div style="position: absolute; height: 100%; width: 100%; margin: 0; padding: 0; top: 0; left: 0;">
  <video autoplay loop muted style="height: 100%; width: 100%;">
    <source src="/videos/final-background.mp4" type="video/mp4">
    <source src="/videos/final-background.webm" type="video/webm">
    Your browser does not support the video tag.
  </video>
  <img src="/images/qrcode.png" style="position: absolute; float: right; top: 30px; right: 30px; width: 20%">
  <div class="bottom-10" style="position: absolute; left: 20px; background-color: white; padding: 10px; border-radius: 10px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);">
    <h1 style="color: black; text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);">Grazie per l'attenzione</h1>
  </div>
</div>