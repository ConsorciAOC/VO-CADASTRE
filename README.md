# VO-CADASTRE

# Índex

1. [Introducció](#1)
2. [Transmissions de dades disponibles](#2)
3. [Missatgeria dels serveis](#3)
   1. [3.1 Consulta de dades cadastrals (DADES_CADASTRALS)](#3.1)
      1. [3.1.1 Petició](#3.1.1)
      2. [3.1.2 Resposta – dades específiques](#3.1.2)
   2. [3.2 Certificació de titularitat (CERTIFICACIO_TITULARITAT)](#3.2)
      1. [3.2.1 Petició](#3.2.1)
      2. [3.2.2 Resposta – dades específiques](#3.2.2)
   3. [3.3 Certificació descriptiva i gràfica (DESCRIPTIVA_GRAFICA)](#3.3)
      1. [3.3.1 Petició](#3.3.1)
      2. [3.3.2 Resposta – dades específiques](#3.3.2)
   4. [3.4 Obtenció d’un document mitjançant CSV (DOCUMENT_CSV)](#3.4)
      1. [3.4.1 Petició](#3.4.1)
      2. [3.4.2 Resposta – dades específiques](#3.4.2)


# 1. Introducció <a name="1"></a>

Aquest document detalla la missatgeria associada al servei de la Dirección General de Catastro.

Per poder realitzar la integració cal conèixer prèviament la següent documentació:

· Document d’Especificació de missatgeria pel consum de productes de la plataforma PCI del Consorci AOC.


# 2 Transmissions de dades disponibles <a name="2"></a>

Lesdadesdisponiblesatravésdelserveisónlesqueespresentenacontinuació:

| **EMISSOR** |
| --- |
| DirecciónGeneraldeCatastro |
| **PRODUCTE** | **MODALITAT** | **DESCRIPCIO** |
| **CADASTRE** | DADES\_CADASTRALS | Certificatdeconsultadedadescadastrals. |
| CERTIFICACIO\_TITULARITAT | Certificaciódetitularitatd&#39;unbéimmoble. |
| DESCRIPTIVA\_GRAFICA | Certificaciódescriptivaigràficad&#39;unimmoble |
| DOCUMENT\_CSV | Obtenciódel documentassociataun CSV |

La modalitat de consulta de dades cadastrals té disponible la versió imprimible del resultat de laconsulta en format PDF. Per més detalls adreceu-vos a l&#39;apartat _Extensions__de missatgeria_ deldocumentdemissatgeriagenèrica.

1.
# Missatgeriadelsserveis

AcontinuacióesdetallalamissatgeriacorresponentallesmodalitatsdeconsumdelproducteCADASTRE.

L&#39;emissordelesdadesrequereixques&#39;informinlesdadesdel funcionari querealitzalaconsulta.Així,calinformarelssegüentscampsdel&#39;elementFuncionariodelblocde dadesgenèriques:

/Peticion/Funcionario/NombreCompletoFuncionario,

/Peticion/Funcionario/NifFuncionario,

//SolicitudTransmision/DatosGenericos/Solicitante/Funcionario/NombreCompletoFuncionarioi

//SolicitudTransmision/DatosGenericos/Solicitante/Funcionario/NifFuncionario


 ![](RackMultipart20211201-4-e3jz8z_html_17b1a0ab7c224ed3.png)

  1.
## Consultadedadescadastrals(DADES\_CADASTRALS)

Aquesta modalitatpermet consultarinformació de dades cadastrals d&#39;acordalssegüents criterisdecerca:

- Dadesdeltitular

- Referènciacadastrali/oreferènciarústica

    1.
### Petició

      1.
#### Dadesgenèriques–consultaperdadesdetitular

Si es desitja fer la consulta per dades del titular, cal informar el bloc de dades

DatosGenericos/Titulardelamissatgeriagenèrica.

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipusdedocumentació(DNI/NIF,NIEoCIF). |
| //DatosGenericos/Titular/Documentacion | Documentació. |

      1.
#### Dadesespecífiques–consultaperreferènciacadastral/referènciarústica

Acontinuacióesdetallal&#39;_schema_associatalapeticióespecificaencasdevolerrealitzarlaconsultaperreferènciacadastrali/olareferènciarústica.

L&#39;emissordelesdadesrequereixqueaquestaconsultasiguiexcloent,ésadir,obéesconsultaperreferènciacadastralo béesrealitzaatravés dereferènciarústica.


 ![](RackMultipart20211201-4-e3jz8z_html_17b1a0ab7c224ed3.png)

![](RackMultipart20211201-4-e3jz8z_html_23c996a7c3972d97.png)

Del&#39;_schema_associatalapeticióespecifica,elserveiinformalesdadesqueesdetallenacontinuació.

| _Element_ | _Descripció_ |
| --- | --- |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral | Bloc de dades que engloba la informació de lareferènciacadastral. |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral/Pc1 | 1-7dígitsdelareferènciacadastral. |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral/Pc2 | 8-14dígitsdelareferènciacadastral. |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral/car | Càrrecdelareferènciacadastral. |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral/Cc1 | Dígit de control 1 de la referència cadastral. Sempreque s&#39;incloguin els dígits de control, caldrà informar elsdosdígits. |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral/Cc2 | Dígit de control 2 de la referència cadastral. Sempreque s&#39;incloguin els dígits de control, caldrà informar elsdosdígits. |
| //peticioConsultaDades/DatosEntrada/referenciaRustica | Bloc de dades que engloba la informació de lareferènciaRustica |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/localizacionINE | Bloc de dades que conté els codis de provincia imunicipisegonsl&#39;INE |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/localizacionINE/cp | CodideprovinciadelINE |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/localizacionINE/cm | Codidemunicipidel INE |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/cpp | Bloc de dades que conté els codis de polígon iparcel·la |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/cpp/cpo | Codidepolígon |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/cpp/cpa | Codideparcel·la |

    1.
### Resposta–dadesespecífiques

![](RackMultipart20211201-4-e3jz8z_html_7be102e0a11ecb0c.png)

Del&#39;_schema_associatalarespostaespecifica,elserveiinformalesdadesqueesdetallenacontinuació.

| _Element_ | _Descripció_ |
| --- | --- |
| //respostaConsultaDades/peticioConsultaDades | Bloc de dades que conté la informació de lapeticióenviada.Veureladescripciódelbloc3.1.1.2 |
| //respostaConsultaDades/listaBienesInmuebles/datosInmueble | Bloc de dades que conté informació del béimmoble. |
| //listaBienesInmuebles/datosInmueble/BienInmuebleRustico | Bloc de dades que engloba la informaciód&#39;identificació del bé immoble. |
| //listaBienesInmuebles/datosInmueble/BienInmuebleRustico/idine | Bloc de dades que conté informació del bécadastral. |
| //listaBienesInmuebles/datosInmueble/BienInmuebleRustico/idine/cn | Codi de naturalesa del bé immoble, pot ser Urbà(UR),Rústic (RU) o Especial(BI). |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc | Bloc de dades que engloba la informació de lareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc/Pc1 | 1-7dígitsdelareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc/Pc2 | 8-14dígitsdelareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc/car | Càrrecdelareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc/Cc1 | Dígitdecontrol1delareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc/Cc2 | Dígitdecontrol2delareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/loine | Bloc de dades que conté la localització del béimmoble segons elscodisdelINE. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/loine/Cp | CodidelaprovínciasegonselINE. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/loine/Cm | CodidelmunicipisegonselINE. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/Ldt | Domicilitributàriperimmoblesurbans. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi | Blocdedadeseconòmiquesdelbéimmoble. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/avc | Anydel valorcadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/vcat | Valorcadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/vcs | Valorcadastraldel sòl. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/vcc | Valorcadastral delaconstrucció. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/uso | Úsdelbéimmoble. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/sfc | Superfícieconstruïda. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/cpt | Coeficientdeparticipaciódeltitular. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/ant | Antiguitatdelbéimmoble. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol | Bloc de dades de les finques confrontants al béimmoble. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col | Blocdedadesdelafincaconfrontant. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof | Bloc de dades de la referència cadastral de lafinca confrontant. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rc | Bloc de dades de la referència cadastral de lafinca, en el cas que la finca només tingui unimmobles&#39;omplenaaquestblocamblareferènciacadastralcompleta. |
| //listaBienesInmuebles/datosInmueble | 1-7dígitsdelareferènciacadastral. |

| _Element_ | _Descripció_ |
| --- | --- |
| /bienInmuebleRustico/lcol/col/rcof/rc/Pc1 |
 |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rc/Pc2 | 8-14dígitsdelareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rc/car | Càrrecdelareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rc/cc1 | Dígitdecontrol1delareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rc/cc2 | Dígitdecontrol2delareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rfin | Bloc de dades de la referència cadastral de lafinca, en el cas de que la finca tingui més d&#39;unimmobles&#39;omplenaaquestblocamblareferènciacadastral de14dígits. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rfin/pc1 | 1-7dígitsdelareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rfin/pc2 | 8-14dígitsdelareferènciacadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/ldp\_out | Blocde dadesdel titulardelafinca. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/ldp\_out/nif | Documentidentificatiudeltitulardelafinca. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/ldp\_out/nombre | Nomdeltitulardela finca. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/sup | Superfíciedela finca. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/lloc | Domicilidelafincaperimmoblesurbans. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus | Bloc de dades del domicili de la finca perimmobles rústics. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus | Bloc de dades de la localització rústica de lafinca. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/cma | Codidelmunicipiafegit. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/czc | Codidelazonadeconcentració. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/cpp | Blocdedadesdelaidentificaciórústica. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/cpp/cpo | Codidelpolígon. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/cpp/cpa | Codideparcel·la. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/cpp/npa | Nomdelparatge. |
| //listaBienesInmuebles/datosInmueble/listaTitulares | Bloc de dades que conté el llistat dels titulars delbé immoble. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular | Blocdedadesdeltitulardelbéimmoble. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/der | Bloc de dades de la informació del dret sobre elbé immoble. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/der/cdr | Codideldret:
- PR:Propietat
- NP:Nul·lapropietat
- US:usdefruti
 |

| _Element_ | _Descripció_ |
| --- | --- |
|
 |
- CA:Concessióadministrativa
- DS:Dretdesuperfície
- DF:Disfrutador
 |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/der/pct | Percentatgedeltitularsobreelbéimmoble. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/ord | Ordinaldeltitulardins delallista. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp | Bloc de dades que conté informació sobre lapersona. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp/nif | Identificaciódeltitular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp/nom | Cognomsinomoraósocialdeltitular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idpa | Blocdedadesquecontélainformaciósobrelapersona amb nif o explicació d&#39;absència de laidentificació. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idpa/nif | Identificaciódeltitular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idpa/anif | Motiudel&#39;absènciadeNIF:
- 1:ExtrangersenseNIE
- 2:Menord&#39;edatsenseNIF
- 9:Altressituacions
 |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idpa/nom | CognomsiNom. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idps | Bloc de dades que conté la informació sobre lapersona amb nifo explicació d&#39;absència de laidentificació. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idps/nif | Identificaciódeltitular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idps/cii | Claud&#39;identificacióinterna. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idps/nom | CognomsiNom. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp\_out | Bloc de dades de sortida d&#39;informació sobre lapersona. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp\_out/nif | Identificaciódeltitular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp\_out/nom | Nom. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/lder | Literaldeldretsobreelbéimmoble. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df | Bloc de dades que conté la informació sobre eldomicili fiscal. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loine | Bloc de dades que contenen la localització del béimmoble segons elscodisdelINE. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loine/cp | CodidelaprovínciasegonselINE. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loine/cm | CodidelmunicipisegonselINE. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/cmc | Codi de municipi segons la Direcció general delCadastre. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/np | Nomdelaprovincia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/nm | Nomdelmunicipi. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/nem | Nombred&#39;entitatmenor. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir | Blocdedadesquecontél&#39;informaciódel&#39;adreça |
| //listaBienesInmuebles/datosInmueble | Codidela via. |

| _Element_ | _Descripció_ |
| --- | --- |
| /listaTitulares/titular/df/dir/cv |
 |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/tv | Tipusdevia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/nv | Nomdela via. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/pnp | Primernúmerodepolicia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/plp | Lletradelprimernúmerodepolicia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/snp | Segonnúmerodepolicia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/slp | Lletradelsegonnúmerodepolicia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/km | Quilòmetre. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/td | Direcciónoestructurada. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loint | Bloc de dades que conté la informació sobre lalocalitzacióinterna. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loint/bq | Bloc. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loint/es | Escala. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loint/pt | Planta. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loint/pu | Porta. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/pos | Bloc de dades que conté la informació de lesdades postals. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/pos/dp | Codipostal. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/pos/ac | Apartatdecorreus. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/ldf | Literaldeldomicilifiscal |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/cony | Bloc de dades que conté la informació sobre elcònjuge. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/cony/nif | Identificaciódelcònjuge. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/cony/nom | Cognomsinomoraósocialdelcònjuge. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idcbf | Bloc de dades que conté la informació sobre lacomunitatdebéns formal. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idcbf/nifcb | Nifdelacomunitatdelsbéns. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idcbf/nomcb | Denominació o raó social de la comunitat debéns. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/iatit | Bloc de dades que conté la informació addicionalsobreeltitular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/iatit/nifcy | Nifdelcònjuge. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/iatit/nifcb | Nifdelacomunitatdebéns. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/iatit/ct | Complementdetitularitat. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/rtit | Bloc de dades que conté la informació sobre elperíode detempsdetitularitat. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/rtit/fit | Datad&#39;inicidelatitularitat. |
| //listaBienesInmuebles/datosInmueble | Datafidelatitularitat. |

| _Element_ | _Descripció_ |
| --- | --- |
| /listaTitulares/titular/rtit/fft |
 |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/faj | Datad&#39;alteraciójurídica. |
| //listaBienesInmuebles/datosInmueble/finca | Bloc de dades que engloba la informació sobre lafinca a onestàsituatelbé immoble. |
| //listaBienesInmuebles/datosInmueble/finca/ldt | Localitzaciódelafinca. |
| //listaBienesInmuebles/datosInmueble/finca/ltp | Tipusd&#39;immoble. |
| //listaBienesInmuebles/datosInmueble/finca/dff | Bloc de dades que conté la informació sobre lesdades físiquesdela finca. |
| //listaBienesInmuebles/datosInmueble/finca/dff/ssf | Bloc de dades que conté la informació sobre lesdades físiquesdela finca. |
| //listaBienesInmuebles/datosInmueble/finca/dff/ssf/ss | Superfíciedelsól dela finca. |
| //listaBienesInmuebles/datosInmueble/finca/dff/ssf/sct | Superfícieconstruïdadelafinca. |
| //listaBienesInmuebles/datosInmueble/finca/infgraf | Bloc de dades que conté la informaciócartogràficadelafinca. |
| //listaBienesInmuebles/datosInmueble/finca/infgraf/esc | Escaladelacartografia. |
| //listaBienesInmuebles/datosInmueble/finca/infgraf/lgraf | Url en la que es pot obtenir la cartografia de lafinca |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones | Blocdedadesquecontélesconstruccions. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion | Bloc de dades que conté la informació de laconstrucció. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/lcd | Ús delaconstrucció. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt | Bloc de dades que conté la informació sobre laconstrucció. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb | Bloc de dades que conté informació sobre lalocalitzacióde laconstrucció. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb/loint | Bloc de dades que conté la informació sobre lalocalitzacióinterna de laconstrucció. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb/loint/bq | Bloc. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb/loint/es | Escala. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb/loint/pt | Planta. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb/loint/pu | Porta. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dfcons | Bloc de dades que conté la informació sobre lasuperfície construïda. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dfcons/stl | Superfíciedelaconstrucció. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas | Blocde dadesquecontéles subparcel·les. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela | Bloc de dades que conté la informació sobre lessubparcel·les. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/cspr | Codidelasubparcel·la. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr | Bloc de dades que conté la informació sobre lasubparcel·la. |

| _Element_ | _Descripció_ |
| --- | --- |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr/ccc | Qualificaciócadastral. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr/dcc | Denominaciódelaclassedecultiu. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr/ip | Intensitatproductiva. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr/ssp | Superfíciedela subparcel·laen metresquadrats. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr/vsp | Valorcadastraldelasubparcel·la. |
| //respostaConsultaDades/resultat/codiResultat | Codiresultatdelaresposta. |
| //respostaConsultaDades/resultat/descripcio | Descripciódel&#39;estatdelaresposta |

      1.
#### Codisderesultat

- 0003:TRAMITADA.Titularlocalitzat.
- 0012:ERRORALRECUPERARDATOSDELBIEN.
- 0013:ERRORALRECUPERARLASSUBPARCELAS.
- 0017:ELINMUEBLENOEXISTE.
- 0018:AVISO:LAREFERENCIACATASTRALSOLICITADAHASIDOMODIFICADA.LANUEVAREFERENCIACORRESPONDIENTEALINMUEBLEES:…
- 0020:NOHAYBIENES PARALOSDATOSDEENTRADA.
- 0021:ELNIFNOTIENEINMUEBLESASOCIADOSDENTRODELAMBITOTERRITORIALDELACONSULTA,AUNQUESIFUERADEESTE.
- 0022:ELNIFTIENEINMUEBLESASOCIADOSFUERADELAMBITOTERRITORIALDELACONSULTA.
- 0025:ELNIFNOTIENEINMUEBLESASOCIADOS.
- 0026:ELNIFCON LOSAPELLIDOSYNOMBRENOTIENEINMUEBLESASOCIADOS.
- 0027:ERRORALRECUPERARDATOSDETITULARES.
- 0029:ERRORALRECUPERARDATOSDELAFINCA.
- 0030:ERRORALRECUPERARDATOSDELOCALES.
- 0040:IMPOSIBLEREALIZARLACONSULTA.ELNÚMEROMÁXIMODEBIENESQUEPUEDENVISUALIZARSEES DE6000.ACOTELABÚSQUEDA.
- 0502:Errortècnicrealitzantlaconsulta.

  1.
## Certificaciódetitularitat(CERTIFICACIO\_TITULARITAT)

Mitjançantaquestamodalitats&#39;obtéunacertificaciódetitularitatd&#39;unbéimmoble,ésadir,undocument que certifica els immobles associats a un titular cadastral o bé, la circumstància de nofigurarcomatitular cadastraldebensimmobles a labasededadesdelCadastre.

La consulta es realitza per DNI o NIE tot i que es pot acotar l&#39;àmbit de la consulta a una determinadaComunitatAutònoma,provínciaimunicipi.Addicionalment,tambéespotlimitarlaconsultapertipologia delsbensimmobles(urbans,rústicso decaracterístiques especials).

    1.
### Petició

      1.
#### Dadesgenèriques

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipusdedocumentació(DNI/NIF,NIEoCIF). |
| //DatosGenericos/Titular/Documentacion | Documentació. |

      1.
#### Dadesespecífiques

L&#39;_schema_associatalapeticióespecificaesdetallaacontinuació.

![](RackMultipart20211201-4-e3jz8z_html_f78babe07304dad7.png)

| _Element_ | _Descripció_ |
| --- | --- |
| //DatosEntrada/ambito | Bloc de dades que engloba les dades delocalitzaciódel&#39;immoble. |
| //DatosEntrada/ambito/ccaa | CodideComunitatAutònoma:
01:ANDALUCIA02: ARAGON03: P.ASTURIAS04: ILLESBALEARS05:CANARIAS06:CANTABRIA07:CASTILLA-MANCHA08: CASTILLAYLEON09:CATALUNYA10:EXTREMADURA11:GALICIA12: C.MADRID13: R.MURCIA14: C.F.NAVARRA15: PAISVASCO16:LARIOJA17: C.VALENCIANA18: CEUTA19:MELILLA |
| //DatosEntrada/ambito/cp | CodideprovínciasegonsINE. |
| //DatosEntrada/ambito/cm | CodidemunicipisegonsINE. |
| //DatosEntrada/cn | Tipusdebéimmoble(UR:urbà,RU:rústic,BI: |

| _Element_ | _Descripció_ |
| --- | --- |
|
 | característiquesespecials). |

    1.
### Resposta–dadesespecífiques

![](RackMultipart20211201-4-e3jz8z_html_faa2ce28faf332a8.png)

Del&#39;_schema_associatalarespostaespecifica,elserveiinformalesdadesqueesdetallenacontinuació.

| _Element_ | _Descripció_ |
| --- | --- |
| //peticioCertificacioTitular | Bloc de dades que conté la petició específicaassociada a la resposta. Per més detallsconsulteul&#39;apartat anterior. |
| //DatosSalida/pdf | PDFdelcertificatenbase64. |
| //DatosSalida/listaNombres/nombreApellidos | Nom complertdeltitular. |
| //resultat | Resultatdelaconsulta.Permésdetallsconsulteul&#39;apartat 3.2.2.1. |

      1.
#### Codisderesultat

- 0003:TRAMITADA.Titularlocalitzat.
- 0007:IMPOSIBLEREALIZARLACONSULTA.ELNÚMEROMÁXIMODEBIENESQUEPUEDEN CERTIFICAR ES DE 6000. ACOTE LA BUSQUEDA O DIRÍJASE A LA GERENCIATERRITORIALCORRESPONDIENTE.
- 0008: IMPOSIBLE REALIZAR LA CONSULTA . EL ÁMBITO ELEGIDO NO SE ENCUENTRADENTRODELÁMBITO TERRITORIALDELUSUARIO.
- 0013:NOEXISTEDELEGACION PARALOSDATOSINTRODUCIDOS.
- 0015:ELNIFINTRODUCIDONOSEENCUENTRAENLA BASEDE DATOS.
- 0016:ELNIFINTRODUCIDOTIENEASOCIADOSMÁSDEUNAPELLIDOSYNOMBRE.
- 0502:Errortècnicrealitzantlaconsulta.

  1.
## Certificaciódescriptivaigràfica(DESCRIPTIVA\_GRAFICA)

Mitjançantaquestamodalitats&#39;obtéunacertificaciódescriptivaigraficad&#39;unbéimmoble.

Laconsultaesrealitzaapartirdelaprovíncia,municipiilareferènciacadastralolareferènciarústica.

    1.
### Petició

      1.
#### Dadesespecífiques

L&#39;_schema_associatalapeticióespecificaesdetallaacontinuació.

![](RackMultipart20211201-4-e3jz8z_html_6721555f18223409.png)

| _Element_ | _Descripció_ |
| --- | --- |
| //peticioDescriptivaIGrafica/DatosEntrada/localizacionINE | Bloc de dades que conté els codis de provincia imunicipisegonsl&#39;INE |
| //peticioDescriptivaIGrafica/DatosEntrada/localizacionINE/cp | CodideprovinciadelINE |
| //peticioDescriptivaIGrafica/DatosEntrada/localizacionINE/cm | Codidemunicipidel INE |
| //peticioDescriptivaIGrafica/DatosEntrada/referenciaCatastral | Bloc de dades que engloba la informació de lareferènciacadastral. |
| //peticioDescriptivaIGrafica/DatosEntrada/referenciaCatastral/Pc1 | 1-7dígitsdelareferènciacadastral. |
| //peticioDescriptivaIGrafica/DatosEntrada/referenciaCatastral/Pc2 | 8-14dígitsdelareferènciacadastral. |
| //peticioDescriptivaIGrafica/DatosEntrada/referenciaCatastral/car | Càrrecdelareferènciacadastral. |

| _Element_ | _Descripció_ |
| --- | --- |
| //peticioDescriptivaIGrafica/DatosEntrada/referenciaCatastral/Cc1 | Dígitdecontrol1delareferènciacadastral. |
| //peticioDescriptivaIGrafica/DatosEntrada/referenciaCatastral/Cc2 | Dígitdecontrol2delareferènciacadastral. |
| //peticioDescriptivaIGrafica/DatosEntrada/referenciaRustica | Bloc de dades que engloba la informació de lareferènciaRustica |
| //peticioDescriptivaIGrafica/DatosEntrada/referenciaRustica/cpo | Codidepolígon |
| //peticioDescriptivaIGrafica/DatosEntrada/referenciaRustica/cpa | Codideparcel·la |

    1.
### Resposta–dadesespecífiques

![](RackMultipart20211201-4-e3jz8z_html_5f4a7879561a8346.png)

Del&#39;_schema_associatalarespostaespecifica,elserveiinformalesdadesqueesdetallenacontinuació.

| _Element_ | _Descripció_ |
| --- | --- |
| //peticioDescriptivaIGrafica | Bloc de dades que conté la petició específicaassociada a la resposta. Per més detallsconsulteul&#39;apartat anterior. |
| //DatosSalida/pdf | PDFdelcertificatenbase64. |
| //resultat | Resultatdelaconsulta.Permésdetallsconsulteul&#39;apartat 3.2.2.1. |

      1.
#### Codisderesultat

- 0003:TRAMITADA.
- 0014:REFERENCIACATASTRALINVÁLIDA(ONOTIENE14,18NI20DÍGITOS).
- 0017:ELINMUEBLENOEXISTE.
- 0018:AVISO:LAREFERENCIACATASTRALSOLICITADAHASIDOMODIFICADA.LANUEVAREFERENCIACORRESPONDIENTEALINMUEBLEES:
- 0019:ELBIENNOSEENCUENTRAENELÁMBITOTERRITORIALDECONSULTADELUSUARIO.
- 0020:NOHAYBIENES PARALOSDATOSDEENTRADA.

- 0021: EXISTE MÁS DE UN BIEN INMUEBLE PARA LOS DATOS DE ENTRADA. HAGA LABÚSQUEDAPORREFERENCIACATASTRAL.
- 0022:NOESPOSIBLELAEMISIONDELACERTIFICACIONDESCRIPTIVAYGRAFICAPORQUESEHADETECTADOUNAINCONSISTENCIAENLASBASESDEDATOSCATASTRALES.LACERTIFICACIONPUEDESERSOLICITADAENLAGERENCIAOSUBGERENCIA DEL CATASTRO, DONDE SERA EMITIDA UNA VEZ CORREGIDAS DICHASINCONSISTENCIAS.
- 0023:CARTOGRAFÍANODISPONIBLEPARADICHOMUNICIPIO.
- 0024:NOEXISTECARTOGRAFÍADIGITALASOCIADAAESAFINCA.
- 0502:Errortècnicrealitzantlaconsulta.

  1.
## Obtenciód&#39;undocumentmitjançantCSV(DOCUMENT\_CSV)

Aquesta modalitat proporciona un documento en PDF generat (i catalogat), mitjançant el seu CSV(codisegur deverificació).

    1.
### Petició

      1.
#### Dadesespecífiques

L&#39;_schema_associatalapeticióespecificaesdetallaacontinuació.

![](RackMultipart20211201-4-e3jz8z_html_248f111da41b6ae6.png)

| _Element_ | _Descripció_ |
| --- | --- |
| //peticioDocumentCSV/CSV | Codisegurdeverificació(16dígits). |

    1.
### Resposta–dadesespecífiques

![](RackMultipart20211201-4-e3jz8z_html_5520a3b9eea12e39.png)

Del&#39;_schema_associatalarespostaespecifica,elserveiinformalesdadesqueesdetallenacontinuació.

| _Element_ | _Descripció_ |
| --- | --- |
| //peticioDocumentCSV | Bloc dedadesquecontélapeticióespecíficaassociadaalaresposta.Permésdetallsconsulteul&#39;apartatanterior. |
| //pdf | PDFgenerat(enbase64). |
| //resultat | Resultatdelaconsulta.Permésdetallsconsulteul&#39;apartat3.4.2.1 |

      1.
#### Codisderesultat

- 0003:TRAMITADA.CSVlocalitzat.
- 2:NUMERO MAXIMO DEINTENTOSFALLIDOS
- 3:NOEXISTEELDOCUMENTOSOLICITADOEN ELCATALOGO.
- 4:ERRORALGRABAR ELNÚMERODEPETICIONESCSV
- 0502:Errortècnicrealitzantlaconsulta.
