<script>
export default {
  name: "CarouselAssociazioni",
  data() {
    return {};
  },
  methods: {
    onSlideStart(slide) {
      this.sliding = true;
    },
    onSlideEnd(slide) {
      this.sliding = false;
    },
  },
  watch: {},
};
</script>

<template>
  <div>
    <b-carousel
      id="carousel-1"
      v-model="slide"
      :interval="4000"
      controls
      indicators
      background="transparent"
      variant='dark'
      img-width="1024"
      img-height="480"
      style="text-shadow: 1px 1px 10px black;text"
      @sliding-start="onSlideStart"
      @sliding-end="onSlideEnd"
    >
      <!-- Text slides with image -->
      <b-carousel-slide
        img-src="./static/imgs/back.jpeg"
        class="w-100"
        alt="image"
        style="height: 30rem"
        ><b-img src="./static/imgs/logofidc.png" style="width: 5rem"></b-img>
        <p class="carousel-text">
          FIdC è una delle associazione storica dei cacciatori Italiani, nata
          nel gennaio del 1900 e riconosciuta con D.L. del settembre del 1928.
          La FIdC elabora indirizzi generali per la gestione del territorio e
          della fauna selvatica, per lo svolgimento della attività venatoria,
          promuove la caccia e tutela gli interessi dei cittadini cacciatori.
          Per tali fini la Fidc aderisce alle associazioni venatorie europee ed
          internazionali. La Federazione promuove l’educazione naturalistica e
          venatoria del cittadino cacciatore e sviluppa attività formativa per
          favorire la crescita culturale e professionale dei propri associati,
          inoltre sviluppa iniziative di tutela ambientale ed ecologica e di
          vigilanza sulle acque interne anche in collaborazione con altre
          associazioni venatorie, agricole ed ambientaliste, svolge attività di
          protezione civile quali l’azione antincendio e la prevenzione del
          bracconaggio, provvede alla organizzazione delle attività sportive
          (cinofilia e tiro) e promuove la ricerca e gli studi scientifici. La
          federazione non persegue scopi di lucro.
        </p>
        <h3 class="carousel-pg">Federcaccia</h3>
        <h6 class="carousel-src">
          Visita il
          <a href="https://www.federcaccia.org">sito</a>
        </h6></b-carousel-slide
      >

      <b-carousel-slide
        img-src="./static/imgs/back.jpeg"
        class="w-100"
        alt="image"
        style="height: 30rem"
        ><b-img src="./static/imgs/logo-anlc.png" style="width: 5rem"></b-img>
        <p class="carousel-text">
          L’associazione venatoria Libera Caccia è nata nel 1959 ed è stata
          riconosciuta dal Ministero dell’Interno e Ministero Agricoltura e
          Foreste nel 1968. Oggi conta 18 Sedi Regionali, 99 Sedi Provinciali e
          3450 Sedi Comunali. ANLC promuove: la difesa della libertà di caccia,
          di pesca e delle attività connesse; l’organizzazione dei cacciatori,
          dei pescatori e la tutela dei loro legittimi interessi; la gestione
          del territorio e della fauna selvatica finalizzata all’esercizio
          dell’attività venatoria; la collaborazione in campo tecnico
          organizzativo della caccia con gli organi dello Stato, delle Regioni e
          degli Enti Locali; l’assistenza ai soci organizzati con provvidenze
          tecniche e normative; la divulgazione fra i cacciatori ed i pescatori
          delle varie conoscenze tecniche, di quelle venatorie e di quelle
          lietutiche; la promozione ed il finanziamento delle iniziative atte a
          migliorare l’immagine associativa ed rendere più proficuo l’esercizio
          venatorio, la pesca e tutte le altre attività previste nel comma 1°;
          l’organizzazione delle gare, mostre, esposizioni ed altre
          manifestazioni di carattere venatorio ed ittiche e quelle meglio
          specificate nel programma allegato al presente Statuto, che ne fa
          parte integrante.
        </p>
        <h3 class="carousel-pg">A.N.L.C.</h3>
        <h6 class="carousel-src">
          Visita il
          <a href="https://www.anlc.it">sito</a>
        </h6></b-carousel-slide
      >

            <b-carousel-slide
        img-src="./static/imgs/back.jpeg"
        class="w-100"
        alt="image"
        style="height: 30rem"
        ><b-img src="./static/imgs/Logo-Enelcaccia.png" style="width: 5rem"></b-img>
        <p class="carousel-text">
ENALCACCIA è un’associazione venatoria riconosciuta dal Ministero dell’Agricoltura e Foreste con D.M. il 20 marzo 1968, ed ha lo scopo di propagandare e promuovere attività sociali, sportive, culturali, artistiche, turistiche ed assistenziali, come mezzi di formazione fisica e morale dei soci, con particolare riguardo all’attività venatoria, alla pesca sportiva, al tiro, alla cinofilia, alla protezione civile ed alla difesa ambientale.

Dalla sua costituzione L’Enalcaccia ha aderito allo C.S.A.IN. (Centri Sportivi Aziendali ed Industriali), ente di promozione sportiva e di assistenza sociale, del quale è parte organica in qualità di Associazione specialistica. ENALCACCIA è la sola struttura sopravvissuta allo scioglimento dell’Ente Assistenza Lavoratori (ENAL).
        </p>
        <h3 class="carousel-pg">Enalcaccia</h3>
        <h6 class="carousel-src">
          Visita il
          <a href="https://www.enalcaccianazionale.it">sito</a>
        </h6></b-carousel-slide
      >

            <b-carousel-slide
        img-src="./static/imgs/back.jpeg"
        class="w-100"
        alt="image"
        style="height: 30rem"
        ><b-img src="./static/imgs/Logo-Arci-Caccia-220x150.png" style="width: 5rem"></b-img>
        <p class="carousel-text">
