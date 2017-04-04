# api documentation for  [pluralize (v4.0.0)](https://github.com/blakeembrey/pluralize#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-pluralize.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-pluralize) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-pluralize.svg)](https://travis-ci.org/npmdoc/node-npmdoc-pluralize)
#### Pluralize and singularize any word

[![NPM](https://nodei.co/npm/pluralize.png?downloads=true)](https://www.npmjs.com/package/pluralize)

[![apidoc](https://npmdoc.github.io/node-npmdoc-pluralize/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-pluralize_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-pluralize/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-pluralize/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-pluralize/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Blake Embrey",
        "email": "hello@blakeembrey.com",
        "url": "http://blakeembrey.me"
    },
    "bugs": {
        "url": "https://github.com/blakeembrey/pluralize/issues"
    },
    "dependencies": {},
    "description": "Pluralize and singularize any word",
    "devDependencies": {
        "chai": "^3.2.0",
        "istanbul": "^0.3.0",
        "mocha": "^2.3.2",
        "semistandard": "^7.0.2"
    },
    "directories": {},
    "dist": {
        "shasum": "59b708c1c0190a2f692f1c7618c446b052fd1762",
        "tarball": "https://registry.npmjs.org/pluralize/-/pluralize-4.0.0.tgz"
    },
    "files": [
        "pluralize.js"
    ],
    "gitHead": "ce8fa7f7486d292195f4bd330e7376eeca0f3f1d",
    "homepage": "https://github.com/blakeembrey/pluralize#readme",
    "keywords": [
        "plural",
        "plurals",
        "pluralize",
        "singular",
        "singularize",
        "inflection"
    ],
    "license": "MIT",
    "main": "pluralize.js",
    "maintainers": [
        {
            "name": "blakeembrey",
            "email": "me@blakeembrey.com"
        }
    ],
    "name": "pluralize",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/blakeembrey/pluralize.git"
    },
    "scripts": {
        "lint": "semistandard",
        "test": "npm run lint && npm run test-cov",
        "test-cov": "istanbul cover node_modules/mocha/bin/_mocha -- -R spec --bail",
        "test-spec": "mocha -R spec --bail"
    },
    "version": "4.0.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module pluralize](#apidoc.module.pluralize)
1.  [function <span class="apidocSignatureSpan">pluralize.</span>addIrregularRule (single, plural)](#apidoc.element.pluralize.addIrregularRule)
1.  [function <span class="apidocSignatureSpan">pluralize.</span>addPluralRule (rule, replacement)](#apidoc.element.pluralize.addPluralRule)
1.  [function <span class="apidocSignatureSpan">pluralize.</span>addSingularRule (rule, replacement)](#apidoc.element.pluralize.addSingularRule)
1.  [function <span class="apidocSignatureSpan">pluralize.</span>addUncountableRule (word)](#apidoc.element.pluralize.addUncountableRule)
1.  [function <span class="apidocSignatureSpan">pluralize.</span>plural (word)](#apidoc.element.pluralize.plural)
1.  [function <span class="apidocSignatureSpan">pluralize.</span>singular (word)](#apidoc.element.pluralize.singular)



# <a name="apidoc.module.pluralize"></a>[module pluralize](#apidoc.module.pluralize)

#### <a name="apidoc.element.pluralize.addIrregularRule"></a>[function <span class="apidocSignatureSpan">pluralize.</span>addIrregularRule (single, plural)](#apidoc.element.pluralize.addIrregularRule)
- description and source-code
```javascript
addIrregularRule = function (single, plural) {
  plural = plural.toLowerCase();
  single = single.toLowerCase();

  irregularSingles[single] = plural;
  irregularPlurals[plural] = single;
}
```
- example usage
```shell
...
pluralize.plural('regex') //=> "regexii"

pluralize.singular('singles') //=> "single"
pluralize.addSingularRule(/singles$/i, 'singular')
pluralize.singular('singles') //=> "singular"

pluralize.plural('irregular') //=> "irregulars"
pluralize.addIrregularRule('irregular', 'regular')
pluralize.plural('irregular') //=> "regular"

pluralize.plural('paper') //=> "papers"
pluralize.addUncountableRule('paper')
pluralize.plural('paper') //=> "paper"
'''
...
```

#### <a name="apidoc.element.pluralize.addPluralRule"></a>[function <span class="apidocSignatureSpan">pluralize.</span>addPluralRule (rule, replacement)](#apidoc.element.pluralize.addPluralRule)
- description and source-code
```javascript
addPluralRule = function (rule, replacement) {
  pluralRules.push([sanitizeRule(rule), replacement]);
}
```
- example usage
```shell
...
pluralize('test', 1) //=> "test"
pluralize('test', 5) //=> "tests"
pluralize('test', 1, true) //=> "1 test"
pluralize('test', 5, true) //=> "5 tests"
pluralize('蘋果', 2, true) //=> "2 蘋果"

pluralize.plural('regex') //=> "regexes"
pluralize.addPluralRule(/gex$/i, 'gexii')
pluralize.plural('regex') //=> "regexii"

pluralize.singular('singles') //=> "single"
pluralize.addSingularRule(/singles$/i, 'singular')
pluralize.singular('singles') //=> "singular"

pluralize.plural('irregular') //=> "irregulars"
...
```

#### <a name="apidoc.element.pluralize.addSingularRule"></a>[function <span class="apidocSignatureSpan">pluralize.</span>addSingularRule (rule, replacement)](#apidoc.element.pluralize.addSingularRule)
- description and source-code
```javascript
addSingularRule = function (rule, replacement) {
  singularRules.push([sanitizeRule(rule), replacement]);
}
```
- example usage
```shell
...
pluralize('蘋果', 2, true) //=> "2 蘋果"

pluralize.plural('regex') //=> "regexes"
pluralize.addPluralRule(/gex$/i, 'gexii')
pluralize.plural('regex') //=> "regexii"

pluralize.singular('singles') //=> "single"
pluralize.addSingularRule(/singles$/i, 'singular')
pluralize.singular('singles') //=> "singular"

pluralize.plural('irregular') //=> "irregulars"
pluralize.addIrregularRule('irregular', 'regular')
pluralize.plural('irregular') //=> "regular"

pluralize.plural('paper') //=> "papers"
...
```

#### <a name="apidoc.element.pluralize.addUncountableRule"></a>[function <span class="apidocSignatureSpan">pluralize.</span>addUncountableRule (word)](#apidoc.element.pluralize.addUncountableRule)
- description and source-code
```javascript
addUncountableRule = function (word) {
  if (typeof word === 'string') {
    uncountables[word.toLowerCase()] = true;
    return;
  }

  // Set singular and plural references for the word.
  pluralize.addPluralRule(word, '$0');
  pluralize.addSingularRule(word, '$0');
}
```
- example usage
```shell
...
pluralize.singular('singles') //=> "singular"

pluralize.plural('irregular') //=> "irregulars"
pluralize.addIrregularRule('irregular', 'regular')
pluralize.plural('irregular') //=> "regular"

pluralize.plural('paper') //=> "papers"
pluralize.addUncountableRule('paper')
pluralize.plural('paper') //=> "paper"
'''

## License

MIT
...
```

#### <a name="apidoc.element.pluralize.plural"></a>[function <span class="apidocSignatureSpan">pluralize.</span>plural (word)](#apidoc.element.pluralize.plural)
- description and source-code
```javascript
plural = function (word) {
  // Get the correct token and case restoration functions.
  var token = word.toLowerCase();

  // Check against the keep object map.
  if (keepMap.hasOwnProperty(token)) {
    return restoreCase(word, token);
  }

  // Check against the replacement map for a direct word replacement.
  if (replaceMap.hasOwnProperty(token)) {
    return restoreCase(word, replaceMap[token]);
  }

  // Run all the rules against the word.
  return sanitizeWord(token, word, rules);
}
```
- example usage
```shell
...
pluralize('test') //=> "tests"
pluralize('test', 1) //=> "test"
pluralize('test', 5) //=> "tests"
pluralize('test', 1, true) //=> "1 test"
pluralize('test', 5, true) //=> "5 tests"
pluralize('蘋果', 2, true) //=> "2 蘋果"

pluralize.plural('regex') //=> "regexes"
pluralize.addPluralRule(/gex$/i, 'gexii')
pluralize.plural('regex') //=> "regexii"

pluralize.singular('singles') //=> "single"
pluralize.addSingularRule(/singles$/i, 'singular')
pluralize.singular('singles') //=> "singular"
...
```

#### <a name="apidoc.element.pluralize.singular"></a>[function <span class="apidocSignatureSpan">pluralize.</span>singular (word)](#apidoc.element.pluralize.singular)
- description and source-code
```javascript
singular = function (word) {
  // Get the correct token and case restoration functions.
  var token = word.toLowerCase();

  // Check against the keep object map.
  if (keepMap.hasOwnProperty(token)) {
    return restoreCase(word, token);
  }

  // Check against the replacement map for a direct word replacement.
  if (replaceMap.hasOwnProperty(token)) {
    return restoreCase(word, replaceMap[token]);
  }

  // Run all the rules against the word.
  return sanitizeWord(token, word, rules);
}
```
- example usage
```shell
...
pluralize('test', 5, true) //=> "5 tests"
pluralize('蘋果', 2, true) //=> "2 蘋果"

pluralize.plural('regex') //=> "regexes"
pluralize.addPluralRule(/gex$/i, 'gexii')
pluralize.plural('regex') //=> "regexii"

pluralize.singular('singles') //=> "single"
pluralize.addSingularRule(/singles$/i, 'singular')
pluralize.singular('singles') //=> "singular"

pluralize.plural('irregular') //=> "irregulars"
pluralize.addIrregularRule('irregular', 'regular')
pluralize.plural('irregular') //=> "regular"
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
