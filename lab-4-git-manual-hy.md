# Լաբ 4
## Տարբերակների կառավարման համակարգ — Git

# 1. Ներածություն

Git-ը **բաշխված տարբերակների կառավարման համակարգ** է, որը օգտագործվում է ֆայլերի փոփոխությունները վերահսկելու և ծրագրավորողների միջև համագործակցությունը կազմակերպելու համար։

Git-ը թույլ է տալիս`

- հետևել նախագծի պատմությանը
- վերադառնալ նախորդ տարբերակներին
- աշխատել մի քանի ֆունկցիաների վրա միաժամանակ
- համագործակցել GitHub-ի միջոցով

Git-ը լայնորեն օգտագործվում է ծրագրավորման, DevOps-ի և գիտական նախագծերի մեջ։

---

# 2. Նախապայմաններ

Լաբորատոր աշխատանքը սկսելուց առաջ համոզվեք, որ`

- Git-ը տեղադրված է համակարգչում
- տեղադրված է code editor (խորհուրդ է տրվում VS Code)
- գիտեք terminal-ի հիմնական հրամանները
- ունեք GitHub account

Առաջարկվող գործիքներ`

| Գործիք | Նպատակ |
|------|------|
| Git | Տարբերակների կառավարում |
| VS Code | Կոդի խմբագրիչ |
| Terminal | Հրամանների կատարում |
| GitHub | Remote repository |

---

# 3. Git-ի տեղադրում

## Windows

1. Բացել Git-ի պաշտոնական կայքը

```
https://git-scm.com
```

2. Ներբեռնել **Git for Windows**
3. Տեղադրել default կարգավորումներով

Ստուգել տեղադրումը`

```bash
git --version
```

---

## Linux

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install git
```

### Fedora

```bash
sudo dnf install git
```

### Arch Linux

```bash
sudo pacman -S git
```

Ստուգել տեղադրումը`

```bash
git --version
```

---

## macOS

Homebrew օգտագործելով`

```bash
brew install git
```

կամ`

```bash
xcode-select --install
```

Ստուգել`

```bash
git --version
```

---

# 4. Git-ի կարգավորում

Git օգտագործելուց առաջ անհրաժեշտ է նշել օգտվողի տվյալները`

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

Ստուգել`

```bash
git config --list
```

---

# 5. Git-ի ներքին կառուցվածք

Git-ը տվյալները պահում է **snapshot-ների տեսքով**։

## Git Object Model

```
Commit
  │
  ├── Tree (directory)
  │      ├── File A (blob)
  │      └── File B (blob)
  │
  └── Parent Commit
```

Git օբյեկտների տեսակներ`

| Օբյեկտ | Նկարագրություն |
|------|-------------|
| Blob | Ֆայլի տվյալներ |
| Tree | Պանակի կառուցվածք |
| Commit | Snapshot |
| Tag | Անվանված commit |

---

# 6. Git աշխատանքային հոսք

```
Working Directory
       │
       │ git add
       ▼
Staging Area
       │
       │ git commit
       ▼
Local Repository
       │
       │ git push
       ▼
Remote Repository
```

---

# 7. Լաբորատոր աշխատանք 1 — Git-ի հիմնական աշխատանք

## Ստեղծել նախագիծ

```bash
mkdir git_lab
cd git_lab
```

Ստեղծել repository`

```bash
git init
```

---

## Ստեղծել ֆայլ

```bash
echo "Hello Git" > example.txt
```

Ստուգել վիճակը`

```bash
git status
```

---

## Ավելացնել staging area

```bash
git add example.txt
```

---

## Ստեղծել commit

```bash
git commit -m "Initial commit"
```

---

## Փոփոխել ֆայլը

```bash
echo "Second line" >> example.txt
```

Տեսնել փոփոխությունները`

```bash
git diff
```

Commit անել`

```bash
git add example.txt
git commit -m "Update example file"
```

---

## Դիտել commit պատմությունը

```bash
git log
```

---

# 8. Լաբորատոր աշխատանք 2 — Branch-եր և Merge Conflict

## Ստեղծել branch

```bash
git branch feature_branch
```

Տեսնել branch-երը`

```bash
git branch
```

---

## Փոխել branch

```bash
git checkout feature_branch
```

կամ`

```bash
git checkout -b feature_branch
```

