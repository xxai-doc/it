<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Si consiglia di installare prima nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) e poi `direnv allow` dopo essere entrati nella directory ( [il file .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) verrà eseguito automaticamente dopo essere entrato nella directory).

Il significato è: traduzione cinese in giapponese, coreano, inglese, traduzione inglese in tutte le altre lingue. Se vuoi supportare solo cinese e inglese, puoi semplicemente scrivere `zh: en` .

Il significato è: traduzione cinese in giapponese, coreano, inglese, traduzione inglese in tutte le altre lingue. Se vuoi supportare solo cinese e inglese, puoi semplicemente scrivere `zh: en` .

* [codice di front-end](https://github.com/xxai-art/web)
* [Language pack per il sito nel suo complesso](https://github.com/xxai-art/web/tree/main/i18n)
* [Language pack per i moduli di accesso](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Sito Web Documentazione multilingue](https://github.com/xxai-doc)

Il linguaggio di programmazione front-end è [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , che aggiunge alcune funzionalità basate sulla sintassi coffeescript, vedi [./coffee_plus.md](./coffee_plus.md) .

## Internazionalizzazione di siti web e documenti

Costruisci sui seguenti 3 progetti

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Il suffisso è `.mdt` , puoi utilizzare la sintassi simile a `<+ ./coffee_plus/import.js>` per fare riferimento a file esterni e generare markdown con il suffisso `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  La traduzione Markdown non tradurrà codici e collegamenti e memorizzerà nella cache le frasi tradotte. Se la traduzione viene modificata ma il testo originale non viene modificato, eseguirlo di nuovo non sovrascriverà la modifica della traduzione.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  File di lingua per la traduzione di siti Web generati `yaml` .

### Istruzioni per l'automazione della traduzione di documenti

Vedi repository di codice [xxai-art/doc](https://github.com/xxai-art/doc)

Si consiglia di installare prima nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) e poi `direnv allow` dopo essere entrati nella directory ( [il file .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) verrà eseguito automaticamente dopo essere entrato nella directory).

Per evitare la grande base di codice tradotta in centinaia di lingue, ho creato una base di codice separata per ogni lingua e ho creato un'organizzazione per archiviare la base di codice

L'impostazione della variabile di ambiente `GITHUB_ACCESS_TOKEN` e quindi l'esecuzione [di create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) creerà automaticamente il repository di codice.

Ovviamente puoi anche inserirlo in una base di codice.

Riferimento allo script di traduzione [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Il codice dello script viene interpretato come segue:

[bunx](https://bun.sh/docs/cli/bunx) è un sostituto di npx, che è più veloce. Ovviamente, se non hai bun installato, puoi invece usare `npx` .

`bunx mdt zh` esegue il rendering `.mdt` nella directory zh come `.md` , vedere i 2 file collegati di seguito

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` è il codice principale per la traduzione (se hai solo `nodejs` installato, ma `bun` e `direnv` non sono installati, puoi anche eseguire `npx i18n` per tradurre).

Analizzerà [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , la configurazione di `i18n.yml` in questo documento è la seguente:

```
en:
zh: ja ko en
```

Il significato è: traduzione cinese in giapponese, coreano, inglese, traduzione inglese in tutte le altre lingue. Se vuoi supportare solo cinese e inglese, puoi semplicemente scrivere `zh: en` .

L'ultimo è [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , che estrae il contenuto tra il titolo principale e il primo sottotitolo di `README.md` di ciascuna lingua per generare una voce `README.md` . Il codice è molto semplice, puoi guardarlo tu stesso.

L'API di Google viene utilizzata per la traduzione gratuita. Se non riesci ad accedere a Google, configura e imposta un proxy, ad esempio:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Lo script di traduzione genererà una cache tradotta nella directory `.i18n` , controllala con `git status` e aggiungila al repository di codice per evitare traduzioni ripetute.

Eseguire `bunx i18n` ogni volta che si modifica la traduzione per aggiornare la cache.

Se il testo originale e la traduzione vengono modificati contemporaneamente, la cache sarà confusa, quindi se vuoi modificarne, puoi modificarne solo uno, quindi eseguire `bunx i18n` per aggiornare la cache.
