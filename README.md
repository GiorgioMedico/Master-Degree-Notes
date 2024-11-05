# Guida all'Installazione di LaTeX e Git LFS

Questa guida spiega come installare LaTeX, i pacchetti essenziali e Git LFS su Ubuntu e macOS.

## Ubuntu 22.04

Installa i pacchetti LaTeX essenziali usando i seguenti comandi:

```bash
sudo apt-get update
sudo apt-get install texlive-base texlive-binaries texlive-fonts-recommended \
 texlive-lang-english texlive-lang-italian texlive-lang-greek \
texlive-latex-base texlive-latex-extra texlive-latex-recommended \
 texlive-pictures texlive-plain-generic texlive-science
```

### Verifica dell'installazione

Per verificare i pacchetti installati:

```bash
dpkg -l | grep texlive
```

## macOS

Su macOS, ci sono due opzioni principali per installare LaTeX:

### 1. MacTeX (Raccomandato)

MacTeX è la distribuzione più completa per macOS.

1. Scarica MacTeX dal sito ufficiale:
   - Visita [MacTeX Download](https://www.tug.org/mactex/mactex-download.html)
   - Scarica il file .pkg (circa 4GB)

2. Installa il pacchetto scaricato:
   - Apri il file .pkg scaricato
   - Segui le istruzioni dell'installer

### 2. Homebrew (Alternativa più leggera)

Se preferisci usare Homebrew per una installazione più leggera:

```bash
brew install --cask basictex
```

Dopo l'installazione base, aggiungi i pacchetti equivalenti:

```bash
sudo tlmgr update --self
sudo tlmgr install latex-base latex-recommended latex-extra \
 fonts-recommended pictures plain-generic science \
lang-english lang-italian lang-greek
```

## Verifica dell'Installazione LaTeX

Per verificare che LaTeX sia installato correttamente su entrambi i sistemi:

```bash
latex --version
```

## Git LFS (Large File Storage)

Git LFS è utile per gestire file di grandi dimensioni in progetti LaTeX (come immagini ad alta risoluzione o PDF).

### Installazione Git LFS

**Ubuntu:**
```bash
sudo apt-get install git-lfs
```

**macOS:**
```bash
brew install git-lfs
```

### Configurazione Git LFS

1. Inizializza Git LFS nel tuo account:
```bash
git lfs install
```

2. Specifica quali tipi di file tracciare con Git LFS (esempio per file comuni in progetti LaTeX):
```bash
git lfs track "*.pdf"
git lfs track "*.png"
git lfs track "*.jpg"
git lfs track "*.jpeg"
git lfs track "*.eps"
```

3. Assicurati di committare il file .gitattributes:
```bash
git add .gitattributes
git commit -m "Configurazione Git LFS per file binari"
```

### Verifica Configurazione Git LFS

Per verificare i tipi di file tracciati:
```bash
git lfs track
```

Per verificare lo stato dei file LFS:
```bash
git lfs status
```

## Editor Consigliati

Per lavorare con LaTeX, si consiglia l'utilizzo di uno dei seguenti editor:
- TeXmaker
- TeXstudio
- Visual Studio Code con l'estensione LaTeX Workshop

## Note Aggiuntive

- Su Ubuntu, potrebbe essere necessario installare anche un editor LaTeX:
  ```bash
  sudo apt-get install texstudio
  ```
- Su macOS con MacTeX, viene installato automaticamente TeXShop come editor
- Per aggiornare i pacchetti LaTeX:
  - Ubuntu: `sudo apt-get update && sudo apt-get upgrade`
  - macOS (MacTeX/BasicTeX): `sudo tlmgr update --self --all`