ARCI CACCIA è un’associazione venatoria, riconosciuta con D.M. del 2/2/1974 che opera senza fini di lucro. Impegnata nella conservazione dell’ambiente, difende e riafferma i valori della Costituzione repubblicana. Si giova dell’apporto volontario dei propri soci ed è organizzata su base regionale.

L’Associazione autonoma, indipendente e pluralista è aperta all’adesione di tutti coloro che si riconoscono nello Statuto. E’ federata all’ARCI e consente ai propri soci di usufruire dei benefici connessi al riconoscimento ufficiale della Federazione ARCI. Opera per tutelare i diritti dei propri associati, assisterli e fornire loro, a titolo gratuito, i servizi utili al migliore svolgimento dell’attività venatoria e delle attività sportive, nel rispetto delle norme nazionali ed europee; si ispira agli ideali della solidarietà e del mutualismo.
        </p>
        <h3 class="carousel-pg">Arci Caccia</h3>
        <h6 class="carousel-src">
          Visita il
          <a href="https://www.arcicaccia.it">sito</a>
        </h6></b-carousel-slide
      >

                  <b-carousel-slide
        img-src="./static/imgs/back.jpeg"
        class="w-100"
        alt="image"
        style="height: 30rem"
        ><b-img src="./static/imgs/Logo-Anuu.png" style="width: 5rem"></b-img>
        <p class="carousel-text">
L’ANUU è stata costituita il 28 marzo 1958 a Bergamo, per lo studio, la tutela e la conservazione delle cacce tradizionali italiane agli uccelli migratori. Lo scopo fondamentale dell’associazione era, ed è tutt’oggi, quello di garantire una gestione corretta e scientifica dell’attività venatoria, nel rispetto delle tradizioni cinegetiche del nostro Paese e attraverso un prelievo razionale delle risorse faunistiche, da realizzarsi tramite censimenti, rigorosi piani di utilizzo sostenibile ed accurata gestione del territorio.

A livello comunitario aderisce alla FACE/Federazione delle Associazioni dei Cacciatori e per la Conservazione della Natura dell’UE e all’AECT/Associazione europea delle cacce tradizionali, mentre a livello internazionale è membra del CIC/Consiglio Internazionale della Caccia e della Salvaguardia della Fauna.
        </p>
        <h3 class="carousel-pg">ANUU</h3>
        <h6 class="carousel-src">
          Visita il
          <a href="https://www.anuu.it">sito</a>
        </h6></b-carousel-slide
      >


                  <b-carousel-slide
        img-src="./static/imgs/back.jpeg"
        class="w-100"
        alt="image"
        style="height: 30rem"
        ><b-img src="./static/imgs/italcaccia-logo.png" style="width: 5rem"></b-img>
        <p class="carousel-text">
E’ nata il 13 Maggio 1969 ed è stata riconosciuta con D.M. il 2 Febbraio 1974. Italcaccia difende le libertà dell’uomo, vede prossima un’organizzazione venatoria europea che rispecchi diritti e doveri dei popoli della UE, e auspica inoltre un calendario mondiale.
Italcaccia è nata cogliendo il senso delle libertà, accordate ai cittadini dalla costituzione repubblicana; si caratterizza per una sua peculiare visione dei diritti dell’uomo e per la battaglia che conduce per rafforzare le libertà venatorie a livello internazionale.
L’Unione Europea è, secondo l’Italcaccia, la sede idonea per stabilire diritti e doveri del cittadino cacciatore europeo.
La tutela della fauna selvatica è un impegno che può essere assolto dal mondo civile. Italcaccia ribadisce così l’impegno di tutti i suoi associati per un ecosistema degno di una civiltà evoluta.
        </p>
        <h3 class="carousel-pg">Italcaccia</h3>
        <h6 class="carousel-src">
          Visita il
          <a href="https://www.italcaccia.it">sito</a>
        </h6></b-carousel-slide
      >

                        <b-carousel-slide
        img-src="./static/imgs/back.jpeg"
        class="w-100"
        alt="image"
        style="height: 30rem"
        ><b-img src="./static/imgs/logo-EPS.png" style="width: 5rem"></b-img>
        <p class="carousel-text">
L’Ente Produttori Selvaggina (EPS) si propone di diffondere il concetto di caccia sostenibile, riconoscendo il valore primario ed indiscusso della gestione faunistico venatoria, nonché la tutela, la rappresentanza e l’assistenza tecnico giuridica a favore delle aziende venatorie, dei centri privati di produzione di selvaggina, delle riserve di caccia in senso lato, delle aziende agri turistico venatorie, degli allevatori e produttori di selvaggina anche allo stato naturale, ed in genere degli altri istituti venatori aventi carattere privatistico, previsti dalle norme vigenti oltre che di tutti quelli che condividono le finalità dell’Ente.
        </p>
        <h3 class="carousel-pg">EPS</h3>
        <h6 class="carousel-src">
          Visita il
          <a href="https://www.epsitalia.it">sito</a>
        </h6></b-carousel-slide
      >

    </b-carousel>
    <span class="credits_">Fonte: <a href='https://iocaccio.it/associazioni-venatorie-italiane/#:~:text=In%20Italia%20ai%20sensi%20dell,Arci%20Caccia%2C%20Italcaccia%20e%20EPS'>IoCaccio</a></span>

    
  </div>
</template>

<style>

</style>