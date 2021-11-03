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


