<script>
import MapEu from "../components/MapEu.vue";
import MapItaly from "../components/MapItaly.vue";
import TreemapAnimals from "./TreemapAnimals.vue";
import ParallelPlotAnimals from "./ParallelPlotAnimals.vue";
import LineHunters from "./LineHunters.vue";
import BarSports from "./BarSports.vue";
import D3CirclesAssociazioni from "./D3CirclesAssociazioni.vue";
import D3RectVoti from "./D3RectVoti.vue";
import LineMacellazioni from "./LineMacellazioni.vue";
import MapItalyRiserve from "./MapItalyRiserve.vue";
import ItalyRiserveHeat from "./ItalyRiserveHeat.vue";
import LineDemoIt from "./LineDemoIt.vue";
import LinePrezzi from "./LinePrezzi.vue";
import ScatterAnimals from "./ScatterAnimals.vue";
import CarouselAssociazioni from "./CarouselAssociazioni.vue";
import AOS from "aos";
import "aos/dist/aos.css";

export default {
  name: "Home",
  props: {},
  components: {
    MapEu,
    MapItaly,
    TreemapAnimals,
    ParallelPlotAnimals,
    LineHunters,
    BarSports,
    D3CirclesAssociazioni,
    D3RectVoti,
    LineMacellazioni,
    MapItalyRiserve,
    ItalyRiserveHeat,
    LineDemoIt,
    LinePrezzi,
    ScatterAnimals,
    CarouselAssociazioni,
  },
  data() {
    return {};
  },
  mounted() {},
  methods: {
        handle_index(idx) {
      var el = document.getElementById(idx);
      el.scrollIntoView({ behavior: "smooth" });
    },
  },
  watch: {},
};
</script>

