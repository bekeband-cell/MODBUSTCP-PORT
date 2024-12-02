# PsModbusTcp

rem Indítási paraméterek:
rem -o output directory default: ".\DATAS\" Az indítási könyvtár /DATAS alkönyvtára.
rem -c computername vagy IP address default: 172.30.10.244
rem -p portnumber default: 502 (MODBUS/TCP általánois port)
rem -g samplesec (1..6 minta per perc) default: 6 (6 minta per perc, azaz 10 sec-ként egy minta)
rem -a MODBUS address (0..254) default: 1 (MODBUS address a TCP-n belül)
rem -l samplechannels (1..8) default: 2 (Mintavételezési csatornák száma)
rem -j samplecount (2..30) default: 30 (Ennyi minta után trendel. Figyelembe kell venni az egy perc alatti minták számát is!!)
rem -d debug default: nincs (hibakeresési információk kiírása.)
rem FIGYELEM! A program indítás után esetleg sokat várhat az első adatbeolvasással, mert megvárja a következő 10-zel maradáktalanul osztható perc 0. másodpercét.
rem PL.: ha 12:16:55-kor indítjuk, akkor legközelebb 12:20:00-kor kezdi az adatgyűjtést és a samplesec és samplecount paramétereknek megfeleően legközelebb vagy
rem 20 másodperc múlva (samplesec = 6 : 10sec-ként 1 minta, samplecount = 2 : 2 mintánként trendelés, azaz 20 másodpercenként,
rem vagy a legnagyobb: samplesec = 1 (egy percenként minta) és samplecount = 30 (30 mintánként trend), azaz 30 percenként
rem Jelenleg a samplecount-nak megfelelő számú mintát lineárisan átlagolunk és azt az értéket trendeljük.
rem A kimenő fájl szerkezete: amennyiben a kimenő könyvtár nincs meg (és létrehozható), akkor létrehozzuk. A kimenő könyvtárba készül egy ÉÉÉÉHH nevű
rem alkönyvtár, amibe rendre a ÉÉÉÉHHNN.csv nevű fájl. Ez naponként, a könyvtár havonta létrehozódik és a megfelelő aznapi fájl íródik.
rem Amikor valami másolási, vagy adatkinyerési akciót kell végezni, akkor érdemes az előző napi fájlt megnyitni, mert az már biztosan nem íródik.
