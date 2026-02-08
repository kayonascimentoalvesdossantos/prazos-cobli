# prazos-cobli[index.html](https://github.com/user-attachments/files/25157430/index.html)
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Consulta de Prazo de Entrega | Cobli</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    
    <script src="https://unpkg.com/lucide@latest"></script>

    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;800&display=swap" rel="stylesheet">
    
    <style>
        body { font-family: 'Plus Jakarta Sans', sans-serif; }
        .glass-header { background: rgba(15, 23, 42, 0.8); backdrop-filter: blur(12px); }
    </style>
</head>
<body class="bg-slate-50 text-slate-900">
    <div id="root"></div>

    <script type="text/babel">
        const { useState, useMemo } = React;
        const { Search, MapPin, Filter, X, Globe, Truck, Clock, AlertCircle, ChevronDown, Package } = lucide;

        const RAW_DATA = `ÁGUA BRANCA	AL	Interior 2	Nordeste	12
ANADIA	AL	Interior 1	Nordeste	12
ARAPIRACA	AL	Interior 1	Nordeste	12
ATALAIA	AL	Interior 1	Nordeste	12
BARRA DE SANTO ANTONIO	AL	Interior 1	Nordeste	12
BARRA DE SÃO MIGUEL	AL	Interior 1	Nordeste	12
BATALHA	AL	Interior 2	Nordeste	12
BELEM	AL	Interior 1	Nordeste	12
BELO MONTE	AL	Interior 2	Nordeste	12
BOCA DA MATA	AL	Interior 1	Nordeste	12
BRANQUINHA	AL	Interior 1	Nordeste	12
CACIMBINHAS	AL	Interior 2	Nordeste	12
CAJUEIRO	AL	Interior 1	Nordeste	12
CAMPESTRE	AL	Interior 2	Nordeste	12
CAMPO ALEGRE	AL	Interior 1	Nordeste	12
CAMPO GRANDE	AL	Interior 2	Nordeste	12
CANAPI	AL	Interior 2	Nordeste	12
CAPELA	AL	Interior 1	Nordeste	12
CARNEIROS	AL	Interior 2	Nordeste	12
CHÃ PRETA	AL	Interior 2	Nordeste	12
COITE DO NOIA	AL	Interior 2	Nordeste	12
COLONIA DE LEOPODINA	AL	Interior 2	Nordeste	12
COQUEIRO SECO	AL	Interior 1	Nordeste	12
CURURIPE	AL	Interior 1	Nordeste	12
CRAIBAS	AL	Interior 2	Nordeste	12
DELMIRO GOLVEIA	AL	Interior 2	Nordeste	12
DOIS RIACHOS	AL	Interior 2	Nordeste	12
ESTRELA DE ALAGOAS	AL	Interior 2	Nordeste	12
FEIRA GRANDE	AL	Interior 2	Nordeste	12
FELIZ DESERTO	AL	Interior 1	Nordeste	12
FLEXEIRAS	AL	Interior 2	Nordeste	12
GIRAU DO PONCIANO	AL	Interior 2	Nordeste	12
IBATEGUARA	AL	Interior 2	Nordeste	12
IGACI	AL	Interior 2	Nordeste	12
IGREJA NOVA	AL	Interior 2	Nordeste	12
INHAPI	AL	Interior 2	Nordeste	12
JACARE DOS HOMENS	AL	Interior 2	Nordeste	12
JACUIPE	AL	Interior 2	Nordeste	12
JAPARATINGA	AL	Interior 1	Nordeste	12
JARAMATAIA	AL	Interior 2	Nordeste	12
JEQUIA DA PRAIA	AL	Interior 1	Nordeste	12
JOAQUIM GOMES	AL	Interior 2	Nordeste	12
JUNDIÁ	AL	Interior 2	Nordeste	12
JUNQUEIRO	AL	Interior 2	Nordeste	12
LAGOA DA CANOA	AL	Interior 2	Nordeste	12
LIMOEIRO DE ANADIA	AL	Interior 2	Nordeste	12
MACEIO	AL	Capital	Nordeste	8
MAJOR ISIDORO	AL	Interior 2	Nordeste	12
MAR VERMELHO	AL	Interior 1	Nordeste	12
MARAGOGI	AL	Interior 2	Nordeste	12
MARAVILHA	AL	Interior 2	Nordeste	12
MARECHAL DEODORO	AL	Interior 1	Nordeste	12
MARIBONDO	AL	Interior 1	Nordeste	12
MATA GRANDE	AL	Interior 2	Nordeste	12
MATRIZ DE CAMARAGIBE	AL	Interior 2	Nordeste	12
MESSIAS	AL	Interior 1	Nordeste	12
MINADOR DO NEGRÃO	AL	Interior 2	Nordeste	12
MONTEIROPOLIS	AL	Interior 2	Nordeste	12
MURICI	AL	Interior 1	Nordeste	12
NOVO LINO	AL	Interior 2	Nordeste	12
OLHO DAGUA DAS FLORES	AL	Interior 2	Nordeste	12
OLHO D'ÁGUA DO CASADO	AL	Interior 2	Nordeste	12
OLHO DAGUA GRANDE	AL	Interior 2	Nordeste	12
OLIVENÇA	AL	Interior 2	Nordeste	12
OURO BRANCO	AL	Interior 2	Nordeste	12
PALESTINA	AL	Interior 2	Nordeste	12
PALMEIRA DOS INDIOS	AL	Interior 1	Nordeste	12
PÃO DE AÇUCAR	AL	Interior 2	Nordeste	12
PARICONHA	AL	Interior 2	Nordeste	12
PARIPUEIRA	AL	Interior 2	Nordeste	12
PASSO DE CAMARAGIBE	AL	Interior 2	Nordeste	12
PAULO JACINTO	AL	Interior 1	Nordeste	12
PENEDO	AL	Interior 2	Nordeste	12
PIAÇABUÇU	AL	Interior 2	Nordeste	12
PILAR	AL	Interior 1	Nordeste	12
PINDOBA	AL	Interior 1	Nordeste	12
PIRANHAS	AL	Interior 2	Nordeste	12
POÇO DAS TRINCHEIRAS	AL	Interior 2	Nordeste	12
PORTO CALVO	AL	Interior 2	Nordeste	12
PORTO DE PEDRAS	AL	Interior 2	Nordeste	12
PORTO REAL DO COLEGIO	AL	Interior 2	Nordeste	12
QUEBRANGULO	AL	Interior 2	Nordeste	12
RIO LARGO	AL	Interior 1	Nordeste	12
ROTEIRO	AL	Interior 1	Nordeste	12
SANTA LUZIA DO NORTE	AL	Interior 1	Nordeste	12
SANTANA DO IPANEMA	AL	Interior 2	Nordeste	12
SANTANA DO MUNDAU	AL	Interior 2	Nordeste	12
SÃO BRAZ	AL	Interior 2	Nordeste	12
SÃO JOSE DA LAJE	AL	Interior 1	Nordeste	12
SÃO JOSE DA TAPERA	AL	Interior 2	Nordeste	12
SÃO LUIS DO QUITUNDE	AL	Interior 1	Nordeste	12
SÃO MIGUEL DOS CAMPOS	AL	Interior 1	Nordeste	12
SÃO MIGUEL DOS MILAGRES	AL	Interior 1	Nordeste	12
SÃO SEBASTIAO	AL	Interior 2	Nordeste	12
SATUBA	AL	Interior 1	Nordeste	12
SENADOR RUI PALMEIRA	AL	Interior 2	Nordeste	12
TANQUE D’ARCA	AL	Interior 2	Nordeste	12
TAQUARANA	AL	Interior 2	Nordeste	12
TEOTONIO VILELA	AL	Interior 1	Nordeste	12
TRAIPU	AL	Interior 2	Nordeste	12
UNIÃO DOS PALMARES	AL	Interior 2	Nordeste	12
VIÇOSA	AL	Interior 1	Nordeste	12
ABAIRA	BA	Interior 1	Nordeste	12
ABARE	BA	Interior 1	Nordeste	12
ACAJUTIBA	BA	Interior 1	Nordeste	12
ADUSTINA	BA	Interior 1	Nordeste	12
AGUA FRIA	BA	Interior 1	Nordeste	12
AIQUARA	BA	Interior 1	Nordeste	12
ALAGOINHAS	BA	Interior 1	Nordeste	12
ALCOBACA	BA	Interior 1	Nordeste	12
ALMADINA	BA	Interior 1	Nordeste	12
AMARGOSA	BA	Interior 1	Nordeste	12
AMELIA RODRIGUES	BA	Interior 1	Nordeste	12
AMERICA DOURADA	BA	Interior 1	Nordeste	12
ANAGE	BA	Interior 1	Nordeste	12
ANDARAI	BA	Interior 1	Nordeste	12
ANDORINHA	BA	Interior 1	Nordeste	12
ANGICAL	BA	Interior 1	Nordeste	12
ANGUERA	BA	Interior 1	Nordeste	12
ANTAS	BA	Interior 1	Nordeste	12
ANTONIO CARDOSO	BA	Interior 1	Nordeste	12
ANTONIO GONCALVES	BA	Interior 1	Nordeste	12
APORA	BA	Interior 1	Nordeste	12
APUAREMA	BA	Interior 1	Nordeste	12
ARACAS	BA	Interior 1	Nordeste	12
ARACATU	BA	Interior 1	Nordeste	12
ARACI	BA	Interior 1	Nordeste	12
ARAMARI	BA	Interior 1	Nordeste	12
ARATACA	BA	Interior 1	Nordeste	12
ARATUIPE	BA	Interior 1	Nordeste	12
AURELINO LEAL	BA	Interior 1	Nordeste	12
BAIANOPOLIS	BA	Interior 1	Nordeste	12
BAIXA GRANDE	BA	Interior 1	Nordeste	12
BANZAE	BA	Interior 1	Nordeste	12
BARRA	BA	Interior 1	Nordeste	12
BARRA DA ESTIVA	BA	Interior 1	Nordeste	12
BARRA DO CHOCA	BA	Interior 1	Nordeste	12
BARRA DO MENDES	BA	Interior 1	Nordeste	12
BARRA DO ROCHA	BA	Interior 1	Nordeste	12
BARREIRAS	BA	Interior 1	Nordeste	12
BARRO ALTO	BA	Interior 1	Nordeste	12
BARRO PRETO	BA	Interior 1	Nordeste	12
BARROCAS	BA	Interior 1	Nordeste	12
BELMONTE	BA	Interior 1	Nordeste	12
BELO CAMPO	BA	Interior 1	Nordeste	12
BIRITINGA	BA	Interior 1	Nordeste	12
BOA NOVA	BA	Interior 1	Nordeste	12
BOA VISTA DO TUPIM	BA	Interior 1	Nordeste	12
BOM JESUS DA LAPA	BA	Interior 1	Nordeste	12
BOM JESUS DA SERRA	BA	Interior 1	Nordeste	12
BONINAL	BA	Interior 1	Nordeste	12
BONITO	BA	Interior 1	Nordeste	12
BOQUIRA	BA	Interior 1	Nordeste	12
BOTUPORA	BA	Interior 1	Nordeste	12
BREJOES	BA	Interior 1	Nordeste	12
BREJOLANDIA	BA	Interior 1	Nordeste	12
BROTAS DE MACAUBAS	BA	Interior 1	Nordeste	12
BRUMADO	BA	Interior 1	Nordeste	12
BUERAREMA	BA	Interior 1	Nordeste	12
BURITIRAMA	BA	Interior 1	Nordeste	12
CAATIBA	BA	Interior 1	Nordeste	12
CABACEIRAS DO PARAGUACU	BA	Interior 1	Nordeste	12
CACHOEIRA	BA	Interior 1	Nordeste	12
CACULE	BA	Interior 1	Nordeste	12
CAEM	BA	Interior 1	Nordeste	12
CAETANOS	BA	Interior 1	Nordeste	12
CAETITE	BA	Interior 1	Nordeste	12
CAFARNAUM	BA	Interior 1	Nordeste	12
CAIRU	BA	Interior 1	Nordeste	12
CALDEIRAO GRANDE	BA	Interior 1	Nordeste	12
CAMACAN	BA	Interior 1	Nordeste	12
CAMACARI	BA	Interior 1	Nordeste	12
CAMAMU	BA	Interior 1	Nordeste	12
CAMPO ALEGRE DE LOURDES	BA	Interior 1	Nordeste	12
CAMPO FORMOSO	BA	Interior 1	Nordeste	12
CANAPOLIS	BA	Interior 1	Nordeste	12
CANARANA	BA	Interior 1	Nordeste	12
CANAVIEIRAS	BA	Interior 1	Nordeste	12
CANDEAL	BA	Interior 1	Nordeste	12
CANDEIAS	BA	Interior 1	Nordeste	12
CANDIBA	BA	Interior 1	Nordeste	12
CANDIDO SALES	BA	Interior 1	Nordeste	12
CANSANCAO	BA	Interior 1	Nordeste	12
CANUDOS	BA	Interior 1	Nordeste	12
CAPELA DO ALTO ALEGRE	BA	Interior 1	Nordeste	12
CAPIM GROSSO	BA	Interior 1	Nordeste	12
CARAIBAS	BA	Interior 1	Nordeste	12
CARAVELAS	BA	Interior 1	Nordeste	12
CARDEAL DA SILVA	BA	Interior 1	Nordeste	12
CARINHANHA	BA	Interior 1	Nordeste	12
CASA NOVA	BA	Interior 1	Nordeste	12
CASTRO ALVES	BA	Interior 1	Nordeste	12
CATOLANDIA	BA	Interior 1	Nordeste	12
CATU	BA	Interior 1	Nordeste	12
CATURAMA	BA	Interior 1	Nordeste	12
CENTRAL	BA	Interior 1	Nordeste	12
CHORROCHO	BA	Interior 1	Nordeste	12
CICERO DANTAS	BA	Interior 1	Nordeste	12
CIPO	BA	Interior 1	Nordeste	12
COARACI	BA	Interior 1	Nordeste	12
COCOS	BA	Interior 1	Nordeste	12
CONCEICAO DA FEIRA	BA	Interior 1	Nordeste	12
CONCEIÇAO DO ALMEIDA	BA	Interior 1	Nordeste	12
CONCEICAO DO COITE	BA	Interior 1	Nordeste	12
CONCEICAO DO JACUIPE	BA	Interior 1	Nordeste	12
CONDE	BA	Interior 1	Nordeste	12
CONDEUBA	BA	Interior 1	Nordeste	12
CONTENDAS DO SINCORA	BA	Interior 1	Nordeste	12
CORACAO DE MARIA	BA	Interior 1	Nordeste	12
CORDEIROS	BA	Interior 1	Nordeste	12
CORIBE	BA	Interior 1	Nordeste	12
CORONEL JOAO SA	BA	Interior 1	Nordeste	12
CORRENTINA	BA	Interior 1	Nordeste	12
COTEGIPE	BA	Interior 1	Nordeste	12
CRAVOLANDIA	BA	Interior 1	Nordeste	12
CRISOPOLIS	BA	Interior 1	Nordeste	12
CRISTOPOLIS	BA	Interior 1	Nordeste	12
CRUZ DAS ALMAS	BA	Interior 1	Nordeste	12
CURACA	BA	Interior 1	Nordeste	12
DARIO MEIRA	BA	Interior 1	Nordeste	12
DIAS DAVILA	BA	Interior 1	Nordeste	12
DOM BASILIO	BA	Interior 1	Nordeste	12
DOM MACEDO COSTA	BA	Interior 1	Nordeste	12
ELISIO MEDRADO	BA	Interior 1	Nordeste	12
ENCRUZILHADA	BA	Interior 1	Nordeste	12
ENTRE RIOS	BA	Interior 1	Nordeste	12
ERICO CARDOSO	BA	Interior 1	Nordeste	12
ESPLANADA	BA	Interior 1	Nordeste	12
EUCLIDES DA CUNHA	BA	Interior 1	Nordeste	12
EUNAPOLIS	BA	Interior 1	Nordeste	12
FATIMA	BA	Interior 1	Nordeste	12
FEIRA DA MATA	BA	Interior 1	Nordeste	12
FEIRA DE SANTANA	BA	Interior 1	Nordeste	12
FILADELFIA	BA	Interior 1	Nordeste	12
FIRMINO ALVES	BA	Interior 1	Nordeste	12
FLORESTA AZUL	BA	Interior 1	Nordeste	12
FORMOSA DO RIO PRETO	BA	Interior 1	Nordeste	12
GANDU	BA	Interior 1	Nordeste	12
GAVIAO	BA	Interior 1	Nordeste	12
GENTIO DO OURO	BA	Interior 1	Nordeste	12
GLORIA	BA	Interior 1	Nordeste	12
GONGOGI	BA	Interior 1	Nordeste	12
GOVERNADOR MANGABEIRA	BA	Interior 1	Nordeste	12
GUAJERU	BA	Interior 1	Nordeste	12
GUANAMBI	BA	Interior 1	Nordeste	12
GUARATINGA	BA	Interior 1	Nordeste	12
HELIOPOLIS	BA	Interior 1	Nordeste	12
IACU	BA	Interior 1	Nordeste	12
IBIASSUCE	BA	Interior 1	Nordeste	12
IBICARAI	BA	Interior 1	Nordeste	12
IBICOARA	BA	Interior 1	Nordeste	12
IBICUI	BA	Interior 1	Nordeste	12
IBIPEBA	BA	Interior 1	Nordeste	12
IBIPITANGA	BA	Interior 1	Nordeste	12
IBIQUERA	BA	Interior 1	Nordeste	12
IBIRAPITANGA	BA	Interior 1	Nordeste	12
IBIRAPUA	BA	Interior 1	Nordeste	12
IBIRATAIA	BA	Interior 1	Nordeste	12
IBITIARA	BA	Interior 1	Nordeste	12
IBITITA	BA	Interior 1	Nordeste	12
IBOTIRAMA	BA	Interior 1	Nordeste	12
ICHU	BA	Interior 1	Nordeste	12
IGAPORA	BA	Interior 1	Nordeste	12
IGRAPIUNA	BA	Interior 1	Nordeste	12
IGUAI	BA	Interior 1	Nordeste	12
ILHEUS	BA	Interior 1	Nordeste	12
INHAMBUPE	BA	Interior 1	Nordeste	12
IPECAETA	BA	Interior 1	Nordeste	12
IPIAU	BA	Interior 1	Nordeste	12
IPIRA	BA	Interior 1	Nordeste	12
IPUPIARA	BA	Interior 1	Nordeste	12
IRAJUBA	BA	Interior 1	Nordeste	12
IRAMAIA	BA	Interior 1	Nordeste	12
IRAQUARA	BA	Interior 1	Nordeste	12
IRARA	BA	Interior 1	Nordeste	12
IRECE	BA	Interior 1	Nordeste	12
ITABELA	BA	Interior 1	Nordeste	12
ITABERABA	BA	Interior 1	Nordeste	12
ITABUNA	BA	Interior 1	Nordeste	12
ITACARE	BA	Interior 1	Nordeste	12
ITAETE	BA	Interior 1	Nordeste	12
ITAGI	BA	Interior 1	Nordeste	12
ITAGIBA	BA	Interior 1	Nordeste	12
ITAGIMIRIM	BA	Interior 1	Nordeste	12
ITAGUACU DA BAHIA	BA	Interior 1	Nordeste	12
ITAJU DO COLONIA	BA	Interior 1	Nordeste	12
ITAJUIPE	BA	Interior 1	Nordeste	12
ITAMARAJU	BA	Interior 1	Nordeste	12
ITAMARI	BA	Interior 1	Nordeste	12
ITAMBE	BA	Interior 1	Nordeste	12
ITANAGRA	BA	Interior 1	Nordeste	12
ITANHEM	BA	Interior 1	Nordeste	12
ITAPARICA	BA	Interior 1	Nordeste	12
ITAPE	BA	Interior 1	Nordeste	12
ITAPEBI	BA	Interior 1	Nordeste	12
ITAPETINGA	BA	Interior 1	Nordeste	12
ITAPICURU	BA	Interior 1	Nordeste	12
ITAPITANGA	BA	Interior 1	Nordeste	12
ITAQUARA	BA	Interior 1	Nordeste	12
ITARANTIM	BA	Interior 1	Nordeste	12
ITATIM	BA	Interior 1	Nordeste	12
ITIRUCU	BA	Interior 1	Nordeste	12
ITIUBA	BA	Interior 1	Nordeste	12
ITORORO	BA	Interior 1	Nordeste	12
ITUACU	BA	Interior 1	Nordeste	12
ITUBERA	BA	Interior 1	Nordeste	12
IUIU	BA	Interior 1	Nordeste	12
JABORANDI	BA	Interior 1	Nordeste	12
JACARACI	BA	Interior 1	Nordeste	12
JACOBINA	BA	Interior 1	Nordeste	12
JAGUAQUARA	BA	Interior 1	Nordeste	12
JAGUARARI	BA	Interior 1	Nordeste	12
JAGUARIPE	BA	Interior 1	Nordeste	12
JANDAIRA	BA	Interior 1	Nordeste	12
JEQUIE	BA	Interior 1	Nordeste	12
JEREMOABO	BA	Interior 1	Nordeste	12
JIQUIRICA	BA	Interior 1	Nordeste	12
JITAUNA	BA	Interior 1	Nordeste	12
JOAO DOURADO	BA	Interior 1	Nordeste	12
JUAZEIRO	BA	Interior 1	Nordeste	12
JUCURUCU	BA	Interior 1	Nordeste	12
JUSSARA	BA	Interior 1	Nordeste	12
JUSSARI	BA	Interior 1	Nordeste	12
JUSSIAPE	BA	Interior 1	Nordeste	12
LAFAIETE COUTINHO	BA	Interior 1	Nordeste	12
LAGOA REAL	BA	Interior 1	Nordeste	12
LAJE	BA	Interior 1	Nordeste	12
LAJEDAO	BA	Interior 1	Nordeste	12
LAJEDINHO	BA	Interior 1	Nordeste	12
LAJEDO DO TABOCAL	BA	Interior 1	Nordeste	12
LAMARAO	BA	Interior 1	Nordeste	12
LAPAO	BA	Interior 1	Nordeste	12
LAURO DE FREITAS	BA	Interior 1	Nordeste	12
LENCOIS	BA	Interior 1	Nordeste	12
LICINIO DE ALMEIDA	BA	Interior 1	Nordeste	12
LIVRAMENTO DE NOSSA SENHORA	BA	Interior 1	Nordeste	12
LUIS EDUARDO MAGALHAES	BA	Interior 1	Nordeste	12
MACAJUBA	BA	Interior 1	Nordeste	12
MACARANI	BA	Interior 1	Nordeste	12
MACAUBAS	BA	Interior 1	Nordeste	12
MACURURE	BA	Interior 1	Nordeste	12
MADRE DE DEUS	BA	Interior 1	Nordeste	12
MAETINGA	BA	Interior 1	Nordeste	12
MAIQUINIQUE	BA	Interior 1	Nordeste	12
MAIRI	BA	Interior 1	Nordeste	12
MALHADA	BA	Interior 1	Nordeste	12
MALHADA DE PEDRAS	BA	Interior 1	Nordeste	12
MANOEL VITORINO	BA	Interior 1	Nordeste	12
MANSIDAO	BA	Interior 1	Nordeste	12
MARACAS	BA	Interior 1	Nordeste	12
MARAGOGIPE	BA	Interior 1	Nordeste	12
MARAU	BA	Interior 1	Nordeste	12
MARCIONILIO SOUZA	BA	Interior 1	Nordeste	12
MASCOTE	BA	Interior 1	Nordeste	12
MATA DE SAO JOAO	BA	Interior 1	Nordeste	12
MATINA	BA	Interior 1	Nordeste	12
MEDEIROS NETO	BA	Interior 1	Nordeste	12
MIGUEL CALMON	BA	Interior 1	Nordeste	12
MILAGRES	BA	Interior 1	Nordeste	12
MIRANGABA	BA	Interior 1	Nordeste	12
MIRANTE	BA	Interior 1	Nordeste	12
MONTE SANTO	BA	Interior 1	Nordeste	12
MORPARA	BA	Interior 1	Nordeste	12
MORRO DO CHAPEU	BA	Interior 1	Nordeste	12
MORTUGABA	BA	Interior 1	Nordeste	12
MUCUGE	BA	Interior 1	Nordeste	12
MUCURI	BA	Interior 1	Nordeste	12
MULUNGU DO MORRO	BA	Interior 1	Nordeste	12
MUNDO NOVO	BA	Interior 1	Nordeste	12
MUNIZ FERREIRA	BA	Interior 1	Nordeste	12
MUQUEM DO SAO FRANCISCO	BA	Interior 1	Nordeste	12
MURITIBA	BA	Interior 1	Nordeste	12
MUTUIPE	BA	Interior 1	Nordeste	12
NAZARE	BA	Interior 1	Nordeste	12
NILO PECANHA	BA	Interior 1	Nordeste	12
NORDESTINA	BA	Interior 1	Nordeste	12
NOVA CANAA	BA	Interior 1	Nordeste	12
NOVA FATIMA	BA	Interior 1	Nordeste	12
NOVA IBIA	BA	Interior 1	Nordeste	12
NOVA ITARANA	BA	Interior 1	Nordeste	12
NOVA REDENCAO	BA	Interior 1	Nordeste	12
NOVA SOURE	BA	Interior 1	Nordeste	12
NOVA VICOSA	BA	Interior 1	Nordeste	12
NOVO HORIZONTE	BA	Interior 1	Nordeste	12
NOVO TRIUNFO	BA	Interior 1	Nordeste	12
OLINDINA	BA	Interior 1	Nordeste	12
OLIVEIRA DOS BREJINHOS	BA	Interior 1	Nordeste	12
OURICANGAS	BA	Interior 1	Nordeste	12
OUROLANDIA	BA	Interior 1	Nordeste	12
PALMAS DE MONTE ALTO	BA	Interior 1	Nordeste	12
PALMEIRAS	BA	Interior 1	Nordeste	12
PARAMIRIM	BA	Interior 1	Nordeste	12
PARATINGA	BA	Interior 1	Nordeste	12
PARIPIRANGA	BA	Interior 1	Nordeste	12
PAU BRASIL	BA	Interior 1	Nordeste	12
PAULO AFONSO	BA	Interior 1	Nordeste	12
PE DE SERRA	BA	Interior 1	Nordeste	12
PEDRAO	BA	Interior 1	Nordeste	12
PEDRO ALEXANDRE	BA	Interior 1	Nordeste	12
PIATA	BA	Interior 1	Nordeste	12
PILAO ARCADO	BA	Interior 1	Nordeste	12
PINDAI	BA	Interior 1	Nordeste	12
PINDOBACU	BA	Interior 1	Nordeste	12
PINTADAS	BA	Interior 1	Nordeste	12
PIRAI DO NORTE	BA	Interior 1	Nordeste	12
PIRIPA	BA	Interior 1	Nordeste	12
PIRITIBA	BA	Interior 1	Nordeste	12
PLANALTINO	BA	Interior 1	Nordeste	12
PLANALTO	BA	Interior 1	Nordeste	12
POCOES	BA	Interior 1	Nordeste	12
POJUCA	BA	Interior 1	Nordeste	12
PONTO NOVO	BA	Interior 1	Nordeste	12
PORTO SEGURO	BA	Interior 1	Nordeste	12
POTIRAGUA	BA	Interior 1	Nordeste	12
PRADO	BA	Interior 1	Nordeste	12
PRESIDENTE DUTRA	BA	Interior 1	Nordeste	12
PRESIDENTE JANIO QUADROS	BA	Interior 1	Nordeste	12
PRESIDENTE TANCREDO NEVES	BA	Interior 1	Nordeste	12
QUEIMADAS	BA	Interior 1	Nordeste	12
QUIJINGUE	BA	Interior 1	Nordeste	12
QUIXABEIRA	BA	Interior 1	Nordeste	12
RAFAEL JAMBEIRO	BA	Interior 1	Nordeste	12
REMANSO	BA	Interior 1	Nordeste	12
RETIROLANDIA	BA	Interior 1	Nordeste	12
RIACHAO DAS NEVES	BA	Interior 1	Nordeste	12
RIACHAO DO JACUIPE	BA	Interior 1	Nordeste	12
RIACHO DE SANTANA	BA	Interior 1	Nordeste	12
RIBEIRA DO AMPARO	BA	Interior 1	Nordeste	12
RIBEIRA DO POMBAL	BA	Interior 1	Nordeste	12
RIBEIRAO DO LARGO	BA	Interior 1	Nordeste	12
RIO DE CONTAS	BA	Interior 1	Nordeste	12
RIO DO ANTONIO	BA	Interior 1	Nordeste	12
RIO DO PIRES	BA	Interior 1	Nordeste	12
RIO REAL	BA	Interior 1	Nordeste	12
RODELAS	BA	Interior 1	Nordeste	12
RUY BARBOSA	BA	Interior 1	Nordeste	12
SALINAS DA MARGARIDA	BA	Interior 1	Nordeste	12
SALVADOR	BA	Capital	Nordeste	7
SANTA BARBARA	BA	Interior 1	Nordeste	12
SANTA BRIGIDA	BA	Interior 1	Nordeste	12
SANTA CRUZ CABRALIA	BA	Interior 1	Nordeste	12
SANTA CRUZ DA VITORIA	BA	Interior 1	Nordeste	12
SANTA INES	BA	Interior 1	Nordeste	12
SANTA LUZIA	BA	Interior 1	Nordeste	12
SANTA MARIA DA VITORIA	BA	Interior 1	Nordeste	12
SANTA RITA DE CASSIA	BA	Interior 1	Nordeste	12
SANTA TEREzINHA	BA	Interior 1	Nordeste	12
SANTALUZ	BA	Interior 1	Nordeste	12
SANTANA	BA	Interior 1	Nordeste	12
SANTANOPOLIS	BA	Interior 1	Nordeste	12
SANTO AMARO	BA	Interior 1	Nordeste	12
SANTO ANTONIO DE JESUS	BA	Interior 1	Nordeste	12
SANTO ESTEVAO	BA	Interior 1	Nordeste	12
SAO DESIDERIO	BA	Interior 1	Nordeste	12
SAO DOMINGOS	BA	Interior 1	Nordeste	12
SAO FELIPE	BA	Interior 1	Nordeste	12
SAO FELIX	BA	Interior 1	Nordeste	12
SAO FELIX DO CORIBE	BA	Interior 1	Nordeste	12
SAO FRANCISCO DO CONDE	BA	Interior 1	Nordeste	12
SAO GABRIEL	BA	Interior 1	Nordeste	12
SAO GONCALO DOS CAMPOS	BA	Interior 1	Nordeste	12
SAO JOSE DA VITORIA	BA	Interior 1	Nordeste	12
SAO JOSE DO JACUIPE	BA	Interior 1	Nordeste	12
SAO MIGUEL DAS MATAS	BA	Interior 1	Nordeste	12
SAO SEBASTIAO DO PASSE	BA	Interior 1	Nordeste	12
SAPEACU	BA	Interior 1	Nordeste	12
SATIRO DIAS	BA	Interior 1	Nordeste	12
SAUBARA	BA	Interior 1	Nordeste	12
SAUDE	BA	Interior 1	Nordeste	12
SEABRA	BA	Interior 1	Nordeste	12
SEBASTIAO LARANJEIRAS	BA	Interior 1	Nordeste	12
SENHOR DO BONFIM	BA	Interior 1	Nordeste	12
SENTO SE	BA	Interior 1	Nordeste	12
SERRA DO RAMALHO	BA	Interior 1	Nordeste	12
SERRA DOURADA	BA	Interior 1	Nordeste	12
SERRA PRETA	BA	Interior 1	Nordeste	12
SERRINHA	BA	Interior 1	Nordeste	12
SERROLANDIA	BA	Interior 1	Nordeste	12
SIMOES FILHO	BA	Interior 1	Nordeste	12
SITIO DO MATO	BA	Interior 1	Nordeste	12
SITIO DO QUINTO	BA	Interior 1	Nordeste	12
SOBRADINHO	BA	Interior 1	Nordeste	12
SOUTO SOARES	BA	Interior 1	Nordeste	12
TABOCAS DO BREJO VELHO	BA	Interior 1	Nordeste	12
TANHACU	BA	Interior 1	Nordeste	12
TANQUE NOVO	BA	Interior 1	Nordeste	12
TANQUINHO	BA	Interior 1	Nordeste	12
TAPEROA	BA	Interior 1	Nordeste	12
TAPIRAMUTA	BA	Interior 1	Nordeste	12
TEIXEIRA DE FREITAS	BA	Interior 1	Nordeste	12
TEODORO SAMPAIO	BA	Interior 1	Nordeste	12
TEOFILANDIA	BA	Interior 1	Nordeste	12
TEOLANDIA	BA	Interior 1	Nordeste	12
TERRA NOVA	BA	Interior 1	Nordeste	12
TREMEDAL	BA	Interior 1	Nordeste	12
TUCANO	BA	Interior 1	Nordeste	12
UAUA	BA	Interior 1	Nordeste	12
UBAIRA	BA	Interior 1	Nordeste	12
UBAITABA	BA	Interior 1	Nordeste	12
UBATA	BA	Interior 1	Nordeste	12
UIBAI	BA	Interior 1	Nordeste	12
UMBURANAS	BA	Interior 1	Nordeste	12
UNA	BA	Interior 1	Nordeste	12
URANDI	BA	Interior 1	Nordeste	12
URUCUCA	BA	Interior 1	Nordeste	12
UTINGA	BA	Interior 1	Nordeste	12
VALENCA	BA	Interior 1	Nordeste	12
VALENTE	BA	Interior 1	Nordeste	12
VARZEA DA ROCA	BA	Interior 1	Nordeste	12
VARZEA DO POCO	BA	Interior 1	Nordeste	12
VARZEA NOVA	BA	Interior 1	Nordeste	12
VARZEDO	BA	Interior 1	Nordeste	12
VERA CRUZ	BA	Interior 1	Nordeste	12
VEREDA	BA	Interior 1	Nordeste	12
VITORIA DA CONQUISTA	BA	Vitoria da Conquista	Nordeste	7
WAGNER	BA	Interior 1	Nordeste	12
WANDERLEY	BA	Interior 1	Nordeste	12
WENCESLAU GUIMARAES	BA	Interior 1	Nordeste	12
XIQUE XIQUE	BA	Interior 1	Nordeste	12
ABAIARA	CE	Interior 1	Nordeste	15
ACARAPE	CE	Interior 1	Nordeste	15
ACARAU	CE	Interior 2	Nordeste	15
ACOPIARA	CE	Interior 2	Nordeste	15
AIUABA	CE	Interior 2	Nordeste	15
ALCANTARAS	CE	Interior 2	Nordeste	15
ALTANEIRA	CE	Interior 1	Nordeste	15
ALTO SANTO	CE	Interior 2	Nordeste	15
AMONTADA	CE	Interior 1	Nordeste	15
ANTONINA DO NORTE	CE	Interior 2	Nordeste	15
APUIARES	CE	Interior 1	Nordeste	15
AQUIRAZ	CE	Interior 1	Nordeste	15
ARACATI	CE	Interior 2	Nordeste	15
ARACOIABA	CE	Interior 1	Nordeste	15
ARARENDA	CE	Interior 2	Nordeste	15
ARARIPE	CE	Interior 1	Nordeste	15
ARATUBA	CE	Interior 1	Nordeste	15
ARNEIROZ	CE	Interior 2	Nordeste	15
ASSARE	CE	Interior 1	Nordeste	15
AURORA	CE	Interior 1	Nordeste	15
BAIXIO	CE	Interior 2	Nordeste	15
BANABUIU	CE	Interior 2	Nordeste	15
BARBALHA	CE	Interior 1	Nordeste	15
BARREIRA	CE	Interior 1	Nordeste	15
BARRO	CE	Interior 1	Nordeste	15
BARROQUINHA	CE	Interior 2	Nordeste	15
BATURITE	CE	Interior 1	Nordeste	15
BEBERIBE	CE	Interior 1	Nordeste	15
BELA CRUZ	CE	Interior 2	Nordeste	15
BOA VIAGEM	CE	Interior 2	Nordeste	15
BREJO SANTO	CE	Interior 1	Nordeste	15
CAMOCIM	CE	Interior 2	Nordeste	15
CAMPOS SALES	CE	Interior 1	Nordeste	15
CANINDE	CE	Interior 1	Nordeste	15
CAPISTRANO	CE	Interior 1	Nordeste	15
CARIDADE	CE	Interior 1	Nordeste	15
CARIRE	CE	Interior 2	Nordeste	15
CARIRIACU	CE	Interior 1	Nordeste	15
CARIUS	CE	Interior 2	Nordeste	15
CARNAUBAL	CE	Interior 2	Nordeste	15
CASCAVEL	CE	Interior 2	Nordeste	15
CATARINA	CE	Interior 2	Nordeste	15
CATUNDA	CE	Interior 2	Nordeste	15
CAUCAIA	CE	Interior 1	Nordeste	15
CEDRO	CE	Interior 2	Nordeste	15
CHAVAL	CE	Interior 2	Nordeste	15
CHORO	CE	Interior 2	Nordeste	15
CHOROZINHO	CE	Interior 2	Nordeste	15
COREAU	CE	Interior 2	Nordeste	15
CRATEUS	CE	Interior 2	Nordeste	15
CRATO	CE	Interior 1	Nordeste	15
CROATA	CE	Interior 2	Nordeste	15
CRUZ	CE	Interior 2	Nordeste	15
DEPUTADO IRAPUAN PINHEIRO	CE	Interior 2	Nordeste	15
ERERE	CE	Interior 2	Nordeste	15
EUSEBIO	CE	Interior 1	Nordeste	15
FARIAS BRITO	CE	Interior 1	Nordeste	15
FORQUILHA	CE	Interior 2	Nordeste	15
FORTALEZA	CE	Capital	Nordeste	8
FORTIM	CE	Interior 2	Nordeste	15
FRECHEIRINHA	CE	Interior 2	Nordeste	15
GENERAL SAMPAIO	CE	Interior 1	Nordeste	15
GRACA	CE	Interior 2	Nordeste	15
GRANJA	CE	Interior 2	Nordeste	15
GRANJEIRO	CE	Interior 1	Nordeste	15
GROAIRAS	CE	Interior 2	Nordeste	15
GUAIUBA	CE	Interior 2	Nordeste	15
GUARACIABA DO NORTE	CE	Interior 2	Nordeste	15
GUARAMIRANGA	CE	Interior 1	Nordeste	15
HIDROLANDIA	CE	Interior 2	Nordeste	15
HORIZONTE	CE	Interior 1	Nordeste	15
IBARETAMA	CE	Interior 2	Nordeste	15
IBIAPINA	CE	Interior 2	Nordeste	15
IBICUITINGA	CE	Interior 2	Nordeste	15
ICAPUI	CE	Interior 2	Nordeste	15
ICO	CE	Interior 2	Nordeste	15
IGUATU	CE	Interior 2	Nordeste	15
INDEPENDENCIA	CE	Interior 2	Nordeste	15
IPAPORANGA	CE	Interior 2	Nordeste	15
IPAUMIRIM	CE	Interior 2	Nordeste	15
IPU	CE	Interior 2	Nordeste	15
IPUEIRAS	CE	Interior 2	Nordeste	15
IRACEMA	CE	Interior 2	Nordeste	15
IRAUCUBA	CE	Interior 2	Nordeste	15
ITAICABA	CE	Interior 2	Nordeste	15
ITAITINGA	CE	Interior 1	Nordeste	15
ITAPAJE	CE	Interior 1	Nordeste	15
ITAPIPOCA	CE	Interior 1	Nordeste	15
ITAPIUNA	CE	Interior 1	Nordeste	15
ITAREMA	CE	Interior 2	Nordeste	15
ITATIRA	CE	Interior 1	Nordeste	15
JAGUARETAMA	CE	Interior 2	Nordeste	15
JAGUARIBARA	CE	Interior 2	Nordeste	15
JAGUARIBE	CE	Interior 2	Nordeste	15
JAGUARUANA	CE	Interior 2	Nordeste	15
JARDIM	CE	Interior 1	Nordeste	15
JATI	CE	Interior 1	Nordeste	15
JIJOCA DE JERICOACOARA	CE	Interior 2	Nordeste	15
JUAZEIRO DO NORTE	CE	Interior 1	Nordeste	15
JUCAS	CE	Interior 2	Nordeste	15
LAVRAS DA MANGABEIRA	CE	Interior 2	Nordeste	15
LIMOEIRO DO NORTE	CE	Interior 2	Nordeste	15
MADALENA	CE	Interior 2	Nordeste	15
MARACANAU	CE	Interior 1	Nordeste	15
MARANGUAPE	CE	Interior 1	Nordeste	15
MARCO	CE	Interior 2	Nordeste	15
MARTINOPOLE	CE	Interior 2	Nordeste	15
MASSAPE	CE	Interior 2	Nordeste	15
MAURITI	CE	Interior 1	Nordeste	15
MERUOCA	CE	Interior 2	Nordeste	15
MILAGRES	CE	Interior 1	Nordeste	15
MILHA	CE	Interior 2	Nordeste	15
MIRAIMA	CE	Interior 2	Nordeste	15
MISSAO VELHA	CE	Interior 1	Nordeste	15
MOMBACA	CE	Interior 2	Nordeste	15
MONSENHOR TABOSA	CE	Interior 2	Nordeste	15
MORADA NOVA	CE	Interior 2	Nordeste	15
MORAUJO	CE	Interior 2	Nordeste	15
MORRINHOS	CE	Interior 2	Nordeste	15
MUCAMBO	CE	Interior 2	Nordeste	15
MULUNGU	CE	Interior 1	Nordeste	15
NOVA OLINDA	CE	Interior 1	Nordeste	15
NOVA RUSSAS	CE	Interior 2	Nordeste	15
NOVO ORIENTE	CE	Interior 2	Nordeste	15
OCARA	CE	Interior 1	Nordeste	15
OROS	CE	Interior 2	Nordeste	15
PACAJUS	CE	Interior 2	Nordeste	15
PACATUBA	CE	Interior 1	Nordeste	15
PACOTI	CE	Interior 1	Nordeste	15
PACUJA	CE	Interior 2	Nordeste	15
PALHANO	CE	Interior 2	Nordeste	15
PALMACIA	CE	Interior 1	Nordeste	15
PARACURU	CE	Interior 2	Nordeste	15
PARAIPABA	CE	Interior 2	Nordeste	15
PARAMBU	CE	Interior 2	Nordeste	15
PARAMOTI	CE	Interior 1	Nordeste	15
PEDRA BRANCA	CE	Interior 2	Nordeste	15
PENAFORTE	CE	Interior 1	Nordeste	15
PENTECOSTE	CE	Interior 1	Nordeste	15
PEREIRO	CE	Interior 2	Nordeste	15
PINDORETAMA	CE	Interior 2	Nordeste	15
PIQUET CARNEIRO	CE	Interior 2	Nordeste	15
PIRES FERREIRA	CE	Interior 2	Nordeste	15
PORANGA	CE	Interior 2	Nordeste	15
PORTEIRAS	CE	Interior 1	Nordeste	15
POTENGI	CE	Interior 1	Nordeste	15
POTIRETAMA	CE	Interior 2	Nordeste	15
QUITERIANOPOLIS	CE	Interior 2	Nordeste	15
QUIXADA	CE	Interior 2	Nordeste	15
QUIXELO	CE	Interior 2	Nordeste	15
QUIXERAMOBIM	CE	Interior 2	Nordeste	15
QUIXERE	CE	Interior 2	Nordeste	15
REDENCAO	CE	Interior 1	Nordeste	15
RERIUTABA	CE	Interior 2	Nordeste	15
RUSSAS	CE	Interior 2	Nordeste	15
SABOEIRO	CE	Interior 2	Nordeste	15
SALITRE	CE	Interior 1	Nordeste	15
SANTA QUITERIA	CE	Interior 2	Nordeste	15
SANTANA DO ACARAU	CE	Interior 2	Nordeste	15
SANTANA DO CARIRI	CE	Interior 1	Nordeste	15
SAO BENEDITO	CE	Interior 2	Nordeste	15
SAO GONCALO DO AMARANTE	CE	Interior 2	Nordeste	15
SAO JOAO DO JAGUARIBE	CE	Interior 2	Nordeste	15
SAO LUIS DO CURU	CE	Interior 2	Nordeste	15
SENADOR POMPEU	CE	Interior 2	Nordeste	15
SENADOR SA	CE	Interior 2	Nordeste	15
SOBRAL	CE	Interior 2	Nordeste	15
SOLONOPOLE	CE	Interior 2	Nordeste	15
TABULEIRO DO NORTE	CE	Interior 2	Nordeste	15
TAMBORIL	CE	Interior 2	Nordeste	15
TARRAFAS	CE	Interior 2	Nordeste	15
TAUA	CE	Interior 2	Nordeste	15
TEJUCUOCA	CE	Interior 1	Nordeste	15
TIANGUA	CE	Interior 2	Nordeste	15
TRAIRI	CE	Interior 2	Nordeste	15
TURURU	CE	Interior 1	Nordeste	15
UBAJARA	CE	Interior 2	Nordeste	15
UMARI	CE	Interior 2	Nordeste	15
UMIRIM	CE	Interior 1	Nordeste	15
URUBURETAMA	CE	Interior 1	Nordeste	15
URUOCA	CE	Interior 2	Nordeste	15
VARJOTA	CE	Interior 2	Nordeste	15
VARZEA ALEGRE	CE	Interior 2	Nordeste	15
VICOSA DO CEARA	CE	Interior 2	Nordeste	15
BRASÍLIA	DF	Brasília	Centro-Oeste	3
AFONSO CLAUDIO	ES	Interior 1	Sudeste	6
AGUA DOCE DO NORTE	ES	Interior 1	Sudeste	6
AGUIA BRANCA	ES	Interior 1	Sudeste	6
ALEGRE	ES	Interior 1	Sudeste	6
ALFREDO CHAVES	ES	Interior 1	Sudeste	6
ALTO RIO NOVO	ES	Interior 1	Sudeste	6
ANCHIETA	ES	Interior 1	Sudeste	6
APIACA	ES	Interior 1	Sudeste	6
ARACRUZ	ES	Interior 1	Sudeste	6
ATILIO VIVACQUA	ES	Interior 1	Sudeste	6
BAIXO GUANDU	ES	Interior 1	Sudeste	6
BARRA DE SAO FRANCISCO	ES	Interior 1	Sudeste	6
BOA ESPERANCA	ES	Interior 1	Sudeste	6
BOM JESUS DO NORTE	ES	Interior 1	Sudeste	6
BREJETUBA	ES	Interior 1	Sudeste	6
CACHOEIRO DE ITAPEMIRIM	ES	Interior 1	Sudeste	6
CARIACICA	ES	Capital	Sudeste	3
CASTELO	ES	Interior 1	Sudeste	6
COLATINA	ES	Interior 1	Sudeste	6
CONCEICAO DA BARRA	ES	Interior 1	Sudeste	6
CONCEICAO DO CASTELO	ES	Interior 1	Sudeste	6
DIVINO DE SAO LOURENCO	ES	Interior 1	Sudeste	6
DOMINGOS MARTINS	ES	Interior 1	Sudeste	6
DORES DO RIO PRETO	ES	Interior 1	Sudeste	6
ECOPORANGA	ES	Interior 1	Sudeste	6
FUNDAO	ES	Interior 1	Sudeste	6
GOVERNADOR LINDENBERG	ES	Interior 1	Sudeste	6
GUACUI	ES	Interior 1	Sudeste	6
GUARAPARI	ES	Interior 1	Sudeste	6
IBATIBA	ES	Interior 1	Sudeste	6
IBIRACU	ES	Interior 1	Sudeste	6
IBITIRAMA	ES	Interior 1	Sudeste	6
ICONHA	ES	Interior 1	Sudeste	6
IRUPI	ES	Interior 1	Sudeste	6
ITAGUACU	ES	Interior 1	Sudeste	6
ITAPEMIRIM	ES	Interior 1	Sudeste	6
ITARANA	ES	Interior 1	Sudeste	6
IUNA	ES	Interior 1	Sudeste	6
JAGUARE	ES	Interior 1	Sudeste	6
JERONIMO MONTEIRO	ES	Interior 1	Sudeste	6
JOAO NEIVA	ES	Interior 1	Sudeste	6
LARANJA DA TERRA	ES	Interior 1	Sudeste	6
LINHARES	ES	Interior 1	Sudeste	6
MANTENOPOLIS	ES	Interior 1	Sudeste	6
MARATAIZES	ES	Interior 1	Sudeste	6
MARECHAL FLORIANO	ES	Interior 1	Sudeste	6
MARILANDIA	ES	Interior 1	Sudeste	6
MIMOSO DO SUL	ES	Interior 1	Sudeste	6
MONTANHA	ES	Interior 1	Sudeste	6
MUCURICI	ES	Interior 1	Sudeste	6
MUNIZ FREIRE	ES	Interior 1	Sudeste	6
MUQUI	ES	Interior 1	Sudeste	6
NOVA VENECIA	ES	Interior 1	Sudeste	6
PANCAS	ES	Interior 1	Sudeste	6
PEDRO CANARIO	ES	Interior 1	Sudeste	6
PINHEIROS	ES	Interior 1	Sudeste	6
PIUMA	ES	Interior 1	Sudeste	6
PONTO BELO	ES	Interior 1	Sudeste	6
PRESIDENTE KENNEDY	ES	Interior 1	Sudeste	6
RIO BANANAL	ES	Interior 1	Sudeste	6
RIO NOVO DO SUL	ES	Interior 1	Sudeste	6
SANTA LEOPOLDINA	ES	Interior 1	Sudeste	6
SANTA MARIA DE JETIBA	ES	Interior 1	Sudeste	6
SANTA TERESA	ES	Interior 1	Sudeste	6
SAO DOMINGOS DO NORTE	ES	Interior 1	Sudeste	6
SAO GABRIEL DA PALHA	ES	Interior 1	Sudeste	6
SAO JOSE DO CALCADO	ES	Interior 1	Sudeste	6
SAO MATEUS	ES	Interior 1	Sudeste	6
SAO ROQUE DO CANAA	ES	Interior 1	Sudeste	6
SERRA	ES	Capital	Sudeste	3
SOORETAMA	ES	Interior 1	Sudeste	6
VARGEM ALTA	ES	Interior 1	Sudeste	6
VENDA NOVA DO IMIGRANTE	ES	Interior 1	Sudeste	6
VIANA	ES	Capital	Sudeste	3
VILA PAVAO	ES	Interior 1	Sudeste	6
VILA VALERIO	ES	Interior 1	Sudeste	6
VILA VELHA	ES	Capital	Sudeste	3
VITORIA	ES	Capital	Sudeste	3
ABADIA DE GOIAS	GO	Interior 1	Centro-Oeste	6
ABADIANIA	GO	Interior 1	Centro-Oeste	6
ACREUNA	GO	Interior 1	Centro-Oeste	6
ADELANDIA	GO	Interior 1	Centro-Oeste	6
AGUA FRIA DE GOIAS	GO	Interior 1	Centro-Oeste	6
AGUA LIMPA	GO	Interior 1	Centro-Oeste	6
AGUAS LINDAS DE GOIAS	GO	Interior 1	Centro-Oeste	6
ALEXANIA	GO	Interior 1	Centro-Oeste	6
ALOANDIA	GO	Interior 1	Centro-Oeste	6
ALTO HORIZONTE	GO	Interior 1	Centro-Oeste	6
ALTO PARAISO DE GOIAS	GO	Interior 1	Centro-Oeste	6
ALVORADA DO NORTE	GO	Interior 1	Centro-Oeste	6
AMARALINA	GO	Interior 1	Centro-Oeste	6
AMERICANO DO BRASIL	GO	Interior 1	Centro-Oeste	6
AMORINOPOLIS	GO	Interior 1	Centro-Oeste	6
ANAPOLIS	GO	Capital	Centro-Oeste	3
ANHANGUERA	GO	Interior 1	Centro-Oeste	6
ANICUNS	GO	Interior 1	Centro-Oeste	6
APARECIDA DE GOIANIA	GO	Capital	Centro-Oeste	3
APARECIDA DO RIO DOCE	GO	Interior 1	Centro-Oeste	6
APORE	GO	Interior 1	Centro-Oeste	6
ARACU	GO	Interior 1	Centro-Oeste	6
ARAGARCAS	GO	Interior 1	Centro-Oeste	6
ARAGOIANIA	GO	Interior 1	Centro-Oeste	6
ARAGUAPAZ	GO	Interior 1	Centro-Oeste	6
ARENOPOLIS	GO	Interior 1	Centro-Oeste	6
ARUANA	GO	Interior 1	Centro-Oeste	6
AURILANDIA	GO	Interior 1	Centro-Oeste	6
AVELINOPOLIS	GO	Interior 1	Centro-Oeste	6
BALIZA	GO	Interior 1	Centro-Oeste	6
BARRO ALTO	GO	Interior 1	Centro-Oeste	6
BELA VISTA DE GOIAS	GO	Interior 1	Centro-Oeste	6
BOM JARDIM DE GOIAS	GO	Interior 1	Centro-Oeste	6
BOM JESUS DE GOIAS	GO	Interior 1	Centro-Oeste	6
BONFINOPOLIS	GO	Interior 1	Centro-Oeste	6
BONOPOLIS	GO	Interior 1	Centro-Oeste	6
BRAZABRANTES	GO	Interior 1	Centro-Oeste	6
BRITANIA	GO	Interior 1	Centro-Oeste	6
BURITI ALEGRE	GO	Interior 1	Centro-Oeste	6
BURITI DE GOIAS	GO	Interior 1	Centro-Oeste	6
BURITINOPOLIS	GO	Interior 1	Centro-Oeste	6
CABECEIRAS	GO	Interior 1	Centro-Oeste	6
CACHOEIRA ALTA	GO	Interior 1	Centro-Oeste	6
CACHOEIRA DE GOIAS	GO	Interior 1	Centro-Oeste	6
CACHOEIRA DOURADA	GO	Interior 1	Centro-Oeste	6
CACU	GO	Interior 1	Centro-Oeste	6
CAIAPONIA	GO	Interior 1	Centro-Oeste	6
CALDAS NOVAS	GO	Interior 1	Centro-Oeste	6
CALDAZINHA	GO	Interior 1	Centro-Oeste	6
CAMPESTRE DE GOIAS	GO	Interior 1	Centro-Oeste	6
CAMPINACU	GO	Interior 1	Centro-Oeste	6
CAMPINORTE	GO	Interior 1	Centro-Oeste	6
CAMPO ALEGRE DE GOIAS	GO	Interior 1	Centro-Oeste	6
CAMPO LIMPO DE GOIAS	GO	Interior 1	Centro-Oeste	6
CAMPOS BELOS	GO	Interior 1	Centro-Oeste	6
CAMPOS VERDES	GO	Interior 1	Centro-Oeste	6
CARMO DO RIO VERDE	GO	Interior 1	Centro-Oeste	6
CASTELANDIA	GO	Interior 1	Centro-Oeste	6
CATALAO	GO	Interior 1	Centro-Oeste	6
CATURAI	GO	Interior 1	Centro-Oeste	6
CAVALCANTE	GO	Interior 1	Centro-Oeste	6
CERES	GO	Interior 1	Centro-Oeste	6
CEZARINA	GO	Interior 1	Centro-Oeste	6
CHAPADAO DO CEU	GO	Interior 1	Centro-Oeste	6
CIDADE OCIDENTAL	GO	Interior 1	Centro-Oeste	6
COCALZINHO DE GOIAS	GO	Interior 1	Centro-Oeste	6
COLINAS DO SUL	GO	Interior 1	Centro-Oeste	6
CORREGO DO OURO	GO	Interior 1	Centro-Oeste	6
CORUMBA DE GOIAS	GO	Interior 1	Centro-Oeste	6
CORUMBAIBA	GO	Interior 1	Centro-Oeste	6
CRISTALINA	GO	Interior 1	Centro-Oeste	6
CRISTIANOPOLIS	GO	Interior 1	Centro-Oeste	6
CRIXAS	GO	Interior 1	Centro-Oeste	6
CROMINIA	GO	Interior 1	Centro-Oeste	6
CUMARI	GO	Interior 1	Centro-Oeste	6
DAMIANOPOLIS	GO	Interior 1	Centro-Oeste	6
DAMOLANDIA	GO	Interior 1	Centro-Oeste	6
DAVINOPOLIS	GO	Interior 1	Centro-Oeste	6
DIORAMA	GO	Interior 1	Centro-Oeste	6
DIVINOPOLIS DE GOIAS	GO	Interior 1	Centro-Oeste	6
DOVERLANDIA	GO	Interior 1	Centro-Oeste	6
EDEALINA	GO	Interior 1	Centro-Oeste	6
EDEIA	GO	Interior 1	Centro-Oeste	6
ESTRELA DO NORTE	GO	Interior 1	Centro-Oeste	6
FAINA	GO	Interior 1	Centro-Oeste	6
FAZENDA NOVA	GO	Interior 1	Centro-Oeste	6
FIRMINOPOLIS	GO	Interior 1	Centro-Oeste	6
FLORES DE GOIAS	GO	Interior 1	Centro-Oeste	6
FORMOSA	GO	Interior 1	Centro-Oeste	6
FORMOSO	GO	Interior 1	Centro-Oeste	6
GAMELEIRA DE GOIAS	GO	Interior 1	Centro-Oeste	6
GOIANAPOLIS	GO	Interior 1	Centro-Oeste	6
GOIANDIRA	GO	Interior 1	Centro-Oeste	6
GOIANESIA	GO	Interior 1	Centro-Oeste	6
GOIANIA	GO	Capital	Centro-Oeste	3
GOIANIRA	GO	Interior 1	Centro-Oeste	6
GOIAS	GO	Interior 1	Centro-Oeste	6
GOIATUBA	GO	Interior 1	Centro-Oeste	6
GOUVELANDIA	GO	Interior 1	Centro-Oeste	6
GUAPO	GO	Interior 1	Centro-Oeste	6
GUARAITA	GO	Interior 1	Centro-Oeste	6
GUARANI DE GOIAS	GO	Interior 1	Centro-Oeste	6
GUARINOS	GO	Interior 1	Centro-Oeste	6
HEITORAI	GO	Interior 1	Centro-Oeste	6
HIDROLANDIA	GO	Interior 1	Centro-Oeste	6
HIDROLINA	GO	Interior 1	Centro-Oeste	6
IACIARA	GO	Interior 1	Centro-Oeste	6
INACIOLANDIA	GO	Interior 1	Centro-Oeste	6
INDIARA	GO	Interior 1	Centro-Oeste	6
INHUMAS	GO	Interior 1	Centro-Oeste	6
IPAMERI	GO	Interior 1	Centro-Oeste	6
IPIRANGA DE GOIAS	GO	Interior 1	Centro-Oeste	6
IPORA	GO	Interior 1	Centro-Oeste	6
ISRAELANDIA	GO	Interior 1	Centro-Oeste	6
ITABERAI	GO	Interior 1	Centro-Oeste	6
ITAGUARI	GO	Interior 1	Centro-Oeste	6
ITAGUARU	GO	Interior 1	Centro-Oeste	6
ITAJA	GO	Interior 1	Centro-Oeste	6
ITAPACI	GO	Interior 1	Centro-Oeste	6
ITAPIRAPUA	GO	Interior 1	Centro-Oeste	6
ITAPURANGA	GO	Interior 1	Centro-Oeste	6
ITARUMA	GO	Interior 1	Centro-Oeste	6
ITAUCU	GO	Interior 1	Centro-Oeste	6
ITUMBIARA	GO	Interior 1	Centro-Oeste	6
IVOLANDIA	GO	Interior 1	Centro-Oeste	6
JANDAIA	GO	Interior 1	Centro-Oeste	6
JARAGUA	GO	Interior 1	Centro-Oeste	6
JATAI	GO	Interior 1	Centro-Oeste	6
JAUPACI	GO	Interior 1	Centro-Oeste	6
JESUPOLIS	GO	Interior 1	Centro-Oeste	6
JOVIANIA	GO	Interior 1	Centro-Oeste	6
JUSSARA	GO	Interior 1	Centro-Oeste	6
LAGOA SANTA	GO	Interior 1	Centro-Oeste	6
LEOPOLDO DE BULHOES	GO	Interior 1	Centro-Oeste	6
LUZIANIA	GO	Interior 1	Centro-Oeste	6
MAIRIPOTABA	GO	Interior 1	Centro-Oeste	6
MAMBAI	GO	Interior 1	Centro-Oeste	6
MARA ROSA	GO	Interior 1	Centro-Oeste	6
MARZAGAO	GO	Interior 1	Centro-Oeste	6
MATRINCHA	GO	Interior 1	Centro-Oeste	6
MAURILANDIA	GO	Interior 1	Centro-Oeste	6
MIMOSO DE GOIAS	GO	Interior 1	Centro-Oeste	6
MINACU	GO	Interior 1	Centro-Oeste	6
MINEIROS	GO	Interior 1	Centro-Oeste	6
MOIPORA	GO	Interior 1	Centro-Oeste	6
MONTE ALEGRE DE GOIAS	GO	Interior 1	Centro-Oeste	6
MONTES CLAROS DE GOIAS	GO	Interior 1	Centro-Oeste	6
MONTIVIDIU	GO	Interior 1	Centro-Oeste	6
MONTIVIDIU DO NORTE	GO	Interior 1	Centro-Oeste	6
MORRINHOS	GO	Interior 1	Centro-Oeste	6
MORRO AGUDO DE GOIAS	GO	Interior 1	Centro-Oeste	6
MOSSAMEDES	GO	Interior 1	Centro-Oeste	6
MOZARLANDIA	GO	Interior 1	Centro-Oeste	6
MUNDO NOVO	GO	Interior 1	Centro-Oeste	6
MUTUNOPOLIS	GO	Interior 1	Centro-Oeste	6
NAZARIO	GO	Interior 1	Centro-Oeste	6
NEROPOLIS	GO	Interior 1	Centro-Oeste	6
NIQUELANDIA	GO	Interior 1	Centro-Oeste	6
NOVA AMERICA	GO	Interior 1	Centro-Oeste	6
NOVA AURORA	GO	Interior 1	Centro-Oeste	6
NOVA CRIXAS	GO	Interior 1	Centro-Oeste	6
NOVA GLORIA	GO	Interior 1	Centro-Oeste	6
NOVA IGUACU DE GOIAS	GO	Interior 1	Centro-Oeste	6
NOVA ROMA	GO	Interior 1	Centro-Oeste	6
NOVA VENEZA	GO	Interior 1	Centro-Oeste	6
NOVO BRASIL	GO	Interior 1	Centro-Oeste	6
NOVO GAMA	GO	Interior 1	Centro-Oeste	6
NOVO PLANALTO	GO	Interior 1	Centro-Oeste	6
ORIZONA	GO	Interior 1	Centro-Oeste	6
OURO VERDE DE GOIAS	GO	Interior 1	Centro-Oeste	6
OUVIDOR	GO	Interior 1	Centro-Oeste	6
PADRE BERNARDO	GO	Interior 1	Centro-Oeste	6
PALESTINA DE GOIAS	GO	Interior 1	Centro-Oeste	6
PALMEIRAS DE GOIAS	GO	Interior 1	Centro-Oeste	6
PALMELO	GO	Interior 1	Centro-Oeste	6
PALMINOPOLIS	GO	Interior 1	Centro-Oeste	6
PANAMA	GO	Interior 1	Centro-Oeste	6
PARANAIGUARA	GO	Interior 1	Centro-Oeste	6
PARAUNA	GO	Interior 1	Centro-Oeste	6
PEROLANDIA	GO	Interior 1	Centro-Oeste	6
PETROLINA DE GOIAS	GO	Interior 1	Centro-Oeste	6
PILAR DE GOIAS	GO	Interior 1	Centro-Oeste	6
PIRACANJUBA	GO	Interior 1	Centro-Oeste	6
PIRANHAS	GO	Interior 1	Centro-Oeste	6
PIRENOPOLIS	GO	Interior 1	Centro-Oeste	6
PIRES DO RIO	GO	Interior 1	Centro-Oeste	6
PLANALTINA	GO	Interior 1	Centro-Oeste	6
PONTALINA	GO	Interior 1	Centro-Oeste	6
PORANGATU	GO	Interior 1	Centro-Oeste	6
PORTEIRAO	GO	Interior 1	Centro-Oeste	6
PORTELANDIA	GO	Interior 1	Centro-Oeste	6
POSSE	GO	Interior 1	Centro-Oeste	6
PROFESSOR JAMIL	GO	Interior 1	Centro-Oeste	6
QUIRINOPOLIS	GO	Interior 1	Centro-Oeste	6
RIALMA	GO	Interior 1	Centro-Oeste	6
RIANAPOLIS	GO	Interior 1	Centro-Oeste	6
RIO QUENTE	GO	Interior 1	Centro-Oeste	6
RIO VERDE	GO	Interior 1	Centro-Oeste	6
RUBIATABA	GO	Interior 1	Centro-Oeste	6
SANCLERLANDIA	GO	Interior 1	Centro-Oeste	6
SANTA BARBARA DE GOIAS	GO	Interior 1	Centro-Oeste	6
SANTA CRUZ DE GOIAS	GO	Interior 1	Centro-Oeste	6
SANTA FE DE GOIAS	GO	Interior 1	Centro-Oeste	6
SANTA HELENA DE GOIAS	GO	Interior 1	Centro-Oeste	6
SANTA ISABEL	GO	Interior 1	Centro-Oeste	6
SANTA RITA DO ARAGUAIA	GO	Interior 1	Centro-Oeste	6
SANTA RITA DO NOVO DESTINO	GO	Interior 1	Centro-Oeste	6
SANTA ROSA DE GOIAS	GO	Interior 1	Centro-Oeste	6
SANTA TEREZA DE GOIAS	GO	Interior 1	Centro-Oeste	6
SANTA TEREZINHA DE GOIAS	GO	Interior 1	Centro-Oeste	6
SANTO ANTONIO DA BARRA	GO	Interior 1	Centro-Oeste	6
SANTO ANTONIO DE GOIAS	GO	Interior 1	Centro-Oeste	6
SANTO ANTONIO DO DESCOBERTO	GO	Interior 1	Centro-Oeste	6
SAO DOMINGOS	GO	Interior 1	Centro-Oeste	6
SAO FRANCISCO DE GOIAS	GO	Interior 1	Centro-Oeste	6
SAO JOAO DA PARAUNA	GO	Interior 1	Centro-Oeste	6
SAO JOAO D ALIANCA	GO	Interior 1	Centro-Oeste	6
SAO LUIS DE MONTES BELOS	GO	Interior 1	Centro-Oeste	6
SAO LUIZ DO NORTE	GO	Interior 1	Centro-Oeste	6
SAO MIGUEL DO ARAGUAIA	GO	Interior 1	Centro-Oeste	6
SAO MIGUEL DO PASSA QUATRO	GO	Interior 1	Centro-Oeste	6
SAO PATRICIO	GO	Interior 1	Centro-Oeste	6
SAO SIMAO	GO	Interior 1	Centro-Oeste	6
SENADOR CANEDO	GO	Interior 1	Centro-Oeste	6
SERRANOPOLIS	GO	Interior 1	Centro-Oeste	6
SILVANIA	GO	Interior 1	Centro-Oeste	6
SIMOLANDIA	GO	Interior 1	Centro-Oeste	6
SITIO D ABADIA	GO	Interior 1	Centro-Oeste	6
TAQUARAL DE GOIAS	GO	Interior 1	Centro-Oeste	6
TERESINA DE GOIAS	GO	Interior 1	Centro-Oeste	6
TEREZOPOLIS DE GOIAS	GO	Interior 1	Centro-Oeste	6
TRES RANCHOS	GO	Interior 1	Centro-Oeste	6
TRINDADE	GO	Interior 1	Centro-Oeste	6
TROMBAS	GO	Interior 1	Centro-Oeste	6
TURVANIA	GO	Interior 1	Centro-Oeste	6
TURVELANDIA	GO	Interior 1	Centro-Oeste	6
UIRAPURU	GO	Interior 1	Centro-Oeste	6
URUACU	GO	Interior 1	Centro-Oeste	6
URUANA	GO	Interior 1	Centro-Oeste	6
URUTAI	GO	Interior 1	Centro-Oeste	6
VALPARAISO DE GOIAS	GO	Interior 1	Centro-Oeste	6
VARJAO	GO	Interior 1	Centro-Oeste	6
VIANOPOLIS	GO	Interior 1	Centro-Oeste	6
VICENTINOPOLIS	GO	Interior 1	Centro-Oeste	6
VILA BOA	GO	Interior 1	Centro-Oeste	6
VILA PROPICIO	GO	Interior 1	Centro-Oeste	6
ACAILANDIA	MA	Interior 1	Nordeste	15
AFONSO CUNHA	MA	Sob Consulta	Nordeste	Sob Consulta
AGUA DOCE DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
ALCANTARA	MA	Sob Consulta	Nordeste	Sob Consulta
ALDEIAS ALTAS	MA	Sob Consulta	Nordeste	Sob Consulta
ALTAMIRA DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
ALTO ALEGRE DO MARANHAO	MA	Interior 1	Nordeste	15
ALTO ALEGRE DO PINDARE	MA	Sob Consulta	Nordeste	Sob Consulta
ALTO PARNAIBA	MA	Sob Consulta	Nordeste	Sob Consulta
AMAPA DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
AMARANTE DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
ANAJATUBA	MA	Interior 1	Nordeste	15
ANAPURUS	MA	Sob Consulta	Nordeste	Sob Consulta
APICUM-ACU	MA	Sob Consulta	Nordeste	Sob Consulta
ARAGUANA	MA	Sob Consulta	Nordeste	Sob Consulta
ARAIOSES	MA	Sob Consulta	Nordeste	Sob Consulta
ARAME	MA	Sob Consulta	Nordeste	Sob Consulta
ARARI	MA	Interior 1	Nordeste	15
AXIXA	MA	Interior 1	Nordeste	15
BACABAL	MA	Interior 1	Nordeste	15
BACABEIRA	MA	Interior 1	Nordeste	15
BACURI	MA	Sob Consulta	Nordeste	Sob Consulta
BACURITUBA	MA	Sob Consulta	Nordeste	Sob Consulta
BALSAS	MA	Sob Consulta	Nordeste	Sob Consulta
BARAO DE GRAJAU	MA	Sob Consulta	Nordeste	Sob Consulta
BARRA DO CORDA	MA	Interior 1	Nordeste	15
BARREIRINHAS	MA	Interior 1	Nordeste	15
BELA VISTA DO MARANHAO	MA	Interior 1	Nordeste	15
BELAGUA	MA	Sob Consulta	Nordeste	Sob Consulta
BENEDITO LEITE	MA	Sob Consulta	Nordeste	Sob Consulta
BEQUIMAO	MA	Sob Consulta	Nordeste	Sob Consulta
BERNARDO DO MEARIM	MA	Interior 1	Nordeste	15
BOA VISTA DO GURUPI	MA	Sob Consulta	Nordeste	Sob Consulta
BOM JARDIM	MA	Interior 1	Nordeste	15
BOM JESUS DAS SELVAS	MA	Sob Consulta	Nordeste	Sob Consulta
BOM LUGAR	MA	Sob Consulta	Nordeste	Sob Consulta
BREJO	MA	Interior 1	Nordeste	15
BREJO DE AREIA	MA	Sob Consulta	Nordeste	Sob Consulta
BURITI	MA	Sob Consulta	Nordeste	Sob Consulta
BURITI BRAVO	MA	Sob Consulta	Nordeste	Sob Consulta
BURITICUPU	MA	Sob Consulta	Nordeste	Sob Consulta
BURITIRANA	MA	Sob Consulta	Nordeste	Sob Consulta
CACHOEIRA GRANDE	MA	Interior 1	Nordeste	15
CAJAPIO	MA	Sob Consulta	Nordeste	Sob Consulta
CAJARI	MA	Sob Consulta	Nordeste	Sob Consulta
CAMPESTRE DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
CANDIDO MENDES	MA	Sob Consulta	Nordeste	Sob Consulta
CANTANHEDE	MA	Interior 1	Nordeste	15
CAPINZAL DO NORTE	MA	Sob Consulta	Nordeste	Sob Consulta
CAROLINA	MA	Sob Consulta	Nordeste	Sob Consulta
CARUTAPERA	MA	Sob Consulta	Nordeste	Sob Consulta
CAXIAS	MA	Sob Consulta	Nordeste	Sob Consulta
CEDRAL	MA	Sob Consulta	Nordeste	Sob Consulta
CENTRAL DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
CENTRO DO GUILHERME	MA	Sob Consulta	Nordeste	Sob Consulta
CENTRO NOVO DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
CHAPADINHA	MA	Interior 1	Nordeste	15
CIDELANDIA	MA	Sob Consulta	Nordeste	Sob Consulta
CODO	MA	Interior 1	Nordeste	15
COELHO NETO	MA	Sob Consulta	Nordeste	Sob Consulta
COLINAS	MA	Interior 1	Nordeste	15
CONCEICAO DO LAGO-ACU	MA	Sob Consulta	Nordeste	Sob Consulta
COROATA	MA	Interior 1	Nordeste	15
CURURUPU	MA	Sob Consulta	Nordeste	Sob Consulta
DAVINOPOLIS	MA	Sob Consulta	Nordeste	Sob Consulta
DOM PEDRO	MA	Interior 1	Nordeste	15
DUQUE BACELAR	MA	Sob Consulta	Nordeste	Sob Consulta
ESPERANTINOPOLIS	MA	Sob Consulta	Nordeste	Sob Consulta
ESTREITO	MA	Sob Consulta	Nordeste	Sob Consulta
FEIRA NOVA DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
FERNANDO FALCAO	MA	Sob Consulta	Nordeste	Sob Consulta
FORMOSA DA SERRA NEGRA	MA	Sob Consulta	Nordeste	Sob Consulta
FORTALEZA DOS NOGUEIRAS	MA	Sob Consulta	Nordeste	Sob Consulta
FORTUNA	MA	Sob Consulta	Nordeste	Sob Consulta
GODOFREDO VIANA	MA	Sob Consulta	Nordeste	Sob Consulta
GONCALVES DIAS	MA	Sob Consulta	Nordeste	Sob Consulta
GOVERNADOR ARCHER	MA	Sob Consulta	Nordeste	Sob Consulta
GOVERNADOR EDISON LOBAO	MA	Sob Consulta	Nordeste	Sob Consulta
GOVERNADOR EUGENIO BARROS	MA	Sob Consulta	Nordeste	Sob Consulta
GOVERNADOR LUIZ ROCHA	MA	Sob Consulta	Nordeste	Sob Consulta
GOVERNADOR NEWTON BELLO	MA	Sob Consulta	Nordeste	Sob Consulta
GOVERNADOR NUNES FREIRE	MA	Sob Consulta	Nordeste	Sob Consulta
GRACA ARANHA	MA	Sob Consulta	Nordeste	Sob Consulta
GRAJAU	MA	Sob Consulta	Nordeste	Sob Consulta
GUIMARAES	MA	Sob Consulta	Nordeste	Sob Consulta
HUMBERTO DE CAMPOS	MA	Interior 1	Nordeste	15
ICATU	MA	Interior 1	Nordeste	15
IGARAPE DO MEIO	MA	Interior 1	Nordeste	15
IGARAPE GRANDE	MA	Interior 1	Nordeste	15
IMPERATRIZ	MA	Imperatriz	Nordeste	8
ITAIPAVA DO GRAJAU	MA	Sob Consulta	Nordeste	Sob Consulta
ITAPECURU MIRIM	MA	Interior 1	Nordeste	15
ITINGA DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
JATOBA	MA	Sob Consulta	Nordeste	Sob Consulta
JENIPAPO DOS VIEIRAS	MA	Sob Consulta	Nordeste	Sob Consulta
JOAO LISBOA	MA	Sob Consulta	Nordeste	Sob Consulta
JOSELANDIA	MA	Sob Consulta	Nordeste	Sob Consulta
JUNCO DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
LAGO DA PEDRA	MA	Interior 1	Nordeste	15
LAGO DO JUNCO	MA	Interior 1	Nordeste	15
LAGO DOS RODRIGUES	MA	Sob Consulta	Nordeste	Sob Consulta
LAGO VERDE	MA	Sob Consulta	Nordeste	Sob Consulta
LAGOA DO MATO	MA	Sob Consulta	Nordeste	Sob Consulta
LAGOA GRANDE DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
LAJEADO NOVO	MA	Sob Consulta	Nordeste	Sob Consulta
LIMA CAMPOS	MA	Interior 1	Nordeste	15
LORETO	MA	Sob Consulta	Nordeste	Sob Consulta
LUIS DOMINGUES	MA	Sob Consulta	Nordeste	Sob Consulta
MAGALHAES DE ALMEIDA	MA	Sob Consulta	Nordeste	Sob Consulta
MARACACUME	MA	Sob Consulta	Nordeste	Sob Consulta
MARAJA DO SENA	MA	Sob Consulta	Nordeste	Sob Consulta
MARANHAOZINHO	MA	Sob Consulta	Nordeste	Sob Consulta
MATA ROMA	MA	Sob Consulta	Nordeste	Sob Consulta
MATINHA	MA	Interior 1	Nordeste	15
MATOES	MA	Sob Consulta	Nordeste	Sob Consulta
MATOES DO NORTE	MA	Interior 1	Nordeste	15
MILAGRES DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
MIRADOR	MA	Sob Consulta	Nordeste	Sob Consulta
MIRANDA DO NORTE	MA	Interior 1	Nordeste	15
MIRINZAL	MA	Sob Consulta	Nordeste	Sob Consulta
MONCAO	MA	Interior 1	Nordeste	15
MONTES ALTOS	MA	Sob Consulta	Nordeste	Sob Consulta
MORROS	MA	Interior 1	Nordeste	15
NINA RODRIGUES	MA	Interior 1	Nordeste	15
NOVA COLINAS	MA	Sob Consulta	Nordeste	Sob Consulta
NOVA IORQUE	MA	Sob Consulta	Nordeste	Sob Consulta
NOVA OLINDA DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
OLHO D AGUA DAS CUNHAS	MA	Sob Consulta	Nordeste	Sob Consulta
OLINDA NOVA DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
PACO DO LUMIAR	MA	Interior 1	Nordeste	15
PALMEIRANDIA	MA	Sob Consulta	Nordeste	Sob Consulta
PARAIBANO	MA	Sob Consulta	Nordeste	Sob Consulta
PARNARAMA	MA	Sob Consulta	Nordeste	Sob Consulta
PASSAGEM FRANCA	MA	Sob Consulta	Nordeste	Sob Consulta
PASTOS BONS	MA	Sob Consulta	Nordeste	Sob Consulta
PAULINO NEVES	MA	Sob Consulta	Nordeste	Sob Consulta
PAULO RAMOS	MA	Sob Consulta	Nordeste	Sob Consulta
PEDREIRAS	MA	Interior 1	Nordeste	15
PEDRO DO ROSARIO	MA	Sob Consulta	Nordeste	Sob Consulta
PENALVA	MA	Interior 1	Nordeste	15
PERI MIRIM	MA	Sob Consulta	Nordeste	Sob Consulta
PERITORO	MA	Interior 1	Nordeste	15
PINDARE-MIRIM	MA	Interior 1	Nordeste	15
PINHEIRO	MA	Interior 1	Nordeste	15
PIO XII	MA	Interior 1	Nordeste	15
PIRAPEMAS	MA	Interior 1	Nordeste	15
POCAO DE PEDRAS	MA	Sob Consulta	Nordeste	Sob Consulta
PORTO FRANCO	MA	Sob Consulta	Nordeste	Sob Consulta
PORTO RICO DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
PRESIDENTE DUTRA	MA	Interior 1	Nordeste	15
PRESIDENTE JUSCELINO	MA	Interior 1	Nordeste	15
PRESIDENTE MEDICI	MA	Sob Consulta	Nordeste	Sob Consulta
PRESIDENTE SARNEY	MA	Sob Consulta	Nordeste	Sob Consulta
PRESIDENTE VARGAS	MA	Interior 1	Nordeste	15
PRIMEIRA CRUZ	MA	Sob Consulta	Nordeste	Sob Consulta
RAPOSA	MA	Interior 1	Nordeste	15
RIACHAO	MA	Sob Consulta	Nordeste	Sob Consulta
RIBAMAR FIQUENE	MA	Sob Consulta	Nordeste	Sob Consulta
ROSARIO	MA	Interior 1	Nordeste	15
SAMBAIBA	MA	Sob Consulta	Nordeste	Sob Consulta
SANTA FILOMENA DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
SANTA HELENA	MA	Sob Consulta	Nordeste	Sob Consulta
SANTA INES	MA	Interior 1	Nordeste	15
SANTA LUZIA	MA	Interior 1	Nordeste	15
SANTA LUZIA DO PARUA	MA	Sob Consulta	Nordeste	Sob Consulta
SANTA QUITERIA DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
SANTA RITA	MA	Interior 1	Nordeste	15
SANTANA DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
SANTO AMARO DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
SANTO ANTONIO DOS LOPES	MA	Sob Consulta	Nordeste	Sob Consulta
SAO BENEDITO DO RIO PRETO	MA	Sob Consulta	Nordeste	Sob Consulta
SAO BENTO	MA	Interior 1	Nordeste	15
SAO BERNARDO	MA	Sob Consulta	Nordeste	Sob Consulta
SAO DOMINGOS DO AZEITAO	MA	Sob Consulta	Nordeste	Sob Consulta
SAO DOMINGOS DO MARANHAO	MA	Interior 1	Nordeste	15
SAO FELIX DE BALSAS	MA	Sob Consulta	Nordeste	Sob Consulta
SAO FRANCISCO DO BREJAO	MA	Sob Consulta	Nordeste	Sob Consulta
SAO FRANCISCO DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
SAO JOAO BATISTA	MA	Sob Consulta	Nordeste	Sob Consulta
SAO JOAO DO CARU	MA	Sob Consulta	Nordeste	Sob Consulta
SAO JOAO DO PARAISO	MA	Sob Consulta	Nordeste	Sob Consulta
SAO JOAO DO SOTER	MA	Sob Consulta	Nordeste	Sob Consulta
SAO JOAO DOS PATOS	MA	Sob Consulta	Nordeste	Sob Consulta
SAO JOSE DE RIBAMAR	MA	Interior 1	Nordeste	15
SAO JOSE DOS BASILIOS	MA	Sob Consulta	Nordeste	Sob Consulta
SAO LUIS	MA	Capital	Nordeste	10
SAO LUIS GONZAGA DO MARANHAO	MA	Interior 1	Nordeste	15
SAO MATEUS DO MARANHAO	MA	Interior 1	Nordeste	15
SAO PEDRO DA AGUA BRANCA	MA	Sob Consulta	Nordeste	Sob Consulta
SAO PEDRO DOS CRENTES	MA	Sob Consulta	Nordeste	Sob Consulta
SAO RAIMUNDO DAS MANGABEIRAS	MA	Sob Consulta	Nordeste	Sob Consulta
SAO RAIMUNDO DO DOCA BEZERRA	MA	Sob Consulta	Nordeste	Sob Consulta
SAO ROBERTO	MA	Sob Consulta	Nordeste	Sob Consulta
SAO VICENTE FERRER	MA	Sob Consulta	Nordeste	Sob Consulta
SATUBINHA	MA	Sob Consulta	Nordeste	Sob Consulta
SENADOR ALEXANDRE COSTA	MA	Sob Consulta	Nordeste	Sob Consulta
SENADOR LA ROCQUE	MA	Sob Consulta	Nordeste	Sob Consulta
SERRANO DO MARANHAO	MA	Sob Consulta	Nordeste	Sob Consulta
SITIO NOVO	MA	Sob Consulta	Nordeste	Sob Consulta
SUCUPIRA DO NORTE	MA	Sob Consulta	Nordeste	Sob Consulta
SUCUPIRA DO RIACHAO	MA	Sob Consulta	Nordeste	Sob Consulta
TASSO FRAGOSO	MA	Sob Consulta	Nordeste	Sob Consulta
TIMBIRAS	MA	Sob Consulta	Nordeste	Sob Consulta
TIMON	MA	Interior 1	Nordeste	15
TRIZIDELA DO VALE	MA	Interior 1	Nordeste	15
TUFILANDIA	MA	Sob Consulta	Nordeste	Sob Consulta
TUNTUM	MA	Interior 1	Nordeste	15
TURIACU	MA	Sob Consulta	Nordeste	Sob Consulta
TURILANDIA	MA	Sob Consulta	Nordeste	Sob Consulta
TUTOIA	MA	Sob Consulta	Nordeste	Sob Consulta
URBANO SANTOS	MA	Interior 1	Nordeste	15
VARGEM GRANDE	MA	Interior 1	Nordeste	15
VIANA	MA	Interior 1	Nordeste	15
VILA NOVA DOS MARTIRIOS	MA	Sob Consulta	Nordeste	Sob Consulta
VITORIA DO MEARIM	MA	Interior 1	Nordeste	15
VITORINO FREIRE	MA	Interior 1	Nordeste	15
ZE DOCA	MA	Interior 1	Nordeste	15
ABADIA DOS DOURADOS	MG	Interior 2	Sudeste	5
ABAETE	MG	Interior 1	Sudeste	5
ABRE CAMPO	MG	Interior 2	Sudeste	5
ACAIACA	MG	Interior 1	Sudeste	5
ACUCENA	MG	Interior 2	Sudeste	5
AGUA BOA	MG	Interior 2	Sudeste	5
AGUA COMPRIDA	MG	Interior 2	Sudeste	5
AGUANIL	MG	Interior 2	Sudeste	5
AGUAS FORMOSAS	MG	Interior 2	Sudeste	5
AGUAS VERMELHAS	MG	Interior 2	Sudeste	5
AIMORES	MG	Interior 2	Sudeste	5
AIURUOCA	MG	Interior 2	Sudeste	5
ALAGOA	MG	Interior 2	Sudeste	5
ALBERTINA	MG	Interior 2	Sudeste	5
ALEM PARAIBA	MG	Interior 2	Sudeste	5
ALFENAS	MG	Interior 2	Sudeste	5
ALFREDO VASCONCELOS	MG	Interior 1	Sudeste	5
ALMENARA	MG	Interior 2	Sudeste	5
ALPERCATA	MG	Interior 2	Sudeste	5
ALPINOPOLIS	MG	Interior 2	Sudeste	5
ALTEROSA	MG	Interior 2	Sudeste	5
ALTO CAPARAO	MG	Interior 2	Sudeste	5
ALTO JEQUITIBA	MG	Interior 2	Sudeste	5
ALTO RIO DOCE	MG	Interior 2	Sudeste	5
ALVARENGA	MG	Interior 2	Sudeste	5
ALVINOPOLIS	MG	Interior 2	Sudeste	5
ALVORADA DE MINAS	MG	Interior 2	Sudeste	5
AMPARO DO SERRA	MG	Interior 1	Sudeste	5
ANDRADAS	MG	Interior 2	Sudeste	5
ANDRELANDIA	MG	Interior 2	Sudeste	5
ANGELANDIA	MG	Interior 2	Sudeste	5
ANTONIO CARLOS	MG	Interior 2	Sudeste	5
ANTONIO DIAS	MG	Interior 1	Sudeste	5
ANTONIO PRADO DE MINAS	MG	Interior 2	Sudeste	5
ARACAI	MG	Interior 1	Sudeste	5
ARACITABA	MG	Interior 2	Sudeste	5
ARACUAI	MG	Interior 2	Sudeste	5
ARAGUARI	MG	Interior 2	Sudeste	5
ARANTINA	MG	Interior 2	Sudeste	5
ARAPONGA	MG	Interior 2	Sudeste	5
ARAPORA	MG	Interior 2	Sudeste	5
ARAPUA	MG	Interior 1	Sudeste	5
ARAUJOS	MG	Interior 1	Sudeste	5
ARAXA	MG	Interior 1	Sudeste	5
ARCEBURGO	MG	Interior 2	Sudeste	5
ARCOS	MG	Interior 1	Sudeste	5
AREADO	MG	Interior 2	Sudeste	5
ARGIRITA	MG	Interior 2	Sudeste	5
ARICANDUVA	MG	Interior 2	Sudeste	5
ARINOS	MG	Interior 2	Sudeste	5
ASTOLFO DUTRA	MG	Interior 1	Sudeste	5
ATALEIA	MG	Interior 2	Sudeste	5
AUGUSTO DE LIMA	MG	Interior 2	Sudeste	5
BAEPENDI	MG	Interior 2	Sudeste	5
BALDIM	MG	Interior 1	Sudeste	5
BAMBUI	MG	Interior 2	Sudeste	5
BANDEIRA	MG	Interior 2	Sudeste	5
BANDEIRA DO SUL	MG	Interior 2	Sudeste	5
BARAO DE COCAIS	MG	Interior 1	Sudeste	5
BARAO DE MONTE ALTO	MG	Interior 2	Sudeste	5
BARBACENA	MG	Interior 1	Sudeste	5
BARRA LONGA	MG	Interior 1	Sudeste	5
BARROSO	MG	Interior 1	Sudeste	5
BELA VISTA DE MINAS	MG	Interior 1	Sudeste	5
BELMIRO BRAGA	MG	Interior 2	Sudeste	5
BELO HORIZONTE	MG	Capital	Sudeste	2
BELO ORIENTE	MG	Interior 1	Sudeste	5
BELO VALE	MG	Interior 2	Sudeste	5
BERILO	MG	Interior 2	Sudeste	5
BERIZAL	MG	Interior 2	Sudeste	5
BERTOPOLIS	MG	Interior 2	Sudeste	5
BETIM	MG	Interior 1	Sudeste	5
BIAS FORTES	MG	Interior 2	Sudeste	5
BICAS	MG	Interior 2	Sudeste	5
BIQUINHAS	MG	Interior 2	Sudeste	5
BOA ESPERANCA	MG	Interior 2	Sudeste	5
BOCAINA DE MINAS	MG	Interior 2	Sudeste	5
BOCAIUVA	MG	Interior 2	Sudeste	5
BOM DESPACHO	MG	Interior 1	Sudeste	5
BOM JARDIM DE MINAS	MG	Interior 2	Sudeste	5
BOM JESUS DA PENHA	MG	Interior 2	Sudeste	5
BOM JESUS DO AMPARO	MG	Interior 1	Sudeste	5
BOM JESUS DO GALHO	MG	Interior 2	Sudeste	5
BOM REPOUSO	MG	Interior 2	Sudeste	5
BOM SUCESSO	MG	Interior 2	Sudeste	5
BONFIM	MG	Interior 2	Sudeste	5
BONFINOPOLIS DE MINAS	MG	Interior 2	Sudeste	5
BONITO DE MINAS	MG	Interior 2	Sudeste	5
BORDA DA MATA	MG	Interior 2	Sudeste	5
BOTELHOS	MG	Interior 2	Sudeste	5
BOTUMIRIM	MG	Interior 2	Sudeste	5
BRAS PIRES	MG	Interior 2	Sudeste	5
BRASILANDIA DE MINAS	MG	Interior 2	Sudeste	5
BRASILIA DE MINAS	MG	Interior 2	Sudeste	5
BRASOPOLIS	MG	Interior 2	Sudeste	5
BRAUNAS	MG	Interior 1	Sudeste	5
BRUMADINHO	MG	Interior 1	Sudeste	5
BUENO BRANDAO	MG	Interior 2	Sudeste	5
BUENOPOLIS	MG	Interior 2	Sudeste	5
BUGRE	MG	Interior 2	Sudeste	5
BURITIS	MG	Interior 2	Sudeste	5
BURITIZEIRO	MG	Interior 2	Sudeste	5
CABECEIRA GRANDE	MG	Interior 2	Sudeste	5
CABO VERDE	MG	Interior 2	Sudeste	5
CACHOEIRA DA PRATA	MG	Interior 2	Sudeste	5
CACHOEIRA DE MINAS	MG	Interior 2	Sudeste	5
CACHOEIRA DE PAJEU	MG	Interior 2	Sudeste	5
CACHOEIRA DOURADA	MG	Interior 2	Sudeste	5
CAETANOPOLIS	MG	Interior 1	Sudeste	5
CAETE	MG	Interior 1	Sudeste	5
CAIANA	MG	Interior 2	Sudeste	5
CAJURI	MG	Interior 2	Sudeste	5
CALDAS	MG	Interior 2	Sudeste	5
CAMACHO	MG	Interior 2	Sudeste	5
CAMANDUCAIA	MG	Interior 2	Sudeste	5
CAMBUI	MG	Interior 2	Sudeste	5
CAMBUQUIRA	MG	Interior 2	Sudeste	5
CAMPANARIO	MG	Interior 2	Sudeste	5
CAMPANHA	MG	Interior 2	Sudeste	5
CAMPESTRE	MG	Interior 2	Sudeste	5
CAMPINA VERDE	MG	Interior 2	Sudeste	5
CAMPO AZUL	MG	Interior 2	Sudeste	5
CAMPO BELO	MG	Interior 2	Sudeste	5
CAMPO DO MEIO	MG	Interior 2	Sudeste	5
CAMPO FLORIDO	MG	Interior 2	Sudeste	5
CAMPOS ALTOS	MG	Interior 1	Sudeste	5
CAMPOS GERAIS	MG	Interior 2	Sudeste	5
CANA VERDE	MG	Interior 2	Sudeste	5
CANAA	MG	Interior 2	Sudeste	5
CANAPOLIS	MG	Interior 2	Sudeste	5
CANDEIAS	MG	Interior 2	Sudeste	5
CANTAGALO	MG	Interior 2	Sudeste	5
CAPARAO	MG	Interior 2	Sudeste	5
CAPELA NOVA	MG	Interior 2	Sudeste	5
CAPELINHA	MG	Interior 2	Sudeste	5
CAPETINGA	MG	Interior 2	Sudeste	5
CAPIM BRANCO	MG	Interior 1	Sudeste	5
CAPINOPOLIS	MG	Interior 2	Sudeste	5
CAPITAO ANDRADE	MG	Interior 2	Sudeste	5
CAPITAO ENEAS	MG	Interior 2	Sudeste	5
CAPITOLIO	MG	Interior 2	Sudeste	5
CAPUTIRA	MG	Interior 2	Sudeste	5
CARAI	MG	Interior 2	Sudeste	5
CARANAIBA	MG	Interior 2	Sudeste	5
CARANDAI	MG	Interior 1	Sudeste	5
CARANGOLA	MG	Interior 2	Sudeste	5
CARATINGA	MG	Interior 2	Sudeste	5
CARBONITA	MG	Interior 2	Sudeste	5
CAREACU	MG	Interior 2	Sudeste	5
CARLOS CHAGAS	MG	Interior 2	Sudeste	5
CARMESIA	MG	Interior 2	Sudeste	5
CARMO DA CACHOEIRA	MG	Interior 2	Sudeste	5
CARMO DA MATA	MG	Interior 2	Sudeste	5
CARMO DE MINAS	MG	Interior 2	Sudeste	5
CARMO DO CAJURU	MG	Interior 1	Sudeste	5
CARMO DO PARNAIBA	MG	Interior 1	Sudeste	5
CARMO DO RIO CLARO	MG	Interior 2	Sudeste	5
CARMOPOLIS DE MINAS	MG	Interior 2	Sudeste	5
CARNEIRINHO	MG	Interior 2	Sudeste	5
CARRANCAS	MG	Interior 2	Sudeste	5
CARVALHOPOLIS	MG	Interior 2	Sudeste	5
CARVALHOS	MG	Interior 2	Sudeste	5
CASA GRANDE	MG	Interior 2	Sudeste	5
CASCALHO RICO	MG	Interior 2	Sudeste	5
CASSIA	MG	Interior 2	Sudeste	5
CATAGUASES	MG	Interior 1	Sudeste	5
CATAS ALTAS	MG	Interior 2	Sudeste	5
CATAS ALTAS DA NORUEGA	MG	Interior 2	Sudeste	5
CATUJI	MG	Interior 2	Sudeste	5
CATUTI	MG	Interior 2	Sudeste	5
CAXAMBU	MG	Interior 2	Sudeste	5
CEDRO DO ABAETE	MG	Interior 2	Sudeste	5
CENTRAL DE MINAS	MG	Interior 2	Sudeste	5
CENTRALINA	MG	Interior 2	Sudeste	5
CHACARA	MG	Interior 2	Sudeste	5
CHALE	MG	Interior 2	Sudeste	5
CHAPADA DO NORTE	MG	Interior 2	Sudeste	5
CHAPADA GAUCHA	MG	Interior 2	Sudeste	5
CHIADOR	MG	Interior 2	Sudeste	5
CIPOTANEA	MG	Interior 2	Sudeste	5
CLARAVAL	MG	Interior 2	Sudeste	5
CLARO DOS POCOES	MG	Interior 2	Sudeste	5
CLAUDIO	MG	Interior 1	Sudeste	5
COIMBRA	MG	Interior 2	Sudeste	5
COLUNA	MG	Interior 2	Sudeste	5
COMENDADOR GOMES	MG	Interior 2	Sudeste	5
COMERCINHO	MG	Interior 2	Sudeste	5
CONCEICAO DA APARECIDA	MG	Interior 2	Sudeste	5
CONCEICAO DA BARRA DE MINAS	MG	Interior 2	Sudeste	5
CONCEICAO DAS ALAGOAS	MG	Interior 2	Sudeste	5
CONCEICAO DAS PEDRAS	MG	Interior 2	Sudeste	5
CONCEICAO DE IPANEMA	MG	Interior 2	Sudeste	5
CONCEICAO DO MATO DENTRO	MG	Interior 2	Sudeste	5
CONCEICAO DO PARA	MG	Interior 2	Sudeste	5
CONCEICAO DO RIO VERDE	MG	Interior 2	Sudeste	5
CONCEICAO DOS OUROS	MG	Interior 2	Sudeste	5
CONEGO MARINHO	MG	Interior 2	Sudeste	5
CONFINS	MG	Interior 1	Sudeste	5
CONGONHAL	MG	Interior 2	Sudeste	5
CONGONHAS	MG	Interior 1	Sudeste	5
CONGONHAS DO NORTE	MG	Interior 2	Sudeste	5
CONQUISTA	MG	Interior 2	Sudeste	5
CONSELHEIRO LAFAIETE	MG	Interior 1	Sudeste	5
CONSELHEIRO PENA	MG	Interior 2	Sudeste	5
CONSOLACAO	MG	Interior 2	Sudeste	5
CONTAGEM	MG	Interior 1	Sudeste	5
COQUEIRAL	MG	Interior 2	Sudeste	5
CORACAO DE JESUS	MG	Interior 2	Sudeste	5
CORDISBURGO	MG	Interior 1	Sudeste	5
CORDISLANDIA	MG	Interior 2	Sudeste	5
CORINTO	MG	Interior 1	Sudeste	5
COROACI	MG	Interior 2	Sudeste	5
COROMANDEL	MG	Interior 2	Sudeste	5
CORONEL FABRICIANO	MG	Interior 1	Sudeste	5
CORONEL MURTA	MG	Interior 2	Sudeste	5
CORONEL PACHECO	MG	Interior 2	Sudeste	5
CORONEL XAVIER CHAVES	MG	Interior 2	Sudeste	5
CORREGO DANTA	MG	Interior 1	Sudeste	5
CORREGO DO BOM JESUS	MG	Interior 2	Sudeste	5
CORREGO FUNDO	MG	Interior 2	Sudeste	5
CORREGO NOVO	MG	Interior 2	Sudeste	5
COUTO DE MAGALHAES DE MINAS	MG	Interior 2	Sudeste	5
CRISOLITA	MG	Interior 2	Sudeste	5
CRISTAIS	MG	Interior 2	Sudeste	5
CRISTALIA	MG	Interior 2	Sudeste	5
CRISTIANO OTONI	MG	Interior 1	Sudeste	5
CRISTINA	MG	Interior 2	Sudeste	5
CRUCILANDIA	MG	Interior 2	Sudeste	5
CRUZEIRO DA FORTALEZA	MG	Interior 2	Sudeste	5
CRUZILIA	MG	Interior 2	Sudeste	5
CUPARAQUE	MG	Interior 2	Sudeste	5
CURRAL DE DENTRO	MG	Interior 2	Sudeste	5
CURVELO	MG	Interior 1	Sudeste	5
DATAS	MG	Interior 2	Sudeste	5
DELFIM MOREIRA	MG	Interior 2	Sudeste	5
DELFINOPOLIS	MG	Interior 2	Sudeste	5
DELTA	MG	Interior 2	Sudeste	5
DESCOBERTO	MG	Interior 2	Sudeste	5
DESTERRO DE ENTRE RIOS	MG	Interior 2	Sudeste	5
DESTERRO DO MELO	MG	Interior 2	Sudeste	5
DIAMANTINA	MG	Interior 2	Sudeste	5
DIOGO DE VASCONCELOS	MG	Interior 2	Sudeste	5
DIONISIO	MG	Interior 2	Sudeste	5
DIVINESIA	MG	Interior 2	Sudeste	5
DIVINO	MG	Interior 2	Sudeste	5
DIVINO DAS LARANJEIRAS	MG	Interior 2	Sudeste	5
DIVINOLANDIA DE MINAS	MG	Interior 2	Sudeste	5
DIVINOPOLIS	MG	Interior 1	Sudeste	5
DIVISA ALEGRE	MG	Interior 2	Sudeste	5
DIVISA NOVA	MG	Interior 2	Sudeste	5
DIVISOPOLIS	MG	Interior 2	Sudeste	5
DOM BOSCO	MG	Interior 2	Sudeste	5
DOM CAVATI	MG	Interior 2	Sudeste	5
DOM JOAQUIM	MG	Interior 2	Sudeste	5
DOM SILVERIO	MG	Interior 2	Sudeste	5
DOM VICOSO	MG	Interior 2	Sudeste	5
DONA EUSEBIA	MG	Interior 2	Sudeste	5
DORES DE CAMPOS	MG	Interior 1	Sudeste	5
DORES DE GUANHAES	MG	Interior 2	Sudeste	5
DORES DO INDAIA	MG	Interior 1	Sudeste	5
DORES DO TURVO	MG	Interior 2	Sudeste	5
DORESOPOLIS	MG	Interior 2	Sudeste	5
DOURADOQUARA	MG	Interior 2	Sudeste	5
DURANDE	MG	Interior 2	Sudeste	5
ELOI MENDES	MG	Interior 2	Sudeste	5
ENGENHEIRO CALDAS	MG	Interior 2	Sudeste	5
ENGENHEIRO NAVARRO	MG	Interior 2	Sudeste	5
ENTRE FOLHAS	MG	Interior 2	Sudeste	5
ENTRE RIOS DE MINAS	MG	Interior 1	Sudeste	5
ERVALIA	MG	Interior 1	Sudeste	5
ESMERALDAS	MG	Interior 2	Sudeste	5
ESPERA FELIZ	MG	Interior 2	Sudeste	5
ESPINOSA	MG	Interior 2	Sudeste	5
ESPIRITO SANTO DO DOURADO	MG	Interior 2	Sudeste	5
ESTIVA	MG	Interior 2	Sudeste	5
ESTRELA DALVA	MG	Interior 2	Sudeste	5
ESTRELA DO INDAIA	MG	Interior 2	Sudeste	5
ESTRELA DO SUL	MG	Interior 2	Sudeste	5
EUGENOPOLIS	MG	Interior 2	Sudeste	5
EWBANK DA CAMARA	MG	Interior 2	Sudeste	5
EXTREMA	MG	Interior 2	Sudeste	5
FAMA	MG	Interior 2	Sudeste	5
FARIA LEMOS	MG	Interior 2	Sudeste	5
FELICIO DOS SANTOS	MG	Interior 2	Sudeste	5
FELISBURGO	MG	Interior 2	Sudeste	5
FELIXLANDIA	MG	Interior 2	Sudeste	5
FERNANDES TOURINHO	MG	Interior 2	Sudeste	5
FERROS	MG	Interior 1	Sudeste	5
FERVEDOURO	MG	Interior 2	Sudeste	5
FLORESTAL	MG	Interior 1	Sudeste	5
FORMIGA	MG	Interior 1	Sudeste	5
FORMOSO	MG	Interior 2	Sudeste	5
FORTALEZA DE MINAS	MG	Interior 2	Sudeste	5
FORTUNA DE MINAS	MG	Interior 2	Sudeste	5
FRANCISCO BADARO	MG	Interior 2	Sudeste	5
FRANCISCO DUMONT	MG	Interior 2	Sudeste	5
FRANCISCO SA	MG	Interior 2	Sudeste	5
FRANCISCOPOLIS	MG	Interior 2	Sudeste	5
FREI GASPAR	MG	Interior 2	Sudeste	5
FREI INOCENCIO	MG	Interior 2	Sudeste	5
FREI LAGONEGRO	MG	Interior 2	Sudeste	5
FRONTEIRA	MG	Interior 2	Sudeste	5
FRONTEIRA DOS VALES	MG	Interior 2	Sudeste	5
FRUTA DE LEITE	MG	Interior 2	Sudeste	5
FRUTAL	MG	Interior 2	Sudeste	5
FUNILANDIA	MG	Interior 1	Sudeste	5
GALILEIA	MG	Interior 2	Sudeste	5
GAMELEIRAS	MG	Interior 2	Sudeste	5
GLAUCILANDIA	MG	Interior 2	Sudeste	5
GOIABEIRA	MG	Interior 2	Sudeste	5
GOIANA	MG	Interior 2	Sudeste	5
GONCALVES	MG	Interior 2	Sudeste	5
GONZAGA	MG	Interior 2	Sudeste	5
GOUVEIA	MG	Interior 2	Sudeste	5
GOVERNADOR VALADARES	MG	Interior 2	Sudeste	5
GRAO MOGOL	MG	Interior 2	Sudeste	5
GRUPIARA	MG	Interior 2	Sudeste	5
GUANHAES	MG	Interior 2	Sudeste	5
GUAPE	MG	Interior 2	Sudeste	5
GUARACIABA	MG	Interior 1	Sudeste	5
GUARACIAMA	MG	Interior 2	Sudeste	5
GUARANESIA	MG	Interior 2	Sudeste	5
GUARANI	MG	Interior 2	Sudeste	5
GUARARA	MG	Interior 2	Sudeste	5
GUARDA-MOR	MG	Interior 2	Sudeste	5
GUAXUPE	MG	Interior 2	Sudeste	5
GUIDOVAL	MG	Interior 2	Sudeste	5
GUIMARANIA	MG	Interior 2	Sudeste	5
GUIRICEMA	MG	Interior 2	Sudeste	5
GURINHATA	MG	Interior 2	Sudeste	5
HELIODORA	MG	Interior 2	Sudeste	5
IAPU	MG	Interior 2	Sudeste	5
IBERTIOGA	MG	Interior 2	Sudeste	5
IBIA	MG	Interior 1	Sudeste	5
IBIAI	MG	Interior 2	Sudeste	5
IBIRACATU	MG	Interior 2	Sudeste	5
IBIRACI	MG	Interior 2	Sudeste	5
IBIRITE	MG	Interior 1	Sudeste	5
IBITIURA DE MINAS	MG	Interior 2	Sudeste	5
IBITURUNA	MG	Interior 2	Sudeste	5
ICARAI DE MINAS	MG	Interior 2	Sudeste	5
IGARAPE	MG	Interior 1	Sudeste	5
IGARATINGA	MG	Interior 2	Sudeste	5
IGUATAMA	MG	Interior 2	Sudeste	5
IJACI	MG	Interior 2	Sudeste	5
ILICINEA	MG	Interior 2	Sudeste	5
IMBE DE MINAS	MG	Interior 2	Sudeste	5
INCONFIDENTES	MG	Interior 2	Sudeste	5
INDAIABIRA	MG	Interior 2	Sudeste	5
INDIANOPOLIS	MG	Interior 2	Sudeste	5
INGAI	MG	Interior 2	Sudeste	5
INHAPIM	MG	Interior 2	Sudeste	5
INHAUMA	MG	Interior 1	Sudeste	5
INIMUTABA	MG	Interior 2	Sudeste	5
IPABA	MG	Interior 2	Sudeste	5
IPANEMA	MG	Interior 2	Sudeste	5
IPATINGA	MG	Interior 1	Sudeste	5
IPIACU	MG	Interior 2	Sudeste	5
IPUIUNA	MG	Interior 2	Sudeste	5
IRAI DE MINAS	MG	Interior 2	Sudeste	5
ITABIRA	MG	Interior 1	Sudeste	5
ITABIRINHA	MG	Interior 2	Sudeste	5
ITABIRITO	MG	Interior 1	Sudeste	5
ITACAMBIRA	MG	Interior 2	Sudeste	5
ITACARAMBI	MG	Interior 2	Sudeste	5
ITAGUARA	MG	Interior 1	Sudeste	5
ITAIPE	MG	Interior 2	Sudeste	5
ITAJUBA	MG	Interior 2	Sudeste	5
ITAMARANDIBA	MG	Interior 2	Sudeste	5
ITAMARATI DE MINAS	MG	Interior 1	Sudeste	5
ITAMBACURI	MG	Interior 2	Sudeste	5
ITAMBE DO MATO DENTRO	MG	Interior 2	Sudeste	5
ITAMOGI	MG	Interior 2	Sudeste	5
ITAMONTE	MG	Interior 2	Sudeste	5
ITANHANDU	MG	Interior 2	Sudeste	5
ITANHOMI	MG	Interior 2	Sudeste	5
ITAOBIM	MG	Interior 2	Sudeste	5
ITAPAGIPE	MG	Interior 2	Sudeste	5
ITAPECERICA	MG	Interior 2	Sudeste	5
ITAPEVA	MG	Interior 2	Sudeste	5
ITATIAIUCU	MG	Interior 1	Sudeste	5
ITAU DE MINAS	MG	Interior 2	Sudeste	5
ITAUNA	MG	Interior 1	Sudeste	5
ITAVERAVA	MG	Interior 1	Sudeste	5
ITINGA	MG	Interior 2	Sudeste	5
ITUETA	MG	Interior 2	Sudeste	5
ITUIUTABA	MG	Interior 2	Sudeste	5
ITUMIRIM	MG	Interior 2	Sudeste	5
ITURAMA	MG	Interior 2	Sudeste	5
ITUTINGA	MG	Interior 2	Sudeste	5
JABOTICATUBAS	MG	Interior 1	Sudeste	5
JACINTO	MG	Interior 2	Sudeste	5
JACUI	MG	Interior 2	Sudeste	5
JACUTINGA	MG	Interior 2	Sudeste	5
JAGUARACU	MG	Interior 2	Sudeste	5
JAIBA	MG	Interior 2	Sudeste	5
JAMPRUCA	MG	Interior 2	Sudeste	5
JANAUBA	MG	Interior 2	Sudeste	5
JANUARIA	MG	Interior 2	Sudeste	5
JAPARAIBA	MG	Interior 2	Sudeste	5
JAPONVAR	MG	Interior 2	Sudeste	5
JECEABA	MG	Interior 1	Sudeste	5
JENIPAPO DE MINAS	MG	Interior 2	Sudeste	5
JEQUERI	MG	Interior 2	Sudeste	5
JEQUITAI	MG	Interior 2	Sudeste	5
JEQUITIBA	MG	Interior 2	Sudeste	5
JEQUITINHONHA	MG	Interior 2	Sudeste	5
JESUANIA	MG	Interior 2	Sudeste	5
JOAIMA	MG	Interior 2	Sudeste	5
JOANESIA	MG	Interior 2	Sudeste	5
JOAO MONLEVADE	MG	Interior 1	Sudeste	5
JOAO PINHEIRO	MG	Interior 2	Sudeste	5
JOAQUIM FELICIO	MG	Interior 2	Sudeste	5
JORDANIA	MG	Interior 2	Sudeste	5
JOSE GONCALVES DE MINAS	MG	Interior 2	Sudeste	5
JOSE RAYDAN	MG	Interior 2	Sudeste	5
JOSENOPOLIS	MG	Interior 2	Sudeste	5
JUATUBA	MG	Interior 1	Sudeste	5
JUIZ DE FORA	MG	Interior 1	Sudeste	5
JURAMENTO	MG	Interior 2	Sudeste	5
JURUAIA	MG	Interior 2	Sudeste	5
JUVENILIA	MG	Interior 2	Sudeste	5
LADAINHA	MG	Interior 2	Sudeste	5
LAGAMAR	MG	Interior 2	Sudeste	5
LAGOA DA PRATA	MG	Interior 1	Sudeste	5
LAGOA DOS PATOS	MG	Interior 2	Sudeste	5
LAGOA DOURADA	MG	Interior 2	Sudeste	5
LAGOA FORMOSA	MG	Interior 1	Sudeste	5
LAGOA GRANDE	MG	Interior 2	Sudeste	5
LAGOA SANTA	MG	Interior 1	Sudeste	5
LAJINHA	MG	Interior 2	Sudeste	5
LAMBARI	MG	Interior 2	Sudeste	5
LAMIM	MG	Interior 2	Sudeste	5
LARANJAL	MG	Interior 2	Sudeste	5
LASSANCE	MG	Interior 2	Sudeste	5
LAVRAS	MG	Interior 2	Sudeste	5
LEANDRO FERREIRA	MG	Interior 2	Sudeste	5
LEME DO PRADO	MG	Interior 2	Sudeste	5
LEOPOLDINA	MG	Interior 2	Sudeste	5
LIBERDADE	MG	Interior 2	Sudeste	5
LIMA DUARTE	MG	Interior 2	Sudeste	5
LIMEIRA DO OESTE	MG	Interior 2	Sudeste	5
LONTRA	MG	Interior 2	Sudeste	5
LUISBURGO	MG	Interior 2	Sudeste	5
LUISLANDIA	MG	Interior 2	Sudeste	5
LUMINARIAS	MG	Interior 2	Sudeste	5
LUZ	MG	Interior 1	Sudeste	5
MACHACALIS	MG	Interior 2	Sudeste	5
MACHADO	MG	Interior 2	Sudeste	5
MADRE DE DEUS DE MINAS	MG	Interior 2	Sudeste	5
MALACACHETA	MG	Interior 2	Sudeste	5
MAMONAS	MG	Interior 2	Sudeste	5
MANGA	MG	Interior 2	Sudeste	5
MANHUACU	MG	Interior 2	Sudeste	5
MANHUMIRIM	MG	Interior 2	Sudeste	5
MANTENA	MG	Interior 2	Sudeste	5
MAR DE ESPANHA	MG	Interior 2	Sudeste	5
MARAVILHAS	MG	Interior 2	Sudeste	5
MARIA DA FE	MG	Interior 2	Sudeste	5
MARIANA	MG	Interior 1	Sudeste	5
MARILAC	MG	Interior 2	Sudeste	5
MARIO CAMPOS	MG	Interior 1	Sudeste	5
MARIPA DE MINAS	MG	Interior 2	Sudeste	5
MARLIERIA	MG	Interior 1	Sudeste	5
MARMELOPOLIS	MG	Interior 2	Sudeste	5
MARTINHO CAMPOS	MG	Interior 2	Sudeste	5
MARTINS SOARES	MG	Interior 2	Sudeste	5
MATA VERDE	MG	Interior 2	Sudeste	5
MATERLANDIA	MG	Interior 2	Sudeste	5
MATEUS LEME	MG	Interior 1	Sudeste	5
MATHIAS LOBATO	MG	Interior 2	Sudeste	5
MATIAS BARBOSA	MG	Interior 2	Sudeste	5
MATIAS CARDOSO	MG	Interior 2	Sudeste	5
MATIPO	MG	Interior 2	Sudeste	5
MATO VERDE	MG	Interior 2	Sudeste	5
MATOZINHOS	MG	Interior 1	Sudeste	5
MATUTINA	MG	Interior 1	Sudeste	5
MEDEIROS	MG	Interior 2	Sudeste	5
MEDINA	MG	Interior 2	Sudeste	5
MENDES PIMENTEL	MG	Interior 2	Sudeste	5
MERCES	MG	Interior 2	Sudeste	5
MESQUITA	MG	Interior 2	Sudeste	5
MINAS NOVAS	MG	Interior 2	Sudeste	5
MINDURI	MG	Interior 2	Sudeste	5
MIRABELA	MG	Interior 2	Sudeste	5
MIRADOURO	MG	Interior 2	Sudeste	5
MIRAI	MG	Interior 1	Sudeste	5
MIRAVANIA	MG	Interior 2	Sudeste	5
MOEDA	MG	Interior 1	Sudeste	5
MOEMA	MG	Interior 1	Sudeste	5
MONJOLOS	MG	Interior 2	Sudeste	5
MONSENHOR PAULO	MG	Interior 2	Sudeste	5
MONTALVANIA	MG	Interior 2	Sudeste	5
MONTE ALEGRE DE MINAS	MG	Interior 2	Sudeste	5
MONTE AZUL	MG	Interior 2	Sudeste	5
MONTE BELO	MG	Interior 2	Sudeste	5
MONTE CARMELO	MG	Interior 2	Sudeste	5
MONTE FORMOSO	MG	Interior 2	Sudeste	5
MONTE SANTO DE MINAS	MG	Interior 2	Sudeste	5
MONTE SIAO	MG	Interior 2	Sudeste	5
MONTES CLAROS	MG	Interior 2	Sudeste	5
MONTEZUMA	MG	Interior 2	Sudeste	5
MORADA NOVA DE MINAS	MG	Interior 2	Sudeste	5
MORRO DA GARCA	MG	Interior 2	Sudeste	5
MORRO DO PILAR	MG	Interior 2	Sudeste	5
MUNHOZ	MG	Interior 2	Sudeste	5
MURIAE	MG	Interior 1	Sudeste	5
MUTUM	MG	Interior 2	Sudeste	5
MUZAMBINHO	MG	Interior 2	Sudeste	5
NACIP RAYDAN	MG	Interior 2	Sudeste	5
NANUQUE	MG	Interior 2	Sudeste	5
NAQUE	MG	Interior 2	Sudeste	5
NATALANDIA	MG	Interior 2	Sudeste	5
NATERCIA	MG	Interior 2	Sudeste	5
NAZARENO	MG	Interior 2	Sudeste	5
NEPOMUCENO	MG	Interior 2	Sudeste	5
NINHEIRA	MG	Interior 2	Sudeste	5
NOVA BELEM	MG	Interior 2	Sudeste	5
NOVA ERA	MG	Interior 1	Sudeste	5
NOVA LIMA	MG	Interior 1	Sudeste	5
NOVA MODICA	MG	Interior 2	Sudeste	5
NOVA PONTE	MG	Interior 2	Sudeste	5
NOVA PORTEIRINHA	MG	Interior 2	Sudeste	5
NOVA RESENDE	MG	Interior 2	Sudeste	5
NOVA SERRANA	MG	Interior 1	Sudeste	5
NOVA UNIAO	MG	Interior 1	Sudeste	5
NOVO CRUZEIRO	MG	Interior 2	Sudeste	5
NOVO ORIENTE DE MINAS	MG	Interior 2	Sudeste	5
NOVORIZONTE	MG	Interior 2	Sudeste	5
OLARIA	MG	Interior 2	Sudeste	5
OLHOS-D AGUA	MG	Interior 2	Sudeste	5
OLIMPIO NORONHA	MG	Interior 2	Sudeste	5
OLIVEIRA	MG	Interior 1	Sudeste	5
OLIVEIRA FORTES	MG	Interior 2	Sudeste	5
ONCA DE PITANGUI	MG	Interior 1	Sudeste	5
ORATORIOS	MG	Interior 2	Sudeste	5
ORIZANIA	MG	Interior 2	Sudeste	5
OURO BRANCO	MG	Interior 1	Sudeste	5
OURO FINO	MG	Interior 2	Sudeste	5
OURO PRETO	MG	Interior 1	Sudeste	5
OURO VERDE DE MINAS	MG	Interior 2	Sudeste	5
PADRE CARVALHO	MG	Interior 2	Sudeste	5
PADRE PARAISO	MG	Interior 2	Sudeste	5
PAI PEDRO	MG	Interior 2	Sudeste	5
PAINEIRAS	MG	Interior 2	Sudeste	5
PAINS	MG	Interior 2	Sudeste	5
PAIVA	MG	Interior 2	Sudeste	5
PALMA	MG	Interior 2	Sudeste	5
PALMOPOLIS	MG	Interior 2	Sudeste	5
PAPAGAIOS	MG	Interior 1	Sudeste	5
PARA DE MINAS	MG	Interior 1	Sudeste	5
PARACATU	MG	Interior 2	Sudeste	5
PARAGUACU	MG	Interior 2	Sudeste	5
PARAISOPOLIS	MG	Interior 2	Sudeste	5
PARAOPEBA	MG	Interior 1	Sudeste	5
PASSA QUATRO	MG	Interior 2	Sudeste	5
PASSA TEMPO	MG	Interior 2	Sudeste	5
PASSABEM	MG	Interior 2	Sudeste	5
PASSA-VINTE	MG	Interior 2	Sudeste	5
PASSOS	MG	Interior 2	Sudeste	5
PATIS	MG	Interior 2	Sudeste	5
PATOS DE MINAS	MG	Interior 1	Sudeste	5
PATROCINIO	MG	Interior 1	Sudeste	5
PATROCINIO DO MURIAE	MG	Interior 2	Sudeste	5
PAULA CANDIDO	MG	Interior 2	Sudeste	5
PAULISTAS	MG	Interior 2	Sudeste	5
PAVAO	MG	Interior 2	Sudeste	5
PECANHA	MG	Interior 2	Sudeste	5
PEDRA AZUL	MG	Interior 2	Sudeste	5
PEDRA BONITA	MG	Interior 2	Sudeste	5
PEDRA DO ANTA	MG	Interior 2	Sudeste	5
PEDRA DO INDAIA	MG	Interior 1	Sudeste	5
PEDRA DOURADA	MG	Interior 2	Sudeste	5
PEDRALVA	MG	Interior 2	Sudeste	5
PEDRAS DE MARIA DA CRUZ	MG	Interior 2	Sudeste	5
PEDRINOPOLIS	MG	Interior 2	Sudeste	5
PEDRO LEOPOLDO	MG	Interior 1	Sudeste	5
PEDRO TEIXEIRA	MG	Interior 2	Sudeste	5
PEQUERI	MG	Interior 2	Sudeste	5
PEQUI	MG	Interior 2	Sudeste	5
PERDIGAO	MG	Interior 1	Sudeste	5
PERDIZES	MG	Interior 2	Sudeste	5
PERDOES	MG	Interior 2	Sudeste	5
PERIQUITO	MG	Interior 2	Sudeste	5
PESCADOR	MG	Interior 2	Sudeste	5
PIAU	MG	Interior 2	Sudeste	5
PIEDADE DE CARATINGA	MG	Interior 2	Sudeste	5
PIEDADE DE PONTE NOVA	MG	Interior 2	Sudeste	5
PIEDADE DO RIO GRANDE	MG	Interior 2	Sudeste	5
PIEDADE DOS GERAIS	MG	Interior 2	Sudeste	5
PIMENTA	MG	Interior 2	Sudeste	5
PINGO D'AGUA	MG	Interior 1	Sudeste	5
PINTOPOLIS	MG	Interior 2	Sudeste	5
PIRACEMA	MG	Interior 2	Sudeste	5
PIRAJUBA	MG	Interior 2	Sudeste	5
PIRANGA	MG	Interior 2	Sudeste	5
PIRANGUCU	MG	Interior 2	Sudeste	5
PIRANGUINHO	MG	Interior 2	Sudeste	5
PIRAPETINGA	MG	Interior 2	Sudeste	5
PIRAPORA	MG	Interior 2	Sudeste	5
PIRAUBA	MG	Interior 1	Sudeste	5
PITANGUI	MG	Interior 1	Sudeste	5
PIUMHI	MG	Interior 1	Sudeste	5
PLANURA	MG	Interior 2	Sudeste	5
POCO FUNDO	MG	Interior 2	Sudeste	5
POCOS DE CALDAS	MG	Interior 2	Sudeste	5
POCRANE	MG	Interior 2	Sudeste	5
POMPEU	MG	Interior 2	Sudeste	5
PONTE NOVA	MG	Interior 1	Sudeste	5
PONTO CHIQUE	MG	Interior 2	Sudeste	5
PONTO DOS VOLANTES	MG	Interior 2	Sudeste	5
PORTEIRINHA	MG	Interior 2	Sudeste	5
PORTO FIRME	MG	Interior 2	Sudeste	5
POTE	MG	Interior 2	Sudeste	5
POUSO ALEGRE	MG	Interior 2	Sudeste	5
POUSO ALTO	MG	Interior 2	Sudeste	5
PRADOS	MG	Interior 1	Sudeste	5
PRATA	MG	Interior 2	Sudeste	5
PRATAPOLIS	MG	Interior 2	Sudeste	5
PRATINHA	MG	Interior 2	Sudeste	5
PRESIDENTE BERNARDES	MG	Interior 2	Sudeste	5
PRESIDENTE JUSCELINO	MG	Interior 2	Sudeste	5
PRESIDENTE KUBITSCHEK	MG	Interior 2	Sudeste	5
PRESIDENTE OLEGARIO	MG	Interior 2	Sudeste	5
PRUDENTE DE MORAIS	MG	Interior 1	Sudeste	5
QUARTEL GERAL	MG	Interior 2	Sudeste	5
QUELUZITO	MG	Interior 2	Sudeste	5
RAPOSOS	MG	Interior 1	Sudeste	5
RAUL SOARES	MG	Interior 2	Sudeste	5
RECREIO	MG	Interior 2	Sudeste	5
REDUTO	MG	Interior 2	Sudeste	5
RESENDE COSTA	MG	Interior 2	Sudeste	5
RESPLENDOR	MG	Interior 2	Sudeste	5
RESSAQUINHA	MG	Interior 2	Sudeste	5
RIACHINHO	MG	Interior 2	Sudeste	5
RIACHO DOS MACHADOS	MG	Interior 2	Sudeste	5
RIBEIRAO DAS NEVES	MG	Interior 1	Sudeste	5
RIBEIRAO VERMELHO	MG	Interior 2	Sudeste	5
RIO ACIMA	MG	Interior 1	Sudeste	5
RIO CASCA	MG	Interior 1	Sudeste	5
RIO DO PRADO	MG	Interior 2	Sudeste	5
RIO DOCE	MG	Interior 2	Sudeste	5
RIO ESPERA	MG	Interior 2	Sudeste	5
RIO MANSO	MG	Interior 1	Sudeste	5
RIO NOVO	MG	Interior 2	Sudeste	5
RIO PARNAIBA	MG	Interior 1	Sudeste	5
RIO PARDO DE MINAS	MG	Interior 2	Sudeste	5
RIO PIRACICABA	MG	Interior 1	Sudeste	5
RIO POMBA	MG	Interior 1	Sudeste	5
RIO PRETO	MG	Interior 2	Sudeste	5
RIO VERMELHO	MG	Interior 2	Sudeste	5
RITAPOLIS	MG	Interior 2	Sudeste	5
ROCHEDO DE MINAS	MG	Interior 2	Sudeste	5
RODEIRO	MG	Interior 2	Sudeste	5
ROMARIA	MG	Interior 2	Sudeste	5
ROSARIO DA LIMEIRA	MG	Interior 2	Sudeste	5
RUBELITA	MG	Interior 2	Sudeste	5
RUBIM	MG	Interior 2	Sudeste	5
SABARA	MG	Interior 1	Sudeste	5
SABINOPOLIS	MG	Interior 2	Sudeste	5
SACRAMENTO	MG	Interior 2	Sudeste	5
SALINAS	MG	Interior 2	Sudeste	5
SALTO DA DIVISA	MG	Interior 2	Sudeste	5
SANTA BARBARA	MG	Interior 1	Sudeste	5
SANTA BARBARA DO LESTE	MG	Interior 2	Sudeste	5
SANTA BARBARA DO MONTE VERDE	MG	Interior 2	Sudeste	5
SANTA BARBARA DO TUGURIO	MG	Interior 2	Sudeste	5
SANTA CRUZ DE MINAS	MG	Interior 2	Sudeste	5
SANTA CRUZ DE SALINAS	MG	Interior 2	Sudeste	5
SANTA CRUZ DO ESCALVADO	MG	Interior 2	Sudeste	5
SANTA EFIGENIA DE MINAS	MG	Interior 2	Sudeste	5
SANTA FE DE MINAS	MG	Interior 2	Sudeste	5
SANTA HELENA DE MINAS	MG	Interior 2	Sudeste	5
SANTA JULIANA	MG	Interior 2	Sudeste	5
SANTA LUZIA	MG	Interior 1	Sudeste	5
SANTA MARGARIDA	MG	Interior 2	Sudeste	5
SANTA MARIA DE ITABIRA	MG	Interior 1	Sudeste	5
SANTA MARIA DO SALTO	MG	Interior 2	Sudeste	5
SANTA MARIA DO SUACUI	MG	Interior 2	Sudeste	5
SANTA RITA DE CALDAS	MG	Interior 2	Sudeste	5
SANTA RITA DE IBITIPOCA	MG	Interior 2	Sudeste	5
SANTA RITA DE JACUTINGA	MG	Interior 2	Sudeste	5
SANTA RITA DE MINAS	MG	Interior 2	Sudeste	5
SANTA RITA DO ITUETO	MG	Interior 2	Sudeste	5
SANTA RITA DO SAPUCAI	MG	Interior 2	Sudeste	5
SANTA ROSA DA SERRA	MG	Interior 2	Sudeste	5
SANTA VITORIA	MG	Interior 2	Sudeste	5
SANTANA DA VARGEM	MG	Interior 2	Sudeste	5
SANTANA DE CATAGUASES	MG	Interior 2	Sudeste	5
SANTANA DE PIRAPAMA	MG	Interior 2	Sudeste	5
SANTANA DO DESERTO	MG	Interior 2	Sudeste	5
SANTANA DO GARAMBEU	MG	Interior 2	Sudeste	5
SANTANA DO JACARE	MG	Interior 2	Sudeste	5
SANTANA DO MANHUACU	MG	Interior 2	Sudeste	5
SANTANA DO PARAISO	MG	Interior 1	Sudeste	5
SANTANA DO RIACHO	MG	Interior 2	Sudeste	5
SANTANA DOS MONTES	MG	Interior 2	Sudeste	5
SANTO ANTONIO DO AMPARO	MG	Interior 2	Sudeste	5
SANTO ANTONIO DO AVENTUREIRO	MG	Interior 2	Sudeste	5
SANTO ANTONIO DO GRAMA	MG	Interior 2	Sudeste	5
SANTO ANTONIO DO ITAMBE	MG	Interior 2	Sudeste	5
SANTO ANTONIO DO JACINTO	MG	Interior 2	Sudeste	5
SANTO ANTONIO DO MONTE	MG	Interior 1	Sudeste	5
SANTO ANTONIO DO RETIRO	MG	Interior 2	Sudeste	5
SANTO ANTONIO DO RIO ABAIXO	MG	Interior 2	Sudeste	5
SANTO HIPOLITO	MG	Interior 2	Sudeste	5
SANTOS DUMONT	MG	Interior 2	Sudeste	5
SAO BENTO ABADE	MG	Interior 2	Sudeste	5
SAO BRAS DO SUACUI	MG	Interior 1	Sudeste	5
SAO DOMINGOS DAS DORES	MG	Interior 2	Sudeste	5
SAO DOMINGOS DO PRATA	MG	Interior 2	Sudeste	5
SAO FELIX DE MINAS	MG	Interior 2	Sudeste	5
SAO FRANCISCO	MG	Interior 2	Sudeste	5
SAO FRANCISCO DE PAULA	MG	Interior 2	Sudeste	5
SAO FRANCISCO DE SALES	MG	Interior 2	Sudeste	5
SAO FRANCISCO DO GLORIA	MG	Interior 2	Sudeste	5
SÃO GERALDO	MG	Interior 1	Sudeste	5
SAO GERALDO DA PIEDADE	MG	Interior 2	Sudeste	5
SAO GERALDO DO BAIXIO	MG	Interior 2	Sudeste	5
SAO GONCALO DO ABAETE	MG	Interior 2	Sudeste	5
SAO GONCALO DO PARA	MG	Interior 2	Sudeste	5
SAO GONCALO DO RIO ABAIXO	MG	Interior 1	Sudeste	5
SAO GONCALO DO RIO PRETO	MG	Interior 2	Sudeste	5
SAO GONCALO DO SAPUCAI	MG	Interior 2	Sudeste	5
SÃO GOTARDO	MG	Interior 1	Sudeste	5
SAO JOAO BATISTA DO GLORIA	MG	Interior 2	Sudeste	5
SAO JOAO DA LAGOA	MG	Interior 2	Sudeste	5
SAO JOAO DA MATA	MG	Interior 2	Sudeste	5
SAO JOAO DA PONTE	MG	Interior 2	Sudeste	5
SAO JOAO DAS MISSOES	MG	Interior 2	Sudeste	5
SAO JOAO DEL REI	MG	Interior 1	Sudeste	5
SAO JOAO DO MANHUACU	MG	Interior 2	Sudeste	5
SAO JOAO DO MANTENINHA	MG	Interior 2	Sudeste	5
SAO JOAO DO ORIENTE	MG	Interior 2	Sudeste	5
SAO JOAO DO PACUI	MG	Interior 2	Sudeste	5
SAO JOAO DO PARAISO	MG	Interior 2	Sudeste	5
SAO JOAO EVANGELISTA	MG	Interior 2	Sudeste	5
SAO JOAO NEPOMUCENO	MG	Interior 2	Sudeste	5
SAO JOAQUIM DE BICAS	MG	Interior 1	Sudeste	5
SAO JOSE DA BARRA	MG	Interior 2	Sudeste	5
SAO JOSE DA LAPA	MG	Interior 1	Sudeste	5
SAO JOSE DA SAFIRA	MG	Interior 2	Sudeste	5
SAO JOSE DA VARGINHA	MG	Interior 2	Sudeste	5
SAO JOSE DO ALEGRE	MG	Interior 2	Sudeste	5
SAO JOSE DO DIVINO	MG	Interior 2	Sudeste	5
SAO JOSE DO GOIABAL	MG	Interior 2	Sudeste	5
SAO JOSE DO JACURI	MG	Interior 2	Sudeste	5
SAO JOSE DO MANTIMENTO	MG	Interior 2	Sudeste	5
SAO LOURENCO	MG	Interior 2	Sudeste	5
SAO MIGUEL DO ANTA	MG	Interior 2	Sudeste	5
SAO PEDRO DA UNIAO	MG	Interior 2	Sudeste	5
SAO PEDRO DO SUACUI	MG	Interior 2	Sudeste	5
SAO PEDRO DOS FERROS	MG	Interior 2	Sudeste	5
SAO ROMAO	MG	Interior 2	Sudeste	5
SAO ROQUE DE MINAS	MG	Interior 2	Sudeste	5
SAO SEBASTIAO DA BELA VISTA	MG	Interior 2	Sudeste	5
SAO SEBASTIAO DA VARGEM ALEGRE	MG	Interior 2	Sudeste	5
SAO SEBASTIAO DO ANTA	MG	Interior 2	Sudeste	5
SAO SEBASTIAO DO MARANHAO	MG	Interior 2	Sudeste	5
SAO SEBASTIAO DO OESTE	MG	Interior 1	Sudeste	5
SAO SEBASTIAO DO PARAISO	MG	Interior 2	Sudeste	5
SAO SEBASTIAO DO RIO PRETO	MG	Interior 2	Sudeste	5
SAO SEBASTIAO DO RIO VERDE	MG	Interior 2	Sudeste	5
SAO THOME DAS LETRAS	MG	Interior 2	Sudeste	5
SAO TIAGO	MG	Interior 2	Sudeste	5
SAO TOMAS DE AQUINO	MG	Interior 2	Sudeste	5
SAO VICENTE DE MINAS	MG	Interior 2	Sudeste	5
SAPUCAI-MIRIM	MG	Interior 2	Sudeste	5
SARDOA	MG	Interior 2	Sudeste	5
SARZEDO	MG	Interior 1	Sudeste	5
SEM-PEIXE	MG	Interior 2	Sudeste	5
SENADOR AMARAL	MG	Interior 2	Sudeste	5
SENADOR CORTES	MG	Interior 2	Sudeste	5
SENADOR FIRMINO	MG	Interior 2	Sudeste	5
SENADOR JOSE BENTO	MG	Interior 2	Sudeste	5
SENADOR MODESTINO GONCALVES	MG	Interior 2	Sudeste	5
SENHORA DE OLIVEIRA	MG	Interior 2	Sudeste	5
SENHORA DO PORTO	MG	Interior 2	Sudeste	5
SENHORA DOS REMEDIOS	MG	Interior 2	Sudeste	5
SERICITA	MG	Interior 2	Sudeste	5
SERITINGA	MG	Interior 2	Sudeste	5
SERRA AZUL DE MINAS	MG	Interior 2	Sudeste	5
SERRA DA SAUDADE	MG	Interior 2	Sudeste	5
SERRA DO SALITRE	MG	Interior 1	Sudeste	5
SERRA DOS AIMORES	MG	Interior 2	Sudeste	5
SERRANIA	MG	Interior 2	Sudeste	5
SERRANOPOLIS DE MINAS	MG	Interior 2	Sudeste	5
SERRANOS	MG	Interior 2	Sudeste	5
SERRO	MG	Interior 2	Sudeste	5
SETE LAGOAS	MG	Interior 1	Sudeste	5
SETUBINHA	MG	Interior 2	Sudeste	5
SILVEIRANIA	MG	Interior 2	Sudeste	5
SILVIANOPOLIS	MG	Interior 2	Sudeste	5
SIMAO PEREIRA	MG	Interior 2	Sudeste	5
SIMONESIA	MG	Interior 2	Sudeste	5
SOBRALIA	MG	Interior 2	Sudeste	5
SOLEDADE DE MINAS	MG	Interior 2	Sudeste	5
TABULEIRO	MG	Interior 2	Sudeste	5
TAIOBEIRAS	MG	Interior 2	Sudeste	5
TAPARUBA	MG	Interior 2	Sudeste	5
TAPIRA	MG	Interior 2	Sudeste	5
TAPIRAI	MG	Interior 2	Sudeste	5
TAQUARACU DE MINAS	MG	Interior 2	Sudeste	5
TARUMIRIM	MG	Interior 2	Sudeste	5
TEIXEIRAS	MG	Interior 2	Sudeste	5
TEOFILO OTONI	MG	Interior 2	Sudeste	5
TIMOTEO	MG	Interior 1	Sudeste	5
TIRADENTES	MG	Interior 1	Sudeste	5
TIROS	MG	Interior 1	Sudeste	5
TOCANTINS	MG	Interior 1	Sudeste	5
TOCOS DO MOJI	MG	Interior 2	Sudeste	5
TOLEDO	MG	Interior 2	Sudeste	5
TOMBOS	MG	Interior 2	Sudeste	5
TRES CORACOES	MG	Interior 2	Sudeste	5
TRES MARIAS	MG	Interior 2	Sudeste	5
TRES PONTAS	MG	Interior 2	Sudeste	5
TUMIRITINGA	MG	Interior 2	Sudeste	5
TUPACIGUARA	MG	Interior 2	Sudeste	5
TURMALINA	MG	Interior 2	Sudeste	5
TURVOLANDIA	MG	Interior 2	Sudeste	5
UBA	MG	Interior 1	Sudeste	5
UBAI	MG	Interior 2	Sudeste	5
UBAPORANGA	MG	Interior 2	Sudeste	5
UBERABA	MG	Interior 2	Sudeste	5
UBERLANDIA	MG	Uberlandia	Sudeste	Sob Consulta
UMBURATIBA	MG	Interior 2	Sudeste	5
UNAI	MG	Interior 2	Sudeste	5
UNIAO DE MINAS	MG	Interior 2	Sudeste	5
URUANA DE MINAS	MG	Interior 2	Sudeste	5
URUCANIA	MG	Interior 2	Sudeste	5
URUCUIA	MG	Interior 2	Sudeste	5
VARGEM ALEGRE	MG	Interior 2	Sudeste	5
VARGEM BONITA	MG	Interior 2	Sudeste	5
VARGEM GRANDE DO RIO PARDO	MG	Interior 2	Sudeste	5
VARGINHA	MG	Interior 2	Sudeste	5
VARJAO DE MINAS	MG	Interior 2	Sudeste	5
VARZEA DA PALMA	MG	Interior 2	Sudeste	5
VARZELANDIA	MG	Interior 2	Sudeste	5
VAZANTE	MG	Interior 2	Sudeste	5
VERDELANDIA	MG	Interior 2	Sudeste	5
VEREDINHA	MG	Interior 2	Sudeste	5
VERISSIMO	MG	Interior 2	Sudeste	5
VERMELHO NOVO	MG	Interior 2	Sudeste	5
VESPASIANO	MG	Interior 1	Sudeste	5
VICOSA	MG	Interior 2	Sudeste	5
VIEIRAS	MG	Interior 2	Sudeste	5
VIRGEM DA LAPA	MG	Interior 2	Sudeste	5
VIRGINIA	MG	Interior 2	Sudeste	5
VIRGINOPOLIS	MG	Interior 2	Sudeste	5
VIRGOLANDIA	MG	Interior 2	Sudeste	5
VISCONDE DO RIO BRANCO	MG	Interior 1	Sudeste	5
VOLTA GRANDE	MG	Interior 2	Sudeste	5
WENCESLAU BRAZ	MG	Interior 2	Sudeste	5
AGUA CLARA	MS	Interior 1	Centro-Oeste	10
ALCINOPOLIS	MS	Interior 1	Centro-Oeste	10
AMAMBAI	MS	Interior 1	Centro-Oeste	10
ANASTACIO	MS	Interior 1	Centro-Oeste	10
ANAURILANDIA	MS	Interior 1	Centro-Oeste	10
ANGELICA	MS	Interior 1	Centro-Oeste	10
ANTONIO JOAO	MS	Interior 1	Centro-Oeste	10
APARECIDA DO TABOADO	MS	Interior 1	Centro-Oeste	10
AQUIDAUANA	MS	Interior 1	Centro-Oeste	10
ARAL MOREIRA	MS	Interior 1	Centro-Oeste	10
BANDEIRANTES	MS	Interior 1	Centro-Oeste	10
BATAGUASSU	MS	Interior 1	Centro-Oeste	10
BATAYPORA	MS	Interior 1	Centro-Oeste	10
BELA VISTA	MS	Interior 1	Centro-Oeste	10
BODOQUENA	MS	Interior 1	Centro-Oeste	10
BONITO	MS	Interior 1	Centro-Oeste	10
BRASILANDIA	MS	Interior 1	Centro-Oeste	10
CAARAPO	MS	Interior 1	Centro-Oeste	10
CAMAPUA	MS	Interior 1	Centro-Oeste	10
CAMPO GRANDE	MS	Capital	Centro-Oeste	6
CARACOL	MS	Interior 1	Centro-Oeste	10
CASSILANDIA	MS	Interior 1	Centro-Oeste	10
CHAPADAO DO SUL	MS	Interior 1	Centro-Oeste	10
CORGUINHO	MS	Interior 1	Centro-Oeste	10
CORONEL SAPUCAIA	MS	Interior 1	Centro-Oeste	10
CORUMBA	MS	Interior 1	Centro-Oeste	10
COSTA RICA	MS	Interior 1	Centro-Oeste	10
COXIM	MS	Interior 1	Centro-Oeste	10
DEODAPOLIS	MS	Interior 1	Centro-Oeste	10
DOIS IRMAOS DO BURITI	MS	Interior 1	Centro-Oeste	10
DOURADINA	MS	Interior 1	Centro-Oeste	10
DOURADOS	MS	Interior 1	Centro-Oeste	10
ELDORADO	MS	Interior 1	Centro-Oeste	10
FATIMA DO SUL	MS	Interior 1	Centro-Oeste	10
FIGUEIRAO	MS	Interior 1	Centro-Oeste	10
GLORIA DE DOURADOS	MS	Interior 1	Centro-Oeste	10
GUIA LOPES DA LAGUNA	MS	Interior 1	Centro-Oeste	10
IGUATEMI	MS	Interior 1	Centro-Oeste	10
INOCENCIA	MS	Interior 1	Centro-Oeste	10
ITAPORA	MS	Interior 1	Centro-Oeste	10
ITAQUIRAI	MS	Interior 1	Centro-Oeste	10
IVINHEMA	MS	Interior 1	Centro-Oeste	10
JAPORA	MS	Interior 1	Centro-Oeste	10
JARAGUARI	MS	Interior 1	Centro-Oeste	10
JARDIM	MS	Interior 1	Centro-Oeste	10
JATEI	MS	Interior 1	Centro-Oeste	10
JUTI	MS	Interior 1	Centro-Oeste	10
LADARIO	MS	Interior 1	Centro-Oeste	10
LAGUNA CARAPA	MS	Interior 1	Centro-Oeste	10
MARACAJU	MS	Interior 1	Centro-Oeste	10
MIRANDA	MS	Interior 1	Centro-Oeste	10
MUNDO NOVO	MS	Interior 1	Centro-Oeste	10
NAVIRAI	MS	Interior 1	Centro-Oeste	10
NIOAQUE	MS	Interior 1	Centro-Oeste	10
NOVA ALVORADA DO SUL	MS	Interior 1	Centro-Oeste	10
NOVA ANDRADINA	MS	Interior 1	Centro-Oeste	10
NOVO HORIZONTE DO SUL	MS	Interior 1	Centro-Oeste	10
PARAISO DAS AGUAS 	MS	Interior 1	Centro-Oeste	10
PARANAIBA	MS	Interior 1	Centro-Oeste	10
PARANHOS	MS	Interior 1	Centro-Oeste	10
PEDRO GOMES	MS	Interior 1	Centro-Oeste	10
PONTA PORA	MS	Interior 1	Centro-Oeste	10
PORTO MURTINHO	MS	Interior 1	Centro-Oeste	10
RIBAS DO RIO PARDO	MS	Interior 1	Centro-Oeste	10
RIO BRILHANTE	MS	Interior 1	Centro-Oeste	10
RIO NEGRO	MS	Interior 1	Centro-Oeste	10
RIO VERDE DE MATO GROSSO	MS	Interior 1	Centro-Oeste	10
ROCHEDO	MS	Interior 1	Centro-Oeste	10
SANTA RITA DO PARDO	MS	Interior 1	Centro-Oeste	10
SAO GABRIEL DO OESTE	MS	Interior 1	Centro-Oeste	10
SELVIRIA	MS	Interior 1	Centro-Oeste	10
SETE QUEDAS	MS	Interior 1	Centro-Oeste	10
SIDROLANDIA	MS	Interior 1	Centro-Oeste	10
SONORA	MS	Interior 1	Centro-Oeste	10
TACURU	MS	Interior 1	Centro-Oeste	10
TAQUARUSSU	MS	Interior 1	Centro-Oeste	10
TERENOS	MS	Interior 1	Centro-Oeste	10
TRES LAGOAS	MS	Interior 1	Centro-Oeste	10
VICENTINA	MS	Interior 1	Centro-Oeste	10
ACORIZAL	MT	Interior 1	Centro-Oeste	10
ÁGUA BOA	MT	Interior 1	Centro-Oeste	10
ALTA FLORESTA	MT	Interior 1	Centro-Oeste	10
ALTO ARAGUAIA	MT	Interior 1	Centro-Oeste	10
ALTO BOA VISTA	MT	Interior 2	Centro-Oeste	10
ALTO GARÇAS	MT	Interior 1	Centro-Oeste	10
ALTO PARAGUAI	MT	Interior 2	Centro-Oeste	10
ALTO TAQUARI	MT	Interior 1	Centro-Oeste	10
APIACÁS	MT	Interior 2	Centro-Oeste	10
ARAGUAIANA	MT	Interior 2	Centro-Oeste	10
ARAGUAINHA	MT	Interior 2	Centro-Oeste	10
ARAPUTANGA	MT	Interior 1	Centro-Oeste	10
ARENÁPOLIS	MT	Interior 1	Centro-Oeste	10
ARIPUANÃ	MT	Interior 2	Centro-Oeste	10
BARÃO DE MELGAÇO	MT	Interior 1	Centro-Oeste	10
BARRA DO BUGRES	MT	Interior 1	Centro-Oeste	10
BARRA DO GARÇAS	MT	Interior 1	Centro-Oeste	10
BOM JESUS DO ARAGUAIA	MT	Interior 2	Centro-Oeste	10
BRASNORTE	MT	Interior 1	Centro-Oeste	10
CÁCERES	MT	Interior 1	Centro-Oeste	10
CAMPINÁPOLIS	MT	Interior 2	Centro-Oeste	10
CAMPO NOVO DO PARECIS	MT	Interior 1	Centro-Oeste	10
CAMPO VERDE	MT	Interior 1	Centro-Oeste	10
CAMPOS DE JÚLIO	MT	Interior 1	Centro-Oeste	10
CANABRAVA DO NORTE	MT	Interior 1	Centro-Oeste	10
CANARANA	MT	Interior 2	Centro-Oeste	10
CARLINDA	MT	Interior 1	Centro-Oeste	10
CASTANHEIRA	MT	Interior 2	Centro-Oeste	10
CHAPADA DOS GUIMARÂES	MT	Interior 1	Centro-Oeste	10
CLÁUDIA	MT	Interior 1	Centro-Oeste	10
COCALINHO	MT	Interior 2	Centro-Oeste	10
COLÍDER	MT	Interior 1	Centro-Oeste	10
COLNIZA	MT	Interior 2	Centro-Oeste	10
COMODORO	MT	Interior 2	Centro-Oeste	10
CONFRESA	MT	Interior 2	Centro-Oeste	10
CONQUISTA D´OESTE	MT	Interior 2	Centro-Oeste	10
COTRIGUAÇU	MT	Interior 2	Centro-Oeste	10
CUIABA	MT	Capital	Centro-Oeste	7
CURVELÂNDIA	MT	Interior 1	Centro-Oeste	10
DENISE	MT	Interior 1	Centro-Oeste	10
DIAMANTINO	MT	Interior 1	Centro-Oeste	10
DOM AQUINO	MT	Interior 1	Centro-Oeste	10
FELIZ NATAL	MT	Interior 1	Centro-Oeste	10
FIGUEIRÓPOLIS D' OESTE	MT	Interior 1	Centro-Oeste	10
GAÚCHA DO NORTE	MT	Interior 2	Centro-Oeste	10
GENERAL CARNEIRO	MT	Interior 1	Centro-Oeste	10
GLÓRIA D´OESTE	MT	Interior 1	Centro-Oeste	10
GUARANTÃ DO NORTE	MT	Interior 1	Centro-Oeste	10
GUIRATINGA	MT	Interior 1	Centro-Oeste	10
INDIAVAÍ	MT	Interior 1	Centro-Oeste	10
IPIRANGA DO NORTE	MT	Interior 1	Centro-Oeste	10
ITANHANGÁ	MT	Interior 1	Centro-Oeste	10
ITAÚBA	MT	Interior 1	Centro-Oeste	10
ITIQUIRA	MT	Interior 1	Centro-Oeste	10
JACIARA	MT	Interior 1	Centro-Oeste	10
JANGADA	MT	Interior 1	Centro-Oeste	10
JAURU	MT	Interior 1	Centro-Oeste	10
JUARA	MT	Interior 1	Centro-Oeste	10
JUÍNA	MT	Interior 1	Centro-Oeste	10
JURUENA	MT	Interior 1	Centro-Oeste	10
JUSCIMEIRA	MT	Interior 1	Centro-Oeste	10
LAMBARI D´OESTE	MT	Interior 1	Centro-Oeste	10
LUCAS DO RIO VERDE	MT	Interior 1	Centro-Oeste	10
LUCIARA	MT	Interior 2	Centro-Oeste	10
MARCELÂNDIA	MT	Interior 1	Centro-Oeste	10
MATUPÁ	MT	Interior 1	Centro-Oeste	10
MIRASSOL D´OESTE	MT	Interior 1	Centro-Oeste	10
NOBRES	MT	Interior 1	Centro-Oeste	10
NORTELÂNDIA	MT	Interior 1	Centro-Oeste	10
NOSSA SENHORA DO LIVRAMENTO	MT	Interior 1	Centro-Oeste	10
NOVA BANDEIRANTES	MT	Interior 1	Centro-Oeste	10
NOVA BRASILÂNDIA	MT	Interior 1	Centro-Oeste	10
NOVA CANAÃ DO NORTE	MT	Interior 1	Centro-Oeste	10
NOVA GUARITA	MT	Interior 2	Centro-Oeste	10
NOVA LACERDA	MT	Interior 1	Centro-Oeste	10
NOVA MARILÂNDIA	MT	Interior 1	Centro-Oeste	10
NOVA MARINGÁ	MT	Interior 2	Centro-Oeste	10
NOVA MONTE VERDE	MT	Interior 2	Centro-Oeste	10
NOVA MUTUM	MT	Interior 1	Centro-Oeste	10
NOVA NAZARÉ	MT	Sob Consulta	Centro-Oeste	Sob Consulta
NOVA OLÍMPIA	MT	Interior 1	Centro-Oeste	10
NOVA SANTA HELENA	MT	Interior 1	Centro-Oeste	10
NOVA UBIRATÃ	MT	Interior 1	Centro-Oeste	10
NOVA XAVANTINA	MT	Interior 1	Centro-Oeste	10
NOVO HORIZONTE DO NORTE	MT	Interior 1	Centro-Oeste	10
NOVO MUNDO	MT	Interior 1	Centro-Oeste	10
NOVO SANTO ANTONIO	MT	Interior 2	Centro-Oeste	10
NOVO SÃO JOAQUIM	MT	Interior 2	Centro-Oeste	10
PARANAÍTA	MT	Interior 2	Centro-Oeste	10
PARANATINGA	MT	Interior 1	Centro-Oeste	10
PEDRA PRETA	MT	Interior 1	Centro-Oeste	10
PEIXOTO DE AZEVEDO	MT	Interior 1	Centro-Oeste	10
PLANALTO DA SERRA	MT	Interior 2	Centro-Oeste	10
POCONÉ	MT	Interior 1	Centro-Oeste	10
PONTAL DO ARAGUAIA	MT	Interior 1	Centro-Oeste	10
PONTE BRANCA	MT	Interior 2	Centro-Oeste	10
PONTES E LACERDA	MT	Interior 1	Centro-Oeste	10
PORTO ALEGRE DO NORTE	MT	Interior 2	Centro-Oeste	10
PORTO DOS GAÚCHOS	MT	Interior 1	Centro-Oeste	10
PORTO ESPERIDIÃO	MT	Interior 1	Centro-Oeste	10
PORTO ESTRELA	MT	Interior 1	Centro-Oeste	10
POXORÉU	MT	Interior 1	Centro-Oeste	10
PRIMAVERA DO LESTE	MT	Interior 1	Centro-Oeste	10
QUERÊNCIA	MT	Interior 2	Centro-Oeste	10
RESERVA DO CABAÇAL	MT	Interior 1	Centro-Oeste	10
RIBEIRÃO CASCALHEIRA	MT	Interior 2	Centro-Oeste	10
RIBEIRÃOZINHO	MT	Interior 2	Centro-Oeste	10
RIO BRANCO	MT	Interior 1	Centro-Oeste	10
RONDOLÂNDIA	MT	Sob Consulta	Centro-Oeste	Sob Consulta
RONDONÓPOLIS	MT	Interior 1	Centro-Oeste	10
ROSÁRIO OESTE	MT	Interior 1	Centro-Oeste	10
SALTO DO CÉU	MT	Interior 1	Centro-Oeste	10
SANTA CARMEM	MT	Interior 1	Centro-Oeste	10
SANTA CRUZ DO XINGU	MT	Sob Consulta	Centro-Oeste	Sob Consulta
SANTA RITA DO TRIVELATO	MT	Interior 1	Centro-Oeste	10
SANTA TEREZINHA	MT	Interior 2	Centro-Oeste	10
SANTO AFONSO	MT	Interior 1	Centro-Oeste	10
SANTO ANTONIO DO LESTE	MT	Interior 1	Centro-Oeste	10
SANTO ANTÔNIO DE LEVERGER	MT	Interior 1	Centro-Oeste	10
SÃO FELIX DO ARAGUAIA	MT	Interior 2	Centro-Oeste	10
SÃO JOSÉ DO POVO	MT	Interior 1	Centro-Oeste	10
SÃO JOSÉ DO RIO CLARO	MT	Interior 1	Centro-Oeste	10
SÃO JOSÉ DO XINGU	MT	Sob Consulta	Centro-Oeste	Sob Consulta
SÃO JOSÉ DOS QUATRO MARCOS	MT	Interior 1	Centro-Oeste	10
SÃO PEDRO DA CIPA	MT	Interior 1	Centro-Oeste	10
SAPEZAL	MT	Interior 1	Centro-Oeste	10
SERRA NOVA DOURADA	MT	Interior 2	Centro-Oeste	10
SINOP	MT	Interior 1	Centro-Oeste	10
SORRISO	MT	Interior 1	Centro-Oeste	10
TABAPORÂ	MT	Interior 1	Centro-Oeste	10
TANGARÁ DA SERRA	MT	Interior 1	Centro-Oeste	10
TAPURAH	MT	Interior 1	Centro-Oeste	10
TERRA NOVA DO NORTE	MT	Interior 1	Centro-Oeste	10
TESOURO	MT	Interior 1	Centro-Oeste	10
TORIXORÉU	MT	Interior 2	Centro-Oeste	10
UNIÃO DO SUL	MT	Interior 1	Centro-Oeste	10
VALE DE SÃO DOMINGOS	MT	Interior 1	Centro-Oeste	10
VARZEA GRANDE	MT	Capital	Centro-Oeste	7
VERA	MT	Interior 1	Centro-Oeste	10
VILA BELA DA SANTÍSSIMA TRINDADE	MT	Interior 1	Centro-Oeste	10
VILA RICA	MT	Interior 2	Centro-Oeste	10
ABAETETUBA	PA	Interior 1	Norte	12
ABEL FIGUEIREDO	PA	Interior 1	Norte	12
ACARÁ	PA	Interior 2	Norte	15
AFUA	PA	Sob Consulta	Norte	Sob Consulta
AGUA AZUL DO NORTE	PA	Sob Consulta	Norte	Sob Consulta
ALENQUER	PA	Interior 1	Norte	12
ALMEIRIM	PA	Interior 1	Norte	12
ALTAMIRA	PA	Interior 2	Norte	15
ANAJÁS	PA	Sob Consulta	Norte	Sob Consulta
ANANINDEUA	PA	Capital	Norte	9
ANAPU	PA	Interior 2	Norte	15
AUGUSTO CORRÊA	PA	Interior 2	Norte	15
AURORA DO PARÁ	PA	Interior 2	Norte	15
AVEIRO	PA	Interior 1	Norte	12
BAGRE	PA	Sob Consulta	Norte	Sob Consulta
BAIÃO	PA	Sob Consulta	Norte	Sob Consulta
BANNACH	PA	Interior 2	Norte	15
BARCARENA	PA	Interior 2	Norte	15
BELÉM	PA	Capital	Norte	9
BELTERRA	PA	Interior 1	Norte	12
BENEVIDES	PA	Interior 2	Norte	15
BOM JESUS DO TOCANTINS	PA	Interior 2	Norte	15
BONITO	PA	Interior 2	Norte	15
BRAGANÇA	PA	Interior 2	Norte	15
BRASIL NOVO	PA	Interior 2	Norte	15
BREJO GRANDE DO ARAGUAIA	PA	Interior 2	Norte	15
BREU BRANCO	PA	Interior 2	Norte	15
BREVES	PA	Sob Consulta	Norte	Sob Consulta
BUJARU	PA	Sob Consulta	Norte	Sob Consulta
CACHOEIRA DO ARARI	PA	Sob Consulta	Norte	Sob Consulta
CACHOEIRA DO PIRIÁ	PA	Interior 2	Norte	15
CAMETÁ	PA	Sob Consulta	Norte	Sob Consulta
CANAÃ DOS CARAJÁS	PA	Interior 2	Norte	15
CAPANEMA	PA	Interior 1	Norte	12
CAPITÃO POÇO	PA	Interior 2	Norte	15
CASTANHAL	PA	Interior 2	Norte	15
CHAVES	PA	Sob Consulta	Norte	Sob Consulta
COLARES	PA	Sob Consulta	Norte	Sob Consulta
CONCEIÇÃO DO ARAGUAIA	PA	Sob Consulta	Norte	Sob Consulta
CONCÓRDIA DO PARÁ	PA	Sob Consulta	Norte	Sob Consulta
CUMARU DO NORTE	PA	Interior 2	Norte	15
CURIONÓPOLIS	PA	Interior 1	Norte	12
CURRALINHO	PA	Sob Consulta	Norte	Sob Consulta
CURUA	PA	Interior 1	Norte	12
CURUÇÁ	PA	Interior 2	Norte	15
DOM ELISEU	PA	Interior 2	Norte	15
ELDORADO DOS CARAJÁS	PA	Interior 1	Norte	12
FARO	PA	Interior 1	Norte	12
FLORESTA DO ARAGUAIA	PA	Sob Consulta	Norte	Sob Consulta
GARRAFÃO DO NORTE	PA	Interior 2	Norte	15
GOIANÉSIA DO PARÁ	PA	Interior 2	Norte	15
GURUPÁ	PA	Sob Consulta	Norte	Sob Consulta
IGARAPÉ-AÇU	PA	Interior 2	Norte	15
IGARAPÉ-MIRI	PA	Interior 2	Norte	15
INHANGAPI	PA	Interior 2	Norte	15
IPIXUNA DO PARÁ	PA	Interior 2	Norte	15
IRITUIA	PA	Interior 2	Norte	15
ITAITUBA	PA	Interior 1	Norte	12
ITUPIRANGA	PA	Sob Consulta	Norte	Sob Consulta
JACAREACANGA	PA	Interior 2	Norte	15
JACUNDÁ	PA	Interior 1	Norte	12
JURUTI	PA	Interior 1	Norte	12
LIMOEIRO DO AJURU	PA	Sob Consulta	Norte	Sob Consulta
MÃE DO RIO	PA	Interior 1	Norte	12
MAGALHÃES BARATA	PA	Interior 2	Norte	15
MARABÁ	PA	Interior 2	Norte	15
MARACANÃ	PA	Interior 2	Norte	15
MARAPANIM	PA	Interior 2	Norte	15
MARITUBA	PA	Capital	Norte	9
MEDICILANDIA	PA	Interior 2	Norte	15
MELGAÇO	PA	Sob Consulta	Norte	Sob Consulta
MOCAJUBA	PA	Sob Consulta	Norte	Sob Consulta
MOJU	PA	Interior 2	Norte	15
MOJUI DOS CAMPOS	PA	Interior 1	Norte	12
MONTE ALEGRE	PA	Interior 1	Norte	12
MUANÁ	PA	Sob Consulta	Norte	Sob Consulta
NOVA ESPERANÇA DO PIRIA	PA	Interior 2	Norte	15
NOVA IPIXUNA	PA	Interior 1	Norte	12
NOVA TIMBOTEUA	PA	Interior 2	Norte	15
NOVO PROGRESSO	PA	Interior 2	Norte	15
NOVO REPARTIMENTO	PA	Sob Consulta	Norte	Sob Consulta
OBIDOS	PA	Interior 1	Norte	12
OEIRAS DO PARÁ	PA	Sob Consulta	Norte	Sob Consulta
ORIXIMINA	PA	Interior 1	Norte	12
OURÉM	PA	Interior 2	Norte	15
OURILÂNDIA DO NORTE	PA	Sob Consulta	Norte	Sob Consulta
PACAJÁ	PA	Interior 2	Norte	15
PALESTINA DO PARÁ	PA	Interior 2	Norte	15
PARAGOMINAS	PA	Interior 1	Norte	12
PARAUAPEBAS	PA	Interior 2	Norte	15
PAU DARCO	PA	Interior 2	Norte	15
PEIXE-BOI	PA	Interior 2	Norte	15
PIÇARRA	PA	Interior 2	Norte	15
PLACAS	PA	Interior 2	Norte	15
PONTA DE PEDRAS	PA	Sob Consulta	Norte	Sob Consulta
PORTEL	PA	Sob Consulta	Norte	Sob Consulta
PORTO DE MOZ	PA	Sob Consulta	Norte	Sob Consulta
PRAINHA	PA	Interior 1	Norte	12
PRIMAVERA	PA	Interior 2	Norte	15
QUATIPURU	PA	Interior 2	Norte	15
REDENÇÃO	PA	Interior 2	Norte	15
RIO MARIA	PA	Interior 2	Norte	15
RONDON DO PARÁ	PA	Interior 1	Norte	12
RUROPOLIS	PA	Interior 2	Norte	15
SALINÓPOLIS	PA	Interior 2	Norte	15
SALVATERRA	PA	Sob Consulta	Norte	Sob Consulta
SANTA BARBARA	PA	Interior 2	Norte	15
SANTA CRUZ DO ARARI	PA	Sob Consulta	Norte	Sob Consulta
SANTA ISABEL DO PARÁ	PA	Interior 2	Norte	15
SANTA LUZIA DO PARÁ	PA	Interior 2	Norte	15
SANTA MARIA DAS BARREIRAS	PA	Interior 2	Norte	15
SANTA MARIA DO PARÁ	PA	Interior 2	Norte	15
SANTANA DO ARAGUAIA	PA	Sob Consulta	Norte	Sob Consulta
SANTARÉM	PA	Interior 2	Norte	15
SANTARÉM NOVO	PA	Interior 2	Norte	15
SANTO ANTÔNIO DO TAUÁ	PA	Interior 2	Norte	15
SÃO CAETANO DE ODIVELAS	PA	Interior 2	Norte	15
SÃO DOMINGOS DO ARAGUAIA	PA	Interior 2	Norte	15
SÃO DOMINGOS DO CAPIM	PA	Interior 2	Norte	15
SÃO FELIX DO XINGU	PA	Sob Consulta	Norte	Sob Consulta
SÃO FRANCISCO DO PARÁ	PA	Interior 2	Norte	15
SÃO GERALDO DO ARAGUAIA	PA	Interior 2	Norte	15
SÃO JOÃO DA PONTA	PA	Interior 2	Norte	15
SÃO JOÃO DE PIRABAS	PA	Interior 2	Norte	15
SÃO JOÃO DO ARAGUAIA	PA	Interior 2	Norte	15
SÃO MIGUEL DO GUAMÁ	PA	Interior 2	Norte	15
SÃO SEBASTIÃO DA BOA VISTA	PA	Sob Consulta	Norte	Sob Consulta
SAPUCAIA	PA	Interior 2	Norte	15
SENADOR JOSÉ PORFÍRIO	PA	Interior 2	Norte	15
SOURE	PA	Sob Consulta	Norte	Sob Consulta
TAILANDIA	PA	Interior 2	Norte	15
TERRA ALTA	PA	Interior 2	Norte	15
TERRA SANTA	PA	Interior 1	Norte	12
TOMÉ-AÇU	PA	Sob Consulta	Norte	Sob Consulta
TRACUATEUA	PA	Interior 2	Norte	15
TRAIRAO	PA	Interior 2	Norte	15
TUCUMÃ	PA	Sob Consulta	Norte	Sob Consulta
TUCURUÍ	PA	Interior 2	Norte	15
ULIANÓPOLIS	PA	Interior 2	Norte	15
URUARA	PA	Interior 2	Norte	15
VIGIA	PA	Interior 2	Norte	15
VISEU	PA	Interior 2	Norte	15
VITÓRIA DO XINGU	PA	Interior 2	Norte	15
XINGUARA	PA	Interior 1	Norte	12
ÁGUA BRANCA	PB	Sob Consulta	Nordeste	Sob Consulta
AGUIAR	PB	Sob Consulta	Nordeste	Sob Consulta
ALAGOA GRANDE	PB	Interior 1	Nordeste	10
ALAGOA NOVA	PB	Interior 2	Nordeste	10
ALAGOINHA	PB	Interior 2	Nordeste	10
ALCANTIL	PB	Interior 2	Nordeste	10
ALGODÃO DE JANDAIRA	PB	Interior 2	Nordeste	10
ALHANDRA	PB	Interior 1	Nordeste	10
AMPARO	PB	Interior 2	Nordeste	10
APARECIDA	PB	Sob Consulta	Nordeste	Sob Consulta
ARACAGI	PB	Interior 1	Nordeste	10
ARARA	PB	Interior 2	Nordeste	10
ARARUNA	PB	Interior 2	Nordeste	10
AREIA	PB	Interior 1	Nordeste	10
AREIA DE BARAÚNAS	PB	Interior 2	Nordeste	10
AREIAL	PB	Interior 2	Nordeste	10
AROEIRAS	PB	Interior 2	Nordeste	10
ASSUNÇÃO	PB	Interior 2	Nordeste	10
BAIA DA TRAIÇÃO	PB	Interior 1	Nordeste	10
BANANEIRAS	PB	Interior 1	Nordeste	10
BARAUINAS	PB	Interior 2	Nordeste	10
BARRA DE SANTA ROSA	PB	Interior 2	Nordeste	10
BARRA DE SANTANA	PB	Interior 2	Nordeste	10
BARRA DE SAO MIGUEL	PB	Sob Consulta	Nordeste	Sob Consulta
BAYEUX	PB	Capital	Nordeste	7
BELÉM	PB	Interior 2	Nordeste	10
BELÉM DO BREJO CRUZ	PB	Sob Consulta	Nordeste	Sob Consulta
BERNADINO BATISTA	PB	Sob Consulta	Nordeste	Sob Consulta
BOA VENTURA	PB	Sob Consulta	Nordeste	Sob Consulta
BOA VISTA	PB	Interior 2	Nordeste	10
BOM JESUS	PB	Sob Consulta	Nordeste	Sob Consulta
BOM SUCESSO	PB	Sob Consulta	Nordeste	Sob Consulta
BONITO DE SANTA FE	PB	Sob Consulta	Nordeste	Sob Consulta
BOQUEIRAO	PB	Sob Consulta	Nordeste	Sob Consulta
BORBOREMA	PB	Interior 2	Nordeste	10
BREJO DO CRUZ	PB	Interior 1	Nordeste	10
BREJO DOS SANTOS	PB	Sob Consulta	Nordeste	Sob Consulta
CAAPORÃ	PB	Interior 2	Nordeste	10
CABACEIRAS	PB	Interior 1	Nordeste	10
CABEDELO	PB	Interior 1	Nordeste	10
CACHOEIRA DOS INDIOS	PB	Sob Consulta	Nordeste	Sob Consulta
CACIMBA DE AREIA	PB	Sob Consulta	Nordeste	Sob Consulta
CACIMBA DE DENTRO	PB	Interior 1	Nordeste	10
CACIMBAS	PB	Sob Consulta	Nordeste	Sob Consulta
CAIÇARA	PB	Interior 2	Nordeste	10
CAJAZEIRAS	PB	Interior 1	Nordeste	10
CAJAZEIRINHAS	PB	Sob Consulta	Nordeste	Sob Consulta
CALDAS DE BRANDÃO	PB	Interior 2	Nordeste	10
CAMALAU	PB	Interior 1	Nordeste	10
CAMPINA GRANDE	PB	Interior 1	Nordeste	10
CAPIM	PB	Interior 2	Nordeste	10
CARAUBAS	PB	Sob Consulta	Nordeste	Sob Consulta
CARRAPATEIRA	PB	Sob Consulta	Nordeste	Sob Consulta
CASSERENGUE	PB	Interior 2	Nordeste	10
CATINGUEIRA	PB	Sob Consulta	Nordeste	Sob Consulta
CATOLE DO ROCHA	PB	Interior 1	Nordeste	10
CATURITE	PB	Sob Consulta	Nordeste	Sob Consulta
CONCEICAO	PB	Sob Consulta	Nordeste	Sob Consulta
CONDADO	PB	Sob Consulta	Nordeste	Sob Consulta
CONDE	PB	Interior 1	Nordeste	10
CONGO	PB	Interior 1	Nordeste	10
COREMAS	PB	Sob Consulta	Nordeste	Sob Consulta
COXIXOLA	PB	Interior 1	Nordeste	10
CRUZ DO ESPIRITO SANTO	PB	Interior 1	Nordeste	10
CUBATI	PB	Interior 1	Nordeste	10
CUITE	PB	Interior 1	Nordeste	10
CUITE DE MAMANGUAPE	PB	Interior 2	Nordeste	10
CUITIGI	PB	Interior 2	Nordeste	10
CURRAL DE CIMA	PB	Interior 2	Nordeste	10
CURRAL VELHO	PB	Sob Consulta	Nordeste	Sob Consulta
DAMIÃO	PB	Interior 2	Nordeste	10
DESTERRO	PB	Sob Consulta	Nordeste	Sob Consulta
DIAMANTE	PB	Interior 2	Nordeste	10
DONA INES	PB	Interior 1	Nordeste	10
DUAS ESTRADAS	PB	Interior 1	Nordeste	10
EMAS	PB	Sob Consulta	Nordeste	Sob Consulta
ESPERANÇA	PB	Interior 1	Nordeste	10
FAGUNDES	PB	Interior 2	Nordeste	10
FREI MARTINHO	PB	Interior 1	Nordeste	10
GADO BRAVO	PB	Interior 1	Nordeste	10
GUARABIRA	PB	Interior 1	Nordeste	10
GURINHÉM	PB	Interior 2	Nordeste	10
GURJAO	PB	Sob Consulta	Nordeste	Sob Consulta
IBIARA	PB	Sob Consulta	Nordeste	Sob Consulta
IGARACY	PB	Sob Consulta	Nordeste	Sob Consulta
IMACULADA	PB	Sob Consulta	Nordeste	Sob Consulta
INGA	PB	Interior 2	Nordeste	10
ITABAIANA	PB	Interior 2	Nordeste	10
ITAPORANGA	PB	Interior 1	Nordeste	10
ITAPOROROCA	PB	Interior 2	Nordeste	10
ITATUBA	PB	Interior 1	Nordeste	10
JACARÚ	PB	Interior 2	Nordeste	10
JERICO	PB	Sob Consulta	Nordeste	Sob Consulta
JOÃO PESSOA	PB	Capital	Nordeste	7
JOCA CLAUDINO	PB	Sob Consulta	Nordeste	Sob Consulta
JUAREZ TAVORA	PB	Interior 2	Nordeste	10
JUAZEIRINHO	PB	Interior 1	Nordeste	10
JUNCO DO SERIDO	PB	Sob Consulta	Nordeste	Sob Consulta
JURIPIRANGA	PB	Interior 2	Nordeste	10
JURU	PB	Sob Consulta	Nordeste	Sob Consulta
LAGOA	PB	Sob Consulta	Nordeste	Sob Consulta
LAGOA DE DENTRO	PB	Interior 2	Nordeste	10
LAGOA SECA	PB	Interior 2	Nordeste	10
LASTRO	PB	Sob Consulta	Nordeste	Sob Consulta
LIVRAMENTO	PB	Interior 1	Nordeste	10
LOGRADOURO	PB	Interior 2	Nordeste	10
LUCENA	PB	Interior 2	Nordeste	10
MAE D AGUA	PB	Sob Consulta	Nordeste	Sob Consulta
MALTA	PB	Interior 1	Nordeste	10
MAMANGUAPE	PB	Interior 1	Nordeste	10
MANAIRA	PB	Sob Consulta	Nordeste	Sob Consulta
MARCACAO	PB	Sob Consulta	Nordeste	Sob Consulta
MARI	PB	Interior 1	Nordeste	10
MARIZOPOLIS	PB	Sob Consulta	Nordeste	Sob Consulta
MASSARANDUBA	PB	Interior 2	Nordeste	10
MATARACA	PB	Interior 2	Nordeste	10
MATINHAS	PB	Interior 2	Nordeste	10
MATO GROSSO	PB	Sob Consulta	Nordeste	Sob Consulta
MATUREIA	PB	Sob Consulta	Nordeste	Sob Consulta
MOGEIRO	PB	Interior 2	Nordeste	10
MONTADAS	PB	Interior 2	Nordeste	10
MONTE HOREBE	PB	Sob Consulta	Nordeste	Sob Consulta
MONTEIRO	PB	Interior 1	Nordeste	10
MULUNGU	PB	Interior 2	Nordeste	10
NATUBA	PB	Interior 1	Nordeste	10
NAZAREZINHO	PB	Sob Consulta	Nordeste	Sob Consulta
NOVA FLORESTA	PB	Interior 1	Nordeste	10
NOVA OLINDA	PB	Sob Consulta	Nordeste	Sob Consulta
NOVA PALMEIRA	PB	Interior 1	Nordeste	10
OLHO D AGUA	PB	Sob Consulta	Nordeste	Sob Consulta
OLIVEDOS	PB	Interior 1	Nordeste	10
OURO VELHO	PB	Interior 1	Nordeste	10
PARARI	PB	Interior 1	Nordeste	10
PASSAGEM	PB	Sob Consulta	Nordeste	Sob Consulta
PATOS	PB	Interior 1	Nordeste	10
PAULISTA	PB	Interior 1	Nordeste	10
PEDRA BRANCA	PB	Sob Consulta	Nordeste	Sob Consulta
PEDRA LAVRADA	PB	Interior 1	Nordeste	10
PEDRAS DE FOGO	PB	Interior 2	Nordeste	10
PEDRO REGIS	PB	Interior 2	Nordeste	10
PIANCÓ	PB	Interior 1	Nordeste	10
PICUI	PB	Interior 1	Nordeste	10
PILAR	PB	Interior 2	Nordeste	10
PILOES	PB	Interior 2	Nordeste	10
PILOEZINHOS	PB	Interior 2	Nordeste	10
PIRPIRITUBA	PB	Interior 1	Nordeste	10
PITIMBU	PB	Interior 2	Nordeste	10
POCINHOS	PB	Interior 1	Nordeste	10
POCO DANTAS	PB	Sob Consulta	Nordeste	Sob Consulta
POCO DE JOSE DE MOURA	PB	Sob Consulta	Nordeste	Sob Consulta
POMBAL	PB	Interior 1	Nordeste	10
PRATA	PB	Interior 1	Nordeste	10
PRINCESA ISABEL	PB	Sob Consulta	Nordeste	Sob Consulta
PUXINANA	PB	Interior 1	Nordeste	10
QUEIMADAS	PB	Interior 1	Nordeste	10
QUIXABA	PB	Sob Consulta	Nordeste	Sob Consulta
REMIGIO	PB	Interior 1	Nordeste	10
RIACHAO	PB	Sob Consulta	Nordeste	Sob Consulta
RIACHAO DO BACAMARTE	PB	Interior 2	Nordeste	10
RIACHAO DO POCO	PB	Interior 2	Nordeste	10
RIACHO DE SANTO ANTONIO	PB	Interior 2	Nordeste	10
RIACHO DOS CAVALOS	PB	Sob Consulta	Nordeste	Sob Consulta
RIO TINTO	PB	Interior 1	Nordeste	10
SALGADINHO	PB	Sob Consulta	Nordeste	Sob Consulta
SALGADO DE SAO FELIX	PB	Interior 2	Nordeste	10
SANTA CECILIA	PB	Interior 1	Nordeste	10
SANTA CRUZ	PB	Sob Consulta	Nordeste	Sob Consulta
SANTA HELENA	PB	Sob Consulta	Nordeste	Sob Consulta
SANTA INES	PB	Sob Consulta	Nordeste	Sob Consulta
SANTA LUZIA	PB	Interior 1	Nordeste	10
SANTA RITA	PB	Interior 1	Nordeste	10
SANTA TERESINHA	PB	Sob Consulta	Nordeste	Sob Consulta
SANTANA DE MANGUEIRA	PB	Sob Consulta	Nordeste	Sob Consulta
SANTANA DOS GARROTES	PB	Sob Consulta	Nordeste	Sob Consulta
SANTO ANDRE	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO BENTINHO	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO BENTO	PB	Interior 1	Nordeste	10
SÃO DOMINGOS 	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO DOMINGOS DO CARIRI	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO FRANCISCO	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOAO DO CARIRI	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOAO DO RIO DO PEIXE	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOAO DO TIGRE	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOSE DA LAGOA TAPADA	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOSE DE CAIANA	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOSE DE ESPINHARAS	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOSE DE PIRANHAS	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOSE DE PRINCESA	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOSE DO BONFIM	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOSE DO BREJO DO CRUZ	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOSE DO SABUGI	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO JOSE DOS CORDEIROS	PB	Interior 2	Nordeste	10
SÃO JOSE DOS RAMOS	PB	Interior 2	Nordeste	10
SÃO MAMEDE	PB	Interior 1	Nordeste	10
SÃO MIGUEL DE TAIPU	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO SEBASTIAO DE LAGOA DE ROCA	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO SEBASTIAO DO UMBUZEIRO	PB	Sob Consulta	Nordeste	Sob Consulta
SÃO VICENTE DO SERIDO	PB	Sob Consulta	Nordeste	Sob Consulta
SAPÉ	PB	Interior 1	Nordeste	10
SERRA BRANCA	PB	Interior 1	Nordeste	10
SERRA DA RAIZ	PB	Interior 2	Nordeste	10
SERRA GRANDE	PB	Sob Consulta	Nordeste	Sob Consulta
SERRA REDONDA	PB	Interior 2	Nordeste	10
SERRARIA	PB	Interior 2	Nordeste	10
SERTAOZINHO	PB	Sob Consulta	Nordeste	Sob Consulta
SOBRADO	PB	Interior 2	Nordeste	10
SOLANEA	PB	Interior 1	Nordeste	10
SOLEDADE	PB	Interior 1	Nordeste	10
SOSSEGO	PB	Interior 1	Nordeste	10
SOUSA	PB	Interior 1	Nordeste	10
SUME	PB	Sob Consulta	Nordeste	Sob Consulta
TACIMA	PB	Sob Consulta	Nordeste	Sob Consulta
TAPEROA	PB	Interior 1	Nordeste	10
TAVARES	PB	Sob Consulta	Nordeste	Sob Consulta
TEIXEIRA	PB	Interior 1	Nordeste	10
TENORIO	PB	Sob Consulta	Nordeste	Sob Consulta
TRIUNFO	PB	Sob Consulta	Nordeste	Sob Consulta
UIRAUNA	PB	Sob Consulta	Nordeste	Sob Consulta
UMBUZEIRO	PB	Interior 2	Nordeste	10
VARZEA	PB	Interior 1	Nordeste	10
VIEIROPOLIS	PB	Sob Consulta	Nordeste	Sob Consulta
VISTA SERRANA	PB	Sob Consulta	Nordeste	Sob Consulta
ZABELE	PB	Sob Consulta	Nordeste	Sob Consulta
ABREU E LIMA	PE	Interior 2	Nordeste	10
AFOGADOS DA INGAZEIRA	PE	Interior 2	Nordeste	10
AFRÂNIO	PE	Interior 2	Nordeste	10
AGRESTINA	PE	Interior 2	Nordeste	10
ÁGUA PRETA	PE	Interior 1	Nordeste	10
ÁGUAS BELAS	PE	Interior 2	Nordeste	10
ALAGOINHA	PE	Interior 2	Nordeste	10
ALIANÇA	PE	Interior 1	Nordeste	10
ALTINHO	PE	Interior 2	Nordeste	10
AMARAJI	PE	Interior 1	Nordeste	10
ANGELIM	PE	Interior 2	Nordeste	10
ARAÇOIABA	PE	Interior 1	Nordeste	10
ARARIPINA	PE	Interior 2	Nordeste	10
ARCOVERDE	PE	Interior 2	Nordeste	10
BARRA DE GUARABIRA	PE	Interior 1	Nordeste	10
BARREIROS	PE	Interior 1	Nordeste	10
BELÉM DE MARIA	PE	Interior 2	Nordeste	10
BELÉM DE SÃO FRANCISCO	PE	Interior 2	Nordeste	10
BELO JARDIM	PE	Interior 2	Nordeste	10
BETÂNIA	PE	Interior 2	Nordeste	10
BEZERRO	PE	Interior 1	Nordeste	10
BODOCÓ	PE	Interior 2	Nordeste	10
BOM CONSELHO	PE	Interior 2	Nordeste	10
BOM JARDIM	PE	Interior 1	Nordeste	10
BONITO	PE	Interior 1	Nordeste	10
BREJÃO	PE	Interior 2	Nordeste	10
BREJINHO	PE	Interior 2	Nordeste	10
BREJO DA MADRE DE DEUS	PE	Interior 2	Nordeste	10
BUENOS AIRES	PE	Interior 1	Nordeste	10
BUÍQUE	PE	Interior 2	Nordeste	10
CABO DE SANTO AGOSTINHO	PE	Interior 2	Nordeste	10
CABROBÓ	PE	Interior 2	Nordeste	10
CACHOEIRINHA	PE	Interior 2	Nordeste	10
CAETÉS	PE	Interior 2	Nordeste	10
CALÇADO	PE	Interior 2	Nordeste	10
CALUMBI	PE	Interior 2	Nordeste	10
CAMARAGIBE	PE	Interior 2	Nordeste	10
CAMOCIM DE SÃO FÉLIX	PE	Interior 1	Nordeste	10
CAMUTANGA	PE	Interior 1	Nordeste	10
CANHOTINHO	PE	Interior 2	Nordeste	10
CAPOEIRAS	PE	Interior 2	Nordeste	10
CARNAÍBA	PE	Interior 2	Nordeste	10
CARNAUBEIRA DA PENHA	PE	Interior 2	Nordeste	10
CARPINA	PE	Interior 1	Nordeste	10
CARUARU	PE	Interior 1	Nordeste	10
CASINHAS	PE	Interior 1	Nordeste	10
CATENDE	PE	Interior 1	Nordeste	10
CEDRO	PE	Interior 2	Nordeste	10
CHÃ DE ALEGRIA	PE	Interior 1	Nordeste	10
CHÃ GRANDE	PE	Interior 1	Nordeste	10
CONDADO	PE	Interior 1	Nordeste	10
CORRENTES	PE	Interior 2	Nordeste	10
CORTÊS	PE	Interior 1	Nordeste	10
CUMARU	PE	Interior 1	Nordeste	10
CUPIRA	PE	Interior 2	Nordeste	10
CUSTÓDIA	PE	Interior 2	Nordeste	10
DORMENTES	PE	Interior 2	Nordeste	10
ESCADA	PE	Interior 1	Nordeste	10
EXU	PE	Interior 2	Nordeste	10
FEIRA NOVA	PE	Interior 1	Nordeste	10
FERNANDO DE NORONHA	PE	Sob Consulta	Nordeste	Sob Consulta
FERREIROS	PE	Interior 1	Nordeste	10
FLORES	PE	Interior 2	Nordeste	10
FLORESTA	PE	Interior 2	Nordeste	10
FREI MIGUELINHO	PE	Interior 2	Nordeste	10
GAMELEIRA	PE	Interior 1	Nordeste	10
GARANHUNS	PE	Interior 2	Nordeste	10
GLORIA DO GOITÁ	PE	Interior 1	Nordeste	10
GOIANA	PE	Interior 1	Nordeste	10
GRANITO	PE	Interior 2	Nordeste	10
GRAVATÁ	PE	Interior 1	Nordeste	10
IATI	PE	Interior 2	Nordeste	10
IBIMIRIM	PE	Interior 2	Nordeste	10
IBIRAJUBA	PE	Interior 2	Nordeste	10
IGARASSU	PE	Interior 1	Nordeste	10
IGUARACI	PE	Interior 2	Nordeste	10
ILHA DE ITAMARACÁ	PE	Interior 1	Nordeste	10
INAJÁ	PE	Interior 2	Nordeste	10
INGAZEIRA	PE	Interior 2	Nordeste	10
IPOJUCA	PE	Interior 1	Nordeste	10
IPUBI	PE	Interior 2	Nordeste	10
ITACURUBÁ	PE	Interior 2	Nordeste	10
ITAÍBA	PE	Interior 2	Nordeste	10
ITAMBÉ	PE	Interior 1	Nordeste	10
ITAPETIM	PE	Interior 2	Nordeste	10
ITAPISSUMA	PE	Interior 1	Nordeste	10
ITAQUITINGA	PE	Interior 1	Nordeste	10
JABOATAO DOS GUARARAPES	PE	Capital	Nordeste	7
JAQUEIRA	PE	Interior 1	Nordeste	10
JATAÚBA	PE	Interior 2	Nordeste	10
JATOBÁ	PE	Interior 2	Nordeste	10
JOÃO ALFREDO	PE	Interior 1	Nordeste	10
JOAQUIM NABUCO	PE	Interior 1	Nordeste	10
JUCATI	PE	Interior 2	Nordeste	10
JUPI	PE	Interior 2	Nordeste	10
JUREMA	PE	Interior 2	Nordeste	10
LAGOA DO CARRO	PE	Interior 1	Nordeste	10
LAGOA DO ITAENGA	PE	Interior 1	Nordeste	10
LAGOA DO OURO	PE	Interior 2	Nordeste	10
LAGOA DOS GATOS	PE	Interior 2	Nordeste	10
LAGOA GRANDE	PE	Interior 2	Nordeste	10
LAJEDO	PE	Interior 2	Nordeste	10
LIMOEIRO	PE	Interior 1	Nordeste	10
MACAPARANA	PE	Interior 1	Nordeste	10
MACHADOS	PE	Interior 1	Nordeste	10
MANARI	PE	Interior 2	Nordeste	10
MARAIAL	PE	Interior 2	Nordeste	10
MIRANDIBA	PE	Interior 2	Nordeste	10
MOREILÂNDIA	PE	Interior 2	Nordeste	10
MORENO	PE	Interior 2	Nordeste	10
NAZARÉ DA MATA	PE	Interior 1	Nordeste	10
OLINDA	PE	Capital	Nordeste	7
OROBÓ	PE	Interior 1	Nordeste	10
OROCÓ	PE	Interior 2	Nordeste	10
OURICURI	PE	Interior 2	Nordeste	10
PALMARES	PE	Interior 1	Nordeste	10
PALMEIRINA	PE	Interior 2	Nordeste	10
PANELAS	PE	Interior 2	Nordeste	10
PARANATAMA	PE	Interior 2	Nordeste	10
PARNAMIRIM	PE	Interior 2	Nordeste	10
PASSIRA	PE	Interior 1	Nordeste	10
PAUDALHO	PE	Interior 1	Nordeste	10
PAULISTA	PE	Interior 2	Nordeste	10
PEDRA	PE	Interior 2	Nordeste	10
PESQUEIRA	PE	Interior 2	Nordeste	10
PETROLÂNDIA	PE	Interior 2	Nordeste	10
PETROLINA	PE	Interior 2	Nordeste	10
POÇÃO	PE	Interior 2	Nordeste	10
POMBOS	PE	Interior 1	Nordeste	10
PRIMAVERA	PE	Interior 1	Nordeste	10
QUIPAPÁ	PE	Interior 2	Nordeste	10
QUIXABA	PE	Interior 2	Nordeste	10
RECIFE	PE	Capital	Nordeste	7
RIACHO DAS ALMAS	PE	Interior 2	Nordeste	10
RIBEIRÃO	PE	Interior 1	Nordeste	10
RIO FORMOSO	PE	Interior 1	Nordeste	10
SAIRÉ	PE	Interior 1	Nordeste	10
SALGADINHO	PE	Interior 1	Nordeste	10
SALGUEIRO	PE	Interior 2	Nordeste	10
SALOÁ	PE	Interior 2	Nordeste	10
SANHARÓ	PE	Interior 2	Nordeste	10
SANTA CRUZ	PE	Interior 2	Nordeste	10
SANTA CRUZ DA BAIXA VERDE	PE	Interior 2	Nordeste	10
SANTA CRUZ DO CAPIBARIBE	PE	Interior 2	Nordeste	10
SANTA FILOMENA	PE	Interior 2	Nordeste	10
SANTA MARIA DA BOA VISTA	PE	Interior 2	Nordeste	10
SANTA MARIA DO CAMBUCÁ	PE	Interior 1	Nordeste	10
SANTA TEREZINHA	PE	Interior 2	Nordeste	10
SÃO BENEDITO DO SUL	PE	Interior 2	Nordeste	10
SÃO BENTO DO UMA	PE	Interior 2	Nordeste	10
SÃO CAITANO	PE	Interior 2	Nordeste	10
SÃO JOÃO	PE	Interior 2	Nordeste	10
SÃO JOAQUIM DO MONTE	PE	Interior 1	Nordeste	10
SÃO JOSÉ DA COROA GRANDE	PE	Interior 1	Nordeste	10
SÃO JOSÉ DO BELMONTE	PE	Interior 2	Nordeste	10
SÃO JOSÉ DO EGITO	PE	Interior 2	Nordeste	10
SÃO LOURENÇO DA MATA	PE	Interior 1	Nordeste	10
SÃO VICENTE FERRER	PE	Interior 1	Nordeste	10
SERRA TALHADA	PE	Interior 2	Nordeste	10
SERRITA	PE	Interior 2	Nordeste	10
SERTÂNIA	PE	Interior 2	Nordeste	10
SIRINHAÉM	PE	Interior 1	Nordeste	10
SOLIDÃO	PE	Interior 2	Nordeste	10
SURUBIM	PE	Interior 1	Nordeste	10
TABIRA	PE	Interior 2	Nordeste	10
TACAIMBÓ	PE	Interior 2	Nordeste	10
TACARATU	PE	Interior 2	Nordeste	10
TAMANDARÉ	PE	Interior 1	Nordeste	10
TAQUARITINGA DO NORTE	PE	Interior 2	Nordeste	10
TEREZINHA	PE	Interior 2	Nordeste	10
TERRA NOVA	PE	Interior 2	Nordeste	10
TIMBAÚBA	PE	Interior 1	Nordeste	10
TORITAMA	PE	Interior 2	Nordeste	10
TRACUNHAÉM	PE	Interior 1	Nordeste	10
TRINDADE	PE	Interior 2	Nordeste	10
TRIUNFO	PE	Interior 2	Nordeste	10
TUPANATINGA	PE	Interior 2	Nordeste	10
TUPARETAMA	PE	Interior 2	Nordeste	10
VENTUROSA	PE	Interior 2	Nordeste	10
VERDEJANTE	PE	Interior 2	Nordeste	10
VERTENTE DO LÉRIO	PE	Interior 1	Nordeste	10
VERTENTES	PE	Interior 2	Nordeste	10
VICÊNCIA	PE	Interior 1	Nordeste	10
VITÓRIA DE SANTO ANTÃO	PE	Interior 1	Nordeste	10
XEXÉU	PE	Interior 1	Nordeste	10
ACAUA	PI	Interior 1	Nordeste	12
AGRICOLANDIA	PI	Sob Consulta	Nordeste	Sob Consulta
AGUA BRANCA	PI	Interior 1	Nordeste	12
ALAGOINHA DO PIAUI	PI	Interior 1	Nordeste	12
ALEGRETE DO PIAUI	PI	Interior 1	Nordeste	12
ALTO LONGA	PI	Interior 1	Nordeste	12
ALTOS	PI	Interior 1	Nordeste	12
ALVORADA DO GURGUEIA	PI	Interior 1	Nordeste	12
AMARANTE	PI	Interior 1	Nordeste	12
ANGICAL DO PIAUI	PI	Interior 1	Nordeste	12
ANISIO DE ABREU	PI	Sob Consulta	Nordeste	Sob Consulta
ANTÔNIO ALMEIDA	PI	Sob Consulta	Nordeste	Sob Consulta
AROAZES	PI	Interior 1	Nordeste	12
AROEIRAS DO ITAIM	PI	Sob Consulta	Nordeste	Sob Consulta
ARRAIAL	PI	Interior 1	Nordeste	12
ASSUNCAO DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
AVELINO LOPES	PI	Interior 1	Nordeste	12
BAIXA GRANDE DO RIBEIRO	PI	Sob Consulta	Nordeste	Sob Consulta
BARRA D ALCANTARA	PI	Interior 1	Nordeste	12
BARRAS	PI	Interior 1	Nordeste	12
BARREIRAS DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
BARRO DURO	PI	Interior 1	Nordeste	12
BATALHA	PI	Interior 1	Nordeste	12
BELA VISTA DO PIAUI	PI	Interior 1	Nordeste	12
BELEM DO PIAUI	PI	Interior 1	Nordeste	12
BENEDITINOS	PI	Interior 1	Nordeste	12
BERTOLINIA	PI	Interior 1	Nordeste	12
BETANIA DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
BOA HORA	PI	Interior 1	Nordeste	12
BOCAINA	PI	Interior 1	Nordeste	12
BOM JESUS	PI	Interior 1	Nordeste	12
BOM PRINCIPIO DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
BONFIM DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
BOQUEIRAO DO PIAUI	PI	Interior 1	Nordeste	12
BRASILEIRA	PI	Interior 1	Nordeste	12
BREJO DO PIAUI	PI	Interior 1	Nordeste	12
BURITI DOS LOPES	PI	Interior 1	Nordeste	12
BURITI DOS MONTES	PI	Sob Consulta	Nordeste	Sob Consulta
CABECEIRAS DO PIAUI	PI	Interior 1	Nordeste	12
CAJAZEIRAS DO PIAUI	PI	Interior 1	Nordeste	12
CAJUEIRO DA PRAIA	PI	Interior 1	Nordeste	12
CALDEIRAO GRANDE DO PIAUI	PI	Interior 1	Nordeste	12
CAMPINAS DO PIAUI	PI	Interior 1	Nordeste	12
CAMPO ALEGRE DO FIDALGO	PI	Interior 1	Nordeste	12
CAMPO GRANDE DO PIAUI	PI	Interior 1	Nordeste	12
CAMPO LARGO DO PIAUI	PI	Interior 1	Nordeste	12
CAMPO MAIOR	PI	Interior 1	Nordeste	12
CANAVIEIRA	PI	Sob Consulta	Nordeste	Sob Consulta
CANTO DO BURITI	PI	Interior 1	Nordeste	12
CAPITAO DE CAMPOS	PI	Interior 1	Nordeste	12
CAPITAO GERVASIO OLIVEIRA	PI	Interior 1	Nordeste	12
CARACOL	PI	Sob Consulta	Nordeste	Sob Consulta
CARAUBAS DO PIAUI	PI	Interior 1	Nordeste	12
CARIDADE DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
CASTELO DO PIAUI	PI	Interior 1	Nordeste	12
CAXINGO	PI	Interior 1	Nordeste	12
COCAL	PI	Interior 1	Nordeste	12
COCAL DE TELHA	PI	Interior 1	Nordeste	12
COCAL DOS ALVES	PI	Sob Consulta	Nordeste	Sob Consulta
COIVARAS	PI	Interior 1	Nordeste	12
COLONIA DO GURGUEIA	PI	Interior 1	Nordeste	12
COLÔNIA DO PIAUÍ	PI	Interior 1	Nordeste	12
CONCEICAO DO CANINDE	PI	Sob Consulta	Nordeste	Sob Consulta
CORONEL JOSÉ DIAS	PI	Interior 1	Nordeste	12
CORRENTE	PI	Interior 1	Nordeste	12
CRISTALANDIA DO PIAUI	PI	Interior 1	Nordeste	12
CRISTINO CASTRO	PI	Interior 1	Nordeste	12
CURIMATA	PI	Interior 1	Nordeste	12
CURRAIS	PI	Sob Consulta	Nordeste	Sob Consulta
CURRAL NOVO DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
CURRALINHOS	PI	Sob Consulta	Nordeste	Sob Consulta
DEMERVAL LOBãO	PI	Interior 1	Nordeste	12
DIRCEU ARCOVERDE	PI	Sob Consulta	Nordeste	Sob Consulta
DOM EXPEDITO LOPES	PI	Interior 1	Nordeste	12
DOM INOCENCIO	PI	Sob Consulta	Nordeste	Sob Consulta
DOMINGOS MOURAO	PI	Sob Consulta	Nordeste	Sob Consulta
ELESBAO VELOSO	PI	Interior 1	Nordeste	12
ELISEU MARTINS	PI	Interior 1	Nordeste	12
ESPERANTINA	PI	Interior 1	Nordeste	12
FARTURA DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
FLORES DO PIAUI	PI	Interior 1	Nordeste	12
FLORESTA DO PIAUI	PI	Interior 1	Nordeste	12
FLORIANO	PI	Interior 1	Nordeste	12
FRANCINOPOLIS	PI	Interior 1	Nordeste	12
FRANCISCO AYRES	PI	Interior 1	Nordeste	12
FRANCISCO MACEDO	PI	Interior 1	Nordeste	12
FRANCISCO SANTOS	PI	Interior 1	Nordeste	12
FRONTEIRAS	PI	Interior 1	Nordeste	12
GEMINIANO	PI	Interior 1	Nordeste	12
GILBUES	PI	Interior 1	Nordeste	12
GUADALUPE	PI	Sob Consulta	Nordeste	Sob Consulta
GUARIBAS	PI	Sob Consulta	Nordeste	Sob Consulta
HUGO NAPOLEAO	PI	Interior 1	Nordeste	12
ILHA GRANDE	PI	Interior 1	Nordeste	12
INHUMA	PI	Interior 1	Nordeste	12
IPIRANGA DO PIAUí	PI	Interior 1	Nordeste	12
ISAIAS COELHO	PI	Interior 1	Nordeste	12
ITAINOPOLIS	PI	Interior 1	Nordeste	12
ITAUEIRA	PI	Interior 1	Nordeste	12
JACOBINA DO PIAUI	PI	Interior 1	Nordeste	12
JAICOS	PI	Interior 1	Nordeste	12
JARDIM DO MULATO	PI	Interior 1	Nordeste	12
JATOBA DO PIAUI	PI	Interior 1	Nordeste	12
JERUMENHA	PI	Interior 1	Nordeste	12
JOAO COSTA	PI	Sob Consulta	Nordeste	Sob Consulta
JOAQUIM PIRES	PI	Interior 1	Nordeste	12
JOCA MARQUES	PI	Interior 1	Nordeste	12
JOSE DE FREITAS	PI	Interior 1	Nordeste	12
JUAZEIRO DO PIAUI	PI	Interior 1	Nordeste	12
JULIO BORGES	PI	Interior 1	Nordeste	12
JUREMA	PI	Sob Consulta	Nordeste	Sob Consulta
LAGOA ALEGRE	PI	Sob Consulta	Nordeste	Sob Consulta
LAGOA DE SAO FRANCISCO	PI	Interior 1	Nordeste	12
LAGOA DO BARRO DO PIAUI	PI	Interior 1	Nordeste	12
LAGOA DO PIAUí	PI	Interior 1	Nordeste	12
LAGOA DO SITIO	PI	Interior 1	Nordeste	12
LAGOINHA DO PIAUÍ	PI	Interior 1	Nordeste	12
LANDRI SALES	PI	Sob Consulta	Nordeste	Sob Consulta
LUIS CORREIA	PI	Interior 1	Nordeste	12
LUZILANDIA	PI	Interior 1	Nordeste	12
MADEIRO	PI	Interior 1	Nordeste	12
MANOEL EMIDIO	PI	Interior 1	Nordeste	12
MARCOLANDIA	PI	Interior 1	Nordeste	12
MARCOS PARENTE	PI	Sob Consulta	Nordeste	Sob Consulta
MASSAPE DO PIAUI	PI	Interior 1	Nordeste	12
MATIAS OLIMPIO	PI	Interior 1	Nordeste	12
MIGUEL ALVES	PI	Interior 1	Nordeste	12
MIGUEL LEAO	PI	Sob Consulta	Nordeste	Sob Consulta
MILTON BRANDAO	PI	Interior 1	Nordeste	12
MONSENHOR GIL	PI	Interior 1	Nordeste	12
MONSENHOR HIPOLITO	PI	Interior 1	Nordeste	12
MONTE ALEGRE DO PIAUI	PI	Interior 1	Nordeste	12
MORRO CABECA NO TEMPO	PI	Sob Consulta	Nordeste	Sob Consulta
MORRO DO CHAPÉU DO PIAUÍ	PI	Interior 1	Nordeste	12
MURICI DOS PORTELAS	PI	Interior 1	Nordeste	12
NAZARE DO PIAUI	PI	Interior 1	Nordeste	12
NAZARIA	PI	Sob Consulta	Nordeste	Sob Consulta
NOSSA SENHORA DE NAZARE	PI	Interior 1	Nordeste	12
NOSSA SENHORA DOS REMEDIOS	PI	Interior 1	Nordeste	12
NOVA SANTA RITA	PI	Interior 1	Nordeste	12
NOVO ORIENTE DO PIAUI	PI	Interior 1	Nordeste	12
NOVO SANTO ANTONIO	PI	Interior 1	Nordeste	12
OEIRAS	PI	Interior 1	Nordeste	12
OLHO D AGUA DO PIAUI	PI	Interior 1	Nordeste	12
PADRE MARCOS	PI	Interior 1	Nordeste	12
PAES LANDIM	PI	Interior 1	Nordeste	12
PAJEU DO PIAUI	PI	Interior 1	Nordeste	12
PALMEIRA DO PIAUI	PI	Interior 1	Nordeste	12
PALMEIRAIS	PI	Sob Consulta	Nordeste	Sob Consulta
PAQUETA	PI	Sob Consulta	Nordeste	Sob Consulta
PARNAGUA	PI	Interior 1	Nordeste	12
PARNAíBA	PI	Interior 1	Nordeste	12
PASSAGEM FRANCA DO PIAUI	PI	Interior 1	Nordeste	12
PATOS DO PIAUI	PI	Interior 1	Nordeste	12
PAU D ARCO DO PIAUI	PI	Interior 1	Nordeste	12
PAULISTANA	PI	Interior 1	Nordeste	12
PAVUSSU	PI	Sob Consulta	Nordeste	Sob Consulta
PEDRO II	PI	Interior 1	Nordeste	12
PEDRO LAURENTINO	PI	Interior 1	Nordeste	12
PICOS	PI	Interior 1	Nordeste	12
PIMENTEIRAS	PI	Interior 1	Nordeste	12
PIO IX	PI	Interior 1	Nordeste	12
PIRACURUCA	PI	Interior 1	Nordeste	12
PIRIPIRI	PI	Interior 1	Nordeste	12
PORTO	PI	Interior 1	Nordeste	12
PORTO ALEGRE DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
PRATA DO PIAUI	PI	Interior 1	Nordeste	12
QUEIMADA NOVA	PI	Interior 1	Nordeste	12
REDENCAO DO GURGUEIA	PI	Interior 1	Nordeste	12
REGENERAÇÃO	PI	Interior 1	Nordeste	12
RIACHO FRIO	PI	Sob Consulta	Nordeste	Sob Consulta
RIBEIRA DO PIAUI	PI	Interior 1	Nordeste	12
RIBEIRO GONCALVES	PI	Sob Consulta	Nordeste	Sob Consulta
RIO GRANDE DO PIAUI	PI	Interior 1	Nordeste	12
SANTA CRUZ DO PIAUI	PI	Interior 1	Nordeste	12
SANTA CRUZ DOS MILAGRES	PI	Interior 1	Nordeste	12
SANTA FILOMENA	PI	Sob Consulta	Nordeste	Sob Consulta
SANTA LUZ	PI	Interior 1	Nordeste	12
SANTA ROSA DO PIAUI	PI	Interior 1	Nordeste	12
SANTANA DO PIAUI	PI	Interior 1	Nordeste	12
SANTO ANTONIO DE LISBOA	PI	Interior 1	Nordeste	12
SANTO ANTONIO DOS MILAGRES	PI	Interior 1	Nordeste	12
SANTO INACIO DO PIAUI	PI	Interior 1	Nordeste	12
SAO BRAZ DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
SAO FELIX DO PIAUI	PI	Interior 1	Nordeste	12
SAO FRANCISCO DE ASSIS DO PIAUI	PI	Interior 1	Nordeste	12
SAO FRANCISCO DO PIAUI	PI	Interior 1	Nordeste	12
SAO GONCALO DO GURGUEIA	PI	Interior 1	Nordeste	12
SAO GONCALO DO PIAUI	PI	Interior 1	Nordeste	12
SAO JOAO DA CANABRAVA	PI	Interior 1	Nordeste	12
SAO JOAO DA FRONTEIRA	PI	Sob Consulta	Nordeste	Sob Consulta
SAO JOAO DA SERRA	PI	Interior 1	Nordeste	12
SAO JOAO DA VARJOTA	PI	Sob Consulta	Nordeste	Sob Consulta
SAO JOAO DO ARRAIAL	PI	Sob Consulta	Nordeste	Sob Consulta
SÃO JOÃO DO PIAUÍ	PI	Interior 1	Nordeste	12
SAO JOSE DO DIVINO	PI	Interior 1	Nordeste	12
SAO JOSE DO PEIXE	PI	Interior 1	Nordeste	12
SAO JOSE DO PIAUI	PI	Interior 1	Nordeste	12
SAO JULIAO	PI	Interior 1	Nordeste	12
SAO LOURENCO DO PIAUI	PI	Sob Consulta	Nordeste	Sob Consulta
SAO LUIS DO PIAUI	PI	Interior 1	Nordeste	12
SAO MIGUEL DA BAIXA GRANDE	PI	Interior 1	Nordeste	12
SAO MIGUEL DO FIDALGO	PI	Interior 1	Nordeste	12
SAO MIGUEL DO TAPUIO	PI	Interior 1	Nordeste	12
SAO PEDRO DO PIAUI	PI	Interior 1	Nordeste	12
SãO RAIMUNDO NONATO	PI	Interior 1	Nordeste	12
SEBASTIAO BARROS	PI	Sob Consulta	Nordeste	Sob Consulta
SEBASTIÃO LEAL	PI	Sob Consulta	Nordeste	Sob Consulta
SIGEFREDO PACHECO	PI	Interior 1	Nordeste	12
SIMOES	PI	Interior 1	Nordeste	12
SIMPLICIO MENDES	PI	Interior 1	Nordeste	12
SOCORRO DO PIAUI	PI	Interior 1	Nordeste	12
SUSSUAPARA	PI	Interior 1	Nordeste	12
TAMBORIL DO PIAUI	PI	Interior 1	Nordeste	12
TANQUE DO PIAUI	PI	Interior 1	Nordeste	12
TERESINA	PI	Capital	Nordeste	8
UNIÃO	PI	Interior 1	Nordeste	12
URUÇUI	PI	Sob Consulta	Nordeste	Sob Consulta
VALENÇA DO PIAUÍ	PI	Interior 1	Nordeste	12
VARZEA BRANCA	PI	Sob Consulta	Nordeste	Sob Consulta
VARZEA GRANDE	PI	Interior 1	Nordeste	12
VERA MENDES	PI	Interior 1	Nordeste	12
VILA NOVA DO PIAUI	PI	Interior 1	Nordeste	12
WALL FERRAZ	PI	Interior 1	Nordeste	12
ABATIA	PR	Interior 1	Sul	5
ADRIANOPOLIS	PR	Interior 1	Sul	5
AGUDOS DO SUL	PR	Interior 1	Sul	5
ALMIRANTE TAMANDARE	PR	Interior 1	Sul	5
ALTAMIRA DO PARANA	PR	Interior 1	Sul	5
ALTO PARAISO	PR	Interior 1	Sul	5
ALTO PARANA	PR	Interior 1	Sul	5
ALTO PIQUIRI	PR	Interior 1	Sul	5
ALTONIA	PR	Interior 1	Sul	5
ALVORADA DO SUL	PR	Interior 1	Sul	5
AMAPORA	PR	Interior 1	Sul	5
AMPERE	PR	Interior 1	Sul	5
ANAHY	PR	Interior 1	Sul	5
ANDIRA	PR	Interior 1	Sul	5
ANGULO	PR	Interior 1	Sul	5
ANTONINA	PR	Interior 1	Sul	5
ANTONIO OLINTO	PR	Interior 1	Sul	5
APUCARANA	PR	Interior 1	Sul	5
ARAPONGAS	PR	Interior 1	Sul	5
ARAPOTI	PR	Interior 1	Sul	5
ARAPUA	PR	Interior 1	Sul	5
ARARUNA	PR	Interior 1	Sul	5
ARAUCARIA	PR	Capital	Sul	2
ARIRANHA DO IVAI	PR	Interior 1	Sul	5
ASSAI	PR	Interior 1	Sul	5
ASSIS CHATEAUBRIAND	PR	Interior 1	Sul	5
ASTORGA	PR	Interior 1	Sul	5
ATALAIA	PR	Interior 1	Sul	5
BALSA NOVA	PR	Interior 1	Sul	5
BANDEIRANTES	PR	Interior 1	Sul	5
BARBOSA FERRAZ	PR	Interior 1	Sul	5
BARRA DO JACARE	PR	Interior 1	Sul	5
BARRACAO	PR	Interior 1	Sul	5
BELA VISTA DA CAROBA	PR	Interior 1	Sul	5
BELA VISTA DO PARAISO	PR	Interior 1	Sul	5
BITURUNA	PR	Interior 1	Sul	5
BOA ESPERANCA	PR	Interior 1	Sul	5
BOA ESPERANCA DO IGUACU	PR	Interior 1	Sul	5
BOA VENTURA DE SAO ROQUE	PR	Interior 1	Sul	5
BOA VISTA DA APARECIDA	PR	Interior 1	Sul	5
BOCAIUVA DO SUL	PR	Interior 1	Sul	5
BOM JESUS DO SUL	PR	Interior 1	Sul	5
BOM SUCESSO	PR	Interior 1	Sul	5
BOM SUCESSO DO SUL	PR	Interior 1	Sul	5
BORRAZOPOLIS	PR	Interior 1	Sul	5
BRAGANEY	PR	Interior 1	Sul	5
BRASILANDIA DO SUL	PR	Interior 1	Sul	5
CAFEARA	PR	Interior 1	Sul	5
CAFELANDIA	PR	Interior 1	Sul	5
CAFEZAL DO SUL	PR	Interior 1	Sul	5
CALIFORNIA	PR	Interior 1	Sul	5
CAMBARA	PR	Interior 1	Sul	5
CAMBE	PR	Interior 1	Sul	5
CAMBIRA	PR	Interior 1	Sul	5
CAMPINA DA LAGOA	PR	Interior 1	Sul	5
CAMPINA DO SIMAO	PR	Interior 1	Sul	5
CAMPINA GRANDE DO SUL	PR	Capital	Sul	2
CAMPO BONITO	PR	Interior 1	Sul	5
CAMPO DO TENENTE	PR	Interior 1	Sul	5
CAMPO LARGO	PR	Interior 1	Sul	5
CAMPO MAGRO	PR	Capital	Sul	2
CAMPO MOURAO	PR	Interior 1	Sul	5
CANDIDO DE ABREU	PR	Interior 1	Sul	5
CANDOI	PR	Interior 1	Sul	5
CANTAGALO	PR	Interior 1	Sul	5
CAPANEMA	PR	Interior 1	Sul	5
CAPITAO LEONIDAS MARQUES	PR	Interior 1	Sul	5
CARAMBEI	PR	Interior 1	Sul	5
CARLOPOLIS	PR	Interior 1	Sul	5
CASCAVEL	PR	Interior 1	Sul	5
CASTRO	PR	Interior 1	Sul	5
CATANDUVAS	PR	Interior 1	Sul	5
CENTENARIO DO SUL	PR	Interior 1	Sul	5
CERRO AZUL	PR	Interior 1	Sul	5
CEU AZUL	PR	Interior 1	Sul	5
CHOPINZINHO	PR	Interior 1	Sul	5
CIANORTE	PR	Interior 1	Sul	5
CIDADE GAUCHA	PR	Interior 1	Sul	5
CLEVELANDIA	PR	Interior 1	Sul	5
COLOMBO	PR	Interior 1	Sul	5
COLORADO	PR	Interior 1	Sul	5
CONGONHINHAS	PR	Interior 1	Sul	5
CONSELHEIRO MAIRINCK	PR	Interior 1	Sul	5
CONTENDA	PR	Interior 1	Sul	5
CORBELIA	PR	Interior 1	Sul	5
CORNELIO PROCOPIO	PR	Interior 1	Sul	5
CORONEL DOMINGOS SOARES	PR	Interior 1	Sul	5
CORONEL VIVIDA	PR	Interior 1	Sul	5
CORUMBATAI DO SUL	PR	Interior 1	Sul	5
CRUZ MACHADO	PR	Interior 1	Sul	5
CRUZEIRO DO IGUACU	PR	Interior 1	Sul	5
CRUZEIRO DO OESTE	PR	Interior 1	Sul	5
CRUZEIRO DO SUL	PR	Interior 1	Sul	5
CRUZMALTINA	PR	Interior 1	Sul	5
CURITIBA	PR	Capital	Sul	2
CURIUVA	PR	Interior 1	Sul	5
DIAMANTE DO NORTE	PR	Interior 1	Sul	5
DIAMANTE DO SUL	PR	Interior 1	Sul	5
DIAMANTE D OESTE	PR	Interior 1	Sul	5
DOIS VIZINHOS	PR	Interior 1	Sul	5
DOURADINA	PR	Interior 1	Sul	5
DOUTOR CAMARGO	PR	Interior 1	Sul	5
DOUTOR ULYSSES	PR	Interior 1	Sul	5
ENEAS MARQUES	PR	Interior 1	Sul	5
ENGENHEIRO BELTRAO	PR	Interior 1	Sul	5
ENTRE RIOS DO OESTE	PR	Interior 1	Sul	5
ESPERANCA NOVA	PR	Interior 1	Sul	5
ESPIGAO ALTO DO IGUACU	PR	Interior 1	Sul	5
FAROL	PR	Interior 1	Sul	5
FAXINAL	PR	Interior 1	Sul	5
FAZENDA RIO GRANDE	PR	Interior 1	Sul	5
FENIX	PR	Interior 1	Sul	5
FERNANDES PINHEIRO	PR	Interior 1	Sul	5
FIGUEIRA	PR	Interior 1	Sul	5
FLOR DA SERRA DO SUL	PR	Interior 1	Sul	5
FLORAI	PR	Interior 1	Sul	5
FLORESTA	PR	Interior 1	Sul	5
FLORESTOPOLIS	PR	Interior 1	Sul	5
FLORIDA	PR	Interior 1	Sul	5
FORMOSA DO OESTE	PR	Interior 1	Sul	5
FOZ DO IGUACU	PR	Interior 1	Sul	5
FOZ DO JORDAO	PR	Interior 1	Sul	5
FRANCISCO ALVES	PR	Interior 1	Sul	5
FRANCISCO BELTRAO	PR	Interior 1	Sul	5
GENERAL CARNEIRO	PR	Interior 1	Sul	5
GODOY MOREIRA	PR	Interior 1	Sul	5
GOIOERE	PR	Interior 1	Sul	5
GOIOXIM	PR	Interior 1	Sul	5
GRANDES RIOS	PR	Interior 1	Sul	5
GUAIRA	PR	Interior 1	Sul	5
GUAIRACA	PR	Interior 1	Sul	5
GUAMIRANGA	PR	Interior 1	Sul	5
GUAPIRAMA	PR	Interior 1	Sul	5
GUAPOREMA	PR	Interior 1	Sul	5
GUARACI	PR	Interior 1	Sul	5
GUARANIACU	PR	Interior 1	Sul	5
GUARAPUAVA	PR	Interior 1	Sul	5
GUARAQUECABA	PR	Interior 1	Sul	5
GUARATUBA	PR	Interior 1	Sul	5
HONORIO SERPA	PR	Interior 1	Sul	5
IBAITI	PR	Interior 1	Sul	5
IBEMA	PR	Interior 1	Sul	5
IBIPORA	PR	Interior 1	Sul	5
ICARAIMA	PR	Interior 1	Sul	5
IGUARACU	PR	Interior 1	Sul	5
IGUATU	PR	Interior 1	Sul	5
IMBAU	PR	Interior 1	Sul	5
IMBITUVA	PR	Interior 1	Sul	5
INACIO MARTINS	PR	Interior 1	Sul	5
INAJA	PR	Interior 1	Sul	5
INDIANOPOLIS	PR	Interior 1	Sul	5
IPIRANGA	PR	Interior 1	Sul	5
IPORA	PR	Interior 1	Sul	5
IRACEMA DO OESTE	PR	Interior 1	Sul	5
IRATI	PR	Interior 1	Sul	5
IRETAMA	PR	Interior 1	Sul	5
ITAGUAJE	PR	Interior 1	Sul	5
ITAIPULANDIA	PR	Interior 1	Sul	5
ITAMBARACA	PR	Interior 1	Sul	5
ITAMBE	PR	Interior 1	Sul	5
ITAPEJARA D OESTE	PR	Interior 1	Sul	5
ITAPERUCU	PR	Interior 1	Sul	5
ITAUNA DO SUL	PR	Interior 1	Sul	5
IVAI	PR	Interior 1	Sul	5
IVAIPORA	PR	Interior 1	Sul	5
IVATE	PR	Interior 1	Sul	5
IVATUBA	PR	Interior 1	Sul	5
JABOTI	PR	Interior 1	Sul	5
JACAREZINHO	PR	Interior 1	Sul	5
JAGUAPITA	PR	Interior 1	Sul	5
JAGUARIAIVA	PR	Interior 1	Sul	5
JANDAIA DO SUL	PR	Interior 1	Sul	5
JANIOPOLIS	PR	Interior 1	Sul	5
JAPIRA	PR	Interior 1	Sul	5
JAPURA	PR	Interior 1	Sul	5
JARDIM ALEGRE	PR	Interior 1	Sul	5
JARDIM OLINDA	PR	Interior 1	Sul	5
JATAIZINHO	PR	Interior 1	Sul	5
JESUITAS	PR	Interior 1	Sul	5
JOAQUIM TAVORA	PR	Interior 1	Sul	5
JUNDIAI DO SUL	PR	Interior 1	Sul	5
JURANDA	PR	Interior 1	Sul	5
JUSSARA	PR	Interior 1	Sul	5
KALORE	PR	Interior 1	Sul	5
LAPA	PR	Interior 1	Sul	5
LARANJAL	PR	Interior 1	Sul	5
LARANJEIRAS DO SUL	PR	Interior 1	Sul	5
LEOPOLIS	PR	Interior 1	Sul	5
LIDIANOPOLIS	PR	Interior 1	Sul	5
LINDOESTE	PR	Interior 1	Sul	5
LOANDA	PR	Interior 1	Sul	5
LOBATO	PR	Interior 1	Sul	5
LONDRINA	PR	Interior 1	Sul	5
LUIZIANA	PR	Interior 1	Sul	5
LUNARDELLI	PR	Interior 1	Sul	5
LUPIONOPOLIS	PR	Interior 1	Sul	5
MALLET	PR	Interior 1	Sul	5
MAMBORE	PR	Interior 1	Sul	5
MANDAGUACU	PR	Interior 1	Sul	5
MANDAGUARI	PR	Interior 1	Sul	5
MANDIRITUBA	PR	Interior 1	Sul	5
MANFRINOPOLIS	PR	Interior 1	Sul	5
MANGUEIRINHA	PR	Interior 1	Sul	5
MANOEL RIBAS	PR	Interior 1	Sul	5
MARECHAL CANDIDO RONDON	PR	Interior 1	Sul	5
MARIA HELENA	PR	Interior 1	Sul	5
MARIALVA	PR	Interior 1	Sul	5
MARILANDIA DO SUL	PR	Interior 1	Sul	5
MARILENA	PR	Interior 1	Sul	5
MARILUZ	PR	Interior 1	Sul	5
MARINGA	PR	Capital	Sul	2
MARIOPOLIS	PR	Interior 1	Sul	5
MARIPA	PR	Interior 1	Sul	5
MARMELEIRO	PR	Interior 1	Sul	5
MARQUINHO	PR	Interior 1	Sul	5
MARUMBI	PR	Interior 1	Sul	5
MATELANDIA	PR	Interior 1	Sul	5
MATINHOS	PR	Interior 1	Sul	5
MATO RICO	PR	Interior 1	Sul	5
MAUA DA SERRA	PR	Interior 1	Sul	5
MEDIANEIRA	PR	Interior 1	Sul	5
MERCEDES	PR	Interior 1	Sul	5
MIRADOR	PR	Interior 1	Sul	5
MIRASELVA	PR	Interior 1	Sul	5
MISSAL	PR	Interior 1	Sul	5
MOREIRA SALES	PR	Interior 1	Sul	5
MORRETES	PR	Interior 1	Sul	5
MUNHOZ DE MELO	PR	Interior 1	Sul	5
NOSSA SENHORA DAS GRACAS	PR	Interior 1	Sul	5
NOVA ALIANCA DO IVAI	PR	Interior 1	Sul	5
NOVA AMERICA DA COLINA	PR	Interior 1	Sul	5
NOVA AURORA	PR	Interior 1	Sul	5
NOVA CANTU	PR	Interior 1	Sul	5
NOVA ESPERANCA	PR	Interior 1	Sul	5
NOVA ESPERANCA DO SUDOESTE	PR	Interior 1	Sul	5
NOVA FATIMA	PR	Interior 1	Sul	5
NOVA LARANJEIRAS	PR	Interior 1	Sul	5
NOVA LONDRINA	PR	Interior 1	Sul	5
NOVA OLIMPIA	PR	Interior 1	Sul	5
NOVA PRATA DO IGUACU	PR	Interior 1	Sul	5
NOVA SANTA BARBARA	PR	Interior 1	Sul	5
NOVA SANTA ROSA	PR	Interior 1	Sul	5
NOVA TEBAS	PR	Interior 1	Sul	5
NOVO ITACOLOMI	PR	Interior 1	Sul	5
ORTIGUEIRA	PR	Interior 1	Sul	5
OURIZONA	PR	Interior 1	Sul	5
OURO VERDE DO OESTE	PR	Interior 1	Sul	5
PAICANDU	PR	Interior 1	Sul	5
PALMAS	PR	Interior 1	Sul	5
PALMEIRA	PR	Interior 1	Sul	5
PALMITAL	PR	Interior 1	Sul	5
PALOTINA	PR	Interior 1	Sul	5
PARAISO DO NORTE	PR	Interior 1	Sul	5
PARANACITY	PR	Interior 1	Sul	5
PARANAGUA	PR	Interior 1	Sul	5
PARANAPOEMA	PR	Interior 1	Sul	5
PARANAVAI	PR	Interior 1	Sul	5
PATO BRAGADO	PR	Interior 1	Sul	5
PATO BRANCO	PR	Interior 1	Sul	5
PAULA FREITAS	PR	Interior 1	Sul	5
PAULO FRONTIN	PR	Interior 1	Sul	5
PEABIRU	PR	Interior 1	Sul	5
PEROBAL	PR	Interior 1	Sul	5
PEROLA	PR	Interior 1	Sul	5
PEROLA D OESTE	PR	Interior 1	Sul	5
PIEN	PR	Interior 1	Sul	5
PINHAIS	PR	Capital	Sul	2
PINHAL DE SAO BENTO	PR	Interior 1	Sul	5
PINHALAO	PR	Interior 1	Sul	5
PINHAO	PR	Interior 1	Sul	5
PIRAI DO SUL	PR	Interior 1	Sul	5
PIRAQUARA	PR	Interior 1	Sul	5
PITANGA	PR	Interior 1	Sul	5
PITANGUEIRAS	PR	Interior 1	Sul	5
PLANALTINA DO PARANA	PR	Interior 1	Sul	5
PLANALTO	PR	Interior 1	Sul	5
PONTA GROSSA	PR	Interior 1	Sul	5
PONTAL DO PARANA	PR	Interior 1	Sul	5
PORECATU	PR	Interior 1	Sul	5
PORTO AMAZONAS	PR	Interior 1	Sul	5
PORTO BARREIRO	PR	Interior 1	Sul	5
PORTO RICO	PR	Interior 1	Sul	5
PORTO VITORIA	PR	Interior 1	Sul	5
PRADO FERREIRA	PR	Interior 1	Sul	5
PRANCHITA	PR	Interior 1	Sul	5
PRESIDENTE CASTELO BRANCO	PR	Interior 1	Sul	5
PRIMEIRO DE MAIO	PR	Interior 1	Sul	5
PRUDENTOPOLIS	PR	Interior 1	Sul	5
QUARTO CENTENARIO	PR	Interior 1	Sul	5
QUATIGUA	PR	Interior 1	Sul	5
QUATRO BARRAS	PR	Interior 1	Sul	5
QUATRO PONTES	PR	Interior 1	Sul	5
QUEDAS DO IGUACU	PR	Interior 1	Sul	5
QUERENCIA DO NORTE	PR	Interior 1	Sul	5
QUINTA DO SOL	PR	Interior 1	Sul	5
QUITANDINHA	PR	Interior 1	Sul	5
RAMILANDIA	PR	Interior 1	Sul	5
RANCHO ALEGRE	PR	Interior 1	Sul	5
RANCHO ALEGRE D OESTE	PR	Interior 1	Sul	5
REALEZA	PR	Interior 1	Sul	5
REBOUCAS	PR	Interior 1	Sul	5
RENASCENCA	PR	Interior 1	Sul	5
RESERVA	PR	Interior 1	Sul	5
RESERVA DO IGUACU	PR	Interior 1	Sul	5
RIBEIRAO CLARO	PR	Interior 1	Sul	5
RIBEIRAO DO PINHAL	PR	Interior 1	Sul	5
RIO AZUL	PR	Interior 1	Sul	5
RIO BOM	PR	Interior 1	Sul	5
RIO BONITO DO IGUACU	PR	Interior 1	Sul	5
RIO BRANCO DO IVAI	PR	Interior 1	Sul	5
RIO BRANCO DO SUL	PR	Interior 1	Sul	5
RIO NEGRO	PR	Interior 1	Sul	5
ROLANDIA	PR	Interior 1	Sul	5
RONCADOR	PR	Interior 1	Sul	5
RONDON	PR	Interior 1	Sul	5
ROSARIO DO IVAI	PR	Interior 1	Sul	5
SABAUDIA	PR	Interior 1	Sul	5
SALGADO FILHO	PR	Interior 1	Sul	5
SALTO DO ITARARE	PR	Interior 1	Sul	5
SALTO DO LONTRA	PR	Interior 1	Sul	5
SANTA AMELIA	PR	Interior 1	Sul	5
SANTA CECILIA DO PAVAO	PR	Interior 1	Sul	5
SANTA CRUZ DE MONTE CASTELO	PR	Interior 1	Sul	5
SANTA FE	PR	Interior 1	Sul	5
SANTA HELENA	PR	Interior 1	Sul	5
SANTA INES	PR	Interior 1	Sul	5
SANTA ISABEL DO IVAI	PR	Interior 1	Sul	5
SANTA IZABEL DO OESTE	PR	Interior 1	Sul	5
SANTA LUCIA	PR	Interior 1	Sul	5
SANTA MARIA DO OESTE	PR	Interior 1	Sul	5
SANTA MARIANA	PR	Interior 1	Sul	5
SANTA MONICA	PR	Interior 1	Sul	5
SANTA TEREZA DO OESTE	PR	Interior 1	Sul	5
SANTA TEREZINHA DE ITAIPU	PR	Interior 1	Sul	5
SANTANA DO ITARARE	PR	Interior 1	Sul	5
SANTO ANTONIO DA PLATINA	PR	Interior 1	Sul	5
SANTO ANTONIO DO CAIUA	PR	Interior 1	Sul	5
SANTO ANTONIO DO PARAISO	PR	Interior 1	Sul	5
SANTO ANTONIO DO SUDOESTE	PR	Interior 1	Sul	5
SANTO INACIO	PR	Interior 1	Sul	5
SAO CARLOS DO IVAI	PR	Interior 1	Sul	5
SAO JERONIMO DA SERRA	PR	Interior 1	Sul	5
SAO JOAO	PR	Interior 1	Sul	5
SAO JOAO DO CAIUA	PR	Interior 1	Sul	5
SAO JOAO DO IVAI	PR	Interior 1	Sul	5
SAO JOAO DO TRIUNFO	PR	Interior 1	Sul	5
SAO JORGE DO IVAI	PR	Interior 1	Sul	5
SAO JORGE DO PATROCINIO	PR	Interior 1	Sul	5
SAO JORGE D OESTE	PR	Interior 1	Sul	5
SAO JOSE DA BOA VISTA	PR	Interior 1	Sul	5
SAO JOSE DAS PALMEIRAS	PR	Interior 1	Sul	5
SAO JOSE DOS PINHAIS	PR	Capital	Sul	2
SAO MANOEL DO PARANA	PR	Interior 1	Sul	5
SAO MATEUS DO SUL	PR	Interior 1	Sul	5
SAO MIGUEL DO IGUACU	PR	Interior 1	Sul	5
SAO PEDRO DO IGUACU	PR	Interior 1	Sul	5
SAO PEDRO DO IVAI	PR	Interior 1	Sul	5
SAO PEDRO DO PARANA	PR	Interior 1	Sul	5
SAO SEBASTIAO DA AMOREIRA	PR	Interior 1	Sul	5
SAO TOME	PR	Interior 1	Sul	5
SAPOPEMA	PR	Interior 1	Sul	5
SARANDI	PR	Interior 1	Sul	5
SAUDADE DO IGUACU	PR	Interior 1	Sul	5
SENGES	PR	Interior 1	Sul	5
SERRANOPOLIS DO IGUACU	PR	Interior 1	Sul	5
SERTANEJA	PR	Interior 1	Sul	5
SERTANOPOLIS	PR	Interior 1	Sul	5
SIQUEIRA CAMPOS	PR	Interior 1	Sul	5
SULINA	PR	Interior 1	Sul	5
TAMARANA	PR	Interior 1	Sul	5
TAMBOARA	PR	Interior 1	Sul	5
TAPEJARA	PR	Interior 1	Sul	5
TAPIRA	PR	Interior 1	Sul	5
TEIXEIRA SOARES	PR	Interior 1	Sul	5
TELEMACO BORBA	PR	Interior 1	Sul	5
TERRA BOA	PR	Interior 1	Sul	5
TERRA RICA	PR	Interior 1	Sul	5
TERRA ROXA	PR	Interior 1	Sul	5
TIBAGI	PR	Interior 1	Sul	5
TIJUCAS DO SUL	PR	Interior 1	Sul	5
TOLEDO	PR	Interior 1	Sul	5
TOMAZINA	PR	Interior 1	Sul	5
TRES BARRAS DO PARANA	PR	Interior 1	Sul	5
TUNAS DO PARANA	PR	Interior 1	Sul	5
TUNEIRAS DO OESTE	PR	Interior 1	Sul	5
TUPASSI	PR	Interior 1	Sul	5
TURVO	PR	Interior 1	Sul	5
UBIRATA	PR	Interior 1	Sul	5
UMUARAMA	PR	Interior 1	Sul	5
UNIAO DA VITORIA	PR	Interior 1	Sul	5
UNIFLOR	PR	Interior 1	Sul	5
URAI	PR	Interior 1	Sul	5
VENTANIA	PR	Interior 1	Sul	5
VERA CRUZ DO OESTE	PR	Interior 1	Sul	5
VERE	PR	Interior 1	Sul	5
VIRMOND	PR	Interior 1	Sul	5
VITORINO	PR	Interior 1	Sul	5
WENCESLAU BRAZ	PR	Interior 1	Sul	5
XAMBRE	PR	Interior 1	Sul	5
ANGRA DOS REIS	RJ	Interior 1	Sudeste	4
APERIBE	RJ	Interior 1	Sudeste	4
ARARUAMA	RJ	Interior 1	Sudeste	4
AREAL	RJ	Interior 1	Sudeste	4
ARMACAO DOS BUZIOS	RJ	Interior 1	Sudeste	4
ARRAIAL DO CABO	RJ	Interior 1	Sudeste	4
BARRA DO PIRAI	RJ	Interior 1	Sudeste	4
BARRA MANSA	RJ	Interior 1	Sudeste	4
BELFORD ROXO	RJ	Interior 1	Sudeste	4
BOM JARDIM	RJ	Interior 1	Sudeste	4
BOM JESUS DO ITABAPOANA	RJ	Interior 1	Sudeste	4
CABO FRIO	RJ	Interior 1	Sudeste	4
CACHOEIRAS DE MACACU	RJ	Interior 1	Sudeste	4
CAMBUCI	RJ	Interior 1	Sudeste	4
CAMPOS DOS GOYTACAZES	RJ	Interior 1	Sudeste	4
CANTAGALO	RJ	Interior 1	Sudeste	4
CARAPEBUS	RJ	Interior 1	Sudeste	4
CARDOSO MOREIRA	RJ	Interior 1	Sudeste	4
CARMO	RJ	Interior 1	Sudeste	4
CASIMIRO DE ABREU	RJ	Interior 1	Sudeste	4
COMENDADOR LEVY GASPARIAN	RJ	Interior 1	Sudeste	4
CONCEICAO DE MACABU	RJ	Interior 1	Sudeste	4
CORDEIRO	RJ	Interior 1	Sudeste	4
DUAS BARRAS	RJ	Interior 1	Sudeste	4
DUQUE DE CAXIAS	RJ	Interior 1	Sudeste	4
ENGENHEIRO PAULO DE FRONTIN	RJ	Interior 1	Sudeste	4
GUAPIMIRIM	RJ	Interior 1	Sudeste	4
IGUABA GRANDE	RJ	Interior 1	Sudeste	4
ITABORAI	RJ	Interior 1	Sudeste	4
ITAGUAI	RJ	Interior 1	Sudeste	4
ITALVA	RJ	Interior 1	Sudeste	4
ITAOCARA	RJ	Interior 1	Sudeste	4
ITAPERUNA	RJ	Interior 1	Sudeste	4
ITATIAIA	RJ	Interior 1	Sudeste	4
JAPERI	RJ	Interior 1	Sudeste	4
LAJE DO MURIAE	RJ	Interior 1	Sudeste	4
MACAE	RJ	Interior 1	Sudeste	4
MACUCO	RJ	Interior 1	Sudeste	4
MAGE	RJ	Interior 1	Sudeste	4
MANGARATIBA	RJ	Interior 1	Sudeste	4
MARICA	RJ	Interior 1	Sudeste	4
MENDES	RJ	Interior 1	Sudeste	4
MESQUITA	RJ	Interior 1	Sudeste	4
MIGUEL PEREIRA	RJ	Interior 1	Sudeste	4
MIRACEMA	RJ	Interior 1	Sudeste	4
NATIVIDADE	RJ	Interior 1	Sudeste	4
NILÓPOLIS	RJ	Interior 1	Sudeste	4
NITEROI	RJ	Interior 1	Sudeste	4
NOVA FRIBURGO	RJ	Interior 1	Sudeste	4
NOVA IGUACU	RJ	Interior 1	Sudeste	4
PARACAMBI	RJ	Interior 1	Sudeste	4
PARAIBA DO SUL	RJ	Interior 1	Sudeste	4
PARATI	RJ	Interior 1	Sudeste	4
PATY DO ALFERES	RJ	Interior 1	Sudeste	4
PETROPOLIS	RJ	Interior 1	Sudeste	4
PINHEIRAL	RJ	Interior 1	Sudeste	4
PIRAI	RJ	Interior 1	Sudeste	4
PORCIÚNCULA	RJ	Interior 1	Sudeste	4
PORTO REAL	RJ	Interior 1	Sudeste	4
QUATIS	RJ	Interior 1	Sudeste	4
QUEIMADOS	RJ	Interior 1	Sudeste	4
QUISSAMA	RJ	Interior 1	Sudeste	4
RESENDE	RJ	Interior 1	Sudeste	4
RIO BONITO	RJ	Interior 1	Sudeste	4
RIO CLARO	RJ	Interior 1	Sudeste	4
RIO DAS FLORES	RJ	Interior 1	Sudeste	4
RIO DAS OSTRAS	RJ	Interior 1	Sudeste	4
RIO DE JANEIRO	RJ	Capital	Sudeste	2
SANTA MARIA MADALENA	RJ	Interior 1	Sudeste	4
SANTO ANTONIO DE PADUA	RJ	Interior 1	Sudeste	4
SAO FIDELIS	RJ	Interior 1	Sudeste	4
SAO FRANCISCO DE ITABAPOANA	RJ	Interior 1	Sudeste	4
SAO GONCALO	RJ	Interior 1	Sudeste	4
SAO JOAO DA BARRA	RJ	Interior 1	Sudeste	4
SAO JOAO DE MERITI	RJ	Interior 1	Sudeste	4
SAO JOSE DE UBA	RJ	Interior 1	Sudeste	4
SAO JOSE DO VALE DO RIO PRETO	RJ	Interior 1	Sudeste	4
SAO PEDRO DA ALDEIA	RJ	Interior 1	Sudeste	4
SAO SEBASTIAO DO ALTO	RJ	Interior 1	Sudeste	4
SAPUCAIA	RJ	Interior 1	Sudeste	4
SAQUAREMA	RJ	Interior 1	Sudeste	4
SEROPEDICA	RJ	Interior 1	Sudeste	4
SILVA JARDIM	RJ	Interior 1	Sudeste	4
SUMIDOURO	RJ	Interior 1	Sudeste	4
TANGUA	RJ	Interior 1	Sudeste	4
TERESOPOLIS	RJ	Interior 1	Sudeste	4
TRAJANO DE MORAIS	RJ	Interior 1	Sudeste	4
TRES RIOS	RJ	Interior 1	Sudeste	4
VALENCA	RJ	Interior 1	Sudeste	4
VARRE-SAI	RJ	Interior 1	Sudeste	4
VASSOURAS	RJ	Interior 1	Sudeste	4
VOLTA REDONDA	RJ	Interior 1	Sudeste	4
ACARI	RN	Interior 1	Nordeste	10
ASSU	RN	Interior 1	Nordeste	10
AFONSO BEZERRA	RN	Interior 1	Nordeste	10
AGUA NOVA	RN	Interior 1	Nordeste	10
ALEXANDRIA	RN	Interior 2	Nordeste	10
ALMINO AFONSO	RN	Interior 2	Nordeste	10
ALTO DO RODRIGUES	RN	Interior 2	Nordeste	10
ANGICOS	RN	Interior 1	Nordeste	10
ANTONIO MARTINS	RN	Interior 2	Nordeste	10
APODI	RN	Interior 1	Nordeste	10
AREIA BRANCA	RN	Interior 2	Nordeste	10
ARÊS	RN	Interior 1	Nordeste	10
AUGUSTO SEVERO	RN	Interior 2	Nordeste	10
BAIA FORMOSA	RN	Interior 1	Nordeste	10
BARAUNA	RN	Interior 1	Nordeste	10
BARCELONA	RN	Interior 1	Nordeste	10
BENTO FERNANDES	RN	Interior 1	Nordeste	10
BOA SAUDE	RN	Interior 1	Nordeste	10
BODÓ	RN	Sob Consulta	Nordeste	Sob Consulta
BOM JESUS	RN	Interior 1	Nordeste	10
BREJINHO	RN	Interior 1	Nordeste	10
CAIÇARA DO NORTE	RN	Interior 2	Nordeste	10
CAIÇARA RIO DOS VENTOS	RN	Interior 1	Nordeste	10
CAICÓ	RN	Interior 1	Nordeste	10
CAMPO REDONDO	RN	Interior 1	Nordeste	10
CANGUARETAMA	RN	Interior 1	Nordeste	10
CARAUBAS	RN	Interior 2	Nordeste	10
CARNAUBA DOS DANTAS	RN	Interior 2	Nordeste	10
CARNAUBAIS	RN	Interior 2	Nordeste	10
CEARA-MIRIM	RN	Interior 1	Nordeste	10
CERRO CORA	RN	Sob Consulta	Nordeste	Sob Consulta
CORONEL EZEQUIEL	RN	Interior 2	Nordeste	10
CORONEL JOAO PESSOA	RN	Interior 2	Nordeste	10
CRUZETA	RN	Interior 2	Nordeste	10
CURRAIS NOVOS	RN	Interior 1	Nordeste	10
DOUTOR SEVERIANO	RN	Sob Consulta	Nordeste	Sob Consulta
ENCANTO	RN	Sob Consulta	Nordeste	Sob Consulta
EQUADOR	RN	Interior 2	Nordeste	10
ESPIRITO SANTO	RN	Interior 2	Nordeste	10
EXTREMOZ	RN	Interior 1	Nordeste	10
FELIPE GUERRA	RN	Interior 1	Nordeste	10
FERNANDO PEDROZA	RN	Interior 2	Nordeste	10
FLORANIA	RN	Interior 2	Nordeste	10
FRANCISCO DANTAS	RN	Interior 2	Nordeste	10
FRUTUOSO GOMES	RN	Interior 2	Nordeste	10
GALINHOS	RN	Sob Consulta	Nordeste	Sob Consulta
GOIANINHA	RN	Interior 1	Nordeste	10
GOV. DIX SEPET ROSADO	RN	Interior 2	Nordeste	10
GROSSOS	RN	Interior 2	Nordeste	10
GUAMARÉ	RN	Sob Consulta	Nordeste	Sob Consulta
IELMO MARINHO	RN	Interior 2	Nordeste	10
IPANGUAÇU	RN	Interior 2	Nordeste	10
IPUEIRA	RN	Interior 2	Nordeste	10
ITAJÁ	RN	Interior 2	Nordeste	10
ITAÚ	RN	Interior 2	Nordeste	10
JAÇANA	RN	Interior 2	Nordeste	10
JANDAIRA	RN	Interior 2	Nordeste	10
JANDUIS	RN	Interior 2	Nordeste	10
JANUARIO CICCO	RN	Interior 1	Nordeste	10
JAPI	RN	Interior 2	Nordeste	10
JARDIM DE ANGICOS	RN	Interior 2	Nordeste	10
JARDIM DE PIRANHAS	RN	Interior 2	Nordeste	10
JARDIM DO SERIDO	RN	Interior 1	Nordeste	10
JOÃO CAMARA	RN	Interior 1	Nordeste	10
JOÃO DIAS	RN	Interior 2	Nordeste	10
JOSE DA PENHA	RN	Interior 2	Nordeste	10
JUCURUTU	RN	Interior 2	Nordeste	10
JUNDIÁ	RN	Interior 2	Nordeste	10
LAGOA D ANTA	RN	Interior 2	Nordeste	10
LAGOA DE PEDRAS	RN	Interior 2	Nordeste	10
LAGOA DE VELHOS	RN	Interior 2	Nordeste	10
LAGOA NOVA	RN	Interior 2	Nordeste	10
LAGOA SALGADA	RN	Interior 2	Nordeste	10
LAJES	RN	Interior 1	Nordeste	10
LAJES PINTADAS	RN	Interior 2	Nordeste	10
LUCRECIA	RN	Interior 2	Nordeste	10
LUIS GOMES	RN	Interior 2	Nordeste	10
MACAIBA	RN	Interior 1	Nordeste	10
MACAU	RN	Interior 2	Nordeste	10
MAJOR SALES	RN	Sob Consulta	Nordeste	Sob Consulta
MARCELINO VIEIRA	RN	Interior 1	Nordeste	10
MARTINS	RN	Interior 2	Nordeste	10
MAXARANGUAPE	RN	Interior 2	Nordeste	10
MESSIAS TARGINO	RN	Interior 2	Nordeste	10
MONTANHAS	RN	Interior 1	Nordeste	10
MONTE ALEGRE	RN	Interior 1	Nordeste	10
MONTE DAS GAMELEIRAS	RN	Interior 1	Nordeste	10
MOSSORÓ	RN	Interior 1	Nordeste	10
NATAL	RN	Capital	Nordeste	8
NISIA FLORESTA	RN	Interior 1	Nordeste	10
NOVA CRUZ	RN	Interior 1	Nordeste	10
OLHO D AGUA DO BORGES	RN	Interior 2	Nordeste	10
OURO BRANCO	RN	Interior 2	Nordeste	10
PARANA	RN	Interior 2	Nordeste	10
PARAÚ	RN	Interior 2	Nordeste	10
PARAZINHO	RN	Sob Consulta	Nordeste	Sob Consulta
PARELHAS	RN	Interior 1	Nordeste	10
PARNAMIRIM	RN	Interior 1	Nordeste	10
PASSA E FICA	RN	Interior 2	Nordeste	10
PASSAGEM	RN	Interior 2	Nordeste	10
PATU	RN	Interior 2	Nordeste	10
PAU DOS FERROS	RN	Interior 2	Nordeste	10
PEDRA GRANDE	RN	Sob Consulta	Nordeste	Sob Consulta
PEDRA PRETA	RN	Sob Consulta	Nordeste	Sob Consulta
PEDRO AVELINO	RN	Interior 2	Nordeste	10
PEDRO VELHO	RN	Interior 1	Nordeste	10
PENDENCIAS	RN	Interior 2	Nordeste	10
PILÕES	RN	Sob Consulta	Nordeste	Sob Consulta
POÇO BRANCO	RN	Sob Consulta	Nordeste	Sob Consulta
PORTALEGRE	RN	Interior 2	Nordeste	10
PORTO DO MANGUE	RN	Interior 2	Nordeste	10
PUREZA	RN	Interior 2	Nordeste	10
RAFAEL FERNANDES	RN	Interior 2	Nordeste	10
RAFAEL GODEIRO	RN	Interior 2	Nordeste	10
RIACHO DA CRUZ	RN	Interior 2	Nordeste	10
RIACHO DE SANTANA	RN	Interior 2	Nordeste	10
RIACHUELO	RN	Interior 1	Nordeste	10
RIO DO FOGO	RN	Sob Consulta	Nordeste	Sob Consulta
RODOLFO FERNANDES	RN	Interior 2	Nordeste	10
RUY BARBOSA	RN	Interior 2	Nordeste	10
SANTA CRUZ	RN	Interior 1	Nordeste	10
SANTA MARIA	RN	Interior 1	Nordeste	10
SANTANA DO MATOS	RN	Interior 2	Nordeste	10
SANTANA DO SERIDÓ	RN	Interior 2	Nordeste	10
SANTO ANTONIO	RN	Interior 2	Nordeste	10
SÃO BENTO DO NORTE	RN	Sob Consulta	Nordeste	Sob Consulta
SÃO BENTO DO TRAIRI	RN	Sob Consulta	Nordeste	Sob Consulta
SÃO FERNANDO	RN	Interior 2	Nordeste	10
SÃO FRANCISCO DO OESTE	RN	Sob Consulta	Nordeste	Sob Consulta
SÃO GONÇALO DO AMARANTE	RN	Interior 1	Nordeste	10
SÃO JOÃO DO SABUGI	RN	Interior 2	Nordeste	10
SÃO JOSE DE MIPIBU	RN	Interior 1	Nordeste	10
SÃO JOSE DO CAMPESTRE	RN	Interior 2	Nordeste	10
SÃO JOSE DO SERIDO	RN	Interior 1	Nordeste	10
SÃO MIGUEL	RN	Interior 2	Nordeste	10
SÃO MIGUEL DO GOSTOSO	RN	Sob Consulta	Nordeste	Sob Consulta
SÃO PAULO DO POTENGI	RN	Interior 1	Nordeste	10
SÃO PEDRO	RN	Interior 2	Nordeste	10
SÃO RAFAEL	RN	Interior 2	Nordeste	10
SÃO TOMÉ	RN	Sob Consulta	Nordeste	Sob Consulta
SÃO VICENTE	RN	Interior 2	Nordeste	10
SENADOR ELOI DE SOUZA	RN	Interior 2	Nordeste	10
SENADOR GEORGINO AVELINO	RN	Interior 2	Nordeste	10
SERRA CAIADA	RN	Interior 2	Nordeste	10
SERRA DE SÃO BENTO	RN	Interior 2	Nordeste	10
SERRA DO MEL	RN	Sob Consulta	Nordeste	Sob Consulta
SERRA NEGRA DO NORTE	RN	Sob Consulta	Nordeste	Sob Consulta
SERRINHA	RN	Interior 2	Nordeste	10
SERRINHA DOS PINTOS	RN	Sob Consulta	Nordeste	Sob Consulta
SEVERIANO MELO	RN	Interior 2	Nordeste	10
SITIO NOVO	RN	Interior 2	Nordeste	10
TABOLEIRO GRANDE	RN	Sob Consulta	Nordeste	Sob Consulta
TAIPU	RN	Interior 2	Nordeste	10
TANGARÁ	RN	Interior 2	Nordeste	10
TENENTE ANANIAS	RN	Interior 2	Nordeste	10
TENENTE LAURENTINO CRUZ	RN	Interior 2	Nordeste	10
TIBAU	RN	Interior 2	Nordeste	10
TIBAU DO SUL	RN	Interior 1	Nordeste	10
TIMBAUBÁ DOS BATISTAS	RN	Sob Consulta	Nordeste	Sob Consulta
TOUROS	RN	Interior 2	Nordeste	10
TRIUNFO POTIGUAR	RN	Interior 2	Nordeste	10
UMARIZAL	RN	Interior 2	Nordeste	10
UPANEMA	RN	Interior 2	Nordeste	10
VARZEÁ	RN	Interior 2	Nordeste	10
VENHA-VER	RN	Sob Consulta	Nordeste	Sob Consulta
VERA CRUZ	RN	Interior 2	Nordeste	10
VIÇOSA	RN	Sob Consulta	Nordeste	Sob Consulta
VILA FLOR	RN	Interior 2	Nordeste	10
ACEGUA	RS	Interior 1	Sul	5
AGUA SANTA	RS	Interior 1	Sul	5
AGUDO	RS	Interior 1	Sul	5
AJURICABA	RS	Interior 1	Sul	5
ALECRIM	RS	Interior 1	Sul	5
ALEGRETE	RS	Interior 1	Sul	5
ALEGRIA	RS	Interior 1	Sul	5
ALMIRANTE TAMANDARE DO SUL	RS	Interior 1	Sul	5
ALPESTRE	RS	Interior 1	Sul	5
ALTO ALEGRE	RS	Interior 1	Sul	5
ALTO FELIZ	RS	Interior 1	Sul	5
ALVORADA	RS	Capital	Sul	2
AMARAL FERRADOR	RS	Interior 1	Sul	5
AMETISTA DO SUL	RS	Interior 1	Sul	5
ANDRE DA ROCHA	RS	Interior 1	Sul	5
ANTA GORDA	RS	Interior 1	Sul	5
ANTONIO PRADO	RS	Interior 1	Sul	5
ARAMBARE	RS	Interior 1	Sul	5
ARARICA	RS	Interior 1	Sul	5
ARATIBA	RS	Interior 1	Sul	5
ARROIO DO MEIO	RS	Interior 1	Sul	5
ARROIO DO PADRE	RS	Interior 1	Sul	5
ARROIO DO SAL	RS	Interior 1	Sul	5
ARROIO DO TIGRE	RS	Interior 1	Sul	5
ARROIO DOS RATOS	RS	Interior 1	Sul	5
ARROIO GRANDE	RS	Interior 1	Sul	5
ARVOREZINHA	RS	Interior 1	Sul	5
AUGUSTO PESTANA	RS	Interior 1	Sul	5
AUREA	RS	Interior 1	Sul	5
BAGE	RS	Interior 1	Sul	5
BALNEARIO PINHAL	RS	Interior 1	Sul	5
BARAO	RS	Interior 1	Sul	5
BARAO DE COTEGIPE	RS	Interior 1	Sul	5
BARAO DO TRIUNFO	RS	Interior 1	Sul	5
BARRA DO GUARITA	RS	Interior 1	Sul	5
BARRA DO QUARAI	RS	Interior 1	Sul	5
BARRA DO RIBEIRO	RS	Interior 1	Sul	5
BARRA DO RIO AZUL	RS	Interior 1	Sul	5
BARRA FUNDA	RS	Interior 1	Sul	5
BARRACAO	RS	Interior 1	Sul	5
BARROS CASSAL	RS	Interior 1	Sul	5
BENJAMIN CONSTANT DO SUL	RS	Interior 1	Sul	5
BENTO GONCALVES	RS	Interior 1	Sul	5
BOA VISTA DAS MISSOES	RS	Interior 1	Sul	5
BOA VISTA DO BURICA	RS	Interior 1	Sul	5
BOA VISTA DO CADEADO	RS	Interior 1	Sul	5
BOA VISTA DO INCRA	RS	Interior 1	Sul	5
BOA VISTA DO SUL	RS	Interior 1	Sul	5
BOM JESUS	RS	Interior 1	Sul	5
BOM PRINCIPIO	RS	Interior 1	Sul	5
BOM PROGRESSO	RS	Interior 1	Sul	5
BOM RETIRO DO SUL	RS	Interior 1	Sul	5
BOQUEIRAO DO LEAO	RS	Interior 1	Sul	5
BOSSOROCA	RS	Interior 1	Sul	5
BOZANO	RS	Interior 1	Sul	5
BRAGA	RS	Interior 1	Sul	5
BROCHIER	RS	Interior 1	Sul	5
BUTIA	RS	Interior 1	Sul	5
CACAPAVA DO SUL	RS	Interior 1	Sul	5
CACEQUI	RS	Interior 1	Sul	5
CACHOEIRA DO SUL	RS	Interior 1	Sul	5
CACHOEIRINHA	RS	Capital	Sul	2
CACIQUE DOBLE	RS	Interior 1	Sul	5
CAIBATE	RS	Interior 1	Sul	5
CAICARA	RS	Interior 1	Sul	5
CAMAQUA	RS	Interior 1	Sul	5
CAMARGO	RS	Interior 1	Sul	5
CAMBARA DO SUL	RS	Interior 1	Sul	5
CAMPESTRE DA SERRA	RS	Interior 1	Sul	5
CAMPINA DAS MISSOES	RS	Interior 1	Sul	5
CAMPINAS DO SUL	RS	Interior 1	Sul	5
CAMPO BOM	RS	Interior 1	Sul	5
CAMPO NOVO	RS	Interior 1	Sul	5
CAMPOS BORGES	RS	Interior 1	Sul	5
CANDELARIA	RS	Interior 1	Sul	5
CANDIDO GODOI	RS	Interior 1	Sul	5
CANDIOTA	RS	Interior 1	Sul	5
CANELA	RS	Interior 1	Sul	5
CANGUCU	RS	Interior 1	Sul	5
CANOAS	RS	Capital	Sul	2
CANUDOS DO VALE	RS	Interior 1	Sul	5
CAPAO BONITO DO SUL	RS	Interior 1	Sul	5
CAPAO DA CANOA	RS	Interior 1	Sul	5
CAPAO DO CIPO	RS	Interior 1	Sul	5
CAPAO DO LEAO	RS	Interior 1	Sul	5
CAPELA DE SANTANA	RS	Interior 1	Sul	5
CAPITAO	RS	Interior 1	Sul	5
CAPIVARI DO SUL	RS	Interior 1	Sul	5
CARAA	RS	Interior 1	Sul	5
CARAZINHO	RS	Interior 1	Sul	5
CARLOS BARBOSA	RS	Interior 1	Sul	5
CARLOS GOMES	RS	Interior 1	Sul	5
CASCA	RS	Interior 1	Sul	5
CASEIROS	RS	Interior 1	Sul	5
CATUIPE	RS	Interior 1	Sul	5
CAXIAS DO SUL	RS	Interior 1	Sul	5
CENTENARIO	RS	Interior 1	Sul	5
CERRITO	RS	Interior 1	Sul	5
CERRO BRANCO	RS	Interior 1	Sul	5
CERRO GRANDE	RS	Interior 1	Sul	5
CERRO GRANDE DO SUL	RS	Interior 1	Sul	5
CERRO LARGO	RS	Interior 1	Sul	5
CHAPADA	RS	Interior 1	Sul	5
CHARQUEADAS	RS	Interior 1	Sul	5
CHARRUA	RS	Interior 1	Sul	5
CHIAPETTA	RS	Interior 1	Sul	5
CHUI	RS	Interior 1	Sul	5
CHUVISCA	RS	Interior 1	Sul	5
CIDREIRA	RS	Interior 1	Sul	5
CIRIACO	RS	Interior 1	Sul	5
COLINAS	RS	Interior 1	Sul	5
COLORADO	RS	Interior 1	Sul	5
CONDOR	RS	Interior 1	Sul	5
CONSTANTINA	RS	Interior 1	Sul	5
COQUEIRO BAIXO	RS	Interior 1	Sul	5
COQUEIROS DO SUL	RS	Interior 1	Sul	5
CORONEL BARROS	RS	Interior 1	Sul	5
CORONEL BICACO	RS	Interior 1	Sul	5
CORONEL PILAR	RS	Interior 1	Sul	5
COTIPORA	RS	Interior 1	Sul	5
COXILHA	RS	Interior 1	Sul	5
CRISSIUMAL	RS	Interior 1	Sul	5
CRISTAL	RS	Interior 1	Sul	5
CRISTAL DO SUL	RS	Interior 1	Sul	5
CRUZ ALTA	RS	Interior 1	Sul	5
CRUZALTENSE	RS	Interior 1	Sul	5
CRUZEIRO DO SUL	RS	Interior 1	Sul	5
DAVID CANABARRO	RS	Interior 1	Sul	5
DERRUBADAS	RS	Interior 1	Sul	5
DEZESSEIS DE NOVEMBRO	RS	Interior 1	Sul	5
DILERMANDO DE AGUIAR	RS	Interior 1	Sul	5
DOIS IRMAOS	RS	Interior 1	Sul	5
DOIS IRMAOS DAS MISSOES	RS	Interior 1	Sul	5
DOIS LAJEADOS	RS	Interior 1	Sul	5
DOM FELICIANO	RS	Interior 1	Sul	5
DOM PEDRITO	RS	Interior 1	Sul	5
DOM PEDRO DE ALCANTARA	RS	Interior 1	Sul	5
DONA FRANCISCA	RS	Interior 1	Sul	5
DOUTOR MAURICIO CARDOSO	RS	Interior 1	Sul	5
DOUTOR RICARDO	RS	Interior 1	Sul	5
ELDORADO DO SUL	RS	Interior 1	Sul	5
ENCANTADO	RS	Interior 1	Sul	5
ENCRUZILHADA DO SUL	RS	Interior 1	Sul	5
ENGENHO VELHO	RS	Interior 1	Sul	5
ENTRE RIOS DO SUL	RS	Interior 1	Sul	5
ENTRE-IJUIS	RS	Interior 1	Sul	5
EREBANGO	RS	Interior 1	Sul	5
ERECHIM	RS	Interior 1	Sul	5
ERNESTINA	RS	Interior 1	Sul	5
ERVAL GRANDE	RS	Interior 1	Sul	5
ERVAL SECO	RS	Interior 1	Sul	5
ESMERALDA	RS	Interior 1	Sul	5
ESPERANCA DO SUL	RS	Interior 1	Sul	5
ESPUMOSO	RS	Interior 1	Sul	5
ESTACAO	RS	Interior 1	Sul	5
ESTANCIA VELHA	RS	Interior 1	Sul	5
ESTEIO	RS	Capital	Sul	2
ESTRELA	RS	Interior 1	Sul	5
ESTRELA VELHA	RS	Interior 1	Sul	5
EUGENIO DE CASTRO	RS	Interior 1	Sul	5
FAGUNDES VARELA	RS	Interior 1	Sul	5
FARROUPILHA	RS	Interior 1	Sul	5
FAXINAL DO SOTURNO	RS	Interior 1	Sul	5
FAXINALZINHO	RS	Interior 1	Sul	5
FAZENDA VILANOVA	RS	Interior 1	Sul	5
FELIZ	RS	Interior 1	Sul	5
FLORES DA CUNHA	RS	Interior 1	Sul	5
FLORIANO PEIXOTO	RS	Interior 1	Sul	5
FONTOURA XAVIER	RS	Interior 1	Sul	5
FORMIGUEIRO	RS	Interior 1	Sul	5
FORQUETINHA	RS	Interior 1	Sul	5
FORTALEZA DOS VALOS	RS	Interior 1	Sul	5
FREDERICO WESTPHALEN	RS	Interior 1	Sul	5
GARIBALDI	RS	Interior 1	Sul	5
GARRUCHOS	RS	Interior 1	Sul	5
GAURAMA	RS	Interior 1	Sul	5
GENERAL CAMARA	RS	Interior 1	Sul	5
GENTIL	RS	Interior 1	Sul	5
GETULIO VARGAS	RS	Interior 1	Sul	5
GIRUA	RS	Interior 1	Sul	5
GLORINHA	RS	Interior 1	Sul	5
GRAMADO	RS	Interior 1	Sul	5
GRAMADO DOS LOUREIROS	RS	Interior 1	Sul	5
GRAMADO XAVIER	RS	Interior 1	Sul	5
GRAVATAI	RS	Capital	Sul	2
GUABIJU	RS	Interior 1	Sul	5
GUAIBA	RS	Interior 1	Sul	5
GUAPORE	RS	Interior 1	Sul	5
GUARANI DAS MISSOES	RS	Interior 1	Sul	5
HARMONIA	RS	Interior 1	Sul	5
HERVAL	RS	Interior 1	Sul	5
HERVEIRAS	RS	Interior 1	Sul	5
HORIZONTINA	RS	Interior 1	Sul	5
HULHA NEGRA	RS	Interior 1	Sul	5
HUMAITA	RS	Interior 1	Sul	5
IBARAMA	RS	Interior 1	Sul	5
IBIACA	RS	Interior 1	Sul	5
IBIRAIARAS	RS	Interior 1	Sul	5
IBIRAPUITA	RS	Interior 1	Sul	5
IBIRUBA	RS	Interior 1	Sul	5
IGREJINHA	RS	Interior 1	Sul	5
IJUI	RS	Interior 1	Sul	5
ILOPOLIS	RS	Interior 1	Sul	5
IMBE	RS	Interior 1	Sul	5
IMIGRANTE	RS	Interior 1	Sul	5
INDEPENDENCIA	RS	Interior 1	Sul	5
INHACORA	RS	Interior 1	Sul	5
IPE	RS	Interior 1	Sul	5
IPIRANGA DO SUL	RS	Interior 1	Sul	5
IRAI	RS	Interior 1	Sul	5
ITAARA	RS	Interior 1	Sul	5
ITACURUBI	RS	Interior 1	Sul	5
ITAPUCA	RS	Interior 1	Sul	5
ITAQUI	RS	Interior 1	Sul	5
ITATI	RS	Interior 1	Sul	5
ITATIBA DO SUL	RS	Interior 1	Sul	5
IVORA	RS	Interior 1	Sul	5
IVOTI	RS	Interior 1	Sul	5
JABOTICABA	RS	Interior 1	Sul	5
JACUIZINHO	RS	Interior 1	Sul	5
JACUTINGA	RS	Interior 1	Sul	5
JAGUARAO	RS	Interior 1	Sul	5
JAGUARI	RS	Interior 1	Sul	5
JAQUIRANA	RS	Interior 1	Sul	5
JARI	RS	Interior 1	Sul	5
JOIA	RS	Interior 1	Sul	5
JULIO DE CASTILHOS	RS	Interior 1	Sul	5
LAGOA BONITA DO SUL	RS	Interior 1	Sul	5
LAGOA DOS TRES CANTOS	RS	Interior 1	Sul	5
LAGOA VERMELHA	RS	Interior 1	Sul	5
LAGOAO	RS	Interior 1	Sul	5
LAJEADO	RS	Interior 1	Sul	5
LAJEADO DO BUGRE	RS	Interior 1	Sul	5
LAVRAS DO SUL	RS	Interior 1	Sul	5
LIBERATO SALZANO	RS	Interior 1	Sul	5
LINDOLFO COLLOR	RS	Interior 1	Sul	5
LINHA NOVA	RS	Interior 1	Sul	5
MACAMBARA	RS	Interior 1	Sul	5
MACHADINHO	RS	Interior 1	Sul	5
MAMPITUBA	RS	Interior 1	Sul	5
MANOEL VIANA	RS	Interior 1	Sul	5
MAQUINE	RS	Interior 1	Sul	5
MARATA	RS	Interior 1	Sul	5
MARAU	RS	Interior 1	Sul	5
MARCELINO RAMOS	RS	Interior 1	Sul	5
MARIANA PIMENTEL	RS	Interior 1	Sul	5
MARIANO MORO	RS	Interior 1	Sul	5
MARQUES DE SOUZA	RS	Interior 1	Sul	5
MATA	RS	Interior 1	Sul	5
MATO CASTELHANO	RS	Interior 1	Sul	5
MATO LEITAO	RS	Interior 1	Sul	5
MATO QUEIMADO	RS	Interior 1	Sul	5
MAXIMILIANO DE ALMEIDA	RS	Interior 1	Sul	5
MINAS DO LEAO	RS	Interior 1	Sul	5
MIRAGUAI	RS	Interior 1	Sul	5
MONTAURI	RS	Interior 1	Sul	5
MONTE ALEGRE DOS CAMPOS	RS	Interior 1	Sul	5
MONTE BELO DO SUL	RS	Interior 1	Sul	5
MONTENEGRO	RS	Interior 1	Sul	5
MORMACO	RS	Interior 1	Sul	5
MORRINHOS DO SUL	RS	Interior 1	Sul	5
MORRO REDONDO	RS	Interior 1	Sul	5
MORRO REUTER	RS	Interior 1	Sul	5
MOSTARDAS	RS	Interior 1	Sul	5
MUCUM	RS	Interior 1	Sul	5
MUITOS CAPOES	RS	Interior 1	Sul	5
MULITERNO	RS	Interior 1	Sul	5
NAO-ME-TOQUE	RS	Interior 1	Sul	5
NICOLAU VERGUEIRO	RS	Interior 1	Sul	5
NONOAI	RS	Interior 1	Sul	5
NOVA ALVORADA	RS	Interior 1	Sul	5
NOVA ARACA	RS	Interior 1	Sul	5
NOVA BASSANO	RS	Interior 1	Sul	5
NOVA BOA VISTA	RS	Interior 1	Sul	5
NOVA BRESCIA	RS	Interior 1	Sul	5
NOVA CANDELARIA	RS	Interior 1	Sul	5
NOVA ESPERANCA DO SUL	RS	Interior 1	Sul	5
NOVA HARTZ	RS	Interior 1	Sul	5
NOVA PADUA	RS	Interior 1	Sul	5
NOVA PALMA	RS	Interior 1	Sul	5
NOVA PETROPOLIS	RS	Interior 1	Sul	5
NOVA PRATA	RS	Interior 1	Sul	5
NOVA RAMADA	RS	Interior 1	Sul	5
NOVA ROMA DO SUL	RS	Interior 1	Sul	5
NOVA SANTA RITA	RS	Interior 1	Sul	5
NOVO BARREIRO	RS	Interior 1	Sul	5
NOVO CABRAIS	RS	Interior 1	Sul	5
NOVO HAMBURGO	RS	Capital	Sul	2
NOVO MACHADO	RS	Interior 1	Sul	5
NOVO TIRADENTES	RS	Interior 1	Sul	5
NOVO XINGU	RS	Interior 1	Sul	5
OSORIO	RS	Interior 1	Sul	5
PAIM FILHO	RS	Interior 1	Sul	5
PALMARES DO SUL	RS	Interior 1	Sul	5
PALMEIRA DAS MISSOES	RS	Interior 1	Sul	5
PALMITINHO	RS	Interior 1	Sul	5
PANAMBI	RS	Interior 1	Sul	5
PANTANO GRANDE	RS	Interior 1	Sul	5
PARAI	RS	Interior 1	Sul	5
PARAISO DO SUL	RS	Interior 1	Sul	5
PARECI NOVO	RS	Interior 1	Sul	5
PAROBE	RS	Interior 1	Sul	5
PASSA SETE	RS	Interior 1	Sul	5
PASSO DO SOBRADO	RS	Interior 1	Sul	5
PASSO FUNDO	RS	Interior 1	Sul	5
PAULO BENTO	RS	Interior 1	Sul	5
PAVERAMA	RS	Interior 1	Sul	5
PEDRAS ALTAS	RS	Interior 1	Sul	5
PEDRO OSORIO	RS	Interior 1	Sul	5
PEJUCARA	RS	Interior 1	Sul	5
PELOTAS	RS	Interior 1	Sul	5
PICADA CAFE	RS	Interior 1	Sul	5
PINHAL	RS	Interior 1	Sul	5
PINHAL DA SERRA	RS	Interior 1	Sul	5
PINHAL GRANDE	RS	Interior 1	Sul	5
PINHEIRINHO DO VALE	RS	Interior 1	Sul	5
PINHEIRO MACHADO	RS	Interior 1	Sul	5
PINTO BANDEIRA	RS	Interior 1	Sul	5
PIRAPO	RS	Interior 1	Sul	5
PIRATINI	RS	Interior 1	Sul	5
PLANALTO	RS	Interior 1	Sul	5
POCO DAS ANTAS	RS	Interior 1	Sul	5
PONTAO	RS	Interior 1	Sul	5
PONTE PRETA	RS	Interior 1	Sul	5
PORTAO	RS	Interior 1	Sul	5
PORTO ALEGRE	RS	Capital	Sul	2
PORTO LUCENA	RS	Interior 1	Sul	5
PORTO MAUA	RS	Interior 1	Sul	5
PORTO VERA CRUZ	RS	Interior 1	Sul	5
PORTO XAVIER	RS	Interior 1	Sul	5
POUSO NOVO	RS	Interior 1	Sul	5
PRESIDENTE LUCENA	RS	Interior 1	Sul	5
PROGRESSO	RS	Interior 1	Sul	5
PROTASIO ALVES	RS	Interior 1	Sul	5
PUTINGA	RS	Interior 1	Sul	5
QUARAI	RS	Interior 1	Sul	5
QUATRO IRMAOS	RS	Interior 1	Sul	5
QUEVEDOS	RS	Interior 1	Sul	5
QUINZE DE NOVEMBRO	RS	Interior 1	Sul	5
REDENTORA	RS	Interior 1	Sul	5
RELVADO	RS	Interior 1	Sul	5
RESTINGA SECA	RS	Interior 1	Sul	5
RIO DOS INDIOS	RS	Interior 1	Sul	5
RIO GRANDE	RS	Interior 1	Sul	5
RIO PARDO	RS	Interior 1	Sul	5
RIOZINHO	RS	Interior 1	Sul	5
ROCA SALES	RS	Interior 1	Sul	5
RODEIO BONITO	RS	Interior 1	Sul	5
ROLADOR	RS	Interior 1	Sul	5
ROLANTE	RS	Interior 1	Sul	5
RONDA ALTA	RS	Interior 1	Sul	5
RONDINHA	RS	Interior 1	Sul	5
ROQUE GONZALES	RS	Interior 1	Sul	5
ROSARIO DO SUL	RS	Interior 1	Sul	5
SAGRADA FAMILIA	RS	Interior 1	Sul	5
SALDANHA MARINHO	RS	Interior 1	Sul	5
SALTO DO JACUI	RS	Interior 1	Sul	5
SALVADOR DAS MISSOES	RS	Interior 1	Sul	5
SALVADOR DO SUL	RS	Interior 1	Sul	5
SANANDUVA	RS	Interior 1	Sul	5
SANTA BARBARA DO SUL	RS	Interior 1	Sul	5
SANTA CECILIA DO SUL	RS	Interior 1	Sul	5
SANTA CLARA DO SUL	RS	Interior 1	Sul	5
SANTA CRUZ DO SUL	RS	Interior 1	Sul	5
SANTA MARGARIDA DO SUL	RS	Interior 1	Sul	5
SANTA MARIA	RS	Interior 1	Sul	5
SANTA MARIA DO HERVAL	RS	Interior 1	Sul	5
SANTA ROSA	RS	Interior 1	Sul	5
SANTA TEREZA	RS	Interior 1	Sul	5
SANTA VITORIA DO PALMAR	RS	Interior 1	Sul	5
SANTANA DA BOA VISTA	RS	Interior 1	Sul	5
SANTANA DO LIVRAMENTO	RS	Interior 1	Sul	5
SANTIAGO	RS	Interior 1	Sul	5
SANTO ANGELO	RS	Interior 1	Sul	5
SANTO ANTONIO DA PATRULHA	RS	Interior 1	Sul	5
SANTO ANTONIO DAS MISSOES	RS	Interior 1	Sul	5
SANTO ANTONIO DO PALMA	RS	Interior 1	Sul	5
SANTO ANTONIO DO PLANALTO	RS	Interior 1	Sul	5
SANTO AUGUSTO	RS	Interior 1	Sul	5
SANTO CRISTO	RS	Interior 1	Sul	5
SANTO EXPEDITO DO SUL	RS	Interior 1	Sul	5
SAO BORJA	RS	Interior 1	Sul	5
SAO DOMINGOS DO SUL	RS	Interior 1	Sul	5
SAO FRANCISCO DE ASSIS	RS	Interior 1	Sul	5
SAO FRANCISCO DE PAULA	RS	Interior 1	Sul	5
SAO GABRIEL	RS	Interior 1	Sul	5
SAO JERONIMO	RS	Interior 1	Sul	5
SAO JOAO DA URTIGA	RS	Interior 1	Sul	5
SAO JOAO DO POLESINE	RS	Interior 1	Sul	5
SAO JORGE	RS	Interior 1	Sul	5
SAO JOSE DAS MISSOES	RS	Interior 1	Sul	5
SAO JOSE DO HERVAL	RS	Interior 1	Sul	5
SAO JOSE DO HORTENCIO	RS	Interior 1	Sul	5
SAO JOSE DO INHACORA	RS	Interior 1	Sul	5
SAO JOSE DO NORTE	RS	Interior 1	Sul	5
SAO JOSE DO OURO	RS	Interior 1	Sul	5
SAO JOSE DO SUL	RS	Interior 1	Sul	5
SAO JOSE DOS AUSENTES	RS	Interior 1	Sul	5
SAO LEOPOLDO	RS	Capital	Sul	2
SAO LOURENCO DO SUL	RS	Interior 1	Sul	5
SAO LUIZ GONZAGA	RS	Interior 1	Sul	5
SAO MARCOS	RS	Interior 1	Sul	5
SAO MARTINHO	RS	Interior 1	Sul	5
SAO MARTINHO DA SERRA	RS	Interior 1	Sul	5
SAO MIGUEL DAS MISSOES	RS	Interior 1	Sul	5
SAO NICOLAU	RS	Interior 1	Sul	5
SAO PAULO DAS MISSOES	RS	Interior 1	Sul	5
SAO PEDRO DA SERRA	RS	Interior 1	Sul	5
SAO PEDRO DAS MISSOES	RS	Interior 1	Sul	5
SAO PEDRO DO BUTIA	RS	Interior 1	Sul	5
SAO PEDRO DO SUL	RS	Interior 1	Sul	5
SAO SEBASTIAO DO CAI	RS	Interior 1	Sul	5
SAO SEPE	RS	Interior 1	Sul	5
SAO VALENTIM	RS	Interior 1	Sul	5
SAO VALENTIM DO SUL	RS	Interior 1	Sul	5
SAO VALERIO DO SUL	RS	Interior 1	Sul	5
SAO VENDELINO	RS	Interior 1	Sul	5
SAO VICENTE DO SUL	RS	Interior 1	Sul	5
SAPIRANGA	RS	Interior 1	Sul	5
SAPUCAIA DO SUL	RS	Capital	Sul	2
SARANDI	RS	Interior 1	Sul	5
SEBERI	RS	Interior 1	Sul	5
SEDE NOVA	RS	Interior 1	Sul	5
SEGREDO	RS	Interior 1	Sul	5
SELBACH	RS	Interior 1	Sul	5
SENADOR SALGADO FILHO	RS	Interior 1	Sul	5
SENTINELA DO SUL	RS	Interior 1	Sul	5
SERAFINA CORREA	RS	Interior 1	Sul	5
SERIO	RS	Interior 1	Sul	5
SERTAO	RS	Interior 1	Sul	5
SERTAO SANTANA	RS	Interior 1	Sul	5
SETE DE SETEMBRO	RS	Interior 1	Sul	5
SEVERIANO DE ALMEIDA	RS	Interior 1	Sul	5
SILVEIRA MARTINS	RS	Interior 1	Sul	5
SINIMBU	RS	Interior 1	Sul	5
SOBRADINHO	RS	Interior 1	Sul	5
SOLEDADE	RS	Interior 1	Sul	5
TABAI	RS	Interior 1	Sul	5
TAPEJARA	RS	Interior 1	Sul	5
TAPERA	RS	Interior 1	Sul	5
TAPES	RS	Interior 1	Sul	5
TAQUARA	RS	Interior 1	Sul	5
TAQUARI	RS	Interior 1	Sul	5
TAQUARUCU DO SUL	RS	Interior 1	Sul	5
TAVARES	RS	Interior 1	Sul	5
TENENTE PORTELA	RS	Interior 1	Sul	5
TERRA DE AREIA	RS	Interior 1	Sul	5
TEUTONIA	RS	Interior 1	Sul	5
TIO HUGO	RS	Interior 1	Sul	5
TIRADENTES DO SUL	RS	Interior 1	Sul	5
TOROPI	RS	Interior 1	Sul	5
TORRES	RS	Interior 1	Sul	5
TRAMANDAI	RS	Interior 1	Sul	5
TRAVESSEIRO	RS	Interior 1	Sul	5
TRES ARROIOS	RS	Interior 1	Sul	5
TRES CACHOEIRAS	RS	Interior 1	Sul	5
TRES COROAS	RS	Interior 1	Sul	5
TRES DE MAIO	RS	Interior 1	Sul	5
TRES FORQUILHAS	RS	Interior 1	Sul	5
TRES PALMEIRAS	RS	Interior 1	Sul	5
TRES PASSOS	RS	Interior 1	Sul	5
TRINDADE DO SUL	RS	Interior 1	Sul	5
TRIUNFO	RS	Interior 1	Sul	5
TUCUNDUVA	RS	Interior 1	Sul	5
TUNAS	RS	Interior 1	Sul	5
TUPANCI DO SUL	RS	Interior 1	Sul	5
TUPANCIRETA	RS	Interior 1	Sul	5
TUPANDI	RS	Interior 1	Sul	5
TUPARENDI	RS	Interior 1	Sul	5
TURUCU	RS	Interior 1	Sul	5
UBIRETAMA	RS	Interior 1	Sul	5
UNIAO DA SERRA	RS	Interior 1	Sul	5
UNISTALDA	RS	Interior 1	Sul	5
URUGUAIANA	RS	Interior 1	Sul	5
VACARIA	RS	Interior 1	Sul	5
VALE DO SOL	RS	Interior 1	Sul	5
VALE REAL	RS	Interior 1	Sul	5
VALE VERDE	RS	Interior 1	Sul	5
VANINI	RS	Interior 1	Sul	5
VENANCIO AIRES	RS	Interior 1	Sul	5
VERA CRUZ	RS	Interior 1	Sul	5
VERANOPOLIS	RS	Interior 1	Sul	5
VESPASIANO CORREA	RS	Interior 1	Sul	5
VIADUTOS	RS	Interior 1	Sul	5
VIAMAO	RS	Interior 1	Sul	5
VICENTE DUTRA	RS	Interior 1	Sul	5
VICTOR GRAEFF	RS	Interior 1	Sul	5
VILA FLORES	RS	Interior 1	Sul	5
VILA LANGARO	RS	Interior 1	Sul	5
VILA MARIA	RS	Interior 1	Sul	5
VILA NOVA DO SUL	RS	Interior 1	Sul	5
VISTA ALEGRE	RS	Interior 1	Sul	5
VISTA ALEGRE DO PRATA	RS	Interior 1	Sul	5
VISTA GAUCHA	RS	Interior 1	Sul	5
VITORIA DAS MISSOES	RS	Interior 1	Sul	5
WESTFALIA	RS	Interior 1	Sul	5
XANGRI-LA	RS	Interior 1	Sul	5
ABDON BATISTA	SC	Interior 1	Sul	5
ABELARDO LUZ	SC	Interior 1	Sul	5
AGROLANDIA	SC	Interior 1	Sul	5
AGRONOMICA	SC	Interior 1	Sul	5
AGUA DOCE	SC	Interior 1	Sul	5
AGUAS DE CHAPECO	SC	Interior 1	Sul	5
AGUAS FRIAS	SC	Interior 1	Sul	5
AGUAS MORNAS	SC	Interior 1	Sul	5
ALFREDO WAGNER	SC	Interior 1	Sul	5
ALTO BELA VISTA	SC	Interior 1	Sul	5
ANCHIETA	SC	Interior 1	Sul	5
ANGELINA	SC	Interior 1	Sul	5
ANITA GARIBALDI	SC	Interior 1	Sul	5
ANITAPOLIS	SC	Interior 1	Sul	5
ANTONIO CARLOS	SC	Interior 1	Sul	5
APIUNA	SC	Interior 1	Sul	5
ARABUTA	SC	Interior 1	Sul	5
ARAQUARI	SC	Interior 1	Sul	5
ARARANGUA	SC	Interior 1	Sul	5
ARMAZEM	SC	Interior 1	Sul	5
ARROIO TRINTA	SC	Interior 1	Sul	5
ARVOREDO	SC	Interior 1	Sul	5
ASCURRA	SC	Interior 1	Sul	5
ATALANTA	SC	Interior 1	Sul	5
AURORA	SC	Interior 1	Sul	5
BALNEARIO ARROIO DO SILVA	SC	Interior 1	Sul	5
BALNEARIO BARRA DO SUL	SC	Interior 1	Sul	5
BALNEARIO CAMBORIU	SC	Capital	Sul	2
BALNEARIO GAIVOTA	SC	Interior 1	Sul	5
BALNEARIO PICARRAS	SC	Interior 1	Sul	5
BALNEARIO RINCAO	SC	Interior 1	Sul	5
BANDEIRANTE	SC	Interior 1	Sul	5
BARRA BONITA	SC	Interior 1	Sul	5
BARRA VELHA	SC	Interior 1	Sul	5
BELA VISTA DO TOLDO	SC	Interior 1	Sul	5
BELMONTE	SC	Interior 1	Sul	5
BENEDITO NOVO	SC	Interior 1	Sul	5
BIGUACU	SC	Interior 1	Sul	5
BLUMENAU	SC	Capital	Sul	2
BOCAINA DO SUL	SC	Interior 1	Sul	5
BOM JARDIM DA SERRA	SC	Interior 1	Sul	5
BOM JESUS	SC	Interior 1	Sul	5
BOM JESUS DO OESTE	SC	Interior 1	Sul	5
BOM RETIRO	SC	Interior 1	Sul	5
BOMBINHAS	SC	Interior 1	Sul	5
BOTUVERA	SC	Interior 1	Sul	5
BRACO DO NORTE	SC	Interior 1	Sul	5
BRACO DO TROMBUDO	SC	Interior 1	Sul	5
BRUNOPOLIS	SC	Interior 1	Sul	5
BRUSQUE	SC	Interior 1	Sul	5
CACADOR	SC	Interior 1	Sul	5
CAIBI	SC	Interior 1	Sul	5
CALMON	SC	Interior 1	Sul	5
CAMBORIU	SC	Capital	Sul	2
CAMPO ALEGRE	SC	Interior 1	Sul	5
CAMPO BELO DO SUL	SC	Interior 1	Sul	5
CAMPO ERE	SC	Interior 1	Sul	5
CAMPOS NOVOS	SC	Interior 1	Sul	5
CANELINHA	SC	Interior 1	Sul	5
CANOINHAS	SC	Interior 1	Sul	5
CAPAO ALTO	SC	Interior 1	Sul	5
CAPINZAL	SC	Interior 1	Sul	5
CAPIVARI DE BAIXO	SC	Interior 1	Sul	5
CATANDUVAS	SC	Interior 1	Sul	5
CAXAMBU DO SUL	SC	Interior 1	Sul	5
CELSO RAMOS	SC	Interior 1	Sul	5
CERRO NEGRO	SC	Interior 1	Sul	5
CHAPADAO DO LAGEADO	SC	Interior 1	Sul	5
CHAPECO	SC	Interior 1	Sul	5
COCAL DO SUL	SC	Interior 1	Sul	5
CONCORDIA	SC	Interior 1	Sul	5
CORDILHEIRA ALTA	SC	Interior 1	Sul	5
CORONEL FREITAS	SC	Interior 1	Sul	5
CORONEL MARTINS	SC	Interior 1	Sul	5
CORREIA PINTO	SC	Interior 1	Sul	5
CORUPA	SC	Interior 1	Sul	5
CRICIUMA	SC	Interior 1	Sul	5
CUNHA PORA	SC	Interior 1	Sul	5
CUNHATAI	SC	Interior 1	Sul	5
CURITIBANOS	SC	Interior 1	Sul	5
DESCANSO	SC	Interior 1	Sul	5
DIONISIO CERQUEIRA	SC	Interior 1	Sul	5
DONA EMMA	SC	Interior 1	Sul	5
DOUTOR PEDRINHO	SC	Interior 1	Sul	5
ENTRE RIOS	SC	Interior 1	Sul	5
ERMO	SC	Interior 1	Sul	5
ERVAL VELHO	SC	Interior 1	Sul	5
FAXINAL DOS GUEDES	SC	Interior 1	Sul	5
FLOR DO SERTAO	SC	Interior 1	Sul	5
FLORIANOPOLIS	SC	Capital	Sul	2
FORMOSA DO SUL	SC	Interior 1	Sul	5
FORQUILHINHA	SC	Interior 1	Sul	5
FRAIBURGO	SC	Interior 1	Sul	5
FREI ROGERIO	SC	Interior 1	Sul	5
GALVAO	SC	Interior 1	Sul	5
GAROPABA	SC	Interior 1	Sul	5
GARUVA	SC	Interior 1	Sul	5
GASPAR	SC	Capital	Sul	2
GOVERNADOR CELSO RAMOS	SC	Interior 1	Sul	5
GRAO PARA	SC	Interior 1	Sul	5
GRAVATAL	SC	Interior 1	Sul	5
GUABIRUBA	SC	Interior 1	Sul	5
GUARACIABA	SC	Interior 1	Sul	5
GUARAMIRIM	SC	Interior 1	Sul	5
GUARUJA DO SUL	SC	Interior 1	Sul	5
GUATAMBU	SC	Interior 1	Sul	5
HERVAL D OESTE	SC	Interior 1	Sul	5
IBIAM	SC	Interior 1	Sul	5
IBICARE	SC	Interior 1	Sul	5
IBIRAMA	SC	Interior 1	Sul	5
ICARA	SC	Interior 1	Sul	5
ILHOTA	SC	Capital	Sul	2
IMARUI	SC	Interior 1	Sul	5
IMBITUBA	SC	Interior 1	Sul	5
IMBUIA	SC	Interior 1	Sul	5
INDAIAL	SC	Interior 1	Sul	5
IOMERE	SC	Interior 1	Sul	5
IPIRA	SC	Interior 1	Sul	5
IPORA DO OESTE	SC	Interior 1	Sul	5
IPUACU	SC	Interior 1	Sul	5
IPUMIRIM	SC	Interior 1	Sul	5
IRACEMINHA	SC	Interior 1	Sul	5
IRANI	SC	Interior 1	Sul	5
IRATI	SC	Interior 1	Sul	5
IRINEOPOLIS	SC	Interior 1	Sul	5
ITA	SC	Interior 1	Sul	5
ITAIOPOLIS	SC	Interior 1	Sul	5
ITAJAI	SC	Capital	Sul	2
ITAPEMA	SC	Interior 1	Sul	5
ITAPIRANGA	SC	Interior 1	Sul	5
ITAPOA	SC	Interior 1	Sul	5
ITUPORANGA	SC	Interior 1	Sul	5
JABORA	SC	Interior 1	Sul	5
JACINTO MACHADO	SC	Interior 1	Sul	5
JAGUARUNA	SC	Interior 1	Sul	5
JARAGUA DO SUL	SC	Capital	Sul	2
JARDINOPOLIS	SC	Interior 1	Sul	5
JOACABA	SC	Interior 1	Sul	5
JOINVILLE	SC	Interior 1	Sul	5
JOSE BOITEUX	SC	Interior 1	Sul	5
JUPIA	SC	Interior 1	Sul	5
LACERDOPOLIS	SC	Interior 1	Sul	5
LAGES	SC	Interior 1	Sul	5
LAGUNA	SC	Interior 1	Sul	5
LAJEADO GRANDE	SC	Interior 1	Sul	5
LAURENTINO	SC	Interior 1	Sul	5
LAURO MULLER	SC	Interior 1	Sul	5
LEBON REGIS	SC	Interior 1	Sul	5
LEOBERTO LEAL	SC	Interior 1	Sul	5
LINDOIA DO SUL	SC	Interior 1	Sul	5
LONTRAS	SC	Interior 1	Sul	5
LUIZ ALVES	SC	Interior 1	Sul	5
LUZERNA	SC	Interior 1	Sul	5
MACIEIRA	SC	Interior 1	Sul	5
MAFRA	SC	Interior 1	Sul	5
MAJOR GERCINO	SC	Interior 1	Sul	5
MAJOR VIEIRA	SC	Interior 1	Sul	5
MARACAJA	SC	Interior 1	Sul	5
MARAVILHA	SC	Interior 1	Sul	5
MAREMA	SC	Interior 1	Sul	5
MASSARANDUBA	SC	Interior 1	Sul	5
MATOS COSTA	SC	Interior 1	Sul	5
MELEIRO	SC	Interior 1	Sul	5
MIRIM DOCE	SC	Interior 1	Sul	5
MODELO	SC	Interior 1	Sul	5
MONDAI	SC	Interior 1	Sul	5
MONTE CARLO	SC	Interior 1	Sul	5
MONTE CASTELO	SC	Interior 1	Sul	5
MORRO DA FUMACA	SC	Interior 1	Sul	5
MORRO GRANDE	SC	Interior 1	Sul	5
NAVEGANTES	SC	Interior 1	Sul	5
NOVA ERECHIM	SC	Interior 1	Sul	5
NOVA ITABERABA	SC	Interior 1	Sul	5
NOVA TRENTO	SC	Interior 1	Sul	5
NOVA VENEZA	SC	Interior 1	Sul	5
NOVO HORIZONTE	SC	Interior 1	Sul	5
ORLEANS	SC	Interior 1	Sul	5
OTACILIO COSTA	SC	Interior 1	Sul	5
OURO	SC	Interior 1	Sul	5
OURO VERDE	SC	Interior 1	Sul	5
PAIAL	SC	Interior 1	Sul	5
PAINEL	SC	Interior 1	Sul	5
PALHOCA	SC	Interior 1	Sul	5
PALMA SOLA	SC	Interior 1	Sul	5
PALMEIRA	SC	Interior 1	Sul	5
PALMITOS	SC	Interior 1	Sul	5
PAPANDUVA	SC	Interior 1	Sul	5
PARAISO	SC	Interior 1	Sul	5
PASSO DE TORRES	SC	Interior 1	Sul	5
PASSOS MAIA	SC	Interior 1	Sul	5
PAULO LOPES	SC	Interior 1	Sul	5
PEDRAS GRANDES	SC	Interior 1	Sul	5
PENHA	SC	Interior 1	Sul	5
PERITIBA	SC	Interior 1	Sul	5
PESCARIA BRAVA	SC	Interior 1	Sul	5
PETROLANDIA	SC	Interior 1	Sul	5
PINHALZINHO	SC	Interior 1	Sul	5
PINHEIRO PRETO	SC	Interior 1	Sul	5
PIRATUBA	SC	Interior 1	Sul	5
PLANALTO ALEGRE	SC	Interior 1	Sul	5
POMERODE	SC	Interior 1	Sul	5
PONTE ALTA	SC	Interior 1	Sul	5
PONTE ALTA DO NORTE	SC	Interior 1	Sul	5
PONTE SERRADA	SC	Interior 1	Sul	5
PORTO BELO	SC	Interior 1	Sul	5
PORTO UNIAO	SC	Interior 1	Sul	5
POUSO REDONDO	SC	Interior 1	Sul	5
PRAIA GRANDE	SC	Interior 1	Sul	5
PRESIDENTE CASTELLO BRANCO	SC	Interior 1	Sul	5
PRESIDENTE GETULIO	SC	Interior 1	Sul	5
PRESIDENTE NEREU	SC	Interior 1	Sul	5
PRINCESA	SC	Interior 1	Sul	5
QUILOMBO	SC	Interior 1	Sul	5
RANCHO QUEIMADO	SC	Interior 1	Sul	5
RIO DAS ANTAS	SC	Interior 1	Sul	5
RIO DO CAMPO	SC	Interior 1	Sul	5
RIO DO OESTE	SC	Interior 1	Sul	5
RIO DO SUL	SC	Interior 1	Sul	5
RIO DOS CEDROS	SC	Interior 1	Sul	5
RIO FORTUNA	SC	Interior 1	Sul	5
RIO NEGRINHO	SC	Interior 1	Sul	5
RIO RUFINO	SC	Interior 1	Sul	5
RIQUEZA	SC	Interior 1	Sul	5
RODEIO	SC	Interior 1	Sul	5
ROMELANDIA	SC	Interior 1	Sul	5
SALETE	SC	Interior 1	Sul	5
SALTINHO	SC	Interior 1	Sul	5
SALTO VELOSO	SC	Interior 1	Sul	5
SANGAO	SC	Interior 1	Sul	5
SANTA CECILIA	SC	Interior 1	Sul	5
SANTA HELENA	SC	Interior 1	Sul	5
SANTA ROSA DE LIMA	SC	Interior 1	Sul	5
SANTA ROSA DO SUL	SC	Interior 1	Sul	5
SANTA TEREZINHA	SC	Interior 1	Sul	5
SANTA TEREZINHA DO PROGRESSO	SC	Interior 1	Sul	5
SANTIAGO DO SUL	SC	Interior 1	Sul	5
SANTO AMARO DA IMPERATRIZ	SC	Interior 1	Sul	5
SAO BENTO DO SUL	SC	Interior 1	Sul	5
SAO BERNARDINO	SC	Interior 1	Sul	5
SAO BONIFACIO	SC	Interior 1	Sul	5
SAO CARLOS	SC	Interior 1	Sul	5
SAO CRISTOVAO DO SUL	SC	Interior 1	Sul	5
SAO DOMINGOS	SC	Interior 1	Sul	5
SAO FRANCISCO DO SUL	SC	Interior 1	Sul	5
SAO JOAO BATISTA	SC	Interior 1	Sul	5
SAO JOAO DO ITAPERIU	SC	Interior 1	Sul	5
SAO JOAO DO OESTE	SC	Interior 1	Sul	5
SAO JOAO DO SUL	SC	Interior 1	Sul	5
SAO JOAQUIM	SC	Interior 1	Sul	5
SAO JOSE	SC	Capital	Sul	2
SAO JOSE DO CEDRO	SC	Interior 1	Sul	5
SAO JOSE DO CERRITO	SC	Interior 1	Sul	5
SAO LOURENCO DO OESTE	SC	Interior 1	Sul	5
SAO LUDGERO	SC	Interior 1	Sul	5
SAO MARTINHO	SC	Interior 1	Sul	5
SAO MIGUEL DA BOA VISTA	SC	Interior 1	Sul	5
SAO MIGUEL DO OESTE	SC	Interior 1	Sul	5
SAO PEDRO DE ALCANTARA	SC	Interior 1	Sul	5
SAUDADES	SC	Interior 1	Sul	5
SCHROEDER	SC	Interior 1	Sul	5
SEARA	SC	Interior 1	Sul	5
SERRA ALTA	SC	Interior 1	Sul	5
SIDEROPOLIS	SC	Interior 1	Sul	5
SOMBRIO	SC	Interior 1	Sul	5
SUL BRASIL	SC	Interior 1	Sul	5
TAIO	SC	Interior 1	Sul	5
TANGARA	SC	Interior 1	Sul	5
TIGRINHOS	SC	Interior 1	Sul	5
TIJUCAS	SC	Interior 1	Sul	5
TIMBE DO SUL	SC	Interior 1	Sul	5
TIMBO	SC	Interior 1	Sul	5
TIMBO GRANDE	SC	Interior 1	Sul	5
TRES BARRAS	SC	Interior 1	Sul	5
TREVISO	SC	Interior 1	Sul	5
TREZE DE MAIO	SC	Interior 1	Sul	5
TREZE TILIAS	SC	Interior 1	Sul	5
TROMBUDO CENTRAL	SC	Interior 1	Sul	5
TUBARAO	SC	Interior 1	Sul	5
TUNAPOLIS	SC	Interior 1	Sul	5
TURVO	SC	Interior 1	Sul	5
UNIAO DO OESTE	SC	Interior 1	Sul	5
URUBICI	SC	Interior 1	Sul	5
URUPEMA	SC	Interior 1	Sul	5
URUSSANGA	SC	Interior 1	Sul	5
VARGEAO	SC	Interior 1	Sul	5
VARGEM	SC	Interior 1	Sul	5
VARGEM BONITA	SC	Interior 1	Sul	5
VIDAL RAMOS	SC	Interior 1	Sul	5
VIDEIRA	SC	Interior 1	Sul	5
VITOR MEIRELES	SC	Interior 1	Sul	5
WITMARSUM	SC	Interior 1	Sul	5
XANXERE	SC	Interior 1	Sul	5
XAVANTINA	SC	Interior 1	Sul	5
XAXIM	SC	Interior 1	Sul	5
ZORTEA	SC	Interior 1	Sul	5
AMPARO DE SAO FRANCISCO	SE	Interior 1	Nordeste	10
AQUIDABA	SE	Interior 1	Nordeste	10
ARACAJU	SE	Capital	Nordeste	7
ARAUA	SE	Interior 1	Nordeste	10
AREIA BRANCA	SE	Interior 1	Nordeste	10
BARRA DOS COQUEIROS	SE	Interior 1	Nordeste	10
BOQUIM	SE	Interior 1	Nordeste	10
BREJO GRANDE	SE	Interior 1	Nordeste	10
CAMPO DO BRITO	SE	Interior 1	Nordeste	10
CANHOBA	SE	Interior 1	Nordeste	10
CANINDE DE SAO FRANCISCO	SE	Interior 1	Nordeste	10
CAPELA	SE	Interior 1	Nordeste	10
CARIRA	SE	Interior 1	Nordeste	10
CARMOPOLIS	SE	Interior 1	Nordeste	10
CEDRO DE SAO JOAO	SE	Interior 1	Nordeste	10
CRISTINAPOLIS	SE	Interior 1	Nordeste	10
CUMBE	SE	Interior 1	Nordeste	10
DIVINA PASTORA	SE	Interior 1	Nordeste	10
ESTANCIA	SE	Interior 1	Nordeste	10
FEIRA NOVA	SE	Interior 1	Nordeste	10
FREI PAULO	SE	Interior 1	Nordeste	10
GARARU	SE	Interior 1	Nordeste	10
GENERAL MAYNARD	SE	Interior 1	Nordeste	10
GRACHO CARDOSO	SE	Interior 1	Nordeste	10
ILHA DAS FLORES	SE	Interior 1	Nordeste	10
INDIAROBA	SE	Interior 1	Nordeste	10
ITABAIANA	SE	Interior 1	Nordeste	10
ITABAIANINHA	SE	Interior 1	Nordeste	10
ITABI	SE	Interior 1	Nordeste	10
ITAPORANGA D AJUDA	SE	Interior 1	Nordeste	10
JAPARATUBA	SE	Interior 1	Nordeste	10
JAPOATA	SE	Interior 1	Nordeste	10
LAGARTO	SE	Interior 1	Nordeste	10
LARANJEIRAS	SE	Interior 1	Nordeste	10
MACAMBIRA	SE	Interior 1	Nordeste	10
MALHADA DOS BOIS	SE	Interior 1	Nordeste	10
MALHADOR	SE	Interior 1	Nordeste	10
MARUIM	SE	Interior 1	Nordeste	10
MOITA BONITA	SE	Interior 1	Nordeste	10
MONTE ALEGRE DE SERGIPE	SE	Interior 1	Nordeste	10
MURIBECA	SE	Interior 1	Nordeste	10
NEOPOLIS	SE	Interior 1	Nordeste	10
NOSSA SENHORA APARECIDA	SE	Interior 1	Nordeste	10
NOSSA SENHORA DA GLORIA	SE	Interior 1	Nordeste	10
NOSSA SENHORA DAS DORES	SE	Interior 1	Nordeste	10
NOSSA SENHORA DE LOURDES	SE	Interior 1	Nordeste	10
NOSSA SENHORA DO SOCORRO	SE	Interior 1	Nordeste	10
PACATUBA	SE	Interior 1	Nordeste	10
PEDRA MOLE	SE	Interior 1	Nordeste	10
PEDRINHAS	SE	Interior 1	Nordeste	10
PINHAO	SE	Interior 1	Nordeste	10
PIRAMBU	SE	Interior 1	Nordeste	10
POCO REDONDO	SE	Interior 1	Nordeste	10
POCO VERDE	SE	Interior 1	Nordeste	10
PORTO DA FOLHA	SE	Interior 1	Nordeste	10
PROPRIA	SE	Interior 1	Nordeste	10
RIACHAO DO DANTAS	SE	Interior 1	Nordeste	10
RIACHUELO	SE	Interior 1	Nordeste	10
RIBEIROPOLIS	SE	Interior 1	Nordeste	10
ROSARIO DO CATETE	SE	Interior 1	Nordeste	10
SALGADO	SE	Interior 1	Nordeste	10
SANTA LUZIA DO ITANHY	SE	Interior 1	Nordeste	10
SANTA ROSA DE LIMA	SE	Interior 1	Nordeste	10
SANTANA DO SAO FRANCISCO	SE	Interior 1	Nordeste	10
SANTO AMARO DAS BROTAS	SE	Interior 1	Nordeste	10
SAO CRISTOVAO	SE	Interior 1	Nordeste	10
SAO DOMINGOS	SE	Interior 1	Nordeste	10
SAO FRANCISCO	SE	Interior 1	Nordeste	10
SAO MIGUEL DO ALEIXO	SE	Interior 1	Nordeste	10
SIMAO DIAS	SE	Interior 1	Nordeste	10
SIRIRI	SE	Interior 1	Nordeste	10
TELHA	SE	Interior 1	Nordeste	10
TOBIAS BARRETO	SE	Interior 1	Nordeste	10
TOMAR DO GERU	SE	Interior 1	Nordeste	10
UMBAUBA	SE	Interior 1	Nordeste	10
ADAMANTINA	SP	Interior 2	Sudeste	3
ADOLFO	SP	Interior 2	Sudeste	3
AGUAI	SP	Interior 2	Sudeste	3
AGUAS DA PRATA	SP	Interior 2	Sudeste	3
AGUAS DE LINDOIA	SP	Interior 2	Sudeste	3
AGUAS DE SANTA BARBARA	SP	Interior 1	Sudeste	3
AGUAS DE SAO PEDRO	SP	Interior 2	Sudeste	3
AGUDOS	SP	Interior 1	Sudeste	3
ALAMBARI	SP	Interior 2	Sudeste	3
ALFREDO MARCONDES	SP	Interior 1	Sudeste	3
ALTAIR	SP	Interior 2	Sudeste	3
ALTINOPOLIS	SP	Interior 1	Sudeste	3
ALTO ALEGRE	SP	Interior 2	Sudeste	3
ALUMINIO	SP	Interior 1	Sudeste	3
ALVARES FLORENCE	SP	Interior 2	Sudeste	3
ALVARES MACHADO	SP	Interior 1	Sudeste	3
ALVARO DE CARVALHO	SP	Interior 2	Sudeste	3
ALVINLANDIA	SP	Interior 2	Sudeste	3
AMERICANA	SP	Interior 2	Sudeste	3
AMERICO BRASILIENSE	SP	Interior 1	Sudeste	3
AMERICO DE CAMPOS	SP	Interior 2	Sudeste	3
AMPARO	SP	Interior 1	Sudeste	3
ANALANDIA	SP	Interior 1	Sudeste	3
ANDRADINA	SP	Interior 1	Sudeste	3
ANGATUBA	SP	Interior 2	Sudeste	3
ANHEMBI	SP	Interior 2	Sudeste	3
ANHUMAS	SP	Interior 1	Sudeste	3
APARECIDA	SP	Interior 1	Sudeste	3
APARECIDA D OESTE	SP	Interior 2	Sudeste	3
APIAI	SP	Interior 2	Sudeste	3
ARACARIGUAMA	SP	Interior 1	Sudeste	3
ARACATUBA	SP	Interior 1	Sudeste	3
ARACOIABA DA SERRA	SP	Interior 1	Sudeste	3
ARAMINA	SP	Interior 1	Sudeste	3
ARANDU	SP	Interior 2	Sudeste	3
ARAPEI	SP	Interior 2	Sudeste	3
ARARAQUARA	SP	Interior 1	Sudeste	3
ARARAS	SP	Interior 1	Sudeste	3
ARCO-IRIS	SP	Interior 2	Sudeste	3
AREALVA	SP	Interior 1	Sudeste	3
AREIAS	SP	Interior 2	Sudeste	3
AREIOPOLIS	SP	Interior 1	Sudeste	3
ARIRANHA	SP	Interior 2	Sudeste	3
ARTUR NOGUEIRA	SP	Interior 1	Sudeste	3
ARUJA	SP	Interior 2	Sudeste	3
ASPASIA	SP	Interior 2	Sudeste	3
ASSIS	SP	Interior 1	Sudeste	3
ATIBAIA	SP	Interior 1	Sudeste	3
AURIFLAMA	SP	Interior 2	Sudeste	3
AVAI	SP	Interior 2	Sudeste	3
AVANHANDAVA	SP	Interior 2	Sudeste	3
AVARE	SP	Interior 1	Sudeste	3
BADY BASSITT	SP	Interior 1	Sudeste	3
BALBINOS	SP	Interior 1	Sudeste	3
BALSAMO	SP	Interior 1	Sudeste	3
BANANAL	SP	Interior 2	Sudeste	3
BARAO DE ANTONINA	SP	Interior 2	Sudeste	3
BARBOSA	SP	Interior 2	Sudeste	3
BARIRI	SP	Interior 1	Sudeste	3
BARRA BONITA	SP	Interior 1	Sudeste	3
BARRA DO CHAPEU	SP	Interior 2	Sudeste	3
BARRA DO TURVO	SP	Interior 2	Sudeste	3
BARRETOS	SP	Interior 1	Sudeste	3
BARRINHA	SP	Interior 1	Sudeste	3
BARUERI	SP	Interior 1	Sudeste	3
BASTOS	SP	Interior 2	Sudeste	3
BATATAIS	SP	Interior 1	Sudeste	3
BAURU	SP	Bauru	Sudeste	2
BEBEDOURO	SP	Interior 1	Sudeste	3
BENTO DE ABREU	SP	Interior 2	Sudeste	3
BERNARDINO DE CAMPOS	SP	Interior 1	Sudeste	3
BERTIOGA	SP	Interior 2	Sudeste	3
BILAC	SP	Interior 2	Sudeste	3
BIRIGUI	SP	Interior 1	Sudeste	3
BIRITIBA-MIRIM	SP	Interior 2	Sudeste	3
BOA ESPERANCA DO SUL	SP	Interior 1	Sudeste	3
BOCAINA	SP	Interior 1	Sudeste	3
BOFETE	SP	Interior 2	Sudeste	3
BOITUVA	SP	Interior 1	Sudeste	3
BOM JESUS DOS PERDOES	SP	Interior 2	Sudeste	3
BOM SUCESSO DE ITARARE	SP	Interior 2	Sudeste	3
BORA	SP	Interior 2	Sudeste	3
BORACEIA	SP	Interior 2	Sudeste	3
BORBOREMA	SP	Interior 2	Sudeste	3
BOREBI	SP	Interior 1	Sudeste	3
BOTUCATU	SP	Interior 1	Sudeste	3
BRAGANCA PAULISTA	SP	Interior 1	Sudeste	3
BRAUNA	SP	Interior 2	Sudeste	3
BREJO ALEGRE	SP	Interior 2	Sudeste	3
BRODOWSKI	SP	Interior 1	Sudeste	3
BROTAS	SP	Interior 1	Sudeste	3
BURI	SP	Interior 2	Sudeste	3
BURITAMA	SP	Interior 1	Sudeste	3
BURITIZAL	SP	Interior 1	Sudeste	3
CABRALIA PAULISTA	SP	Interior 2	Sudeste	3
CABREUVA	SP	Interior 2	Sudeste	3
CACAPAVA	SP	Interior 1	Sudeste	3
CACHOEIRA PAULISTA	SP	Interior 1	Sudeste	3
CACONDE	SP	Interior 1	Sudeste	3
CAFELANDIA	SP	Interior 1	Sudeste	3
CAIABU	SP	Interior 2	Sudeste	3
CAIEIRAS	SP	Interior 2	Sudeste	3
CAIUA	SP	Interior 2	Sudeste	3
CAJAMAR	SP	Interior 2	Sudeste	3
CAJATI	SP	Interior 2	Sudeste	3
CAJOBI	SP	Interior 2	Sudeste	3
CAJURU	SP	Interior 1	Sudeste	3
CAMPINA DO MONTE ALEGRE	SP	Interior 1	Sudeste	3
CAMPINAS	SP	Campinas	Sudeste	2
CAMPO LIMPO PAULISTA	SP	Interior 2	Sudeste	3
CAMPOS DO JORDAO	SP	Interior 1	Sudeste	3
CAMPOS NOVOS PAULISTA	SP	Interior 2	Sudeste	3
CANANEIA	SP	Interior 2	Sudeste	3
CANAS	SP	Interior 2	Sudeste	3
CANDIDO MOTA	SP	Interior 1	Sudeste	3
CANDIDO RODRIGUES	SP	Interior 2	Sudeste	3
CANITAR	SP	Interior 2	Sudeste	3
CAPAO BONITO	SP	Interior 2	Sudeste	3
CAPELA DO ALTO	SP	Interior 1	Sudeste	3
CAPIVARI	SP	Interior 1	Sudeste	3
CARAGUATATUBA	SP	Interior 1	Sudeste	3
CARAPICUIBA	SP	Interior 1	Sudeste	3
CARDOSO	SP	Interior 2	Sudeste	3
CASA BRANCA	SP	Interior 1	Sudeste	3
CASSIA DOS COQUEIROS	SP	Interior 1	Sudeste	3
CASTILHO	SP	Interior 2	Sudeste	3
CATANDUVA	SP	Interior 1	Sudeste	3
CATIGUA	SP	Interior 2	Sudeste	3
CEDRAL	SP	Interior 1	Sudeste	3
CERQUEIRA CESAR	SP	Interior 1	Sudeste	3
CERQUILHO	SP	Interior 1	Sudeste	3
CESARIO LANGE	SP	Interior 2	Sudeste	3
CHARQUEADA	SP	Interior 2	Sudeste	3
CHAVANTES	SP	Interior 1	Sudeste	3
CLEMENTINA	SP	Interior 2	Sudeste	3
COLINA	SP	Interior 1	Sudeste	3
COLOMBIA	SP	Interior 2	Sudeste	3
CONCHAL	SP	Interior 1	Sudeste	3
CONCHAS	SP	Interior 2	Sudeste	3
CORDEIROPOLIS	SP	Interior 1	Sudeste	3
COROADOS	SP	Interior 1	Sudeste	3
CORONEL MACEDO	SP	Interior 2	Sudeste	3
CORUMBATAI	SP	Interior 2	Sudeste	3
COSMOPOLIS	SP	Interior 1	Sudeste	3
COSMORAMA	SP	Interior 1	Sudeste	3
COTIA	SP	Interior 1	Sudeste	3
CRAVINHOS	SP	Interior 1	Sudeste	3
CRISTAIS PAULISTA	SP	Interior 1	Sudeste	3
CRUZALIA	SP	Interior 2	Sudeste	3
CRUZEIRO	SP	Interior 1	Sudeste	3
CUBATAO	SP	Interior 2	Sudeste	3
CUNHA	SP	Interior 2	Sudeste	3
DESCALVADO	SP	Interior 1	Sudeste	3
DIADEMA	SP	Interior 1	Sudeste	3
DIRCE REIS	SP	Interior 2	Sudeste	3
DIVINOLANDIA	SP	Interior 1	Sudeste	3
DOBRADA	SP	Interior 1	Sudeste	3
DOIS CORREGOS	SP	Interior 2	Sudeste	3
DOLCINOPOLIS	SP	Interior 2	Sudeste	3
DOURADO	SP	Interior 2	Sudeste	3
DRACENA	SP	Interior 2	Sudeste	3
DUARTINA	SP	Interior 1	Sudeste	3
DUMONT	SP	Interior 1	Sudeste	3
ECHAPORA	SP	Interior 2	Sudeste	3
ELDORADO	SP	Interior 2	Sudeste	3
ELIAS FAUSTO	SP	Interior 1	Sudeste	3
ELISIARIO	SP	Interior 2	Sudeste	3
EMBAUBA	SP	Interior 2	Sudeste	3
EMBU DAS ARTES	SP	Interior 1	Sudeste	3
EMBU-GUACU	SP	Interior 2	Sudeste	3
EMILIANOPOLIS	SP	Interior 2	Sudeste	3
ENGENHEIRO COELHO	SP	Interior 1	Sudeste	3
ESPIRITO SANTO DO PINHAL	SP	Interior 2	Sudeste	3
ESPIRITO SANTO DO TURVO	SP	Interior 1	Sudeste	3
ESTIVA GERBI	SP	Interior 1	Sudeste	3
ESTRELA DO NORTE	SP	Interior 2	Sudeste	3
ESTRELA D OESTE	SP	Interior 1	Sudeste	3
EUCLIDES DA CUNHA PAULISTA	SP	Interior 2	Sudeste	3
FARTURA	SP	Interior 2	Sudeste	3
FERNANDO PRESTES	SP	Interior 2	Sudeste	3
FERNANDOPOLIS	SP	Interior 1	Sudeste	3
FERNAO	SP	Interior 2	Sudeste	3
FERRAZ DE VASCONCELOS	SP	Interior 2	Sudeste	3
FLORA RICA	SP	Interior 2	Sudeste	3
FLOREAL	SP	Interior 2	Sudeste	3
FLORIDA PAULISTA	SP	Interior 2	Sudeste	3
FLORINIA	SP	Interior 2	Sudeste	3
FRANCA	SP	Interior 1	Sudeste	3
FRANCISCO MORATO	SP	Interior 2	Sudeste	3
FRANCO DA ROCHA	SP	Interior 2	Sudeste	3
GABRIEL MONTEIRO	SP	Interior 2	Sudeste	3
GALIA	SP	Interior 2	Sudeste	3
GARCA	SP	Interior 1	Sudeste	3
GASTAO VIDIGAL	SP	Interior 2	Sudeste	3
GAVIAO PEIXOTO	SP	Interior 1	Sudeste	3
GENERAL SALGADO	SP	Interior 2	Sudeste	3
GETULINA	SP	Interior 1	Sudeste	3
GLICERIO	SP	Interior 2	Sudeste	3
GUAICARA	SP	Interior 1	Sudeste	3
GUAIMBE	SP	Interior 1	Sudeste	3
GUAIRA	SP	Interior 1	Sudeste	3
GUAPIACU	SP	Interior 1	Sudeste	3
GUAPIARA	SP	Interior 2	Sudeste	3
GUARA	SP	Interior 1	Sudeste	3
GUARACAI	SP	Interior 2	Sudeste	3
GUARACI	SP	Interior 2	Sudeste	3
GUARANI D OESTE	SP	Interior 2	Sudeste	3
GUARANTA	SP	Interior 1	Sudeste	3
GUARARAPES	SP	Interior 1	Sudeste	3
GUARAREMA	SP	Interior 2	Sudeste	3
GUARATINGUETA	SP	Interior 1	Sudeste	3
GUAREI	SP	Interior 2	Sudeste	3
GUARIBA	SP	Interior 1	Sudeste	3
GUARUJA	SP	Interior 2	Sudeste	3
GUARULHOS	SP	Interior 1	Sudeste	3
GUATAPARA	SP	Interior 1	Sudeste	3
GUZOLANDIA	SP	Interior 2	Sudeste	3
HERCULANDIA	SP	Interior 2	Sudeste	3
HOLAMBRA	SP	Interior 2	Sudeste	3
HORTOLANDIA	SP	Interior 1	Sudeste	3
IACANGA	SP	Interior 1	Sudeste	3
IACRI	SP	Interior 2	Sudeste	3
IARAS	SP	Interior 2	Sudeste	3
IBATE	SP	Interior 1	Sudeste	3
IBIRA	SP	Interior 1	Sudeste	3
IBIRAREMA	SP	Interior 2	Sudeste	3
IBITINGA	SP	Interior 2	Sudeste	3
IBIUNA	SP	Interior 2	Sudeste	3
ICEM	SP	Interior 2	Sudeste	3
IEPE	SP	Interior 2	Sudeste	3
IGARACU DO TIETE	SP	Interior 1	Sudeste	3
IGARAPAVA	SP	Interior 1	Sudeste	3
IGARATA	SP	Interior 2	Sudeste	3
IGUAPE	SP	Interior 2	Sudeste	3
ILHA COMPRIDA	SP	Interior 2	Sudeste	3
ILHA SOLTEIRA	SP	Interior 2	Sudeste	3
ILHABELA	SP	Interior 2	Sudeste	3
INDAIATUBA	SP	Interior 1	Sudeste	3
INDIANA	SP	Interior 2	Sudeste	3
INDIAPORA	SP	Interior 2	Sudeste	3
INUBIA PAULISTA	SP	Interior 2	Sudeste	3
IPAUSSU	SP	Interior 1	Sudeste	3
IPERO	SP	Interior 1	Sudeste	3
IPEUNA	SP	Interior 2	Sudeste	3
IPIGUA	SP	Interior 2	Sudeste	3
IPORANGA	SP	Interior 2	Sudeste	3
IPUA	SP	Interior 1	Sudeste	3
IRACEMAPOLIS	SP	Interior 2	Sudeste	3
IRAPUA	SP	Interior 2	Sudeste	3
IRAPURU	SP	Interior 2	Sudeste	3
ITABERA	SP	Interior 2	Sudeste	3
ITAI	SP	Interior 2	Sudeste	3
ITAJOBI	SP	Interior 2	Sudeste	3
ITAJU	SP	Interior 2	Sudeste	3
ITANHAEM	SP	Interior 2	Sudeste	3
ITAOCA	SP	Interior 2	Sudeste	3
ITAPECERICA DA SERRA	SP	Interior 2	Sudeste	3
ITAPETININGA	SP	Interior 1	Sudeste	3
ITAPEVA	SP	Interior 2	Sudeste	3
ITAPEVI	SP	Interior 2	Sudeste	3
ITAPIRA	SP	Interior 1	Sudeste	3
ITAPIRAPUA PAULISTA	SP	Interior 2	Sudeste	3
ITAPOLIS	SP	Interior 2	Sudeste	3
ITAPORANGA	SP	Interior 2	Sudeste	3
ITAPUI	SP	Interior 1	Sudeste	3
ITAPURA	SP	Interior 2	Sudeste	3
ITAQUAQUECETUBA	SP	Interior 2	Sudeste	3
ITARARE	SP	Interior 2	Sudeste	3
ITARIRI	SP	Interior 2	Sudeste	3
ITATIBA	SP	Interior 1	Sudeste	3
ITATINGA	SP	Interior 1	Sudeste	3
ITIRAPINA	SP	Interior 1	Sudeste	3
ITIRAPUA	SP	Interior 1	Sudeste	3
ITOBI	SP	Interior 1	Sudeste	3
ITU	SP	Interior 1	Sudeste	3
ITUPEVA	SP	Interior 1	Sudeste	3
ITUVERAVA	SP	Interior 1	Sudeste	3
JABORANDI	SP	Interior 1	Sudeste	3
JABOTICABAL	SP	Interior 1	Sudeste	3
JACAREI	SP	Interior 1	Sudeste	3
JACI	SP	Interior 1	Sudeste	3
JACUPIRANGA	SP	Interior 2	Sudeste	3
JAGUARIUNA	SP	Interior 2	Sudeste	3
JALES	SP	Interior 1	Sudeste	3
JAMBEIRO	SP	Interior 1	Sudeste	3
JANDIRA	SP	Interior 2	Sudeste	3
JARDINOPOLIS	SP	Interior 1	Sudeste	3
JARINU	SP	Interior 1	Sudeste	3
JAU	SP	Interior 1	Sudeste	3
JERIQUARA	SP	Interior 1	Sudeste	3
JOANOPOLIS	SP	Interior 2	Sudeste	3
JOAO RAMALHO	SP	Interior 1	Sudeste	3
JOSE BONIFACIO	SP	Interior 1	Sudeste	3
JULIO MESQUITA	SP	Interior 1	Sudeste	3
JUMIRIM	SP	Interior 2	Sudeste	3
JUNDIAI	SP	Interior 1	Sudeste	3
JUNQUEIROPOLIS	SP	Interior 2	Sudeste	3
JUQUIA	SP	Interior 2	Sudeste	3
JUQUITIBA	SP	Interior 2	Sudeste	3
LAGOINHA	SP	Interior 2	Sudeste	3
LARANJAL PAULISTA	SP	Interior 2	Sudeste	3
LAVINIA	SP	Interior 1	Sudeste	3
LAVRINHAS	SP	Interior 2	Sudeste	3
LEME	SP	Interior 1	Sudeste	3
LENCOIS PAULISTA	SP	Interior 1	Sudeste	3
LIMEIRA	SP	Interior 2	Sudeste	3
LINDOIA	SP	Interior 2	Sudeste	3
LINS	SP	Interior 1	Sudeste	3
LORENA	SP	Interior 1	Sudeste	3
LOURDES	SP	Interior 2	Sudeste	3
LOUVEIRA	SP	Interior 2	Sudeste	3
LUCELIA	SP	Interior 2	Sudeste	3
LUCIANOPOLIS	SP	Interior 2	Sudeste	3
LUIS ANTONIO	SP	Interior 1	Sudeste	3
LUIZIANIA	SP	Interior 2	Sudeste	3
LUPERCIO	SP	Interior 2	Sudeste	3
LUTECIA	SP	Interior 2	Sudeste	3
MACATUBA	SP	Interior 1	Sudeste	3
MACAUBAL	SP	Interior 2	Sudeste	3
MACEDONIA	SP	Interior 2	Sudeste	3
MAGDA	SP	Interior 2	Sudeste	3
MAIRINQUE	SP	Interior 2	Sudeste	3
MAIRIPORA	SP	Interior 2	Sudeste	3
MANDURI	SP	Interior 1	Sudeste	3
MARABA PAULISTA	SP	Interior 2	Sudeste	3
MARACAI	SP	Interior 2	Sudeste	3
MARAPOAMA	SP	Interior 2	Sudeste	3
MARIAPOLIS	SP	Interior 2	Sudeste	3
MARILIA	SP	Interior 1	Sudeste	3
MARINOPOLIS	SP	Interior 2	Sudeste	3
MARTINOPOLIS	SP	Interior 1	Sudeste	3
MATAO	SP	Interior 1	Sudeste	3
MAUA	SP	Interior 2	Sudeste	3
MENDONCA	SP	Interior 2	Sudeste	3
MERIDIANO	SP	Interior 2	Sudeste	3
MESOPOLIS	SP	Interior 2	Sudeste	3
MIGUELOPOLIS	SP	Interior 1	Sudeste	3
MINEIROS DO TIETE	SP	Interior 2	Sudeste	3
MIRA ESTRELA	SP	Interior 2	Sudeste	3
MIRACATU	SP	Interior 2	Sudeste	3
MIRANDOPOLIS	SP	Interior 1	Sudeste	3
MIRANTE DO PARANAPANEMA	SP	Interior 2	Sudeste	3
MIRASSOL	SP	Interior 1	Sudeste	3
MIRASSOLANDIA	SP	Interior 2	Sudeste	3
MOCOCA	SP	Interior 1	Sudeste	3
MOGI DAS CRUZES	SP	Interior 2	Sudeste	3
MOGI GUACU	SP	Interior 2	Sudeste	3
MOGI MIRIM	SP	Interior 2	Sudeste	3
MOMBUCA	SP	Interior 2	Sudeste	3
MONCOES	SP	Interior 2	Sudeste	3
MONGAGUA	SP	Interior 2	Sudeste	3
MONTE ALEGRE DO SUL	SP	Interior 1	Sudeste	3
MONTE ALTO	SP	Interior 1	Sudeste	3
MONTE APRAZIVEL	SP	Interior 2	Sudeste	3
MONTE AZUL PAULISTA	SP	Interior 1	Sudeste	3
MONTE CASTELO	SP	Interior 2	Sudeste	3
MONTE MOR	SP	Interior 1	Sudeste	3
MONTEIRO LOBATO	SP	Interior 2	Sudeste	3
MORRO AGUDO	SP	Interior 1	Sudeste	3
MORUNGABA	SP	Interior 1	Sudeste	3
MOTUCA	SP	Interior 1	Sudeste	3
MURUTINGA DO SUL	SP	Interior 2	Sudeste	3
NANTES	SP	Interior 2	Sudeste	3
NARANDIBA	SP	Interior 2	Sudeste	3
NATIVIDADE DA SERRA	SP	Interior 2	Sudeste	3
NAZARE PAULISTA	SP	Interior 2	Sudeste	3
NEVES PAULISTA	SP	Interior 1	Sudeste	3
NHANDEARA	SP	Interior 1	Sudeste	3
NIPOA	SP	Interior 2	Sudeste	3
NOVA ALIANCA	SP	Interior 2	Sudeste	3
NOVA CAMPINA	SP	Interior 2	Sudeste	3
NOVA CANAA PAULISTA	SP	Interior 2	Sudeste	3
NOVA CASTILHO	SP	Interior 2	Sudeste	3
NOVA EUROPA	SP	Interior 2	Sudeste	3
NOVA GRANADA	SP	Interior 2	Sudeste	3
NOVA GUATAPORANGA	SP	Interior 2	Sudeste	3
NOVA INDEPENDENCIA	SP	Interior 2	Sudeste	3
NOVA LUZITANIA	SP	Interior 2	Sudeste	3
NOVA ODESSA	SP	Interior 1	Sudeste	3
NOVAIS	SP	Interior 2	Sudeste	3
NOVO HORIZONTE	SP	Interior 2	Sudeste	3
NUPORANGA	SP	Interior 1	Sudeste	3
OCAUCU	SP	Interior 2	Sudeste	3
OLEO	SP	Interior 2	Sudeste	3
OLIMPIA	SP	Interior 1	Sudeste	3
ONDA VERDE	SP	Interior 2	Sudeste	3
ORIENTE	SP	Interior 2	Sudeste	3
ORINDIUVA	SP	Interior 2	Sudeste	3
ORLANDIA	SP	Interior 1	Sudeste	3
OSASCO	SP	Interior 1	Sudeste	3
OSCAR BRESSANE	SP	Interior 2	Sudeste	3
OSVALDO CRUZ	SP	Interior 1	Sudeste	3
OURINHOS	SP	Interior 1	Sudeste	3
OURO VERDE	SP	Interior 2	Sudeste	3
OUROESTE	SP	Interior 2	Sudeste	3
PACAEMBU	SP	Interior 2	Sudeste	3
PALESTINA	SP	Interior 2	Sudeste	3
PALMARES PAULISTA	SP	Interior 1	Sudeste	3
PALMEIRA D OESTE	SP	Interior 2	Sudeste	3
PALMITAL	SP	Interior 1	Sudeste	3
PANORAMA	SP	Interior 2	Sudeste	3
PARAGUACU PAULISTA	SP	Interior 1	Sudeste	3
PARAIBUNA	SP	Interior 1	Sudeste	3
PARAISO	SP	Interior 2	Sudeste	3
PARANAPANEMA	SP	Interior 2	Sudeste	3
PARANAPUA	SP	Interior 2	Sudeste	3
PARAPUA	SP	Interior 2	Sudeste	3
PARDINHO	SP	Interior 2	Sudeste	3
PARIQUERA-ACU	SP	Interior 2	Sudeste	3
PARISI	SP	Interior 2	Sudeste	3
PATROCINIO PAULISTA	SP	Interior 1	Sudeste	3
PAULICEIA	SP	Interior 2	Sudeste	3
PAULINIA	SP	Interior 1	Sudeste	3
PAULISTANIA	SP	Interior 2	Sudeste	3
PAULO DE FARIA	SP	Interior 2	Sudeste	3
PEDERNEIRAS	SP	Interior 1	Sudeste	3
PEDRA BELA	SP	Interior 2	Sudeste	3
PEDRANOPOLIS	SP	Interior 2	Sudeste	3
PEDREGULHO	SP	Interior 1	Sudeste	3
PEDREIRA	SP	Interior 1	Sudeste	3
PEDRINHAS PAULISTA	SP	Interior 2	Sudeste	3
PEDRO DE TOLEDO	SP	Interior 2	Sudeste	3
PENAPOLIS	SP	Interior 1	Sudeste	3
PEREIRA BARRETO	SP	Interior 2	Sudeste	3
PEREIRAS	SP	Interior 2	Sudeste	3
PERUIBE	SP	Interior 2	Sudeste	3
PIACATU	SP	Interior 2	Sudeste	3
PIEDADE	SP	Interior 1	Sudeste	3
PILAR DO SUL	SP	Interior 1	Sudeste	3
PINDAMONHANGABA	SP	Interior 1	Sudeste	3
PINDORAMA	SP	Interior 2	Sudeste	3
PINHALZINHO	SP	Interior 1	Sudeste	3
PIQUEROBI	SP	Interior 2	Sudeste	3
PIQUETE	SP	Interior 2	Sudeste	3
PIRACAIA	SP	Interior 2	Sudeste	3
PIRACICABA	SP	Interior 1	Sudeste	3
PIRAJU	SP	Interior 2	Sudeste	3
PIRAJUI	SP	Interior 1	Sudeste	3
PIRANGI	SP	Interior 2	Sudeste	3
PIRAPORA DO BOM JESUS	SP	Interior 2	Sudeste	3
PIRAPOZINHO	SP	Interior 1	Sudeste	3
PIRASSUNUNGA	SP	Interior 1	Sudeste	3
PIRATININGA	SP	Interior 1	Sudeste	3
PITANGUEIRAS	SP	Interior 1	Sudeste	3
PLANALTO	SP	Interior 2	Sudeste	3
PLATINA	SP	Interior 2	Sudeste	3
POA	SP	Interior 2	Sudeste	3
POLONI	SP	Interior 2	Sudeste	3
POMPEIA	SP	Interior 1	Sudeste	3
PONGAI	SP	Interior 2	Sudeste	3
PONTAL	SP	Interior 1	Sudeste	3
PONTALINDA	SP	Interior 2	Sudeste	3
PONTES GESTAL	SP	Interior 2	Sudeste	3
POPULINA	SP	Interior 2	Sudeste	3
PORANGABA	SP	Interior 2	Sudeste	3
PORTO FELIZ	SP	Interior 2	Sudeste	3
PORTO FERREIRA	SP	Interior 1	Sudeste	3
POTIM	SP	Interior 1	Sudeste	3
POTIRENDABA	SP	Interior 1	Sudeste	3
PRACINHA	SP	Interior 2	Sudeste	3
PRADOPOLIS	SP	Interior 1	Sudeste	3
PRAIA GRANDE	SP	Interior 2	Sudeste	3
PRATANIA	SP	Interior 2	Sudeste	3
PRESIDENTE ALVES	SP	Interior 1	Sudeste	3
PRESIDENTE BERNARDES	SP	Interior 1	Sudeste	3
PRESIDENTE EPITACIO	SP	Interior 2	Sudeste	3
PRESIDENTE PRUDENTE	SP	Interior 1	Sudeste	3
PRESIDENTE VENCESLAU	SP	Interior 1	Sudeste	3
PROMISSAO	SP	Interior 1	Sudeste	3
QUADRA	SP	Interior 2	Sudeste	3
QUATA	SP	Interior 2	Sudeste	3
QUEIROZ	SP	Interior 2	Sudeste	3
QUELUZ	SP	Interior 2	Sudeste	3
QUINTANA	SP	Interior 2	Sudeste	3
RAFARD	SP	Interior 2	Sudeste	3
RANCHARIA	SP	Interior 1	Sudeste	3
REDENCAO DA SERRA	SP	Interior 2	Sudeste	3
REGENTE FEIJO	SP	Interior 1	Sudeste	3
REGINOPOLIS	SP	Interior 1	Sudeste	3
REGISTRO	SP	Interior 2	Sudeste	3
RESTINGA	SP	Interior 1	Sudeste	3
RIBEIRA	SP	Interior 2	Sudeste	3
RIBEIRAO BONITO	SP	Interior 2	Sudeste	3
RIBEIRAO BRANCO	SP	Interior 2	Sudeste	3
RIBEIRAO CORRENTE	SP	Interior 1	Sudeste	3
RIBEIRAO DO SUL	SP	Interior 2	Sudeste	3
RIBEIRAO DOS INDIOS	SP	Interior 2	Sudeste	3
RIBEIRAO GRANDE	SP	Interior 2	Sudeste	3
RIBEIRAO PIRES	SP	Interior 2	Sudeste	3
RIBEIRAO PRETO	SP	Capital	Sudeste	1
RIFAINA	SP	Interior 2	Sudeste	3
RINCAO	SP	Interior 1	Sudeste	3
RINOPOLIS	SP	Interior 2	Sudeste	3
RIO CLARO	SP	Interior 1	Sudeste	3
RIO DAS PEDRAS	SP	Interior 2	Sudeste	3
RIO GRANDE DA SERRA	SP	Interior 2	Sudeste	3
RIOLANDIA	SP	Interior 2	Sudeste	3
RIVERSUL	SP	Interior 2	Sudeste	3
ROSANA	SP	Interior 2	Sudeste	3
ROSEIRA	SP	Interior 1	Sudeste	3
RUBIACEA	SP	Interior 2	Sudeste	3
RUBINEIA	SP	Interior 2	Sudeste	3
SABINO	SP	Interior 2	Sudeste	3
SAGRES	SP	Interior 2	Sudeste	3
SALES	SP	Interior 2	Sudeste	3
SALES OLIVEIRA	SP	Interior 1	Sudeste	3
SALESOPOLIS	SP	Interior 2	Sudeste	3
SALMOURAO	SP	Interior 2	Sudeste	3
SALTINHO	SP	Interior 2	Sudeste	3
SALTO	SP	Interior 2	Sudeste	3
SALTO DE PIRAPORA	SP	Interior 1	Sudeste	3
SALTO GRANDE	SP	Interior 2	Sudeste	3
SANDOVALINA	SP	Interior 2	Sudeste	3
SANTA ADELIA	SP	Interior 2	Sudeste	3
SANTA ALBERTINA	SP	Interior 2	Sudeste	3
SANTA BARBARA D OESTE	SP	Interior 2	Sudeste	3
SANTA BRANCA	SP	Interior 2	Sudeste	3
SANTA CLARA D OESTE	SP	Interior 2	Sudeste	3
SANTA CRUZ DA CONCEICAO	SP	Interior 1	Sudeste	3
SANTA CRUZ DA ESPERANCA	SP	Interior 1	Sudeste	3
SANTA CRUZ DAS PALMEIRAS	SP	Interior 1	Sudeste	3
SANTA CRUZ DO RIO PARDO	SP	Interior 1	Sudeste	3
SANTA ERNESTINA	SP	Interior 1	Sudeste	3
SANTA FE DO SUL	SP	Interior 2	Sudeste	3
SANTA GERTRUDES	SP	Interior 2	Sudeste	3
SANTA ISABEL	SP	Interior 1	Sudeste	3
SANTA LUCIA	SP	Interior 1	Sudeste	3
SANTA MARIA DA SERRA	SP	Interior 2	Sudeste	3
SANTA MERCEDES	SP	Interior 2	Sudeste	3
SANTA RITA DO PASSA QUATRO	SP	Interior 1	Sudeste	3
SANTA RITA D OESTE	SP	Interior 2	Sudeste	3
SANTA ROSA DE VITERBO	SP	Interior 1	Sudeste	3
SANTA SALETE	SP	Interior 2	Sudeste	3
SANTANA DA PONTE PENSA	SP	Interior 2	Sudeste	3
SANTANA DE PARNAIBA	SP	Interior 2	Sudeste	3
SANTO ANASTACIO	SP	Interior 1	Sudeste	3
SANTO ANDRE	SP	Interior 1	Sudeste	3
SANTO ANTONIO DA ALEGRIA	SP	Interior 1	Sudeste	3
SANTO ANTONIO DE POSSE	SP	Interior 1	Sudeste	3
SANTO ANTONIO DO ARACANGUA	SP	Interior 2	Sudeste	3
SANTO ANTONIO DO JARDIM	SP	Interior 2	Sudeste	3
SANTO ANTONIO DO PINHAL	SP	Interior 2	Sudeste	3
SANTO EXPEDITO	SP	Interior 2	Sudeste	3
SANTOPOLIS DO AGUAPEI	SP	Interior 2	Sudeste	3
SANTOS	SP	Interior 2	Sudeste	3
SAO BENTO DO SAPUCAI	SP	Interior 2	Sudeste	3
SAO BERNARDO DO CAMPO	SP	Interior 1	Sudeste	3
SAO CAETANO DO SUL	SP	Interior 1	Sudeste	3
SAO CARLOS	SP	Interior 1	Sudeste	3
SAO FRANCISCO	SP	Interior 2	Sudeste	3
SAO JOAO DA BOA VISTA	SP	Interior 1	Sudeste	3
SAO JOAO DAS DUAS PONTES	SP	Interior 2	Sudeste	3
SAO JOAO DE IRACEMA	SP	Interior 2	Sudeste	3
SAO JOAO DO PAU D ALHO	SP	Interior 2	Sudeste	3
SAO JOAQUIM DA BARRA	SP	Interior 1	Sudeste	3
SAO JOSE DA BELA VISTA	SP	Interior 1	Sudeste	3
SAO JOSE DO BARREIRO	SP	Interior 2	Sudeste	3
SAO JOSE DO RIO PARDO	SP	Interior 1	Sudeste	3
SAO JOSE DO RIO PRETO	SP	Sao Jose do Rio Preto	Sudeste	Sob Consulta
SAO JOSE DOS CAMPOS	SP	Interior 1	Sudeste	3
SAO LOURENCO DA SERRA	SP	Interior 2	Sudeste	3
SAO LUIS DO PARAITINGA	SP	Interior 2	Sudeste	3
SAO MANUEL	SP	Interior 1	Sudeste	3
SAO MIGUEL ARCANJO	SP	Interior 1	Sudeste	3
SAO PAULO	SP	Capital	Sudeste	1
SAO PEDRO	SP	Interior 2	Sudeste	3
SAO PEDRO DO TURVO	SP	Interior 1	Sudeste	3
SAO ROQUE	SP	Interior 2	Sudeste	3
SAO SEBASTIAO	SP	Interior 1	Sudeste	3
SAO SEBASTIAO DA GRAMA	SP	Interior 1	Sudeste	3
SAO SIMAO	SP	Interior 1	Sudeste	3
SAO VICENTE	SP	Interior 2	Sudeste	3
SARAPUI	SP	Interior 1	Sudeste	3
SARUTAIA	SP	Interior 2	Sudeste	3
SEBASTIANOPOLIS DO SUL	SP	Interior 2	Sudeste	3
SERRA AZUL	SP	Interior 1	Sudeste	3
SERRA NEGRA	SP	Interior 2	Sudeste	3
SERRANA	SP	Interior 1	Sudeste	3
SERTAOZINHO	SP	Interior 1	Sudeste	3
SETE BARRAS	SP	Interior 2	Sudeste	3
SEVERINIA	SP	Interior 1	Sudeste	3
SILVEIRAS	SP	Interior 2	Sudeste	3
SOCORRO	SP	Interior 2	Sudeste	3
SOROCABA	SP	Interior 1	Sudeste	3
SUD MENNUCCI	SP	Interior 2	Sudeste	3
SUMARE	SP	Interior 1	Sudeste	3
SUZANAPOLIS	SP	Interior 2	Sudeste	3
SUZANO	SP	Interior 2	Sudeste	3
TABAPUA	SP	Interior 2	Sudeste	3
TABATINGA	SP	Interior 2	Sudeste	3
TABOAO DA SERRA	SP	Interior 1	Sudeste	3
TACIBA	SP	Interior 2	Sudeste	3
TAGUAI	SP	Interior 2	Sudeste	3
TAIACU	SP	Interior 1	Sudeste	3
TAIUVA	SP	Interior 1	Sudeste	3
TAMBAU	SP	Interior 1	Sudeste	3
TANABI	SP	Interior 1	Sudeste	3
TAPIRAI	SP	Interior 2	Sudeste	3
TAPIRATIBA	SP	Interior 1	Sudeste	3
TAQUARAL	SP	Interior 1	Sudeste	3
TAQUARITINGA	SP	Interior 1	Sudeste	3
TAQUARITUBA	SP	Interior 2	Sudeste	3
TAQUARIVAI	SP	Interior 2	Sudeste	3
TARABAI	SP	Interior 2	Sudeste	3
TARUMA	SP	Interior 1	Sudeste	3
TATUI	SP	Interior 1	Sudeste	3
TAUBATE	SP	Interior 1	Sudeste	3
TEJUPA	SP	Interior 2	Sudeste	3
TEODORO SAMPAIO	SP	Interior 2	Sudeste	3
TERRA ROXA	SP	Interior 1	Sudeste	3
TIETE	SP	Interior 2	Sudeste	3
TIMBURI	SP	Interior 2	Sudeste	3
TORRE DE PEDRA	SP	Interior 2	Sudeste	3
TORRINHA	SP	Interior 2	Sudeste	3
TRABIJU	SP	Interior 2	Sudeste	3
TREMEMBE	SP	Interior 1	Sudeste	3
TRES FRONTEIRAS	SP	Interior 2	Sudeste	3
TUIUTI	SP	Interior 2	Sudeste	3
TUPA	SP	Interior 1	Sudeste	3
TUPI PAULISTA	SP	Interior 2	Sudeste	3
TURIUBA	SP	Interior 2	Sudeste	3
TURMALINA	SP	Interior 2	Sudeste	3
UBARANA	SP	Interior 1	Sudeste	3
UBATUBA	SP	Interior 1	Sudeste	3
UBIRAJARA	SP	Interior 2	Sudeste	3
UCHOA	SP	Interior 1	Sudeste	3
UNIAO PAULISTA	SP	Interior 2	Sudeste	3
URANIA	SP	Interior 2	Sudeste	3
URU	SP	Interior 2	Sudeste	3
URUPES	SP	Interior 1	Sudeste	3
VALENTIM GENTIL	SP	Interior 1	Sudeste	3
VALINHOS	SP	Interior 1	Sudeste	3
VALPARAISO	SP	Interior 1	Sudeste	3
VARGEM	SP	Interior 2	Sudeste	3
VARGEM GRANDE DO SUL	SP	Interior 1	Sudeste	3
VARGEM GRANDE PAULISTA	SP	Interior 2	Sudeste	3
VARZEA PAULISTA	SP	Interior 2	Sudeste	3
VERA CRUZ	SP	Interior 2	Sudeste	3
VINHEDO	SP	Interior 1	Sudeste	3
VIRADOURO	SP	Interior 1	Sudeste	3
VISTA ALEGRE DO ALTO	SP	Interior 1	Sudeste	3
VITORIA BRASIL	SP	Interior 2	Sudeste	3
VOTORANTIM	SP	Interior 1	Sudeste	3
VOTUPORANGA	SP	Interior 1	Sudeste	3
ZACARIAS	SP	Interior 2	Sudeste	3
ABREULANDIA	TO	Interior 1	Norte	10
AGUIARNOPOLIS	TO	Sob Consulta	Norte	Sob Consulta
ALIANÇA DO TOCANTINS	TO	Interior 1	Norte	10
ALMAS	TO	Interior 2	Norte	10
ALVORADA	TO	Sob Consulta	Norte	Sob Consulta
ANANAS	TO	Sob Consulta	Norte	Sob Consulta
ANGICO	TO	Sob Consulta	Norte	Sob Consulta
APARECIDA DO RIO NEGRO	TO	Interior 1	Norte	10
ARAGOMINAS	TO	Sob Consulta	Norte	Sob Consulta
ARAGUACEMA	TO	Interior 2	Norte	10
ARAGUACU	TO	Sob Consulta	Norte	Sob Consulta
ARAGUAINA	TO	Interior 1	Norte	10
ARAGUANA	TO	Sob Consulta	Norte	Sob Consulta
ARAGUATINS	TO	Sob Consulta	Norte	Sob Consulta
ARAPOEMA	TO	Sob Consulta	Norte	Sob Consulta
ARRAIAS	TO	Sob Consulta	Norte	Sob Consulta
AUGUSTINOPOLIS	TO	Sob Consulta	Norte	Sob Consulta
AURORA DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
AXIXA DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
BABACULANDIA	TO	Sob Consulta	Norte	Sob Consulta
BANDEIRANTES DO TOCANTINS	TO	Interior 2	Norte	10
BARRA DO OURO	TO	Sob Consulta	Norte	Sob Consulta
BARROLANDIA	TO	Interior 1	Norte	10
BERNARDO SAYAO	TO	Sob Consulta	Norte	Sob Consulta
BOM JESUS DO TOCANTINS	TO	Interior 2	Norte	10
BRASILÂNDIA	TO	Interior 1	Norte	10
BREJINHO DE NAZARÉ	TO	Interior 1	Norte	10
BURITI DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
CACHOEIRINHA	TO	Sob Consulta	Norte	Sob Consulta
CAMPOS LINDOS	TO	Sob Consulta	Norte	Sob Consulta
CARIRI DO TOCANTINS	TO	Interior 2	Norte	10
CARMOLANDIA	TO	Sob Consulta	Norte	Sob Consulta
CARRASCO BONITO	TO	Sob Consulta	Norte	Sob Consulta
CASEARA	TO	Interior 2	Norte	10
CENTENARIO	TO	Interior 2	Norte	10
CHAPADA DA NATIVIDADE	TO	Interior 2	Norte	10
CHAPADA DE AREIA	TO	Interior 1	Norte	10
COLINAS DO TOCANTINS	TO	Interior 1	Norte	10
COLMEIA	TO	Interior 2	Norte	10
COMBINADO	TO	Sob Consulta	Norte	Sob Consulta
CONCEIÇÃO DO TOCANTINS	TO	Interior 2	Norte	10
COUTO MAGALHAES	TO	Interior 2	Norte	10
CRISTALANDIA	TO	Sob Consulta	Norte	Sob Consulta
CRIXAS DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
DARCINOPOLIS	TO	Sob Consulta	Norte	Sob Consulta
DIANOPOLIS	TO	Sob Consulta	Norte	Sob Consulta
DIVINÓPOLIS DO TOCANTINS	TO	Interior 1	Norte	10
DOIS IRMAOS DO TOCANTINS	TO	Interior 2	Norte	10
DUERÉ	TO	Interior 2	Norte	10
ESPERANTINA	TO	Sob Consulta	Norte	Sob Consulta
FÁTIMA	TO	Interior 1	Norte	10
FIGUEIROPOLIS	TO	Interior 2	Norte	10
FILADELFIA	TO	Sob Consulta	Norte	Sob Consulta
FORMOSO DO ARAGUAIA	TO	Sob Consulta	Norte	Sob Consulta
FORTALEZA DO TABOCÃO	TO	Interior 1	Norte	10
GOIANORTE	TO	Interior 2	Norte	10
GOIATINS	TO	Sob Consulta	Norte	Sob Consulta
GUARAI	TO	Interior 1	Norte	10
GURUPI	TO	Interior 1	Norte	10
IPUEIRAS	TO	Interior 1	Norte	10
ITACAJA	TO	Interior 2	Norte	10
ITAGUATINS	TO	Sob Consulta	Norte	Sob Consulta
ITAPIRATINS	TO	Interior 2	Norte	10
ITAPORÃ DO TOCANTINS	TO	Interior 2	Norte	10
JAU DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
JUARINA	TO	Sob Consulta	Norte	Sob Consulta
LAGOA DA CONFUSÃO	TO	Interior 2	Norte	10
LAGOA DO TOCANTINS	TO	Interior 1	Norte	10
LAJEADO	TO	Interior 1	Norte	10
LAVANDEIRA	TO	Sob Consulta	Norte	Sob Consulta
LIZARDA	TO	Sob Consulta	Norte	Sob Consulta
LUZINOPOLIS	TO	Sob Consulta	Norte	Sob Consulta
MARIANOPOLIS DO TOCANTINS	TO	Interior 2	Norte	10
MATEIROS	TO	Sob Consulta	Norte	Sob Consulta
MAURILANDIA DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
MIRACEMA DO TOCANTINS	TO	Interior 1	Norte	10
MIRANORTE	TO	Interior 1	Norte	10
MONTE DO CARMO	TO	Interior 1	Norte	10
MONTE SANTO DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
MURICILANDIA	TO	Sob Consulta	Norte	Sob Consulta
NATIVIDADE	TO	Interior 2	Norte	10
NAZARE	TO	Sob Consulta	Norte	Sob Consulta
NOVA OLINDA	TO	Interior 1	Norte	10
NOVA ROSALÂNDIA	TO	Interior 1	Norte	10
NOVO ACORDO	TO	Interior 1	Norte	10
NOVO ALEGRE	TO	Sob Consulta	Norte	Sob Consulta
NOVO JARDIM	TO	Sob Consulta	Norte	Sob Consulta
OLIVEIRA DE FATIMA	TO	Interior 1	Norte	10
PALMAS	TO	Capital	Norte	7
PALMEIRANTE	TO	Sob Consulta	Norte	Sob Consulta
PALMEIRAS DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
PALMEIROPOLIS	TO	Sob Consulta	Norte	Sob Consulta
PARAÍSO DO TOCANTINS	TO	Interior 1	Norte	10
PARANA	TO	Sob Consulta	Norte	Sob Consulta
PAU D ARCO	TO	Sob Consulta	Norte	Sob Consulta
PEDRO AFONSO	TO	Interior 2	Norte	10
PEIXE	TO	Sob Consulta	Norte	Sob Consulta
PEQUIZEIRO	TO	Interior 2	Norte	10
PINDORAMA DO TOCANTINS	TO	Interior 2	Norte	10
PIRAQUE	TO	Sob Consulta	Norte	Sob Consulta
PIUM	TO	Interior 1	Norte	10
PONTE ALTA DO BOM JESUS	TO	Sob Consulta	Norte	Sob Consulta
PONTE ALTA DO TOCANTINS	TO	Interior 2	Norte	10
PORTO ALEGRE DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
PORTO NACIONAL	TO	Interior 1	Norte	10
PRAIA NORTE	TO	Sob Consulta	Norte	Sob Consulta
PRESIDENTE KENNEDY	TO	Interior 1	Norte	10
PUGMIL	TO	Interior 1	Norte	10
RECURSOLANDIA	TO	Sob Consulta	Norte	Sob Consulta
RIACHINHO	TO	Sob Consulta	Norte	Sob Consulta
RIO DA CONCEICAO	TO	Sob Consulta	Norte	Sob Consulta
RIO DOS BOIS	TO	Interior 1	Norte	10
RIO SONO	TO	Interior 1	Norte	10
SAMPAIO	TO	Sob Consulta	Norte	Sob Consulta
SANDOLANDIA	TO	Sob Consulta	Norte	Sob Consulta
SANTA FE DO ARAGUAIA	TO	Sob Consulta	Norte	Sob Consulta
SANTA MARIA DO TOCANTINS	TO	Interior 2	Norte	10
SANTA RITA DO TOCANTINS	TO	Interior 1	Norte	10
SANTA ROSA DO TOCANTINS	TO	Interior 2	Norte	10
SANTA TEREZA DO TOCANTINS	TO	Interior 1	Norte	10
SANTA TEREZINHA DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
SAO BENTO DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
SAO FELIX DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
SAO MIGUEL DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
SAO SALVADOR DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
SAO SEBASTIAO DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
SÃO VALERIO DA NATIVIDADE	TO	Interior 2	Norte	10
SILVANOPOLIS	TO	Interior 1	Norte	10
SITIO NOVO DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
SUCUPIRA	TO	Sob Consulta	Norte	Sob Consulta
TAGUATINGA	TO	Sob Consulta	Norte	Sob Consulta
TAIPAS DO TOCANTINS	TO	Sob Consulta	Norte	Sob Consulta
TALISMA	TO	Sob Consulta	Norte	Sob Consulta
TOCANTINIA	TO	Interior 1	Norte	10
TOCANTINOPOLIS	TO	Sob Consulta	Norte	Sob Consulta
TUPIRAMA	TO	Interior 1	Norte	10
TUPIRATINS	TO	Interior 2	Norte	10
WANDERLANDIA	TO	Sob Consulta	Norte	Sob Consulta
XAMBIOA	TO	Sob Consulta	Norte	Sob Consulta`; 

        const parseData = (raw) => {
            return raw.split('\n').filter(l => l.trim()).map(line => {
                const parts = line.split('\t');
                return { cidade: parts[0], uf: parts[1], tipo: parts[2], regiao: parts[3], prazo: parts[4] };
            });
        };

        function App() {
            const data = useMemo(() => parseData(RAW_DATA), []);
            const [searchTerm, setSearchTerm] = useState('');
            const [selectedUf, setSelectedUf] = useState('');
            const [limit, setLimit] = useState(20);

            const ufs = Array.from(new Set(data.map(i => i.uf))).sort();

            const filteredData = data.filter(item => {
                const matchesSearch = item.cidade.toLowerCase().includes(searchTerm.toLowerCase());
                const matchesUf = selectedUf === '' || item.uf === selectedUf;
                return matchesSearch && matchesUf;
            });

            return (
                <div className="min-h-screen">
                    {/* Hero Section */}
                    <header className="relative h-[300px] flex items-center justify-center bg-slate-900 text-white overflow-hidden">
                        <div className="absolute inset-0 opacity-30">
                            <div className="absolute inset-0 bg-[url('https://www.transparenttextures.com/patterns/carbon-fibre.png')]"></div>
                        </div>
                        <div className="relative z-10 text-center px-6">
                            <div className="inline-flex items-center gap-2 bg-blue-600/20 border border-blue-500/30 px-4 py-2 rounded-full mb-6">
                                <Package size={16} className="text-blue-400" />
                                <span className="text-xs font-bold uppercase tracking-widest text-blue-400">Sistema Original Cobli</span>
                            </div>
                            <h1 className="text-4xl md:text-5xl font-black tracking-tighter mb-4">Calculadora de Prazos 2026</h1>
                            <p className="text-slate-400 max-w-xl mx-auto font-medium">Consulte o tempo estimado de entrega para operações nacionais.</p>
                        </div>
                    </header>

                    {/* Filtros */}
                    <main className="max-w-6xl mx-auto px-4 -mt-12 pb-20 relative z-20">
                        <div className="bg-white rounded-[2rem] shadow-2xl p-6 md:p-8 border border-slate-200 grid grid-cols-1 md:grid-cols-12 gap-4">
                            <div className="md:col-span-7 relative">
                                <Search className="absolute left-4 top-1/2 -translate-y-1/2 text-slate-400" size={20} />
                                <input 
                                    type="text" 
                                    placeholder="Digite o nome da cidade..."
                                    className="w-full pl-12 pr-4 py-4 bg-slate-50 border-2 border-slate-100 rounded-2xl focus:border-blue-600 outline-none font-bold transition-all"
                                    value={searchTerm}
                                    onChange={(e) => setSearchTerm(e.target.value)}
                                />
                            </div>
                            <div className="md:col-span-3">
                                <select 
                                    className="w-full px-4 py-4 bg-slate-50 border-2 border-slate-100 rounded-2xl focus:border-blue-600 outline-none font-bold text-slate-600 appearance-none cursor-pointer"
                                    value={selectedUf}
                                    onChange={(e) => setSelectedUf(e.target.value)}
                                >
                                    <option value="">Todos os Estados</option>
                                    {ufs.map(uf => <option key={uf} value={uf}>{uf}</option>)}
                                </select>
                            </div>
                            <button 
                                onClick={() => {setSearchTerm(''); setSelectedUf('');}}
                                className="md:col-span-2 bg-slate-900 text-white font-black rounded-2xl hover:bg-blue-600 transition-colors uppercase text-xs tracking-widest"
                            >
                                Limpar
                            </button>
                        </div>

                        {/* Tabela de Resultados */}
                        <div className="mt-10 bg-white rounded-[2rem] shadow-xl border border-slate-200 overflow-hidden">
                            <table className="w-full text-left">
                                <thead className="bg-slate-50 border-b border-slate-200">
                                    <tr>
                                        <th className="px-8 py-6 text-[10px] font-black uppercase tracking-widest text-slate-400">Destino</th>
                                        <th className="px-8 py-6 text-[10px] font-black uppercase tracking-widest text-slate-400 text-right">Prazo Estimado</th>
                                    </tr>
                                </thead>
                                <tbody className="divide-y divide-slate-100">
                                    {filteredData.slice(0, limit).map((item, idx) => (
                                        <tr key={idx} className="hover:bg-blue-50/50 transition-colors group">
                                            <td className="px-8 py-6">
                                                <div className="flex items-center gap-4">
                                                    <div className="w-10 h-10 bg-slate-100 rounded-xl flex items-center justify-center text-slate-400 group-hover:bg-blue-600 group-hover:text-white transition-all">
                                                        <MapPin size={18} />
                                                    </div>
                                                    <div>
                                                        <p className="font-extrabold text-slate-900 uppercase tracking-tight">{item.cidade}</p>
                                                        <p className="text-[10px] font-bold text-slate-400 uppercase">{item.uf} • {item.regiao}</p>
                                                    </div>
                                                </div>
                                            </td>
                                            <td className="px-8 py-6 text-right">
                                                <div className="inline-flex items-center gap-2 bg-blue-50 text-blue-700 px-4 py-2 rounded-xl border border-blue-100 font-black">
                                                    <Clock size={16} />
                                                    {item.prazo} Dias
                                                </div>
                                            </td>
                                        </tr>
                                    ))}
                                </tbody>
                            </table>
                            {filteredData.length > limit && (
                                <div className="p-8 text-center bg-slate-50/50 border-t border-slate-100">
                                    <button 
                                        onClick={() => setLimit(l => l + 20)}
                                        className="text-blue-600 font-black text-xs uppercase tracking-widest hover:text-blue-800 transition-colors"
                                    >
                                        Carregar mais resultados
                                    </button>
                                </div>
                            )}
                        </div>
                    </main>
                </div>
            );
        }

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>