<template>
  <b-container id="Home">
{{/*sidebar*/}}
 <div>
      <b-button v-b-toggle.sidebar-footer id="menu_toggle"
        >Mostra<br/>indice</b-button
      >
      <b-sidebar
        id="sidebar-footer"
        aria-label="Sidebar with custom footer"
        no-header
        shadow
      >
        <template #footer="{ hide }">
          <div class="d-flex bg-dark text-light align-items-center px-3 py-2">
            <strong class="mr-auto">Indice</strong>
            <b-button size="sm" @click="hide" style="margin-left:30%">Nascondi indice</b-button>
          </div>
        </template>
        <h4>Per sezione</h4>
        <div class="px-3 py-2">
          <ul id="index">
            <li>
              <b-button class="idx_els" @click="handle_index('first_section')"
                >Dati e criticità</b-button
              >
            </li>
            <li>
              <b-button class="idx_els" @click="handle_index('second_section')"
                >La caccia in Europa</b-button
              >
            </li>
                        <li>
              <b-button class="idx_els" @click="handle_index('third_section')"
                >La caccia in Italia</b-button
              >
            </li>
          </ul>
          <hr/>
          <h4>Per grafico</h4>
                    <ul id="index">
            <li>
              <b-button class="idx_els" @click="handle_index('second_section')"
                >Mappa Europa</b-button
              >
            </li>
            <li>
              <b-button class="idx_els" @click="handle_index('third_section')"
                >Linea cacciatori</b-button
              >
            </li>
                        <li>
              <b-button class="idx_els" @click="handle_index('line_demoIt')"
                >Linea demografia</b-button
              >
            </li>


            <li>
              <b-button class="idx_els" @click="handle_index('line_macellazioni')"
                >Linee macellazioni</b-button
              >
            </li>
            <li>
              <b-button class="idx_els" @click="handle_index('bar_sport')"
                >Barre sport</b-button
              >
            </li>
                        <li>
              <b-button class="idx_els" @click="handle_index('line_prices')"
                >Linee prezzi</b-button
              >
            </li>

                        <li>
              <b-button class="idx_els" @click="handle_index('rects_votes')"
                >Barre referendum</b-button
              >
            </li>
            <li>
              <b-button class="idx_els" @click="handle_index('Map_it')"
                >Mappa Italia</b-button
              >
            </li>
                        <li>
              <b-button class="idx_els" @click="handle_index('circles_associazioni')"
                >Cerchi associazioni</b-button
              >
            </li>


                        <li>
              <b-button class="idx_els" @click="handle_index('tree_animals1')"
                >Treemaps animali</b-button
              >
            </li>
            <li>
              <b-button class="idx_els" @click="handle_index('parallel_')"
                >Calendario venatorio</b-button
              >
            </li>
                        <li>
              <b-button class="idx_els" @click="handle_index('svg_it_res')"
                >Mappa riserve</b-button
              >
            </li>
                                    <li>
              <b-button class="idx_els" @click="handle_index('riserve_it_heat')"
                >Heatmap riserve</b-button
              >
            </li>

          </ul>

        </div>
      </b-sidebar>
    </div>


    <h3 class="title_section" id="first_section">Dati e criticità</h3>
    <div class="body_section">
      I dati riguardanti la caccia sono, tanto a livello europeo quanto a
      livello italiano, distribuiti in maniera altamente eterogenea. La mancanza
      di un database centralizzato che consenta di consultare i dati in maniera
      standardizzata costituisce una lacuna informativa nel panorama della
      filosofia open data. Più specificatamente, il recepimento della Direttiva
      Open Data è avvenuto in Italia attraverso il
      <a
        href="https://www.gazzettaufficiale.it/atto/serie_generale/caricaDettaglioAtto/originario?atto.dataPubblicazioneGazzetta=2021-11-30&atto.codiceRedazionale=21G00213&elenco30giorni=false"
        >d.lgs. 8 novembre 2021, n. 200</a
      >
      il quale appunto attualizza la
      <a
        href="https://eur-lex.europa.eu/legal-content/IT/TXT/?uri=CELEX:32019L1024"
        >direttiva europea 2019/1024</a
      >
      riguardante la strategia europea per i dati (abrogando la previgente
      <a
        href="http://trasparenza.formez.it/content/direttiva-200398ce-parlamento-europeo-e-consiglio-17-novembre-2003-relativa-riutilizzo"
        >direttiva 2003/98/CE</a
      >
      così come modificata dalla
      <a
        href="https://eur-lex.europa.eu/legal-content/IT/TXT/?uri=uriserv:OJ.L_.2013.175.01.0001.01.ITA"
        >direttiva 2013/37/UE</a
      >). Con questa misura, l’Europa ha scelto di investire
      <a href="https://digital-strategy.ec.europa.eu/en/policies/strategy-data"
        >2 mld di euro</a
      >
      per la creazione di infrastrutture atte a processare e distribuire dati
      per il bene dei cittadini. Il
      <a href="https://digital-strategy.ec.europa.eu/en/policies/data-act"
        >Data Act</a
      >
      (la Regolazione sulle regole di armonizzazione sul coretto uso e accesso
      ai dati) è stato adottato dalla Commissione il 23 febbraio 2022, con
      diversi intenti fra cui: “(ndr. creazione di) mezzi per i corpi del
      settore pubblico per l’accesso e l’uso dei dati propri del settore privato
      che sono necessari per specifici motivi di pubblico interesse”. Da un
      punto di vista giuridico, regolamenti e direttive sono due atti fortemente
      vincolanti:
      <ul>
        <li>
          i regolamenti sono di applicazione generale, vincolanti in ogni
          elemento e, soprattutto, direttamente applicabili in tutti i soggetti
          (non occorre dunque che gli stati li ratifichino);
        </li>
        <li>
          le direttive, sempre vincolanti in ogni loro elemento, prevedono il
          raggiungimento di obiettivi comuni lasciando tuttavia margine d’azione
          ai singoli stati (pur ponendo vincoli a livello temporale).
        </li>
      </ul>

      Riguardo al recepimento della Direttiva Open Data in Italia, si nota come
      nella modifica all’art.12 nel d.lgs.8 novembre 2021, n. 200 si afferma che
      “L'Agenzia per l'Italia digitale adotta entro 180 giorni le Linee guida”
      tuttavia affermando poco dopo, nel art 12-bis che i dati sono resi
      disponibili gratuitamente, salvo che (fra le tante) “siano detenuti da
      amministrazioni pubbliche o organismi di diritto pubblico che devono
      generare utili per coprire una parte sostanziale dei costi inerenti allo
      svolgimento dei propri compiti istituzionali e la messa a disposizione
      gratuita di tali dati avrebbe un impatto sostanziale sul bilancio dei
      suddetti enti“ (art 12-bis, paragrafo 3). Quindi una libera circolazione
      dei dati, sì, ma limitatamente alle necessità economiche legate alla
      produzione e alla circolazione dei suddetti. Tralasciando l’ambito
      prettamente giuridico e venendo all’aspetto più pratico, un’ulteriore
      criticità riguarda il metodo di distribuzione dei dati. Sebbene
      giuridicamente (art 1, paragrafo 8 del suddetto disegno di legge) i dati
      debbano essere messi a disposizione in un “formato leggibile
      meccanicamente”, l’abitudine della pubblica amministrazione italiana (e in
      vero di molte associazioni e comitati) nel rendere fruibili i dati in
      formati come il pdf scoraggiano il cittadino medio da una ricerca
      riflessiva, consistendo di fatti in report prolissi che, si spera
      involontariamente, non tengono conto dell’abitudine di lettura del lettore
      medio. Tali report simulano l’accesso orizzontale e trasparente ai dati
      auspicato dalla prospettiva europea, restando di fatto appannaggio di
      pochi cittadini (per esempio associazioni, comitati, esperti...). Al fine
      del presente articolo, per via dell’eterogeneità dei dati e della poca
      documentazione presente in rete, sono state utilizzati fonti istituzionali
      come l’ISTAT quando possibile, attingendo laddove necessario ad altre
      fonti (da Legambiente ai siti intesi per gli appassionati di caccia e,
      dunque, rivolti al mercato del turismo venatorio).
    </div>
    <h3 class="title_section" id="second_section">La caccia in Europa</h3>
    <MapEu></MapEu>
    <div class="body_section">
      Secondo il
      <a
        href="https://www.face.eu/sites/default/files/attachments/data_hunters-region_sept_2010.pdf"
        >report annuale 2009/2010</a
      >
      sulla presenza di cacciatori in Europa della Federazione Europea per la
      Caccia e la Conservazione (FACE), le nazioni in cui il rapporto
      cacciatore/abitante è più alto sono, in ordine decrescente: Irlanda,
      Finlandia, Cipro, Norvegia, Svezia e Danimarca (rispettivamente 1:12,
      1:17, 1:17, 1:24, 1:31 e 1:33). Nella fascia intermedia figurano, sempre
      in ordine decrescente: Spagna, Grecia, Portogallo e Francia
      (rispettivamente 1:41, 1:45, 1:46 e 1:48). Si registrano i valori più
      bassi per Paesi Bassi, Belgio ed est Europa in generale (i primi due
      aventi in assoluto i valori più bassi, specificatamente 1:618 e 1:452).
      Tuttavia, osservando i dati per i restanti attributi del report si nota
      che (per esigenza di spazio vengono elencati solo i top 5 per ogni punto):
      <ul>
        <li>
          Le regioni più estese sono, in ordine crescente e in km2: Turchia (781
          mila), Francia (643 mila), Spagna (505 mila), Svezia (450 mila),
          Germania (358 mila) con l’Italia al nono posto (301 mila)
        </li>
        <li>
          Le regioni con maggiore densità demografica per metro sono: Germania
          (82.5), Turchia(73.2), Francia(64.1), Regno Unito (61.1), Italia
          (58.1)
        </li>
        <li>
          Le regioni con maggiore densità demografica per chilometro quadrato
          sono: Malta (1333), Paesi Bassi (395), Belgio (341), Regno Unito
          (248), Germania (230) con l’Italia al sesto posto (193
        </li>
        <li>
          Le regioni con il valore assoluto di cacciatori più alto sono: Francia
          (1 milione e 331 mila), Spagna (980 mila), Regno Unito (800 mila),
          Italia (750 mila) e Germania (351 mila)
        </li>
      </ul>
      Dai suddetti dati (e dalla mappa generata a partire da questi) si può
      notare che l’Italia compare in tutti gli attributi con valori medio alti
      dunque si può dire che l’Italia:
      <ul>
        <li>
          È fra i paesi più estesi d’Europa (sebbene meno della metà di Turchia
          e Francia, è molto simile per estensione a Germania e Polonia)
        </li>
        <li>
          È fra i paesi con densità demografica per metro più alta d’Europa
          (comparabile a Francia e Regno Unito)
        </li>
        <li>
          È fra i paesi con densità demografica per chilometro quadrato più alta
          d’Europa (comparabile con Regno Unito e Germania ma non con la Francia
          che risulta avere valori dimezzati) probabilmente a causa della
          morfologia del territorio (la popolazione italiana si sviluppa per lo
          più sulle coste, essendo l’Italia costituita per gran parte da catene
          montuose)
        </li>
        <li>
          È fra i Paesi con valore assoluto di cacciatori più elevato,
          comparabile con il Regno Unito ma non con Spagna o Francia,
          quest’ultima avente quasi il doppio dei cacciatori italiani e il
          valore in assoluto più alto d’Europa)
        </li>
      </ul>
      Considerando inoltre che, stando sempre ai dati del 2010, la popolazione
      italiana (60 milioni) era poco meno di quella francese (65 milioni) e di
      quella inglese (62 milioni), con queste ultime tra le più popolose
      d’Europa (Germania con 81 milioni esclusa) si deduce che in Italia la
      caccia è una realtà importante e che non può essere considerata “distante”
      né culturalmente, né fisicamente (vista l’alta densità demografica dovuta
      alle caratteristiche peculiari della morfologia della penisola e vista la
      sua ricchezza naturalistica).
    </div>

    <h3 class="title_section" id="third_section">La caccia in Italia</h3>
    <LineHunters></LineHunters>
    <div class="body_section">
      La percezione della caccia come espediente ricreativo ha iniziato a
      indebolirsi a partire dagli anni 70/80, quando generazioni sempre più
      scolarizzate hanno iniziato ad affrancarsi dalle tradizioni, immersi
      sempre più in contesti urbani e con una visione sempre più rivolta
      all’intrattenimento videoludico. Sebbene, come denunciato dagli
      appassionati di caccia, la figura del cacciatore è in qualche modo
      fisiologica (ndr. se coscienzioso), diventa patologica nel momento in cui
      alla necessità di contenimento delle specie subentra, perverso, il piacere
      della caccia come sport antico. Questa dicotomia emerge in affermazioni
      tanto nobili quanto oramai deprecabili, come nel caso del principe
      <a
        href="https://www.cacciamagazine.it/cala-il-numero-dei-cacciatori-in-italia-il-declino-puo-essere-fermato/"
        >Francesco Chigi Albani della Rovere</a
      >, nel 1935 famoso ornitologo, il quale pur affermando che “la
      legislazione sulla caccia presuppone una preparazione culturale, orientata
      verso la zoologia, in tutti i dirigenti ed in tutti i gregari della
      caccia” afferma comunque che i cacciatori ben formati “avrebbero sentito
      che loro compito non è distruggere animali, ma utilizzarli e per lo sport
      e per la scienza”. In affermazioni come questa si nota l’aporia
      dell’attuale tentativo di far ritornare in qualche modo in auge la pratica
      della caccia in quanto pratica ludica. Considerando effettivamente
      fisiologica la funzione di contenimento delle specie del cacciatore, in
      ultima analisi e a livello fondamentale, qual è realmente il focus del
      praticante? L’equilibrio dell’ecosistema o la soddisfazione di porre fine
      alla vita di altri esseri viventi attraverso l’astuzia e la brutalità?
      Posto che teoricamente considerazioni come quella del suddetto principe
      ornitologo siano legittime, quanti cacciatori sono effettivamente
      “paladini ecozoologici”? E quanti invece “ciechi predatori”? I giovani,
      consci del set mentale perverso del cacciatore medio, hanno scelto di
      considerare eccitanti pratiche come i videogame o il softair anziché la
      caccia, percependo sempre meno l’uccisione di un essere vivente come
      pratica sportiva. Di fatti si noti come nel seguente grafico le licenze da
      cacciatore in Italia, da circa 1 milione e 700 mila negli anni 80, vengano
      dimezzate nel solo arco di un decennio (tra 1990 e 2000 scendono a 800
      mila). Il picco minimo viene raggiunto nel 2007 (700mila circa) mostrando
      tuttavia una lieve ripresa post 2007.
    </div>
    <LineDemoIt></LineDemoIt>

    <div class="body_section">
      Come detto in precedenza, la caccia perde d’attrattiva fra i giovani a
      partire dagli anni 80, stessi anni in cui
      <a href="https:/italiaindati.com/demografia/"
        >la crescita demografica italiana rallenta sensibilmente</a
      >, indice di un cambiamento radicale nello stile di vita delle famiglie di
      fine millennio.
    </div>
    <LineMacellazioni></LineMacellazioni>
    <div class="body_section">
      Come è possibile notare dai
      <a
        href="https://seriestoriche.istat.it/index.php?id=1&no_cache=1&tx_usercento_centofe%5Bcategoria%5D=13&tx_usercento_centofe%5Baction%5D=show&tx_usercento_centofe%5Bcontroller%5D=Categoria&cHash=e3503d8195dd4231ff53ba078ad5c124"
        >dati ISTAT sulle macellazioni</a
      >, la caccia nell’ambito alimentare è marginale sin dai tempi dall’unità
      d’Italia: le fonti principali di carne risultano essere gli allevamenti
      (in particolar modo di bovini, suini e pollame). Si noti come,
      successivamente alla Prima Guerra Mondiale, il trend delle curve inizi a
      diventare instabile, con riduzione e aumento altalenante delle
      macellazioni di suini e bovini, lo stazionamento della produzione di
      pollame e ovini/caprini ed equini e un sensibile aumento della produzione
      di conigli e selvaggina. Guardando al ventennio 1920/1940 è possibile
      affermare che la caccia ha avuto un ruolo sempre più importante
      nell’alimentazione degli italiani. Di fatti, da 152 migliaia di quintali
      di selvaggina prodotta nel 1920 si raggiunge il picco massimo nel 1944
      (800 migliaia di quintali, circa cinque volte di più) con il concomitante
      crollo nella produzione di bovini e suini principalmente, ma anche di
      ovini e pollame. Questo trend si manifesta esclusivamente nel
      <a
        href="https://www.lasinistraquotidiana.it/1944-lannus-horribilis-della-guerra-in-italia/"
        >1944, anno terribile per l’Italia</a
      >, stretta nella morsa finale della Seconda Guerra Mondiale e
      dell’invasione nazista. Si può dunque affermare che la caccia come
      attività di sopravvivenza sia fisiologica in tempi duri, tempi in cui gli
      allevamenti, per un motivo o un altro, sono obbligati a ridurre
      drasticamente la loro produzione, tempi in cui il costo della carne
      diventa esorbitante rispetto alle possibilità del cittadino medio. Erano
      gli stessi anni in cui il consumo intenso della carne era culturalmente
      limitato al fine settimana e non abitudine quotidiana.
      <a
        href="https://www.matteogaruti.com/seconda-guerra-mondiale-alimentazione/#:~:text=80%20g%20di%20carne%20bovina,sostituita%20con%20strutto%20o%20lardo."
      >
        Fonte principale di alimentazione </a
      >erano legumi e patate, derivati animali e cereali. Tuttavia, dopo il
      picco negativo degli allevamenti bovini e suini (rispettivamente da 4855 e
      3295 migliaia di quintali nel 1940 a 994 e 1133 migliaia di quintali nel
      1944), con valori simili al 1861 nonostante il raddoppiare della
      popolazione (da 26 milioni a 42 milioni), il precedente pattern di
      macellazione riprende senza più crolli, andando grossomodo a incrementare
      le tendenze precedenti alla seconda guerra mondiale: bovini e suini
      riprendono ad essere all’apice della produzione di carni, il consumo di
      pollame aumenta sensibilmente raggiungendo gli stessi livelli di bovini
      mentre ovini/caprini ed equini rimangono relativamente marginali.
      Tuttavia, nonostante questa impennata di consumo di carni da allevamento,
      con l’aggiungersi persino del pollame come parte integrante della
      produzione principale assieme a bovini e suini, si noti come i valori
      della selvaggina, dopo un iniziale decremento nel ventennio 1940/60 (in
      concomitanza con l’aumento sostanziale del pollame) ritorni ai livelli
      record del 1944 senza più diminuire, per lo meno fino ai giorni nostri. La
      crescita sensibile della macellazione di selvaggina passa dai valori
      simili alla fine del secondo conflitto mondiale raggiunti nel 1960 al
      triplo nell’arco di un ventennio (1960/80, da 571 a 1835 migliaia di
      quintali) mentre la curva si stabilizza nei decenni successivi, giungendo
      tuttavia a un picco storico nel 2007 (3000 migliaia di quintali), seguito
      da un dimezzamento del valore nel solo giro di un anno ( 1825 migliaia di
      quintali nel 2008). Da questo punto il valore decresce sensibilmente di
      anno in anno sino al 2011, anno in cui vengono escluse dal conteggio le
      macellazioni domestiche di conigli e selvaggina, tornando così a valori
      simili agli anni a cavallo fra le due Guerre Mondiali. Notando questo
      cambio drastico della curva nell’esclusione delle macellazioni domestiche,
      si può affermare come la maggior parte della selvaggina cacciata fosse
      fondamentalmente destinata a uso domestico (prodotto di caccia per sport e
      tradizione piuttosto che necessità). Caso esemplare è la tradizione
      settentrionale di
      <a
        href="https://greenreport.it/news/aree-protette-e-biodiversita/litalia-crocevia-del-bracconaggio-e-del-traffico-di-specie-protette-maglia-nera-alla-lombardia/"
        >“polenta e osei”</a
      >
      che, stando alle parole del WWF nel report SWiPE, si fonda sostanzialmente
      su bracconaggio e commercio illegale di piccoli volatili (anche specie
      protette).
    </div>
    <BarSports></BarSports>
    <div class="body_section">
      Questo tipo di dinamica rimane essenzialmente legata alla tradizione e
      alla incapacità delle vecchie generazioni di comprendere come molte delle
      tradizioni siano ormai incompatibili con la modernità. Considerando che la
      tradizione sia il filtro attraverso cui le generazioni passate guardano al
      presente, e considerando che
      <a
        href="https://www.ilsole24ore.com/art/censimento-italiani-sotto-soglia-60milioni-eta-media-45-anni-e-5-anziani-ogni-bambino-ADgvtN8?refresh_ce=1"
        >l’età media in Italia</a
      >, nel 2019, risulta essere di 45 anni (con l’incidenza di 5 anziani per
      ogni bambino), la piaga dell’illegalità mascherata da tradizione (e non
      solo nella caccia) permarrà ancora nei decenni a venire. Questo
      soprattutto per il diffuso disinteresse che si riflette nella già
      accennata mancanza di database centralizzati per lo studio del fenomeno
      del bracconaggio. Osservando i
      <a href="https://www.istat.it/it/archivio/204663"
        >dati ISTAT sulle pratiche sportive degli italiani</a
      >
      (ai fini del presente grafico è stata utilizzata solo la “Tavola 7 segue”)
      e comparandoli con la serie storica relativa alle macellazioni, si nota
      come a considerare attualmente la caccia e la pesca come sport sia
      essenzialmente la generazione cresciuta nel ventennio 1960/1980 (quindi
      ultra sessantenni e over quaranta), stesso ventennio in cui la produzione
      di selvaggina (soprattutto con macellazione domestica) ha conosciuto una
      crescita incomparabile ai valori passati e, soprattutto, senza un vero
      motivo di necessità (di nuovo: perché, pur essendo aumentata sensibilmente
      la popolazione a causa del boom economico, tanto la produzione di bovini e
      suini quanto l’aumento repentino e senza precedenti della produzione di
      pollame sarebbero potuti bastare per sopravvivere, in particolar modo per
      via del basso costo di polli e suini, questi quasi mai oltre,
      rispettivamente, i 100 e i 200 euro al quintale).
    </div>
    <LinePrezzi></LinePrezzi>

    <D3RectVoti></D3RectVoti>
    <div class="body_section">
      Il 3 giugno del 1990 la popolazione italiana fu chiamata alle urne per 3
      quesiti referendari abrogativi aventi come tema, rispettivamente: la
      disciplina sulla caccia, l’accesso dei cacciatori a fondi privati e l’uso
      dei pesticidi. Tutti temi, questi, che riflettono il cambiamento di
      sensibilità nella popolazione italiana rispetto all’ecosistema e alla
      sostenibilità ambientale delle pratiche umane. Tuttavia l’affluenza alle
      urne non è stata tale da raggiungere il quorum, rendendo dunque inutile il
      tentativo di partiti di sinistra (Partito Radicale, PCI, Democrazia
      Proletaria e Verdi) e delle associazioni ambientaliste (Lega Italiana
      Protezione Uccelli, Legambiente e WWF) perlomeno in pratica. Nonostante il
      quorum mancato, rimane più che chiara la volontà dei votanti. In
      particolare:
      <ol>
        <br />

        <li>
          Nel primo quesito (<b>abolizione della caccia</b>) veniva richiesto di
          abrogare la
          <a
            href="http://www.edizionieuropee.it/law/html/3/zn16_01_02a.html#:~:text=E'%20vietato%2C%20ai%20fini%20della,appartenenti%20alla%20fauna%20selvatica%20italiana."
            >legge 27 dicembre 1997, n.968</a
          >, con lo scopo di:
          <ul>
            <li>
              rendere illegale la caccia di certe specie a prescindere dai
              calendari venatori regionali ([…] limitatamente a: art. 2,
              limitatamente alle parole "ai sensi del successivo art. 12");
            </li>
            <li>
              ridurre la portata della legge nei termini di mezzi e fini della
              caccia ([…] limitatamente a: art. 2, limitatamente alle parole "ai
              sensi del successivo art. 12");
            </li>
            <li>
              l’abrogazione in toto degli articoli 4 (per lo scioglimento del
              comitato tecnico venatorio nazionale), 5, 6, 7 (per l’abolizione
              della discrezionalità regionale/locale in materia di caccia), 8,
              9, 10 (per rendere illegale tout-court l’esercizio della caccia);
            </li>
            <li>
              abrogazione delle eccezioni in virtù dei calendari venatori (art.
              11, secondo comma) e della possibilità di disporre variazioni su
              suddette eccezioni (art. 11, terzo comma);
            </li>
            <li>
              l’abrogazione in toto degli articoli 12 (riduzione della
              discrezione regionale sul controllo della fauna), 13 (per il
              divieto di introduzione di selvaggina dall’estero), 14
              (l’eliminazione dei calendari venatori regionali), 15 (per
              impossibilitare le regioni nel delegare la gestione del territorio
              ad associazioni venatorie e a strutture associative), 16 (contro
              gli appostamenti,sia fissi che temporanei) e 17 (per vietare la
              caccia in fondi chiusi);
            </li>
            <li>
              abrogazione della possibilità, per le regioni, di creare impianti
              adibiti a cattura o detenzione anche per periodi altri rispetto
              all’art.11, col fine di utilizzare le prede o come richiami vivi o
              come merce d’esposizione in tradizionali fiere (articolo 18,
              secondo comma) e della possibilità, sempre per le regioni e/o
              individui da esse nominati, di cacciare e cedere civette o falchi
              per il loro uso nell’esercizio venatorio (articolo 18, quarto
              comma);
            </li>
            <li>
              l’abrogazione in toto degli articoli 20 (una serie di divieti
              contenenti altresì eccezioni relative ad altri articoli), 21,22
              (abolire la licenza di porto d’armi per uso di caccia, rilasciata
              da commissioni regionali e degli esami per il relativo
              conseguimento, anch’essi a discrezione regionale), 23,24 e 25
              (impedire l’indotto venatorio che avviene attraverso tassazioni su
              porto d’armi, su appostamenti fissi, su aziende faunistiche e su
              riserve),26 (per vietare il versamento del 43% dei proventi
              acquisiti mediante suddette tassazioni all’Istituto nazionale di
              biologia della selvaggina);
            </li>
            <li>
              l’eliminazione dell’attività venatoria come motivo di istituzione,
              a livello regionale, di fondi di tutela della produzione agricola
              (articolo 26, primo comma) e, come già detto, il decadere dell’uso
              dei proventi delle tassazioni sull’esercizio venatorio per il
              finaziamento di suddetti fondi di tutela;
            </li>
            <li>
              l’abrogazione in toto degli articoli 27 (riguardo soprattutto ad
              agenti venatori nominati con discrezionalità regionale o a
              discrezione delle associazioni venatorie) e 28 (riguardante i
              poteri di suddetti agenti);
            </li>
            <li>
              l’abrogazione della possibilità, per le associazioni venatorie
              istituite per atto pubblico, di essere legalmente riconosciute
              (articolo 29, secondo, terzo, quarto, quinto, sesto e settimo
              comma);
            </li>
            <li>
              l’abrogazione in toto degli articoli 30 (impossibilitare le
              associazioni venatorie riconosciute nell’esercizio dei loro
              compiti, come organizzare, tutelare e formare i cacciatori,
              proporre alle autorità il riconoscimento di guardie volontarie
              venatorie ecc…), 31, 32, 33 (abolizione del sistema di sanzioni
              per l’attività venatoria), 34 (impossibilitare le regioni
              nell’emanare norme in materia e per vietare la messa in atto dei
              precedenti articoli riguardanti aspetti burocratici come le
              tassazioni), 36 (per impossibilitare le regioni nel trasformare le
              riserve in aziende faunistico-venatorie oltre che per impedire
              piani annuali di ripopolamento e abbattimento a discrezione
              regionale) e 37 (per impedire un ruolo pubblico e provinciale dei
              dipendenti dei comitati provinciali di caccia, in caso di
              scioglimento invece per quanto riguarda l’Ente produttori
              selvaggina).
            </li>
          </ul>
          Nel caso del presente quesito, nonostante il mancato raggiungimento
          del quorum con un’affluenza di circa 43%, circa il 38% della
          popolazione (e dunque il 92% dei votanti) risultavano essere
          favorevoli all’abolizione della caccia in Italia.
        </li>
        <br />
        <li>
          Nel secondo quesito (<b>accesso dei cacciatori a fondi privati</b>)
          veniva richiesto di abrogare l’
          <a
            href="https://www.gazzettaufficiale.it/atto/serie_generale/caricaArticolo?art.versione=1&art.idGruppo=105&art.flagTipoArticolo=2&art.codiceRedazionale=042U0262&art.idArticolo=842&art.idSottoArticolo=1&art.idSottoArticolo1=10&art.dataPubblicazioneGazzetta=1942-04-04&art.progressivo=0#:~:text=842.,in%20atto%20suscettibili%20di%20danno."
            >articolo 842 del codice civile</a
          >
          al primo comma (vietare l’esercizio della caccia anche in fondi non
          chiusi come previsto dalla legge del precedente quesito, ossia legge
          27 dicembre 1997, n.968) e al secondo comma (per impossibilitare il
          cacciatore nel vedere riconosciuto il proprio diritto alla caccia
          sulla base della propria licenza).<br />
          Anche nel caso di questo quesito, con un’affluenza di circa il 43%,
          circa il 38% della popolazione italiana (e dunque il 92% dei votanti)
          risultava essere favorevole alla limitazione dell’esercizio della
          caccia.
        </li>
        <br />
        <li>
          Nel terzo ed ultimo quesito (<b>uso dei pesticidi</b>) veniva
          richiesto di abrogare l’articolo 5 della
          <a
            href="https://www.gazzettaufficiale.it/eli/id/1962/06/04/062U0283/sg"
            >legge 30 aprile 1962, n. 283</a
          >, limitatamente alla discrezionalità con cui il ministro della sanità
          decide i limiti di tolleranza e l’intervallo minimo che deve
          intercorrere tra l’ultimo trattamento e la raccolta e, per le sostanze
          alimentari immagazzinate, tra l’ultimo trattamento e l’immissione al
          consumo (secondo paragrafo del comma h).
          <br />
          Come per i due precedenti quesiti, con un’affluenza del 43%, circa il
          39% della popolazione (e dunque circa il 93% dei votanti) risultava
          essere d’accordo con un uso più consapevole di prodotti chimici
          nell’ambito alimentare.
        </li>
      </ol>

      Sebbene in tutti e tre i casi il quorum non sia stato raggiunto, i
      risultati hanno molto da dire rispetto all’evoluzione culturale degli
      italiani durante gli anni 90, essendo circa 18 milioni di italiani a
      favore di tutti e tre i quesiti abrogativi. Inoltre, stando all’
      <a href="https://pagellapolitica.it/articoli/storia-referendum-abrogativi"
        >elaborazione dei dati del Ministero dell’Interno</a
      >
      (Referendum abrogativi: affluenza regionale, 1990) a disertare le urne
      sono state proprio alcune delle regioni con una maggiore presenza di
      cacciatori/riserve di caccia/superficie di aziende faunistico-venatorie e
      agrituristico-venatorie (regioni con affluenza del meno del 40% in ordine
      crescente: Umbria 25.9%, Calabria 30.2%, Sardegna 32%, Toscana 33.8%,
      Sicilia 34.4%, Campania 36.4%, Marche 37.7%, Molise 38.4% e Basilicata
      39.57%. Le regioni più partecipative sono state: Piemonte, Friuli-Venezia
      Giulia e Veneto (rispettivamente 51.4%, 52.4% e 55%).
    </div>

    <MapItaly></MapItaly>
    <div class="body_section">
      Riguardo i dati ISTAT relativi alla caccia, si tratta di quattro tavole:
      <ol>
        <li>
          numero e superficie delle aziende faunistico-venatorie e
          agrituristico-venatorie per zona altimetrica (in ettari);
        </li>
        <li>
          numero e superficie delle oasi di protezione e rifugio della fauna per
          zona altimetrica (in ettari);
        </li>
        <li>
          numero di superficie delle zone di ripopolamento e cattura della
          selvaggina per zona altimetrica (in ettari);
        </li>
        <li>Principali indicatori sulla caccia.</li>
      </ol>
      Prima di procedere,
      <a href="https://www.earmi.it/caccia/azienda%20faunistica.html"
        >per maggiore chiarezza</a
      >:
      <ul>
        <li>
          le <b>aziende faunistico-venatorie sono senza fine di lucro</b>, con
          prevalenti finalità naturalistiche e faunistiche e prevedono che
          <b
            >tutti possano cacciare sebbene nel rispetto dei calendari
            venatori</b
          >. Inoltre
          <b
            >può essere immessa/liberata selvaggina ma solo prima del 31
            agosto</b
          >.
        </li>
        <li>
          le <b>aziende agri-turistico-venatorie</b>, invece,
          <b>sono intese ai fini di impresa agricola</b> e prevedono
          <b
            >l’immissione e l’abbattimento di fauna selvatica di allevamento per
            tutta la stagione venatoria</b
          >. Inoltre,
          <b
            >il prelievo di fauna selvatica nell’esercizio di tali imprese non
            costituisce esercizio venatorio</b
          >.
        </li>
      </ul>
      E
      <a
        href="https://www.gazzettaufficiale.it/atto/regioni/caricaArticolo?art.progressivo=0&art.idArticolo=7&art.versione=1&art.codiceRedazionale=094R0822&art.dataPubblicazioneGazzetta=1995-01-28&art.idGruppo=2&art.idSottoArticolo=1"
        >ancora</a
      >:
      <ul>
        <li>
          le
          <b
            >oasi di protezione sono aree destinate al rifugio, alla
            riproduzione e alla sosta della fauna selvatica</b
          >;
        </li>
        <li>
          le
          <b
            >zone di ripopolamento e cattura sono dedicate a riproduzione della
            fauna selvatica allo stato naturale e alla cattura della stessa </b
          >, ai fini della ricostruzione e stabilizzazione della densità
          faunistica del territorio
        </li>
      </ul>

      Procedendo con ordine e considerando l’intera serie temporale:
      <ol>
        <li>
          Il
          <b
            >numero di aziende faunistico-venatorie e agrituristico-venatorie</b
          >
          è in media 75, con picco massimo di 309 in Toscana (230 in
          Emilia-Romagna e valori maggiori o uguali a 100 in Veneto, Lombardia,
          Piemonte e Lazio).La maggior parte di esse sono site in territori
          collinari e dal grafico a linea è possibile notare come ci sia stato
          un aumento del 28% nel numero di colline aperte a suddette attività
          nel biennio 2002-2003 (da 639 a 820). L’aumento in questo biennio, per
          il territorio collinare, è dovuto soprattutto alla Sardegna: dalle 103
          colline del 2002 alle 209 del 2004, praticamente un aumento del 103%
          in un solo anno. Per la Toscana si registra un piccolo aumento (da 209
          a 250). Aumento leggero in numero ma consistente in superficie per la
          Sicilia: (da 37 nel 2001 a 49 nel 2007 per valori assoluti, ma da 12
          mila ettari a 50 mila ettari nello stesso periodo, con un incremento
          di quasi 300%). Tuttavia, già dal grafico a linea, si nota come i
          valori rimangano grossomodo stabili fino al 2005, accennando dal 2006
          a un lento declino. Anche in questo caso, le variazioni sono date
          dalla Sardegna che, dopo l’incremento vertiginoso del 2003, subisce un
          ulteriore picco vertiginoso, questa volta negativo: nel 2006 il numero
          scende a 151, raggiungendo i 61 nel 2007 (con variazione,
          relativamente al 2002, del -70%). Sempre in rapporto al numero di
          aziende e alle zone altimetriche: le aziende si distribuiscono, oltre
          che principalmente in collina, anche in pianura con valori minimi per
          le montagne. Tuttavia, guardando all’estensione territoriale per zona
          altimetrica, si nota come pur essendo le pianure numericamente di più
          rispetto alle montagne, così non è per la loro estensione: di fatti le
          zone montuose risultano essere più estese di quelle pianeggianti (in
          media 100 mila ettari in più): con valori compresi fra 30 e 40 mila
          ettari in Toscana, Emilia-Romagna e valori superiori a 45 mila ettari
          in Lazio e Piemonte. Aggiungendo la pianura alle osservazioni, si nota
          come Emilia-Romagna e Piemonte hanno gli stessi ettari dedicati sia
          alla montagna che alla pianura, mentre sempre per queste due zone il
          Veneto risulta essere per lo più pianeggiante (anche Puglia e Sardegna
          ma con estensioni incomparabili con il Veneto). In generale e sempre
          per superficie e zone altimetriche: le zone più eterogenee per
          suddette aziende risultano essere Emilia-Romagna e Piemonte, mentre
          quelle più prevalentemente collinari sono Toscana, Lazio, Sardegna,
          Sicilia, Umbria e Marche. Infine, risultano più pianeggianti Veneto
          Lombardia, Friuli e Puglia.
        </li>
        <li>
          Il <b>numero delle oasi di protezione e rifugio </b> è in media 52
          (valori simili in Puglia e Sardegna), con valori massimi nel
          centro-nord Italia (picco di 222 in Piemonte nel 2001; valori in media
          superiori a 100 in Piemonte, Lombardia, Veneto, Emilia-Romagna e
          Toscana).A differenza dei valori totali della tavola 1, dal grafico a
          linea è possibile notare come la situazione per zona altimetrica del
          2001 (montagne, seguite da colline e pianure) diventi praticamente
          inversa a partire dal 2004. Di fatti è possibile notare dal 2001 al
          2006, un +15% di pianure, un +3% colline (sebbene con una prevalenza
          rispetto alle altre zone altimetriche solo nell’anno 2003) e -12% per
          le montagne. Analizzando in dettaglio le zone altimetriche: la
          diminuzione delle oasi site in zone montuose dipendono per lo più dal
          Piemonte (da 110 a 82 in tutta la serie temporale, con dunque un -25%
          avvenuto fondamentalmente nel 2003) mentre il leggero aumento a
          territori come Lombardia ed Emilia-Romagna che, a fronte di un
          iniziale decremento, ritornano a valori maggiori a fine serie; per
          quanto riguarda i territori collinari invece, le variazioni dipendono
          in particolar modo da Toscana (la quale vede raddoppiare il proprio
          numero di oasi collinari, dalle 35 del 2001 alle 80 del 2007, dunque
          +128%, con iniziale aumento drastico nel 2003) e in senso opposto
          dalla Sardegna (che passa da 58 a 37 nell’arco dell’intera serie,
          dunque -36%, con decremento più forte nel 2004); infine, con
          riferimento al numero di oasi nelle pianure, il trend è fortemente
          influenzato, in ordine cronologico, da: Emilia-Romagna (con una rapida
          crescita dal 2001 al 2005, passando da 75 a 90, quindi +20%),
          Lombardia (che nel 2005 passa da circa 50 a 81, quindi +62%,
          ritornando tuttavia a 57 già nel 2007, quindi -30%) e Veneto (che a
          fronte di in un iniziale e costante decremento, vede un aumento del
          +20%, passando da circa 90 a 109). Guardando alla superficie,
          osservando tutte le zone altimetriche, si nota che, pur essendo le
          oasi montane minori per numero assoluto, esse risultano le più estese
          della penisola (in particolare Trentino, Piemonte, Toscana e
          Lombardia) con un aumento vertiginoso per quanto riguarda il Trentino
          nel 2006 (da 67 mila ettari del 2005 a 120 mila ettari, con +80% in un
          solo anno). Per quanto riguarda le colline, invece, oasi più estese si
          trovano in Sardegna, Toscana, Puglia, Piemonte, Lombardia e Lazio (
          con la Puglia che vede dimezzare le proprie oasi collinari nel 2007,
          passando da essere la prima assieme alla Sardegna con valori superiori
          a 50 mila ettari nel 2006, a 21 mila ettari nel 2007, dunque -60%).
          Infine, la zona altimetrica meno rappresentata per le oasi è la
          pianura, con un andamento costante nel tempo in media di 170 mila
          ettari, principalmente in Emilia-Romagna, Sardegna, Veneto, Puglia,
          Piemonte e Lombardia (con un importante aumento nel caso della
          Sardegna, che passa dai 29 mila ettari di inizio serie ai 38 mila
          ettari nel 2007, con +30%). Dunque: le regioni con un maggior numero
          di oasi sono Emilia, Lombardia, Piemonte e Veneto; quello con oasi di
          maggiore estensione sono Trentino, Toscana, Piemonte, Lombardia,
          Sardegna, Emilia, Lazio e Veneto. Si noti come sebbene il Trentino sia
          per numero apparentemente ininfluente, per superficie è la prima
          regione Italiana per oasi di protezione e rifugio (120 mila ettari
          esclusivamente montani).
        </li>
        <li>
          Il <b>numero delle zone di ripopolamento e cattura</b> è in media 91,
          con valori massimi in Emilia-Romagna (ben 514 nel 2007), valori
          maggiori di circa 300 in Veneto, Lombardia e Piemonte e infine valori
          maggiori di 100 in Toscana e Marche. Come si nota dal grafico a linea,
          si tratta di zone per lo più pianeggianti e collinari (le pianure sono
          di più per valore assoluto, ma leggermente meno per estensione
          rispetto alle colline, sebbene i trend convergano verso il 2017 a
          circa 550 mila ettari). Si noti, fra l’altro, il lento ma costante
          aumento soprattutto nel numero di pianure dedicate al ripopolamento e
          alla cattura. In particolare, per zona altimetrica: le pianure sono
          appannaggio di Emilia-Romagna (361 nel 2007), Lombardia, Piemonte e
          Veneto, con valori minori per Puglia, Sardegna e Toscana; le colline
          sono distribuite in modo omogeneo con picchi di circa 150 per Toscana
          e Piemonte, valori di circa 100 per Marche ed Emilia-Romagna, e con
          cambiamenti repentini in Lazio (da 39 nel 2002, a 21 nel 2003, dunque
          -46% in un solo anno) e in Sardegna (da 15 nel 2002, a 37 nel 2003,
          dunque +146% in un solo anno) e con un diffuso e leggero aumento nel
          2006; infine, per quanto riguarda le zone montuose, regioni con
          elevato numero sono Emilia-Romagna, Liguria, Lombardia, Piemonte,
          Toscana, Campania, Marche, Molise e Lazio, con andamento analogo per
          le superfici. Dunque: le zone di ripopolamento e cattura sono per lo
          più in pianure e colline, e sono concentrate per lo più in
          Emilia-Romagna, Lombardia, Piemonte e Veneto.
        </li>
        <li>
          Infine, per quanto riguarda i
          <b>principali indicatori sulla caccia</b>: su una superficie totale di
          30 milioni di ettari (con regioni principali Emilia-Romagna,
          Lombardia, Piemonte, Puglia, Sardegna, Sicilia, Toscana e Veneto,
          tutti con valori di circa 2 milioni di ettari) 19 milioni e 500 mila
          sono dedicati ad attività aziendale agro-forestale (in pratica il 63%)
          ma con una diminuzione a 18 milioni e 500 mila nel 2004 (-5%, con
          diminuzione contenuta ma diffusa in tutta la penisola), inoltre ad
          avere più territorio dedicato sono le stesse regioni con maggiore
          estensione territoriale. Nel caso del numero di cacciatori, si osserva
          nel grafico a linea un lento aumento fino al 2004 seguito da un
          costante decremento (da 806 mila a 751 mila nel 2007, dunque -7%),
          dovuto alla forte riduzione nelle regioni con più cacciatori (Toscana,
          Sardegna, Sicilia, Lombardia, Lazio, Campania Veneto, tutte con valori
          compresi fa 50 mila e 100mila) in particolare, da inizio a fine serie:
          Toscana da 120 mila a 100 mila (-16% con intervento nel 2003) e
          soprattutto Sardegna da 50 mila a 500 (-99%, con interventi nel 2005 e
          2007). Per quanto riguarda la densità venatoria, si tratta della
          presenza di cacciatori per 1000 ettari (equivalenti circa
          all’estensione di più di 10 campi da calcio) e si osserva nella serie
          un andamento crescente fino al 2005 e un successivo declino (da 40 a
          inizio serie a 40 a fine serie, con picco massimo di 42 nel 2005). Con
          una superficie relativamente ridotta di 542 mila ettari (circa 1/4
          della Toscana) la Liguria mostra la più alta presenza di cacciatori
          per 1000 ettari in quanto si attesta sempre attorno ai 150. Oltre al
          caso limite della Liguria, regioni estese ma con valore elevato
          (intorno ai 70) sono: Toscana, Lombardia, Lazio, Campania, Umbria e
          Veneto. Passando al successivo attributo, per agenti venatori si
          intende fondamentalmente la figura del guardiacaccia e si nota dal
          grafico a linea come la mancata annotazione della Sardegna nel 2004 e
          2007 corrisponda decrementi di 1000 (da circa 3700 a 2700, -27%). Dal
          grafico a barre si nota come la Sardegna abbia valori fissi a 950
          (esclusi i periodi non annotati che mostrano 0 come volare) per tutta
          la serie mentre ci sono variazioni in regioni critiche come Toscana
          (da 162 a 204, +25%), Sicilia ( con valori oscillanti ma di circa 200
          da inizio a fine serie ), Piemonte (da 85 a 137, 52%) e Lombardia (da
          329 a 138, -58%), Lazio (da 80 a 287, +259%). Ad affiancare gli agenti
          venatori nel controllo ci sono le guardie volontarie che, osservando
          il grafico a linea, aumentano considerevolmente da inizio a fine serie
          (da 10 mila a 15 mila, +50%) con picco nel 2005 (da 13 mila a 15 mila,
          +15%).Osservando la mappa e il grafico a barre, è possibile notare
          come se nel 2001 le guardie volontarie erano concentrate nelle regioni
          critiche (Toscana e Marche con 10mila, Piemonte con 7mila, Veneto e
          Liguria con circa 5000 e nel sud 3400 per Lazio e Campania), nel resto
          della serie si assiste a una diminuzione di concentrazione in suddette
          aree e una diffusione su tutta la penisola: a fine serie ogni regione
          ha la media dell’intera distribuzione (circa 1000) ad esclusione di
          Molise, Puglia, Sardegna, Valle d’Aosta, Trentino e Friuli, tutte con
          valori di 100. Per un’analisi più significativa, osservando la densità
          di agenti e/o guardie per 1000 ettari (vigilanza venatoria) si nota,
          nel grafico a linea (considerando lo 0 come valore non annotato), un
          importante incremento dell’indice per via di un diffuso aumento su
          tutta la penisola. I valori particolarmente alti della Liguria
          sembrano suggerire, assieme agli alti valori di cacciatori, che sia
          fra le zone più piccole ma più critiche d’Italia (per 150 cacciatori
          in 1000 ettari, ci sono 4 controllori). Tuttavia restano critiche
          anche Campania e Lazio (per circa 60 cacciatori in 1000 ettari, ci
          sono circa 2 controllori), Lombardia, Toscana e Umbria ( per circa 70
          cacciatori in 1000 ettari, c’è circa un controllore) e Veneto (per
          circa 50 cacciatori in 1000 ettari, c’è circa un controllore). Per
          ulteriori riflessioni su questi dati si rimanda alla sezione “riserve
          di caccia”.
        </li>
      </ol>
    </div>
    <D3CirclesAssociazioni></D3CirclesAssociazioni>
    <div class="body_section">
      Le associazioni venatorie riconosciute ai sensi della
      <a
        href="https://www.gazzettaufficiale.it/eli/id/1992/02/25/092G0211/sg#:~:text=La%20fauna%20selvatica%20e'%20patrimonio,danno%20effettivo%20alle%20produzioni%20agricole."
        >legge 11 febbraio 1992, n.157</a
      >
      sono (articolo 34, comma 5):
      <ul>
        <li>
          <b>Federazione Italiana della Caccia</b> (Federcaccia o FIdC) con
          400mila associati;
        </li>
        <li><b>Libera Caccia</b> (A.N.L.C.) con 100mila associati;</li>
        <li>
          <b>Unione Nazionale Enalcaccia Pesca e Tiro</b> (Enalcaccia) con
          80mila associati;
        </li>
        <li><b>Arci Caccia</b> con 50mila associati;</li>
        <li>
          <b
            >Associazione dei Migratoristi Italiani per la conservazione
            dell’ambiente naturale</b
          >
          (ANUU) con 30mila associati;
        </li>
        <li><b>Italcaccia</b> 15mila associati;</li>
        <li><b>Ente Produttori Selvaggina</b> (EPS) con 11 mila associati.</li>
      </ul>
      Tutte queste associazioni hanno sede nazionale a Roma, a differenza di
      ANUU avente sede a Bergamo. Nel comma 8 dell’articolo 12 di suddetta legge
      si afferma che per esercitare l’attività venatoria occorre essere
      maggiorenni, avere una licenza per porto di fucile per uso di caccia, di
      due polizze assicurative (per la responsabilità civile di terzi e per
      infortuni del cacciatore) mentre nel comma 12 si afferma che occorre
      essere muniti di tesserino regionale con impresse zone e specie in cui può
      avvenire la caccia (questo a seconda della regione). Nel comma 11 si
      afferma che la licenza è valida su tutta la penisola previo rispetto delle
      disposizioni regionali in materia di caccia (come ad esempio i calendari
      venatori).
    </div>
    <CarouselAssociazioni></CarouselAssociazioni>
    <br />
    <div class="body_section">
      Nell’articolo 10, comma 1, si legge che “tutto il territorio
      agro-silvo-pastorale è soggetto a pianificazione fuanistico-venatoria” ai
      fini della conservazione e contenimento delle fauna. Nel comma 2 si
      afferma che tale pianificazione è prerogativa regionale e, nel comma 3, si
      afferma che, in genere, tra il 20 e il 30% del territorio ASP
      (agro-silvo-pastorale) dev’essere dedicato alla protezione della fauna
      selvatica (tra il 10 e il 20% nel caso delle Alpi). Per protezione, nel
      comma 4, si intende “divieto di abbattimento e cattura a fini venatori
      accompagnato da provvedimenti atti ad agevolare la sosta della fauna, la
      riproduzione e la cura della prole.” Nel comma 5 si legge che al massimo
      15% del territorio può essere dedicato a gestione privata. Infine,
      tornando alle associazioni, nell’articolo 34, comma 2, si legge che le
      associazioni venatorie istituite per atto pubblico possono essere
      riconosciute per legge se: hanno finalità ricreative, formative o tecnico
      venatorie; hanno ordinamento democratico e una organizzazione stabile a
      carattere nazionale; hanno un numero di iscritti non inferiore ad un
      quindicesimo del totale dei cacciatori italiani. Il ruolo delle
      associazioni venatorie è importante poiché agiscono di concerto alle
      regioni nella gestione del territorio ai fini della gestione della fauna:
      ad esempio, le guardie volontarie dipendono dalle associazioni
      venatorie/agricole o da associazioni di protezione ambientale riconosciute
      dal Ministero dell’ambiente o presenti nel Comitato tecnico
      faunistico-venatorio (articolo 27, comma 1, b).
    </div>

    <TreemapAnimals></TreemapAnimals>
    <br />
    <div class="body_section">
      Consultando i dati del Ministero della Transizione Ecologica (MITE)
      riguardo il
      <a
        href="https://www.mite.gov.it/pagina/repertorio-della-fauna-italiana-protetta"
        >repertorio della fauna italiana</a
      >, leggendo i contenuti della pagina, si legge che su 57.422 specie, il
      97% (56168) appartiene agli invertebrati, mentre il restante 3% ai
      vertebrati (1254). Inoltre, la premura nella salvaguardia riguarda
      fondamentalmente questo 3%, in particolare per quanto riguarda gli animali
      terrestri si legge che sono tutelati “93 Mammiferi su 118, 467 Uccelli su
      473, 58 Rettili su 58, 38 Anfibi su 38”. <br /><br />
      Passando ai dati, il controllo fatto dal MITE riguarda la presenza di
      informazioni in diversi documenti (regolamenti, direttive, convenzioni…
      per approfondimento visitare la pagina) e, parallelamente, la
      categorizzazione secondo l’organizzazione non governativa IUCN (Unione
      Mondiale per la Conservazione della Natura). Al fine di poter paragonare
      questi due tipi di informazione (da un lato la presenza della specie in
      suddetti documenti, dall’altro la categoria IUCN) sono state create due
      treemap: nella prima, a sinistra, i dati vengono raggruppati per Classe =>
      Famiglia => Specie italiana => Specie latina (eliminando livelli meno
      informativi ai fini della presente analisi, come il Phylum, ma mantenendo
      la famiglia in modo da recuperare facilmente l’informazione sulla base del
      seguente grafico ad assi y paralleli) e la grandezza riguarda il numero di
      volte che un animale appare in un documento per la tutela dell’ambiente;
      nella seconda, a destra, vengono riportate solo le specie categorizzate
      dall’IUCN, mantenendo come grandezza il numero di volte in cui la specie
      appare in suddetti documenti. Osservando il grafico a sinistra, si nota
      come effettivamente più della metà delle specie da tutelare ricadono
      uccelli (la cui famiglia appare ben 1380 volte in tutti i documenti in
      esame), mammiferi (369), rettili (133), esapodi (insetti con 6 zampe, 107)
      e anfibi (106). Osservando il grafico a destra, invece, è possibile vedere
      l’intersezione fra i dati catalogati da IUCN e il numero di citazioni nei
      vari documenti: fra le specie gravemente minacciate compaiono alcuni
      membri delle famiglie di rettili, mammiferi, uccelli; fra quelle
      minacciate rettili e mammiferi; fra quelle vulnerabili mammiferi, uccelli,
      anfibi e rettili (ma anche esapodi); fra quelle a minor rischio/dipendenti
      dalla protezione mammiferi e uccelli; fra quelle a minor rischio/quasi a
      rischio si trovano mammiferi, anfibi, uccelli e rettili; fra i quasi a
      rischio solo mammiferi. Le due categorie più rappresentate sono i
      vulnerabili e quelli a minor rischio/quasi a rischio (citate nei suddetti
      documenti rispettivamente 143 e 124 volte). Seguono quelli gravemente
      minacciati (34) e quelli minacciati (32) con infine quelli a minor
      rischio/dipendenti da protezione (20) e i quasi a rischio (7). Alcuni di
      quelli per cui non sono sufficienti i dati restano comunque molto citati
      in suddetti documenti (48 volte in tutto, con i mammiferi come principale
      classe escludendo gli osteitti, anche detti pesci ossei). Comparando
      questi due grafici con il successivo grafico ad assi y paralleli
      (mostrante i dati riportati nella legge 11 febbraio 1992, n. 157
      all’articolo 18, comma 1, a) è possibile osservare come effettivamente le
      specie cacciabili si ripartiscono in modo assai eterogeneo fra mammiferi e
      uccelli: delle 48 specie riportate nell’articolo, il 75% appartiene alla
      classe degli uccelli (36) mentre il restante 25% appartiene ai mammiferi
      (12). Per quanto riguarda le famiglie, a le più predate sono, in ordine
      crescente: anatidi (9, 18%), galliformi (8, 16%), lagomorfi (5,10%) e
      turdidi (4, 8%) e scolopacidi (3, 6%). Infine Il periodo con più specie
      cacciabili va dalla terza domenica di settembre al 31 gennaio (con 27
      specie, il 56%) seguito dal periodo che va dalla terza domenica di
      settembre al 31 gennaio ( con 11 specie, il 22%), e gli ultimi due che
      vanno, rispettivamente, dal primo ottobre al 30 novembre (9, 11%) e dal
      primo ottobre al 31 dicembre o dal primo novembre al 31 gennaio (una sola
      specie, ossia il cinghiale, 2%).
      <br /><br />
      Prima di procedere, può essere d’aiuto ricordare al lettore che in Italia:
      ai sensi dell’articolo 3, comma 1 della legge del 1992 è vietata ogni
      forma di uccellagione (caccia di uccelli attraverso dispositivi fissi,
      come trappole, finalizzata alla cattura di massa) mentre si rimanda
      all’articolo 2 per la lista di animali per cui vige divieto di caccia,
      unitamente a specie dichiarate a rischio di estinzione da organismi
      internazionali e/o Presidente del Consiglio (fra cui quelle segnalate
      nelle due treemap).
    </div>
    <ParallelPlotAnimals></ParallelPlotAnimals>
    <br/>
    <div class="body_section">
      Osservando prima dall’asse per famiglie all’asse delle specie e controllando, per famiglia, le specie nelle due treemap, si può comprendere se ad essere cacciate sono specie anche solo potenzialmente a rischio.
<ul>
  <li>nel grafico a sinistra: fra gli anatidi cacciabili figurano alzavola (4), canapiglia (3), codone (4), germano reale (4), marzaiola (3), mestolone (4), moretta (4) e moriglione (4). Praticamente tutte tranne il fischione; fra i bovidi appare il camoscio alpino (3)e la sottospecie sarda del muflone (4); fra i caradriidi la pavoncella (3); fra i cervidi il capriolo (1), il cervo (1) e il daino (1), praticamente tutti; fra i columbidi colombaccio (2) e tortora (2, sebbene con differenza di nome latino); fra i rallidi folaga (4), gallinella d’acqua (2), porciglione (2), praticamente tutti; fra gli scolopacidi beccaccia (4), beccaccino (4) e Frullino(4), anche qui tutti; fra i suidi la sottospecie meridionale del cinghiale (2); fra i turdidi cesena (2), merlo (2), tordo bottaccio (2), tordo sassello (2), anche qui tutti. Infine, per quanto riguarda i lagomorfi, occorre vedere la famiglia leprideae, in cui figura la lepre sarda (2);</li>
  <li>nel grafico a destra:  fra i bovidi la sottospecie sarda del muflone.</li>
</ul>

Si nota dunque che, sebbene le specie cacciabili non siano critiche a detta della IUCN, lo stesso non vale per i diversi documenti internazionali in cui si citano specie che necessitano attenzione. Tutte le specie cacciabili di anatide, ad esempio, vengono menzionate almeno dalle 3 alle 4 (per un totale di 30); tutti i cervidi sebbene una sola volta; tutti i rallidi tra le 2 e le 4 volte (per un totale di 8); tutti gli scolopacidi 4 volte (per un totale 12); tutti i turdidi 2 volte (per un totale di 8). Trattasi, in tutti i casi a eccezione dei cervidi, di specie appartenenti alla classe degli uccelli.
<br/><br/>
Osservando l’asse dei periodi, la stagione venatoria si apre la terza domenica di settembre e si protrae fino al 31 gennaio. Tuttavia in ogni periodo solo alcune specie possono essere cacciate e per ogni periodo si prevedono diverse date di inizio e di fine. Il grafico è provvisto di input per decidere l’informazione da visualizzare: categoria se si è interessati al confronto sull’intero asse y, colore se si vogliono informazioni percentuali riguardanti la singola selezione. Nel caso del filtro colore si ricorda che nel tooltip che appare passando con il mouse sulla selezione: P(Attributo | color) è il valore da moltiplicare per 100 per avere la percentuale del colore di quell’attributo sull’intero asse, mentre P(color | Attributo) si riferisce, anche qui moltiplicando per 100, alla percentuale del colore dell’attributo rispettivamente al solo attributo. Per convenzione fra parentesi verranno indicati con ordine  ( P(color | Attributo) , P(Attributo |color) ).
<ul>
  <li><b>b)</b> Nel periodo b, con il 56% delle specie cacciabili, osservando la classe si nota come sulle 27 specie cacciabili si tratti nel 96% dei casi di uccelli (il 72% di uccelli cacciabili) e 4% di mammiferi (l’8% dei mammiferi cacciabili). Osservando l’asse delle famiglie, l’elevato numero è dovuto al fatto che a essere cacciate sono, tra le altre, le specie numericamente più consistenti dell’intero calendario riportate precedentemente. In particolare: gli anatidi (i più cacciati in assoluto, il 100% dei cacciabili e il 33% delle famiglie nel periodo di analisi) seguiti da corvidi (100%, 15%), rallidi e scolopacidi (100%,11%),turdidi(75%,11%), caradriidi (100%,7%), columbidi (50%,4%), galliformi (12%, 4%) e, come unici mammiferi, canidi (100%,4%). Specie cacciate che sono per lo meno menzionate al fine della tutela sono:  fra gli anatidi tutti tranne il fischione; fra i cardiidi la pavoncella; fra i columbidi il colombaccio; tutti i rallidi e gli scolopacidi; fra i turdidi cesena, tordo boccaccio e tordo sassello.</li>
  <li><b>a)</b> Nel periodo a, con il 23% delle specie cacciabili, delle 11 specie cacciate si tratta per il 64% di uccelli (il 19% dei cacciabili) e per il 36% di mammiferi (il 33% dei cacciabili). Riguardo le famiglie, si nota la presenza di, in ordine decrescente: galliformi (50%, 36%), lagomorfi (80%, 36%), passeridi (100%, 9%), columbidi (50%, 9%) e turdidi (25%,9%). Specie cacciate che sono per lo meno menzionate al fine della tutela sono: fra i columbidi la tortora comune; fra i lagomorfi la lepre sarda; fra i turdidi il merlo.</li>
  <li><b>c)</b> Nel periodo c, con il 19% delle specie cacciabili,  delle 9 specie cacciate si tratta per il 67% di mammiferi (il 50% dei cacciabili) e per il 33% di uccelli (l’8% dei cacciabili). Riguardo le famiglie, in ordine decrescente: cervidi (100%, 33%), galliformi (38%, 33%), bovidi (100%, 22%) e lagomorfi (20%, 11%). Tra le specie cacciate in questo periodo, sono nominate al fine di potenziale tutela: fra i bovidi il camoscio alpino; tutti i cervidi.</li>
  <li><b>d)</b> Nel periodo d viene esclusivamente cacciato il cinghiale.</li>
