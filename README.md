<h1>Automatic Version</h1>

~~~bash
npm i release-it @release-it/conventional-changelog @commitli
nt/config-conventional @commitlint/cli --include=dev
~~~

~~~json
  "release-it": {
    "git": {
      "commitMessage": "chore: release v${version}"
    },
    "github": {
      "release": true
    },
    "npm": {
      "publish": false
    },
    "plugins": {
      "@release-it/conventional-changelog": {
        "infile": "CHANGELOG.md",
        "preset": {
          "name": "conventionalcommits",
          "types": [
            {
              "type": "feat",
              "section": "Features"
            },
            {
              "type": "fix",
              "section": "Bug Fixes"
            },
            {}
          ]
        }
      }
    }
  }
~~~

~~~bash
npm i husky --save-dev
~~~

~~~bash
#isso permite executar comandos com base em ações de confirmação
./node_modules/husky/lib/bin.js install
~~~

~~~bash
#verificar as mensagens de confirmação
touch .husky/commit-msg && chmod a+x .husky/commit-msg
~~~

~~~shell
#fala para o husky para executar comando commitlint no commit

#!/bin/sh
. "${dirname "$0"}/_/husky.sh"

npx commitlint --edit
~~~

~~~bash
#roda a release
npm run release
~~~