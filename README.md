# string-similarity-match
[Site](https://github.com/AndreaCardamone/string-similarity-match) |
[Docs](https://github.com/AndreaCardamone/string-similarity-match) |

The [string-similarity](https://www.npmjs.com/package/string-similarity) wrapper for more common usage

## Installation
In a browser:
Waiting update for in-browser support

Using npm:
```shell
$ npm i -s https://github.com/AndreaCardamone/string-similarity-match.git
```


## Example

```js
const { matchs } = require('string-similarity-match')

let sources = ["foobar", "test"];
let targets = ["toobar", "foo-bar", "barfoo", "test", "fest", "cest"];
let m = matchs({ sources, targets });

// the match of "[foobar, test]" from "[toobar, foo-bar, barfoo, test, fest, cest] is {"foobar":"foo-bar","test":"test"}
console.log(`the match of "${source}" from "[${targets.join(', ')}] is ${m}`);
```

```js
const { matchs } = require('string-similarity-match')

let targets = JSON.parse(readFileSync('./sources.json', 'utf8'))
let sources = [
  {value: `"ELEONORE O' KON" <stephen91@gmail.com>`},
  {value: `Chaim Bogan<Gregoria_McKenzie@yahoo.com>`}
]
let m = matchs({
  sources, targets,
  log: true,
  source_getter: d => d.value,
  target_getter: d => `${d.firstname} ${d.lastname} ${d.email}`,
  threshold: 0.7,
  match_callback: ({ source, target, score }) => source.score = score,
})

console.log(m)
```

## Related

- **[string-similarity](https://github.com/aceakash/string-similarity)**:
  Finds degree of similarity between two strings, based on [Dice's Coefficient](http://en.wikipedia.org/wiki/S%C3%B8rensen%E2%80%93Dice_coefficient),
  which is mostly better than [Levenshtein distance](http://en.wikipedia.org/wiki/Levenshtein_distance).