</ul>   
Si nota, dunque, come periodi critici per gli uccelli (almeno stando alla legge) siano il periodo a e b (rispettivamente 64% e 72% degli uccelli cacciabili) e in minima parte il periodo c (8%). Per i mammiferi invece, periodi critici risultano il periodo a e c (rispettivamente 33% e 50%) e in minima parte i periodi b (4%) e d (caccia esclusivamente al cinghiale). Inoltre, essendo le specie cacciabili da tutelare per lo più uccelli,<b> possiamo concludere che i periodi più critici siano dunque, in particolar modo, il periodo a e b</b>.
    </div>

    <MapItalyRiserve></MapItalyRiserve>
    <div class="body_section">
      La mappa delle riserve sponsorizzate sul <a href="https://www.turismovenatorio.it/ita/">sito per il turismo venatorio</a> è provvista di due legende: la prima per quanto riguarda le regioni e riguarda l’estensione territoriale delle riserve; la seconda per quanto riguarda le singole riserve e riguarda il numero di specie cacciabili (mentre la grandezza dei punti riguarda l’estensione delle singole riserve). Osservandola si evince che le riserve più estese si trovino in Piemonte e Marche, mentre numerose e dall’estensione intermedia nel sud della Toscana e nel nord Lazio, mentre ce ne sono 2 mediamente estese in Sardegna. In generale, Piemonte, Toscana, Marche e Lazio hanno più offerta in numero di riserve, estensione e numero di specie cacciabili. Per il numero di specie, in ognuna delle 4 riserve si caccia la quasi totalità delle specie offerte da tutte le riserve. Seguono Marche (con una riserva avente quasi numero massimo e un’altra con valori oltre la media) e 5 in toscana con valori oltre la media. 
    </div>
    <ItalyRiserveHeat></ItalyRiserveHeat>
    <div class="body_section">
      Nella heatmap è possibile osservare il numero di riserve che permettono di cacciare una certa specie in un certo luogo. Si nota come in Piemonte, 3 riserve permettano la caccia alla pernice rossa, due riserve beccaccia, fagiano, quaglia, starna e tordi mentre solo una per allodola e cinghiale. Di tutte le specie cacciabili nelle riserve piemontesi, solo il cinghiale appartiene all’ordine dei mammiferi. Osservando valori diversi da uno ad eslcusione del Piemonte: nelle Marche due riserve offrono la caccia alla starna mentre 2 in Toscana alla beccaccia. Anche qui, si tratta esclusivamente di uccelli. In verità, considerando tutte le specie cacciabili in tutte le riserve, si tratta per lo più di uccelli (ad esclusione di capriolo, cervo, cinghiale, coniglio, daino, lepre, lepre sarda e muflone). Suddividendo per ordine di appartenenza: le regioni che offrono più caccia a mammiferi sono Campania, Lazio e in particolare Toscana, mentre c’è prevalentemente caccia agli uccelli nelle Marche, Puglia e Sardegna. In generale, invece, le regioni con più specie cacciabili sono: Toscana, Marche e Lazio.
    </div>
  </b-container>
</template>

<style>
#Home {
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}
.body_section {
  text-align: justify;
  text-justify: inter-word;
  margin-bottom: 2rem;
}
.credits_ {
  font-weight: bold;
  margin-bottom: 1rem;
}
.data_path {
  margin-top: -1rem;
  font-size: 12px;
}
 #menu_toggle {
    font-size: 10px;
    margin-top: 0rem;
    opacity: 0.8;
    position: fixed;
    left:0;
    top:5rem
  }
  .idx_els{
    width:100%
  }
</style>