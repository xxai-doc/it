<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Parte del codice del sito web è open source, benvenuto per aiutare a ottimizzare la traduzione.

## codice di front-end

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
