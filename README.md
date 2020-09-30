# Git Parancsok

## Helyi repo
`git init` : Helyi repo létrehozás (mappán belül)
`git init mappa` : Helyi repo létrehozása a mappa nevű mappában


`git config --global user.email xy.gmail.com` : Email megadása  
`git config --global user.nam xy` : Usernév megadása  

`git status` : Git állapotának lekérdezése  

`git add .` : Minden fájl -> színpad (stage)   
`git add *.txt` : Minden txt fájl -> színpad (stage)  
`git add valami.txt` : valami.txt fájl -> színpad (stage)  

`git commit -m "Commit üzenet"` : A helyi repóba mentjük a színpad tartalmát (commit)  
`git commit -am "Commit üzenet"` : Add és commit összevonása (mindent színpadra tesz)  

`git log` : Commitok részletes listázása  
`git log --oneline` : Commitok tömör listázása  
`git log --oneline --graph` : Commitok tömör listázása  "grafkusan"  

`git checkout commitID` : Időgép: a megadott commitID-jű állapotba állítja a projektet  
`git checkout HEAD~1` : Időgép: menj egy committal előbbi állapotra  
`git checkout master` : Időgép: visszaállás a legfrisebb állapotra  

## Helyi repo - GitHUb összekapcsolódás

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
6a. Ha rossz helyre kapcsolódtunk, az visza lehet vonni: `git remote remove origin`
7. Feltölteni ami a helyi repo-ban van: `git push -u origin master`

## Ágak (branch)
Egy ágat azért hozunk létre, hogy anélkül fejlesszünk, hogy zavarnánk a többi ágat.  
Ha kész vagyunk a fejlesztéssel, akkor a master ágba egyesíthetjük: merge.  
A helyi repó ágai nem kerülnek fel a GitHub-ra ott külön létre kell őket hozni.  



