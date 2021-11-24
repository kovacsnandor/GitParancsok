# Git Parancsok

## Helyi repo
### Email és User név beállítása
`git config --global user.email xy.gmail.com` : Email megadása globálisan  
`git config --global user.name xy` : Usernév megadása globálisan  

`git config user.email xy.gmail.com` : Email megadása lokálisan (csak arra a mappára)  
`git config user.name xy` : Usernév megadása lokálisan  

`git config --list` : A konfig fájl listája (kilépés: `q`)

### Helyi repo létrehozása
`git init` : Helyi repo létrehozás (mappán belül)
`git init mappa` : Helyi repo létrehozása a mappa nevű mappában

### Alap parancsok
`git status` : Git állapotának lekérdezése  

`git add .` : Minden fájl -> színpad (stage)   
`git add *.txt` : Minden txt fájl -> színpad (stage)  
`git add valami.txt` : valami.txt fájl -> színpad (stage)  

`git commit -m "Commit üzenet"` : A helyi repóba mentjük a színpad tartalmát (commit)  
`git commit -am "Commit üzenet"` : Add és commit összevonása (mindent színpadra tesz) 

`git diff` : Megnézhetem, hogy mit változtattam az alőzőhöz képest  

`git log` : Commitok részletes listázása  
`git log --oneline` : Commitok tömör listázása  
`git log --oneline --graph` : Commitok tömör listázása  "grafkusan"  

### Időgép parancsok
`git checkout commitID` : Időgép: a megadott commitID-jű állapotba állítja a projektet  
`git checkout HEAD~1` : Időgép: menj egy committal előbbi állapotra  
`git checkout master` : Időgép: visszaállás a legfrisebb állapotra  



### Branch (ágak)
- Alapban a `master` nevű ág van, abban vagyunk.
- A külön ágak azért kellenek, hogy egymástól elkülönülve tudjunk fejleszteni pl. a következő verziót
- A végén az ágat egyesítjük a master ágba, és ez lesz az aktuális verzió
    - Így ha baj van, vissza tudunk térni az ez előtti verzióra
- Ág egyesítés (`honnan ág`-ból a `hova ág`-ba):
    - Átmegyek abba az ágba ahova egyesíteni akarok (pl. master): `git checkout master`
    - Kiadom a merge parancsot (`merge művelet`): melyik ágat egyesítsem ide: `git merge 1.0`
    - Úgy mondjuk: "bemergeltem az 1.0-ás ágat a master brech-be"
    - A `merge` összegyűjti az az összes olyan commitot a honnan ágból ami nincs a hova ágban, és átpakolja.
    - A `merge` után a honnan ág nem szűnik meg, csak bele egyesül a hova ágba
- Konfliktus: Akkor történik, ha:
    - a honnan és hova ágban uganabban a fájban módosítottuk ugyanazt a sort, és mergelünk.
    - A rendszer jelzi, hogy konfliktus van
    - Feloldás: 
        - A probémás fájlba a rendszer mindkét változatot beteszi, és kézzel eldöntjük, hogy melyik jó.

`git checkout -b 1.0` : Új branch (ág) létrehozása (pl. 1.0), átváltás az új ágra  
`git branch` : Branc-ek lekérdezése (azt is mutatja, hogy jelenleg hol vagyok)  
`git checkout master` : Ugrás a megadott (pl. master) ágra  
`git merge 1.0` : Az 1.0-ás ág egyesítése azzal az ággal, ahol vagyok.  

## Helyi repo - GitHUb összekapcsolódás
Az első push-nál `personal acces token`-t kell létrehozni:
- Github / Setting / Developer settigs
    - Personal access tokens
        - Generate new token
            - Kell egy név
            - mennyi időre
            - pipáljuk a repo-t
            - Ad egy tokent
            - ezt kell beilleszteni

### Meglévő GitHub repo klónozása
`git clone url` : A helyi gép mappájába lehúzza az url-hez tartozó gitHub repót a repó nevének mappájába  
`git clone url mappa` : A helyi gép mappájába lehúzza az url-hez tartozó gitHub repót a megadott nevű mappába  

### First GitHud módszer
Ez a legcélravezetőbb:
1. A GitHub-on létre kell hozni egy repót README.md-vel
2. Ki kell másolni a repóhoz tartozó url-t
3. Helyi gépen egy mefelelő mappába kónozni:
`git clone url`

### First Helyi repó módszer
#### A projekt mappájának parancssorában (ez lesz a projekt neve):
1. Heyi repó létrehozása: `git init`
2. Létrehozni a **README.md** fájlt.
3. README.md -> színpad (stage): `git add README.md`
4. Commit: `git commit -m "first commit"`  
#### A GitHub-on:
5. Létrehozni a projektet **README.md nélkül !!!** és kimásolni az url-t
#### Helyi gép parancssorában:  
6. kapcsolódni a GitHub projekthez origin néven: `git remote add origin url`  
  (Ha az 5. lépésben mégis létrehoztuk a README.md fájlt, akkor ki kell adni az alábbi parancsot:  
  `git pull origin master --allow-unrelated-histories`)
7. Ha rossz helyre kapcsolódtunk, vissza lehet vonni: `git remote remove origin`
8. Feltölteni ami a helyi repo-ban van: `git push -u origin master`

### push, pull
`git push` : A commitált váltztatások felküldése a távoli repóba  
`git pull` : A távoli repóból lehúzza a változatásokat (érdemes mindig ezzel kezdeni)  
Ha a távoli repóban van változás és még nem volt pul, akkor nem működik a push


## Ágak (branch)
Egy ágat azért hozunk létre, hogy anélkül fejlesszünk, hogy zavarnánk a többi ágat.  
Ha kész vagyunk a fejlesztéssel, akkor a master ágba egyesíthetjük: merge.  
A helyi repó ágai nem kerülnek fel a GitHub-ra ott külön létre kell őket hozni.  



