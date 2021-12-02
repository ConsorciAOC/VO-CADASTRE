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

Les dades disponibles a través del servei són les que es presenten a continuació:

| **EMISSOR** |
| --- |
| Dirección General de Catastro |

| **PRODUCTE** | **MODALITAT** | **DESCRIPCIO** |
| --- | --- | --- |
| **CADASTRE** | DADES CADASTRALS _ | Certificat de consulta de dades cadastrals. |
| **CADASTRE** | CERTIFICACIO_TITULARITAT | Certificació de titularitat d’un bé immoble. |
| **CADASTRE** | DESCRIPTIVA_GRAFICA | Certificació descriptiva i gràfica d’un immoble. |
| **CADASTRE** | DOCUMENT_CSV | Obtenció del document associat a un CSV. |

La modalitat de consulta de dades cadastrals té disponible la versió imprimible del resultat de la consulta en format PDF. Per més detalls adreceu-vos a l’apartat Extensions de missatgeria del document de missatgeria genèrica.


# 3 Missatgeria dels serveis <a name="3"></a>

A continuació es detalla la missatgeria corresponent al les modalitats de consum del producte CADASTRE.

![image](https://user-images.githubusercontent.com/32306731/144471771-e8a0a800-f1f3-43a0-803f-cda9217aa337.png) L’emissor de les dades requereix que s’informin les dades del funcionari que realitza la consulta. Així, cal informar els següents camps de l’element Funcionario del bloc de dades genèriques:

/Peticion/Funcionario/NombreCompletoFuncionario,
/Peticion/Funcionario/NifFuncionario,
//SolicitudTransmision/DatosGenericos/Solicitante/Funcionario/NombreCompletoFuncionario i
//SolicitudTransmision/DatosGenericos/Solicitante/Funcionario/NifFuncionario


## 3.1 Consulta de dades cadastrals (DADES_CADASTRALS) <a name="3.1"></a>

Aquesta modalitat permet consultar informació de dades cadastrals d’acord als següents criteris de cerca:
•	Dades del titular

•	Referència cadastral i/o referència rústica

### 3.1.1 Petició <a name="3.1.1"></a>

#### 3.1.1.1 Dades genèriques – consulta per dades de titular

Si	es	desitja	fer	la	consulta	per	dades	del	titular,	cal	informar	el	bloc	de	dades DatosGenericos/Titular de la missatgeria genèrica.


| _Element_ | _Descripció_ |
| --- | --- |
| //DatosGenericos/Titular/TipoDocumentacion | Tipus de documentació (DNI / NIF, NIE o CIF). |
| //DatosGenericos/Titular/Documentacion | Documentació. |

#### 3.1.1.2 Dades específiques – consulta per referència cadastral / referència rústica

A continuació es detalla l’schema associat a la petició especifica en cas de voler realitzar la consulta per referència cadastral i/o la referència rústica.

![image](https://user-images.githubusercontent.com/32306731/144472243-e09d5292-ebda-4517-9051-046b448f269f.png) L’emissor de les dades requereix que aquesta consulta sigui excloent, és a dir, o bé es consulta per referència cadastral o bé es realitza a través de referència rústica.

![image](https://user-images.githubusercontent.com/32306731/144472284-5f5c71ca-ee03-4a49-b9e6-422f4c528f9b.png)

De l’schema associat a la petició especifica, el servei informa les dades que es detallen a continuació.

| _Element_ | _Descripció_ |
| --- | --- |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral | Bloc de dades que engloba la informació de la referència cadastral. |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral/Pc1 | 1-7 dígits de la referència cadastral. |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral/Pc2 | 8-14 dígits de la referència cadastral. |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral/car | Càrrec de la referència cadastral. |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral/Cc1 | Dígit de control 1 de la referència cadastral. Sempre que s’incloguin els dígits de control, caldrà informar els dos dígits. |
| //peticioConsultaDades/DatosEntrada/referenciaCatastral/Cc2 | Dígit de control 2 de la referència cadastral. Sempre que s’incloguin els dígits de control, caldrà informar els dos dígits. |
| //peticioConsultaDades/DatosEntrada/referenciaRustica | Bloc de dades que engloba la informació de la referència Rustica |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/localizacionINE | Bloc de dades que conté els codis de provincia i municipi segons l’INE |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/localizacionINE/cp | Codi de provincia del INE |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/localizacionINE/cm | Codi de municipi del INE |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/cpp | Bloc de dades que conté els codis de polígon i parcel·la |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/cpp/cpo | Codi de polígon |
| //peticioConsultaDades/DatosEntrada/referenciaRustica/cpp/cpa | Codi de parcel·la |


### 3.1.2 Resposta – dades específiques

![image](https://user-images.githubusercontent.com/32306731/144472742-57bd8913-56e7-43b7-933c-d77148dccb86.png)

De l’schema associat a la resposta especifica, el servei informa les dades que es detallen a continuació.

| _Element_ | _Descripció_ |
| --- | --- |
| //respostaConsultaDades/peticioConsultaDades | Bloc de dades que conté informació del bé immoble. |
| //respostaConsultaDades/listaBienesInmuebles/datosInmueble | Bloc de dades que conté informació del béimmoble. |
| //listaBienesInmuebles/datosInmueble/BienInmuebleRustico | Bloc de dades que engloba la informació d’identificació del bé immoble. |
| //listaBienesInmuebles/datosInmueble/BienInmuebleRustico/idine | Bloc de dades que conté informació del bé cadastral. |
| //listaBienesInmuebles/datosInmueble/BienInmuebleRustico/idine/cn | Codi de naturalesa del bé immoble, pot ser Urbà (UR), Rústic (RU) o Especial (BI). |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc | Bloc de dades que engloba la informació de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc/Pc1 | 1-7 dígits de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc/Pc2 | 8-14 dígits de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc/car | Càrrec de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc/Cc1 | Dígit de control 1 de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/rc/Cc2 | Dígit de control 2 de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/loine | Bloc de dades que conté la localització del bé immoble segons els codis del INE. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/loine/Cp | Codi de la província segons el INE. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/idine/loine/Cm | Codi del municipi segons el INE. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/Ldt | Domicili tributàri per immobles urbans. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi | Bloc de dades econòmiques del bé immoble. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/avc | Any del valor cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/vcat | Valor cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/vcs | Valor cadastral del sòl. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/vcc | Valor cadastral de la construcció. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/uso | Ús del bé immoble. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/sfc | Superfície construïda. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/cpt | Coeficient de participació del titular. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/debi/ant | Antiguitat del bé immoble. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol | Bloc de dades de les finques confrontants al bé immoble. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col | Bloc de dades de la finca confrontant. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof | Bloc de dades de la referència cadastral de la finca confrontant. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rc | Bloc de dades de la referència cadastral de la finca, en el cas que la finca només tingui un immoble s’omplena aquest bloc amb la referència
cadastral completa. |
| //listaBienesInmuebles/datosInmueble | 1-7 dígits de la referència cadastral. |
| /bienInmuebleRustico/lcol/col/rcof/rc/Pc1 | |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rc/Pc2 | 8-14 dígits de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rc/car | Càrrec de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rc/cc1 | Dígit de control 1 de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rc/cc2 | Dígit de control 2 de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rfin | Bloc de dades de la referència cadastral de la finca, en el cas de que la finca tingui més d’un immoble s’omplena aquest bloc amb la referència
cadastral de 14 dígits. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rfin/pc1 | 1-7 dígits de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/rcof/rfin/pc2 | 8-14 dígits de la referència cadastral. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/ldp\_out | Bloc de dades del titular de la finca. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/ldp\_out/nif | Document identificatiu del titular de la finca. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/ldp\_out/nombre | Nom del titular de la finca. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/sup | Superfície de la finca. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/lloc | Domicili de la finca per immobles urbans. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus | Bloc de dades del domicili de la finca per immobles rústics. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus | Bloc de dades de la localització rústica de la finca. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/cma | Codi del municipi afegit. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/czc | Codi de la zona de concentració. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/cpp | Bloc de dades de la identificació rústica. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/cpp/cpo | Codi del polígon. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/cpp/cpa | Codi de parcel·la. |
| //listaBienesInmuebles/datosInmueble/bienInmuebleRustico/lcol/col/dtrus/lorus/cpp/npa | Nom del paratge. |
| //listaBienesInmuebles/datosInmueble/listaTitulares | Bloc de dades que conté el llistat dels titulars del bé immoble. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular | Bloc de dades del titular del bé immoble. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/der | Bloc de dades de la informació del dret sobre el bé immoble. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/der/cdr | Codi del dret: <lu><li>PR: Propietat</li><li>NP: Nul·la propietat</li><li>US: usdefruti</li><li>CA: Concessió administrativa</li><li>DS: Dret de superfície</li><li>DF: Disfrutador</li></lu> |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/der/pct | Percentatge del titular sobre el bé immoble. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/ord | Ordinal del titular dins de la llista. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp | Bloc de dades que conté informació sobre la persona. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp/nif | Identificació del titular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp/nom | Cognoms i nom o raó social del titular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idpa | Bloc de dades que conté la informació sobre la
persona amb nif o explicació d’absència de la identificació. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idpa/nif | Identificació del titular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idpa/anif | Motiu de l’absència de NIF: <lu><li>1: Extranger sense NIE</li><li>2: Menor d’edat sense NIF</li><li>9: Altres situacions</li></lu> |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idpa/nom | Cognoms i Nom. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idps | Bloc de dades que conté la informació sobre la persona amb nif o explicació d’absència de la identificació. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idps/nif | Identificació del titular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idps/cii | Clau d’identificació interna. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idps/nom | Cognoms i Nom. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp\_out | Bloc de dades de sortida d’informació sobre la persona. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp\_out/nif | Identificació del titular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idp\_out/nom | Nom. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/lder | Literal del dret sobre el bé immoble. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df | Bloc de dades que conté la informació sobre el domicili fiscal. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loine | Bloc de dades que contenen la localització del bé immoble segons els codis del INE. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loine/cp | Codi de la província segons el INE. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loine/cm | Codi del municipi segons el INE. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/cmc | Codi de municipi segons la Direcció general del Cadastre. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/np | Nom de la provincia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/nm | Nom del municipi. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/nem | Nombre d’entitat menor. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir | Bloc de dades que conté l’informació de l’adreça. |
| //listaBienesInmuebles/datosInmueble | Codi de la via. |

| /listaTitulares/titular/df/dir/cv | |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/tv | Tipus de via. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/nv | Nom de la via. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/pnp | Primer número de policia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/plp | Lletra del primer número de policia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/snp | Segon número de policia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/slp | Lletra del segon número de policia. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/km | Quilòmetre. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/dir/td | Direcció no estructurada. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loint | Bloc de dades que conté la informació sobre la localització interna. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loint/bq | Bloc. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loint/es | Escala. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loint/pt | Planta. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/loint/pu | Porta. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/pos | Bloc de dades que conté la informació de les dades postals. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/pos/dp | Codi postal. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/df/pos/ac | Apartat de correus. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/ldf | Literal del domicili fiscal |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/cony | Bloc de dades que conté la informació sobre el cònjuge. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/cony/nif | Identificació del cònjuge. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/cony/nom | Cognoms i nom o raó social del cònjuge. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idcbf | Bloc de dades que conté la informació sobre la comunitat de béns formal. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idcbf/nifcb | Nif de la comunitat dels béns. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/idcbf/nomcb | Denominació o raó social de la comunitat debéns. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/iatit | Bloc de dades que conté la informació addicional sobre el titular. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/iatit/nifcy | Nif del cònjuge. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/iatit/nifcb | Nif de la comunitat de béns. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/iatit/ct | Complement de titularitat. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/rtit | Bloc de dades que conté la informació sobre el període de temps de titularitat. |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/rtit/fit | Data d’inici de la titularitat. |
| //listaBienesInmuebles/datosInmueble | Data fi de la titularitat. |
| /listaTitulares/titular/rtit/fft | |
| //listaBienesInmuebles/datosInmueble/listaTitulares/titular/faj | Data d’alteració jurídica. |
| //listaBienesInmuebles/datosInmueble/finca | Bloc de dades que engloba la informació sobre la finca a on està situat el bé immoble. |
| //listaBienesInmuebles/datosInmueble/finca/ldt | Localització de la finca. |
| //listaBienesInmuebles/datosInmueble/finca/ltp | Tipus d’immoble. |
| //listaBienesInmuebles/datosInmueble/finca/dff | Bloc de dades que conté la informació sobre lesdades físiques de la finca. |
| //listaBienesInmuebles/datosInmueble/finca/dff/ssf | Bloc de dades que conté la informació sobre les dades físiques de la finca. |
| //listaBienesInmuebles/datosInmueble/finca/dff/ssf/ss | Superfície del sól de la finca. |
| //listaBienesInmuebles/datosInmueble/finca/dff/ssf/sct | Superfície construïda de la finca. |
| //listaBienesInmuebles/datosInmueble/finca/infgraf | Bloc de dades que conté la informació cartogràfica de la finca. |
| //listaBienesInmuebles/datosInmueble/finca/infgraf/esc | Escala de la cartografia. |
| //listaBienesInmuebles/datosInmueble/finca/infgraf/lgraf | Url en la que es pot obtenir la cartografia de la finca |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones | Bloc de dades que conté les construccions. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion | Bloc de dades que conté la informació de la construcció. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/lcd | Ús de la construcció. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt | Bloc de dades que conté la informació sobre la construcció. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb | Bloc de dades que conté informació sobre la localització de la construcció. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb/loint | Bloc de dades que conté la informació sobre la localització interna de la construcció. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb/loint/bq | Bloc. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb/loint/es | Escala. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb/loint/pt | Planta. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dt/lourb/loint/pu | Porta. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dfcons | Bloc de dades que conté la informació sobre la superfície construïda. |
| //listaBienesInmuebles/datosInmueble/listaConstrucciones/construccion/dfcons/stl | Superfície de la construcció. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas | Bloc de dades que conté les subparcel·les. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela | Bloc de dades que conté la informació sobre les subparcel·les. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/cspr | Codi de la subparcel·la. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr | Bloc de dades que conté la informació sobre la subparcel·la. |

| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr/ccc | Qualificació cadastral. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr/dcc | Denominació de la classe de cultiu. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr/ip | Intensitat productiva. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr/ssp | Superfície de la subparcel·la en metres quadrats. |
| //listaBienesInmuebles/datosInmueble/listaSubparcelas/subparcela/dspr/vsp | Valor cadastral de la subparcel·la. |
| //respostaConsultaDades/resultat/codiResultat | Codi resultat de la resposta. |
| //respostaConsultaDades/resultat/descripcio | Descripció de l’estat de la resposta. |


#### 3.1.2.1 Codis de resultat

•	0003: TRAMITADA. Titular localitzat.
•	0012: ERROR AL RECUPERAR DATOS DEL BIEN.
•	0013: ERROR AL RECUPERAR LAS SUBPARCELAS.
•	0017: EL INMUEBLE NO EXISTE.
•	0018: AVISO: LA REFERENCIA CATASTRAL SOLICITADA HA SIDO MODIFICADA. LA NUEVA REFERENCIA CORRESPONDIENTE AL INMUEBLE ES:…
•	0020: NO HAY BIENES PARA LOS DATOS DE ENTRADA.
•	0021: EL NIF NO TIENE INMUEBLES ASOCIADOS DENTRO DEL AMBITO TERRITORIAL DE LA CONSULTA, AUNQUE SI FUERA DE ESTE.
•	0022: EL NIF TIENE INMUEBLES ASOCIADOS FUERA DEL AMBITO TERRITORIAL DE LA CONSULTA.
•	0025: EL NIF NO TIENE INMUEBLES ASOCIADOS.
•	0026: EL NIF CON LOS APELLIDOS Y NOMBRE NO TIENE INMUEBLES ASOCIADOS.
•	0027: ERROR AL RECUPERAR DATOS DE TITULARES.
•	0029: ERROR AL RECUPERAR DATOS DE LA FINCA.
•	0030: ERROR AL RECUPERAR DATOS DE LOCALES.
•	0040: IMPOSIBLE REALIZAR LA CONSULTA. EL NÚMERO MÁXIMO DE BIENES QUE PUEDEN VISUALIZARSE ES DE 6000. ACOTE LA BÚSQUEDA.
•	0502: Error tècnic realitzant la consulta.

## 3.2	Certificació de titularitat (CERTIFICACIO_TITULARITAT)

===================== CONTINUAR AQUI =====================

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
