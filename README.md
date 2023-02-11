# Berlin Termin Bot

## AWS EC2 Setup

[ - ] *t3.nano* failed.   Price: *$0.0052*

- [-] Running the selenium in *t2.medium* worked! Price  *$0.0464*
- t3a.micro worked only for selenium and finder. Not for elastic

- [x] **t3a.small**: Works

- t4g.micro was not available


Other recommandations
- t4g.small
- t4g.medium

![](ec2_price.png)



## How to dockerize


`docker build --tag 'yilmaznaslan/berlinterminfinder:latest' .`

docker build --tag yilmaznaslan/berlinterminfinder:latest --file DockerFileForDebian

docker build -t yilmaznaslan/berlinterminfinder:pi -f DockerfileForDebian .

`docker push yilmaznaslan/berlinterminfinder:latest`

`docker push yilmaznaslan/berlinterminfinder:pi`


`sudo docker run --name termifinder --network=termin yilmaznaslan/berlinterminfinder:latest`



docker login

docker push yilmaznaslan/berlinterminfinder:latest

# Setup
#COPY build/libs/berlinTerminFinder-1.0-SNAPSHOT-all.jar /opt/hello/

#EXPOSE 80
#WORKDIR /opt/hello
#CMD ["java", "-jar", "berlinTerminFinder-1.0-SNAPSHOT-all.jar"]


## ToDo's

- java.util.concurrent.TimeoutException error


# Root logger option
log4j.rootLogger=info, stdout, FILE
log=/logs

# Redirect log messages to console
log4j.appender.stdout=org.apache.log4j.ConsoleAppender
log4j.appender.stdout.Target=System.out
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=%d{yyyy-MM-dd HH:mm:ss} %-2p  %c{1} - %m%n

# Write log messages to log files
log4j.appender.FILE=org.apache.log4j.rolling.RollingFileAppender
log4j.appender.FILE.RollingPolicy=org.apache.log4j.rolling.TimeBasedRollingPolicy
log4j.appender.FILE.RollingPolicy.ActiveFileName=${log}/log-0.log
log4j.appender.FILE.RollingPolicy.FileNamePattern=${log}/log-%d{yyyy-MM-dd-HH_mm_ss}.log
log4j.appender.FILE.RollingPolicy.maxIndex=10000000
log4j.appender.FILE.TriggeringPolicy=org.apache.log4j.rolling.SizeBasedTriggeringPolicy
log4j.appender.FILE.TriggeringPolicy.MaxFileSize=1000000
log4j.appender.FILE.layout=org.apache.log4j.PatternLayout
log4j.appender.FILE.layout.ConversionPattern=%d{yyyy-MM-dd HH:mm:ss} %-5p %c{1} - %m%n



