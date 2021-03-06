# Szervíz és orvosi robotika 

követelmények:
- zh 20%
  - lehet házit írni és akkor nem kell ZH, házik neptun üzenetben
    - sebészeti eszközök szegmentálása, synthetic miccai adatsor alapján
    - sebészeti eszközök szegmenseinek szegmentálása ugyanazon az adadsoron <- nehéz feladat
    - sebészeti eszközök 6D pozícióbecslése <- matekos feladat, 2D kameraképen megmondnai az eszközök 3D pozícióját
    - kinematikai és endoszkópos kamerakép lapú sebészeti kézségfelmérés jellemzőkinyerő <- sebészeti készségeket értékelünk pontok alapján, amiket látunk a képen
- vizsga félév végén 20%
  - ha félév végéig dolgozol a projekten akkor nincs vizsga

https://robotacademy.net.au/

---------------

## EA1

ppt: https://docplayer.hu/14015312-Robotok-diadalmenetben-a-sebeszrobotika-elso-20-eve.html

Mit nevezünk robotnak: *"I can't define a robot, but I know one when I see one" ~ J. Engelberger*

-ipari robotok
 - kollaboratív robotok
   - szervíz robotok <- nagyobb autonómiájuk van
- személyi szervízrobotok
  - orvosi robotok
    - sebészeti robotok

Az első műtét amit automatán megoldottak az a csontfúrás volt.

