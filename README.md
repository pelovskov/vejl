# Sådan bruger du dette skelet

1. Opret et nyt repository på GitHub (fx kaldet `vejledninger`).
2. Upload alle filerne fra denne mappe til repositoriet
   (`_config.yml`, `index.md`, `vejledning-eksempel.md`).
3. Gå til **Settings → Pages** i dit repository.
4. Under "Build and deployment" vælger du branch `main` og mappen `/ (root)`.
5. Vent ca. 1 minut — din side er nu klar på:
   `https://dit-brugernavn.github.io/vejledninger/`

## Sådan tilføjer du en ny vejledning

1. Lav en ny fil, fx `vejledning-2.md`.
2. Start filen med front matter (de tre streger + titel):

   ```
   ---
   title: Din nye titel
   ---
   ```

3. Skriv din vejledning i almindelig Markdown derunder.
4. Tilføj et link til den nye fil i `index.md`, så den kan findes fra forsiden.

## Skift tema

Åbn `_config.yml` og skift linjen `theme: jekyll-theme-minimal` ud med et af disse:

- `jekyll-theme-slate`
- `jekyll-theme-cayman`
- `jekyll-theme-architect`
- `jekyll-theme-dinky`

Gem, og siden bygger automatisk om efter ca. 30-60 sekunder.