curl 'https://otv.verwalt-berlin.de/api/remote2/TerminBuchen/28c478a6-cf59-4f1d-8a84-74e610c4c52a/proceed?dswid=1419&suppressRenderOnChange=true' \
-H 'Accept: */*' \
-H 'Accept-Language: en,de-DE;q=0.9,de;q=0.8,en-DE;q=0.7,en-US;q=0.6' \
-H 'Connection: keep-alive' \
-H 'Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryBPnv6DTbATQruQcS' \
-H 'Cookie: SERVERID=frontend-1; otv_neu=689981eba202123fd8dec80cc900cb5b; JSESSIONID=rYF3crdgpUnl0vIQNaQcNcdYkhzzATGDPA6OJiXE.frontend-1; TS018ca6c6=01d33437f9cef9a46858765100ddb3128dcc14a4122caa73228223181736859722ce74142d48752c6e195119a1967db55805d3d4f1' \
-H 'Origin: https://otv.verwalt-berlin.de' \
-H 'Referer: https://otv.verwalt-berlin.de/ams/TerminBuchen/wizardng/28c478a6-cf59-4f1d-8a84-74e610c4c52a?dswid=1419&dsrid=225&st=2&v=1672087016092' \
-H 'Sec-Fetch-Dest: empty' \
-H 'Sec-Fetch-Mode: cors' \
-H 'Sec-Fetch-Site: same-origin' \
-H 'User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36' \
-H 'X-Requested-With: XMLHttpRequest' \
-H 'sec-ch-ua: "Not?A_Brand";v="8", "Chromium";v="108", "Google Chrome";v="108"' \
-H 'sec-ch-ua-mobile: ?0' \
-H 'sec-ch-ua-platform: "macOS"' \
--data-raw $'------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="applicationForm:managedForm"\r\n\r\napplicationForm:managedForm\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="frid"\r\n\r\n17145f03-e4bd-45cd-b2a4-8579a07f9297\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="lang"\r\n\r\nde\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="anliegen_auswahl_deutsch"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="anliegen_auswahl_andere"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="sammelfeld_konsulat"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="init_sprachauswahl"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="contrydatacsv"\r\n\r\nTürkei\u0021-163\u0021-nein\u0021-163-0\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="sel_staat"\r\n\r\n163\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="personenAnzahl_normal"\r\n\r\n1\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dokumente"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="personenAnzahl_mit_dokument"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="personenAnzahl_ohne_dokument"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="lebnBrMitFmly"\r\n\r\n2\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="fmlyMemNationality"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="angehoeriger_eu_ewr"\r\n\r\n163-0\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="sel_anliegensgruppe"\r\n\r\nx\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="sel_anliegenszweck"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="sel_service"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="enter_sachgebiet"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="level1"\r\n\r\n163-0-1\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="level2"\r\n\r\n163-0-1-3\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="level3"\r\n\r\n163-0-1-3-328338\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="aggregatedServices"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="selectedService"\r\n\r\n163-0-1-3-328338\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="swissSelectedService"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="serviceValidationElement"\r\n\r\nAufenthaltserlaubnis für eine Berufsausbildung (§ 16a)\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="accId"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="TAprozessID"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dienstleistungName"\r\n\r\nAufenthaltserlaubnis für eine Berufsausbildung (§ 16a)\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dienstleistung"\r\n\r\n328338\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="sachgebietName"\r\n\r\nReferat B 1 und B 2 +++ 2. und 3. Etage, Warteräume 204 und 303\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="clusterId"\r\n\r\n450\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="standortId"\r\n\r\n0\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="standortId1"\r\n\r\n0\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="targetVal"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dl_dienstleistung_ID"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="aufhenthaltnr_pflicht"\r\n\r\n0\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dl_dienstleister"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dl_dienstleistung_name"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="InfoBarrierefreiheit"\r\n\r\nDer Zugang zur Einrichtung ist Rollstuhlgerecht.Ein rollstuhlgerechter Aufzug ist vorhanden.Ein rollstuhlgerechtes WC ist vorhanden.\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="OEPNVInfo"\r\n\r\nU-Bahn: U 7 (Mierendorffplatz) Bus: M27 (Haltestelle Keplerstraße) \r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="Leistungsname"\r\n\r\nAufenthaltserlaubnis für eine Berufsausbildung\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="Leistungsbeschreibung"\r\n\r\nFür eine qualifizierte betriebliche oder schulische Berufsausbildung *kann* eine Aufenthaltserlaubnis erteilt und verlängert werden, wenn die Berufsausbildung zu einem anerkannten Abschluss führt.\r\n* Die Aufenthaltserlaubnis berechtigt zur Ausübung einer (von der Ausbildung unabhängigen) Beschäftigung von maximal 10 Stunden je Woche. Eine selbstständige Tätigkeit ist damit nicht gestattet.\r\n* Während der Ausbildung kann in der Regel keine andere Aufenthaltserlaubnis erteilt werden, außer es besteht ein gesetzlicher Anspruch.\r\n* Nach erfolgreichem Abschluss der Berufsausbildung kann die Aufenthaltserlaubnis für bis zu 12 Monate verlängert werden. In dieser Zeit kann dann ein Arbeitsplatz gesucht werden. Der Arbeitsplatz muss der abgeschlossenen Berufsausbildung angemessen sein.\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="Gebuehrenrahmen"\r\n\r\n* 100,00 Euro: für die erstmalige Erteilung der Aufenthaltserlaubnis\r\n* 96,00 Euro: für die Verlängerung der Aufenthaltserlaubnis\r\nTürkische Staatsangehörige (sowohl für die erste Erteilung als auch für die Verlängerung):\r\n* 22,80 Euro: bis zum vollendeten 24. Lebensjahr\r\n* 37,00 Euro: ab dem vollendeten 24. Lebensjahr\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="benoetigteUnterlagen"\r\n\r\nGültiger Pass |1 aktuelles biometrisches Foto - 35mm x 45mm, Frontalaufnahme mit neutralem Gesichtsausdruck und geschlossenem Mund gerade in die Kamera blickend, heller Hintergrund (https://www.berlin.de/labo/_assets/kraftfahrzeugwesen/foto-mustertafel.pdf)|Formular Antrag auf Erteilung eines Aufenthaltstitels (ausgefüllt) - Nur bei erstmaliger Beantragung einer Aufenthaltserlaubnis erforderlich. (unter Formulare)|Bei einer betrieblichen Ausbildung: Formular &quot;Erklärung zum Beschäftigungsverhältnis (Stellenbeschreibung)&quot; - bitte ausgefüllt (unter Formulare)|Bei einer betrieblichen Ausbildung: - Ausbildungsvertrag mit Eintragung in die Lehrlingsrolle, eventuell Vertrag über vorgeschalteten berufsbezogenen Sprachkurs|Bei einer schulischen Ausbildung: Schulvertrag - Es genügt auch die Vorlage einer aktuellen Aufnahmeentscheidung im Sinne der geltenden Ausbildungs- und Prüfungsverordnung, sofern daraus der Berufsabschluss und die Ausbildungsdauer hervorgehen.|Nachweis zum Lebensunterhalt (im Original) - Als Nachweise für den gesicherten Lebensunterhalt während der Ausbildung (siehe Abschnitt "Voraussetzungen") genügen:\r\n* eigene Mittel, wie zum Beispiel das Einkommen aus der Ausbildung,\r\nergänzend:\r\n* Sperrkonto bei einer deutschen Bank, \r\n* Verpflichtungserklärung auf amtlichem Vordruck, \r\n* notariell beglaubigte Erklärung der Eltern, für die Dauer der Ausbildung den Lebensunterhalt zu sichern, zusammen mit Nachweisen über das Einkommen der Eltern in den letzten sechs Monaten oder \r\n* Bewilligung von Leistungen nach dem BAföG|Krankenversicherung - Der Nachweis eines gesicherten Lebensunterhalts umfasst auch einen ausreichenden Krankenversicherungsschutz. Gesetzlich Krankenversicherte sind ausreichend versichert. Privat Krankenversicherte müssen auf Art und Umfang ihrer Krankenversicherung achten. Für mehr Informationen dazu bitte das Merkblatt lesen.|Nachweis über den Hauptwohnsitz in Berlin - * Bescheinigung über die Anmeldung der Wohnung (Meldebestätigung) \r\n*oder*\r\n* Mietvertrag und Einzugsbestätigung des Vermieters\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="Besonderheiten"\r\n\r\nQualifizierte Berufsausbildung - Die Berufsausbildung muss zu einem staatlich anerkannten oder vergleichbar geregelten Berufsabschluss führen.|Ausreichende Sprachkenntnisse - Die für die Berufsausbildung erforderlichen Sprachkenntnisse müssen vorhanden sein. In der Regel sind das ausreichende deutsche Sprachkenntnisse auf dem Niveau B 1 des Gemeinsamen Europäischen Referenzrahmens für Sprachen. \r\nEine Ausnahme davon ist nur möglich, wenn die Ausbildungseinrichtung \r\n* während der Ausbildung eine individuelle Sprachförderung gewährt oder\r\n* bestätigt, dass die Sprachkenntnisse für die Absolvierung der qualifizierten Berufsausbildung ausreichend sind.|Bei einer betrieblichen Ausbildung: Zustimmung der Bundesagentur für Arbeit - Die Aufenthaltserlaubnis kann für eine betriebliche Ausbildung in der Regel nur erteilt werden, wenn die Bundesagentur für Arbeit zugestimmt hat.|Bei schulischer, fachtheoretischer Berufsausbildung: Anerkannter Bildungsträger - Eine schulische Ausbildung kann nur an Berufsfachschulen oder privaten, staatlich anerkannten Ergänzungsschulen absolviert werden.|Gesicherter Lebensunterhalt - Der Lebensunterhalt muss während der Ausbildung aus eigenen Mitteln oder durch Dritte gesichert sein. Monatlich müssen dafür mindestens 836,00 Euro zur Verfügung stehen.\r\nSofern für die Ausbildung Gebühren entstehen, erhöht sich der monatliche Mindestbetrag entsprechend.|Hauptwohnsitz in Berlin - |Persönliche Vorsprache ist erforderlich - Die Vorsprache sollte möglichst mit Termin erfolgen\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="rechtlicheGrundlage"\r\n\r\nAufenthaltsgesetz (AufenthG) § 16a (https://www.gesetze-im-internet.de/aufenthg_2004/__16a.html)\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="Organisationsname"\r\n\r\n\r\n                LEA, Keplerstr.\r\n            \r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dl_str"\r\n\r\nKeplerstraße\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dl_nr"\r\n\r\n2\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dl_plz"\r\n\r\n10589\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dl_ort"\r\n\r\nBerlin\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="dl_response_error"\r\n\r\n0\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="sel_staat_hidden_val"\r\n\r\n163\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="angehoeriger_eu_ewr_hidden_val"\r\n\r\n163-0\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="anliegen_nr_hidden"\r\n\r\n1\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="countrySelected"\r\n\r\n1\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="country998"\r\n\r\n0\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="personen_anzahl_hidden_val"\r\n\r\n1\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="selectedService"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="xima-9875-required"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="xfc-pp-elementslist"\r\n\r\nanliegen_auswahl_deutsch,anliegen_auswahl_andere,sammelfeld_konsulat,init_sprachauswahl,contrydatacsv,sel_staat,personenAnzahl_normal,dokumente,personenAnzahl_mit_dokument,personenAnzahl_ohne_dokument,lebnBrMitFmly,fmlyMemNationality,angehoeriger_eu_ewr,sel_anliegensgruppe,sel_anliegenszweck,sel_service,enter_sachgebiet,aggregatedServices,selectedService,swissSelectedService,level1Val,level2Val,level3Val,serviceValidationElement,accId,TAprozessID,dienstleistungName,dienstleistung,sachgebietName,clusterId,standortId,standortId1,targetVal,dl_dienstleistung_ID,aufhenthaltnr_pflicht,dl_dienstleister,dl_dienstleistung_name,InfoBarrierefreiheit,OEPNVInfo,Leistungsname,Leistungsbeschreibung,Gebuehrenrahmen,benoetigteUnterlagen,Besonderheiten,rechtlicheGrundlage,Organisationsname,dl_str,dl_nr,dl_plz,dl_ort,dl_response_error,sel_staat_hidden_val,angehoeriger_eu_ewr_hidden_val,anliegen_nr_hidden,countrySelected,country998,personen_anzahl_hidden_val,selectedService\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="error_code"\r\n\r\n;57f;:9df08i0<i7g4;0;d077:9h347f8fd5\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="clientWizardStep"\r\n\r\nMl9BbmxpZWdlbnNrbMOkcnVuZw==\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="applicationForm:managedForm:j_idt314"\r\n\r\n\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="javax.faces.ViewState"\r\n\r\n4890948359753698854:9060295820573569071\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS\r\nContent-Disposition: form-data; name="javax.faces.ClientWindow"\r\n\r\n1419\r\n------WebKitFormBoundaryBPnv6DTbATQruQcS--\r\n' \
--compressed


docker exec -ti 18b3d6e1415b sh