![számítógéppel integrált sebészet](https://docplayer.hu/docs-images/43/14015312/images/page_7.jpg)
- Digitális információ
  - beteg specifikus informáci
    - modell
      - tervezés
        - műtéti beavatkozás
          - betegspecifikus kiértékelés ()
            - statisztikai analízis  

**leggyakoribb rovidítések:**
- `CIS` computer integratedd surgery
- `IGS(T)` image guided surgery
- `MIS` minimally invasive surgery
- `surgical CAD/CAM` számítógéppel támogatott tervezés
- `CIIM` computer integrated inerventionoal medicine
- `CAS` computer assisted surgery


## EA-GY2
| | |
| ------------- |:-------------:| 
|![kuka orvosi robot](https://raw.githubusercontent.com/gabboraron/szerviz_robotok-orvosi_robotika/main/IMG_20210915_115429.jpg) | ![da vinci robotkar](https://github.com/gabboraron/szerviz_robotok-orvosi_robotika/blob/main/IMG_20210915_120840.jpg)|

## EA-GY3
*Szilágyi Áron**

![robot típusok](https://www.sardi.com/wp-content/uploads/2020/05/SARDI_INNOVATION_Cobot_expert_in_robot.jpg)

![robot részegységei](https://www.researchgate.net/profile/M-Arslan-2/publication/285590368/figure/fig5/AS:639520680710169@1529485020595/Movement-Structure-and-the-Main-Robot-Parts-22.png)

![kinematic structure](https://www.researchgate.net/publication/341034960/figure/fig2/AS:885873201655808@1588220038554/a-Robotic-arm-anatomy-b-Detail-view-of-gripper-assembly-attached-with-camera-c.jpg)

### fontos tulajdonságai egy robotnak:
- **pontosság:** a hiba átlaga. Nagyrészt a szoftvertől függ!
- **ismétlési pontosság:** felhasználás szempontjából ez a fontosabb adat, mert ez adja meg mennyire tud pontosan megismételni egy adott folyamatot, azaz a szórása a pontosságnak tulajdonképpen. Nagyrészt a hardwaretől függ!
- **maximum terhelhetőség:** ez egy függvény, mert a robotkar végpontján más az érték mint a közepén, stb. Tehát a robot végoontjától függ a terhelhetősége.
- **mozgathatóság határa:** meddig ér el a kar, stb
- **vezérlőszoftver**
- **holtjáték:** az ismétlési pontosságot befolyásolja, hogy ha megfogod a robotot miközben áll mennyit tud mozogni.

> ### Kinematika
> A geometriai leírásai a mozgásoknak. 

> ### Szbadságfok
> Ha egy 7 csuklós mechanizmus akkor 7 motorral kezelhető, tehát egy `7x7`es mátrixal írható le.

> ### kinematikai csukló szabadsgi foka
> Két szegmens összekötése hány szabadsági fokot ír le? Tehát két merev test három forgást és három elmozdulást tud leírni.

> ### mechanizmus szabadsági foka
> Valamilyen szegmens összekötve csuklókkal amit valahogy tudsz mozgatni.

### Kinemaatika definíciói:
- direkt kinematika: A transzformáció a csuklóváltozókból a térbeli pontját adja meg a robot végpontjának, csuklóról csuklóra számolva. 
- inverz kinematika: HA van egy célpont a térben akkor merről tudja robot elérni azt. Itt egy vektor egy eredményt ad.

![kinamtics definitons](https://www.researchgate.net/profile/Karl_Wallkum/post/What-is-the-difference-between-forward-kinematics-and-inverse-kinematics/attachment/5e542a253843b0499fe97e13/AS%3A862192492630020%401582574117930/image/FWDvsINV_Kinematics_HighResTransp.png)

`F=M*a` alapon a motor a csuklóban erőt és/vagy nyomatékot ad a szegmensekre amik között van. Ebből sebességet és gyorsulást sázmolhatunk idő szerinti integrálással.

Ezért mer itt nem gegyértelmű merre a `+` és a `-` irány bevezettk a Denavit-Hartenberg formát:
[YouTube: Denavit-Hartenberg Reference Frame Layout](https://www.youtube.com/watch?v=rA9tm0gTln8)

![matematikája](https://i.ytimg.com/vi/IKOGwoJ2HLk/maxresdefault.jpg)

> https://robotacademy.net.au/lesson/inverse-kinematics-for-a-2-joint-robot-arm-using-geometry/

Szögsebességekből kiszámoljuka végpont sebességét és szögsebességét jacobi mátrixal. Ha a mátrix rangja nem egyezik meg a méretével akkor a robot szinguláris pozícióban van. 

### Robot munkatere:
> **def:** 
> - elérhető munkatér: a teljes munkatér amit nem minden szabadsági fokával, de elég nehezen akár ér el a robot. 
> - dexterous munkatér: megvan mindne szabadsági foka és mindne irányba mozgatható.

### Aktivátorok
- DC motorok elektromágneses motork, kefés és kefe nélküli motorok állandó mágneses és savas gerjeszétsű motor. 
- piezoelektromos motor: egy kristályra

![piezolektromos motor működése](https://d1otjdv2bf0507.cloudfront.net/images/Article_Images/ImageForArticle_5307(4).png)

![mechanizmusok](https://eschool.iaspaper.net/wp-content/uploads/2018/06/Types-of-gear.jpg)

### Enkóderek
> Egy tárcsán kivágunk lyukakat és egyik oldlaára teszünk egy lámpát a másik oldalán egy fényérzékelőt amivel meghatározhatjuk, hogy a tárcsa milyen gyorsan forog, vagy milyen irányba. Ehhez használjuka grey codeot:
> 
> ![grey code]()https://scienceprog.com/wp-content/uploads/2021/02/image-6.png)

EGy vezeték ellenállása arányos a hosszával és fordítottan arányos a szélességével, tehát ha megnyújtnk egy vezetéket akkor annak ellnállásával mérhetjük a nyúlás hosszát.

### Robot control
Lemodellezzük matematikailag egy olyan szintre ahol nem érdekel minket, hogy fizikailag micsoda.
- elméleti modellje a plantnek főleg az inputokra adott válaszok értelmében.
- bementeke és kimenetek köött szeretnénk tiszátn matamtikai modelleket alkotni ahol nincs külöjnbség abban, hogy folyadékról vagy miről van szó.

> **irányítás:** mindne esetben visszacsatolást tartalmaz.
> 
> **vezérlés:** minden külső paramétert/surlódást ismerek és nem mérek vissza.
> 
> **PID controller** egy lineáris szabályozó, a hibához arányosan, a hiba integráljával arányosan, és a hiba deriváltjával is arányso jelet ad. 

## EA-GY4
- 95-ben alakult a cég ami létrehozta a davincit
- 98-ban volt az első emberes műtét davincivel

Az erő erősségét vissza tudjuk adni a vezérlésnek a motor áramfelvételéből tudjuk kiszámolni

A karokat a műtét elején beállítjuk egy pontba és a műtét során onnan nem mozdul, ezzel a 6 szabadsági fokból 4 marad meg, de ez rögzíti a bemeneti pontot a testen, így nem lehet véletlenül onnnan elmozdullni.

## EA-GY5
- a **modell:** sok képen bejelöljük, hogy hol a beteg rész, stb és az alapján javasolunk egy eljárást a beteghez
- a **terv:** az, hogy távolítjuk el a tumort, hogy vágjuk ki, stb.

> **endoszkópia**
> 
> - minimál invazív sebészet kategóriája, amikor csak kamerát dugunk be és az eszközt ami elvégzi a feladatot.
> - da vincinél a sebész állítja be a kamerát is, míg a hagyományosnál a rezidens tartja

### PET 
> https://github.com/gabboraron/diagnosztikai_celu_orvosi_kepalkotas#pet
> 
> gamma fotonokkal alkotunk képet, miközben bomlik aközben próbáljuk a bomlást követni szenzorokkal

### ultrahang
> piezoelektromos kristály képes a kibocsájtott és visszaverődő hangot is érzékelni, és ezt tartja a szenzorfej
> 
> - olcsó
> - vals idejű
> - mozgást lehet vele detektálni
> - *nagy frekvencián éget!*
> - 20 kHz

### röntgen
> https://github.com/gabboraron/diagnosztikai_celu_orvosi_kepalkotas#r%C3%B6ntgen-rtg
> 
> https://www.youtube.com/watch?v=hTz_rGP4v9Y
>
> https://www.nibib.nih.gov/science-education/science-topics/x-rays

- minnél kisebb a hullámhossza az elektromágneses hullámnak annál veszélyesebb, *ionizálóbb*
- a röntgensugárzás ionizálós sugárzás
- ahogy a vákumba becsapódik a fény úgy keletkezik a röntgensugárzás

### CT
> https://www.youtube.com/watch?v=l9swbAtRRbg
> 
> [Diagnosztikai célú orvosi képalkotás - CT](https://github.com/gabboraron/diagnosztikai_celu_orvosi_kepalkotas#computer-tomogr%C3%A1fia-ct)

### MRI
> - [YT How Does an MRI Scan Work?](https://www.youtube.com/watch?v=1CGzk-nV06g)
> - [Diagnosztikai célú orvosi képalkotás - MRI](https://github.com/gabboraron/diagnosztikai_celu_orvosi_kepalkotas#mri) 
>  
> - a proton kölcsönhatását nézi a mágneses térben

## EA-GY6
> Az FDA szabályozza az orvostechnikai eszközök forgalamazását. Minden ami orvosi értékeket ad ki, ilyenkor a gyártó felelősségre vonható. Szintén kérhető olyan jelzés ami indokolja, hogy ez nem orvostechinkai eszköz! 
> 
> Nem öszekeverendő a china exporttal:
> ![ce vs ce](https://siloscordoba.com/wp-content/uploads/2013/07/CE-and-China-Export-1.jpg)
> ![FDA ce engedélyeztetés](https://images.slideplayer.com/17/5304510/slides/slide_3.jpg)
> 
> **Szabványok:**
> - ISO/TC 184/SC 2/JWG 9
> - ISO 1298 ~ ipari robotok szabványa: ember robot közelébe működés közben nem mehet.
> - FDA 
> 
> **tréning:**
> - 5 napos tréning
> - mostmár laporoszkópiában nem jártas orvosokat is betanítanak
> - gyors növekedésű tanulási görbe jellemző a davinci betanítására
>  
> [Elizabeth Holes story](Elizabeth Holmes)

### Intra operative Tracking
> operáció alatti eszközök követése - pozíció és meghatározás
> 
> ![intra opertive tracking](https://www.researchgate.net/profile/Gregory-Bootsma/publication/253612637/figure/fig1/AS:298196090802177@1448106896489/a-Photograph-of-a-real-time-tracking-system-NDI-Polaris-integrated-with-the.png)

> **optikai alapaú követés**nél vagy olyant használok ami visszaveri a fényt, vagy megjelölöm az eszközeimet. A Los-hoz látni kell az eszközöket, ezért minimal invazív sebészetnél ez nem játszik.
> 
> **elektromágneses követés**nél van egy tekercsel mérjük a különbséget, amit a mozgás okoz, ezt egy elektormágneses mezővel tudjuk követni. Erre Daviniél nem feltétlen van szükség, mert vannak kinematikai adataim.
> 
> **gyneacology:** célzott nőgyógyászati beavatkozás, amikor egy tűvel próbáljuk bejuttatni a rákos szövethez az anyagot.
>   **robogyn:** ha mindne információ adott akkor akár robottal is elvégezhető ugyanez

***Mindig azt kell nézni ami a betegnek is és orvosnak is jó egyszerre, hogy, hiába jó az eljárás, de ha több energia az orvosnak akkor mindne hiába.***


1. képen megnézzük hogy hol a tumor
2. a kép koordináta rendszerében megmondjuk, hogy hol a tumor.

> #### zh kérdések:
> 
> teszt alapú
> 
> - mi a minimál invazív sebészet
> - mikor és hol született a da-vinci ötletete
> - orvosi képalkotás - ultraang, röntgen, ct, mri, pet
> - Milyen operáció amire először robotot használtak? - csontfúrás
> - mi a számítógéppel támogatot sebészet elemei/lépései?
> - mi a kép által vezett sebészet?


## EA-GY7
### Kiterjesztett valóság sebész szemszögből
glasgow kóma skála: https://www.glasgowcomascale.org/
Móga Kristóf

## EA-GY8
![](https://thejns.org/focus/view/journals/neurosurg-focus/27/3/0270009f1.jpg)

- trokárok 

**problémák:** 
- nincs erővisszacsatolás da vincinél

**orvosok képességei:**
- eszköz kezelés
- endoscope
- sebesség
- pontosság
- csapatmunka
- döntéshozási képesség
- fősebész vezető szerepe
- stressz tűrés
- előkészületek minősége

[da Vinci Robot Stitches a Grape Back Together](https://www.youtube.com/watch?v=0XdC1HUp-rU)

kulcslyuksebészet

### FLS
> Sebész értékelő objektív pontrendszer, amit a laporoszkópiás seészek képzésében használnak, így egységesítve a számonkérést is és a tananyagot is.

### FRS
> https://frsurgery.org hasonló mint az FLS, csak robot sebészek számára.
> 
> ![manual vs automated skill assessment surgical](https://www.auajournals.org/cms/asset/50f8e4bc-c9fc-4c5d-8751-ded7cc538a42/j.juro.2018.06.078f2.jpg)

## EA-GY9
### Mesterséges neurális hálózatok
![conventional computer vs neurocomputer](https://www.researchgate.net/publication/317752979/figure/tbl1/AS:668911594917889@1536492360299/Comparison-of-the-conventional-computer-and-neurocomputer.png)

- minden neuronhoz 10^4 kapcsolat tartozik
- 10^11 neuron van
- lassú kapcsolat 10^-3

A kapcsolatok nem állandóak. A tanulás nem a kapcsolatok építéséről, hanem lebontásáról szól, ez azlvás közen történik leginkább.

Az agyban az erősség a frekvenciában kódolódik, tehát ha valamit nagoyn sűrűn juttatunk át az idegsejten akkor az az erős tudás

**Mikor használjun AANt?** csak ha nem létezik rá maetmatikai megoldás

`w = w + n(d(x) - y(x))x`

Gradiens ereszkedés módszer: parciális deriváltakat használunk, de ez csak a lokális minimum megtalálását garantálja, csak sigmoid függvényt deriválhatunk, tehát a beemenet is sigmoid.

Backpropagation

rekurrens: hogy az egyik neuron kimenete a másik bemenete

CNN: celluláris háló

### Hogy döntsünk topológiáról:
- bementek száma
- kimenetek száma
- mi a feladat
- hány rejtett réteg van

### convulotional neural network:
- még mindig csak a súlyokat változtatjuk
- a legtöbb esetben továbbra is gradiens ereszkedéssel adom meg
- konvolúció: van egy képem, egy kis ablakkal végigiterálok rajta *(klasszikus kpfeldolgozásnál ez acsúszóablakos megoldás)*
- így egy réteggel kereshetünk egy elemet a képen, a másikkkal egy másikat, stb.

### RCNN: region based CNN
megmondjuk, hol van a képen amit találunk.

![](https://media.nature.com/lw800/magazine-assets/d41586-019-03013-5/d41586-019-03013-5_17247076.png)

# A jövő útjai
## újdonságok a minimál invazív sebészetben
- endoluminális sebészet ![endoluminális sebészet](https://i2.wp.com/abdominalkey.com/wp-content/uploads/2017/07/A340956_1_En_23_Fig2_HTML.gif?zoom=1.25&w=960)
- ultrahang vezérelt robotok: https://koellner-medical.com/
- MRI kompatibilis robotok
- szem műtétre alkalmas tű szerű robot

**Sűrgősségi esetet a robot nem tud ellátni!**

![](https://4.bp.blogspot.com/-iNgjTRV4FXg/XMp8YtFZTjI/AAAAAAACADg/_S5AEG1k4HMq15nr3oC9QEtHfuLp2Z7dgCLcBGAs/s1600/LoA%2Bfigure%2Bv2.3.png)

> ## vállakozási tanácsok
> - hanyadikként lépünk piacra
> - mennyi idő alatt térül meg
> - mennyi pénz kell hozzá
> - mikor kell kiszállni
> - meddig érdemes ezt csinálni
> - a felhasználók jól értékelik-e

- döntéstámogatás
- intelligens eszközök
- hozzáadott érték
- nagyobb pontosság

Távsebészetnél ha űrben szeretnénk használni akkor könnyű legyen az eszköz, hogy könnyen odajuttatható legyen

100-500 ms között késleltetésnek nevezzük, az alatt nem érezhető emberként

**Lindbergh operáció**: 2001 szept 7 New York - Strassbourg egy órás epehólyageltávolítás 150 ms késleltetés

**kooperatív sebészet:** a master és slave ugyanaz az eszköz

Ha egészségügyi témáról van szó akkor úgy kell elérni, hogy a betegnek jó legyen, de ha lehet az orvosnak is legyne jobb

# Vizsgakérdések
- szegmentálási lehhetőségek: neurális hálók/képfeldolgozás
- mi a davinci sebészeti robotrendszer?
  - távsebészeti eszköz
  - mester-szolga oldal
  - minimál invazív
    - kevsebb kórházi idő
    - gyorsabb gyógyulás
    - nehezebb a sebésznek
  - 3D kamerakép
  - könnyű kezelhetőség  
  - nagyít
  - kézremegés szűrés
  - 5000-s nagyságrend
- képalkotások
- neurálsi hálók
  - rajzolj le egy mesterséges neuront
- kép által vezettt sebészet (image guided surgery)
  - optikai/elektormágneses tracking 
- assesment




