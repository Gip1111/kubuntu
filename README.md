# AstraMind Glass per Kubuntu Plasma 6

AstraMind Glass e un pacchetto installabile su Kubuntu gia presente. Include:

- tema KDE Plasma 6 con look scuro/glass;
- tema SDDM;
- wallpaper e splash;
- plasmoid/launcher AstraMind;
- assistente smart offline `astramind`;
- menu contestuali Dolphin;
- installer e uninstaller con backup.

La prima versione non richiede un modello AI. L'assistente usa un catalogo locale di comandi, sinonimi, guide offline e aperture sicure di strumenti KDE. Ollama/API sono predisposti come upgrade opzionale.

## ISO Kubuntu completa

Questo repository puo anche generare una ISO Kubuntu 26.04 LTS AMD64 completa con AstraMind gia integrato.

Su GitHub:

1. Apri la tab **Actions**.
2. Avvia **Build AstraMind Kubuntu ISO**.
3. Scarica l'artifact `astramind-kubuntu-iso`.

Su Linux/Kubuntu:

```bash
sudo bash iso/build-iso.sh
```

Output previsto:

```text
dist/astramind-kubuntu-26.04-amd64.iso
dist/astramind-kubuntu-26.04-amd64.iso.sha256
```

Il builder usa come base la ISO ufficiale Kubuntu 26.04 LTS AMD64 e la personalizza nel filesystem live.

## Requisiti

- Kubuntu 25/26 o altro sistema KDE Plasma 6.
- Bash, Python 3, sudo.
- Consigliati: `kdialog`, `plasma-discover`, `lookandfeeltool`, `kcmshell6`.

## Installazione

Da Linux, entra nella cartella del progetto e lancia:

```bash
bash install.sh
```

L'installer:

- controlla Plasma 6;
- copia i componenti in `/usr/share`;
- applica colori, tema Plasma e wallpaper quando possibile;
- abilita il tema SDDM in `/etc/sddm.conf.d/astramind-glass.conf`;
- installa `astramind` e `astramind-gui`;
- crea backup in `/var/backups/astramind-glass`.

Per installare senza prompt:

```bash
ASTRA_ASSUME_YES=1 bash install.sh
```

## Uso

```bash
astramind "configura wifi"
astramind "aggiorna sistema"
astramind "installa chrome"
astramind "tema scuro"
astramind "backup file"
astramind list
```

Per aprire la finestra rapida:

```bash
astramind-gui
```

## Disinstallazione

```bash
sudo bash uninstall.sh
```

L'uninstaller rimuove i file installati da AstraMind e disabilita la configurazione SDDM dedicata.

## AI opzionale

La v1 funziona senza AI. Per una fase successiva:

- 8 GB RAM: Ollama con `llama3.2:1b` o `gemma3:1b`;
- 8-16 GB RAM: `llama3.2:3b`;
- 16 GB+ RAM: modelli 3B/4B piu comodi;
- API key utente: possibile integrazione futura con KWallet.

## Struttura

```text
.github/workflows/       build automatico ISO su GitHub Actions
assistant/                 sorgenti assistente smart
iso/                       builder ISO Kubuntu
packages/plasma/           tema Plasma, colori, wallpaper, plasmoid
packages/sddm/             tema login SDDM
packages/applications/     desktop entry
packages/kio/              menu contestuali Dolphin
packages/icons/            icona AstraMind
scripts/validate.sh        controlli statici locali
install.sh                 installazione sistema
uninstall.sh               rimozione sistema
```