---

## Ստեղծել նոր ֆայլ

```bash
echo "Feature file" > feature.txt
```

Commit`

```bash
git add feature.txt
git commit -m "Add feature file"
```

---

## Merge անել branch-ը

```bash
git checkout master
git merge feature_branch
```

---

# Merge Conflict օրինակ

```
<<<<<<< HEAD
Master change
=======
Branch change
>>>>>>> feature_branch
```

Լուծել conflict`

```bash
git add example.txt
git commit
```

---

# 9. Լաբորատոր աշխատանք 3 — GitHub և համագործակցություն

## Ստեղծել GitHub repository

1. Մուտք գործել GitHub
2. Սեղմել **New Repository**
3. Մուտքագրել անուն
4. Սեղմել **Create Repository**

---

## Clone անել repository

```bash
git clone https://github.com/username/repository.git
```

Մուտք գործել պանակ`

```bash
cd repository
```

---

## Ստեղծել ֆայլ

```bash
echo "GitHub project" > project.txt
```

Commit`

```bash
git add project.txt
git commit -m "Add project file"
```

---

## Push անել GitHub

```bash
git push origin master
```

---

## Pull անել փոփոխությունները

```bash
git pull
```

---

# 10. Branch-երի գրաֆիկական պատկերացում

## Հիմնական պատմություն

```
A --- B --- C --- D
```

## Feature branch

```
A --- B --- C --- D
            \
             E --- F
```

## Merge օրինակ

```
A --- B --- C -------- G
            \        /
             D ---- E
```

---

# 11. Git հրամանների cheat sheet

## Repository

| Հրաման | Նկարագրություն |
|------|-------------|
| git init | Ստեղծել repository |
| git clone | Ներբեռնել repository |
| git status | Տեսնել վիճակը |
| git log | Commit պատմություն |

---

## Ֆայլերի կառավարում

| Հրաման | Նկարագրություն |
|------|-------------|
| git add | Ավելացնել staging |
| git diff | Տեսնել փոփոխությունները |
| git commit | Snapshot |

---

## Branch-եր

| Հրաման | Նկարագրություն |
|------|-------------|
| git branch | Branch ցուցակ |
| git checkout | Փոխել branch |
| git merge | Միավորել branch |

---

# 12. GitHub աշխատանքային հոսք

```
Developer
   │
   ▼
Clone repository
   │
   ▼
Create branch
   │
   ▼
Commit changes
   │
   ▼
Push branch
   │
   ▼
Create Pull Request
   │
   ▼
Review
   │
   ▼
Merge
```

---

# 13. Screenshot բաժին

Ավելացնել նկարներ`

```
images/github_create_repo.png
images/github_clone.png
images/github_pull_request.png
```

Markdown օրինակ`

```
![Create Repository](images/github_create_repo.png)
```

---

# 14. Առաջադրանքներ ուսանողների համար

Ուսանողները պետք է`

1. Տեղադրեն Git
2. Կարգավորեն Git
3. Ստեղծեն repository
4. Commit անեն ֆայլ
5. Ստեղծեն branch
6. Merge անեն branch
7. Լուծեն merge conflict
8. Push անեն GitHub
9. Ստեղծեն Pull Request

---

# 15. Լավագույն պրակտիկաներ

- Գրեք պարզ commit message
- Commit արեք փոքր փոփոխություններով
- Օգտագործեք branch-եր
- Pull արեք մինչև push
- Մի commit արեք ժամանակավոր ֆայլեր

---

# 16. Սպասվող արդյունք

Լաբորատոր աշխատանքից հետո ուսանողները պետք է կարողանան`

- տեղադրել Git
- ստեղծել repository
- commit անել փոփոխությունները
- աշխատել branch-երով
- լուծել merge conflict
- աշխատել GitHub-ի հետ

---

# 17. Լրացուցիչ ռեսուրսներ

Git Documentation  
https://git-scm.com/docs

Pro Git Book  
https://git-scm.com/book

GitHub Learning Lab  
https://lab.github.com

---

# Եզրակացություն

Այս լաբորատոր աշխատանքը ուսանողներին ծանոթացնում է Git-ի հիմնական և առաջադեմ հնարավորություններին, ներառյալ branch-եր, merge conflict և GitHub համագործակցություն։
